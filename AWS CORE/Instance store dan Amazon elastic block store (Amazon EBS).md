#AmazonEBS 
Ketika aplikasi berjalan menggunakan instance EC2, aplikasi kerap membutuhkan akses pada *block level storage* (Penyimpanan tingkat block), anggap saja #blocklevelstorage setiap file yang disimpan diaplikasi akan tersimpan pada block di disk fisik.

![[Pasted image 20230306080845.png]]

pada saat file pada disk diperbarui, file yang tersedia tak akan menimpa seluruh rangkaian blok, melainkan memperbarui bagian yang berubah saja.

Dengan sistem seperti ini, penyimpanan untuk aplikasi (database, perangkat lunak perusahaan, atau sistem file) jadi lebih efisien.

