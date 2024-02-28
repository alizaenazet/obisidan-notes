	npm install --save-dev jest

melakukan pengubahan pada `package.json` 
```js
"scripts": {
"test": "jest __test__/*.test.js"
},
```
*pada bagian "script" dan properti "test" *

pada bagian yang diisi adalah ` "jest __test__/*.test.js"` , breakdown : 
`jest` = test yang digunakan .
`__test__` = folder yang berisikan modul-modul test pada contoh folder bernama `__test__`
.
`*.test.js` = menunjukan dimana semua file yang memiliki format `.test.js` akan dapat dijalankan test didalamnya.

import pada fungsi atau nilai yang akan ditest pada contoh merupakan fungsi `averageExams` 
```js
import { averageExams } from "../gradeCalculations";
```

contoh penggunaan test :
```js
test(`its should return exact average`, () => {

const listValueOfExama = [80, 100, 100, 80];

expect(averageExams(listValueOfExama).toEqual(90));

})
```
