Teknik composition adalah sebuah teknik dimana **Membuat** komponen yang terdiri dari beberapa komponen(kecil) lain yang dapat digunakan kembali menjadi satu kesatuan. 
contoh : 
ketika terdapat membuat komponen *card* maka akan sekaligus membuat beberapa komponen baru yang lebih kecil sebagai isi dari komponen *card* tersebut, seperti : "Header", "Body", dan "Footer", komponen yang lebih kecil tersebut dinamakan ***Sub-component*** .

berikut sebuah gambar teknik *composition* pada komponen layar utama pada sebuah aplikasi, dimana komponen tersebut terdari dari beberapa *sub-component* :
![[Pasted image 20230428172739.png]]
*terdapat beberapa subcomponent yaitu : form, todoData, todoItem dan AllTodos *

## Penerapan 
membuat sebuah komponen "Card" yang terdiri dari komponen "Header", "Body", dan "Footer". Kita dapat membuat masing-masing komponen tersebut sebagai sub-komponen dari "Card" dengan menggunakan teknik composition.

Berikut adalah contoh kode untuk komponen "Card" dengan menggunakan teknik composition:
```jsx
import React from 'react';
import CardHeader from './CardHeader';
import CardBody from './CardBody';
import CardFooter from './CardFooter';

function Card(props) {
  return (
    <div className="card">
      <CardHeader title={props.title} /> //subcomponent
      <CardBody text={props.text} /> //subcomponent
      <CardFooter author={props.author} /> //subcomponent
    </div>
  );
}

export default Card;

```
*Component Card dengan beberapa subcomponent*

Pada kode di atas, kita menggunakan komponen "CardHeader", "CardBody", dan "CardFooter" sebagai sub-komponen dari "Card". Dengan cara ini, kita dapat menggabungkan beberapa komponen menjadi 1 komponen yang lebih kompleks dan terstruktur.

Dalam contoh di atas, "Card" menerima properti "title", "text", dan "author" dari komponen induknya. Properti tersebut kemudian diteruskan ke masing-masing sub-komponen untuk ditampilkan sesuai dengan fungsinya. Dengan teknik composition, kita dapat membuat komponen yang modular dan mudah dipelihara, karena masing-masing sub-komponen hanya bertanggung jawab pada tugasnya masing-masing.

