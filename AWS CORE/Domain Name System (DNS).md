ketika anda ingin mencari sebuah letak rumah teman anda maka anda harus mengetahui alamatnya bukan?, sama dengan ketika anda ingin menuju sebuah website maka anda harus mengetahui alamat website tersebut, maka alamat website tersebut dinamakan IP Address / Alamat IP (Internet Protocol)

Setiap website memiliki alamat yang mana alamat tersebutlah akan mengarahkan dimana website tersebut ketika ada yang ingin mengaksesnya.

anda memiliki teman bernama Joni lalu ia ingin kamu mencatat alamat rumahnya untuk bermain besok, maka anda akan menulis:

**Rumah Joni** *(**DNS**)* 
Jl.ahmad yani No.3 Surabaya jawa timur. *(**IP Address***) 

Dimana ketika anda membuka catatannya lagi maka kata kunci yang akan anda cari adalah "Rumah Joni" dan akan menunjukan alamat rumahnya yang menuntun anda ke rumah si Joni, sederhananya ketika anda mengetik DNS maka anda akan menuju IP address website tersebut.

Ibarat sebuah buku daftar telefon ketika anda mencari Nomor untuk menghubungi  Damkar maka anda akan menemukan nomor telefon yang ketika anda hubungi akan tersambung dengan damkar itu, Buku daftar telfon itu adalah ibarat DNS yang mana ketika anda mencari www.contohDnsDamkar.com maka anda akan diarahkan pada IP Address dari website Damkar itu.

![[Pasted image 20230305224710.png]]
*Di AWS tersedia layanan DNS yang dapat Anda gunakan, yakni Amazon Route 53* #AmazonRoute53

Mari kita ambil contoh bagaimana DNS bekerja. Katakanlah Anda ingin membuka halaman www.example.com.

1.  Masukkan nama domain tersebut ke browser Anda.
2.  Lalu, permintaan tersebut akan dikirimkan ke Amazon Route 53 guna memperoleh alamat IP yang sesuai dengan website tersebut.
3.  Route 53 merespons dengan memberikan alamat IP. Misalkan 80.17.25.131.
4.  Kemudian, komputer atau browser Anda pun akan dirutekan ke alamat tadi.
5.  Tada! Website pun termuat.

