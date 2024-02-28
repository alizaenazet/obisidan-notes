- sisipkan file dengan nama `error.js/ts(x)` didalam direktori app route 
![[Screenshot 2023-05-21 at 11.09.54.png]]

- buat sebuah function untuk komponen 
```tsx
export default function ErrorPage(error:Error,reset:()=> void) {
//Error handling 

}
```
*mengambil 2 argument `error` & `reset` digunakan melakukan mengambil erro dan melakukan sebuah refresh pada route*

- Contoh penggunaan menampilkan error 
```jsx
"use client" //useEffect harus use client
import { useEffect } from "react";

export default function ErrorPage(error:Error,reset:()=> void) {

useEffect(()=> {
console.log("error nih bos") 
console.log(error) // melakukan print error pada console
}, [error])

	return(
	<div>
		<details>
		<summary>waduh ada error nich 😱</summary> //tampilan pada halaman
		<p>anda dapat menyanjikan eror juga disini </p>
		</details>
			<button onClick={() => reset()}>Coba lagi</button> //refresh
	</div>
	)

}
```

- dapat digunakan pada setiap `segment` pada setiap route direktori 

