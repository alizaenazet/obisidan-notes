#subnet adalah sebuah bagian dari #VPC dimana anda dapat mengelompokan sumber daya berdasarkan kebutuhan operasional dan keamanan.
![[Pasted image 20230305172629.png]]
*Didalam kotak VPC terdapat 2 subnet dengan kebutuhan dan keamanan yang berbeda*
Satu-satunya alasan teknis untuk menggunakan subnet di VPC adalah untuk mengontrol akses ke gateway. Subnet publik memiliki akses ke Internet Gateway, sementara Subnet privat tidak dan subnet juga dapat mengatur perizinan traffic.

Subnet akan diatur sesuai kegunaannya dimana akan diatur akses atas subnet tersebut untuk keamanan, seperti menyimpan data pribadi pelanggan dan riwayat pesanan yang mana subnet privat tidak diinginkan apabila dapat diakses oleh sembarang orang.

Di VPC subnet dapat berkomunikasi satu sama lain. Misalnya, Anda dapat memiliki aplikasi pada Amazon EC2 instance di subnet publik yang berkomunikasi dengan database di subnet pribadi.

#privateSubnet #publicSubnet #typeOfSubnet #perizinanTraffic 
