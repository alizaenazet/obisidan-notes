#PopUp #Alert #PopUpAllert 

## Alert
#Alert 
ini akan menampilan sebuah peringatan pada browser

```js
<script>

alert(" ini alert loh ");

</script>
```

maka hasil dari `alert` :
![[Jepretan Layar 2023-03-17 pukul 14.21.58.png]]



## Promp
anda akan mengeluarkan popup yang dapat menerima input dari user 
``
```js
const name = prompt("masukan nama anda")
```

maka hasil akan mengeluarkan sebuah popup yang tedapat text field dan dapat user isi, seperti berikut :
![[Jepretan Layar 2023-03-17 pukul 14.31.47.png]]

anda juga dapat mengkombinasikannnya dengan #Alert 
```js
<script>

const name = prompt("masukan nama anda")

alert(`ini alert untuk ${name}`);

</script>
```

`alert` akan mengeluarkan popup dari apa yang telah diinput menggunakan prompt, seperti ini :
![[Jepretan Layar 2023-03-17 pukul 14.31.58 1.png]]


## Confirm
pop ini akan memberikan 2 pilihan yang akan menghasilkan sebuah nilai boolean antara iya(true)/tidak(false);

```js
 const sebut = confirm("mau aku sebut nama mu ?")

if (sebut) {
alert(`ini alert untuk ${name}😱`);
} else {
alert(`yaudah deh 😔`)

}
```
![[Jepretan Layar 2023-03-17 pukul 14.37.15.png]]



## video penjelasan lebih lengkap
https://youtu.be/SDROba_M42g?t=10541