
## Membuat class
membuat class pada JS anda dapat memasukan sebuah kata kunci `class` dan memberikan nama pada `class` tersebut. 

```js
class Person{
//a class with Person named
}
```
*class denga nama 'Person' *

### Membuat Field pada class
setelah sebuah class dibuat anda dapat membuat field didalmnya, beranggap bahwa pada `class person` memiliki field `name` dan `role` , berikut implementasi fieldnya :

```js
class Person{
	name // field name 
	role // field role
}
```
*Class Person memiliki field name dan role*


## Membuat constructor
sebuah class dapat memiliki constructor dengan menambahkan kata kunci `constructor` didalam class tersebut.
```js
class Person{
	name
	role
	
	constructor(){
	// an constructor inside Person class
	} 
}
```
*constructor kosong tanpa parameter dan isi*

### parameter pada constructor
anda dapat memberi parameter pada constructor seperti berikut :
```js
constructor(param1,param2){
	//constuctor with 2 parameter (param1,param2)
}
```
apabila membuat object dari person maka anda dapat memasukan sebuah nilai pada parameter dimana parameter tersebut *'biasanya'* diteruskan pada field dari class tersebut.

perhatikan kode berikut :
```js
class Person{
	name
	role
	constructor(name, role){
	this.name = name;
	this.role = role;
	} 
}
```
*kini field `name` memiliki nilai = name pada constructor begitu pula dengan `age`* 

perlu diingat bahwa `name` pada constructor adalah sebuah nilai ketika class `Person` menjadi sebuah object dan memasukan nilai `name` tersebut, **intinya** yang perlu diingat bahwa keduanya berbeda walaupun diberi nama yang sama, sebab itu kenapa terdapat penambahan kata kunci `this` untuk menunjukan bahwa name yang menggunakan kata kunci `this` adalah field dari class bukan `name` dari parameter.


anda juga dapat membuat field untuk class melalui constructor, dengan memberi kata kunci `this` seakan-akan class tersebut memang memiliki field tersebut, berikut adalah contoh apabila anda ingin menambah field `age` pada class person melalui constructor :
```js
class Person{
	name
	role 
	constructor(name, role, age){
	this.name = name;
	this.role = role;
	this.age = age; // dengan ini field 'age' ditambahkan pada class Person
	} 
}
```


## Mebuat Method pada class 
setiap class dapat memiliki `method` yang berada didalam scope class, sederhananya anda membuat fungsi untuk sebuah class dan diletakan didalam scope class tersebut. Berikut cara penulisannya :
```js
//didalam class scope
myMethod(){
//isi pada method
} // penulisannya persis seperti fungsi namun tanpa kata kunci `function`
```

berikut contoh sebuah method bernama `sayHello` pada class `Person` dan akan melakukan output pada console sebuah kalimat sederhana perkenalan

```js
class Person{
	name
	role 
	constructor(name, role, age){
	this.name = name;
	this.role = role;
	this.age = age; // dengan ini field 'age' ditambahkan pada class Person
	} 

	sayHello(){
	console.info(`hello my name is ${name} iam a ${role}`)
	} // Ex: hello my name is {budi} iam a {manager}
}
```

### Parameter pada method
seperti halnya Fungsi dan constructor anda juga dapat memberi parameter pada pada sebuah method, sekarang mari kita method `sayHello` menyapa lawan bicaranya dengan mengatakan sebuah nama orang lain. berikut implementasinya : 

```js
class Person{
	name
	role 
	constructor(name, role, age){
	this.name = name;
	this.role = role;
	this.age = age; // dengan ini field 'age' ditambahkan pada class Person
	} 

	//nameParam = "anton";
	sayHello(nameParam){
	console.info(`hello ${nameParam} my name is ${this.name} iam a ${this.role}`)
	} // Ex: hello {anton} my name is {budi} iam a {manager}
}
```


## Membuat  object 
perlu diingat bahwa object tidak mungkin dibuat tanpa adanya sebuah class.

berikut pembuatan object : 
```js
 myobj = new Myclass();
```
myobj = penamaan pada object tersebut , *Myclass = nama class*

pembuatan object budi padag class `Person` :
```js
 budi = new Person();
```
*sebuah object `budi` dibuat dari class `Person`*

penggunaan class :
```js
budi = new Person("budi","manager","age"); //Membuat sebuah object serta mengisi constructor 

budi.sayHello("anton") // Output: hello anton my name is budi iam a manager
```

**Note:** apabila sebuah constructor tidak di-isi maka field akan bernilai `undefined`.

