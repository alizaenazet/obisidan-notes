```jsx
export default // Cara export varitif namun wajib menggunakan `export default`
class MyClassComponent extends React.Component { // deklrasi `class` komponen

render(){ //pemanggilan fungsi `render()`
return ( // melakukan `return`

<div>

<h1>Class Component</h1>
<hr></hr>

</div>

)
}
}
```

- Melakukan Export pada Component `export default`
- deklarasi class `extends React.Component` `class MyClassComponent extends React.Component`
- Menggunakan CamelCase pada penamaan component (**Salah** `myComp` **Benar** `MyComp`).
- memanggil fungsi `render()`
- melakukan `return` pada semua isi component didalam fungsi `render()`
