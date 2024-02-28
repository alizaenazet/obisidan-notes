
#FaktorPemilihanRegion #DataCenter  
![[Pasted image 20230305132458.png]]
AWS memiliki data center diberbagai tempat dibeberapa negara yang dapat kita gunakan sesuai kebutuhan.

## 4 Faktor bisnis menentukan pemilihan region :
### 1. Compliance (Kepatuhan)
Sebelum faktor lainnya, Anda harus terlebih dahulu melihat _compliance requirement_ (persyaratan kepatuhan) Anda. Opsi lainnya menjadi tidak penting saat Anda memiliki persyaratan kepatuhan.  
  
Misalnya, jika Anda memiliki persyaratan bahwa data Anda harus tinggal di perbatasan negara Inggris, maka pilihlah Region London. Atau jika Anda harus masuk ke dalam perbatasan negara Cina, maka Anda bisa memilih salah satu Region Cina.  
  
Namun, sebagian besar perusahaan tidak diatur oleh regulasi yang ketat semacam itu. Jadi, jika Anda tidak memiliki kontrol kepatuhan atau regulasi yang mewajibkan penentuan Region, maka Anda dapat mempertimbangkan faktor lain.

### 2. Proximity (Kedekatan)
Memilih region yang paling dekat dengan basis pelanggan akan membantu Anda untuk mengirimkan konten lebih cepat kepada mereka.  
  
Katakanlah suatu perusahaan berlokasi di Washington, DC, namun kebanyakan pelanggannya tinggal di negara Singapura. Nah, untuk kasus ini, solusi yang tepat adalah dengan menjalankan infrastruktur di Region Northern Virginia agar dekat dengan lokasi perusahaan dan menerapkan aplikasi dari Region Singapura.  
  
Dengan begitu, **latensi** (waktu yang diperlukan untuk mengirim dan menerima data) bisa semakin kecil dan pengiriman konten ke pelanggan menjadi lebih cepat.

### 3.**Feature Availability** (Ketersediaan Fitur)
Adakalanya, Region terdekat mungkin tidak memiliki semua fitur AWS yang Anda inginkan. Namun, AWS terus berinovasi untuk pelanggan. Setiap tahun, AWS merilis ribuan fitur dan produk baru secara spesifik untuk menjawab permintaan dan kebutuhan pelanggan.  
  
Tapi, terkadang layanan baru tersebut membutuhkan banyak perangkat keras fisik baru yang harus AWS bangun agar dapat beroperasi. Dan terkadang, itu berarti AWS harus membangun layanan di satu Region pada satu waktu.  
  
Misal Anda ingin membangun sebuah aplikasi yang menggunakan Amazon Braket--platform komputasi kuantum baru AWS. Faktanya, layanan ini belum tersedia di seluruh AWS Regions sehingga Anda harus menjalankannya di Region yang menyediakannya.  
  
Kalau begitu, dapatkah kita mengharapkan fitur tersebut tersedia di semua Region? Ya, itu ekspektasi yang bagus. Tapi, jika Anda ingin menggunakannya hari ini juga, maka Anda harus mempertimbangkan untuk memilih Region lain yang memiliki fitur tersebut.

### 4.Pricing (Harga)
Meskipun spesifikasi perangkat keras pada suatu Region setara dengan Region lain, namun beberapa lokasi bisa lebih mahal pengoperasiannya.  
  
Misal negara Brasil, struktur pajak di sana memiliki tatanan sedemikian rupa sehingga biaya AWS bisa jauh lebih mahal untuk mengoperasikan layanan yang sama persis dibandingkan dengan negara lain. Pengoperasian beban kerja yang sama persis di kota Sao Paulo mungkin bisa 50% lebih mahal daripada di kota Oregon di negara Amerika Serikat.  
  
Harga dapat ditentukan oleh banyak faktor dan AWS akan transparan mengenai hal tersebut.  
  
Ingat! Setiap Region memiliki harga yang berbeda-beda. Jadi, jika bujet adalah perhatian utama Anda, mungkin akan lebih baik untuk mengoperasikan lingkungan AWS Anda di negara lain meskipun basis pelanggan Anda tinggal di Brasil. Sekali lagi, ini berlaku jika anggaran adalah motivasi utama Anda.

