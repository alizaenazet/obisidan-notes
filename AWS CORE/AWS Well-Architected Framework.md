#AWSWellArchitectedFramework #AWSArchitectedFramework #GoodArchitecture 

Layanan ini dirancang untuk membantu anda memahami merancang dan mengoperasikan sistem  yang andal,efisien dan hemat biaya di AWS Cloud.

AWS Well Architected Framework terdiri dari 5 Pilar guna memastikan pendekatan yang konsisten guna meninjau dan merancang arsitektur.

penjabaran 5 pilar :

![[Pasted image 20230310142416.png]]
*5 pilar aspek guna terwujudnya aristektur yang bagus*

## Operational Excellence (Keunggulan Operasional)
#OperationalExcellence #OperasionalUnggul 

Pilar ini berfokus untuk menjalankan dan memantau sistem guna memberikan nilai bisnis serta terus meningkatkan proses dan prosedur. Pilar Operational Excellence mencakup bagaimana organisasi Anda mendukung tujuan bisnis, kemampuan untuk menjalankan beban kerja secara efektif, mendapatkan wawasan tentang operasi, dan juga terus meningkatkan proses dan prosedur pendukung untuk memberikan nilai bisnis.  
  
Misalnya, melakukan _operation as code_ (operasi sebagai kode), membuat anotasi dokumentasi, mengantisipasi kegagalan, dan sering memperbaiki prosedur operasi.

## Security (Keamanan)
#Security #Keamanan
Segi keamanan adalah prioritas utama di AWS, dimana aspek inilah yang bertugas melindungi infromasi, sistem dan aset sekaligus.

Saat mempertimbangkan keamanan arsitektur, implementasikan praktik terbaik berikut:

-   Terapkan keamanan di semua lapisan arsitektur Anda.
-   Lakukan automasi terhadap praktik terbaik keamanan.
-   Lindungi data in-transit dan at rest (sudah kita pelajari di Modul Keamanan).

## Reliability (Keandalan)
#Reliability #Keandalan
Pilar ini mencakup kemampuan sistem untuk memastikan beban kerja melakukan fungsi yang diinginkan dengan benar dan konsisten sesuai harapan.  
  
Beberapa contohnya adalah seperti berikut:

-   Pemulihan otomatis dari kegagalan infrastruktur atau layanan.
-   Horizontal scaling untuk meningkatkan ketersediaan beban kerja.
-   Pengujian prosedur pemulihan.

## Performance Efficiency (Efisiensi kinerja)
Pilar ini berfokus pada penggunaan sumber daya IT dan komputasi secara efisien untuk memenuhi kebutuhan.
  
Misalnya, menggunakan arsitektur _serverless_ (tanpa server), melakukan eksperimen lebih sering, dan merancang sistem agar dapat mendunia dalam hitungan menit.

menyesuaikan dengan kubutuhan untuk mencapai nilai efisiensi adalah hal yang perlu diperhatikan.

## Cost Optimization (Pengoptimalan biaya)
#CostOptimization #PengoptimalanBiaya #BiayaYangOptimal
Pilar ini berfokus untuk mengontrol ke mana uang dibelanjakan guna menghindari biaya yang tak perlu.  
  
Misalnya, menerapkan manajemen keuangan cloud, menganalisis pengeluaran, dan menggunakan _managed service_ (layanan terkelola) untuk mengurangi biaya kepemilikan.



Itulah 5 pilar yang dimiliki oleh AWS Well-Architected Framework. Sebelumnya, untuk mengevaluasi pilar-pilar tersebut, anda dapat menggunakan alat _Framework as a self-service_ (Framework/Kerangka kerja sebagai layanan mandiri), yakni AWS #WellArchitectedTool 
