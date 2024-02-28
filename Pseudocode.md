## Pembahasan
1. aturan umum penulisan [[Pseudocode#Pembahasan]]
2. contoh kasus [[Pseudocode#Contoh penggunaan]]

## aturan umum penulisan pseudocode

1.  Gunakan kata kerja yang tepat pada instruksi, misalnya menggunakan "tambah" untuk penambahan, "kurang" untuk pengurangan, dan "bagi" untuk pembagian.
2.  Gunakan simbol aritmatika seperti tanda tambah (+), kurang (-), kali (*), dan bagi (/) untuk operasi matematika.
3.  Gunakan komentar yang informatif dan jelas untuk menjelaskan algoritma secara rinci.
4.  Gunakan fungsi atau prosedur jika suatu operasi perlu dilakukan beberapa kali.
5.  Buat pseudocode seolah-olah Anda sedang menulis program sesungguhnya dan pikirkan bagaimana program akan berinteraksi dengan pengguna atau lingkungan lain.
6. Gunakan bahasa yang jelas dan mudah dipahami.
```
MINTA a, b, c
IF a > b THEN
   TULIS "a lebih besar dari b"
ELSE IF a < b THEN
   TULIS "b lebih besar dari a"
ELSE
   TULIS "a sama dengan b"
AKHIR IF
```

7. Gunakan instruksi atau kata-kata yang relevan dengan tugas yang akan dilakukan oleh program.
```
MINTA nama_pengguna
MINTA kata_sandi
IF cek_pengguna(nama_pengguna, kata_sandi) THEN
   TULIS "Selamat datang, " + nama_pengguna
ELSE
   TULIS "Nama pengguna atau kata sandi tidak cocok"
AKHIR IF

```

8. Gunakan indentasi atau penjorokan untuk menunjukkan blok kode yang saling terkait.
```
JIKA kondisi1 MAKA
   INSTRUKSI1
   INSTRUKSI2
JIKA TIDAK, JIKA kondisi2 MAKA
   INSTRUKSI3
JIKA TIDAK
   INSTRUKSI4
AKHIR JIKA
```

9. Gunakan komentar untuk menjelaskan maksud dari instruksi tertentu, **jika diperlukan.**
```
MINTA angka_pertama // Meminta input angka pertama
MINTA angka_kedua // Meminta input angka kedua
jumlah = angka_pertama + angka_kedua // Menghitung jumlah kedua angka
TULIS "Jumlah dari " + angka_pertama + " dan " + angka_kedua + " adalah " + jumlah // Menampilkan hasil
```

10. Berikan nama yang deskriptif pada variabel, fungsi, dan prosedur untuk memudahkan pemahaman dan meminimalisir kesalahan.
```
FUNGSI hitung_luas(persegi_panjang)
   PANJANG = ambil_panjang(persegi_panjang)
   LEBAR = ambil_lebar(persegi_panjang)
   LUAS = PANJANG * LEBAR
   KEMBALI LUAS
AKHIR FUNGSI

```

11. Gunakan tanda kurung untuk menunjukkan parameter atau argumen pada instruksi tertentu.
```
FUNGSI pangkat(angka, eksponen)
   HASIL = angka ** eksponen
   KEMBALI HASIL
AKHIR FUNGSI

pangkat(2, 3) // Pangkat dari 2^3 adalah 8

```

12. Gunakan tanda sama dengan (=) untuk memberikan nilai pada variabel.
```
a = 5
b = 10
c = a + b
TULIS c // Output: 15

```

13. Gunakan tanda kurung kurawal ({}) untuk menunjukkan blok kode yang terdiri dari beberapa instruksi.
```
JIKA nilai > 10 MAKA
{
   TULIS "Nilai lebih besar dari 10"
   TULIS "Tingkatkan performa!"
}
JIKA TIDAK
{
   TULIS "Nilai kurang dari

```

## Contoh penggunaan

1. **Function / method** [[Pseudocode#Function / method]]
2. **FOR Loop** [[Pseudocode#FOR Loop]]
3. **For each** [[Pseudocode#For each]]
4. **Print console** [[Pseudocode#Print console]]
5. **Rekursif function** [[Pseudocode#Rekursif function]]
6. **Switch case** [[Pseudocode#Switch case]]
7. **Array** [[Pseudocode#Array]]
8. **IF ELSE statement** [[Pseudocode#IF ELSE statement]]
9. **While Loop** [[Pseudocode#While Loop]]
10. **Do while** [[Pseudocode#Do while]]
11. **Koneksi database** [[Pseudocode#Koneksi database]]


### Function / method
```
FUNCTION tambah(x, y)
    result = x + y
    RETURN result
END FUNCTION
```
*Contoh di atas adalah pseudocode untuk fungsi penambahan yang menerima dua parameter x dan y, kemudian mengembalikan hasil penjumlahan dari kedua parameter tersebut.*

### FOR Loop
```
FOR i = 1 TO 10
    PRINT i
END FOR

```

### For each
```
FOR EACH elemen IN list
    PRINT elemen
END FOR

```

### Print console
```
PRINT "Halo, dunia!"
```

### Rekursif function
```
FUNCTION faktorial(n)
    IF n = 1 THEN
        RETURN 1
    ELSE
        RETURN n * faktorial(n - 1)
    END IF
END FUNCTION

```
Contoh di atas adalah pseudocode untuk fungsi faktorial yang menghitung nilai faktorial dari suatu bilangan n secara rekursif.

### Switch case
```
SWITCH nilai
    CASE 1:
        PRINT "Nilai sama dengan 1"
    CASE 2:
        PRINT "Nilai sama dengan 2"
    CASE 3:
        PRINT "Nilai sama dengan 3"
    DEFAULT:
        PRINT "Nilai tidak sama dengan 1, 2, atau 3"
END SWITCH

```

### Array 
```
DECLARE array[10]

FOR i = 0 TO 9
    array[i] = i * 2
END FOR

FOR i = 0 TO 9
    PRINT array[i]
END FOR

```

## IF ELSE statement
```
IF x > 0 AND y > 0 
    PRINT "Titik (x, y) berada pada kuadran 1"
ELSE IF x < 0 AND y > 0 THEN
    PRINT "Titik (x, y) berada pada kuadran 2"
ELSE IF x < 0 AND y < 0 THEN
    PRINT "Titik (x, y) berada pada kuadran 3"
ELSE IF x > 0 AND y < 0 THEN
    PRINT "Titik (x, y) berada pada kuadran 4"
ELSE
    PRINT "Titik (x, y) berada pada pusat koordinat"
END IF

```

### While Loop
```
DECLARE i = 1

WHILE i <= 10 DO
    PRINT i
    i = i + 1
END WHILE

```

### Do whiel
```
DECLARE n = 1

DO
    PRINT n
    n = n + 1
WHILE n <= 10

```

### Koneksi database
```
DECLARE connection = CONNECT_TO_DATABASE("nama_database", "username", "password")

IF connection IS NOT NULL THEN
    DECLARE query = "SELECT * FROM nama_tabel"
    DECLARE result = EXECUTE_QUERY(query, connection)
    
    WHILE HAS_MORE_ROWS(result) DO
        DECLARE row = GET_NEXT_ROW(result)
        PRINT row.nama, row.umur
    END WHILE
    
    CLOSE_CONNECTION(connection)
ELSE
    PRINT "Gagal terhubung ke database"
END IF

```
