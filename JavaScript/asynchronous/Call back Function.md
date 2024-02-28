fungsi ini mirip *return value* pada fungsi namun dia akan mengembalikan nilai pada parameter dan parameter tersebut dapat di-isi dengan sebuah fungsi kembali.

perhatikan kode berikut : 
```js
function theOutput(someThing) {
console.log(someThing);
}

function myCalculator(num1, num2, myCallback) {
let sum = num1 + num2;
myCallback(sum); //me-inisiasi parameter
}

myCalculator(5, 5, theOutput);
```
*ketika fungsi `theOutput` dijalankan dia akan mengambil paramet pada fungsinya, parameter yang didapat pada fungsi `theOutput` adalah hasil dari fungsi `myCalculator`*

```js
function myCalculator(num1, num2, myCallback) {
let sum = num1 + num2;
myCallback(sum); //me-inisiasi parameter
}
```
melakukan pemanggilan pada parameter `myCallback` hal tersebut akan mengembalikan nilai ketika fungsi `myCalculator` telah selesai dijalankan ke parameter itu sendiri.

```js
myCalculator(5, 5, theOutput); // parameter myCallBack di-isi dengan fungsi `theOutput`
```

berikut urutanya :
- fungsi `myCalculator` berjalan
- hasil dari fungsi `myCalculator` menjadi nilai pada fungi `theOutput`
- fungsi `theOutput` dijalankan

**Contoh lainnya : **
```js
function getUser(callBackCuy) {

setTimeout(() => {
const user = ["budi","anton","joni"];
callBackCuy(user);
}, 3000);
}


function userCallBack(params) {
console.log(`get the data : ${params}`)
}

getUser(userCallBack) //Output : ["budi","anton","joni"]
```


Saat Anda menjadikan fungsi sebagai argumen, ingatlah untuk tidak menggunakan tanda kurung.
Benar:  `myCalculator(5, 5, myDisplayer); `
Salah:   `myCalculator(5, 5, myDisplayer());`