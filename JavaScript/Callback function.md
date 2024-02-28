Sederhanannya adalah, anda dapat memasukan  sebuah nilai berupa fungsi kedalam sebuah fungsi dan didalam fungsi tersebut anda dapat menggunakan nilai berupa fungi yang telah dimasukan seperti fungsi pada umumnya, contoh memanggil fungsi `multiply` *(sebagai nilai)*  kedalam argumen fungsi `mathTutor` : 
```js
// Math Operations

function add(a, b){return a+b }

function subtract(a, b){return a-b }

function multiply(a, b){return a*b}

function divide(a, b){return a/b}

function wrongAdd(a, b){return (a+b)+''}

  

// Add your function type below:

  
  

// Math Tutor Function That Accepts a Callback

function mathTutor(operationCallback) {

console.log("Let's learn how to", operationCallback.name,'!');

let value25 = operationCallback(2,5);

console.log('When we', operationCallback.name, '2 and 5, we get', value25, '.');

console.log('When we', operationCallback.name, value25, 'and 7, we get', operationCallback(value25,7), '.');

console.log('Now fill out this worksheet.');

}

  

// Call your functions below:

mathTutor(multiply) /** output :
Let's learn how to multiply !
When we multiply 2 and 5, we get 10 .
When we multiply 10 and 7, we get 70 .
Now fill out this worksheet.
**/

```

