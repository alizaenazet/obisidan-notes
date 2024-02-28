#1NF 
hal yang akan dilakukan :
- hilangkan data-data yang bersifat perhitungan
- Pisahkan data yang berulang (optional)
-   Tentukan PK FK
-   Tambahkan Additional Information
- temukan lalu tentukan #PartialDependency dan #TransitiveDepedency

## 1. hilangkan data-data yang bersifat perhitungan
data yang bersifat perhitungan adalah dimana yang memiliki sebuah nilai dari perhitungan nilai tabel lainnya atau hanya sebuah nilai yang memiliki patokan pasti.

**perhatikan tabel yang berwarna hijau** berikut :
![[Jepretan Layar 2023-03-27 pukul 06.24.05.png]]
*tabel **No.Produk** memiliki patokan yang pasti dan tabel **Total** adalah penjumlahan sederhana dari 2 tabel disebelahnya*.

## 2. pisahkan data yang berulang

- temukan lalu tentukan sebuah data yang berulang dan tidak memiliki perbedaan ketika berada di baris yang berbeda, perhatikan tabel berikut :
![[Jepretan Layar 2023-03-27 pukul 06.34.23.png]]
*tabel dengan warna biru adalah data yang berulang*

- setelah menemukan dan menentukan anda dapat memisahkan tabel tersebut menjadi 2 bagian agar mempermudah proses. seperti berikut :
![[Jepretan Layar 2023-03-27 pukul 06.37.48.png]]
*tabel dipisah menjadi 2*

- setelah memisahkan tabel menjadi 2 bagian maka fokus terlebih dahulu pada tabel  berisikan data yang berulang.
**Hapus data yang ber-ulang** seperti berikut : 
![[Jepretan Layar 2023-03-27 pukul 06.44.49.png]]
*hapus data yang berulang menjadi beberapa data yang mewakili*

## 3. Tentukan PK dan FK
pada langkah sebelumnya dilakukan pemisahan tabel menjadi 2 tabel terpisah, dengan begitu kini kedua tabel tersebut **harus terhubung**.


4. temukan lalu tentukan #PartialDependency dan #TransitiveDepedency