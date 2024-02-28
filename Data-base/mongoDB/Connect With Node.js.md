```js
const {MongoClient} = require('mongodb'); // import

const url = 'mongodb://localhost:27017'; //Host dan port
const dbName = 'first'; // nama database
const collection = "mahasiswa" // nama collection pada database
const client = new MongoClient(url) // client


async function main() {
try {

await client.connect(); // connect to database WAJIB

// code.....
//contoh operasi :
const result = await client.db(dbName).collection(collection).find(toFinded); 

} catch (error) {
console.error(error)
} finally {
await client.close(); // close koneksi database WAJIB
}


}


main().catch(console.error);
```

