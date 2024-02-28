#AWSTrustedAdvisor #PenasehatAWS #Optimasi 
AWS memiliki penasihat otomatis yang disebut dengan AWS Trusted Advisor. Ia adalah layanan web yang memeriksa lingkungan AWS Anda dan memberikan rekomendasi secara _real time_ sesuai dengan praktik terbaik AWS.

![[Pasted image 20230308172231.png]]

ada 3 kategori yang terdapat pada dashboard tersebut, di antaranya:

-   **Centang hijau** : menunjukkan jumlah item yang terdeteksi _tanpa masalah_.
-   **Segitiga oranye** : mewakili jumlah saran yang mungkin perlu Anda _investigasi_.
-   **Lingkaran merah** : mengindikasikan jumlah rekomendasi yang perlu Anda _tindak lanjuti_.

Dapat Anda lihat pada gambar tersebut, AWS Trusted Advisor mengevaluasi sumber daya Anda berdasarkan 5 pilar, di antaranya:

-   _Cost optimization_ (pengoptimalan biaya)
-   _Performance_ (kinerja)
-   _Security_ (keamanan)
-   _Fault tolerance_ (toleransi terhadap kesalahan)
-   _Service limits_ (batas layanan)

AWS Trusted Advisor juga menyertakan daftar rekomendasi tindakan dan materi pendukung di setiap pemeriksaan pilarnya agar Anda dapat mempelajari lebih lanjut tentang praktik terbaik AWS.

Setelah mengetahui apa itu AWS Trusted Advisor, sekarang mari kita uraikan contoh-contoh masalah yang dapat terdeteksi di setiap pilar dari layanan ini.

-   **Cost optimization**  
    Di pilar ini, contoh masalah yang bisa muncul adalah:
    -   RDS instances yang tidak dipakai.
    -   Beberapa EC2 instance yang jarang digunakan.
    -   EBS volume yang tidak dimanfaatkan.

Anda dapat melakukan _scaling down_--telah kita bahas di modul komputasi di cloud--terhadap instance yang jarang dipakai untuk menghemat biaya. Atau, Anda dapat menghapus sumber daya yang memang tidak digunakan sama sekali.

-   **Performance**  
    Salah satu contoh masalah yang muncul di pilar ini adalah pengiriman konten untuk Amazon CloudFront yang tidak teroptimasi.  
      
    
-   **Security**  
    Beberapa contoh masalah yang muncul pada pilar security atau keamanan adalah:
    -   _IAM password policy_ atau kebijakan kata sandi IAM yang lemah untuk user.
    -   MFA (multi-factor authentication) tidak diaktifkan untuk _root user_.
    -   Security group yang mengizinkan akses publik ke EC2 instance.

Semua hal ini membahayakan sumber daya di akun Anda dan harus ditangani secepat mungkin.

-   **Fault tolerance**  
    Berikut adalah beberapa contoh masalah yang dapat muncul:
    -   EBS volume yang tidak memiliki snapshot. Ingat, snapshot adalah _backup_ (cadangan). Tanpa backup, Anda akan kehilangan data di dalamnya jika volume EBS mengalami kegagalan.
    -   Amazon EC2 yang tidak terdistribusi ke seluruh Availability Zone (AZ). Ini akan buruk jika salah satu AZ mengalami masalah, aplikasi Anda mungkin akan mengalami gangguan.  
          
        
-   **Service limits**  
    Pilar ini akan memberi peringatan saat Anda mendekati atau mencapai batas layanan AWS. Contoh, limit dari kepemilikan VPC per Region adalah 5. Nah, jika telah mencapai batas tersebut, maka AWS Trusted Advisor akan segera memberi tahu Anda.
