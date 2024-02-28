**cara melakukan navigasi antar halaman(route) : **
1.  **`<Link>`**  [[link & navigation#`<Link>`]]
2.  **`useRouter`** [[link & navigation#`useRouter`]]


## `<Link>`
```jsx
<Link href={"/about"}> menuju about page</Link>
```

## `useRouter` 
```jsx
import { useRouter } from 'next/navigation'
```
*import fungsi `useRouter` dari 'next/navigation' *

```jsx
const router = useRouter() // deklrasi pada sebuah variabel

function handelHomeButton() {
router.push("/myPage") //masukan url route sebagai parameter
}
```

