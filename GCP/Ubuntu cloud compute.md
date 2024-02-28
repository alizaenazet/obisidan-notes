# **Deploy Laravel di GCP dengan Nginx Ubuntu: *quick start***

Helloo👋 , Pada artikel kali ini, akan membahas cara deploy aplikasi Laravel pada Google Cloud Platform (GCP) Compute Engine dengan MySQL dan VPC. Artikel ini diharap untuk dapat membantu yang ingin mempelajari cara *deploy* aplikasi Laravel pada *cloud service*, khususnya di GCP.

Kita akan mempelajari beberapa hal :
1. Cloud VM & Cloud computing
2. VPC
3. Cloud Database Instance
4. Serverless architecture

## ketentuan awal :
- Project laravel versi 10 ( perlu sedikit penyesuaian jika menggunakan framework/library tambahan seperti filament/intertia )
- Menggunakan github repository
- Memiliki akun aktif [GCP](https://cloud.google.com/?hl=id)

## setup database
jika kalian menggunakan *database* terlebih diantaranya adalah mysql, postgreSql dan relational db lainnya maka buruntung sekali, sebab kalian dapat membuat server *database* kalian sendiri.


untuk memulai penggunaan databse kita menggunakan product dari [GCP CLOUD SQL](https://cloud.google.com/sql?hl=en)agar lebih mudah ditemukan gunakan search bar dengan kata kunci "SQL".
![[Screenshot 2023-12-22 at 06.51.09.png]]

klik *create instance* dan pilih tipe *database* yang kalian inginkan, pada kasus ini saya akan menggunakan *mysql* .
![[Screenshot 2023-12-22 at 06.54.14.png]]

configurasi yang saya gunakan sebagai berikut :
![[screencapture-console-cloud-google-sql-instances-create-engine-MySQL-2023-12-22-06_58_32.png]]
*konfigurasi pada instance tersebut saya peruntukan untuk study case, dengan tujuan menghindari biaya berlebih*

proses aktivasi *database* dapat cenderung lama, berkisar 30-180 detik bahkan lebih. 

setelah instance database telah berhasil dibuat dan diaktifkan maka akan terlihat pada *dashboard* tipe database kalian beserta keterangannya.
![[Screenshot 2023-12-22 at 07.04.41.png]]
yang perlu kita perhatikan adalah *public IP address*, sebab itu adalah host yang akan kita gunakan untuk terhubung dengan database dan itu juga bisa kalian lakukan dengan database client favorit masing-masing, seperti *phpmyadmin, dbaver, DLL*. 

secara *default* pengaturan autentikasi akan berjalan pada port  `3306` dan memiliki *username* `root`, sisanya sesuai dengan konfigurasi yang kita sesuaikan saat membuat instance. Dengan demikian database telah siap digunakan.

## setup Compute engine instance
agar kita dapat menjalankan aplikasi maka kita butuh server yang siap sedia menangani permentian pada aplikasi kita, maka dari itu kita akan memulai membuat sebuah instance *Cloud VM* dari GCP yaitu [*Compute engine*](https://cloud.google.com/compute?hl=id).

### membuat sebuah instance baru

masuk ke dashboard project dan gunakan *search bar* dengan kata kunci "*Compute engine*".
![[Screenshot 2023-12-22 at 07.13.33 1.png]]

buat instance baru dengan klik menu "*Create instance*" pada bagian atas dashboard.
![[Screenshot 2023-12-22 at 07.15.28.png]]

berikut configurasi sederhana untuk *study case saat ini* :
![[screencapture-console-cloud-google-compute-instancesAdd-2023-12-22-02_42_35 copy.png]]

#### Memilih Boot Disk
pada menu boot disk saya melakukan beberapa perubahan sebagai berikut : 
![[Screenshot 2023-12-22 at 07.23.59.png]]
*configurasi tersebut sangat cocok untuk kita yang pertamakali mencoba sekaligus belajar sehingga tetap dapat menghemat tagihan saat proses belajar*.

saya menggunakan OS *Ubuntu 22.04 LTS* dan jika instance dihapus maka begitu huga dengan *Boot disk*, untuk menghindari tagihan diluar prediksi kelak.

saya melakukan beberapa pengaturan dasar sebagai berikut :
![[screencapture-console-cloud-google-compute-instancesAdd-2023-12-22-02_42_35.png]]

jika dirasa telah tepat dan benar maka klik pada opsi *CREATE* pada bagian pojok kanan bawah

### Reservasi IP address External
setelah berhasil membuat sebuah instance maka kita dapat melihat informasi sederhana akan instance tersebut salah satunya adala *External ip address* untuk memahami lebih detail tentang *IP Address* internal dan external.

tujuan kita adalah ketika sebuah instance dilakukan restart atau dinyalakan kembali dia akan tetap memiliki *IP Address* tetap sehingga kita tidak perlu membeli *domain* untuk penggunaan jangka pendek dan pembelajaran.

ada dua hal yang perlu kita akan terapkan ialah : 
1. [IP Address](https://www.techtarget.com/whatis/definition/IP-address-Internet-Protocol-Address)
2. [VPC](https://www.cloudflare.com/learning/cloud/what-is-a-virtual-private-cloud/)

maka kita akan memulai dengan melakukan reservasi pada *instance* kita terlebih dahulu menggunakan [layanan *VPC* yang telah disediakan oleh *GCP*](https://cloud.google.com/vpc?hl=en). 

#### Memasang reserved IP Address pada Compute instance

untuk mempermudah pencarian akan produk, seperti biasa gunakan *Search bar* pada bagian atas *dashboard* dengan kata kunci *Vpc networks*.
![[Screenshot 2023-12-22 at 07.37.32.png]]

pada dashboard pilih menu *Reserve external static IP address*.
![[Screenshot 2023-12-22 at 06.05.33.png]]

berikut adalah konfigurasi yang saya gunakan dan disesuaikan untuk pada salah satu instance dari *Compute engine*.
![[screencapture-console-cloud-google-networking-addresses-add-2023-12-22-06_10_01.png]]
berikut adalah penjelasan setiap nomor :
1. Nama VPC pada umumnya menjelaskan akan vpc dan product akan dihubungkan.
2. Region adalah tempat dimana instance dari *Compute engine* yang ingin dituju dijalankan.
3. Nama instance yang ingin menggunakan *VPC*
pilih opsi *Reserve* jika telah dirasa benar dan sesuai

setelah berhasil dilakukannya reservasi maka akan menyadari bahwasanya, External IP pada instance kita cenderung lebih rumit ketimbang sebelumnya seperti berikut : 
![[Screenshot 2023-12-22 at 06.12.03.png]]

setelah langkah-langkah sebelumnya selesai terlakasana maka kita akan mulai melakukan *setup* pada *Web server* dan *aplikasi web*.
## Setup Compute engine Instance with Nginx

sebelum menuju lebih dalam, pastikan aplikasi laravel telah berjalan dengan baik pada local environment kita (termasuk pasca dilakukan clone pada repository). 

## install nginx
Agar aplikasi laravel kita dapat dijalankan dengan optimal dan  aman maka kita akan menggunakan web server, untuk web server yang akan kita gunakan adalah [*Nginx*](https://www.nginx.com/resources/glossary/nginx/) pemeilihan akan menggunakan pada *Nginx* salah satunya adalah kemudahan konfigurasi dan bersifat *open source* alias gratis. 

untuk memulai melakukan instalasi pada *webserver* dan aplikasi laravel maka kita akan mengakses [*VM*](https://www.vmware.com/topics/glossary/content/virtual-machine.html) melalaui *Shell/Cli* anda dapat menggunakan *SSH client*  favorit kalian ataupun *Cloud shell* yang telah disediakan oleh *GCP*. Pada kali ini saya akan menggunakan *Cloud shell* agar lebih ringkas dan cepat, berikut langkah-langkahnya : 

1. pergi ke dashboard *Compute engine* 
   ![[Screenshot 2023-12-22 at 08.01.08.png]]
   
2. klik icon opsi disamping menu *SSH* pada instance yang ingin kalian gunakan dan pilih menu *View gcloud command*
   ![[Screenshot 2023-12-22 at 08.01.25.png]] 
   
3.  klik pada *Copy to clipboard* lalu *Run in Cloud shell*
   ![[Screenshot 2023-12-22 at 08.03.02 2.png]]
   
4. agar lebih nyaman saat digunakan klik icon *Open in new window* pada bagian bawah kanan halaman.
   ![[Screenshot 2023-12-22 at 08.05.29.png]]
   tunggu hingga proses selesai dan *Cloud shell* siap digunakan.
5. *Paste* dari yang telah kita *copy* pada *clipboard* dan tekan enter
   maka hasil output kurang-lebih seperti berikut :
![[Pasted image 20231222081049.png]]
*terdapat informasi dasar tentang instance dan aktivitas login *

6.  sekarang kita sudah siap untuk memulai melakuakn instalasi pada webserver dan aplikasi laravel kita.

### install Nginx
jalankan *promp* berikut secara berurutan :
```
sudo apt update
sudo apt install nginx
```
*akan dilakukan update dan melakukan install pada nginx*

**verifikasi instalasi**
jalankan promp `sudo nginx -t`, maka akan menghasilkan *output* seperti berikut : 
```
nginx: the configuration file /etc/nginx/nginx.conf syntax is ok
nginx: configuration file /etc/nginx/nginx.conf test is successful
```
*tidak ada error syntax yang terjadi saat dilakukan verifikasi dan pengecekan*
## install php
untuk menjalankan apliaksi laravel maka diperlukan tersedianya *Php* dan kita akan menggunakan versi yang disarankan pada dokumentasi laravel yaitu versi 8.2, jalankan *promp* berikut secara berurutan :
```
apt update
add-apt-repository ppa:ondrej/php
```

```
apt update
apt install php8.2 -y
```

**verifikasi instalasi**
```
php --version
```
jika berhasil akan menampilkan output seperti berikut :
```
PHP 8.2.13 (cli) (built: Nov 24 2023 08:47:18) (NTS)
Copyright (c) The PHP Group
Zend Engine v4.2.13, Copyright (c) Zend Technologies
    with Zend OPcache v8.2.13, Copyright (c), by Zend Technologies
```

### install php extension 
kita juga diharuskan melakukan install pada beberapa extension php yang paling dasar dapat mengikuti pada, *promp* berikut :
```
sudo apt-get install -y php8.2-cli php8.2-common php8.2-fpm php8.2-mysql php8.2-zip php8.2-gd php8.2-mbstring php8.2-curl php8.2-xml php8.2-bcmath php8.2-dom 
```
*sesuaikan extension yang akan dibutuhkan oleh aplikasi laravel, sebab beberapa extension tidak disertakan seperti "memcahed" dsb*.

kita diharuskan menjalankan salah satu extension yaitu `php-fpm`, berikut adalah 2 promp untuk menjalankan dan menghentikan extension tersebut :
```
sudo systemctl start php8.2-fpm  
sudo systemctl enable php8.2-fpm
```
*`sudo systemctl start php8.2-fpm` jalankan jika belum berjalan sebelumnya*

## install composer
kita juga perlu menginstall *php Composer*.

download file `.phar`
```
php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
php -r "if (hash_file('sha384', 'composer-setup.php') === 'e21205b207c3ff031906575712edab6f13eb0b361f2085f1f1237b7126d785e826a450292b6cfd1d64d92e6563bbde02') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
php composer-setup.php
php -r "unlink('composer-setup.php');"
```

set composer *globally*
```
mv composer.phar /usr/local/bin/composer
```

**verifikasi instalasi**
```
composer
```
*jalankan promp tersebut maka akan keluar menu opsi penggunaan composer jika berhasil dilakukan instalasi*

### install node.js
penggunaan node.js diperlukan untuk melakukan build pada *vite.js* sebagaimana frontend tools pada laravel versi 10.x
```
curl -sL https://deb.nodesource.com/setup_20.x -o nodesource_setup.sh_`
```
*setup_20.x berartikan akan bersiap untuk install versi 20.x anda dapat sesuaikan dengan versi yang diinginkan*

```
sudo bash nodesource_setup.sh_
```

```
sudo apt install nodejs_
```

verifikasi instalasi 
```
juliuswuwung@deploy-laravel:~$ node -v
v20.5.1
juliuswuwung@deploy-laravel:~$ npm -v
9.8.0
```

jika dirasa versi npm perlu dilakukan pembaruan dapat dijalankan dengan 
```
npm install -g npm@10.2.5 // update pada versi 10.x
```
*lakukan jika npm pada versi <10.x*
## setup laravel

#### clone from github repostiory
```
cd 
```
*kembali ke direktori home/utama*

pilih project kalian yang akan anda clone dari repository github.
```
git clone https://github.com/yourusername/Your_Project.git
```
*clone menggunakan https url atau protokol yang anda lebih anda inginkan*

```
cd Your_Project
```
*masuk ke project hasil dari clone repostiory*

install requirement pada laravel dengan menjalankan promp berikut dengan berurutan:
```
sudo npm install
sudo composer update
sudo composer install;
cp .env.example .env
sudo php artisan key:generate;

```

sesuaikan konfigurasi pada file `.env` dengan menjalankan promp `nano .env`

### connect with database

kembali ke project anda dan masuk ke `env` dengan command `nano .env`, setting sesuai dengan kebutuhan, contoh:
```
DB_CONNECTION=mysql
DB_HOST=34.101.213.182 // public ip address
DB_PORT=3306 
DB_DATABASE=your_db_name //database name jika belum dibuat maka akan dibuatkan
DB_USERNAME=root // by default
DB_PASSWORD=your-db-password 
```
*sesuaikan dengan database yang telah disiapkan sebelumnya [[Ubuntu cloud compute#setup database]]*

pastikan seluruh konfigurasi awal termasuk package composer yang diperlukan telah terinstall.
## Setup Nginx
final step, kita akan setup webserver untuk melayani aplikasi laravel kita.

pergi ke direktori utama/home
```
cd
```

pindahkan direktori project anda ke path `/var/www/`, dengan command berikut : 
```
sudo mv ~/Your_Project /var/www/Your_Project
```
*sesuaikan dengan nama direktori laravel app **Your_Project** *
### set permission
```
sudo chown -R :www-data /var/www/Your_Project/storage/

sudo chown -R :www-data /var/www/Your_Project/bootstrap/cache/

sudo chmod -R 0777 /var/www/Your_Project/storage/
```
*sesuaikan dengan nama direktori laravel app **Your_Project** *

```
sudo nano /etc/nginx/sites-available/Your_Project
```
*sesuaikan dengan nama direktori laravel app **Your_Project** *

[copy configurasi pada dokumentasi laravel](https://laravel.com/docs/10.x/deployment#nginx)
```
server_name extrnl_ip_or_your_domain.com;

root /var/www/html/Your_Project/public;
```
*sesuaikan pada line 4 dan 5 *

- pada line 4 masukan external/public ip atau domain yang anda gunakan untuk menjalankan apikasi
- pada line 5 ubah menjadi nama folder aplikasi anda 
- maka akan mendapati hasil seperti berikut : 
```
server {

listen 80;
listen [::]:80;
server_name 35.213.134.147;
root /var/www/AbadiComm_Site/public;

add_header X-Frame-Options "SAMEORIGIN";
add_header X-Content-Type-Options "nosniff";

index index.php;

charset utf-8;

location / {

try_files $uri $uri/ /index.php?$query_string;

}

location = /favicon.ico { access_log off; log_not_found off; }

location = /robots.txt { access_log off; log_not_found off; }

error_page 404 /index.php;

location ~ \.php$ {

fastcgi_pass unix:/var/run/php/php8.2-fpm.sock;

fastcgi_param SCRIPT_FILENAME $realpath_root$fastcgi_script_name;

include fastcgi_params;

}

location ~ /\.(?!well-known).* {

deny all;

}

}
```
*perhatikan dengan teliti pada penyesuain*

confirmasi bahwa tidak ada syntax error, dengan prom berikut :
```
sudo nginx -t
```
jika berjalan dengan baik dan benar maka akan didapati output sebagai berikut :
```
Outputnginx: the configuration file /etc/nginx/nginx.conf syntax is ok
nginx: configuration file /etc/nginx/nginx.conf test is successful
```

untuk menerapkan perubahan maka lakukan reload pada *nginx*, dengan command berikut :
```
sudo systemctl reload nginx
```

coba kunjungi melalui web browser anda menggunakan external/public ip atau domain yang sudah anda hubungkan.

## Conclusion
Setelah kita melewati *step-by-step* yang cukup menyenangkan tersebut kita telah belajar beberapa hal yaitu : 
1. Cloud VM
2. Cloud computing dan Serverless architecture
3. Penggunaan *Webserver*
4. VPC Networks

masih banyak hal-hal menarik tentang Google Cloud Platform dan kita dapat memiliki kesempatan untuk belajar bersama-sama dengan mengikuti program dari Google yaitu [Google Developer Student Clubs](https://gdsc.community.dev/universitas-ciputra-surabaya-1/) dan masih banyak lagi cabang keilmuan lainnya yang tidak kalah menarik. Saya pribadi senang jika dengan adanya artikel ini membantu anda dan apabila ada kritik maupun saran silahkan sertakan dikolom komentar, Terimakasih.
## Notes

## Database Host berubah ketika restart/stop
Layanan vpc reserved external ip tidak tersedia pada database sql karena database sql tidak mendukung penggunaan alamat IP statis. Alamat IP statis adalah alamat IP yang selalu sama, bahkan ketika server dimatikan dan dihidupkan kembali. Database sql menggunakan alamat IP dinamis, yang berarti bahwa alamat IP dapat berubah ketika server dimatikan dan dihidupkan kembali.

Alasan database sql menggunakan alamat IP dinamis adalah untuk meningkatkan ketersediaan. Jika server database sql mati, alamat IP akan dibebaskan dan dapat digunakan oleh server database sql lain. Hal ini memastikan bahwa database sql selalu dapat diakses, bahkan ketika satu server database sql mati.

#### Solusinya
setiapkali instance database berhenti maka kita harus mengubah host pada file `.env` atau kita menggunakan *Load balancer* yang sudah disediakan menjadi sebuah produk *GCP*
####  Nginx failed pasca restart/stop
hal tersebut tidak dalukannya automasi maka anda dapat melakukan langkah berikut :

matikan seluruh server yang telah berjalan sebab memungkinkan konflik pada port
```
sudo killall apache2
```

nyalakan kembali nginx
```
sudo systemctl start nginx
```

lakukan pengecekan pada berjalanya nginx
```
sudo service nginx status

sudo nginx -t
```

lakukan reload jika ada perubahan saat nginx berhenti
```
sudo systemctl reload nginx
```

jika belum melakukan automasi untuk restart dapat mengikuti pada tahapan [[Ubuntu cloud compute#autostart pada nginx]]



## Rererences
- https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-laravel-with-nginx-on-ubuntu-22-04
- https://www.nicesnippets.com/blog/install-laravel-on-ubuntu-2204-with-nginx-example
- https://computingforgeeks.com/how-to-install-php-8-2-on-ubuntu/
- https://utho.com/docs/tutorial/how-to-install-php-8-2-on-ubuntu-22-04/
- https://medium.com/@henri706/how-to-install-php-fpm8-2-on-ubuntu-22-04-lts-d74c9b8ed9dd
- https://serverfault.com/questions/964568/can-not-restart-nginx-job-for-nginx-service-failed-because-the-control-process
- https://www.ispmanager.com/docs/ispmanager-lite/if-nginx-does-not-start-after-rebooting-the-server
- https://www.nginx.com/resources/glossary/nginx/