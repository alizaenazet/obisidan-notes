#AmazonRoute53 
Amazon Route 53 adalah layanan domain name system (DNS) atau sistem nama domain di AWS yang _highly available_ (sangat tersedia) dan _scalable_ (dapat diskalakan). Layanan ini dapat memberikan Anda cara yang andal untuk merutekan pelanggan ke aplikasi internet yang berjalan di AWS.

Amazon Route 53 bertugas untuk menghubungkan permintaan pelanggan ke infrastruktur yang berjalan di AWS (seperti Amazon EC2 instance dan load balancers). Bahkan, ia bisa pula mengarahkan pelanggan ke infrastruktur yang berada di luar AWS.

Jika kita melangkah lebih jauh, Amazon Route 53 itu dapat pula mengarahkan traffic ke _endpoints_ (titik akhir) yang berbeda menggunakan beberapa _routing policies_ (kebijakan perutean) yang berbeda, seperti:

-   Latency-based routing (Perutean berbasis latensi)
-   Geolocation DNS
-   Geoproximity routing
-   Weighted round robin

Contohnya Geolocation DNS, dengan opsi tersebut, kita mengarahkan traffic berdasarkan lokasi pelanggan. Contohnya, lalu lintas yang datang dari Indonesia akan dialihkan ke Region Singapura atau jika berasal dari Jepang akan dialihkan ke Region Tokyo.

Selain mengarahkan traffic, Route 53 dapat digunakan untuk mendaftarkan nama domain baru atau menggunakan nama domain yang Anda miliki. Sehingga, ini memudahkan Anda untuk mengelola semua nama domain dalam satu lokasi.

#AWSDNS 