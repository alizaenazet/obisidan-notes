#AWSCloudWatch #MonitoringServer #PengawasServer

Layanan AWS ini akan memberikan kemudahan visibilitas(**keadaan dapat dilihat dan diamati**) terhadap sistem.

hal ini diperlukan untuk melakukan pengecekan, pemantauan, pembenahan pada sistem dan memastikan keberhasilan pada sistem tersebut saat bekerja.

#AWSCloudWatch dapat memantau insfrastruktur dan aplikasi secara *real time*. cara kerjanya dengan melacak dan memantau #metrik. 

*Metrik* adalah variabel yang terkait langsung dengan sumber daya, seperti penggunaan CPU dari EC2 Instance.

berikut beberapa fitur yang tersedia :

## CloudWatch Alarm

Dengan Amazon CloudWatch, Anda dapat membuat alarm sendiri untuk metrik dari semua jenis sumber daya di AWS.

Cloudwatch alarm juga dapat terintegrasi dengan layanan #amazonSNS , sehingga dapat mengirimkan notifikasi apabila alarm berkerja.

 semisal anda ingin mendapatkan notifikasi ketika penggunaan anda telah mencapai jumlah tertentu yang dapat diatur sesuai keinginan.

## CloudWatch Dashboard
#CloudWatchDashboard 
![[Pasted image 20230308165411.png]]
* *Cloudwatch dashboard menampilkan informasi lengkap 

dengan fitur ini semua metrik digabungkan menjadi satu panel yang mencantumkan metrik hampir secara real time.

dengan begitu dapat memantau penggunaan CPU dari Amazon EC2 instance, jumlah total permintaan yang dibuat ke Amazon S3 bucket, dsb. Sehingga, Anda dapat memonitornya secara proaktif.

keuntungannya sebagai berikut : 
-   **Akses ke semua metrik dari satu lokasi**  
    Anda dapat mengumpulkan metrik dan log dari semua sumber daya yang berjalan di AWS bahkan server yang berada di on-premise.  
      
    
-   **Visibilitas ke seluruh aplikasi, infrastruktur, dan layanan**  
    Dengan visibilitas ke seluruh sistem, Anda dapat mengorelasikan bahkan memvisualisasikan metrik dan log untuk menunjukkan sekaligus menyelesaikan masalah dengan cepat.  
      
    
-   **Mengurangi waktu MTTR dan mengurangi TCO**  
    MTTR (mean time to resolution) adalah rata-rata waktu untuk menyelesaikan suatu masalah, sementara TCO (total cost of ownership) adalah biaya kepemilikan.  
      
    Implementasi di kedai kopinya adalah, jika MTTR untuk jam pembersihan mesin lebih pendek, maka Anda dapat menghemat TCO. Dengan kata lain, Anda tak perlu repot-repot menghabiskan waktu untuk membuat sistem analitik sendiri. AWS telah menyediakan Amazon CloudWatch sehingga Anda dapat fokus pada peningkatan nilai bisnis.  
      
    
-   **Mengoptimalkan aplikasi dan sumber daya operasional**  
    Anda dapat menggabungkan metrik dari seluruh EC2 instance untuk memperoleh wawasan akan operasional dan penggunaannya.







