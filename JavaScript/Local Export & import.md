### Export & Import Common Js

## EXPORT
Modul bekerja dengan cara exporting dan importing nilai. Baik itu nilai variabel, fungsi, array, object, atau class agar bisa digunakan pada berkas JavaScript lain. Satu berkas JavaScript terdiri dari satu module yang dapat kita export menjadi lebih dari satu nilai.

Dalam environment Node.js, gunakan perintah `module.exports` untuk melakukan proses export module. Setiap berkas JavaScript yang berjalan pada Node, memiliki objek module lokal yang memiliki properti `exports`. Properti tersebut digunakan untuk mendefinisikan nilai apa yang akan diekspor dari berkas tersebut.

### Export 1 nilai

```js
const coffeeStock = {
arabica: 100,
robusta: 150,
liberica: 200
}

    module.exports = coffeeStock;
  //perintah exports pada variabel `coffeStock`
  
```
*Kode` module.exports = coffeeStock` membuat object coffeeStock ditetapkan sebagai nilai dari module.exports.*

**Note : ** 
gunakan hanya ketika melakukan export pada 1 nilai saja. jangan menggunakan cara tersebut apabila melakukan export lebih dari 1 nilai

### Export beberapa nilai
ketika anda melakukan export lebih dari 1 nilai maka harus menambahkan nama pada export tersebut dengan memberi `.` diikuti nama export, seperti berikut :
```js
modul.exports.namaMethod = Varnilai ;
modul.exports.namaUsaha = namaToko ;
modul.exports.cabang = cabang;
```
cara lain melakukan export berbagai nilai :
```js
module.exports = {
namaToko : namaUsaha,
cabangToko : cabang,
infoUsaha : spillUsaha,
infoProduk : product
}; //lakukan bila ingin key dan value berbeda nama

module.exports = {namaUsaha,cabang,spillUsaha,product}; // bila ingin key dan value sesuai
```


contoh implementasi :
```js
let namaUsaha = "buah makmur sentosa";

const product = {
nama : "apel malang",
warna : `hijau`,
harga : 8000
}

class cabang{
constructor(){
console.log(`cabang telah dibuat`)
     }
  }  
  

function spillUsaha(){
console.log(`nama toko : ${namaUsaha}`)
}


module.exports.namaUsaha = namaUsaha; 
module.exports.cabang = cabang;
module.exports.spillUsaha = spillUsaha;
module.exports.product = product;
```
*melakukan export pada beberapa nilai seperti variabel, class, fungsi, object*

ketika melakukan export dengan nilai yang lebih dari 1 maka akan dijadikan sebuah object ketika dilakukan import.

## IMPORT
untuk melakukan import dari nilai dari sebuah modul dapat menggunakan method `require()` .

kita gunakan method require() dengan memberikan parameter lokasi berkas yang export. 

```js
module.exports = coffeeStock; // Melakukan export 

const stokKopi = require(`./state`) // Melakukan import

console.log(stokKopi);
```

Jika kita menggunakan lokasi yang relatif (dapat berubah/dipindahkan), pastikan awali dengan menuliskan ./. Contohnya, berkas index.js dan state.js berada pada folder yang sama, maka kita cukup menuliskannya dengan ./state.js.

### Import banyak nilai
melakukan import sebuah nilai atau beberapa nilai memiliki cara yang sama.
ketika anda melakukan banyak nilai pastikan anda melakukan exsport dengan cara yang benar(untuk exsport banyak nilai). pada dasarnya ketika melakukan import pada banyak nilai maka akan dijadikan sebuah object yang berisikan nilai-nilai yang di-export. 

berikut melakukan import pada sebuah class.
```js
let dataUsaha = require(`./state`) //melakukan eksport dari class state
```
*variabel yang menampung akan memiliki nilai object dari hasil import*

```js
{
  namaUsaha: 'buah makmur sentosa',
  cabang: [class cabang],
  spillUsaha: [class cabang],
  product: { nama: 'apel malang', warna: 'hijau', harga: 8000 }
}
```
*output pada variabel `dataUsaha`*


## ES6 
cara ini berbeda dengan metode common JS dibagian atas.
Sejak ES6, JavaScript memiliki sistem modular secara native. Karena itu, sistem ini dapat dijalankan baik pada environment Node.js maupun browser.

### Export 1 nilai
untuk melakukan export sebuah nilai saja pada modul maka gunakan keywoard `export default` diikut dengan menunjukan variabel yang diexport seperti berikut :
```js
export default cabang; //export pada variabel cabang
```

### Export beberapa nilai
apabila ingin melakukan export beberapa nilai maka dapat menerapkan destructuring object, sebeperti berikut :
```js
export {namaUsaha, product ,cabang, spillUsaha}; //me-export 4 variabel sekaligus
```
perlu diperhatikan bahwa dalam melakukan import harus urut dan penamaan sesuai penulisan export.

### Import 1 Nilai
untuk melakukan import pada 1 nilai saja maka memiliki penggunaan yang mirip dengan *common js*, berikut contohnya :
```js
import namaUsaha from "./state.js"; //melakukan eksport dari class state
```
keywoard `import` menunjukan variabel yang akan di-import, diikuti dengan keywoard  `from`
menunjukan lokasi modul pada variabel yang diimport.

**Note : gunakan tanda petik untuk keywoard `from` jangan menggunakan backtick**

### Import beberapa nilai
untuk melakukan import lebih dari 1 nilai maka dapat menggunakan destructuring object, seperti yang dilakukan saat melakukan export. anda harus memasukan nama variabel pada kolom `import` dengan benar dan sesuai urutan. contoh :
```js
import {namaUsaha, product, cabang, spillUsaha} from "./state.js";
```
*apabila penulisan pada baris import terdapat ketidak sesuaian maka akan error*

#### import with alias
anda dapat pemberian nama pada variabel yang diimport dengan keywoard `as`, seperti berikut : 
```js
import {namaUsaha as namaToko, product as produkToko, cabang as cabangToko, spillUsaha as deskripsi} from "./state.js";
```

dengan begitu anda dapat mengakses variabel `namaUsaha` dengan nama `namaToko`.
```js
console.log(namaUsaha) //Output: buah makmur sentosa
console.log(namaToko) //Output: buah makmur sentosa
```

