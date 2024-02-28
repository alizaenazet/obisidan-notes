satu fungsi dalam JavaScript yang digunakan untuk menjadwalkan **sekali pemanggilan** sebuah kode sekaligus membuatnya berjalan secara asynchronous, yakni setTimeout(). Fungsi tersebut menerima dua argumen dengan penjelasan berikut.

1.  Argumen pertama merupakan sebuah fungsi yang akan dipanggil secara terjadwal dan asynchronous.
2.  Argumen kedua merupakan delay waktu dalam satuan _milisecond_ yang menentukan delay dari pemanggilan fungsi pada argumen pertama.

```js
setTimeout(() => {
//isi perintah
}, timeout); // waktu yang ditentukan *mili detik
```
*syntax setTimeOut function* 

```js
console.log("selamat datang ");

setTimeout(() => {
console.log("senang bertemu anda bye, kiw 😚")
}, 3000);

console.log("ini adalah sebuah proggram asynchronous")
```
*fungsi setTimeout akan keluar 3 detik pasca proggram dijalankan*

hasil ketika dijalankan : 
```js
selamat datang 
ini adalah sebuah proggram asynchronous
senang bertemu anda bye, kiw 😚
```

**Note : Pemanggilan hanya sekali saja**
