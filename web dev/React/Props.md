Props adalah singkatan dari *Properties* tidak lain dan tidak bukan adalah layaknya sebuah properties pada fungsi/method, yang mana tujuannya adalah untuk memanggil(fungsi) atau mengambil (data) dari class/file yang berbeda.
Props bersifat **Read Only** .

## apa yang spesial ?

hal yang menjadikan sebuah *props* spesial adalah pada sisi penerapannya, dimana props di-deklarasikan pada sebuah `tag`/`element` *HTML* seperti halnya properties pada `HTML` element.
```jsx
<InfoPengguna /*Pemanggilan Component | 👇 deklrasi/input props*/
		name={name}
		age={age}
		menyapaOrang={menyapaOrang}
		/>
```
*Element "info pengguna" dilakukan deklrasi/input pada tag seperti sebuah element HTML*

*Props* juga seperti berupa objek sehingga berapapun dan apapun yang dimasukan pada Props maka akan ditampung lalu akan dapat diakses dengan seperti mengakses nilai/properi pada object
```jsx
function InfoPengguna(theProps) {

const name = theProps.name; //menggunakan nilai pada props
const age = theProps.age;
```

## Mengirim/mengisi *props* pada component 

```jsx
import InfoPengguna from "./infoPengguna";

export default
function MyformComponent() {

const name = "budi"
const age = 20
const menyapaOrang = (name) => {
console.log("hallo selamat datang, nama saya " + name );
}

	return (
	<>
		<h1>Formulir Page 👍</h1>
		
		<InfoPengguna /*Pemanggilan Component | 👇 deklrasi/input props*/
		name={name}
		age={age}
		menyapaOrang={menyapaOrang}
		/>
	
	</>

	   )
}
```
*Seperti memasukan nilai pada properti didalam `tag` html   *

## Menggunakan nilai pada props

```jsx
export default

function InfoPengguna(theProps) {

const name = theProps.name; //menggunakan nilai pada props
const age = theProps.age;

return (
	<>
	
	<h1>Data pengguna</h1>
	<h3>Nama : {name}</h3>
	<h3>Umur : {age}</h3>
	<button onClick={theProps.menyapaOrang("sutik")} >
	Click untuk menyapa</button>
	
	</>

)
}
```

## Hasil tampilan :
![[Screenshot 2023-04-26 at 20.48.33.png]]
*Nama, Umur dan Aksi pada button didapat dari props*

