#AmazonEFS #AmazonElasticFileSystem #fileStorage #blockstorage

*Amazon EFS* adalah layanan *file storage*, yang berarti client,aplikasi,server dsb dapat mengakses penyimpanan dengan bersamaan.

file server menggunakan *block storage (penyimpanan blok)* untuk mengatur penyimpanan didalamnya menggunakan system *locak file system(sistem file lokal)*.

dibandingkan #blockstorage dan #objectStorage *Amazon EFS* lebih ideal untuk keadaan dimana banyak akses secara bersamaan, itu berarti EFS memungkin beberapa *instance* melakukan proses read dan write pada data secara bersamaan.

EFS dapat memiliki beberapa #instance yang mengakses data secara bersamaan, EFS akan  melakukan proses scalling otomatis #ScaleUp #ScaleOut apabila diperlukan sebab akses data yang masif.

*Amazon EFS* sistem file untuk linux dan merupakan *Regional resource(Sumberdaya regional)*. itu berarti pada setiap #Region data akan disimpan dibeberapa #AZ . Dengan demikian, setiap EC2 instance yang berada di Region yang sama dapat menyimpan data ke sistem file Amazon EFS.

Amazon EFS adalah sistem file terkelola yang bisa diskalakan dan dapat digunakan oleh layanan AWS Cloud dan sumber daya di data center on-premise.

*Regional resource* adalah yang membedakan antara Amazon EFS dengan #AmazonEBS , Amazon EBS volume dilampirkan ke EC2 instance dan merupakan _Availability Zone-level resource_ atau sumber daya tingkat Availability Zone. Itu artinya, EBS akan menyimpan data hanya di satu Availability Zone (AZ). Terlebih lagi, jika Anda ingin memasang EC2 ke EBS, maka Anda harus berada di AZ yang sama.

