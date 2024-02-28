#AWSCloudTrail #CatatanRiwayat
 AWS CloudTrail adalah layanan audit API yang komprehensif. Dengan CloudTrail, Anda dapat melihat riwayat lengkap dari aktivitas pengguna dan panggilan API untuk aplikasi maupun sumber daya Anda.

Mesin akan mencatat dengan tepat tentang identitas pemanggil API, waktu panggilan, alamat IP pemanggil, dan masih banyak lainnya.

AWS CloudTrail. Anda dapat menyimpan log tersebut tanpa batas waktu ke dalam S3 bucket yang aman. Bahkan, Anda dapat menyimpannya dengan menggunakan metode anti-gangguan seperti Vault Lock

**CloudTrail Insights.** Ini adalah fitur opsional yang memungkinkan CloudTrail secara otomatis mendeteksi aktivitas API yang mencurigakan di akun AWS Anda.

Di sana Anda bisa membuka CloudTrail Event History dan menerapkan filter agar hanya menampilkan peristiwa untuk tindakan API "CreateUser" di IAM.

Katakanlah Anda telah menemukan suatu catatan kejadian berupa panggilan API yang mengindikasikan pembuatan IAM user bernama Mary. Catatan ini memberikan detail yang begitu lengkap tentang apa yang terjadi. Tahukah Anda apa isi catatan tersebut?

![[Pasted image 20230308171457.png]]

Pada 1 Januari 2020 pukul 09.00 pagi, IAM user bernama John membuat pengguna baru (Mary) melalui AWS Management Console.