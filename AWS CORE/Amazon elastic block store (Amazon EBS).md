#AmazonEBS #AmazonElasticBlockStore #blockstorage 

Amazon EBS adalah **Layanan** *block level storage* yang dapat digunakan di EC2 Instance.

Amazon EBS memungkinkan Anda untuk membuat _hard drive_ virtual (EBS volume) yang kemudian bisa di-_attach_ (dipasang) ke EC2 instance.

berbeda dengan #InstanceStorage dia memiliki penempatan yang berbeda dan tidak terikat secara langsung dengan host yang menjalankan *EC2 Instance*.

![[Pasted image 20230306105650.png]]

Sebab Amazon EBS tidak terikat langsung dengan Host maka ketika *Instance* dijalankan ulang data yang terdapat di Amazon EBS tidak akan hilang berkat penempatannya yang berbeda. 

penting untuk anda melakukan *backup data* yang terdapat di Amazon EBS sebab seringkali berisi data presisten, untuk melakukan pencadangan EBS volume anda dapat menggunakan Amazon EBS snapshot.

![[Pasted image 20230306110255.png]]
*Illustrasi kerja EBS Snapshot ketika terdapat pembaruan (Incerement BackUp)* 
#AmazonEBSsnapshot disimpan secara bertahap/inkremental. Itu berarti pada saat pertama kali proses pencadangan dilakukan, ia akan menyalin semua data yang ada di EBS volume. Namun, untuk pencadangan berikutnya, ia hanya menyimpan blok data yang berubah dari snapshot terakhir.

Incremental backup ini sesungguhnya berbeda ya dengan full backup (pencadangan penuh). 
#FullBackup itu akan menyalin semua data yang ada di dalam volume setiap pencadangan dilakukan, sementara #incrementalBackup hanya mencadangkan data yang berubah (delta) dari pencadangan sebelumnya.


#HardDrIveVirtual #EBSVolumes #HostStorage #StorageDataPresisten #incrementalBackup 