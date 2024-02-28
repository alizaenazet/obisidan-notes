
- pastikan akses masuk keamana terdapat aturan SSH pada port 22
![[Screenshot 2023-04-11 at 20.06.19.png]]

- konkesikan instance dengan tombol `connect` pada pilihan bagian atas pastikan anda telah memilih instance yang akan diluncurkan.
- pilih opsi `SSH client` 
- pada bagian bawah terdapat bagian `contoh` yang berisikan perintah ssh yang dapat anda langsung salin
![[Pasted image 20230411201653.png]]
salin pada bagian contoh : `ssh -i "namaFilePem.pem" ec2-user@ec2-54-179-118-149.ap-southeast-1.compute.amazonaws.com`

- buka terminal
- arahkan terminal pada folder yang menyimpan file `pem` 
- lalu luncurkan perintah ssh yang telah disalin 
- apabila terdapat error sebab akses terlalu terbuka dapat anda lakukan perintah pada terminal berikut : `chmod 400 notes-api-webserver.pem` 
- lalu ulangi dengan luncurkan perintah ssh yang anda salin tadi
- pastikan port pada kemanan instance dan pada aplikasi pada port yang sama

