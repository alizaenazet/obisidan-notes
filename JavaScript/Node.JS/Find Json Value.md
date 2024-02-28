```js
myJsonFile.find((paramFile) => paramFile.name === contact.name);
```
*paramFile = myJsonFile*

```js
const contact = {name : anton};
const contactsData = JSON.parse(fs.readFileSync(file, 'utf-8')); //File Json
console.log(contactsData.find((paramFile) => paramFile.name === contact.name)) //output : true/false
```

