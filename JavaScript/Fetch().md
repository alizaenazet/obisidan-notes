Fungsi `fetch()` merupakan fungsi bawaan dari JavaScript yang digunakan untuk melakukan permintaan HTTP pada sebuah URL tertentu.

Berikut adalah beberapa parameter penting yang ada pada fungsi `fetch()` dan penjelasannya:

1.  `url`: Parameter ini merupakan URL tempat mengirim permintaan. Contohnya: `"https://api.example.com/data"`
2.  `method`: Parameter ini menentukan metode HTTP yang akan digunakan. Biasanya digunakan untuk mengirim permintaan dengan metode GET, POST, PUT, atau DELETE. Contohnya: `"POST"`
3.  `headers`: Parameter ini merupakan objek asosiatif yang berisi informasi tambahan yang akan dikirimkan bersama permintaan. Contohnya: `{ "Content-Type": "application/json" }`
4.  `body`: Parameter ini berisi data yang akan dikirimkan bersama permintaan. Biasanya digunakan untuk mengirim data dalam format JSON. Contohnya: `JSON.stringify({ username: "johndoe", password: "123456" })`

```jsx
fetch('https://example.com/api/users', {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json'
  },
  body: JSON.stringify({
    name: 'John Doe',
    email: 'johndoe@example.com',
    password: '123456'
  })
})
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error(error))

```

Dalam contoh di atas, kita melakukan permintaan HTTP POST ke URL `https://example.com/api/users` dengan mengirimkan data JSON yang telah di-`stringify` pada properti `body` dari opsi permintaan. Setelah permintaan berhasil, kita mengambil respons HTTP menggunakan method `json()` dan menampilkan data yang diterima melalui `console.log()`. Jika terjadi kesalahan pada permintaan, kita menangkap dan menampilkan pesan error pada `console.error()`.