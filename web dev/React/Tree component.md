Pohon komponen adalah analogi dimana sebuah komponen memiliki struktur seperti sebuah pohon yang mana setiap komponen dari atas hingga keakar akan saling berhubungan.

## Contoh :

Dalam struktur berikut, App adalah **root component**, sedangkan Header dan Body adalah **child component** dari App. Kemudian, Navigation, Content, Sidebar, dan Footer adalah **child component** dari Header dan Body.

![[Screenshot 2023-04-30 at 21.16.34.png]]

Perhatikan gambar berikut dimana komponen App sebagai *root* memiliki beberapa child component : 
![[Pasted image 20230430210447.png]]

## Contoh implementasi :

Pada contoh berikut, kita memiliki root komponen `App` yang memiliki 2 cabang: `Parent1` dan `Parent2`. Setiap cabang kemudian memiliki cabang sendiri-sendiri. Sebagai contoh, `Parent1` memiliki 2 cabang lagi yaitu `Child1` dan `Child2`, dan `Child2` memiliki satu cabang lagi yaitu `Grandchild1`.

Dengan menggunakan struktur seperti ini, kita dapat dengan mudah memvisualisasikan hubungan antar komponen dalam aplikasi kita. Ini juga dapat membantu kita dalam melakukan debugging ketika terjadi masalah pada aplikasi.
```jsx
function App() {
  return (
    <div>
      <h1>Ini adalah root komponen</h1>
      <Parent1 />
      <Parent2 />
    </div>
  );
}

function Parent1() {
  return (
    <div>
      <h2>Ini adalah Parent1</h2>
      <Child1 />
      <Child2 />
    </div>
  );
}

function Parent2() {
  return (
    <div>
      <h2>Ini adalah Parent2</h2>
      <Child3 />
      <Child4 />
    </div>
  );
}

function Child1() {
  return (
    <div>
      <h3>Ini adalah Child1</h3>
    </div>
  );
}

function Child2() {
  return (
    <div>
      <h3>Ini adalah Child2</h3>
      <Grandchild1 />
    </div>
  );
}

function Child3() {
  return (
    <div>
      <h3>Ini adalah Child3</h3>
      <Grandchild2 />
    </div>
  );
}

function Child4() {
  return (
    <div>
      <h3>Ini adalah Child4</h3>
    </div>
  );
}

function Grandchild1() {
  return (
    <div>
      <h4>Ini adalah Grandchild1</h4>
    </div>
  );
}

function Grandchild2() {
  return (
    <div>
      <h4>Ini adalah Grandchild2</h4>
    </div>
  );
}

```