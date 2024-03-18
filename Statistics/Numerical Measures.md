Mempelajari tentang **Mean**, **Median** , **Modes** dan **Deviation**

## Basic *3M* 
`Mean, Median & Modes`
<iframe width="560" height="315" src="https://www.youtube.com/embed/h8EYEJ32oQ8?si=9utmnYoaGWW0PN9k" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

### Mean 
<mark style="background: #BBFABBA6;">jumlah rata-rata dari seluruh nilai pada sebuah data set</mark>, dan nilai *Mean* adalah center points rata-rata <mark style="background: #BBFABBA6;">data set *(yang tidak diurutkan)*</mark>.

`The mean (average) of a data set is found by adding all numbers in the data set and then dividing by the number of values in the set. The median is the middle value when a data set is ordered from least to greatest. The mode is the number that occurs most often in a data set`
`
```python
dataSet = [10,3,6,8] # data set yang akan dicari nilai `mean`

# rumus: total nilai dari seluruh jumlah data / jumlah isi data set

valueOfMean = sum(dataSet) / 4
```

#### Contoh :
![[Screenshot 2024-03-03 at 13.22.19.png]]
	Pada data set tersebut memiliki total panjang nilai 42 *(14 column * 3 row )*


### Median 
<mark style="background: #BBFABBA6;">jumlah rata-rata seluruh nilai pada *dataset* yang telah diurutkan</mark>, 
![[Numerical Measures 2024-03-03 13.35.59.excalidraw]]

### Modes
nilai tertinggi didalam seluruh *dataset*
contoh :
$$
dataset = [1,3,5,1,2,3]
$$
$$
Modes = 5
$$
pada *dataset* tersebut maka nilai *Modes* adalah `5`, sebab diantara seluruh nilai didalam dataset `5` adalah nilai terbesar.


## Weighted & Geometric Mean
### Weighted Mean
`Mean Tertimbang` adalah rata-rata di mana setiap nilai memiliki bobot atau kepentingan yang berbeda.

![[Pasted image 20240303140352.png]]
`Mean Tertimbang` atau `Weighted Mean` yang ada di gambar. pembagian dilakukan dari hasil `jumlah karyawan  * rate gaji/jam` pada setiap  varian rate dengan total penjumalahan nilai dari seluruh karyawan (seluruh varian rate)

#### Mean vs Weighted Mean
`Mean` biasa adalah rata-rata dari semua nilai. Kita jumlahkan semuanya dan bagi dengan banyaknya nilai. Sederhana, kan?

Tapi, `Weighted Mean` berbeda. Di sini, setiap nilai dikali dengan bobotnya (berapa kali nilai itu muncul atau pentingnya nilai itu) sebelum dijumlahkan. Setelah itu, totalnya dibagi dengan jumlah total bobot, bukan jumlah nilai.

Pada contoh pekerja, kita tidak hanya menjumlahkan tarif per jam, tetapi mengalikan dengan jumlah pekerja yang dibayar dengan tarif itu. Ini memberi kita jumlah total yang lebih akurat berdasarkan berapa banyak pekerja yang mendapat tarif tertentu.


### Geomatric Mean
`Mean Geometris` atau `Geometric Mean`. `Mean Geometris` digunakan untuk menghitung rata-rata ketika kita berurusan dengan persentase, laju pertumbuhan, atau nilai-nilai yang dikalikan, bukan dijumlahkan.

pertahikan 2 gambar dari penjelasan berikut :
![[Pasted image 20240303141122.png]]
**Pada gambar pertama**, kita melihat bahwa `Mean Geometris` dari sejumlah nilai adalah akar ke-n dari hasil kali semua nilai tersebut. Ini berbeda dengan rata-rata biasa, yang hanya menjumlahkan nilai dan membaginya dengan jumlah nilai.

![[Pasted image 20240303141128.png]]
**Pada gambar kedua**, diberikan contoh menghitung rata-rata persentase kenaikan gaji dengan `Mean Geometris`. Kenaikan 5% diubah menjadi 1.05 [[Numerical Measures#mengkonversi nilai dalam persentage(%)]], dan kenaikan 15% menjadi 1.15, karena kita menambahkan 1 pada persentase untuk menghitung pertumbuhan total.

Kita kemudian mengalikan kedua nilai pertumbuhan ini dan mengambil akar kuadrat (karena ada dua nilai), yang memberikan `Mean Geometris`.



#### Mean deviation
Mean deviation atau simpangan rata-rata adalah ukuran seberapa tersebar data dari rata-ratanya. Untuk menghitung mean deviation, Anda mengikuti langkah-langkah ini:

1. Hitung rata-rata (\(\bar{X}\)) dari kumpulan data Anda.
2. Untuk setiap angka dalam kumpulan data, hitung selisih absolut (tanpa memandang tanda negatif atau positif) antara angka tersebut dan rata-rata.
3. Jumlahkan semua selisih absolut tersebut.
4. Bagi jumlah selisih absolut dengan jumlah data (n) untuk mendapatkan mean deviation.

Pada contoh yang Anda berikan, rata-rata (\(\bar{X}\)) penjualan cappuccinos adalah 50. Kemudian, mereka telah menghitung selisih absolut antara setiap jumlah penjualan harian dan rata-rata tersebut. 

Selisih absolut ini adalah:
- |20 - 50| = 30
- |40 - 50| = 10
- |50 - 50| = 0
- |60 - 50| = 10
- |80 - 50| = 30

Jumlah selisih absolut adalah \(30 + 10 + 0 + 10 + 30 = 80\).

Karena ada 5 data poin, mean deviation (MD) dihitung sebagai jumlah selisih absolut dibagi dengan jumlah data poin:

![[Screenshot 2024-03-18 at 20.36.40.png]]

Jadi, mean deviation untuk penjualan cappuccinos adalah 16. Ini berarti bahwa pada rata-rata, jumlah cappuccinos yang terjual setiap hari menyimpang dari rata-rata mingguan sebanyak 16 cappuccinos.



#### mengkonversi nilai dalam persentage(%)

![[Pasted image 20240303141339.png]]
Ketika kita berbicara tentang persentase dalam konteks `Mean Geometris`, kita ubah persentase menjadi faktor pertumbuhan. Sebagai contoh:

- Untuk kenaikan 30%, kita tambah 1 dengan 0.30 (karena 30% sama dengan 0.30). Jadi, 1 + 0.30 = 1.3.
- Untuk kenaikan 20%, kita tambah 1 dengan 0.20. Jadi, 1 + 0.20 = 1.2.
- Untuk penurunan -40%, kita kurangi 1 dengan 0.40. Jadi, 1 - 0.40 = 0.6.
- Untuk kenaikan 200%, kita tambah 1 dengan 2.00. Jadi, 1 + 2.00 = 3.0.

Sekarang, untuk menghitung `Mean Geometris`, kita akan mengalikan semua faktor pertumbuhan ini bersama-sama dan kemudian mengambil akar keempat (karena ada empat nilai). Ini memberikan kita tingkat pertumbuhan rata-rata per tahun.

Jadi, jika kamu mengalikan 1.3 (30% kenaikan) dengan 1.2 (20% kenaikan), dengan 0.6 (40% penurunan), dan dengan 3.0 (200% kenaikan), lalu mengambil akar keempat dari hasilnya, kamu akan mendapatkan `Mean Geometris` dari tingkat pertumbuhan investasi.

## Population Variance (Varians Populasi)
- **Apa Itu**: Ukuran seberapa jauh nilai dalam populasi keseluruhan tersebar dari mean (rata-rata) populasi.
- **Rumus**: \(\sigma^2 = \frac{\sum (X_i - \mu)^2}{N}\)
  - \(\sigma^2\): Varian populasi
  - \(X_i\): Setiap nilai dalam populasi
  - \(\mu\): Mean populasi
  - \(N\): Jumlah nilai dalam populasi

**Contoh Situasi**: Ada sebuah kebun buah dan kita ingin tahu seberapa bervariasi ukuran apel yang diproduksi. Kita mengumpulkan data ukuran semua apel selama satu hari, yang tercatat sebagai berikut (dalam cm): 7, 8, 9, 7, 10.

**Langkah-langkah**:
1. Hitung rata-rata ukuran apel: (7 + 8 + 9 + 7 + 10) / 5 = 41 / 5 = 8.2 cm.
2. Kurangi rata-rata dari setiap ukuran apel, kemudian kuadratkan hasilnya:
   - (7 - 8.2)² = (-1.2)² = 1.44
   - (8 - 8.2)² = (-0.2)² = 0.04
   - (9 - 8.2)² = (0.8)² = 0.64
   - (7 - 8.2)² = (-1.2)² = 1.44
   - (10 - 8.2)² = (1.8)² = 3.24
3. Jumlahkan semua hasil kuadrat: 1.44 + 0.04 + 0.64 + 1.44 + 3.24 = 6.8
4. Bagi total dengan jumlah apel: 6.8 / 5 = 1.36 cm².
**Hasil**: Varians ukuran apel di kebun buah adalah 1.36 cm².
## Sample Variance (Varians Sampel)
- **Apa Itu**: Ukuran seberapa jauh nilai dalam sampel tersebar dari mean sampel. Biasanya digunakan karena data populasi lengkap tidak tersedia.
- **Rumus**: \(s^2 = \frac{\sum (x_i - \bar{x})^2}{n-1}\)
  - \(s^2\): Varian sampel
  - \(x_i\): Setiap nilai dalam sampel
  - \(\bar{x}\): Mean sampel
  - \(n\): Jumlah nilai dalam sampel

**Contoh Situasi**: Anda ingin mengetahui seberapa bervariasi pendapatan bulanan dalam grup teman Anda. Anda tidak bisa mengetahui pendapatan semua orang, jadi Anda meminta 6 teman untuk data pendapatannya: $3000, $3200, $2900

**Contoh Situasi**: Anda ingin mengetahui seberapa bervariasi pendapatan bulanan dalam grup teman Anda. Anda tidak bisa mengetahui pendapatan semua orang, jadi Anda meminta 6 teman untuk data pendapatannya: $3000, $3200, $2900, $3100, $3300, $3000.

**Langkah-langkah**:
1. Hitung rata-rata (mean) pendapatan: \((3000 + 3200 + 2900 + 3100 + 3300 + 3000) / 6 = 18500 / 6 = 3083.33\) dolar.
2. Kurangi rata-rata dari setiap pendapatan dan kuadratkan hasilnya:
   - \((3000 - 3083.33)^2 = (-83.33)^2 = 6938.89\)
   - \((3200 - 3083.33)^2 = (116.67)^2 = 13611.11\)
   - \(dan seterusnya untuk setiap nilai...\)
3. Jumlahkan semua hasil kuadrat: misal kita mendapatkan 30000 setelah menghitung semuanya.
4. Karena ini sampel, bagi total dengan jumlah teman minus 1: \(30000 / (6 - 1) = 30000 / 5 = 6000\) dolar².

**Hasil**: Varians sampel pendapatan bulanan teman-teman Anda adalah 6000 dolar².
### Standard Deviation (Standar Deviasi)
- **Apa Itu**: Akar kuadrat dari varian. Ini memberikan ukuran seberapa jauh nilai-nilai dari set data tersebar dalam satuan yang sama dengan data itu sendiri.
- **Rumus**:
  - Populasi: \(\sigma = \sqrt{\sigma^2}\)
  - Sampel: \(s = \sqrt{s^2}\)

**Contoh Situasi**: Kembali ke contoh kebun buah, Anda ingin mengukur seberapa jauh rata-rata ukuran apel bisa bervariasi.

**Langkah-langkah**:
1. Gunakan varians populasi yang sudah dihitung dari contoh sebelumnya, yaitu 1.36 cm².
2. Akar kuadrat dari varians untuk mendapatkan standar deviasi: \(\sqrt{1.36}\) = sekitar 1.17 cm.

**Hasil**: Standar deviasi ukuran apel di kebun adalah sekitar 1.17 cm.

Menggunakan contoh-contoh ini, Anda bisa melihat bahwa varians memberi tahu kita seberapa jauh nilai-nilai bervariasi dalam kuadrat dari satuan aslinya (misalnya, dolar² atau cm²), sedangkan standar deviasi mengembalikan satuan ke bentuk aslinya (misalnya, dolar atau cm), membuatnya lebih mudah untuk dipahami dan dibandingkan dengan data asli kita.