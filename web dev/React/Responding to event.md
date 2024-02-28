Pembahasan :
1. How to basicly melakukan event handling [[Responding to event#How to (basic) ?]]
2. konsep dasar dalam penggunaan dan pembuatan komponen [[Responding to event#Komponen concept]]
3. melakukan umpan(*passing*) props *respon handler* pada komponent [[Responding to event#Passing props in event handlers]]
4. penamaan pada *even handler* dan penggunaan single mapun multiple interaction [[Responding to event#Penamaan Event handler Props]]
5. pengertian tentang *propagation* pada *event* dimana sebuah *event* dapat menjalar pada *event* component yang lebih tinggi [[Responding to event#Event propagation]]

Cara melakukan penanganan dengan respon pada saat yang ditentukan, contoh :
ingin **Tombol** melakukan mencetak teks pada console **ketika ditekan** ,
Tombol --> ketika ditekan --> mencetak teks pada 
**Objek** --> **Event** --> **Respond** .

![[Screenshot 2023-04-29 at 19.42.20.png]]

## How to (basic) ?

- buat fungsi untuk melakukan handle pada komponen dan impelentasi logic didalamnya
```jsx
function handleClick() {
    alert('You clicked me!');
  }
```
*membuat sebuah fungsi `handleClick()`  dan terdapat logic melakukan `alert()` didalamnya*

- Deklarasikan sebuah sub-komponen didalam fungsi komponen parrent
```jsx
 <button>
      Click me
    </button>
```
*pada element button mendelkarasikan fungsi pada props element `button` *

- tambahkan props pada sub-komponen (contoh: `onClick()`)
```jsx
 <button onClick={handleClick}>
      Click me
    </button>
```

- contoh penuh :
```jsx
export default function Button() {
  function handleClick() {
    alert('You clicked me!');
  }

  return (
    <button onClick={handleClick}>
      Click me
    </button>
  );
}

```

**hasil :**
![[sandbox (1).html]]

## Komponen concept
berikut adalah konsep dalam pembuatan dan pemakaian komponen agar dapat mudah digunakan kembali.
![[Screenshot 2023-04-30 at 18.33.33.png]]
Teknik tersebut dilakukan dengan cara ***Passing props in event handlers*


## Passing props in event handlers
Sebuah komponen dapat menerima props untuk masing-masingnya.

```jsx
<PlayButton movieName="Kiki's Delivery Service" />
```
*button akan memiliki nama pada tampilan sesuai props `movieName`*

```jsx
function PlayButton({ movieName }) {
  function handlePlayClick() {
    alert(`Playing ${movieName}!`);
  }

  return (
    <Button onClick={handlePlayClick}>
      Play "{movieName}"
    </Button>
  );
}
```
*props akan menjadi display pada tampilan button*

```jsx
function Button({ onClick, children }) {
  return (
    <button onClick={onClick}>
      {children}
    </button>
  );
}
```
*komponen button akan melakukan respon sesuai pada props `onClick`*

### Contoh lengkap :

```jsx
function Button({ onClick, children }) {

return (
<button onClick={onClick}>
{children}
</button>
);
}

function PlayButton({ movieName }) {
function handlePlayClick() {
alert(`Playing ${movieName}!`);
}

return (
<Button onClick={handlePlayClick}>
Play "{movieName}"
</Button>
);
}

function UploadButton() {
return (
<Button onClick={() => alert('Uploading!')}>
Upload Image
</Button>
);

} 

export default function Toolbar() {
return (
<div>
<PlayButton movieName="Kiki's Delivery Service" />
<UploadButton />
</div>
);
}
```

#### hasil :
![[sandbox (2).html]]

## Penamaan Event handler Props
kita dapat memberikan penamaan pada event handler sesuka kita, namun penamaan harus dimulai dengan kata `on` dan disusul dengan Huruf kapital seperti `onClick` dapat juga dinamakan `onSmash`.

### Single interaction
```jsx
function Button({ onSmash, children }) {
  return (
    <button onClick={onSmash}>
      {children}
    </button>
  );
}
```
*komponen `button` memiliki 1 interaksi*

#### Contoh penuh : 
```jsx
function Button({ onSmash, children }) {
  return (
    <button onClick={onSmash}>
      {children}
    </button>
  );
}

export default function App() {
  return (
    <div>
      <Button onSmash={() => alert('Playing!')}>
        Play Movie
      </Button>
      <Button onSmash={() => alert('Uploading!')}>
        Upload Image
      </Button>
    </div>
  );
}

```

**hasil : **
![[sandbox (3).html]]


### Multiple interactions
```jsx
function Toolbar({ onPlayMovie, onUploadImage }) {
  return (
    <div>
      <Button onClick={onPlayMovie}>
        Play Movie
      </Button>
      <Button onClick={onUploadImage}>
        Upload Image
      </Button>
    </div>
  );
}
```
*komponen `Tolbar` memiliki 2 interaksi digunakan pada 2 sub-component*

#### Contoh penuh :
```jsx
export default function App() {
  return (
    <Toolbar
      onPlayMovie={() => alert('Playing!')}
      onUploadImage={() => alert('Uploading!')}
    />
  );
}

function Toolbar({ onPlayMovie, onUploadImage }) {
  return (
    <div>
      <Button onClick={onPlayMovie}>
        Play Movie
      </Button>
      <Button onClick={onUploadImage}>
        Upload Image
      </Button>
    </div>
  );
}

function Button({ onClick, children }) {
  return (
    <button onClick={onClick}>
      {children}
    </button>
  );
}

```

**hasil : **
![[sandbox (3) 1.html]]


## Event propagation

*propagation* atau *bubbling* yaitu dimana event pada sebuah komponen dapat menyebar pada event komponen yang lebih tinggi secara bertahap didalam [[Tree component]] tersebut.
**contoh :** 
```jsx
export default function Toolbar() {
  return (
    <div className="Toolbar" onClick={() => {
      alert('You clicked on the toolbar!');
    }}>
      <button onClick={() => alert('Playing!')}>
        Play Movie
      </button>
      <button onClick={() => alert('Uploading!')}>
        Upload Image
      </button>
    </div>
  );
}
```
*komponen `Toolbar` terdapat `<div>` sebagai **Root** dan 2 `button` sebagai **child***
![[sandbox (4).html]]

ketika `event` terjadi pada `div` maka tidak akan bereaksi pada 2 child component dimilikinya dan berlaku sebaliknya ketika `event` pada 2 child component akan memicu `event` pada `div` sebagai **Root** component .

### Stoping propagation
cara agar dapat menghentikan bubbling adalah dengan menggunakan fungsi `e.stopPropagation()` pada *handler event*.
**contoh: **
```jsx
function Button({ onClick, children }) {
  return (
    <button onClick={e => {
      e.stopPropagation(); //penggunaan fungsi melakukan stop bubbling
      onClick();
    }}>
      {children}
    </button>
  );
}

export default function Toolbar() {
  return (
    <div className="Toolbar" onClick={() => {
      alert('You clicked on the toolbar!');
    }}>
      <Button onClick={() => alert('Playing!')}>
        Play Movie
      </Button>
      <Button onClick={() => alert('Uploading!')}>
        Upload Image
      </Button>
    </div>
  );
}

```
***event** pada `button` tidak akan merambat pada **event** `Toolbar`*
![[sandbox (5).html]]


