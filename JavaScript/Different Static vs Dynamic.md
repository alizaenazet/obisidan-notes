1.  kamu bisa mendeklarasikan sebuah variabel tanpa menentukan type datanya
```js
	anVar = 0 ; // "ini berarti anVar bertipe data Int" .
	anVar = "0"; // "sebab ada string literal pada nilai variable tersebut maka-  anVar bertipe data String"
```


2. definisi Type data hanya terdiri 2 **'let'** apabila anda ingin menginisiasinya kelak, **'const'** apabila ingin menetapkan sebuah nilai.
```js
	let anVar = 0; 
	anvar = 3;
	const anotherVar = 0;
```
	

3. tidak perlu memberikan "[]" pada nama variabel untuk membuat sebuah array
	```js
let arrayVar = [1,2,3,4,5];
```
	

4. anda dapat memodifkasi nilai dari array walaupun bertype data "*const*" 
	```js
	const arrayVar = ["joni", "anton", "budi"]
	arrayVar[0] = "dodit";
```
	
	
5. Array pada javascrip memiliki beberapa function seperti *shift()*, *unshift()*, *pop()*, *push()*;
dengan fungsi *pop()* anda dapat mengambil sebuah nilai terakhir pada array di index yang dituju dan mengembalikan return value.
```js 
	let arrayVar = ["budi" , "sentosa", "hartono"];
	let getValueArray = arrayVar.pop();
```
*maka kini variabel `'getValueArray' `memiliki nilai = `"hartono"  `


6. diperbolehkan duplikat nama variabel pada scope yang berbeda, apabila ada 2 duplikat variabel dengan scope yang berbeda apabila dipanggil salah satunya maka yang terpanggil adalah variabel yang berada pada scope yang sama .

7. fungsi tidak perlu menentukan type data apabila ingin melakukan return value;
```js
	function aFunction(param1, param2){
	return param1 + param2; 
	}
```
8. dapat me-komprasi 2 *data type* yang berbeda dengan operasi == *(equal)* namun tidak dengan operasi === *('strict' equal)* sebab operasi *'strict'* akan mengecek *data type*  .
equal `==`
 ```js
1   ==  2  // false
1   == '1' // true
"3" ==  3  // true
```
strict equal `===`
```js
3 ===  3  // true
3 === '3' // false
```

itu juga berlaku dengan operasi lain yang memiliki tipe *strict* seperti != dan !== , > dan >= dsb
**Operasi !=**
```js
1 !=  2    // true
1 != "1"   // false
1 != '1'   // false
1 != true  // false
0 != false // false
```

```js
3 !==  3  // false
3 !== '3' // true
4 !==  3  // true
```

**Operasi > dan <**
```js
5   >  3  // true
7   > '3' // true
2   >  3  // false
'1' >  9  // false
```

```js
6   >=  6  // true
7   >= '3' // true
2   >=  3  // false
'7' >=  9  // false
```

```js
2   < 5 // true
'3' < 7 // true
5   < 5 // false
3   < 2 // false
'8' < 4 // false
```

```js
4   <= 5 // true
'7' <= 7 // true
5   <= 5 // true
3   <= 2 // false
'8' <= 4 // false
```


9. switch case dengan case yang kosong, apabila anda memiliki 3 case dengan output yang sama maka buat 3 itu berurutan tanpa da break dan isi tindakan di case terakhir.
```js
let result = "";
switch (val) {
  case 1:
  case 2:
  case 3:
    result = "1, 2, or 3";
    break;
  case 4:
    result = "4 alone";
}
```
apabila val = 1/2/3 maak hasilnya akan sama pada case 3/

10. membuat object dalam js memiliki perbedaan dalam pembuatan properties/field : 
a.  menggunakan "**:**" bukan "**=**". 
b.  setiap properti dapat memiliki spasi pada penamaannya dengan menambahkan " " ketika   mengakses properti tersebut menggunakan tanda bracket notation (`[]`).
c. wajib menggunakan tanda koma " **,** "  setelah penulisan properties. 
d. tidak boleh menyertakan typedata seperti `let` dan `const` .
e. menentukan nama properties dari sebuah `value variabel`
```js
const cat = {
  "name": "Whiskers", // A
  "legs": 4,          // C
  "tails": 1,        // D
  "makanan favorit" : "ikan", //B
  "enemies": ["Water", "Dogs"]
};

const catName = cat.name;
const catFavFood = cat["makanan favorit"]; //B
const myCat = legs; 
const catLegs = cat[myCat];  //E

```
*contoh sebuah object cat*

11. dapat memodifikasi object dengan menambahkan properti baru pada object

```js
const ourDog = {
  "name": "Camper",
  "legs": 4,
  "tails": 1,
  "friends": ["everything!"]
};

ourDog.bark = "bow-wow";
```
*menambahkan properties `bark` dengan value = `"bow-bow"`*

12. setelah memahami point 11 sebelumnya anda mengetahui bahwa properties pada *object* dapat diperbarui namun kali ini anda dapat menghapus properti pada *object* tersebut.
```js
const ourDog = {
  "name": "Camper",
  "legs": 4,
  "tails": 1,
  "friends": ["everything!"],
  "bark": "bow-wow"
};

delete ourDog.bark;
```

13. Nested Object
```js
const ourStorage = {
  "desk": {
    "drawer": "stapler"
  },
  "cabinet": {
    "top drawer": { 
      "folder1": "a file",
      "folder2": "secrets"
    },
    "bottom drawer": "soda"
  }
};

ourStorage.cabinet["top drawer"].folder2;
ourStorage.desk.drawer;
```

14. function parameter
function dalama Js apabila anda memberikan parameter anda tidak dikenakan kewajiban untuk mengisi parameter tersebut apabila memanggil functionnya.

