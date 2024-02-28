#writeFile #menulisFile

cara untuk membuat dan menulis sebuah file.
*apabila sebuah file tidak tersedia maka akan otomatis membuat sebuah file baru, namun jika file telah tersedia maka akan menimpa file .*
pertama diharuskan untuk melakukan import core module `fs`, berikut caranya : 
```js
const fs = require('fs');
```
*import fs modul*

## Syncronous 

- **method** `writeFileSync()`, method tersebut memiliki 2 parameter, yaitu **nama file** dan **isi file ** tersebut, seperti berikut : 
```js 
fs.writeFileSync("test.txt","hello, write file with Syncronous")
```
*parameter pertama : nama file beserta format & parameter ke-2 isi file*

- **method** `writeStream()`, untuk menggunakannya harus mendefinisikan pada sebuah variabel, seperti berikut :
```js
const writeStream = fs.createWriteStream('outputFile.txt');
```
*nama variabel akan memiliki method*.

setelah mendeklarasikan pada sebuah variabel maka variabel tersebut akan memiliki method, sebagai berikut :

**Write :** 
```js
writeStream.write("teks pada baris pertama\n");
```
*method memiliki parameter yang akan menjadi isi pada file*

**End : **
```js
writeStream.end("ini teks terakhir sebagai penutup");
```
**method untuk mengakhiri penulisan file sekaligus memiliki parameter yang dapat di-isi (wajib)*.*


## Asyncronous

- **method** `writeFile()` , memiliki 3 parameter yaitu **nama file dan jenisnya**, **isi file** dan **callback function**.
```js
fs.writeFile("file-dibuat.txt", "write file with Asyncronous", (e) => {console.log(e)});
```
*parameter terakhir berupa fungsi atau arrow function sebagai callBack*.
