**Basic** **C**reat, **R**ead, **U**pdate, **D**elete

## 1. Creat

- ### Membuat sebuah list

**`insertOne()`** 
```js
client.db('myDatabaseName').collection('myCollection').insertOne('myInsert');
```
contoh :
```js
async function addMahasiswa(client, mahasiswa) {
const result = await client.db("kampus").collection('mahasiswa').insertOne(mahasiswa);
console.log(`inserted: ${result.insertedId}`);
}
```
*memasukan **sebuah** nilai pada database `kampus` di collection `mahasiswa` *

penggunaan :
```js
await addMahasiswa(client,
{
nama :"joul",
email : "joul@yahoo.com",
age: 20
}

)
```


- ### Membuat beberapa list

**`insertMany()`**
```js
client.db("myDatabaseName").collection('myCollection').insertMany("myInserts");
```
contoh :
```js
async function addMultipleMahasiswa(client, mahasiswa) {
const result = await client.db("kampus").collection('mahasiswa').insertMany(mahasiswa);
console.log(`inserted: ${result.insertedIds}`);
}
```
*memasukan **beberapa** nilai pada database `kampus` di collection `mahasiswa`*

penggunaan :
```js
await addMultipleMahasiswa(client,[

{ nama: 'sandi', email: 'sandi@gmail.com', age : 11 },
{ nama: 'mirna', email: 'mirna@gmail.com', age : 14},
{ nama: 'sidhi', email: 'sidhi@gmail.com', age : 21}

])
```


## 2. Read

![[Screenshot 2023-04-06 at 19.28.52.png]]
*data sebagai contoh pada database `kampus` di collection `mahasiswa` *

- ### Membaca sebuah nilai

**`findOne()`**
```js
client.db("myDatabaseName").collection('mahasiswa').findOne({name: 'diana'});
```
*mengambi **sebuah** data memiliki nama 'diana'*
contoh :
```js
async function findACollection(client, toFinded) {

const result = await client.db('kampus').collection('mahasiswa').findOne(toFinded);

// pengecekan terhadap hasil yang diambil 
if (result) {
console.log(`found a match with ${toFinded}`);
console.log(result);
}else{
console.log(`not founded`);
}

}
```


penggunaan : 
```js
await findACollection(client,{nama : "diana", age: 23 });
```
hasil :
```js
found a match with [object Object]
{
  _id: new ObjectId("642eafc8c172922d587253dc"),
  nama: 'diana',
  email: 'diana@gmail.com',
  age: 23
}

```


- ### Membaca beberapa list
  
  **`find()`**
  ```js
  client.db('myDatabaseName').collection('myCollection').find({nama: 'diana'});
```
*mengambi **semua** data memiliki nama 'diana'*
contoh :
```js
async function findManyCollection(client, toFinded) {

const result = await client.db('kampus').collection('mahasiswa').find(toFinded);

if (result) {
console.log(`found a match with ${toFinded}`);
const finalResutl = await result.toArray();
console.log(finalResutl);
}else{
console.log(`not founded`);
}

}
```


penggunaan : 
```js
await findManyCollection(client,{nama :'diana', age:23});
```
*mengambil **semua** data dengan  nama 'diana' dan berumur 23 *.
hasil :
```js
found a match with [object Object]
[
  {
    _id: new ObjectId("642eafc8c172922d587253dc"),
    nama: 'diana',
    email: 'diana@gmail.com',
    age: 23
  },
  {
    _id: new ObjectId("642eafeec172922d587253dd"),
    nama: 'diana',
    email: 'dianaputri@yahoo.com',
    age: 23
  }
]

```


## 3. Update

- ### Update sebuah list

**`updateOne()`**
```js
client.db('myDatabase').collection('myCollection').updateOne({nama : "joulius"}, { $set: {nama : "julius"} })
```
*parameter ke-1 menunjukan list yang akan terdampak, parameter 2 melakukan operasi pada list yang terdampak*.

contoh:
```js
async function deleteAList(client, willDeleted) {

const result = await client.db(dbName).collection('mahasiswa').deleteOne({nama : willDeleted})
if (result) {
console.log(`${result.deletedCount} list terhapus`);
}else console.log(`tidak ada terhapus`);
```

penggunaan :
```js
await updateACollection(client,{nama : "joul"}, {nama : "joulius"})
```

hasil :
```js
{
  acknowledged: true,
  modifiedCount: 1,
  upsertedId: null,
  upsertedCount: 0,
  matchedCount: 1
}
```

- ### Update banyak list

**updateMany()**
```js
client.db("myDatabaseName").collection('myCollection').updateMany({age : 14}, { $set: {age : 17}})
```
*parameter 1 menunjukan list yang terdampak, parameter 2 menunjukan dampak(update) pada list*

contoh :
```js
async function updateLists(client, willUpdated, theUpdate) {
const result = await client.db(dbName).collection('mahasiswa').updateMany(willUpdated, { $set: theUpdate})

if (result) {
console.log(`telah terupdate : ${result.modifiedCount}`);
}else console.log(`gagal update`);

}
```

penggunaan : 
```js
await updateLists(client, {age : 21}, {age : 23});
```

hasil :
```js
telah terupdate : 4
```