fungsi ini akan memudahkan dalam mengambil sebuah nilai dari index pada `array` atau properti pada `object` .

## **implementasi pada array :** 
perhatikan baris ke 2 pada kode berikut : 
```js
const myNameArr = ["thomas", "tommy" ,"shelby"]
let{firstName, middleName, lastName} = myNameArr;
  

console.info(firstName) // Output : thomas
console.info(middleName) // Output : tommy
console.info(lastName) // Output : shelby
console.info(address) // Output : undefined
```
dimana anda dapat mengakses sebuah index pada array tanpa perlu menggunakan indexnya, nilai yang diambil akan sesuai dengan urutan pada destructuring. apabila sebuah index tidak ada maka akan mengeluarkan nilai `undefined`.

## implementasi pada Object
fungsi ini akan memungkinkan untuk mengambil sebuah nilai dari properti pada object dan dapat juga memberikan sebuah nilai default pada properti tersebut apabila dipanggil dan tidak memiliki nilai maka default value itu yang akan terpanggil, berikut penerapannya : 
```js
const myNameObj = {
firstName : "thomas",
middleName,
lastName : "shelby",
addres : "bermingham",
gender : "male"

}
let{firstName, middleName = "tom", lastName, ...others} =myNameObj;

  

console.info(firstName) // Output : thomas
console.info(middleName) // Output : tom (nilai default pada destructure)
console.info(lastName) // Output : shelby
console.info(others) // Output : {addres: "bermingham" , gender : "male"}
```
anda dapat memberi nilai default pada preperti pada contoh tersebut diketahui bahwa properti `middleName` tidak terdapat value sehingga ketika dipanggil maka yang akan didapat adalah nilai default tersebut.

pada fungsi tersebut anda juga dapat menambahkan sebuah `rest parameter`, perhatikan pada kolom destructuring `...others`  dimana akan menyimpan semua sisa properti yang tidak disebut, pada contoh tersebut maka properti `addres` dan `male` akan ditampung oleh `...others`

**Note : ** perlu diingat bahwa semua fitur fungsi akan sama pada array maupun object.



