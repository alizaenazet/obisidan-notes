`useQuery()` adalah sebuah fungsi disediakan oleh Tanstack Query untuk melakukan pengambilan data dari server atau memproses data di sisi klien pada aplikasi React. Fungsi `useQuery()` digunakan untuk melakukan query pada data, dan mengembalikan hasil query dalam bentuk objek yang berisi data dan informasi tentang status query. 

Dalam penggunaannya, `useQuery()` membutuhkan dua buah argumen, yaitu `queryKey` dan `queryFn`.
`queryKey` adalah identifier untuk kueri tersebut, sedangkan `queryFn` adalah fungsi yang akan dieksekusi untuk mengambil data dari server atau memproses data di sisi klien.

## Pembahasan
1. Implementasi dasar menggunakan fungi `useQuery()` [[useQuery()#Implementasi]]
2. `queryKey` argumen wajib ke-1 pada fungsi `useQuery()` [[useQuery()#queryKey]]
3. `queryFn` argumen wajib ke-2 pada funsgi `useQuery()` [[useQuery()#queryFn]]
4. peroperti pada fungsi `useQuery()` [[useQuery()#Properti]]
## Implementasi 
- Import fungsi `useQuery` dari `"@tanstack/react-query"`
```jsx
import { useQuery } from "@tanstack/react-query"
```

- deklarasi didalam fungsi
```jsx
const exQueryFunc = useQuery({
// queryKey
//queryFn

})
```

## queryKey
Untuk menjalankan fungsi `useQuery` dengan benar, kita harus memberikan array sebagai key yang memuat informasi yang cukup untuk mengidentifikasi query. Ada beberapa informasi yang umumnya diberikan pada array key, yaitu:

Berikut ini adalah contoh penggunaan array key pada fungsi `useQuery` :

- Nama dari query
```jsx
 useQuery({
 queryKey:["users"] 
 });
```
*pada array key menunjukan bahwa akan mengambil data dari `user`*.
jika kita ingin mengambil data tentang daftar user, kita dapat memberikan key dengan nama "users"

- Parameter dari query
```jsx
useQuery({
queryKey:["users", { name: "John" }] 
)};
```
Misalnya, jika kita ingin mengambil user yang memiliki nama "John", kita dapat memberikan key dengan nama "users" dan parameter "name=John":

- Informasi tambahan (opsional)
Misalnya, jika kita ingin mengambil data tentang todo yang berhubungan dengan user tertentu, kita dapat memberikan key dengan nama "todos" dan parameter "userId=1" 
```jsx
 useQuery({
 queryKey:["todos", { status: "completed" }] 
 });
```

- contoh : 
```jsx
useQuery({
queryKey: ["todos", { userId: 1 }, { status: "completed" }],
})
```
kita ingin mengambil data tentang todo yang berhubungan dengan user tertentu dengan parameter "userId=1" dan hanya data dengan status "completed" yang diambil. Dengan memberikan tiga isi pada array key, kita dapat mengidentifikasi query secara unik dan memastikan bahwa caching berjalan dengan benar.

## queryFn

Argumen kedua pada fungsi `useQuery` adalah `queryFn`, yang merupakan sebuah fungsi untuk mengambil data yang diperlukan oleh query.

Fungsi `queryFn` harus mengembalikan data atau Promise yang menghasilkan data. Saat pertama kali query dijalankan, `queryFn` akan dipanggil untuk mengambil data baru. Data yang diperoleh akan disimpan di dalam cache dan dapat digunakan kembali jika query tersebut dapat dijalankan lagi .

### cara penggunaan 
1. Bagian yang fungsi dapat digunakan [[useQuery()#queryFn#bagian fungsi (sering)]]
2. cara penulisan fungsi [[useQuery()#queryFn#cara penulisan fungsi]]


### bagian fungsi (sering)
- Contoh lengkap :
```jsx
const fetchUsers = async () => {
  const response = await fetch('https://example.com/users')
  
  const data = await response.json()
  
  return data
}```

- **Response**
 Objek `response` mengandung informasi yang dihasilkan oleh permintaan data. Objek `response` ini biasanya memiliki properti seperti `data`, `isLoading`, `isError`, `error`, dan sebagainya.
```jsx
 const response = await fetch('https://example.com/users')
```

- **Data**
Properti `data` menyimpan nilai data yang diperoleh dari hasil query. Nilai `data` ini dapat berupa objek, array, string, atau tipe data lainnya yang dikembalikan oleh server.
```jsx
const data = await response.json()
```

- **Return data**
Fungsi `queryFn` harus selalu mengembalikan data yang diinginkan sebagai return value. Nilai yang dikembalikan oleh fungsi ini akan disimpan di dalam properti `data` pada objek `response`.
```jsx
return data
```


### cara penulisan fungsi
- **Gunakan async/await**
 Sebaiknya gunakan async/await dalam fungsi queryFn karena dapat membuat kode lebih mudah dibaca dan lebih mudah dipahami.
```jsx
const fetchUsers = async () => {
  const response = await fetch('https://example.com/users')
  const data = await response.json()
  return data
}
```

- **Memisahkan fungsi untuk memudahkan testing**
Sebaiknya pisahkan fungsi queryFn menjadi fungsi terpisah untuk memudahkan testing dan memudahkan pemeliharaan kode.
```jsx
const fetchUsers = async () => {
  const response = await fetch('https://example.com/users')
  const data = await response.json()
  return data
}

const getUsers = () => {
  return useQuery('users', fetchUsers)
}
```

- **Memanfaatkan parameter**
 Gunakan parameter pada fungsi queryFn untuk membuatnya lebih fleksibel dan dapat digunakan kembali di berbagai kasus.
 ```jsx
 const fetchPosts = async (category) => {
  const response = await fetch(`https://example.com/posts?category=${category}`)
  const data = await response.json()
  return data
}
const getPosts = (category) => {
  return useQuery(['posts', category], () => fetchPosts(category))
}
```

- **Menggunakan memoization** 
Jika fungsi queryFn membutuhkan waktu yang lama untuk dieksekusi, sebaiknya gunakan memoization untuk menghindari pengambilan data yang berulang-ulang.

```jsx
import { useMemo } from 'react'

const fetchUsers = async () => {
  const response = await fetch('https://example.com/users')
  const data = await response.json()
  return data
}

const getUsers = () => {
  const usersQuery = useQuery('users', fetchUsers)
  const memoizedUsers = useMemo(() => usersQuery.data, [usersQuery.data])
  return { ...usersQuery, data: memoizedUsers }
}
```

## Properti
properti akan menghasilkan nilai ketika fungsi `useQuery()` dijalankan seperti boolean, data, error dsb.

Berikut adalah penjelasan mengenai properti pada `postQuery` beserta contoh penggunaannya :

- `data`
properti ini berisi data hasil query yang berhasil dimuat. Contohnya, ketika data berhasil dimuat, kita bisa menampilkan data tersebut sebagai berikut:
```jsx
return (
  <ul>
    {postQuery.data.map((post) => (
      <li key={post.id}>{post.title}</li>
    ))}
  </ul>
);
```

- `isLoading` 
properti ini menunjukkan apakah query sedang dalam proses loading atau tidak. Contohnya, ketika query sedang memuat data, kita bisa menampilkan pesan loading sebagai berikut:
```jsx
if (postQuery.isLoading) {
  return <p>Loading...</p>;
}
```

- `isError`
 properti ini menunjukkan apakah terdapat kesalahan pada query atau tidak. Contohnya, ketika terjadi kesalahan pada query, kita bisa menampilkan pesan error sebagai berikut:
 ```jsx
 if (postQuery.isError) {
  return <p>Error: {postQuery.error.message}</p>;
}
```

- `status`
properti ini menunjukkan status dari query. Ada beberapa nilai yang mungkin ditampilkan, seperti `idle`, `loading`, `error`, dan `success`. Contohnya, kita bisa menampilkan status query sebagai berikut:
```jsx
    <p>Status: {postQuery.status}</p>
```

- `refetch`
```jsx
<button onClick={() => postQuery.refetch()}>Refresh</button>
```

