sebuah sistem keamanan dalam sekala #instance adalah Security Group.

Pada sebuah #subnet bisa terdapat 1 atau lebih instance yang dapat diatur pada setiap instancenya memiliki aturan yang berbeda terkait perizinan tentang siapa yang dapat mengiriminya pesan, port mana yang dapat menerima pesan.

Security group adalah firewall virtual yang mengontrol traffic masuk dan keluar untuk Amazon EC2 instance.
![[Pasted image 20230305182329.png]]
*Setiap paket yang telah melewati #NetworkACL akan melalui pemeriksaan lagi pada sekala instance pada sebuah subnet.*

secara *default* security group menolak semua traffic masuk namun mengizinkan semua lalu lintas yang keluar dari instance, berbeda dengan *Network ACL* yang akan melakukan pemeriksaan saat keluar dan masuk.

Saat EC2 instance diluncurkan, ia secara otomatis dilengkapi dengan security group. Jika Anda memiliki beberapa Amazon EC2 instance di dalam subnet yang sama, Anda dapat mengaitkannya dengan security group yang sama maupun berbeda untuk setiap instance.

anda dapat mengonfigurasinya dengan menambah aturan sendiri yang mengizinkan atau menolak traffic sesuai kebutuhan.

Network ACL dan Security Group akan sering berkaitan sebab mereka akan saling mengecek paket yang keluar-masuk.

Perbedaan utama antara security group dan network ACL adalah:

-   Security group bersifat _stateful_, yang berarti ia memiliki semacam memori untuk mengingat siapa yang diizinkan masuk atau keluar.
-   Network ACL bersifat _stateless_, artinya ia tidak mengingat apa pun. Layanan ini akan memeriksa setiap paket yang melintasi perbatasannya terlepas dari keadaan apa pun.


### Analogi kerja keduanya :

Yang perlu diingat adalah:
**Security Group bekerja untuk setiap Instance
Network ACL bekerja untuk setiap Subnet
Instance terdapat dalam lingkup Subnet**
*Fahami sejenak*

Pada sebuah kasus terdapat 2 Instance Dari satu paket:
**Pengirim Paket** : Joni (Sebagai anak dari Pasutri) yang lebih dekat dengan ibunya dari pada ayahnya,
**Isi paket** : Joni ingin meminta uang untuk membeli Mainan.
**Subnet** : Subnet 1 (Instance ibu), Subnet 2(Instance ayah)
**Instance** : terdapat 2 Instance, 1.Instance Ibu 2.Instance ayah.
**Aturan** : yang dapat meminta sesuatu hal kepada orang tua adalah anaknya.
*Fahami sejenak*

**Alur **  :
- Paket yang dikirim Joni akan dicek apakah Joni layak melakukan hal tersebut
- **Pemeriksaan masuk oleh Network ACL****
- Sebab Joni adalah seorang anak yang akan meminta kepada orang tuanya maka diperbolehkan
- **Paket menuju Instance Ibu** 
- **Pengecekan oleh Security group dari instance Ibu**
- Sebab Joni adalah anak dari ibu yang berhak meminta sesuatu padanya maka diperbolehkan
- **Paket tersampaikan**
- disana ibu mengharuskan Joni meminta izin pada Ayah apakah diperbolehkan 
- **Paket keluar dari Instance ibu dan menuju Instance Ayah**
- Sebab sifat dari Security group yang tidak memeriksa saat paket keluar dari Instance maka paket itu keluar tanpa adanya pemeriksaan oleh security group, namun setelah paket keluar dari instance dia harus berurusan dengan Network ACL sebab Network ACL bersifat melakukan pengecekan paket yang keluar.
- **Pengecekan keluar oleh Network ACL **
- sebab Paket adalah kiriman dari Joni anak dari si Ibu, maka dia berhak membawa amanat dari ibunya.
- **Paket berhasil keluar**
- **Paket menuju Instance Ayah**
- Paket yang dikirim Joni akan dicek apakah Joni layak melakukan hal tersebut.
- **Pemeriksaan masuk oleh Network ACL**
- Sebab Joni adalah seorang anak yang akan meminta kepada orang tuanya maka diperbolehkan
- **Paket menuju Instance Ibu**
- **Pengecekan oleh Security group dari instance Ayah**
- Sebab Joni adalah anak dari Ayah yang berhak meminta sesuatu padanya maka diperbolehkan.
- **Paket tersampaikan**
- si Ayah memperbolehkan dan menyuruh Paket memberikan umpan balik pada si Ibu
- **Paket keluar dari instance Ayah menuju instance Ibu**
- sebab sifat dari Security group yang tidak memeriksa saat paket keluar dari Instance maka paket itu keluar tanpa adanya pemeriksaan oleh security group, namun setelah paket keluar dari instance dia harus berurusan dengan Network ACL sebab Network ACL bersifat melakukan pengecekan paket yang keluar.
- **Pengecekan keluar oleh Network ACL **
- dari sifati si Network ACL bahwasanya dia tak peduli tentang identitas maka akan tetap memeriksa, sebab Paket adalah kiriman dari Joni anak dari si ayah, maka dia berhak membawa amanat dari ayahnya.
- **Paket berhasil keluar**
- **Paket menuju kembali instace Ibu**
- Paket yang dikirim Joni akan dicek apakah Joni layak melakukan hal tersebut.
- **Pemeriksaan masuk oleh Network ACL**
- Sebab Joni adalah seorang anak yang akan meminta kepada orang tuanya maka diperbolehkan
- **Paket menuju Instance Ibu**
- sebab security group dapat mengenali paket maka dia tidak dikenakan pemeriksaan lagi
- **Paket sampai pada instance Ibu**
- selesai

Video:


