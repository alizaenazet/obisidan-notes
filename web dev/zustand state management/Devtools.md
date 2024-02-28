Zustand dilengkapi dengan devtools bawaan untuk mempermudah debugging aplikasi. Devtools ini memungkinkan kita untuk melihat dan mengubah nilai state dengan mudah. 

## Pembahasan
1.  Jenis penggunaan dapat melalui broser maupun NPM [[Devtools#Jenis Penggunaan]]
2. implementasi pada kode state [[Devtools#Implementasi]]

## Jenis Penggunaan 
Zustand menyediakan dua cara untuk menggunakan devtools: menggunakan ekstensi browser dan menggunakan package pada Node.js.

1.  **Menggunakan ekstensi browser**: Anda dapat menggunakan ekstensi browser seperti React Developer Tools atau Zustand Devtools. Ekstensi tersebut akan menambahkan tab baru di DevTools yang memungkinkan Anda melihat state yang digunakan oleh aplikasi Anda.

berikut cara pemasangan ekstensi pada broser Chrome :
<iframe src="https://scribehow.com/embed/How_to_Use_Redux_DevTools_for_myProject_Example__RFQYsVE4SA2FmduZxDokZg" width="100%" height="640" allowfullscreen frameborder="0"></iframe>


2.  **Menggunakan package pada Node.js**: Jika Anda ingin menggunakan devtools pada lingkungan produksi atau saat menjalankan aplikasi pada server, Anda dapat menggunakan paket `zustand/middleware/devtools` dari Node.js. Dalam hal ini, devtools dijalankan sebagai middleware, dan dapat dipanggil dari kode Anda seperti middleware lainnya.  akses npmjs.com/package/simple-zustand-devtools  


Kedua cara tersebut dapat Anda gunakan sesuai kebutuhan Anda. Jika Anda ingin melakukan debugging pada aplikasi Anda di lingkungan pengembangan, maka menggunakan ekstensi browser mungkin lebih mudah dan cepat. Namun, jika Anda ingin melakukan debugging di lingkungan produksi atau ketika tidak menggunakan browser, maka menggunakan package pada Node.js bisa menjadi pilihan yang lebih baik.

## Implementasi

- Import `devtools` dari `zustand/middleware`
```jsx
import { devtools } from 'zustand/middleware'
```

- gunakan didalam hooks dan letakan state didalamnya
`devtools()` argumen diisi dengan state agar dapat melakukan *tracking* menggunakan devtools pada extensi maupun package.
```jsx
let storeTodo = (set)=>({ //state didalam store
todoList : [`mandi`, `futsal`],
addTodo : (todo) =>
set((state) => ({todoList : [...state.todoList, todo ]})),
})

storeTodo = create(devtools(storeTodo))//penggunaan `devtools` didalam fungsi `create`

export { storeTodo }
```

- pilih cara menggunakan devtools [[Devtools#Jenis Penggunaan]]

**Video **
<iframe width="560" height="315" src="https://www.youtube.com/embed/jLcF0Az1nx8?clip=UgkxPo8YWL-qGJBcCX_KyiTTyqINhS36xsXz&amp;clipt=EKO4IhjGiCU" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>


