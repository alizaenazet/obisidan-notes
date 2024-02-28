**requirement :**
1. AWS CLI
2. AWS SAM CLI
3. DOCKER

```js

const {refreshTokenScheme,allRoleScheme,ownerUserScheme, merchantScheme,userScheme,ownerAdminScheme,ownerScheme} = require('./utils/strategyOptionJwt');
const Jwt = require('@hapi/jwt');
const Hapi = require('@hapi/hapi');


(async () => { // nest in a object 

const server = Hapi.server({
port: 8080, // using port 8080 
host: "0.0.0.0",
});

await server.register(Jwt);
server.route(merchantRoutes)

try {
await server.start()
console.log(`server version ${server.version}`);
console.log(`server perjalan pada ${server.info.uri}`);
} catch (error) {
return error
}

})();
```

## Using docker & AWS SAM

`.dockerignore`
```
node_modules
.aws-sam
```
Excluded file 

`.Dockerfile`
```
FROM public.ecr.aws/docker/library/node:16.13.2-stretch-slim
COPY --from=public.ecr.aws/awsguru/aws-lambda-adapter:0.7.0 /lambda-adapter /opt/extensions/lambda-adapter

EXPOSE 8080 
COPY .env /var/task/.env
WORKDIR "/var/task"
ADD package.json /var/task/package.json
ADD package-lock.json /var/task/package-lock.json
RUN npm install --omit=dev
ADD src/ /var/task

CMD ["node", "server.js"]
```

**Penyesuaian :**

`COPY .env ` : .env di-copy dan menentukan lokasi sesuai path `.env` berarti file berada pada root folder. 

`ADD package.json` & `package-lock.json ` : melakukan `package.json` dan menentukan lokasi path file pada contoh menandakan berada pada root folder 

`ADD src/`  : menunjukan file yang berisikan fungsi,module dsb berada pada file src, contoh jika file berada pada file root (pada contoh lain) : `ADD . /var/task` . 

`CMD ["node", "server.js"]` : menjalankan aplikasi, nilai ke-2 menunjukan main file berada di root folder *(disarankan)*. 


`template.yaml`
``` yaml

AWSTemplateFormatVersion: "2010-09-09"
Transform: AWS::Serverless-2016-10-31
Description: >
sam-app
Sample SAM Template for sam-app

  

# More info about Globals: https://github.com/awslabs/serverless-application-model/blob/master/docs/globals.rst

Globals:
	Function:
		Timeout: 29

Resources:
	CashirinFunction:
		Type: AWS::Serverless::Function
		Properties:
			Policies: # izin mengkases layanan aws sesuaikan dengan module aws yang digunakan e.g S3 Bucket
				- S3CrudPolicy: # more info : https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/serverless-policy-templates.html
					BucketName: cahsierinstorage
			PackageType: Image
			MemorySize: 1024
			Environment:
				Variables:
					RUST_LOG: info
			Events:
			Root:
				Type: HttpApi #tipe api eg.http, httpApi dsb sesuaikan denga ketersediaan pada region
				Properties:
					Path: /
					Method: ANY
			Petstore:
				Type: HttpApi
				Properties:
					Path: /{proxy+}
					Method: ANY
		Metadata:
		DockerTag: v1
		DockerContext: . #lokasi lvl direktori file docker (lokasi pada root)
		Dockerfile: Dockerfile # nama file docker (disanrakan)

Outputs:
	ExpressApi:
	Description: "API Gateway endpoint URL for Prod stage for Express function"
	Value: !Sub "https://${ServerlessHttpApi}.execute-api.${AWS::Region}.${AWS::URLSuffix}/"
	```

## Deploy with AWS SAM

1. Install aws CLI dan lakukan configurasi standar untuk login akun aws
2. Install aws SAM CLI
3. buat sebuah repositori
4. Lakukan login pada sebuah repository yang ditujuh setelah (direkomendasikan menggunakan region yang sama dengan region dipilih untuk aws lambda)
5. <iframe src="https://scribehow.com/embed/Authenticating_Docker_Client_and_Retrieving_Autentikasi_Token__c_x_tmjUTUqToqdaymlzGg" width="100%" height="640" allowfullscreen frameborder="0"></iframe>
6. Paste salinan token autentikasi pada terminal dan pastikan berhasil
7. `sam build` 
8. pastikan semua aman tidak ada kendala 
9. jalankan `sam deploy --guided`
