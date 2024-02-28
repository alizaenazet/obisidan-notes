#AWSOrganizations
Layanan ini akan berguna untuk mengelola beberapa akun sebuah organisasi yang cukup kompleks. dengan *AWS organizations*. anda dapat mengelola beberapa akun AWS, seperti mengelola biaya, kontrol akses, _compliance_ (kepatuhan), keamanan, dan berbagi sumber daya dengan seluruh akun-akun AWS.

AWS Organizations secara otomatis membuat _root_ (wadah induk yang terdiri dari OU(*Organizational Unit*) dan akun AWS di organisasi Anda).

berikut adalah fitur-fitur yang terdapat pada layanan *AWS organizations* :

- ## Manajemen terpusat
dengan fitur ini dapat menggabungkan beberapa akun yang dimiliki (A,B,C,D) menjadi sebuah organisasi, sehingga memungkinkan akun terkelola secara terpusat.

- ## Consolidated billing(tagihan terkonsolidasi)
fitur ini menjadikan satu akun utama dari organisasi untuk menggabungkan dan mengatur pembayaran biaya penggunaan semua akun anggota. dengan begitu menjadikan keuntungan lain yaitu consolidated billing adalah diskon massal.

- ## Pengelompokan hierarki akun
 fitur ini untuk memenuhi kebutuhan keamanan, _compliance_, atau anggaran.
caranya dengan mengelompokkan akun ke dalam organizational unit (OU), untuk mempermudah pengelolaan akun-akun yang memiliki tujuan serupa atau kepentingan persyaratan keamanan.

anda dapat menerepkan *policy (kebijakan)* pada sebuah *OU*, sehingga semua akun yang terkelompokan pada *OU* akan otomatis mewarisi permission yang ada pada *policy* OU tersebut.

Misalnya, jika Anda memiliki akun yang hanya dikhususkan untuk mengakses layanan AWS tertentu, maka Anda dapat memasukkannya ke dalam suatu OU. Kemudian lampirkan policy yang mengatur akses ke layanan AWS tersebut.
[[AWS DATABASE]]
- ## Kontrol atas layanan AWS dan tindakan API
Dengan AWS Organizations, Anda bisa mengontrol layanan AWS dan layanan API yang dapat diakses oleh setiap akun administrator dari akun utama organisasi.  
  
Anda juga dapat menggunakan _service control policies_ (SCP) untuk menentukan _permission_ alias izin maksimum untuk akun anggota di organisasi. Maksudnya, Anda bisa membatasi layanan AWS, sumber daya, dan layanan API individual yang mana dapat diakses oleh _user_ dan _role_ di setiap akun anggota.

penerapan *AWS Organizations* akan sangat membantu dan diperlukan ketika sebuhah organisasi entah perusahaan atau organisasi dsb, dimana memiliki setiap bagian-bagian departemen itu memiliki tugasnya masing-masing, sehingga keperluan masing-masing depertemen akan akses layanan akan berbeda juga, untuk mengatur kerumitan dari kebutuhan kasus tersebut dapat dilakukan pengelompokan sesuai departemen dan kebutuhannya masing masing dengan *AWS organization*.

## Studi kasus

Katakanlah Anda memiliki bisnis dengan akun AWS terpisah untuk setiap departemen: Keuangan, IT, HR (Human Resource/Sumber Daya Manusia), dan Hukum. Anda memutuskan untuk menggabungkan akun ini ke dalam satu organisasi sehingga dapat dikelola dari satu tempat.

Nah selanjutnya, karena departemen HR dan Hukum perlu mengakses layanan dan sumber daya AWS yang sama. sedangkan departemen Keuangan dan IT memiliki persyaratan yang tidak tumpang tindih dengan departemen lain.

Tentu, kebutuhan semacam ini dapat diwujudkan dengan AWS Organizations. Dalam mendesain organisasi, Anda mempertimbangkan kebutuhan bisnis, keamanan, dan peraturan dari setiap departemen. Informasi ini Anda gunakan untuk memutuskan departemen mana yang akan dikelompokkan ke dalam sebuah OU.

![[Pasted image 20230308133839.png]]
*penerapan pada studi kasus*

sebab dikasus ini departemen HR dan Hukum perlu mengakses layanan dan sumber daya AWS yang sama, maka menempatkan akun departemen HR dan Hukum ke dalam OU yang sama, Anda dapat melampirkan _policy_ yang berlaku untuk keduanya. Selain itu, Anda juga dapat lebih mudah memberikan akses ke layanan dan sumber daya yang dibutuhkan.

Walaupun telah menempatkan akun-akun tersebut ke dalam satu OU, Anda tetap dapat memberikan akses untuk _user_, _group_, dan _role_ melalui AWS IAM.



