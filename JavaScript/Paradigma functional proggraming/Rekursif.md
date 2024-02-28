Rekursif merupakan teknik pada sebuah function yang memanggil dirinya sendiri.

Kita akan mencoba mengubah fungsi countDown yang biasanya kita buat menggunakan sintaksis iterasi seperti for, foreach, while seperti kode di bawah menjadi bentuk rekursif :

```js
const countDown = start => {
    do {
      console.log(start);
      start -=1;
    }
    while(start > 0);
 };

  countDown(10);
```

hal tersebut dapat di-implementasi pula dengan rekursif function seperti berikut :
```js
const countDown = start => {
  console.log(start);
  if(start > 0){ //sebagai acuan untuk berhentinya fungsi
  
countDown(start-1);} //memanggil fungisnya sendiri
};

countDown(10); //
```

Dengan teknik rekursif ini, kita sebenarnya bisa menggantikan operasi iterasi dengan rekursi. Namun tidak sebatas itu saja, dengan rekursi kita dapat membuat dan mengolah data structures seperti Tree dan Array.

