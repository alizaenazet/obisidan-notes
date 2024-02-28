#TransitiveDepedency 

Transitive dependency adalah kondisi di mana sebuah atribut di dalam sebuah tabel bergantung pada atribut lain yang bukan primary key. Dalam kata lain, nilai suatu atribut dapat ditentukan melalui atribut lain yang tidak langsung terkait dengannya.

Berikut adalah ciri-ciri dari transitive dependency pada tabel:

1.  Terdapat atribut non-primary key yang dapat ditentukan nilainya melalui atribut lain yang juga bukan primary key.
2.  Terdapat relasi fungsional antara atribut non-primary key dan primary key melalui atribut yang juga bukan primary key.
3.  Atribut yang memiliki ketergantungan transitive hanya boleh ditentukan oleh satu set nilai pada atribut primary key.

## Contoh kasus :
![[Jepretan Layar 2023-03-27 pukul 07.13.55.png]]
Dari tabel di atas, atribut "Deskripsi Kategori" tergantung pada "Kategori" dan bukan pada primary key "Kode Barang". Ini berarti bahwa ada transitive dependency antara "Kode Barang" dan "Deskripsi Kategori" melalui "Kategori".
