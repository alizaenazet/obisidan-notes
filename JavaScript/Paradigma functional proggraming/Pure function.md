Agar lebih mudah dalam mengetahui apakah fungsi yang Anda buat sudah pure atau belum, pastikan 3 konsep ini ada pada fungsi yang Anda buat.

-   Mengembalikan nilai yang sama bila inputannya (nilai parameter) sama.
-   Hanya bergantung pada argumen yang diberikan.
-   Tidak menimbulkan efek samping.

Bila 3 konsep di atas terpenuhi, maka bisa dipastikan Anda membuat sebuah _pure function_.

- ## 1. Tidak bergantung pada nilai diluar fungsi
Salah satu konsep besar dari paradigma FP adalah Pure Function. Apa artinya? Pure Function merupakan konsep dari pembuatan fungsi yang mengharuskan fungsi untuk **tidak bergantung terhadap nilai yang berada di luar fungsi atau parameternya**. Sehingga mau seperti apa keadaanya, fungsi yang dibuat selalu menghasilkan sesuatu yang sama, terkecuali bila fungsi tersebut diberikan nilai parameter yang berbeda.

```js
let PI = 3.14;

const hitungLuasLingkaran = (jariJari) => {
  return PI * (jariJari * jariJari); 
}

console.log(hitungLuasLingkaran(4)); // 50.24
PI = 5; // tidak sengaja nilai PI berubah
console.log(hitungLuasLingkaran(4)); // 80
```
*fungsi `hitungLuasLinkarang` tidak pure function*

Fungsi tersebut tidak bisa dikatakan pure function karena ia membutuhkan nilai yang berada di luar dari fungsinya, yakni nilai PI. Bila nilai PI berubah, maka penggunaan fungsi menghasilkan nilai yang berbeda walaupun diberikan nilai parameter yang sama.

berikut contoh yang sama namu dengan penerapan *Pure function* dengan sesuai :
```js
const hitungLuasLingkaran = (jariJari) => {
  return 3.14 * (jariJari * jariJari); 
}

console.log(hitungLuasLingkaran(4)); // 50.24
console.log(hitungLuasLingkaran(4)); // 50.24
console.log(hitungLuasLingkaran(8)); // 200.96
console.log(hitungLuasLingkaran(8)); // 200.96
```
*nilai `PI` tidak diluar fungsi, maka fungsi tidak lagi bergantung pada nilai diluarnya*.

- ## 2. No side Effecy(tidak memiliki efek samping)

pure function juga **dilarang keras untuk mengubah nilai yang berada di luar baik secara sengaja atau tidak sengaja**. berikut contoh fungsi dengan efek samping :
```js
const createPersonWithAge = (age, person) => {
  person.age = age;
  return person;
};

const person = {
  name: 'Bobo'
};

const newPerson = createPersonWithAge(18, person);

console.log({
  person, //output : person: { name: 'Bobo', age: 18 },
  newPerson //output : newPerson: { name: 'Bobo', age: 18 }
});

```
*fungsi mengubah nilai dari object `person` yang dimasukan sebagai parameter fungsi tersebut*.
bisa disimpulkan bahwa fungsi tersebut mengakibatkan efek samping pada nilai diluar fungsi itu sendiri, berikut fungsi yang sama namun tidak menimbukan efek samping :
```js
const createPersonWithAge = (age, person) => {
  return { ...person, age }; //menggunakan 
};

const person = {
  name: 'Bobo'
};

const newPerson = createPersonWithAge(18, person);

console.log({
  person,
  newPerson
});
```
*manfaatkan destructuring object daripada mengubah objek tersebut secara langsung.*
