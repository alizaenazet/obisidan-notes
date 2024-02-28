**insfrastructure as a service (IaaS)**
-Paling fleksibel
-Memberi kontrol penuh 
-Menyediakan akses ke firtual network, virtual machine, storage, dan OS
#IaaS #ServiceFleksibel #ServiceFullControl

## Amazon EC2
#AmazonEC2 adala layanan yang menyediakan server virtual di cloude dengan secure, resizable dan scalable

amazon EC2 memberikan solusi dimana pembuatan server tidak menjadi pembelian berat diawal, sehingga kita dapat mendeploy dan mendevelop aplikasi lebih cepat.

pada amazon EC2 juga dapat mengatur konfigurasi security, networking dan storage sesuai kebutuhan.

pada layanan tersebut pelanggan dapat melakukan #ScaleUp pengaturan secara vertikal dimana anda dapat megatur dari spesifikasi VM dan melakukan #ScaleOut mengatur jumlah VM secara horizontal dengan spesifikasi yang sama saat melakukan #ScaleUp 

### Amazon EC2 Instance (VM) under the hood (dibalik layar

#instance adalah sebuah *Virtual machine* 



![[Jepretan Layar 2023-03-04 pukul 19.25.28.png]]

*Gambar diurut dari bawah keatas*

#Insftastructure adalah bagian *Physical hardware* dari EC2 Instance (CPU,Memory,Storage dsb).
#HostOS adalah OS pada *Physical* (WIndows, Redhat DLL).
#hypervisor adalah software atau hardware untuk menjalankan dan membuat VM.
#GuestOS operating system pada VM 
#Bins/Lib Binaries, Library atau Dependencies yang dibutuhkan aplikasi
#App Aplikasi yang di deploy pada VM

#AmazonEC2Struktur #StrukturEC2

### Fitur-fitur Amazon EC2
#FiturAmazonEC2
- #Instance: Virtual machine
- #AMI : Preconfigured templates (OS dan additional software yang diperlukan). 
- **Instance types** : Berbagai konfigurasi CPU, memory, storage dan networking. #instanceTypes
- **Key pairs** : Informasi untuk login ke instance dengan aman(asymmetric), terdapat 2 key yaitu public dan private dimana public adalah key yang dibawa oleh aws dan private adalah key yang di simpan oleh pengguna sehingga ketika ingin mengakses server maka kedua key tersebut akan dicocokan. #KeyPairs #KeyAkses 
- **Instance store** : Storages volumes yang terpasang pada instance untuk menyimpan data secara sementara (data terhapus saat instance stop, hibernate atau terminate). #InstanceStore
- **EBS Volumes** : Presistent storage volumes, seperti external hard drive (data tidak akan terhapus jika instance, stop, hibernate atau terminate). #EBSVolumes``
- **Region dan Available Zone** : Lokasi fisik untuk menempatkan resource(Instance), dalam satu Region memiliki beberapa AZ(Data center). #RegionAndAZ #Region #AZ #AvailableZone #DataCenter 
- **Security group**: Firewall untuk menentukan protocols, ports, dan source IP ranges yang memasuki instance. #SecurityGroup #SettingFirewall #SettingProtocols #SettingPorts #SourceIPranges
- Elastic IP address :  Public static IPv4 address untuk instance (IP tidak berubah ketika restart atau terminate instance). #ElasticIPAdress
- #VPC : Virtual networks untuk menempatkan instance.


## Tipe instance Amazon EC2
#tipeInstanceAmazonEC2
### General purpose instance

Tipe instance umum dapat memberikan keseimbangan yang baik pada segi sumber daya komputasi, memori dan jaringan, tipe instance ini biasanya digunakan pada berbagai jenis kerja yang beragam, seperti server aplikasi web atau repositori kode

### Compute optimized instance

Tipe instance yang mengoptimasi pada segi prosesor dengan performa tinggi, tipe ini cocok digunakan sebagai server game, HPC (high-performance computing/komputasi dengan performa tinggi) atau pemodelan ilmiah

### Memory optimized instance

tipe yang mengoptimalkan pada beban kerja memori yang besar, memproses kumpulan data besar pada memori, seperti relasional dan nonrelasional database atau HPC (high-performance computing).

## Cara kerja Amazon EC2
#caraKerjaAmazonEC2
### 1.Luncurkan

-   Memilih tamplate dasar pada instance
-   memilih tipe instance
-   konfigurasi dasar termasuk OS, server aplikasi dan aplikasi lainnya

### 2.Hubungkan

Menghubunkan pada instance terdapat berbagai cara, aplikasi/web memiliki metode yang berbeda-beda untuk terhubung pada instance agar dapat bertukar data langsung dengan _********instance,********_ semua hal tersebut dapat terhubung ke _********instance********_ melalui desktop

### 3.Menggunakan

setelah dipastikan telah terhubung denan _********instance********_ maka anda dapat mulai menggunakanya, ada banyak yang anda dapat lakukan, seperti menginstall OS, menambah penyimpanan, menyalin dan mengatur file DLL

