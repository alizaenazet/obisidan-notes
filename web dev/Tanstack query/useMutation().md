`useMutation` adalah hooks yang digunakan untuk membuat sebuah mutation (create, update, atau delete data) pada API. Dalam penggunaannya, kita bisa menggunakan method HTTP POST, PUT, atau DELETE.

1. **Creat** [[useMutation()#Creat]]
2. **Update** [[useMutation()#Update]]
3. **Delete** [[useMutation()#Delete]]

## Creat

- import `useMutation` dari `"@tanstack/react-query"`
```jsx
import {useMutation} from "@tanstack/react-query"
```

- Buat fungsi yang akan dijalankan sebagai mutationFn ketika request dipanggil. Fungsi ini menerima parameter berupa data yang akan dikirimkan ke API. Fungsi ini juga harus mengembalikan hasil request. Contoh implementasi fungsi untuk membuat post request:
```jsx
const createUser = async (data) => {
  const response = await fetch('/api/users', {
    method: 'POST',
    headers: {
      'Content-Type': 'application/json',
    },
    body: JSON.stringify(data),
  });

  return response.json();
};
```
penjelasan terkait isi pada fungsi `fetch` : [[Fetch()]] 

-  Gunakan `useMutation` dengan memanggil fungsi yang telah dibuat pada langkah sebelumnya sebagai `mutationFn`. Berikut contoh penggunaannya:
```jsx
const [createUserMutation, { isLoading, error, data }] = useMutation(createUser);
```
*`useMutation` akan mengembalikan nilai saat dijalankan dan akan ditampung pada beberapa porertis yang tersedia seperti `isLoading`*, `error`, `data` Dsb

- Panggil fungsi `createUserMutation` yang telah dibuat pada langkah 3 dan masukan data yang ingin dikirim ke API. Berikut contoh penggunaannya:
```jsx
const handleCreateUser = async () => {
  const data = {
    name: 'John Doe',
    email: 'john.doe@example.com',
    password: 'password',
  };

  await createUserMutation(data);
};
```
`handleCreateUser` adalah sebuah fungsi yang dipanggil ketika user ingin membuat user baru. Fungsi ini memanggil `createUserMutation` dan mengirimkan data user sebagai parameter.

- Handle response dari request yang dikirimkan. Properti `data` dari `useMutation` akan mengembalikan data yang diterima dari server. Berikut contoh penggunaannya:
```jsx
if (data) {
  console.log('User created: ', data);
}
```
`console.log` akan mencetak data user yang telah berhasil dibuat jika request berhasil.


## Contoh lengkap :

```jsx
import { useMutation } from 'react-query'

function AddTodo() {
  const [text, setText] = useState('')
  const mutation = useMutation((newTodo) => fetch('/api/todos', {
    method: 'POST',
    headers: { 'Content-Type': 'application/json' },
    body: JSON.stringify({ text: newTodo }),
  }))
  
  const handleSubmit = (e) => {
    e.preventDefault()
    mutation.mutate(text)
    setText('')
  }

  return (
    <form onSubmit={handleSubmit}>
      <input type="text" value={text} onChange={(e) => setText(e.target.value)} />
      <button type="submit">{mutation.isLoading ? 'Adding...' : 'Add Todo'}</button>
    </form>
  )
}

```

1.  Pertama-tama kita memanggil `useMutation` dari `react-query` untuk membuat fungsi `mutation` yang akan digunakan untuk melakukan request pada API. Fungsi `mutation` ini akan mengambil satu parameter, yaitu data yang akan dikirim ke API.
    
2.  Pada contoh di atas, kita membuat form untuk menambahkan todo dengan menggunakan input dan button. Ketika form di-submit, fungsi `handleSubmit` akan dijalankan.
    
3.  Fungsi `handleSubmit` akan mengambil nilai dari input `text`, lalu memanggil fungsi `mutation.mutate` dengan parameter `text`. Hal ini akan memicu `mutation` untuk melakukan request ke API dengan data yang dikirimkan.
    
4.  Selama `mutation` sedang melakukan request, nilai dari `mutation.isLoading` akan menjadi `true`. Kita bisa menggunakan nilai ini untuk menampilkan pesan loading pada button.
    
5.  Jika request berhasil, nilai dari `mutation.isSuccess` akan menjadi `true`. Kita bisa menggunakan nilai ini untuk melakukan aksi tertentu, seperti meng-update UI atau melakukan redirect.
    
6.  Jika request gagal, nilai dari `mutation.isError` akan menjadi `true`. Kita bisa menggunakan nilai ini untuk menampilkan pesan error pada UI.
    
7.  Kita juga bisa menambahkan `onSuccess` dan `onError` pada `useMutation` untuk menentukan aksi yang akan dijalankan saat request berhasil atau gagal. Misalnya:
```jsx
const mutation = useMutation((newTodo) => fetch('/api/todos', {
  method: 'POST',
  headers: { 'Content-Type': 'application/json' },
  body: JSON.stringify({ text: newTodo }),
}), {
  onSuccess: () => {
    console.log('Todo added!')
    // Do something else, like update UI or redirect
  },
  onError: (error) => {
    console.log('Failed to add todo:', error)
    // Do something else, like display error message
  },
})
```
Dengan begitu, kita bisa menentukan aksi yang berbeda-beda tergantung pada hasil dari request.

## Creat

```js
async function CreatPost({dataNumb,title, comment}) {
return axios
.post(`http://localhost:3000/datas${dataNumb}`,{
title,
comment,
id: crypto.randomUUID().subString(0, 5) // mengambil nilai dari angka ke-0 hingga ke 5
}).then(res => res.data )
}
```
*fungsi `CreatPost` akan digunakan pada file element *

```jsx  
import { useRef } from "react"
import { useMutation, useQueryClient } from "@tanstack/react-query"
import {CreatPost} from "./api/datas"


function PostListAdd({dataNumb}) {
const titleRef = useRef()
const commentRef = useRef()
const queryClient = useQueryClient()

const addListMutation = useMutation({
mutationFn : CreatPost, 
onSuccess : () => {
queryClient.invalidateQueries([`datas${dataNumb}`]) //melakukan pembaruan pada tampilan sesuai data yang telah ditambah
}
/**
1.Pada kode di atas, hook `useMutation` digunakan untuk melakukan operasi create data, dengan menggunakan fungsi `CreatPost` yang didefinisikan pada file `api/datas.js`.

Hasil dari operasi create ini, akan diproses pada fungsi `onSuccess` pada properti `addListMutation`, dimana fungsi ini akan dijalankan jika operasi create berhasil dilakukan. Pada kode di atas, hasilnya adalah memanggil fungsi `invalidateQueries` pada `queryClient`, sehingga cache data yang sudah ada akan dihapus dan data baru akan diambil dari backe
**/

})

function handleSubmit(e) {
e.preventDefault()
addListMutation.mutate({
dataNumb,
title : titleRef.current.value,
comment : commentRef.current.value
})
}

/**
2.  Pada saat user menekan tombol submit pada form, fungsi `handleSubmit` akan dijalankan. Fungsi ini akan memanggil fungsi `mutate` pada `addListMutation`, dimana `mutate` adalah sebuah fungsi dari `useMutation` yang akan mengirimkan data yang sudah diisi oleh user pada form, yaitu `dataNumb`, `title`, dan `comment` ke backend melalui fungsi `CreatPost`.
**/

return (

<>

<form onSubmit={handleSubmit}>
<input type="text" ref={titleRef}/> Title input
<input type="text" ref={commentRef}/> comment input
<button type="submit">Add new List</button>
</form>


</>

)
}
/**
3.  Pada form terdapat dua input yang memiliki ref `titleRef` dan `commentRef`. `useRef` digunakan untuk mengambil nilai dari kedua input tersebut ketika tombol submit ditekan oleh user. Nilai input tersebut akan digunakan sebagai data yang akan dikirim ke backend melalui `CreatPost`.
**/

export default PostListAdd
```


## Update

```jsx
async function UpdateDatas({dataNumb, id, title, comment}) {

return axios.put(`http://localhost:3000/${dataNumb}/${id}`, {title, comment})
.then(res => res.data)
}
```
*fungsi `UpdateDatas` akan digunakan pada file element *

- definisikan komponen `UpdateListData` sebagai sebuah functional component yang memiliki dua properti yaitu `dataNumb` dan `id`.
```jsx
function UpdateListData({ dataNumb, id }) {
  // ...
}
```

- gunakan hook `useQueryClient` untuk mendapatkan instance `queryClient` yang nantinya akan digunakan untuk memperbarui cache pada server setelah melakukan update data.
```jsx
const queryClient = useQueryClient()
```

- Gunakan hook `useMutation` untuk mendefinisikan `updateMutationData`, sebuah mutation function yang akan dipanggil ketika form submit
```jsx
const updateMutationData = useMutation({
  mutationFn: UpdateDatas,
  onSuccess: queryClient.invalidateQueries([`${dataNumb}`])
})
```

- Dalam `updateMutationData`, `mutationFn` diset ke fungsi `UpdateDatas` yang kemudian akan dijalankan ketika form submit. Kemudian, `onSuccess` di-set ke fungsi `queryClient.invalidateQueries([`${dataNumb}`])`, yang akan memperbarui cache server ketika update data berhasil dilakukan.
```jsx
mutationFn: UpdateDatas,
onSuccess: queryClient.invalidateQueries([`${dataNumb}`])
```

- Di dalam komponen, gunakan fungsi `handleUpdateData` untuk menangani form submit. Fungsi ini akan mengambil value dari input field `titleInput` dan `comment`, lalu menjalankan `updateMutationData.mutate()` untuk melakukan update data dengan memanggil `UpdateDatas`.
```jsx
const handleUpdateData = (e) =>{
  e.preventDefault()
  updateMutationData.mutate({
    dataNumb,
    id,
    title : e.target.elements.titleInput.value,
    comment : e.target.elements.comment.value
  })
}
```

- tampilkan sebuah form dengan input fields `titleInput` dan `comment`, dan sebuah tombol `update data`. Ketika form submit, maka `handleUpdateData` akan dipanggil dan `updateMutationData.mutate()` akan dijalankan untuk melakukan update data.
```jsx
<form onSubmit={handleUpdateData}>
  title <input type="text" name="titleInput"></input> 
  comment <input type="text" name="comment"></input>
  <button type="submit">update data</button>
</form>
```

- **Contoh lengkap :**
```jsx
import { useMutation, useQueryClient } from "@tanstack/react-query";
import { UpdateDatas} from './api/datas'

function UpdateListData({dataNumb, id}) {

const queryClient = useQueryClient()
const updateMutationData = useMutation({
mutationFn: UpdateDatas,
onSuccess : queryClient.invalidateQueries([`${dataNumb}`])
})

const handleUpdateData = (e) =>{
e.preventDefault()

updateMutationData.mutate({
dataNumb,
id,
title : e.target.elements.titleInput.value,
comment : e.target.elements.comment.value

})

}  

return (

<>

<form onSubmit={handleUpdateData}>
title <input type="text" name="titleInput"></input> comment <input type="text" name="comment"></input>
<button type="submit">update data</button>
</form>
</>

)
}

export default UpdateListData
```


## Delete
```jsx
async function DeteleDatas({dataId,dataNumb}) {
return axios
.delete(`http://localhost:3000/${dataNumb}/${dataId}`)
.then(res => res.data)
}
```
*fungsi `DeleteDatas` akan digunakan pada file element *

- Membuat functional component DeleteListsData yang menerima dua props, yaitu `dataNumb` dan `dataId`.
```jsx
function DeleteListsData({ dataNumb, dataId }) {...}
```

- Menginisialisasi useQueryClient hook yang akan digunakan untuk melakukan invalidasi cache setelah operasi hapus berhasil dilakukan.
```jsx
const queryClient = useQueryClient();
```

- Membuat useMutation hook yang akan digunakan untuk melakukan operasi hapus data pada API. Pada `useMutation` ini, disediakan dua parameter, yaitu `mutationFn` dan `onSuccess`. `MutationFn` merupakan fungsi yang akan dijalankan ketika operasi hapus dilakukan, sedangkan `onSuccess` merupakan fungsi yang akan dijalankan ketika operasi hapus berhasil dilakukan.
```jsx
const deleteDataMutatuon = useMutation({
  mutationFn: DeteleDatas,
  onSuccess: () => {
    queryClient.invalidateQueries([`${dataNumb}`]);
  },
});
```

- Membuat fungsi `handleDelete` yang akan dijalankan ketika tombol Delete ditekan. Fungsi ini akan memanggil fungsi mutasi `deleteDataMutation` dengan mengirimkan `dataId` dan `dataNumb` sebagai parameter.
```jsx
const handleDelete = (e) => {
  e.preventDefault();
  deleteDataMutatuon.mutate({
    dataId,
    dataNumb,
  });
};
```

- Mengembalikan tombol Delete yang ketika diklik akan menjalankan fungsi handleDelete
```jsx
return (
  <>
    <button onClick={handleDelete}>Delete</button>
  </>
);
```

```jsx
import { useMutation, useQueryClient } from "@tanstack/react-query";
import {DeteleDatas} from "./api/datas"  

function DeleteListsData({dataNumb,dataId}) {

const queryClient = useQueryClient()
const deleteDataMutatuon = useMutation({
mutationFn : DeteleDatas,
onSuccess : () => {

queryClient.invalidateQueries([`${dataNumb}`])
}
})

const handleDelete = (e) =>{
	e.preventDefault()
	deleteDataMutatuon.mutate({
	dataId,
	dataNumb,
	})
}

return(

<>
<button onClick={handleDelete}>Delete</button>
</>
	   
)
}

export default DeleteListsData
```

