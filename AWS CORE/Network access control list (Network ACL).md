![[Pasted image 20230305180445.png]]
*Ilustrasi setiap pelanggan meminta data akan melalui pemeriksaan lingkup VPC oleh Internet gateway lalu pemeriksaan lingkup Subnet oleh Network ACL* 

AWS memiliki berbagai layanan yang dapat mencakup setiap lapisan keamanan:
-  _Network hardening_ (Penguatan jaringan).
-   Keamanan aplikasi.
-   Identitas pengguna.
-   Autentikasi dan otorisasi.
-   Pencegahan _distributed denial-of-service_ (DDoS).
-   Integritas data.
-   Enkripsi.
-   dan masih banyak lainnya.

Ketika pelanggan meminta data dari aplikasi yang berjalan di AWS Cloud, maka permintaan ini dikirim sebagai paket. Paket adalah sebuah unit data yang dikirim melalui internet atau jaringan.
![[Pasted image 20230305180955.png]]
*Komponen VPC yang memeriksa izin paket untuk subnet adalah network access control list alias network ACL. Network ACL adalah firewall virtual yang mengontrol traffic masuk dan keluar di tingkat subnet.

Setiap paket yang telah melewati *Gateway* akan dilakukan pemeriksaan terkait izin dengan melihat berdasarkan _siapa_ pengirimnya dan _bagaimana_ ia mencoba berkomunikasi dengan sumber daya yang berada di subnet.

Jika paket memiliki potensi yang dapat membahayakan sumber daya di dalam subnet--seperti upaya untuk menguasai sistem melalui permintaan administratif--maka ia akan diblokir sebelum dapat menyentuh target.

Setiap akun AWS menyertakan network ACL secara default (bawaan). Saat mengonfigurasi VPC, Anda dapat menggunakan default network ACL (mengizinkan semua traffic masuk dan keluar) atau custom network ACL (menolak semua traffic masuk dan keluar hingga Anda secara eksplisit mengizinkannya).

Selain itu, network ACL memiliki aturan penolakan secara eksplisit. Aturan ini berguna untuk memastikan jika sebuah paket tidak cocok dengan salah satu aturan lain di daftar, paket tersebut akan ditolak.

#NetworkACL : Komponen VPY yang memeriksa izin keluar dan masuk paket untuk subnet.
#Paket : Ketika pelanggan meminta data dari aplikasi yang berjalan di AWS Cloud, maka permintaan ini dikirim sebagai paket. Paket adalah sebuah unit data yang dikirim melalui internet atau jaringan.

#LapisanKeamanan #KeamananSubnet 
