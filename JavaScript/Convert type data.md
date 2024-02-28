
#konversiTypeData #konversiNilai
![[Jepretan Layar 2023-03-15 pukul 22.38.41.png]]

```js
let stringVar = "123.13"

let toInt = parseInt(stringVar);

let toFloat = parseFloat(stringVar)

let toNumber = Number(stringVar)

let toString = toNumber.toString()
```

**note :**
apabila anda mengkonversi sebuah string ke type data selain string dan variabel tersebut tidak berisikan sebuah angka maka akan menghasilkan `NaN` *Not a number* , contoh :

```js
let stringVar = "bukan angka";
let toInt = parseInt(stringVar) 
//output : NaN
```
*`stringVar` memiliki nilai yang tak dapat dikonversi * 

namun berbeda apabila pada nilai tersebut memiliki nilai angka diawal maka akan tetap dikonversi angka tersebut, hal tersebut spesial tidak berlaku pada konversi type data `Number` sebab dia tidak mentoleransi, contoh : 
```js
let stringVar = "12 Tiga"
let toInt = parseInt(stringVar) //output = 12
let toNumber = Number(stringVar) //output = NaN
```
*konversi ke type data `number` harus dipastikan tidak terdapat string selain angka*

