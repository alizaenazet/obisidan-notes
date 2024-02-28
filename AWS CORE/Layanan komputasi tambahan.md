EC2 Instance ada VM yang cocok untuk berbagai kebutuhan dari server web sederhana hingga yang komplek sekaligus

EC2 mengharuskan anda untuk mengelola dan mengatur *Instance* dari waktu ke-waktu saat anda menggunakanya, anda akan bertanggung jawab untuk :

1. Melakukan _patching_ (memperbaiki masalah dengan memperbarui program komputer) saat _software package_ (paket perangkat lunak) yang baru tersedia.
2. Menyiapkan _scaling_ (penyesuaian kapasitas).
3. Merancang aplikasi untuk dijalankan dengan cara yang _highly available_ (sangat tersedia).

#KewajibanPenggunaanEC2 #HarusDiSetUpDiEC2 

**Komputasi serverless**

![[Pasted image 20230304115410.png]]

Ketika ingin memiliki server tanpa harus memikirkan akan operasional dan pengelolaan server itu sendiri maka serverless adalah solusinya, dengan serverless anda dapat menjalankan kode(aplikasi/web dsb) tanpa harus membuat atau mengelola server tersebut.

Serverless = menyerahkan keperluan server kita pada pihak lain (AWS) sehingga tak perlu memikirkan tentang terkait keperluan server itu sendiri, anda bisa langsung mengakses dan menggunakan server tanpa harus bingung membangunnya.

Analogi: ketika ingin mendapatkan internet pada smartphone pribadi anda tidak perlu memikirkan tentang bagaimana internet bisa sampai ke smartphone anda (Secara teknis) , anda hanya perlu membeli kartu dan membayar setiap paket internet dari provider tersebut tanpa harus memikirkan membangun tower untuk sinyal dsb.

#ServerLess #ServerPatungan #ServerTakberfisik #SewaServer

**AWS Lamda**

#AwsLambda adalah salah satu opsi layanan #ServerLess dari beberapa opsi lainya yang tersedia pada AWS, layanan AWS Lamba dirancang untuk menjalanlan kode cepat selama <= 15 Menit dengan begitu layanan ini tidak cocok untuk proses yang berjalan lama seperti *deep learning*, layanan ini lebih ideal untuk  _web backend_, penanganan permintaan, atau pemrosesan laporan pengeluaran.

AWS Lambda dikelola sepenuhnya, dapat diskalakan secara otomatis, _highly available_ (sangat tersedia), dan semua pemeliharaan dilakukan oleh AWS. Jika Anda memiliki 1 atau bahkan 1000 _trigger_ (pemicu) yang masuk untuk memanggil _function_ (fungsi), Lambda akan melakukan scaling terhadap function tersebut guna memenuhi permintaan.

#AwsLambda #LayananAWS #LayananAWSUntukProsesCepat 

**Cara kerja AWS Lambda**
#caraKerjaAWSLambda
![[Pasted image 20230304122022.png]]
*dari kiri ke kanan* 
1.  Unggah kode Anda ke AWS Lambda.
2.  Konfigurasikan kode Anda agar terpicu (_trigger_) dari sumber kejadian, seperti layanan AWS, aplikasi seluler, atau HTTP _endpoint_ (titik akhir HTTP).
3.  Kode berjalan hanya ketika mendapat _trigger_.
4.  Cukup bayar sesuai waktu komputasi yang Anda gunakan. Misalnya, Anda mempunyai kode yang dapat mengubah ukuran gambar. Nah, Anda hanya akan membayar waktu komputasi yang digunakan untuk menjalankan fungsi pengubahan ukuran gambar saat ada yang mengunggah sebuah gambar baru.

**Container**
Container adalah layanan yang cocok apabila anda tidak merlukan layanan serverless hingga ke infrastrukturnya namun anda tetap ingin efisiensi dan portabilitas di AWS terdapat 2 layanan yang dapat digunakan yaitu Amazon Elastic Container Service (Amazon ECS) dan Amazon Elastic Kubernetes Service (Amazon EKS), keduanya merupakan jenis layanan *container orchestration* alias orkestrasi kontainer. Container pada 2 hal tersebut adalah *Docker container*.

#DockerContainer  #Docker = Software, #Container = metode.
#Docker adalah platform perangkat lunak populer yang menggunakan virtualisasi sistem operasi untuk memudahkan Anda dalam membangun, menguji, dan men-_deploy_ (menerapkan) aplikasi dengan cepat.
#Container menyediakan cara untuk mengemas kode, konfigurasi, dan dependensi aplikasi Anda ke dalam satu objek.
![[Pasted image 20230304123532.png]]

sesuai gambar diatas
#Container  pada kasus ini (AWS) bekerja diatas EC2 Instance sebagai *Host(Server)nya* . Saat anda menggunakan #DockerContainer di *AWS* anda perlu melakukan proses memulai, menyetop, memulai ulang dan memantau container yang berjalan dimana tidak hanya pada 1 *Instance saja * melainkan di beberapa instance dimana dari beberapa instance tersebut disebut *cluster*. 

