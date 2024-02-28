Routing merupakan istilah dalam menentukan respons server berdasarkan path atau url yang diminta oleh client. 
Request ke [dicoding.com](https://www.dicoding.com/) akan menampilkan homepage Dicoding, sedangkan [dicoding.com/about](https://www.dicoding.com/about) akan menampilkan halaman tentang Dicoding.

dengan begitu kita perlu mendapatkan `url` yang dituju oleh penggunda.

Dalam `http.clientRequest` properti `url` akan mengembalikan nilai path secara lengkap tanpa host dan port yang digunakan server. Contohnya :
alamat **http://localhost:5000/about**  :  **/about**
alamat  **http://localhost:5000/** :  **/**

dengan begitu dapat dilakukan pengecekan untuk menentukan halaman mana yang akan ditampilan (*request*) sesuai url yang dimaksud.

```js
const {url} = req; //mengambil url dari request
```

```js
const {url} = req;

if (url === '/homePage') {
// respon membuka tampilan halaman 'home page'
}else if(url === '/profile'){
// respon membuka tampilan halaman 'profile'
}
```
