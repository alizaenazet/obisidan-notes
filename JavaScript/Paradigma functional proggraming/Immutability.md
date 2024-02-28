Konsep yang kedua adalah immutability. Immutable berarti sebuah objek tidak boleh diubah setelah objek tersebut dibuat. berbalik dengan mutable yang artinya objek boleh diubah setelah objek tersebut dibuat.

berikut contoh fungsi yang tidak mutable dan tidak memenuhi syarat paradigma FP :
```js
const user = {
    firstname: 'Harry',
    lastName: 'Protter', // ups, typo!
}

const renameLastNameUser = (newLastName, user) => {
    user.lastName = newLastName;
}

renameLastNameUser('Potter', user);

console.log(user); //Output: {firstname: 'Harry', lastName: 'Potter'}
```

untuk membuat fungsi tersebut menjadi mutable maka anda harus membuat fungsi tersebut mengembalikan nilai baru bukan menginisiasi/merubah nilai, seperti berikut :
```js
const user = {
    firstname: 'Harry',
    lastName: 'Protter', // ups, typo!
}

const createUserWithNewLastName = (newLastName, user) => {
    return { ...user, lastName: newLastName }
}

const newUser = createUserWithNewLastName('Potter', user);
console.log(newUser); //Output: { firstname: 'Harry', lastName: 'Potter' }
```

perbedaan pada fungsi tersebut adalah alih-alih mengeinisiasi / merubah secara langsung namun fungsi tersebut mengembalikan nilai baru pada object `newUser`.

