conditional code akan mengembalikan sebuah nilai true/false. 
di JS conditional code sangat variatif selain *IF statement*, *switch case* dan *ternary operation* berikut beberapa penjabarannya : 


## Type data Falsy and Truthly
sebelum mengenal beberapa operasi kondisi pada JS alangkah baiknya memahami terhadapa beberapa ketentuan dari pengecekan tipe data boolean, seperti pada umumnya boolean memiliki dua nilai saja yaitu `true` dan `false`, di JS ada beberapa nilai apabila kita cek variabel yang menyimpan dapat menghasilkan kondisi true dan false, berikut data yang dianggap *Falsy*  : 
![[Jepretan Layar 2023-03-17 pukul 20.21.18.png]]
*Data yang dianggap Falsy(false)*

maka selain data tersebut maka akan termasuk *Truthly(true)*.
contoh : 
```js
console.info("Hello" || ""); //Output : Hello
console.info("" || []); //Output : []
console.info(0 || "Nol"); //Output : Nol
console.info("0" || "Nol"); //Output : 0 (yang diawal)
console.info(0 || null); //Output : null (yang diakhir)
```
*OR operator ( `||` ) akan memilih nilai yang bersifat `true`* 


## Operator "IN"
#checkProperty #checkObject  #InOperation
`IN` operation diperuntukan untuk pengecekan sebuah array dan object hal ini akan memudahkan dalam melakukan pengecekan **property** dalam sebuah object atau pada sebuah array.
perlu diingat bahwasanya operasi ini tidak mengecek sebuah nilai apabila sebuah property bernilai `Null/Undefined` selama property itu ada maka akan memberikan input `true`

berikut cara implementasi `in` , kodenya :
```js
let resultVar = "theProperty" in myClass; //result = true/false  
```

contoh :  
```js
const student = {
firstName : Undefined;
lastName : "utomo";
}

const myArray = {"index 0" , null , 2 };


console.info(firstname in student) //Output : true
console.info(gender in student) //Output : false
console.info(lastName in student) //Output : true

console.info(0 in myArray) //Output : true
console.info(5 in myArray) //Output : false
console.info(1 in  myArray)//Output : true

```

**Video lengkap : **
https://youtu.be/SDROba_M42g?t=12299

## Operator Nullish 
#NullishOperation #NullishCheck #NullCheck
perlu diketahui sebuah nilai akan dikatakan Nullish apabila bernilai `Null` dan `Undefined`.
*Nullish operation* digunakan untuk mengecek sebuah variabel apakah memiliki nilai nullish sekaligus melakukan sebuah esekusi sekaligus.
perhatikan *if statement* berikut :
```js
let myVar = null;
let myResut;
if(myVar != null && myVar !- undefinded){
myResult = "inserting a string value"
}
```
*sebuah pengecekan sekaligus melakukan inisiasi pada sebuah nilai variabel*

hal tersebut dapat anda melakukan hal yang sama dengan *Nullish operation*, seperti berikut :
```js
let myVar = null;
let myResut = myVar ?? "inserting a string value"
```

kedua metode tersebut memiliki tindakan yang sama namun dengan cara yang berbeda, maka gunakan operasi nullish untuk sebuah pengecekan sederhana nilai sebuah variabel.

**video lengkap :** 
https://youtu.be/SDROba_M42g?t=12977

## Optional Chaining
#OptionalChaining #CheckVar
Operasi ini sederhanannya akan melakukan pengecekan para *object* beserta propertynya sehingga menghasilkan sebuah output  nilai `variabel` atau `property` bukan nilai `true` / `false`, hal tersebut yang jelas membedakannya dengan #InOperation .

jika dia melakukan sebuah pengecekan pada sebuah *object* atau "*property*" dan tidak menemukannya maka akan mengeluarkan nilai `undefined`.
apabila pengecekan object / property memang ditemukan maka akan mengambil nilai dari property dipaling ujung. berikut contohnya :

```js
const myObj = {
myFamiliy : {
				name : null,
				addres : "the home place"
}
}

document.writeln(myObj?.myFamiliy?.name) //Output : null
document.writeln(myObj?.myFriend?.name) //Output : undefined
document.writeln(myObj?.myFamiliy?.addres) //Output : the home place
document.writeln(myObj?.myFamiliy?.contact) //Output : undefined
```

**video lengkap :** 
https://youtu.be/SDROba_M42g?t=13303


