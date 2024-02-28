#Billing #BillingDashboard #TampilanTagihan 

AWS Billing and Cost Management dashboard. Ia adalah layanan yang dapat Anda gunakan untuk melihat informasi penagihan, membayar tagihan AWS, memantau penggunaan, menganalisis, dan mengontrol biaya.
![[Pasted image 20230310092220.png]]

## Consolidated Billing
#TagihanTerpusat #PusatTagihan 
Consolidated billing adalah fitur yang memungkinkan Anda untuk mendapatkan satu tagihan untuk semua akun AWS yang ada di organisasi. Dengan demikian, Anda tak perlu membayar tagihan untuk setiap akun. Contoh, jika memiliki 100 akun AWS, Anda tak akan mendapatkan 100 tagihan, melainkan hanya satu tagihan terpusat.

![[Pasted image 20230310092538.png]]


manfaat lain dari consolidated billing adalah Anda dapat mendistribusikan _bulk discount pricing_ (harga diskon massal), Savings Plans, dan Reserved Instances di seluruh akun pada organisasi Anda.

Maksudnya begini. Satu akun AWS saja mungkin tidak akan memiliki penggunaan bulanan yang cukup untuk memenuhi syarat diskon. Namun, jika beberapa akun digabungkan, penggunaannya dapat menghasilkan manfaat yang berlaku untuk semua akun yang ada di dalam organisasi.


## Studi Kasus: Consolidated Billing

Katakanlah Anda memiliki perusahaan yang menaungi semua kedai kopi di seluruh kota. Sebagai seorang pemimpin, Anda ingin mengawasi setiap tagihan yang terjadi pada masing-masing akun AWS perusahaan.

Anda memiliki 3 akun (di luar akun utama) untuk setiap departemen: Keuangan, IT, dan Operasional. Anda memutuskan untuk membuat organisasi di AWS Organizations dan menambahkan tiga akun tersebut.

Setiap bulan, AWS melakukan penagihan terhadap akun utama Anda untuk semua akun yang ada di organisasi dengan consolidated billing. Amati gambar berikut:

![[Pasted image 20230310092907.png]]

consolidated billing juga memungkinkan Anda untuk berbagi _volume pricing discounts_ (diskon harga volume) di seluruh akun. Contohnya, beberapa layanan AWS (seperti Amazon S3) dapat memberikan harga yang lebih rendah saat Anda semakin sering menggunakannya.

lantas bagaimana apabila tidak menggunakan Consolidated billing maka perhatikan gambar berikut : 
![[Pasted image 20230310093014.png]]

Di Amazon S3 setelah menggunakan 10 TB data dalam sebulan, Anda bisa membayar harga transfer per GB lebih rendah untuk 40 TB data berikutnya.

dari gambar tersebut ketika tidak terkonsolidasi masing masing akun tidak ada yang memenuhi kapasitas 10 TB perbulan sehingga untuk mendapatkan penawaran layanan yang lebih murah maka dari itu dari beberapa akun tersebut sebaiknya dikonsolidasi pada 1 akun utama.

![[Pasted image 20230310093216.png]]
*Contoh apabila tagihan terkonsolidasi*

ketika tagihan terkonsolidasi pada akun utama dan menghasilkan jumlah transfer data sebesar 14TB yang artinya total >= 10 TB, angka ini telah melebihi ambang batas 10 TB sehingga Anda akan mendapat harga transfer per GB yang lebih rendah untuk data transfer 40 TB berikutnya.

Dengan consolidated billing, AWS akan menggabungkan penggunaan dari semua akun untuk menentukan tingkat harga volume mana yang akan diterapkan. Bahkan, ia juga dapat memberikan harga keseluruhan yang lebih rendah bila memungkinkan. Kemudian, AWS akan mengalokasikan sebagian dari keseluruhan diskon volume untuk setiap akun berdasarkan penggunaan.

Pada contoh di atas, akun Operasional akan menerima porsi yang lebih besar karena ia telah melakukan transfer data sebesar 7 TB. Jumlah ini lebih banyak dibandingkan dengan Keuangan (2 TB) dan IT (5 TB).