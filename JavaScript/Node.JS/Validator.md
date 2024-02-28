**Pustaka validator dan pembersih string.**
memungkinkan dalam melakukan validasi pada setiap input dan type data variable sesuai dengan kebutuhan.

https://www.npmjs.com/package/validator

```js
const validator = require('validator');
```

beberapa contoh :

- validasi **Email** :
```js
validator.isEmail(emailInput)
```

```js
const email = "budi@gmail.com";
const emailSalah = "budi@notEmail"
console.log(validator.isEmail(email)) // Output: true
console.log(validator.isEmail(emailSalah)) // Output: false
```

- validasi **Nomor ponsel** : 
```js
validator.isMobilePhone(noTelp,'id-ID') 
```
*pada parameter ke-2 adalah lokal format nomor ponsel negara, ex: indonesia*.*

```js
const noTelp = +6282132478
const noTelpSalah = 082123234
console.log(validator.isMobilePhone(noTelp,'id-ID') ) // Output : true;
console.log(validator.isMobilePhone(noTelpSalah,'id-ID')) // Output : false;

```

