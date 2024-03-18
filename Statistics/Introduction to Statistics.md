metode keilmuan statistik dapat membantu memprediksi sebuah data untuk waktu kedepan.

macam statistik dibagi menjadi 2 bagian pada umumnya :
1. Deskriptif [[Introduction to Statistics#Descriptive]] - mendeskripsikan
	menggambarkan/menjelaskan secara deskriptif pada data
	contoh: dikelas saya rata-rata berumur 18 tahun
1. Inferential [[Introduction to Statistics#Inferental Statistik]]- menyimpulkan
	menarik sebuah hasil kesimpulan dari data-data yang telah diolah, contoh :
	- seorang mengambil sampel pada seluruh kelas dan mendapatkan hasil bahwa hampir seluruh kelas tidak ingin berpindah tempat untuk kelas yang digunakan, maka <mark style="background: #BBFABBA6;">kesimpulanya kelas tidak seharusnya dipindahkan</mark>
	- harus menggunakan sample size yang cukup

## Descriptive
Deskriptif adalah metode untuk mengorganisir, merangkum dan menyampaikan sebuah data dalam bentuk yang informatif

**Descriptive statistics** adalah metode-metode statistik yang digunakan untuk mendeskripsikan dan meringkas data. Ini termasuk penghitungan seperti rata-rata, median, modus, varians, standar deviasi, rentang, dan kuartil. Descriptive statistics membantu kita untuk mengerti data dengan cara yang lebih sederhana, menyoroti pola, dan memberikan poin-poin untuk analisis lanjutan. Ada dua konsep penting dalam descriptive statistics: **Populasi** dan **Sampel**.

- **Populasi**: Ini merujuk pada seluruh kelompok yang sedang diteliti atau menjadi topik penelitian. Populasi bisa terdiri dari orang-orang, objek, transaksi, atau apapun yang memiliki karakteristik tertentu. Misalnya, jika kita ingin mempelajari tinggi badan anak sekolah di Indonesia, maka populasi kita adalah semua anak sekolah di Indonesia. Dalam konteks populasi:
  - **Parameter**: Suatu nilai yang dihitung dari populasi, seperti rata-rata tinggi badan semua anak sekolah di Indonesia.
  - **Laporan Populasi**: Hasil yang kita dapat dari populasi dianggap sebagai representasi sejati dari kelompok tersebut.

- **Sampel**: Ini adalah bagian atau subset dari populasi. Kita menggunakan sampel ketika tidak praktis atau mungkin untuk mengamati seluruh populasi. Contohnya, jika kita tidak bisa mengukur tinggi semua anak sekolah di Indonesia, kita mungkin mengambil sampel, seperti anak-anak sekolah dari beberapa kota terpilih. Dalam konteks sampel:
  - **Statistik**: Suatu nilai yang dihitung dari sampel, seperti rata-rata tinggi badan dari sampel anak sekolah yang kita ukur.
  - **Laporan Sampel**: Memiliki margin of error dan interval kepercayaan, yang memberi tahu kita seberapa yakin kita bahwa hasil dari sampel bisa menggambarkan populasi.

![[Screenshot 2024-02-20 at 08.43.07.png]]
**Kenapa Sampel itu Penting?**
- **Biaya**: Mengumpulkan data dari seluruh populasi bisa sangat mahal. Jika biayanya terlalu tinggi, lebih baik menggunakan sampel.
- **Kemusnahan Objek**: Dalam beberapa kasus, seperti pengujian kekuatan bahan, pengambilan data bisa merusak objek. Jadi kita hanya menguji beberapa sampel saja.
- **Ketidakmungkinan**: Kadang, tidak mungkin mengumpulkan data dari seluruh populasi karena jumlahnya yang sangat besar atau tersebar luas.

**Contoh Penggunaan Sampel**: Stasiun televisi sering menggunakan sampel untuk mengetahui popularitas acara mereka. Mereka tidak bisa bertanya ke semua penonton, jadi mereka menggunakan sampel dari penonton untuk mendapatkan estimasi.

Dengan menggunakan sampel yang representatif, kita bisa mendapatkan gambaran yang cukup akurat tentang populasi tanpa harus mengumpulkan data dari setiap individu atau objek di dalamnya.

## Inferental Statistik
Mengeneralisasi jumlah data sampel menjadi data asli.
contoh:  5000 mahasiswa kampus diwakili oleh 100 sampel mahasiswa hasil dari sampel akan digeneralisasi menjadi kesimpulan untuk seluruh 5000 mahasiswa.

**Inferential Statistics:**
- **Definisi**: Metode statistik yang digunakan untuk memperkirakan sifat-sifat populasi berdasarkan sampel.
- **Penerapan**: Memungkinkan Anda membuat keputusan berdasarkan kumpulan data yang terbatas.
- **Contoh**: Dari 5000 mahasiswa, 400 diwawancarai. Jika 300 mengatakan makanan sehat itu penting, kita menyimpulkan bahwa sekitar 75% dari semua mahasiswa berpikir makanan sehat penting.

**Tipe-Tipe Variabel:**

1. **Qualitative Variable (Variabel Kualitatif):**
   > [!PDF|yellow] [[Week 1 - Intro to Statistics 2023.2.pdf#page=11&selection=5,0,8,48&color=yellow|Week 1 - Intro to Statistics 2023.2, p.11]]
> > QUALITATIVE VARIABLE An object or individual is observed and recorded as a non-numeric characteristic or attribute. Examples: gender, city of birth, eye color, etc.
> 
> 

<mark style="background: #BBFABBA6;">varibel numerik alias dapat dihitung.</mark>

   - **Ciri-ciri**:
     - Non-numerik.
     - Mewakili karakteristik atau atribut.
   - **Contoh**:
     - Jenis kelamin.
     - Kota kelahiran.
     - Warna mata.

2. **Quantitative Variable (Variabel Kuantitatif):**
   - **Ciri-ciri**:
     - Numerik.
     - Hasil pengukuran atau perhitungan.
   - **Sub-tipe**:

> [!PDF|yellow] [[Week 1 - Intro to Statistics 2023.2.pdf#page=12&selection=5,0,13,10&color=yellow|Week 1 - Intro to Statistics 2023.2, p.12]]
> > Types of Variables • Quantitative variables can be discrete or continuous
> 
> Variabel Kuantitatif memiliki dua tipe berdasarkan tipikal hasil

![[Week 1 - Intro to Statistics 2023.2.pdf#page=13&rect=123,58,622,391&color=yellow|Week 1 - Intro to Statistics 2023.2, p.13]]

 **Discrete (Diskrit)**:
       - Hasil hitungan.
       - Ada "celah" antara nilai-nilai.
       - **Contoh**: Jumlah kamar tidur dalam rumah, jumlah siswa dalam kursus statistik.
         
**Continuous (Kontinu)**:
       - Hasil pengukuran.
       - Bisa menerima nilai apa saja dalam rentang tertentu.
       - **Contoh**: Tekanan udara dalam ban, durasi penerbangan dari Surabaya ke Jakarta.

Inferential statistics membantu kita mengambil sampel data yang terbatas dan menggunakan informasi tersebut untuk membuat generalisasi atau kesimpulan mengenai populasi yang lebih besar. Variabel kualitatif memberikan konteks dan deskripsi, sementara variabel kuantitatif memberikan data numerik yang dapat dihitung dan dianalisis lebih lanjut.



Jenis level variabel : 
![[Screenshot 2024-02-20 at 08.54.11.png]]
![[Pasted image 20240220090254.png]]

1. **Nominal**  
   Ini adalah tingkat pengukuran paling dasar. Data pada tingkat ini hanya dapat dikategorikan berdasarkan nama atau label tanpa adanya urutan tertentu.  
   **Contoh:**  
   - Nomor baju pemain sepak bola: 9, 10, 11, dst.
	   walaupun angka untuk melabeli tidak selalu berarti dapat diurutkan, yang tidak bermakna akan angka tersebut
   - Merek mobil: Toyota, Honda, Ford, dst.

2. **Ordinal**  
   Pada tingkat ini, data tidak hanya dikategorikan, tetapi juga diurutkan atau diberi peringkat. Namun, kita tidak bisa mengetahui seberapa jauh perbedaan antara peringkat.  
   **Contoh:**  
   - Peringkat di kelas: 1st, 2nd, 3rd, dst.
   - Klasemen tim dalam liga: 1st place, 2nd place, dst.

3. **Interval**  
   Data interval memiliki semua karakteristik data ordinal, tapi juga menambahkan informasi tentang besarnya perbedaan antara nilai-nilai data. Akan tetapi, data interval tidak memiliki titik nol yang berarti.  
   **Contoh:**  
   - Suhu: 30°C, 20°C, 10°C, di mana perbedaan 10°C memiliki arti yang sama di mana pun pada skala.

4. **Rasio**  
   Ini adalah tingkat pengukuran yang paling tinggi. Selain memiliki semua karakteristik data interval, data rasio memiliki titik nol yang berarti dan rasio antara dua angka juga berarti.  
   **Contoh:**  
   - Jumlah pasien yang dilihat: 0, 5, 10, di mana 0 berarti tidak ada pasien.
   - Jarak ke kelas: 0 km, 2 km, 5 km, di mana 0 km berarti tidak ada jarak, dan 5 km adalah dua kali lebih jauh dari 2 km.

Mengapa kita perlu mengetahui tingkatan pengukuran ini? Karena tingkat pengukuran menentukan jenis perhitungan statistik apa yang bisa kita lakukan pada data tersebut. Misalnya, kita tidak bisa menghitung rata-rata untuk data nominal, tetapi bisa untuk data interval dan rasio. Selain itu, tingkat pengukuran juga mempengaruhi jenis uji statistik yang bisa kita gunakan untuk menganalisis data.


