#AWSIdentityAndAccessManagement #AWSIAM #AccessManagement 
*AWS IAM* membantu untuk mengelola akses ke layanan dan sumber daya AWS dengan aman.

*IAM* memiliki fleksibilitas yang dapat kita sesuaikan untuk mengkonfigurasi akses berdasarkan kebutuhan operasional dan kemanan yang sepesifik.

*AWS IAM* memiliki berbagai fitur yang perlu difahami.

## IAM USER
Dengan fitur ini anda dapat membuat  *IAM User*, ia mewakili *orang(personal)* yang berinteraksi dengan layanan dan sumberdaya AWS.

secara *default* *IAM User* tidak memiliki permission sama sekali, sehingga semua tindakan yang dilakukannya akan ditolak. 

dengan *IAM Policies* dapat memberikan permission (memberikan/menolak) secara eksplisit dan mengkaitkannya pada *IAM User*.

## IAM POLICIES
*IAM Policies* adalah berupa dokumen *JSON* yang akan mengizinkan / menolak aktivitas tertentu terhadapat layanan dan sumberdaya oleh *IAM User* dengan cara mengkaitkannya.

 ![[Pasted image 20230308112258.png]]
 *Contoh IAM Policies berupa dokumen JSON*

perincian dari contoh sebagai berikut (dari atas kebawah):
- **Effect** : pada kolumn ini akan terdapat 2 pilihan yaitu **Allow/Deny(Izinkan/Totak)***.  dari yang terdapat pada contoh maka kita mengizinkan untuk melakukan sesuatu 
- **Action** : bagian ini dapat mengisinya dengan panggilan API apa pun. Di sini kita menuliskan **s3:ListObject**. Artinya, user dapat mengetahui objek-objek apa saja yang berada di S3 bucket tertentu.
- **Resource** : bagian ini di-isi dengan alamat sumber daya yang dimaksud. Di pernyataan tersebut kita bisa mengisinya dengan **arn:aws:s3:::EXAMPLE-BUCKET**, yaitu alamat ID unik dari S3 bucket tertentu.
jika Anda melampirkan IAM policies tersebut ke IAM users, maka user tersebut dapat melihat daftar seluruh objek yang ada pada bucket yang bernama “EXAMPLE-BUCKET”.

Ingat! Saat memberikan permission, pastikan Anda mengikuti _“principle of least privilege”_. Maksudnya, berikanlah akses sesuai dengan kebutuhan saat itu saja.

Misalnya, jika seorang user hanya memerlukan akses ke bucket tertentu, maka berikanlah akses hanya untuk bucket tersebut di IAM policies, jangan ke semua bucket.


## IAM Group
untuk mempermudah pengelolaan User maka anda dapat mengelompokan beberapa user dalam beberapa grup dengan *IAM Group*.

dengan demikian selain dapat mengaitkan sebuah *IAM Policies* pada setiap User dapat pula mengkaitkan pada sebuah grup, sehingga semua user yang terdapat pada sebuah grup memiliki permission yang sama.

![[Pasted image 20230308113816.png]]
*contoh sebuah group bernama barista*

anda dapat membuat grup dan menambahkan User yang anda mau kedalam grup tersebut, dengan tujuan memudahkan anda mengelola *permission* dengan mengelompoknnya

## IAM Roles
#IAMRoles memiliki permission yang bersifat temporer/sementara di beberapa saat untuk mengizinkan tindakan tertentu pada beberapa hal, seperti sumber daya AWS,user, eksternal user, aplikasi, bahkan layanan AWS lainnya. 

ketika sebuah identitas menggunakan *IAM Roles* maka akan meninggalkan permission sebelumnya yang dimiliki dan mengambil permission *role* tersebut.




