secara dasar membuat http server cukup sederhana, diharuskan anda memahami 2 method yaitu `http.creatServer()` dan `listen()` berserta semua parameternya.

## `http.creatServer()`

- **import/require**
```js
const http = require('http'); //variabel http siap digunakan beserta semua methodnyaa
```

- **method `http.creatServer()`**

method ini berfungsi untuk membuat HTTP server yang merupakan instance dari *http.server* .
```js
http.createServer((req,res) =>{
}) //method digunakan 
```

pada method tersebut memiliki 2 parameter yaitu **request** & **response**, pastikan telah memahami konsep tersebut terlebih dahulu. berikut penjabaran 2 parameter tersebut :

### 1. **Request**, 
Seperti yang tertulis pada contoh kode di atas, request merupakan objek yang menyimpan informasi terkait permintaan yang dikirimkan oleh client. 
pada saat method `creatServer` dijalankan secara otomatis berarti dilakukannya proses *Request*.

### 2. **Response, **
response merupakan objek yang digunakan untuk menanggapi permintaan. Melalui objek ini kita bisa menentukan data yang diberikan, format dokumen yang digunakan, kode status, atau informasi response lainnya. 

```js
http.createServer((req,res) =>{
res.setHeader('Content-Type', 'text/html'); 
res.statusCode = 200;
res.end("<h1> hello cak</h1>")
}
```



## `Listen()`

Method inilah yang membuat http.server selalu standby untuk menangani permintaan yang masuk dari client. Setiap kali ada permintaan yang masuk, request listener akan tereksekusi.

**Method `listen()` dapat menerima 4 parameter**, berikut detailnya:
-   **port** (number) : jalur yang digunakan untuk mengakses HTTP server.
-   **hostname** (string) : nama domain yang digunakan oleh HTTP server.
-   **backlog** (number) : maksimal koneksi yang dapat ditunda (pending) pada HTTP server.
-   **listeningListener** (function) : callback yang akan terpanggil ketika HTTP server sedang bekerja (listening).
keempat parameter di atas bersifat opsional. Kita bisa memberikan nilai port saja, atau kombinasi apa pun dari keempatnya. Hal itu tergantung terhadap kebutuhan Anda. Namun lazimnya, ketika memanggil method listen() kita memberikan nilai port, hostname, dan listeningListener.

```js
const port = 8080;
const host = 'localhost';
listen(port,host, () =>{
console.log(`server berjalan pada port${port} host${host}`)
})
```





## Penerapan 
```js
const http = require('http');
const port = 8080;
const host = 'localhost';


http.createServer((req,res) =>{
res.setHeader('Content-Type', 'text/html');
res.statusCode = 200;
res.end("<h1> hello world</h1>")
}).listen(port,host, () =>{
console.log(`server berjalan pada port${port} host${host}`)
})
```
*penggunaan method `Listen()` berapa setelah `http.creatServer()`*

