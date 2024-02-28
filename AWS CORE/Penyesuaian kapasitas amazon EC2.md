#PenyesuaiankapasitasamazonEC2 #KapasitasAmazonEc2

AWS membuatnya sangat sederhana. Dengan menggunakan metode terprogram yang sama seperti instance kasir yang asli, kita dapat membuat kasir kedua. Sehingga, jika salah satu instance tersebut mengalami kegagalan, kita memiliki instance lain yang sudah berada di garis depan dan siap menerima pesanan.

![[Pasted image 20230317085426.png]]
Dengan begitu, pelanggan tak akan pernah kehilangan kasir. Hal yang sama pun bisa Anda lakukan terhadap instance barista jika Anda mau.

Nah, sekarang kita memiliki sistem yang _highly available_ (sangat tersedia) tanpa satu pun titik celah kegagalan. Selama jumlah pelanggan yang ada di antrean selaras dengan kapasitas instance, kita baik-baik saja.

Skalabilitas berarti kapasitas dari arsitektur Anda dapat merespons terhadap perubahan permintaan dengan melakukan _scaling out_ atau _scaling in_--keduanya akan kita bahas nanti.

Anda cukup membayar sumber daya yang Anda gunakan dan tak perlu lagi khawatir akan kekurangan kapasitas komputasi untuk memenuhi kebutuhan Anda.

Jika ingin proses _scaling_ terjadi secara otomatis untuk instance EC2, maka layanan AWS yang tepat adalah Amazon EC2 Auto Scaling.

### Amazon EC2 Auto Scaling

Pernahkah Anda mencoba mengakses sebuah website namun halaman tersebut tak dapat memuat info dan malah sering kali menunjukkan eror seperti _timeout_ (kehabisan waktu). Itu artinya, website tersebut terlalu banyak menerima permintaan masuk sehingga tak dapat menanganinya lagi. Maka dari itu, hadirlah solusi Amazon EC2 Auto Scaling.

Amazon EC2 Auto Scaling memudahkan Anda untuk menambah atau menghapus Amazon EC2 instances secara otomatis sesuai kebutuhan. Dengan begitu, Anda dapat membuat aplikasi selalu tersedia.

Dengan menggunakan Amazon EC2 Auto Scaling, Anda dapat menggunakan dua pendekatan:

-   _Dynamic scaling_, yaitu merespons terhadap perubahan permintaan.
-   _P__redictive scaling_, yaitu secara otomatis menjadwalkan jumlah Amazon EC2 instances yang tepat berdasarkan prediksi permintaan.

> Catatan: Anda pun dapat menggunakan dynamic scaling dan predictive scaling secara bersamaan agar dapat melakukan scaling arsitektur dengan lebih cepat.