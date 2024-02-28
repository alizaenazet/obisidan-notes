#PartialDependency 

**Ciri-ciri partial dependency :**
- satu tabel memiliki lebih dari 1 PK
- Tabel memiliki primary key yang terdiri dari beberapa atribut.
- Beberapa atribut lainnya dalam tabel bergantung hanya pada sebagian dari primary key.
- Jika salah satu atribut dalam sebagian primary key diubah nilainya, maka beberapa atribut lainnya akan ikut berubah nilainya.

## Contoh kasus :
![[Jepretan Layar 2023-03-27 pukul 07.05.47.png]]
Dalam tabel di atas, primary key terdiri dari dua atribut, yaitu "id_pesanan" dan "id_pelanggan". Namun, atribut "nama_pelanggan" hanya bergantung pada "id_pelanggan", bukan pada keseluruhan primary key.

