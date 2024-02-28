*Effect* memungkinkan untuk menjalankan *code* setelah terjadinya rendering komponent, berbeda dengan halnya [[Responding to event]] dimana dia menjalankan ketika terjadi interaksi, itu tidak berlaku pada cara kerja *effect*, seperti *chat room* yang harus terkoneksi secara langsung saat ditampilkan. Dengan begitu *Effect* akan dijalankan ketika komponen terkait dirender.

## Membuat sebuah useEffect

### 3 Tahap membuat sebuah useEffect
- **Deklarasi sebuah *Effect***. secara *default* akan berjalan setiap *render*.[[Intro to useEffect#Deklarasi sebuah *Effect*]]
- **Spesifik cara kerja *Effect***. kebanyak *Effect* hanya akan dijalankan apabila dibutuhkan saja daripada setiap saat render, seperti animasi *fade-in* pada sebuah komponen hanya terpicu ketika komponen muncul dsb. [[Intro to useEffect#Spesifik cara kerja Effect]]
- **Bersihkan *Effect* (opsional)**. beberapa kasus *Effect* membutuhkan cara stop, undo dan membersihkan *Effect* itu sendiri, seperti "connect" membutuhkan "disconnect", "subscribe" membutuhkan "unsubscribe", dan "fetch" membutuhkan "cancel" atau "ignore" [[Intro to useEffect#Membersihkan *Effect*]]

### Deklarasi sebuah *Effect*

- Import `useEffect()` pada `react`
```jsx
import { useEffect } from 'react';
```

- Panggil pada sisi ter-atas pada fungsi sebuah komponen 
```jsx
function MyComponent() {
useEffect(() =>{
	//kode akan dijalankan setiap merender
})
}
return <div />;
```
setiap komponen dirender maka akan dilakukan update dan menjalan kode didalam `useEffect` , hal itu disebut juga dengan "`useEffect` **Delay**"  keadaan dimana sebuah kode berjalan hingga ditampilkan.

- Contoh penggunaan 
sebagai contoh akan melakukan sinkronisasi dengan sistem external menggunakan `useEffect`.  Melakukan penggunaan dengan sebuah komponen custom `<VideoPlayer>` dan memanfaat sebuah DOM node `video`, dengan begitu dapat menampilkan sebuah video dan melakukan `play()` dan `pause()` pada video tersebut, berikut hasil contoh :
![[sandbox (6).html]]

berikut cara penggunaan `useEffect` untuk menggunakan komponen custome `<VideoPlayer>` :

```jsx
function VideoPlayer({ src, isPlaying }) {  

// TODO: do something with isPlaying  

return <video src={src} />; // Dom node 
}
```
*komponen `VideoPlayer` memiliki 2 props `src` adalah video yang dilampirkan dan `isPlaying` adalah kondisi video tersebut *

komponen `<VideoPlayer>` memiliki props untuk menentukan kondisi video(play/pause).
```jsx
<VideoPlayer isPlaying={isPlaying} />;
```
*props `isPlaying` bernilai boolean yang akan menentukan kondisi pada video*

dengan begitu maka diperlukan sinkronisasi nilai props `isPlaying` sebagai penentu apakah video dalam kondisi `play()` atau `pause()` pada kasus ini nilai *false* sehingga kondisi video `pause()` sebagai nilai *default*.

**Perlu difahami :**
peran penting `useEffect` pada kondisi seperti ini adalah ketika saat komponen `VideoPlayer` dirender maka akan secara langsung melakukan input `src` dari video yang akan ditampilkan, sehingga ketika tidak menggunakan `useEffect` maka akan bernilai `null` dan terjadi **Error**.

```jsx
function VideoPlayer({ src, isPlaying }) {  
const ref = useRef(null);  

useEffect(() => {  //penggunaan useEffect
if (isPlaying) {  
ref.current.play();  
} else {  
ref.current.pause();  
}  

});  
return <video ref={ref} src={src} loop playsInline />;  
}
```
*ketika komponen dirender maka akan berjalan sekaligus dan melakukan `return` *
Dengan membungkus pembaruan DOM dalam sebuah Efek, Anda membiarkan React memperbarui layar terlebih dahulu. Kemudian Efek Anda berjalan.

setidaknya terdapat 3 tahap saat komponen dirender :
- React akan memperbarui layar, memastikan tag `<video>` ada di DOM dengan props yang tepat.
- React menjalankan *Effect* pada komponen
- Effect akan memanggil `play()` atau `pause()` bergantung pada nilai isPlaying.

**Hasil contoh :**
<iframe src="https://codesandbox.io/embed/busy-antonelli-ipn68f?fontsize=14&hidenavigation=1&module=%2FApp.js&theme=dark"
     style="width:100%; height:500px; border:0; border-radius: 4px; overflow:hidden;"
     title="busy-antonelli-ipn68f"
     allow="accelerometer; ambient-light-sensor; camera; encrypted-media; geolocation; gyroscope; hid; microphone; midi; payment; usb; vr; xr-spatial-tracking"
     sandbox="allow-forms allow-modals allow-popups allow-presentation allow-same-origin allow-scripts"
   ></iframe>


### Spesifik cara kerja Effect
- pada saat tertentu ingin sebuah *Effect* hanya dijalankan pada saat dibutuhkan saja 
- pada keadaan tertentu sebuah *Effect* hanya akan dijalankan seperti animasi *fade-in* sebuah komponen hanya dapat diputar sekali saat komponen muncul untuk pertama kali.

dengan keadaan tertentu maka hars me-spesifikan cara kerja sebuah *Effect*.
untuk mendemonstrasikan dengan menambahkan state pada `useEffect()` didalam komponen `<VideoPlayer` [[Intro to useEffect#Deklarasi sebuah *Effect*]], sehingga menjadi seperti berikut :
```jsx 
import { useState, useRef, useEffect } from "react";

function VideoPlayer({ src, isPlaying }) {
const ref = useRef(null);

useEffect(() => {
if (isPlaying) {
console.log("Calling video.play()");
ref.current.play();
} else {
console.log("Calling video.pause()");
ref.current.pause();
}
});

return <video ref={ref} src={src} loop playsInline />;
} 

export default function App() {

const [isPlaying, setIsPlaying] = useState(false);
const [text, setText] = useState("");
return (
<>

<label>
<hr />
text input : <p>{text} </p>
<hr />
</label>

<input value={text} onChange={(e) => setText(e.target.value)} />

<button onClick={() => setIsPlaying(!isPlaying)}>
{isPlaying ? "Pause" : "Play"}
</button>
<VideoPlayer

isPlaying={isPlaying}
src="https://interactive-examples.mdn.mozilla.net/media/cc0-videos/flower.mp4"
/>

</>
);
}
```
*ekspektasi : melakukan print pada console ketika me-klik tombol kondisi video*

<iframe src="https://codesandbox.io/embed/admiring-jerry-jqktn4?expanddevtools=1&fontsize=14&hidenavigation=1&theme=dark"
     style="width:100%; height:500px; border:0; border-radius: 4px; overflow:hidden;"
     title="admiring-jerry-jqktn4"
     allow="accelerometer; ambient-light-sensor; camera; encrypted-media; geolocation; gyroscope; hid; microphone; midi; payment; usb; vr; xr-spatial-tracking"
     sandbox="allow-forms allow-modals allow-popups allow-presentation allow-same-origin allow-scripts"
   ></iframe>
   > *Realita: **Effect** pada komponen video bekerja setiap kali input berubah*

**Perlu difahami :**
- terdapat element `input` akan mengubah dan memicu parent component `App` sehingga akan terjadi render ulang pada komponen parent yang diikuti child componentnya. 
- setiap `input` terpacu maka saat itu juga *parent komponen* akan ter-render ulang sehingga komponen `button` yang berisikan `usaEffect()` akan berjalan pada setiap randernya sebagaimana sifat default *Effect*.
- element yang memicu `useState` akan menjadikan komponen melakukan render ulang maka `useEffect` pada komponen didalamnya agak terpicu pula.

yang perlu ditangani adalah bagaimana 2 komponen dengan 2 tipe hook yang berbeda dapat bekerja secara terpisah dan tidak berdampak terutama pada komponen menggunakan `useEffect` dimana pada kasus contoh seharusnya akan melakukan print pada console saat setiap tombol terjadi interaksi(klik), namun nyatanya setiap kali input berubah maka element dengan `useEffect` akan bekerja.

**Menambahkan parameter pada `useEffect()`**
parameter ke-2 pada `useEffect` berupa `Array[]` dimana array dapat berisi nilai kondisi yang berubah saat terjadi interaksi pada komponen, contoh : `isPlaying` 
```jsx
useEffect(() => {  
// ...  
}, []);
```

```jsx
useEffect(() => {  

if (isPlaying) { // It's used here...  

// ...  
} else {  

// ...  
}  

}, [isPlaying]); // ...so it must be declared here!
```
dengan menambahkan `array` pada parameter ke-2 `useEffect` maka mengatakan pada React bahwa ketika terjadi render komponen apabila selama nilai dari `isPlaying` sama dengan nilai pada `array` maka tidak perlu menjalnkan kode didalam `useEffect`. 

berikut hasil sesuai tujuan :
<iframe src="https://codesandbox.io/embed/nostalgic-ardinghelli-bpsndm?expanddevtools=1&fontsize=14&hidenavigation=1&theme=dark"
     style="width:100%; height:500px; border:0; border-radius: 4px; overflow:hidden;"
     title="nostalgic-ardinghelli-bpsndm"
     allow="accelerometer; ambient-light-sensor; camera; encrypted-media; geolocation; gyroscope; hid; microphone; midi; payment; usb; vr; xr-spatial-tracking"
     sandbox="allow-forms allow-modals allow-popups allow-presentation allow-same-origin allow-scripts"
   ></iframe>
   >
   
React tidak akan menjalankan kode pada *Effect* ketika semua parameter `useEffect()` memiliki nilai yang sama dengan nilai sebelum terjadi render ulang.

Perilaku tanpa ketergantungan parameter dan dengan ketergantungan parameter pada `array[]` kosong berbeda:
```jsx
useEffect(() => {  
// This runs after every render  
});   

useEffect(() => {  
// This runs only on mount (when the component appears)  
}, []);  

useEffect(() => {  
// This runs on mount *and also* if either a or b have changed since the last render  
}, [a, b]);
```


### Membersihkan *Effect* 

keadaan dimana diharuskan mengembalikan sebuah nilai seperti semula, seperti `chatRoom` komponen ketika ditampilkan akan melakukan koneksi dan akan memutus koneksi ketika komponen tidak ditampilkan kembali.

```jsx
useEffect(() => {  
const connection = createConnection();  
connection.connect();  
}, []);
```
kode pada `useEffect` akan selalu terkoneksi walaupun ditidak ditampilkan lagi namun ketika menampilkan ulang maka dia akan membuat koneksi baru tanpa menutup koneksi yang lama.

pada contoh berikut dimana ketika terjadi sebuah upaya koneksi maka akan melakukan print pada console
<iframe src="https://codesandbox.io/embed/serene-rumple-191rb1?expanddevtools=1&fontsize=14&hidenavigation=1&theme=dark"
     style="width:100%; height:500px; border:0; border-radius: 4px; overflow:hidden;"
     title="serene-rumple-191rb1"
     allow="accelerometer; ambient-light-sensor; camera; encrypted-media; geolocation; gyroscope; hid; microphone; midi; payment; usb; vr; xr-spatial-tracking"
     sandbox="allow-forms allow-modals allow-popups allow-presentation allow-same-origin allow-scripts"
   ></iframe>
   > *pada console terdapat angka `2` menunjukan 1 print sama dengan dilakukan sebanyak 2x *
   
yang seharusnya terjadi adalah sebelum terjadi koneksi untuk ke-2xnya maka harus terjadi pemutusan koneksi terlebih dahulu sebelum terjadi koneksi kembali , maka seharusnya hasil console adalah :
```shell
✅ Connecting...
❌ Disconnected.
✅ Connecting...
```

agar berjalan sesuai harapan maka dapat melakukan return dengan kode yang melakukan pemutusan pada koneksi, seperti berikut :

```jsx
useEffect(() => {  
const connection = createConnection();  
connection.connect();  

return () => {  
connection.disconnect();  
};  

}, []);
```

maka akan menghasilkan output yang sesuai, seperti berikut :
```
1.  `"✅ Connecting..."`
2.  `"❌ Disconnected."`
3.  `"✅ Connecting..."`
```

berikut contoh lengkap :
<iframe src="https://codesandbox.io/embed/beautiful-panka-4womvr?expanddevtools=1&fontsize=14&hidenavigation=1&theme=dark"
     style="width:100%; height:500px; border:0; border-radius: 4px; overflow:hidden;"
     title="beautiful-panka-4womvr"
     allow="accelerometer; ambient-light-sensor; camera; encrypted-media; geolocation; gyroscope; hid; microphone; midi; payment; usb; vr; xr-spatial-tracking"
     sandbox="allow-forms allow-modals allow-popups allow-presentation allow-same-origin allow-scripts"
   ></iframe>
   
