inheritance bermakna pewarisan dimana *Parent class*  akan mewariskan semua field dan method pada *Child class*.

bayangkan sebuah class bernama `vehicle` anggap saja class tersebut adalah sebuah sebuah class dari kendaraan secara umum, dimana setiap kendaran memiliki jumlah roda, dan kapasitas penumpang.

 class `vehicle` akan menjadi sebuah *Parent class*, yang memiliki *Child class* anggap dari class `vehicle` terdapat class `Motor` dan `mobil` sebagai *Child*nya.

berikut contohnya :
```js
class Vehicle{
roda
penumpang

spesifikasi(){
	console.info(`Kendaraan memiliki jumlah roda dan menampung beberapa    penumpang`) //perhatikan method sebab ini akan dapat diwariskan pada setiap child class.
}
} 
```
*pembuatan class sama seperti class biasanya, contoh class Vehicle yang akan menjadi "Parent class"*

setelah *Parent class* `Vehicle` dibuat maka kita dapat membuat *Child class* untuk class `Vehicle` .

berikut pembuatan *Child class* `Motor` dan `Mobil` :
```js
class Motor extends Vehicle{

//tidak perlu medeklarasikan property yang telah ada di vehicle kecuali anda ingin membuat sebuah property khusus untuk class Vehicle

spesifikasi(){
	console.info(`Motor memiliki jumlah roda ${roda} dan menampung ${penumpang} penumpang`)
}

class Mobil extends Vehicle{

//tidak perlu medeklarasikan property yang telah ada di vehicle kecuali anda ingin membuat sebuah property khusus untuk class Vehicle

spesifikasi(){
	console.info(`Motor memiliki jumlah roda ${roda} dan menampung ${penumpang} penumpang`)
}

}
```

berikut contoh membuat object dari 3 class tersebut :

```js
const vehicle = new Vehicle() //Membuat object daro Class Vehicle
const motor = new Motor() //Membuat object daro Class Motor
const mobil = new Mobil()  //Membuat object daro Class Mobil

motor.roda = 2;
motor.penumpang = 2; //memberikan nilai pada object motor
mobil.roda = 4;
mobil.penumpang = 8; //memberikan nilai pada object mobil

//menjalankan fungsi setiap object 
motor.spesifikasi() //Output:
// Motor memiliki jumlah roda 2 dan menampung 2 penumpang 

mobil.spesifikasi() //Output : 
// Mobil memiliki jumlah roda 4 dan menampung 8 penumpang 
```

**contoh lainnya :**

```js
class Employee{
name
role
sayHello(name){
document.writeln(`hello ${name} my name is ${this.name} iam as Employee<br>`)
}
}

class Manager extends Employee{

sayHello(name){
document.writeln(`hello ${name} my name is ${this.name} iam as manager<br>`)
}
}

  

const employee = new Employee();
employee.name = "anton";
employee.sayHello("budi"); //Output : hello budi my name is anton iam as Employee
const manager = new Manager();
manager.name = "budi"; //Output: hello anton my name is budi iam as manager
manager.sayHello("anton")
```

## kata kunci `super` pada constructor class
Kata kunci "super" pada constructor class di JavaScript digunakan untuk memanggil constructor dari kelas induk (parent class). Ketika kita ingin membuat sebuah subclass (kelas anak) yang memiliki beberapa properti dan method yang sama dengan kelas induk, kita bisa menggunakan "super" untuk mengakses properti dan method yang telah didefinisikan di kelas induk.

Contoh, misalkan kita punya kelas induk bernama "Person" yang memiliki properti "name" dan method "speak()", dan kita ingin membuat sebuah subclass "Student" yang juga memiliki properti "name" dan method "speak()". Kita bisa menggunakan "super" pada constructor kelas anak "Student" untuk memanggil constructor kelas induk "Person" dan mengakses properti dan method yang telah didefinisikan di kelas induk.

```js
class Employee {
name
constructor(name) {
this.name = name;
}

sayHello(name) {
document.writeln(`hello ${name} my name is ${this.name} iam as Employee<br>`)
}

}
class Manager extends Employee {
constructor(name, fullName) {
super(name)
this.fullName = fullName;
}

sayHello(name) {
document.writeln(`hello ${name} my name is ${this.fullName} iam as manager I am often called ${this.name}<br>`)

}

}

const employee = new Employee("anton");
employee.sayHello("budi");

const manager = new Manager("budi","budi santoso");
manager.sayHello("anton")
```

Kata kunci "super" digunakan pada constructor kelas anak untuk memanggil constructor kelas induk dan mewarisi properti dan metode dari kelas induk. Dengan demikian, kita tidak perlu menulis ulang properti dan metode yang sudah ada di kelas induk. Contohnya dapat dilihat pada kode di atas, di mana kelas Manager merupakan turunan dari kelas Employee, dan menggunakan kata kunci "super" untuk memanggil constructor kelas Employee dan mewarisi properti name.