## AWS memiliki beberapa pilihan penagihan terkait Amazon EC2. Di antaranya adalah:
#HargaAWSEC2
-   **On-Demand** (Sesuai Permintaan)  
    Opsi ini adalah yang paling dikenal, yaitu _On-Demand_. Anda hanya membayar selama instance berjalan--bisa per jam atau per detik--tergantung pada tipe instance dan sistem operasi yang Anda pilih.  
      
    On-Demand sangat ideal untuk penggunaan jangka pendek, pengembangan dan pengujian aplikasi, serta beban kerja yang tidak dapat diprediksi dan diinterupsi. Selain itu, model harga ini juga biasa digunakan untuk yang baru memulai, menguji beban kerja, sekadar bereksperimen, atau mendapatkan rata-rata dasar pemakaian instance.  
      
    Tak perlu kontrak, komitmen jangka panjang, pembayaran di muka, atau komunikasi dengan AWS sebelumnya untuk menggunakan pilihan penagihan yang satu ini.  
      
    
-   **Savings Plans** (Rencana Tabungan)  
    _Savings Plans_ memungkinkan Anda mengurangi biaya komputasi dengan berkomitmen terhadap _jumlah dolar per jam yang keluar_ dan penggunaan komputasi yang konsisten untuk jangka waktu 1 _atau_ 3 tahun. Setiap penggunaan di luar itu akan dikenakan tarif On-Demand biasa.  
      
    Oleh karena itu, model penetapan harga ini dapat memberikan penghematan hingga 72% pada penggunaan komputasi AWS Anda terlepas dari _instance family_ (keluarga instance), ukuran, OS, _tenancy_ (penyewaan), atau region AWS.  
      
    Model Ini juga berlaku untuk penggunaan AWS Fargate dan AWS Lambda yang merupakan opsi komputasi tanpa server yang akan kita bahas nanti.  
      
    Nanti di kelas ini kita akan meninjau tentang AWS Cost Explorer, yaitu layanan yang memungkinkan Anda untuk memvisualisasikan, memahami, serta mengelola biaya dan penggunaan AWS Anda dari waktu ke waktu.  
      
    Jika Anda sedang mempertimbangkan opsi Savings Plans, AWS Cost Explorer dapat menganalisis penggunaan Amazon EC2 Anda selama 7, 30, atau 60 hari terakhir. AWS Cost Explorer juga memberikan rekomendasi yang disesuaikan untuk Savings Plans.  
      
    Rekomendasi ini dapat memperkirakan seberapa banyak Anda dapat menghemat biaya bulanan berdasarkan penggunaan Amazon EC2 sebelumnya dan jumlah komitmen per jam dalam 1 atau 3 tahun.  
      
    
-   **Reserved Instances** (Instance Terpesan)  
    Reserved Instances menawarkan diskon penagihan yang diterapkan untuk instance On-Demand dengan berkomitmen terhadap _tingkat penggunaan_ untuk jangka waktu 1 atau 3 tahun.  
      
    Ada beberapa opsi yang tersedia: Standard Reserved dan Convertible Reserved Instances (Instance Terpesan Standar dan Terpesan Konvertibel) untuk jangka waktu 1 atau 3 tahun. Dan juga tersedia Scheduled Reserved Instance (Instance Terpesan Terjadwal) untuk jangka waktu 1 tahun saja.  
      
    Opsi ini cocok untuk beban kerja dengan kondisi yang stabil atau dapat diprediksi. _Reserved Instance_ menawarkan diskon hingga 75% dibandingkan dengan opsi On-Demand.  
      
    Terdapat tiga opsi pembayaran pada Reserved Instances:
    1.  _All upfront_ (semua di muka), yaitu Anda membayarnya secara penuh saat Anda berkomitmen.
    2.  _Partial upfront_ (sebagian di muka), di mana Anda membayar sebagian di awal.
    3.  _No upfront_ (tanpa uang muka), di mana Anda tak membayar apa pun di muka.

Ketika Reserved Instance berakhir, Anda tetap bisa menggunakan Amazon EC2 instance tanpa gangguan. Namun akan dikenai tarif On-Demand hingga Anda menghentikannya atau membeli Reserved Instance baru yang sesuai dengan atribut instance (tipe instance, region, tenancy (penyewaan), dan platform).  
  

-   **Spot Instances** (Instance Spot)  
    _Spot Instances_ menggunakan kapasitas komputasi Amazon EC2 yang tak terpakai dan menawarkan penghematan biaya hingga 90% dari harga On-Demand. Opsi ini sangat ideal untuk beban kerja dengan waktu mulai dan akhir yang fleksibel dan tak masalah dengan interupsi.  
      
    Jika Anda mengajukan Spot Instances dan kapasitas Amazon EC2 sedang tersedia, maka instance akan diluncurkan. Namun jika tidak, permintaan akan gagal sampai kapasitas tersedia kembali.  
      
    Setelah Anda meluncurkan Spot Instances, AWS dapat mengklaim kembali instance tersebut kapan pun ketika mereka membutuhkannya.  
      
    AWS akan memberikan waktu peringatan dua menit sebelumnya untuk Anda menyelesaikan pekerjaan. Anda selalu dapat melanjutkannya nanti jika perlu. Jadi, saat memilih opsi ini, pastikan beban kerja Anda dapat menerima interupsi.  
      
    
-   **Dedicated Hosts** (_Host_ Khusus)  
    _Dedicated Hosts_ merupakan server fisik dari kapasitas Amazon EC2 instance yang didedikasikan sepenuhnya untuk Anda gunakan.  
      
    Opsi ini biasanya digunakan untuk memenuhi persyaratan _compliance_ (kepatuhan) tertentu dan tidak ada orang lain yang akan berbagi sewa dari server fisik tersebut.  
      
    Pada opsi ini Anda dapat menggunakan lisensi perangkat lunak per-_socket_, per-_core_, atau per-VM yang Anda punya untuk membantu menjaga persyaratan lisensi yang terikat dengan server.