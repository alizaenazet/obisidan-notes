dengan menggunakan framework `zustand` maka state akan dapat diakses tanpa melalui props komponen seperti memanggil sebuah hook.
state yang dilakukan seperti hook disebut pula dengan `custome hook` , dimana dapat membuat hook sesuai kebutuhan dari mulai nama isi dan prilaku hooks.

## Membuat store
- Membuat file format `js` 
contoh : `store.js`
- import fungsi `create` pada zustand
```jsx
import create from 'zustand'i
```

- membuat varibel function
```jsx
const myStore = create((set) = ({
	 // isi store
}))
```
*`myStore` adalah custome hook *
`create` meminta memiliki 1 argumen untuk mengelola state

- menentukan isi pada hook
pada contoh berikut sebuah hook `storeTodo` berisikan 2 properties berisikan `todoList` menyimpan array beberapa *todo* dan `setTodo` fungsi akan dipanggil untuk melakukan perubahan pada array properti `todoList`, berikut contohnya :
```jsx
const storeTodo = create((set)=>({
todoList : [`mandi`, `futsal`],
addTodo : (todo) =>
set((state) => ({todoList : [...state.todoList, todo ]})),
}))
```

- export hooks
```jsx
export {storeTodo}
```

## Menggunaka store
- Import hook pada file 
```jsx
import myStore from "./storePath"
```

- menggunakan properties pada hook
pada contoh akan berkaitan pada contoh sebelumnya [[Create state#Membuat store]]

### *read* pada properties hook
```jsx
const todoList = storeTodo(state => state.todoList)
```
*array pada properties `todoList` akan mengisi nilai pada variabel `todoList` pada fungsi*

### pemanggilan fungsi properties hook
```jsx
const todo = storeTodo(state => state.addTodo)
```
*varibael `todo` akan digunakan untuk melakukan penambahan pada array `todoList`*

### contoh penggunaan 

**Read** pada properti hook
```jsx
import {storeTodo} from "../store"

export default function TodoList(){
const todoList = storeTodo(state => state.todoList)

	const todo = () => {
		
		return(
		<ul>
		{todoList.map(todo => <li key={todo}>{todo}</li>)}
		</ul>
		)
	}

return (

<div>
<h2>TodoList : </h2>
{todo()}
</div>

)
}
```

## Multiple store

```jsx
import create from 'zustand';

const storeTeman = create((set)=>({
people : [`Budi`, `Anton`],
addPerson : (person) =>
set((state) => ({people : [...state.people, person ]})),
}))
  

const storeTodo = create((set)=>({
todoList : [`mandi`, `futsal`],
addTodo : (todo) =>
set((state) => ({todoList : [...state.todoList, todo ]})),
}))

export{storeTeman, storeTodo}
```

penggunaan hook akan sama seperti masing masing hook sesuai dengan fungsi masing masing hook state

## Contoh kasus :

melakukan **Read and Write** pada 2 state yang berbeda 
