## Pengertian

Normalisasi adalah sebuah teknik untuk mengorganisasikan data2 yang paling sering kita temukan dalam bentuk struk ke dalam table2, melalui beberapa tahap dari UNF sampai ke 5NF.

## Tujuan

-   Menjaga data agar tidak redundant atau duplikat
-   Agar data lebih mudah dicari
-   Menghilangkan Anomali

## Key

Kenapa kita butuh key :

-   Menjaga agar data kita tidak duplikat (Primary Key)
-   Memungkinkan kita untuk membuat relasi antar table (Foreign Key)

Macam-macam key :

-   Candidate Key

Kolom2 yang menjadi kandidat primary key

-   Primary Key

Dia yang membedakan 1 baris data dengan baris lainnya, dan dia unik

-   Foreign Key

Dia yang menunjuk ke primary key di table lain (digunakan dalam membuat relasi antar table)

-   Composite Key

Ada 2 primary key di satu table

-   Alternate Key

Kolom dari candidate key yang tidak terpilih menjadi primary key

## Tahap-tahap normalisasi

#UNF:

-   Ngubah data jadi bentuk table

#1NF :

-   Hilangkan data2 yang bersifat perhitungan
-   Pisahkan data yang berulang (optional)
-   Tentukan PK FK
-   Tambahkan Additional Information
- temukan lalu tentukan #PartialDependency dan #TransitiveDepedency

#2NF :

-   Hilangkan Partial Depedency
-   (A, B) C,D,E,F
-   (TransactionID, CakeID) CakeName CakePrice Quantity
-   TransactionID(PK) CakeID(PK, FK) Quantity
-   CakeID(PK) CakeName CakePrice

#3NF :

-   Hilangkan Transitive Depedency
-   A -> B -> C
-   TransactionID(PK) CustomerID CustomerName
-   TransactionID(PK) CustomerID(FK)
-   CustomerID(PK) CustomerName