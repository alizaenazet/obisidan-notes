#AmazonS3 #ObjectLevelStorage
Amazon S3 adalah layanan penyimpanan sederhana yang dapat menampung berbagai bentu file dari gambar,txt,spreadsheet dan keperluan lainnya.

yang membedakan Amazon S3 dengan layanan lainnya ia merupakan  *Object level storage* dan serverless.
![[Pasted image 20230307094636.png]]

sebab *Amazon S3* adalah penyimpanan tingkat object, sehingga apa yang semua ia simpan akan berbentuk object, pada setiap object dapat memiliki ukuran kapasitas sebesar 5 Terabyte.


dari illustrasi diatas menjelaskan bahwasanya setiap data yang disimpan pada Amazon S3 akan dikemas dalam sebuah object, didalam sebuah object akan terdapat 3 hal yaitu Data, Metadata dan Key.
**Data** : pada sebuah object data akan berupa gambar,txt,video,dokumen dsb, lalu terdapat Metadata yang berisikan tentang apa itu data, cara penggunaannya, ukuran objeknya, dsb.
**MetaData** : metadata adalah informasi yang berisi tentang apa itu data, cara penggunaannya, ukuran objeknya, dan sebagainya
**Key** : _key_ (kunci) pada suatu objek adalah identifier/pengenal yang unik.

Object pada Amazon S3 memiliki kemampuan *Versioning* dengan membuat versi pada object, sehingga ketika anda tidak sengaja menimpa sebuah object maka anda tetap dapat memiliki versi sebelumnya.

anda bisa memiliki berbagai object yang dapat anda buat dan object-object tersebut akan disimpan pada yang dinamakan *bucket*, anggap saja pada sebuah laci(bukcet) dapat isi barang-barang(object) didalamnya, Anda juga dapat membuat beberapa bucket lalu menentukan _permission_ (izin) untuk membatasi siapa yang dapat melihat atau mengakses objek di dalamnya.

Amazon S3 memiliki berbagai *Storage class* (kelas penyimpanan), setiap kelas penyimpanan menawarkan mekanisme untuk kasus penggunaan penyimpanan yang berbeda-beda. berikut *Storage class* berserta penjelasannya :

## **S3 Standard**
S3 Standard memiliki kemampuan menyimpan dengan 99,999999999% probabilitas tetap utuh setelah jangka waktu satu tahun, sekaligus setiap data disimpan di 3 data center sehingga memiliki high availbility(ketersediaan tinggi) bagi object. 

Anda juga dapat menggunakan Amazon S3 untuk meng-_hosting_ website statis, yaitu jenis website yang paling dasar dan berisi halaman web dengan konten statis. Caranya cukup mudah, Anda hanya perlu:
    -   Unggah semua file HTML, aset web statis, dan sebagainya ke dalam bucket.
    -   Centang opsi untuk meng-_hosting_ website statis.
    -   Lalu buka website tersebut dengan memasukkan URL _bucket_ dan ta-da! Website instan.

## **S3 Standard-Infrequent Access (S3 Standard-IA)**
#S3Standard-IA kelas penyimpanan ini bersifat jangka panjang yang cocok untuk data(pasif) jarang digunakan namun ketika sekali butuhkan maka dapat digunakan secara cepat, opsi ini adalah tempat yang ideal untuk menyimpan _backup_ (cadangan), _disaster recovery file_ (file pemulihan bencana)

## S3 One Zone Infrequent Access (S3 One Zone-IA )
#S3OneZone-IA
Kelas penyimpanan ini hanya dapat melakukan penyimpanan data di 1 #AZ , maka kelas ini akan menjadi hal yang perlu dipertimbangkan apabila ingin menghemat biaya penyimpanan dan Data dapat diproduksi ulang dengan mudah jika terjadi kegagalan di Availability Zone.

## S3 Intelligent-Tiering
#S3IntelligentTiering
Layanan penyimpan ini akan otomatis memindahkan object didalamnya apabila tidak diakses sama sekali selama 30 hari dari #S3Standard ke #S3Standard-IA , apabila object yang terpindah diakses kembali di *S3 Standard-IA* maka akan otomatis kembali pada *S3 Standard*.

## S3 Glacier
#S3Glacier
Kelas penyimpanan ini cocok untuk penyimpanan data audit, yang mana data tersebut akan disingkat dalam kurun waktu yang lama (tahunan), sehingga tidak memerlukan kemampuan akses instan. Maka dari itu, Anda dapat menggunakan Amazon S3 Glacier untuk mengarsipkan data tersebut. Untuk mengakses *S3 Glacier* memerlukan beberapa menit hingga jam.

Saat penggunaan *S3 Glacier* anda perlu memindahkan data kesana atau dengan membuat *vault(brankas)* dan apabila memiliki *compliance requirement (persyaratan kepatuhan)* untuk periode waktu tertentu, Anda dapat menerapkan _S3 Glacier vault lock policy_ untuk mengunci _vault_ Anda. 

#VaultLockPolicy memungkinkan untuk menentukan _write once/read many_ (WORM) alias menulis data sekali membacanya berkali-kali. Anda juga dapat mengunci kebijakan dari pengeditan di masa mendatang sehingga setelah terkunci, kebijakan tersebut tidak dapat lagi diubah.

ditambah dengan adanya #S3LifecyclePolicies menjadikan kewenangan akan kebijakan memindahkan data dengan secara otomatis antar *Storage class*.

Anda juga memiliki tiga opsi untuk pengambilan data yang berkisar dari hitungan menit hingga jam. Bahkan, Anda memiliki pilihan untuk mengunggah langsung ke kelas Glacier atau menggunakan S3 Lifecycle policies.

*S3 lifecycle policies* dapat memenuhi kebutuhan pemindahan data otomatis berdasarkan waktu yang telah anda tentukan, misalnya, Anda perlu menyimpan objek dalam S3 Standard selama 90 hari. Lalu, Anda ingin memindahkannya ke S3-IA selama 30 hari ke depan. Kemudian setelah total 120 hari, Anda ingin memindahkannya ke S3 Glacier.

## S3 Glacier deep archive
#S3GlacierDeepArchive

Opsi Kelas penyimpanan ini memerlukan waktu akses 12 hingga 48 jam, namun ini adalah opsi penyimpanan dengan biaya terendah dan ideal untuk pengarsipan.