dari proses tersebut lah  yang disebut dengan _container orchestration_ dan tentu akan sangat sulit jika melakukannya sendiri. Layanan orkestrasi dibuat untuk membantu mengelola container Anda.

Cluster/klaster = saat menggunakan #DockerContainer ,kumpulan dari beberapa proses memulai, menyetop, memulai ulang dan memantau container yang berjalan pada salah satu dari beberapa *Instance* dan setiap instance tersebut disebut #cluster  / #klaster.

Container orchestration  = #containerOrchestration adalah men-_deploy_ (menerapkan), mengelola, dan men-_scaling_ aplikasi dalam container.

**Studi kasus :  #Container **

Misal _developer_ aplikasi di suatu perusahaan memiliki infrastruktur komputer yang berbeda dengan staf operasi IT. Developer tersebut ingin memastikan bahwa lingkungan aplikasi tetap konsisten terlepas dari  deployment-_nya (penerapannya) sehingga dia pun menggunakan pendekatan container_.

#Container membantu developer tersebut mengurangi waktu yang dihabiskan untuk _debugging_ (proses mengidentifikasi dan memperbaiki eror) aplikasi dan mendiagnosis perbedaan dalam lingkungan komputasi.

Saat menjalankan _containerized application_ (aplikasi dalam container), penting untuk mempertimbangkan skalabilitas. Ini tergantung kepada setiap kasus penggunaan, Anda bisa saja:

-   Menggunakan satu _host_ dengan banyak container.
-   Mengelola puluhan _host_ dengan ratusan container.
-   Mengurus mungkin ratusan _host_ dengan ribuan container.

Dalam skala besar, bayangkan berapa lama waktu yang Anda butuhkan untuk memantau penggunaan memori, keamanan, _logging_ (tindakan menyimpan log), dsb.

Untuk itulah hadir layanan #containerorchestration (orkestrasi container) yang membantu Anda men-_deploy_ (menerapkan), mengelola, dan men-_scaling_ aplikasi dalam container.

**Amazon elastic container service ( Amazon ECS)**

#AmazonECS  adalah sistem manajemen *container* berkinerja tinggi yang memungkinkan scaling terhadap *containerized application (aplikasi dalam kontainer)* di AWS

#AmazonECS mendukung *Docker container*. AWS mendukung semua versi dari dari software *Docker*. Amazon ECS juga mendukung penggunaan *API* untuk meluncurkan dan menghentikan aplikasi yang mendukung  *Docker*. 

#API adalah  _Application Programming Interface_ adalah perantara perangkat lunak yang memungkinkan dua aplikasi untuk berinteraksi satu sama lain

#EC2SupportDocker #AWSSupportDocker

**Amazon elastic kubernates service (Amazon  EKS)**

#AmazonEKS adalah layanan yang dapat anda gunakan untuk menjalankan #kubernetes di AWS.

AWS secara aktif bekerja sama dengan komunitas Kubernetes yang mengelola Kubernetes. Saat fitur dan fungsionalitas baru dirilis untuk aplikasi Kubernetes, Anda dapat dengan mudah menerapkan pembaruan tersebut ke aplikasi Anda yang dikelola oleh Amazon EKS.

#kubernetes = Software *open-source* untuk *men-deploy(menerapkan)* dan mengelola *containerized application* dalam sekala besar.

#AWSKubernetes #AWSSupportKubernates 

**AWS Fargate**
#AWSFargate
AWS Fargate bukan untuk menggantikan *Amazon Eks* maupun *Amazon ECS*, namun
Ketika ingin menggunakan layanan #AmazonEKS atau #AmazonECS yang mana keduanya berjalanan diatas EC2 maka mengharuskan anda mengurusi EC2, apabila anda tidak ingin disibukkan untuk mengurusi pada EC2 anda dapat menggunakan layanan *AWS Fargate*.

lebih detailnya #AWSFargate adalah platform komputasi serverless untuk Amazon ECS dan Amazon EKS. Saat menggunakan layanan ini, Anda tak perlu menyediakan atau mengelola server(EC2) karena AWS Fargate yang mengelolanya untuk Anda.

#AWSTanpaMengaturServer  

Kesimpulan :
-   Jika Anda ingin menjalankan aplikasi dan menginginkan akses penuh ke sistem operasinya seperti Linux atau Windows, Anda bisa menggunakan **Amazon EC2**.
-  Jika Anda ingin menjalankan fungsi yang berjalan singkat, aplikasi berbasis kejadian, dan Anda tak ingin mengelola infrastrukturnya sama sekali, gunakanlah layanan **AWS Lambda**.
- Jika Anda ingin menjalankan beban kerja berbasis Docker container di AWS, langkah yang perlu Anda lalui adalah:
-  Anda harus memilih layanan orkestrasinya terlebih dahulu. Anda bisa menggunakan **Amazon ECS** atau **Amazon EKS**.
- Setelah memilih alat orkestrasinya, kemudian Anda perlu menentukan platformnya. Anda dapat menjalankan container pada **EC2 instance** yang Anda kelola sendiri atau dalam lingkungan _serverless_ seperti **AWS Fargate** yang dikelola oleh AWS

