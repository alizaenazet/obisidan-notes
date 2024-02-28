**method yang berguna untuk melakukan pembacaan sebuah file**.

## Syncronous
**readFileSync()** 
```js
readFileSync('<directory>');
```
*parameter berisikan directory pada file yang dituju*

```js
 const file = fs.readFileSync('test.txt');
```
apabila dilakukan print pada variabel `file` maka tidak akan menghasilkan sesuai dengan isi dari file tersebut melainkan file buffernya.

```js
const file = fs.readFileSync('test.txt', 'utf-8');
```
*parameter ke-2 menunjukan encoding(format) menjadi tulisan pada umumnya*.

## Asyncronous
```js
fs.readFile('outputFile.txt', 'utf-8', (err, data) => {
if (err) throw err;
console.log(data)
})
```
*dapat menyertakan callback pada parameter ke-3*

