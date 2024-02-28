
**Amazon Simple qeue service**
Ketika ingin menyimpan atau mengirim data antar aplikasi tanpa perlu menyediakan layanan tambahan maka amazon simpel queue service adalah solusi dimana anda dapat menyipan datanya dan itu disebut payload dan akan terlindungi hingga terkiri

Amazon SQS ialah tempat dimana dapat menyimpan/ditaruh pesan hingga pesan itu diproses, cara kerjanya seperti penjembatan ketika 2 aplikasi atau lebih berintraksi, analoginya aplikasi A akan mengirim pada SQS lalu dimasukan pada antrean aplikasi B akan mengambilnya sesuai antrian dan menghapusnya dari antrean

Payload = menyimpan data yang berisi antrian dari antar aplikasi pada SQS

#antrianantaraplikasi #jembatanantaraplikasi #penghubungantaraplikasi #amazonSQS

**Amazon simple notification service (Amazon SNS) **

Amazon SNS berfungsi untuk mengirim pesan ke layanan, bedanya ia juga dapat sekaligus memberikan pesan sebagai notifikasi/pemberitahuan pada pelanggan.
hal tersebut disebabkan model publish/subscribe alias *pub/sub* yang mana akan menjadikan sebuah saluran yang disebut dengan *SNS topic*, ketika melakukan publish anda dapat mengatur pelanggan(*subscirber*) yang akan menerima topik tersebut 

Ketika mengirim satu pesan ke SNS topic yang akan menyebar sebagai pemberitahuan pada semua subscriber dalam sekali jalan;

penerapan: mengirim notifikasi pada pada pelanggan dengan menggunakan *push notification* atau SMS

SNS Topic = terjadinya Pub/sub mengatur subscriber saat publish
Subscriber/Pelanggan = end point pada sebuah SNS topic yang akan menerima pesan, ex SQS queue, fungsi AWS Lambda--akan kita bahas nanti, dan juga server web.

#notifikasipadapelanggan #pemberitahuanpadapelanggan #SNSTopic #Pub/Sub 
#pushNotification #amazonSNS

**Studi kasus : Amazon SNS **

Katakanlah Anda membuat suatu buletin di kedai kopi berupa pembaruan yang mencakup informasi kupon, trivia kopi, dan produk baru. Semua informasi ini dikelompokkan menjadi satu topik karena ini adalah buletin tunggal. Semua pelanggan yang berlangganan buletin menerima pembaruan tentang topik-topik tersebut.

Tak lama kemudian, beberapa pelanggan Anda memberikan umpan balik bahwa mereka lebih suka menerima buletin terpisah hanya untuk topik tertentu saja, sesuai ketertarikan mereka. Anda pun mengabulkannya.

Sekarang buletin di kedai kopi telah terbagi menjadi tiga: kupon, trivia kopi, dan produk baru. Pelanggan pun akan menerima buletin sesuai dengan topik tertentu yang mereka inginkan. Mereka dapat berlangganan satu topik atau beberapa topik sekaligus.

Misalnya, pelanggan pertama hanya berlangganan topik kupon; pelanggan kedua hanya berlangganan topik trivia kopi; dan pelanggan ketiga berlangganan topik kopi trivia dan produk baru.

Meskipun contoh dari kedai kopi ini melibatkan pelanggan yang merupakan manusia, di Amazon SNS, pelanggan/subscribers dapat berupa server web, alamat email, AWS Lambda function, atau beberapa opsi lainnya.

Analogi studi kasus : #amazonSQS  dan #amazonSNS 
![[Pasted image 20230304113856.png]]
Ketika kasir menambahkan antrian yang harus dikerjakan oleh barista dan barista akan mengerjakan berdasarkan pesanan yang telah ditambahkan oleh kasir adalah contoh dari #amazonSQS , kemudian apabila pesanan telah siap dan dapat diambil oleh pelanggan maka pelanggan akan diberi tahu bahwa pesanannya dapat diambil saat itu juga maka itu adalah analogi dari #amazonSNS 

NB:konsep #amazonSQS  menghindari kecacatan sistem apabila kasir langsung menyampaikan pesanan secara langsung kepada barista, hal tersebut terjadi sebab ada kemungkinan si barista sedang istirahat atau sibuk bahkan hingga lupa.

konsep #amazonSNS memudahkan dalam mengirim pemberitahuan pada pelanggan, apabila dalam satu kali pesanan siap terdapat 3 pesanan dari 3 pelanggan yang berbeda, maka pada saat itu juga 3 pelanggan tersebut mendapatkan pemberitahuan bahwasanya pesanan mereka telah siap pada sat itu juga