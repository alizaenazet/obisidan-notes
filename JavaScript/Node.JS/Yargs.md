**memungkinkan menjalankan metod/fitur secara langsung pada terminal node**.
Yargs membantu Anda membangun alat baris perintah interaktif, dengan menguraikan argumen dan menghasilkan antarmuka pengguna yang elegan.

https://www.npmjs.com/package/yargs

```js
const yargs = require('yargs');
```

```js
yargs.command({

command: "add", // perintah yang akan dilakukan
describe: `tambah kontak baru`, //deksripsi perintah
builder: { //berisikan objek yang dijalankan dengan setiap perintah pada masing-masing inputnya.
	nama: { // nama input
	
	describe: `masukan nama kontak`, //deksipsi setiap input
	
	demandOption: true, // wajib ter-isi (true/false)
	
	type: 'string', //type data inputan
	
	},
	
	email: { // nama input
	
	describe: `masukan email kontak`,
	
	demandOption: false,
	
	type: 'string',
	
	},
	
	noTelp: { // nama input
	
	describe: `masukan no-telfon kontak`,
	
	demandOption: true,
	
	type: 'string',
	
	},
	
	},

handler(argv) {
addContacts(argv.nama, argv.email, argv.noTelp);
}, //fungsi yang dijalankan ketika semua input terisi

});

  

yargs.parse(); //parsing untuk memanggil
```

**penggunaan : **
```js
node app add --nama="aldi" --email="anton@gmail.com" --noTelp="+62821312131"
```
*pada file **app.js** dengan perintah **add** beserta setiap inputnya*.

**Tampilan  (terminal) :**
**`node app --help` :**
```
```js
app [command]

Commands:
  app add  tambah kontak baru // hasil

Options:
  --help     Show help                                                 [boolean]
  --version  Show version number                                       [boolean]
```
*tampilan pada perintah  --help*

**`node app add --help ` :**
```js
app add

tambah kontak baru

Options:
  --help     Show help                                                 [boolean]
  --version  Show version number                                       [boolean]
  --nama     masukan nama kontak                             [string] [required]
  --email    masukan email kontak                                       [string]
  --noTelp   masukan no-telfon kontak                        [string] [required]
```
*tampilan pada perintah add --help, terdapat setiap keterangan masing-masing option sesuai yang telah dibuat*.



