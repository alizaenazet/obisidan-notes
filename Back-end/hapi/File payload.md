```js
config:{
handler: merchantUploadLogo,
payload: {
maxBytes: 209715200, // Batas ukuran payload (misalnya, 200 MB)
output: 'file', // Mengoutputkan payload sebagai file
parse: true, // Parsing payload secara otomatis
multipart: true // Mengizinkan tipe konten multipart/form-data
}

}
```

**pastikan konfigurasi pada route sesuai**
```js
//merchantRouter.js
method:"POST",
path:"/merchants/profile/logo/upload",

config:{
handler: merchantUploadLogo, // nama file handler
payload: {
maxBytes: 209715200, // Batas ukuran payload (misalnya, 200 MB)
output: 'file', // Mengoutputkan payload sebagai file
parse: true, // Parsing payload secara otomatis
multipart: true // Mengizinkan tipe konten multipart/form-data
}

}
```

**Buat file upload** 
```js
  // 
const fs = require('fs');
const aws = require('aws-sdk');

aws.config.update({ //configurasi awsS3
accessKeyId:'AKIAWJ46WHK4BLDIOXVS',
secretAccessKey:'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',
region:'ap-southeast-3'
});


const s3 = new aws.S3({
apiVersion:"2023-05-28",
params:{
Bucket:"cahsierinstorage"}
});

async function uploadFile(file) {
const fileContent = fs.readFileSync(file.path); //lakukan pengambilan(baca) pada file kiriman
return new Promise((resolve, reject) => {
const options = { partSize: 10 * 1024 * 1024, queueSize: 1 }; //10mb

const params = { //params yang akan dikirimkan
Bucket: "cahsierinstorage",
Key: file.filename,
Body: fileContent, // file
ContentType: file.headers['content-type']
};

s3.upload(params, options, (err, res) => { //Upload
if (err) {
reject(err);
} else {
resolve(res);
}
});
});

}

module.exports = uploadFile```

**buat file handler** 
```js
  

async function merchantUploadLogo(req, h) {
try {
const responseFile = await uploadFile(req.payload.file);
const url = { fileUrl: responseFile.Location };
const response = h.response({
status:"uploaded",
"file_url":url.fileUrl,
})

response.code(201)
return response;
} catch (err) {
const response = h.response({
"status":"fail"
})

response.code(422);
return response
}

};
```
