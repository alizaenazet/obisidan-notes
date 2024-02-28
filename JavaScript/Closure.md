closure adalah diamna anda melakukan nested function dan mengembalikan nilai dari function yang bersarang didalam function utamanya, contoh :

disini akan membuat sebuah fungsi yang akan menambah sebuah nilai dengan sebuah nilai yang sudah ditentukan pada fungsi tersebut, seperti :
`fungsi tambah10` dimana fungsi tersebut ketika dipanggil anda akan melakukan operasi +(tambah) dengan inputan anda.
perhatikan pada 2 return di fungsi berikut :
```js
function creatAdder(value){
const keterangan =`the value is ${value} + your input = `

function added(params) {
console.info(keterangan)
return value + params // return pada fungsi `added`
}

return added; //return pada fungsi `creatAdder`

}
```
*fungsi yang bersarang akan mengembalikan nilai dari operasi "value + params", lalu nilai tersebut dikembalikan untuk menjadi nilai dari fungsi creatAdder* 

berikut penggunaanya : 
```js
const addTen = creatAdder(10); // value 10 akan ditetapkan sebagai nilai yang akan ditambahkan saat function addTen diinput

console.info(addTen(5))
```
*nilai dari parameter fungsi creatAdder bernilai 10 dan nilai dari parameter fungsi added bernilai 5*.

ketika ingin menggunakan fungsi `creatAdder` maka harus menentukan terlebih dahulu untuk parameter dari fungsinya, hal tersebut dilakukan ketika mendeklarasikan variabel `addTen` dan parameter dari fungsi creatAdder akan terisi nilai 10.

ketika fungsi telah dideklarasikan pada sebuah variabel anda dapat memanggil variabel tersebut berulang kali seperti layaknya fungsi pada umumnya.
```js
const addTen = creatAdder(10); // value 10 akan ditetapkan sebagai nilai yang akan ditambahkan saat function addTen diinput

console.info(addTen(5)) //10(value) + 5(params)
console.info(addTen(20)) //10(value) + 20(params)
```
berikut outputnya :
![[Jepretan Layar 2023-03-18 pukul 12.48.47.png]]

contoh lainnya : 
```js
const addTen = creatAdder(10); // value 10 akan ditetapkan sebagai nilai yang akan ditambahkan saat function addTen diinput

const addFive = creatAdder(5); // value 5 akan ditetapkan sebagai nilai yang akan ditambahkan saat function addTen diinput

console.info(addTen(5)) //10(value) + 5(params)
console.info(addTen(20)) //10(value) + 20(params)

console.info(addFive(5)) //20(value) + 5(params)
console.info(addFive(20)) //20(value) + 20(params)
```
maka outputnya adalah: ![[Jepretan Layar 2023-03-18 pukul 12.51.48.png]]

