pembahasan :
1. Pengertian state pada komponent [[intro to useState#Pengertian state]]
2. Membuat state sederhana [[intro to useState#Membuat State]]
3. Penggunaan state untuk melakukan perubahan pada komponen [[intro to useState#Penggunaan State]]
4. Contoh kasus state dengan mengambil data [[intro to useState#Contoh kasus:]]
5. Transisi pada materi Hooks dalam penggunaan `useState` [[intro to useState#Transisi menuju Hook]]

## Pengertian state
State pada React adalah sebuah objek yang merepresentasikan kondisi atau data dari suatu komponen pada sebuah waktu tertentu.

state berguna untuk menampung sebuah nilai yang akan berubah sebab sebuah aksi dari input maupun hal lainnya yang membuat sebuah nilai dari variabel berubah, sebab berubahnya sebuah nilai dari variabel maka tampilan akan diperbarui pula sesuai dengan nilai pada variabel tersebut. Contoh:
- terdapat sebuah list yang menyimpan beberapa nama
- me-klik `buy` akan menambahkan item keranjang
- terdapat sebuah kolom imput untuk menambah nama pada list
- tersedia sebuah tombol untuk melakukan submit nama tersebut
- ketika mengimput nama pada kolom dan melakukan submit pada tombol maka nilai akan berbubah pada saat itu juga tampilan akan diperbarui sehingga tampilan akan di-render ulang

omponen React perlu **"mengingat"** (memori) sesuatu.
Dalam React, memori komponen ini disebut sebagai state. State memungkinkan komponen untuk merepresentasikan perubahan data dan merender ulang tampilan secara dinamis tanpa harus refresh halaman secara keseluruhan.

## Membuat State
- tambahkan *state* variabel dengan melakukan import `useState` pada bagian atas file
```jsx
import {useState} from 'react';
```

State akan terdiri dari 2 variabel penyimpanan dan fungsi untuk melakukan perubahan pada variabel state
dengan memanggil `useState` maka React akan **mengingat** sesuatu pada komponen tersebut.
```jsx
const [count, setCount] = useState(0);
```
*Variabel `count` harus dirubah melalui `setCount`*

variabel `setCount` adalah sebuah fungsi untuk melakukan set pada `count` dan nilai pada `useState()` adalah nilai awal dari `count`.

### kenapa harus pakai fungsi `set` ?
ketika ingin melakukan perubahan pada nilai varibael maka wajib menggunakan `set` variabel tersebut sebab react tidak akan mendeteksi perubahan apabila tidak menggunakannya, dengan begitu agar tampilan dapat diperbarui selaras dengan nilai pada variabel maka wajib menggunakan fungsi `set`.

## Penggunaan State

```jsx
setCount(count + 1) // melakukan sebuah penambahan nilai pada `count`
```
*melalui `setCount` maka dapat dilakukan perubahan nilai pada variabel `count`*

### CRUD pada state

```jsx
const [count, setCount] = useState(0);
```
*contoh sebuah state*

**Creat**
Untuk membuat/menambahkan nilai pada `count`, kita dapat menggunakan setter yang telah dibuat.
```jsx
setCount(count + 1);
```

**Read**
Untuk membaca/mengambil nilai.
```jsx
count //langsung menggunakan pemanggilan pada variabel
```

**Update**
melakukan update pada `count` 
```jsx
setCount(20)
```

**Delete**
melakukan delete pada `count`
```jsx
setCount(count - 2)
```


### Penggunaan state pada function

```jsx

function tambahCount() {
setCount(count + 1);
}  

function resetCount() {
setCount(count - count);

}
```


## Contoh kasus:

- tambahkan *state* variabel dengan melakukan import `useState` pada bagian atas file
```jsx
import {useState} from 'react';
```
- buat state variabel 
```jsx
const [state, setState] = useState(0);
```
x
- aplikasikan state dengan komponen utama
berikut adalah contoh penggunaan state dimana terdapat state variabel berupa `[index,setIndex]`  dimana index akan berubah seiring `event` pada `button`. penggunaan `useState()` terdapat pada *event handler* `handleClick()`.

<iframe src="https://codesandbox.io/embed/upbeat-keldysh-0efc0f?fontsize=14&hidenavigation=1&module=%2FApp.js&theme=dark"
     style="width:100%; height:500px; border:0; border-radius: 4px; overflow:hidden;"
     title="upbeat-keldysh-0efc0f"
     allow="accelerometer; ambient-light-sensor; camera; encrypted-media; geolocation; gyroscope; hid; microphone; midi; payment; usb; vr; xr-spatial-tracking"
     sandbox="allow-forms allow-modals allow-popups allow-presentation allow-same-origin allow-scripts"
   ></iframe>

## Transisi menuju Hook
useState hooks digunakan untuk mengelola state pada functional component. Hooks tersebut memberikan kemampuan untuk menyimpan dan memperbarui nilai pada state, serta melakukan re-rendering pada komponen saat terjadi perubahan pada state. Dalam penggunaannya, useState mirip dengan state pada class component, namun dapat digunakan pada functional component tanpa harus mengubah komponen menjadi class. Dengan useState, React memungkinkan penggunaan state pada functional component dan membuatnya lebih mudah dan ringkas dalam penggunaannya

