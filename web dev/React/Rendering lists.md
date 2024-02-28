Teknik melakukan Render komponen yang berulang hanya dengan isi yang berbeda, kasus seperti ini biasanya terjadi saat menampilkan sebuah list, galeri foto dsb.

## Rendering data from Array
untuk dapat anda melakukan perulangan render salah satunya memanfaatkan beberapa method dari `array` seperti `map()` dan `filter()` 

pastikan data anda telah tersedia pada sebuah variabel array seperti berikut :
```jsx
const people = [  
'Creola Katherine Johnson: mathematician',  
'Mario José Molina-Pasquel Henríquez: chemist',  
'Mohammad Abdus Salam: physicist',  
'Percy Lavon Julian: chemist',  
'Subrahmanyan Chandrasekhar: astrophysicist'  
];
```
*array sebuah string namun ini berlaku untuk semua tipe array termasuk jika berisikan object*

### `Map()` 
cara kerja `Map()` sesuai dengan sebagaimana dimethod of array pada JS.

- Sediakan sebuah array berisikan data yang akan dirender sebagai isi dari komponen
```jsx
const people = [  
'Creola Katherine Johnson: mathematician',  
'Mario José Molina-Pasquel Henríquez: chemist',  
'Mohammad Abdus Salam: physicist',  
'Percy Lavon Julian: chemist',  
'Subrahmanyan Chandrasekhar: astrophysicist'  
];
```

- gunakan method `Map()` pada sebuah variabel 
```jsx
const listItems = people.map(person => <li>{person}</li>);
```

- lakukan `return` pada komponen
```jsx
return <ul>{listItems}</ul>;
```

#### contoh lengkap :
```jsx
const people = [
  'Creola Katherine Johnson: mathematician',
  'Mario José Molina-Pasquel Henríquez: chemist',
  'Mohammad Abdus Salam: physicist',
  'Percy Lavon Julian: chemist',
  'Subrahmanyan Chandrasekhar: astrophysicist'
];

export default function List() { //komponen List
  const listItems = people.map(person =>
    <li>{person}</li>
  );
  return <ul>{listItems}</ul>;
}

```


### `filter()` 
sadari bahwa langkah ini sebenarnya sama dengan langkah menggunakan `map()` namun method dari `filter()` akan membantu dalam memilah sebuah nilai dari array yang akan dirender.

- Sediakan sebuah array (pada contoh array dengan nilai object)
```jsx
const people = [
{  
id: 0,  
name: 'Creola Katherine Johnson',  
profession: 'mathematician',  
}, {  

id: 1,  
name: 'Mario José Molina-Pasquel Henríquez',  
profession: 'chemist',  

}, {  

id: 2,  
name: 'Mohammad Abdus Salam',  
profession: 'physicist',  

}, {  

name: 'Percy Lavon Julian',  
profession: 'chemist',  

}, {  

name: 'Subrahmanyan Chandrasekhar',  
profession: 'astrophysicist',  

}];

```
*array of object People*

- gunakan method `filter()` untuk melakukan pemilah pada array sesuai keinginan.
```jsx
const chemists = people.filter(person =>  
person.profession === 'chemist'  
);
```
*variabel `chemist` akan menyimpan object dari `people` yang memiliki profesi chemist*

dengan menampung nilai array sesuai pemilahan maka dapat dilakukan rendering dengan method `map()` seperti pada langkah menggunakan method `map()`.

- `Map()` pada variabel hasil dari `filter()`
```jsx
const listItems = chemists.map(person =>  

<li>  
<p>  

<b>{person.name}:</b>  
{' ' + person.profession + ' '}  
known for {person.accomplishment}  

</p>  
</li>  

);
```

- lakukan `return` pada varibel yang menyimpan nilai map
```jsx
return <ul>{listItems}</ul>;
```

#### contoh lengkap :
```jsx
import { people } from './data.js';
import { getImageUrl } from './utils.js';

export default function List() {
  const chemists = people.filter(person =>
    person.profession === 'chemist'
  );
  const listItems = chemists.map(person =>
    <li>
      
      <p>
        <b>{person.name}:</b>
        {' ' + person.profession + ' '}
        known for {person.accomplishment}
      </p>
    </li>
  );
  return <ul>{listItems}</ul>;
}

```

### Contoh kasus :
https://codesandbox.io/s/rendering-list-75hceq