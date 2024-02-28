A JavaScript Promise object can be:

-   Pending
-   Fulfilled
-   Rejected

The Promise object supports two properties: **state** and **result**.

While a Promise object is "pending" (working), the result is undefined.
When a Promise object is "fulfilled", the result is a value.
When a Promise object is "rejected", the result is an error object.
```js
getUser(isOffline) //fungsi GetUser
.then(user => console.log(user))
.catch(err => console.log(err.message));
```

berikut contoh sederhana penggunaan  fungsi dengan promise :
```js
function isOdd(params) {

return new Promise((resolve, reject) => {

if (params % 2 == 0) {
reject(`angka tidak bernilai ganjil ${params}`)
} else {
resolve(`angka ganjil nich😚 ${params}`)
		}
	})
}

isOdd(1).then(
function(value) {console.log(value)},
function(value) {console.log(value)}

)

```

### Penggunaan Promise pada setTimeout

```js


function getUser(params) {

	return new Promise((resolve, reject) => {

	setTimeout(() => {
	const user = ["udin", "alfin", "wawan"]

	if (params) {
	reject(new Error("dia offline cuy"))
	return;
	}
 
	resolve(user)
	
		}, 3000); //Set waktu dipanggil
	})
}

const isOffline = false; 
getUser(isOffline)
.then(user => console.log(user))
.catch(err => console.log(err.message));
```

