#InstanceStore  #InstanceStoreVolume
Instance store (tempat penyimpanan instance) adalah penyimpanan block-level storage sementara untuk Amazon EC2 instance. Saat Anda meluncurkan EC2 instance--tergantung tipe EC2 instance yang Anda pilih--biasanya sudah tersedia penyimpanan lokal alias instance store volume di dalamnya.

Volume ini secara fisik terpasang ke _host_ (mesin fisik), yaitu tempat di mana EC2 instance Anda berjalan. Anda dapat melakukan proses _write_ (menulis) data padanya seperti _hard drive_ pada umumnya.


![[Pasted image 20230306104239.png]]

sebab Instance store bersifat menyimpan sementara ketika Instance tersebut Stop (berhenti bekerja) maka semua yang disimpan pada Instance store akan terhapus, hal tersebut mengakibatkan ketika instance Start (mulai bekerja) kembali maka akan kosong seperti semula, itu terjadi dikarenakan pada saat instance dimulai kembali dia memiliki kemungkinan berjalan di host yang berbeda.

dari sifat si Instance store maka biasanya dia digunakan untuk menyimpan data yang sering berubah, seperti _cache,_ _temporary file_ (file sementara), data yang dapat dibuat ulang dengan mudah, dan konten sementara lainnya bukan data penting.

#PenyimpananSementara #PenyimpananPadaInstance 

