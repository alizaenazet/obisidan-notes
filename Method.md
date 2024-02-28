## 1. Void method

- tidak mengembalik nilai
- hanya mengesekusi kode

```java
void myMethod(){
// kode
}
```

## 2. Return method

- mengembalikan nilai sesuai type data method
- wajib mengembalikan nilai sesuai type data
```java
boolean myBoolMethod(){

return 'landy' // error 
return true / false // bisa

}

String myStrMethod(){

return 21 // error
return false //error
return "landy"

}


```

## 3. Static method

- tidak bergantung pada class 
- tetap didalam sebuah class

```java
static void myVoidStaticMethod(){

}

static boolean myBoolStaticMethod(){
return true // wajib
}

```

## Parameter in method

- tidak terbatas
- memiliki type data
- wajib diisi ketika method dipanggil
- parameter adalah sebuah variabel tersendiiri

```java
Class myClass

int param1;

static void myVoidStaticMethod(Pet param1,String param2){
this.param1 = param2

}

void myMethod(int param1, boolean param2){
// kode
}

```


