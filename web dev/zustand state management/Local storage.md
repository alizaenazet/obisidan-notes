untuk menyimpan sebuah state pada localstorage maka dapat menggunakan middleware persist pada zustand, dimana setiap perubahan pada state akan disimpan pada localstorage.

## Implementasi
- lakukan import pada fungi `persist` dari `zustand/middleware`
```jsx
import { persist } from 'zustand/middleware'
```

- masukan state pada fungsi `persist()` 
```jsx
todoState = persist(todoState)
```

- tambahkan konfigurasi 
```jsx
todoState = persist(todoState, {name : "todoStore"}) 
```
*menambah sebuah konfigurasi nama pada state ketika tersimpan pada localStorage*

Selain `name`, ada beberapa opsi konfigurasi umum pada `persist` yang harus ada, antara lain:

1.  `getStorage`: digunakan untuk menentukan tipe penyimpanan yang digunakan, seperti `localStorage`, `sessionStorage`, atau custom storage.
```jsx
todoState = persist(todoState, {name: "todoStore", getStorage: () => sessionStorage})
```
2.  `onRehydrate`: digunakan untuk menentukan fungsi yang akan dijalankan setelah data berhasil di-rehydrate dari storage. Fungsi ini menerima parameter `state`, yang berisi data state yang telah di-rehydrate.
```jsx
todoState = persist(todoState, {
  name: "todoStore",
  onRehydrate: (state) => console.log("state rehydrated:", state)
})
```
3.  `version`: digunakan untuk menentukan versi state. Jika versi state berubah, maka data state yang lama akan dihapus dan digantikan dengan state yang baru.
```jsx
todoState = persist(todoState, {
  name: "todoStore",
  version: 2
})
```
4.  `whitelist`: digunakan untuk menentukan properti state mana yang ingin disimpan di storage. Properti yang tidak termasuk dalam daftar `whitelist` akan diabaikan.
```jsx
todoState = persist(todoState, {
  name: "todoStore",
  whitelist: ["todoList"]
})
```
5.  `blacklist`: kebalikan dari `whitelist`, digunakan untuk menentukan properti state mana yang tidak ingin disimpan di storage. Properti yang termasuk dalam daftar `blacklist` akan diabaikan.
```jsx
todoState = persist(todoState, {
  name: "todoStore",
  blacklist: ["loading"]
})
```
6.  `serialize`: digunakan untuk menentukan fungsi serialisasi khusus jika diperlukan.
```jsx
import { serialize } from "msgpack-lite";

todoState = persist(todoState, {
  name: "todoStore",
  serialize: (data) => serialize(data)
})
```
7.  `deserialize`: digunakan untuk menentukan fungsi deserialisasi khusus jika diperlukan.
```jsx
import { deserialize } from "msgpack-lite";

todoState = persist(todoState, {
  name: "todoStore",
  deserialize: (data) => deserialize(data)
})
```

