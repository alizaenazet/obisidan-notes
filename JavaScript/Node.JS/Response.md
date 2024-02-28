Indikasi keberhasilan request client ditentukan oleh response status code yang dikirim oleh server. Karena itu, tentu nilai status code tak bisa sembarang kita tetapkan. Status code haruslah bernilai 3 digit angka dengan ketentuan berikut:
-   100-199 : informational responses.
-   **200 - 299 : successful responses.**
-   300-399 : redirect.
-   **400-499 : client error.**
-   **500-599 : server errors.**

	https://developer.mozilla.org/en-US/docs/Web/HTTP/Status?retiredLocale=id

Status message memiliki nilai standar sesuai dengan response code. Namun, kita bisa mengubahnya bila diperlukan. Untuk mengubah status message, Anda bisa gunakan properti `response.statusMessage`.

```js
  const requestListener = (request, response) => {
      response.statusCode = 404;

      // 404 defaultnya adalah 'not found'
      response.statusMessage = 'User is not found';
  };
```
*tidak disarankan untuk mengganti nilai default walau hanya menerjemahkan*

```js
if (method == "GET") {

res.statusCode = 200;
res.end(`<p> ini home page </p>`)
} else {

res.statusCode = 400;
res.end(`<p> Halaman tidak dapat diakses dengan ${method} request </p>`)
}
```
