## Amazon Relational database service (Amazon RDS)
#RelationalDatabase #RDBMS #AmazonRDS #RDS 
*Amazon RDS* adalah layanan Database #RDBMS yang mana menggunakan skema Relasional dengan bahasa SQL. 

Amazon RDS adalah layanan yang terkelola dan mendukung 6 (enam) mesin database, di antaranya:
-   Amazon Aurora
-   PostgreSQL
-   MySQL
-   MariaDB
-   Oracle Database
-   Microsoft SQL Server

Layanan ini memiliki banyak fitur, seperti:
-   Bisa bekerja secara kompatibel dengan MySQL dan PostgreSQL. Bahkan, dapat 5 kali lebih cepat dari database MySQL standar dan bisa 3 kali lebih cepat dari database PostgreSQL standar.
-   Memberikan performa yang setara dengan database komersial dengan perbandingan biaya 1/10.
-   Mampu memastikan replikasi data di seluruh fasilitas.
-   Menerapkan hingga 15 _read replica_ (replika baca).
-   Mencadangkan secara berkelanjutan ke Amazon S3.
-   Menerapkan _point-in-time recovery_ (pemulihan data dari periode tertentu).

Sekarang, mari kita kembali ke pembahasan mengenai Amazon RDS. Layanan Amazon RDS hadir dengan berbagai fitur, termasuk:
-   _Automated patching_ (memperbaiki masalah dengan memperbarui program).
-   _Backup_ (pencadangan).
-   _Redundancy_ (memiliki lebih dari satu instance untuk berjaga-jaga jika instance utama gagal beroperasi).
-   _Failover_ (instance lain akan mengambil alih saat instance utama mengalami kegagalan).
-   _Disaster recovery_ (memulihkan pascabencana).
-   _Encryption at rest_ (enkripsi data saat disimpan).
-   _Encryption in-transit_ (enkripsi data saat sedang dikirim dan diterima).

## Amazon DynamoDB
#DynamoDB #NonRelational  #AmazonDynamoDB

Layanan databse ini berkebalikan dengan #AmazonRDS yang mana *Amazon DynamoDB* merupakan database nonrelasional (NoSQL) dan menggunakan jenis pendekatan pasangan _key-value_ (kunci-nilai).

Selain itu, Amazon DynamoDB juga menyimpan data di beberapa perangkat di seluruh availability zone. Sehingga, ini menjadikannya database yang _highly available_ (sangat tersedia). Layanan ini memiliki kinerja yang sangat tinggi. Ia punya _response time_ (waktu respons) kilat, yakni milidetik, yang akan sangat bermanfaat untuk aplikasi dengan potensi jutaan pengguna.

## AMAZON DynamoDB vs AMAZON RDS
#AmazonRDS #AmazonDynamoDB #AmazonRDSVSAmazonDynamoDb 

Amazon DynamoDB = Non relational 
AMAZON RDS = relational
Kesamaan keduanya adalah mereka sesama *SQL*

![[Jepretan Layar 2023-03-07 pukul 20.09.00.png]]
Jadi, sebenarnya ini tergantung pada kebutuhan beban kerja Anda. Setiap layanan akan menjadi solusi yang tepat untuk kebutuhan tertentu. Maka pahamilah apa yang Anda butuhkan, dengan begitu Anda akan dapat memilih layanan mana yang ideal.

