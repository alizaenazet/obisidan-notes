 
 ## Generate
 Contoh generate sebuah token :
```js
const token = Jwt.token.generate(

{
aud: 'desktop_app', // peruntukan penerima token
iss: 'http://www.api.cashirin.com', // pembuat token
user: username, // identitas pengguna token
},
{
key:process.env.ACCESS_TOKEN_SECRET,
algorithm: 'HS256'
},
{
ttlSec: 60 // usia token berlaku dalam detik (3600=1 jam)
}

)

const decodeToken = Jwt.token.decode(token);
```

Penjelasan pada contoh tersebut sudah benar. Berikut adalah penjelasan untuk setiap properti yang digunakan:

- `aud`: Merupakan singkatan dari "audience" yang menunjukkan penerima token. Dalam contoh tersebut, nilai 'desktop_app' menunjukkan bahwa token ditujukan untuk digunakan oleh aplikasi desktop.

- `iss`: Merupakan singkatan dari "issuer" yang menunjukkan penerbit token. Dalam contoh tersebut, nilai 'https://www.myapp.com' menunjukkan bahwa token diterbitkan oleh aplikasi dengan URL tersebut.

- `user`: Merupakan identitas pengguna yang terkait dengan token. Dalam contoh tersebut, nilai 'merchant_username' menunjukkan bahwa token terkait dengan pengguna dengan username 'merchant_username'.

- `group`: Merupakan kelompok atau grup yang terkait dengan token. Dalam contoh tersebut, nilai 'merchant_group' menunjukkan bahwa token terkait dengan kelompok merchant.

- `key`: Merupakan shared secret key yang digunakan untuk menandatangani (sign) token. Dalam contoh tersebut, nilai 'your_shared_secret_key' adalah kunci rahasia yang digunakan untuk proses signing token.

- `algorithm`: Merupakan algoritma yang digunakan untuk menandatangani (sign) token. Dalam contoh tersebut, nilai 'HS256' menunjukkan bahwa algoritma hash HMAC-SHA256 digunakan.

- `ttlSec`: Merupakan usia token dalam detik, menentukan berapa lama token tersebut berlaku sebelum kadaluarsa. Dalam contoh tersebut, nilai 3600 menunjukkan bahwa token berlaku selama 1 jam (3600 detik).

Setelah token di-generate, kemudian dilakukan decoding pada variabel `decodedToken` untuk mendapatkan informasi yang terdapat dalam token tersebut.


## Validate
Contoh validasi pada objek `options` :
```js
const options = {
keys:process.env.ACCESS_TOKEN_SECRET,

	verify: {
	aud:["web_app","desktop_app"], 
	iss:"http://www.api.cashirin.com",
	sub:false,
	nbf:true,
	exp:true,
	maxAgeSec: 3600,
	timeSkewSec: 15
	},
	
	validate:(artifacts, request, h) => {
		return {
		isValid: true,
		credentials: { user: artifacts.decoded.payload.user }
		};
	}
}
```

