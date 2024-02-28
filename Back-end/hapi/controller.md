berisikan file yang mengatur logika bisnis yang berkaitan dengan penanganan permintaan (request) dari API dan pengembalian respons (response) ke pengguna. Di dalam file tersebut, Anda akan menemukan fungsi-fungsi yang mengimplementasikan logika bisnis spesifik untuk setiap fitur atau entitas dalam aplikasi Anda.

Berikut adalah beberapa contoh fungsi yang mungkin ada dalam file controller:

1. Fungsi untuk mengambil data: Misalnya, fungsi `getProducts` yang mengambil daftar produk dari database dan mengirimkannya sebagai respons kepada pengguna.
2. Fungsi untuk membuat data baru: Misalnya, fungsi `createOrder` yang menerima data pesanan dari pengguna, memvalidasi input, menyimpan pesanan ke database, dan mengirim respons dengan pesanan yang berhasil dibuat.
3. Fungsi untuk memperbarui data: Misalnya, fungsi `updateUser` yang menerima data pembaruan pengguna, memvalidasi input, mengupdate entitas pengguna yang sesuai di database, dan mengirim respons dengan pengguna yang berhasil diperbarui.
4. Fungsi untuk menghapus data: Misalnya, fungsi `deleteProduct` yang menerima ID produk yang akan dihapus, melakukan validasi dan menghapus produk yang sesuai dari database, dan mengirim respons yang sesuai.


```jsx
async function getNotes(userId) {

const [results, metadata] = await sequelize.query(`SELECT * FROM note WHERE user_id=${userId}`)

if (results.length > 0) {
console.log(results);
return [...results]
}
return false
}
```

```jsx
const sequelize = require('../config/db');

  

async function getNotes(userId) {
const [results, metadata] = await sequelize.query(`SELECT * FROM note WHERE user_id=${userId}`)

if (results.length > 0) {
console.log(results);
return [...results]
}

return false
}

module.exports = {
getNotes
}
```
