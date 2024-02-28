Conditional rendering menggunakan conditonal operation seperti :
`&&` , `IF-ELSE`, `? :` (*ternary*).

## `IF` statement

contoh penggunaan if statement pada JSX :
```jsx
if(condition){
return <p> its true </p>
}else { return <p> false </p>}
```
*penggunaan if  untuk melakukan return sebuah element html*

katakan anda ingin melakukan perubahan berikut pada tampilan :
perubahan pada sebuah list pengingat  apabila bernilai `true` maka akan bertanda '✔'.

```jsx
function Item({ name, isPacked }) {
  if (isPacked) {
    return <li className="item">{name} ✔</li>;
  }
  return <li className="item">{name}</li>;
}
```
*component **Item** *

**contoh penggunaan :** 
```jsx
function Item({ name, isPacked }) {
  if (isPacked) {
    return <li className="item">{name} ✔</li>;
  }
  return <li className="item">{name}</li>;
}

export default function PackingList() {
  return (
    <section>
      <h1>Sally Ride's Packing List</h1>
      <ul>
        <Item 
          isPacked={true} 
          name="Space suit" 
        />
        <Item 
          isPacked={1 > 0} 
          name="Helmet with a golden leaf" 
        />
        <Item 
          isPacked={false} 
          name="Photo of Tam" 
        />
      </ul>
    </section>
  );
}
```
https://codesandbox.io/s/dt2pur?file=/App.js&utm_medium=sandpack

### penggunaan penambahan variabel untuk beberapa pengecekan  sekaligus 

penggunaan pengecekan yang banyak pada sebuah component(fungsi) sekaligus akan sangat merepotkan jika harus melakukan return element pada setiap kondisinya maka dengan membuat variabel sementara dapat mempermudah kasus tersebut.

```jsx
function Drink({ name }) {
  let part = 'bean',
  caffeine= '80–185 mg/cup',
  age ='1,000+ years';
  
  if(name === 'tea'){
    part = 'leaf';
    caffeine = '15–70 mg/cup';
    age = '4,000+ years';
  }
    return (
    <section>
      <h1>{name}</h1>
      <dl>
        <dt>Part of plant</dt>
        <dd>{part}</dd>
        <dt>Caffeine content</dt>
        <dd>{caffeine}</dd>
        <dt>Age</dt>
        <dd>{age}</dd>
      </dl>
    </section>
  );
}
```
*dengan melakukan operasi kondisi terlebih dahulu dan menyimpan nilai pada varibel sementara lalu melakukan pemanggilan variabel tersebut pada return element *
https://codesandbox.io/s/kooh7i?file=/App.js&utm_medium=sandpack

## logical operator `&&`

 contoh cara kerja logical operator seperti berikut
```jsx
true && console.log("saya bekerja")
```
*maka akan menghasilkan output pada console "saya bekerja" *
```jsx
false && console.log("saya bekerja")
```
*maka tidak menghasilkan out pada console / tidak diesekusi*.

contoh penggunaan :
```jsx
function Item({ name, isPacked }) {
  return (
    <li className="item">
      {name} {isPacked && '✔'}
    </li>
  );
}
```

```jsx
export default function PackingList() {
  return (
    <section>
      <h1>Sally Ride's Packing List</h1>
      <ul>
        <Item 
          isPacked={false} 
          name="Space suit" 
        />
        <Item 
          isPacked={2 > 0} 
          name="Helmet with a golden leaf" 
        /> 
        <Item 
          isPacked={false} 
          name="Photo of Tam" 
        />
      </ul>
    </section>
  );
}
```
https://codesandbox.io/s/teim3u?file=/App.js&utm_medium=sandpack


## `? :` Ternary operation
```jsx
condition ? DoingIftrue : DoingIffalse ;
```
*bagian pertama adalah sebuah nilai yang dapat menjadi sebuah boolean dan 2 sisi selanjutnya adalah yang akan dikerjakan apabila true dan false*

**FROM THIS** :
```jsx
if (isPacked) {  
return <li className="item">{name} ✔</li>;  
}  
return <li className="item">{name}</li>;
```
**TO THIS** :
```jsx
return (  
<li className="item">  
{isPacked ? name + ' ✔' : name}  
</li>  
);
```

### contoh penggunaan :
```jsx
function Item({ name, isPacked }) {
  return (
    <li className="item">
      {name} {isPacked && '✔'}
    </li>
  );
}
```
*fungsi akan melakukan pengondisian pada nilai variabel name*
```jsx
export default function PackingList() {
  return (
    <section>
      <h1>Sally Ride's Packing List</h1>
      <ul>
        <Item 
          isPacked={true} 
          name="Space suit" 
        />
        <Item 
          isPacked={true} 
          name="Helmet with a golden leaf" 
        />
        <Item 
          isPacked={false} 
          name="Photo of Tam" 
        />
      </ul>
    </section>
  );
}
```

https://codesandbox.io/s/3o6p96?file=%2FApp.js&utm_medium=sandpack










