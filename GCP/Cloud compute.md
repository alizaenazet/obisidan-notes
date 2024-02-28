
## Buat project
buat project sesuaikan nama projectnya, jika memiliki sebuah organisasi biasanya ini dilakukan oleh sebuah tim untuk berkerja bersama timnya dalam satu project.

## Enable product
[Compute engine market](https://console.cloud.google.com/marketplace/product/google/compute.googleapis.com?returnUrl=%2Fcompute%2Finstances%3F_ga%3D2.157024120.-2115883353.1703158410%26_gac%3D1.216956132.1703158410.Cj0KCQiA4Y-sBhC6ARIsAGXF1g5-wLKMHfH609yJyIoTkGJBVIYLozNHDWYBnXnMsbFH2g9THcHE2K4aAsyJEALw_wcB%26creatingProject%3Dtrue%26project%3Dlaravel-app-408812%26supportedpurview%3Dproject&project=laravel-app-408812&supportedpurview=project . pergi ke halaman tersebut dan klik *enable*. 

## masuk ke dashboard project 
pergi ke dashboard akun dan temukan dibagian navigation (diatas bagian tampilan).
![[Screenshot 2023-12-21 at 19.30.16.png]]

jika anda telah ke dashboard maka akan mendapati tampilan seperti ini : 
![[Screenshot 2023-12-21 at 19.29.08.png]]

pergi ke menu pada pojok kanan atas .
![[Screenshot 2023-12-21 at 19.31.59 1.png]]
*klik pada 'compute engine' lalu 'VM instances'*

## Buat instance baru
pada tampilan dashboard pada bagian atas klik pada menu *CREATE INSTANCE*.
![[Screenshot 2023-12-21 at 19.37.08.png]]

## install NgneX
![[Screenshot 2023-12-21 at 20.16.11.png]]
buka ssh console dengan klik pada menu *View gcloud command* lalu klik *RUN IN CLOUD SHELL* dan tekan enter. Bisa kalian sesuaikan jika kalian ingin melakukan remote maka lakukan pada terminal ssh client kalian.


jalankan promp berikut satu persatu pada setiap line secara berurutan :
```
sudo apt-get update
sudo apt -y upgrade
sudo apt install nginx -y
```
*dibutuhkan waktu yang cukup lama, maka anda akan melakukan update dan sekaligus melakukan install pada nginx di cloud instance kalian*

setelah dirasa berhasil melakukan install maka verifikasi dengan menjakankan promp berikut
```
sudo /etc/init.d/nginx status
```

maka akan menunjukan hasil seperti berikut :
```
● nginx.service - A high performance web server and a reverse proxy server
     Loaded: loaded (/lib/systemd/system/nginx.service; enabled; vendor preset: enabled)
     Active: active (running) since Thu 2023-12-21 13:14:39 UTC; 21min ago
       Docs: man:nginx(8)
    Process: 2206 ExecStartPre=/usr/sbin/nginx -t -q -g daemon on; master_process on; (code=exited, status=0/SUCCESS)
    Process: 2207 ExecStart=/usr/sbin/nginx -g daemon on; master_process on; (code=exited, status=0/SUCCESS)
   Main PID: 2396 (nginx)
      Tasks: 3 (limit: 4691)
     Memory: 5.7M
        CPU: 41ms
     CGroup: /system.slice/nginx.service
             ├─2396 nginx: master process /usr/sbin/nginx -g daemon on; master_process on;
             ├─2399 nginx: worker process
             └─2400 nginx: worker process

Dec 21 13:14:39 web-app systemd[1]: Starting A high performance web server and a reverse proxy server...
Dec 21 13:14:39 web-app systemd[1]: Started A high performance web server and a reverse proxy server.
```

kalian juga bisa mencoba dengan melakukan akses pada browser anda pada url  *External IP address* pada instance 
![[Screenshot 2023-12-21 at 20.38.14.png]]


## Install php modules
```
sudo apt update
```

### Add Surý APT repository
PHP 8 packages for Debian tersedia pada [DEB.SURY.ORG](https://deb.sury.org/). maka diperlukan melakukan install pada dependensi dengan cara berikut :
```
sudo apt install -y lsb-release ca-certificates apt-transport-https software-properties-common gnupg2
```
*jalankan pada CLOUD SHELL*

#### Add the PHP packages APT repository to your Debian server.
```
echo "deb https://packages.sury.org/php/ $(lsb_release -sc) main" | sudo tee /etc/apt/sources.list.d/sury-php.list
```

#### Import repository key:
```
wget -qO - https://packages.sury.org/php/apt.gpg | sudo apt-key add -
```

```
sudo apt update
```

#### instal php versi 8.1 
lakukan install pada versi php yang anda inginkan sebab saat ini laravel 10 membutuhkan minimum versi php 8.0 maka saya akan menggunakan versi 8.1
```
sudo apt install php8.1
```
*pada proses Do you want to continue? isi dengan `y`*

lakukan verifikasi instalasi
```
php -v
```
*akan memberikan informasi php yang terinstall*

```
php --ini

// menampilkan sebuah baris berikut :
Loaded Configuration File:         /etc/php/8.1/cli/php.ini
```
*jika tidak menampilkan configuration file dengan sesuai versi php yang anda install silahkan ulangi proses install php kembali dan pastion menggunakan `sudo apt install php8.x` *

## install composer
https://getcomposer.org/doc/00-intro.md#globally

## install nodejs and npm
```
apt install nodejs npm
```

verivikasi instalasi dan versi
```
node -v
```
jika versi anda 

### Setup laravel
#### clone from github repostiory
```
git clone https://github.com/yourusername/yourrepostiory.git
```
*gunakan clone menggunakan https url atau protokol yang anda lebih anda inginkan*

install requirement pada laravel
```
npm install
composer update
composer install;
cp .env.example .env
php artisan key:generate;

```

jika pada `composer install ` mendapati error seperti berikut : 
```
You can also run `php --ini` in a terminal to see which files are used by PHP in CLI mode.
Alternatively, you can run Composer with `--ignore-platform-req=ext-simplexml --ignore-platform-req=ext-dom --ignore-platform-req=ext-xml --ignore-platform-req=ext-curl` to temporarily ignore these required extensions.
```

maka anda yang perlu fokus pada teks didalam backtick pada kasus tersebut adalah `--ignore-platform-req=ext-simplexml --ignore-platform-req=ext-dom --ignore-platform-req=ext-xml --ignore-platform-req=ext-curl`

sehingga anda dapat melanjutkan dengan menambahkan command tersebeut setelah promp pada composer menjadi seperti berikut : 
```
composer install --ignore-platform-req=ext-simplexml --ignore-platform-req=ext-dom --ignore-platform-req=ext-xml --ignore-platform-req=ext-curl
```

### connect with database
![[Screenshot 2023-12-22 at 00.08.49.png]]
![[Screenshot 2023-12-22 at 00.09.10.png]]

pergi ke layanan SQL dan klik pada mysql lalu pilih instance yang telah dibuat sebelumnya.
![[Screenshot 2023-12-22 at 00.17.30.png]]

setelah itu kembali ke cloud shell VM yang kalian akan digunakan dan jalankan promp berikut untuk menginstall sql client:
```

```


![[Screenshot 2023-12-22 at 00.22.28.png]]
lalu gunakan untuk terkoneksi dengan databse sebelumnya dengan menjalankan prom berikut :
```
mysql -h INSTANCE_IP \ -u USERNAME -p
```
*Instance Ip ada pada dashboard instance database secara default username adalah `root`*
untuk keluar tekan kombinasi `control + c` .

kembali ke project anda dan masuk ke `env` dengan command `nano .env`, setting sesuai dengan kebutuhan, contoh:
```
DB_CONNECTION=mysql
DB_HOST=34.101.213.182 // public ip address
DB_PORT=3306 
DB_DATABASE=your_db_name //database name jika belum dibuat maka akan dibuatkan
DB_USERNAME=root // by default
DB_PASSWORD=your-db-password 
```





```
php artisan migrate; // jika terdapat database migrations
php artisan db:seed; // jika terdapat db seed
php artisan storage:link; // jika menggunakan local storage system
npm run build // build seluruh view
sudo php artisan config:cache; 
php artisan route:cache;
php artisan view:cache;
```

## setup nginx untuk laravel



## setup mysql database instance
