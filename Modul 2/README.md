[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/99wpTe72)
| Name           | NRP        | Kelas     |
| ---            | ---        | ----------|
| Agnes Priscilla S.H | 5025221295 | Jaringan Komputer F |
| Justin Chow | 5025231087 | Jaringan Komputer F |

## Find your topology here!

- Link: https://drive.google.com/drive/folders/1ECQD6-cQkg0DzyflG-jSxJZaGaxg0KSU?usp=sharing

- Topology distribution for groups: https://docs.google.com/spreadsheets/d/1QKEZjixTStNbdXznOalJoJS0UQ6ed23o51pP8t8eAIM/edit?gid=1757558734#gid=1757558734

## Put your topology config image here!

![Topology F04](https://github.com/user-attachments/assets/09443ab1-4d2f-4111-b2a6-0b2a5b19ace6)

<br>

## Soal 1

> Topologi terdiri dari node Wortel yang berupa DNS Master*. Selain itu, terdapat pula node Pokcoy sebagai DNS Slave*, yang bertugas sebagai cadangan dari node Wortel.
> <br> </br>
> Selanjutnya terdapat node Tomat dan Taoge yang bekerja sebagai Client*, tiga buah Web Server* yaitu Bayam, Buncis, dan Brokoli, serta Mayur sebagai Router*. Buatlah topologi sesuai dengan pembagian topologi [di sini](https://docs.google.com/spreadsheets/d/1QKEZjixTStNbdXznOalJoJS0UQ6ed23o51pP8t8eAIM/edit?usp=sharing) dan konfigurasi topologi [di sini](https://drive.google.com/drive/folders/1ECQD6-cQkg0DzyflG-jSxJZaGaxg0KSU?usp=sharing). Pastikan bahwa setiap node dapat terhubung ke Internet.

> _The topology consists of a Wortel node which is a DNS Master*. In addition, there is also a Pokcoy node as a DNS Slave*, which serves as a backup for the Wortel node._
> <br> </br>
> _Furthermore, there are Tomat and Taoge nodes that work as Client*, three Web Servers*, namely Bayam, Buncis, and Brokoli, then finally Mayur as Router*. Make a topology according to the topology division [here](https://docs.google.com/spreadsheets/d/1QKEZjixTStNbdXznOalJoJS0UQ6ed23o51pP8t8eAIM/edit?usp=sharing) and the topology configuration [here](https://drive.google.com/drive/folders/1ECQD6-cQkg0DzyflG-jSxJZaGaxg0KSU?usp=sharing). Make sure that each node can connect to the Internet._

**Answer:**

- Screenshot

![image](https://github.com/user-attachments/assets/d5e5a9a5-5047-4ac7-b648-3561fb73d7b3)

- Explanation

1. Atur konfigurasi untuk masing-masing node

MAYUR ROUTER
```
auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
	address 192.235.1.1
	netmask 255.255.255.0

auto eth2
iface eth2 inet static
	address 192.235.2.1
	netmask 255.255.255.0

auto eth3
iface eth3 inet static
	address 192.235.3.1
	netmask 255.255.255.0
```

TOMAT CLIENT
```
auto eth0
iface eth0 inet static
	address 192.235.1.2
	netmask 255.255.255.0
	gateway 192.235.1.1
```

TAUGE CLIENT
```
auto eth0
iface eth0 inet static
	address 192.235.1.3
	netmask 255.255.255.0
	gateway 192.235.1.1
```

POKCOY DNS SLAVE
```
auto eth0
iface eth0 inet static
	address 192.235.2.2
	netmask 255.255.255.0
	gateway 192.235.2.1
```

BROKOLI WEB SERVER
```
auto eth0
iface eth0 inet static
	address 192.235.2.3
	netmask 255.255.255.0
	gateway 192.235.2.1
```

BUNCIS WEB SERVER
```
auto eth0
iface eth0 inet static
	address 192.235.2.4
	netmask 255.255.255.0
	gateway 192.235.2.1
```

BAYAM WEB SERVER
```
auto eth0
iface eth0 inet static
	address 192.235.2.5
	netmask 255.255.255.0
	gateway 192.235.2.1
```

WORTEL DNS MASTER
```
auto eth0
iface eth0 inet static
	address 192.235.3.2
	netmask 255.255.255.0
	gateway 192.235.3.1
```

2. Ketikkan `iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE -s 192.235.0.0/16` pada router MAYUR. Setelah itu ketikkan command `cat /etc/resolv.conf`

3. Masukkan command `echo nameserver 192.168.122.1 > /etc/resolv.conf` pada semua node yang ada dan coba `ping google.com` untuk memastikan bahwa semua node sudah tersambung

4. Melakukan scripting dalam direktori `/root`:
   - Melakukan command `nano /root/.bashrc` untuk menambahkan scripting:
   - Untuk MayurRouter, tambahkan `iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE -s 192.235.0.0/16` di baris terakhir agar kita dapat mengakses jaringan ke luar
   - Untuk node selain MayurRouter, di baris terakhir tambahkan `echo nameserver 192.168.122.1 > /etc/resolv.conf` agar semuanya dapat tersambung ke internet.

<br>

## Soal 2

> Tambahkan konfigurasi untuk domain bayam.yyy.com yang mengarah ke IP node Bayam di DNS Master. Dengan cara yang sama, buat konfigurasi domain brokoli.yyy.com yang mengarah ke IP node Brokoli dan domain buncis.yyy.com yang mengarah ke IP node Buncis. Simpan semua konfigurasi dalam folder Jarkom. Selama pengerjaan soal, ubah yyy menjadi kode kelompok masing-masing (contoh: A02).
> <br> </br>
> Jangan lupa update konfigurasi kedua client agar dapat berkomunikasi dengan semua domain tersebut.

> _Add a configuration for bayam.yyy.com domain that points to the Bayam node IP in the DNS Master. In the same way, create a brokoli.yyy.com domain configuration that points to the Brokoli node IP and a buncis.yyy.com domain that points to the Buncis node IP. Save all configurations in a folder called Jarkom. For this practicum, substitute yyy with the code of each group (ex: A02).
> <br> </br> 
> Don't forget to update the configuration of both clients so that they can communicate with the domains._

**Answer:**

- Screenshot

![image](https://github.com/user-attachments/assets/4e170ea3-f834-45ae-b0cb-873b8f3588e4)

- Explanation

Menambahkan konfigurasi di DNS Master dan menyimpan semua konfigurasi dalam folder Jarkom dengan yyy merupakan kode kelompok (f04). Kita perlu mengetikkan command seperti di bawah ini pada Wortel DNS Master dan menyimpannya dalam sebuah folder bernama `Jarkom`

Lakukan instalasi bind 
```
apt-get update
apt-get install bind9 -y
```

Lalu, edit file `/etc/bind/named.conf.local`.
Tambahkan konfigurasi berikut untuk membuat domain `bayam.f04.com`, `brokoli.f04.com`, dan `buncis.f04.com`:
```
zone "bayam.f04.com" {
	type master;
	file "/etc/bind/jarkom/bayam.f04.com";
};

zone "brokoli.f04.com" {
	type master;
	file "/etc/bind/jarkom/brokoli.f04.com";
};

zone "buncis.f04.com" {
	type master;
	file "/etc/bind/jarkom/buncis.f04.com";
};
```

Buat direktori 
```
mkdir /etc/bind/jarkom
```

Copy file `db.local` ke direktori tersebut 
```
cp /etc/bind/db.local /etc/bind/jarkom/bayam.f04.com
cp /etc/bind/db.local /etc/bind/jarkom/buncis.f04.com
cp /etc/bind/db.local /etc/bind/jarkom/brokoli.f04.com
```

Buka file `bayam.f04.com`, `buncis.f04.com`, dan `brokoli.f04.com` dan edit seperti gambar di bawah ini 
```
nano /etc/bind/jarkom/bayam.f04.com
nano /etc/bind/jarkom/buncis.f04.com
nano /etc/bind/jarkom/brokoli.f04.com
```
![image](https://github.com/user-attachments/assets/10830b39-798e-4b21-b4b1-1c46bd5f81ef)

Lalu, lakukan restart bind9 agar perubahan dalam file konfigurasi dapat ditampilkan dengan baik
```
service bind9 restart
```

Selanjutnya, kita bisa melakukan pengetesan pada node client lain (Tomat atau Tauge) untuk memastikan bahwa konfigurasi sudah benar.  
Di client yang akan digunakan, edit dan tambahkan nameserver dari DNS Master di dalam file `/etc/resolv.conf`:
```
nameserver 192.235.3.2 
````
Lakukan ping untuk mengetes bahwa domain sudah terkonfigurasi dengan baik
```
ping bayam.f04.com -c 5
ping brokoli.f04.com -c 5
ping buncis.f04.com -c 5
```

<br>

## Soal 3

> Tambahkan domain alias berupa www.bayam.yyy.com pada alamat bayam.yyy.com dan www.brokoli.yyy.com pada alamat brokoli.yyy.com.

> _Add a domain alias in the form of www.bayam.yyy.com to the bayam.yyy.com address and www.brokoli.yyy.com to the brokoli.yyy.com address._

**Answer:**

- Screenshot

![image](https://github.com/user-attachments/assets/5596170d-ddc1-4cad-b77d-95ef638c8877)

- Explanation

Untuk menambahkan domain alias, kita perlu menambahkan record `CNAME` dalam konfigurasi domain kita.

Buka file `bayam.f04.com` dan `brokoli.f04.com` dan edit seperti gambar di bawah ini 
```
nano /etc/bind/jarkom/bayam.f04.com
nano /etc/bind/jarkom/brokoli.f04.com
```
![image](https://github.com/user-attachments/assets/9000c516-dbff-4af0-b10d-7347604d9d49)
![image](https://github.com/user-attachments/assets/3e5e92af-2a39-4433-b04d-893fdcc1ad33)

Lalu, lakukan restart bind9 agar perubahan dalam file konfigurasi dapat ditampilkan dengan baik
```
service bind9 restart
```

Lakukan testing pada node client lain (Tomat atau Tauge) dengan command berikut:
```
host -t CNAME www.bayam.f04.com
ping www.bayam.f04.com -c 5

host -t CNAME www.brokoli.f04.com
ping www.brokoli.f04.com -c 5
```

<br>

## Soal 4

> Tambahkan record reverse domain untuk domain brokoli.yyy.com dan buncis.yyy.com.

> _Add a reverse domain record for brokoli.yyy.com and buncis.yyy.com domains._

**Answer:**

- Screenshot

  `Put your screenshot in here`

![Screenshot 2024-10-02 140351](https://github.com/user-attachments/assets/a88a7fd5-d668-47ec-8a6d-ff67da5b963b)


- Explanation

Untuk menambahkan record reverse domain untuk domain brokoli.f04.com dan buncis.f04.com, kita perlu menambah konfigurasi reverse domain.

Buka file `/etc/bind/named.conf.local`

Tambahkan:
```
zone "2.235.192.in-addr.arpa" {
    type master;
    file "/etc/bind/jarkom/2.235.192.in-addr.arpa";
};
```
Kemudian, copy file `/etc/bind/db.local` agar kita bisa melakukan konfigurasi reverse DNS dan record PTR
```
cp /etc/bind/db.local /etc/bind/jarkom/2.235.192.in-addr.arpa
```

Lalu, edit file `2.235.192.in-addr.arpa` seperti gambar berikut:
```
nano /etc/bind/jarkom/2.235.192.in-addr.arpa
```
![Screenshot 2024-10-02 140219](https://github.com/user-attachments/assets/172a7a2e-9f60-43b9-a4d5-6a5088180f8f)

Lalu, lakukan restart bind9 agar perubahan dalam file konfigurasi dapat ditampilkan dengan baik
```
service bind9 restart
```
apt-get update
apt-get install dnsutils

Lakukan testing pada node client lain (Tomat atau Tauge) dengan command berikut:
```
apt-get update
apt-get install dnsutils
```
Lakukan instalasi `dnsutils` terlebih dahulu agar dapat melakukan testing, kemudian ketikkan command berikut:
```
host -t PTR 192.235.2.3
host -t PTR 192.235.2.4
```


<br>

## Soal 5

> Ubah record SOA dari domain bayam.yyy.com sesuai dengan ketentuan berikut:
> - Lama waktu server slave menunggu untuk mengecek salinan baru server master adalah sebesar 2 jam.
> - Field yang mengatur revisi file zona ini diubah menjadi tanggal awal praktikum (format YYYYMMDD) kemudian diikuti dengan nomor kelompok (contoh untuk kelompok A02 maka nomornya 02).
> - Lamanya waktu server harus menunggu untuk meminta pembaruan lagi dari nameserver master yang tidak responsif sebesar 30 menit.
> - Lama waktu nama domain di-cache secara lokal sebelum kadaluarsa dan kembali ke nameserver otoritatif untuk informasi terbaru sebesar 12 jam.
> - Jika server slave tidak mendapatkan respons dari server master dalam waktu 2 minggu, server tersebut harus berhenti merespons kueri untuk zona tersebut.

> _Change the SOA record of the bayam.yyy.com domain according to the following conditions:_
> - The length of time the slave server waits to check for a new revision of the master server is 2 hours.
> - The field that regulates the revision of this zone file is changed to the start date of the practicum (YYYYMMDD format) then followed by the group number (ex: for A02 the group number would be 02).
> - The length of time the server has to wait to request another update from an unresponsive master nameserver is 30 minutes.
> - The length of time a domain name is cached locally before it expires and returns to an authoritative nameserver for up-to-date information is 12 hours.
> - If the slave server does not get a response from the master server within 2 weeks, it must stop responding to queries for that zone.

**Answer:**

- Screenshot

  `Put your screenshot in here`
  ![Screenshot 2024-10-02 141452](https://github.com/user-attachments/assets/38d3eeec-48eb-412b-ba5a-ffcfbbd208e8)


- Explanation

  `Put your explanation in here`
  
Ubah record SOA dari domain bayam.f04.com sesuai dengan ketentuan berikut:
- Lama waktu server slave menunggu untuk mengecek salinan baru server master adalah sebesar 2 jam. (Refresh)
- Field yang mengatur revisi file zona ini diubah menjadi tanggal awal praktikum (format YYYYMMDD) kemudian diikuti dengan nomor kelompok (contoh untuk kelompok A02 maka nomornya 02). (Serial)
- Lamanya waktu server harus menunggu untuk meminta pembaruan lagi dari nameserver master yang tidak responsif sebesar 30 menit. (Retry)
- Lama waktu nama domain di-cache secara lokal sebelum kadaluarsa dan kembali ke nameserver otoritatif untuk informasi terbaru sebesar 12 jam. (Negative TTL)
- Jika server slave tidak mendapatkan respons dari server master dalam waktu 2 minggu, server tersebut harus berhenti merespons kueri untuk zona tersebut. (Expire)

Sehingga kita dapat langsung mengedit file `bayam.f04.com` menjadi seperti berikut:
```
nano /etc/bind/jarkom/bayam.f04.com
```
 ![Screenshot 2024-10-02 141452](https://github.com/user-attachments/assets/38d3eeec-48eb-412b-ba5a-ffcfbbd208e8)
<br>

## Soal 6

> Untuk menangani request yang berlebih dari client ke ketiga alamat yang tadi dibuat, konfigurasikan node Pokcoy sebagai DNS Slave yang bekerja untuk DNS Master Wortel.

> _To handle excess requests from the client to the three addresses created, configure the Pokcoy node as the DNS Slave that works for Wortel DNS Master._

**Answer:**

- Screenshot

  `Put your screenshot in here`
  ![Screenshot 2024-10-02 150515](https://github.com/user-attachments/assets/d07d55f7-d886-40d2-9f3f-6e392593f97d)

- Explanation

  `Put your explanation in here`
```
Membuat Pockoy menjadi DNS Slave dari DNS Master Wortel

Di Wortel:
nano /etc/bind/named.conf.local

Tambahkan
 
notify yes;
also-notify { 192.235.2.2; }; // IP Pokcoy
allow-transfer { 192.235.2.2; }; // IP Pokcoy

ke ketiga zone

Sehingga menjadi:
![Screenshot 2024-10-02 142201](https://github.com/user-attachments/assets/d2326734-895b-4bc0-92b8-8c7300ec43f6)
![Screenshot 2024-10-02 142229](https://github.com/user-attachments/assets/e01359f9-e382-444e-9650-780016b78740)
`service bind9 restart`

Di Pokchoy:

apt-get update
apt-get install bind9 -y

nano /etc/bind/named.conf.local

zone "bayam.f04.com" {
    type slave;
    masters { 192.235.3.2; }; // IP Wortel
    file "/var/lib/bind/bayam.f04.com";
};

zone "brokoli.f04.com" {
    type slave;
    masters { 192.235.3.2; }; // IP Wortel
    file "/var/lib/bind/brokoli.f04.com";
};

zone "buncis.f04.com" {
    type slave;
    masters { 192.235.3.2; }; // IP Wortel
    file "/var/lib/bind/buncis.f04.com";
};

service bind9 restart

Di Tomat (testing):

nano /etc/resolv.conf

Tambahkan
nameserver 192.235.2.2 // IP Pokcoy

service bind9 stop (matikan server di wortel)
![Screenshot 2024-10-02 150505](https://github.com/user-attachments/assets/c53742c4-6358-4dab-9971-f3e29b51995f)

Testing:
ping bayam.f04.com -c 5
ping brokoli.f04.com -c 5
ping buncis.f04.com -c 5
```
<br>

## Soal 7

> Karena membutuhkan tempat untuk menyimpan resep brokoli, buatlah subdomain berupa vitamin.brokoli.yyy.com dengan alias www.vitamin.brokoli.yyy.com dengan mendelegasikannya dari Wortel ke Pokcoy dengan alamat IP menuju Brokoli yang diatur di folder Vitamin.

> _Since we need a place to store Brokoli recipes, create a subdomain in the form of vitamin.brokoli.yyy.com with an alias of www.vitamin.brokoli.yyy.com by delegating it from Wortel to Pokcoy with an ip to the Brokoli node in a folder called Vitamin._

**Answer:**

- Screenshot

  `Put your screenshot in here`
![Screenshot 2024-10-02 152449](https://github.com/user-attachments/assets/26be726a-72ab-4f53-a32b-ba6423cc77b1)
![Screenshot 2024-10-02 152803](https://github.com/user-attachments/assets/a2c61d72-33e6-4be4-95eb-e3f90cdb90ad)

- Explanation

Pada Wortel DNS Master ubah konfigurasi sesuai gambar di bawah ini 

`Put your screenshot in here`
```
Di Wortel:

nano /etc/bind/jarkom/brokoli.f04.com

Tambahkan:
ns1	IN	A	192.235.2.2 ; IP Pokcoy
vitamin	IN	NS	ns1

nano /etc/bind/named.conf.options

Comment dnssec-validation auto;
Tambahkan allow-query{any;};
![Screenshot 2024-10-02 151216](https://github.com/user-attachments/assets/d4b13a5d-cd84-4e78-95cb-0f94f4993e47)

nano /etc/bind/named.conf.local
Ubah zone brokoli menjadi seperti berikut:

zone "brokoli.f04.com" {
    type master;
    file "/etc/bind/jarkom/brokoli.f04.com”;
    allow-transfer { 192.235.2.2; }; // IP Pokcoy
};

Di Pokcoy:

nano /etc/bind/named.conf.options

Comment dnssec-validation auto;
Tambahkan allow-query{any;};

![Screenshot 2024-10-02 151216](https://github.com/user-attachments/assets/d4b13a5d-cd84-4e78-95cb-0f94f4993e47)

nano /etc/bind/named.conf.local

Tambahkan:

zone "vitamin.brokoli.f04.com" {
    type master;
    file "/etc/bind/vitamin/vitamin.brokoli.f04.com”;
};

![Screenshot 2024-10-02 151845](https://github.com/user-attachments/assets/2b3c2a08-7b40-4468-8295-72d6f3bb5d1b)

mkdir /etc/bind/vitamin
cp /etc/bind/db.local /etc/bind/vitamin/vitamin.brokoli.f04.com

nano /etc/bind/vitamin/vitamin.brokoli.f04.com

![Screenshot 2024-10-02 203300](https://github.com/user-attachments/assets/3ef9d8b2-c498-4f16-a290-25db00608bf4)

service bind9 restart

Di Tomat (testing):

ping vitamin.brokoli.f04.com -c 2
ping www.vitamin.brokoli.f04.com -c 2

host -t CNAME www.vitamin.brokoli.f04.com
```


Buka file `/etc/bind/named.conf.options` dan comment `dnssec-validation auto` serta tambahkan `allow-query{any;};` atau bisa langsung menuliskan sesuai syntax di bawah ini 
```
echo 'options {
	directory "/var/cache/bind";

	// If there is a firewall between you and nameservers you want
	// to talk to, you may need to fix the firewall to allow the multiple
	// ports to talk. See http://www.kb.cert.org/vuls/id/800113

	// If your ISP provided one or more IP addresses for stable
	// nameservers, you probably want to use them as forwarders.
	// Uncomment the following block, and insert the addresses replacing
	// the all-0s placeholder.

    	// forwarders {
    	//      0.0.0.0;
    	// };

	//===================================================================$
	// If BIND logs error messages about the root key being expired,
	// you will need to update your keys. See https://www.isc.org/bind-keys
	//===================================================================$
    	//dnssec-validation auto;
	allow-query{any;};

    	auth-nxdomain no;    # conform to RFC1035
    	listen-on-v6 { any; };
};' > /etc/bind/named.conf.options
```

Edit file `/etc/bind/named.conf.local` sesuai syntax di bawah ini
```
```

Restart bind9 sesuai syntax di bawah ini
```
service bind9 restart
```

Pada Pokcoy DNS Slave buka file `/etc/bind/named.conf.options` dan comment `dnssec-validation auto` serta tambahkan `allow-query{any;};` atau bisa langsung menuliskan sesuai syntax di bawah ini
```
echo 'options {
	directory "/var/cache/bind";

	// If there is a firewall between you and nameservers you want
	// to talk to, you may need to fix the firewall to allow the multiple
	// ports to talk. See http://www.kb.cert.org/vuls/id/800113

	// If your ISP provided one or more IP addresses for stable
	// nameservers, you probably want to use them as forwarders.
	// Uncomment the following block, and insert the addresses replacing
	// the all-0s placeholder.

    	// forwarders {
    	//      0.0.0.0;
    	// };

	//===================================================================$
	// If BIND logs error messages about the root key being expired,
	// you will need to update your keys. See https://www.isc.org/bind-keys
	//===================================================================$
    	//dnssec-validation auto;
	allow-query{any;};

    	auth-nxdomain no;    # conform to RFC1035
    	listen-on-v6 { any; };
};' > /etc/bind/named.conf.options
```

Edit file `/etc/bind/named.conf/local` sesuai syntax di bawah ini
```
echo 'zone "vitamin.brokoli.f04.com" {
	type master;
	file "/etc/bind/vitamin/vitamin.brokoli.f04.com";
};' > /etc/bind/named.conf.local
```

Buat direktori 
```
mkdir /etc/bind/vitamin
```

Copy file `db.local` ke diektori tersebut
```
cp /etc/bind/db.local /etc/bind/vitamin/vitamin.brokoli.f04.com
```

Edit file `vitamin.brokoli.f04.com` seperti gambar di bawah ini

`Put your screenshot in here`

Restart bind9 sesuai syntax di bawah ini 
```
service bind9 restart
```

Lakukan pengetesan pada node client lain (TOMAT atau TAUGE). 
```
echo 'nameserver 192.235.2.2
nameserver 192.235.3.2' > /etc/resolv.conf

ping brokoli.f04.com -c 3
ping vitamin.brokoli.f04.com -c 3
ping www.vitamin.brokoli.f04.com -c 3
```

<br>

## Soal 8

> Buatlah subdomain khusus untuk kandungan brokoli dengan akses k1.vitamin.brokoli.yyy.com dengan alias www.k1.vitamin.brokoli.yyy.com yang mengarah ke IP brokoli dan diatur di folder k1.  

> _Create a special subdomain for Brokoli content called k1.vitamin.brokoli.yyy.com with an alias called www.k1.vitamin.brokoli.yyy.com that point to Brokoli node and are organized in a folder called k1._

**Answer:**

- Screenshot
  `Put your screenshot in here`
![Screenshot 2024-10-02 160458](https://github.com/user-attachments/assets/899b98cb-40c3-4efe-8fcc-e683582a47ae)

- Explanation
```
Di Pokcoy:

nano /etc/bind/named.conf.local

Tambahkan:

zone "k1.vitamin.brokoli.f04.com" {
    type master;
    file "/etc/bind/vitamin/k1/k1.vitamin.brokoli.f04.com”;
};
![Screenshot 2024-10-02 160114](https://github.com/user-attachments/assets/dee7e77b-a089-4524-b658-1b2e6eb2db71)

mkdir /etc/bind/vitamin/k1
cp /etc/bind/vitamin/vitamin.brokoli.f04.com /etc/bind/vitamin/k1/k1.vitamin.brokoli.f04.com

nano /etc/bind/vitamin/k1/k1.vitamin.brokoli.f04.com

![Screenshot 2024-10-02 160427](https://github.com/user-attachments/assets/f6749f8f-9a39-4a49-89d0-427d5d0db485)


service bind9 restart

Di Tomat (testing):


ping k1.vitamin.brokoli.f04.com -c 2
ping www.k1.vitamin.brokoli.f04.com -c 2

host -t CNAME www.k1.vitamin.brokoli.f04.com
```



Pada Pokcoy DNS Slave buka file `/etc/bind/named.conf.options` dan comment `dnssec-validation auto` serta tambahkan `allow-query{any;};` atau bisa langsung menuliskan sesuai syntax di bawah ini 
```
echo 'options {
	directory "/var/cache/bind";

	// If there is a firewall between you and nameservers you want
	// to talk to, you may need to fix the firewall to allow the multiple
	// ports to talk. See http://www.kb.cert.org/vuls/id/800113

	// If your ISP provided one or more IP addresses for stable
	// nameservers, you probably want to use them as forwarders.
	// Uncomment the following block, and insert the addresses replacing
	// the all-0s placeholder.

    	// forwarders {
    	//      0.0.0.0;
    	// };

	//===================================================================$
	// If BIND logs error messages about the root key being expired,
	// you will need to update your keys. See https://www.isc.org/bind-keys
	//===================================================================$
    	//dnssec-validation auto;
	allow-query{any;};

    	auth-nxdomain no;    # conform to RFC1035
    	listen-on-v6 { any; };
};' > /etc/bind/named.conf.options
```

Edit file `/etc/bind/named.conf.local` sesuai syntax di bawah ini
```
echo 'zone "vitamin.brokoli.f04.com" {
	type master;
	file "/etc/bind/vitamin/vitamin.brokoli.f04.com";
};' > /etc/bind/named.conf.local
```

Buat direktori
```
mkdir /etc/bind/vitamin
```

Copy file `db.local` ke direktori tersebut
```
cp /etc/bind/db.local /etc/bind/vitamin/vitamin.brokoli.f04.com
```

Edit file `vitain.brokoli.f04.com` seperti gambar di bawah ini

`Put your screenshot in here`

Restart bind9 sesuai syntax di bawah ini
```
service bind9 restart
```

<br>

## Soal 9

> Bayam, Brokoli, dan Buncis masing-masing berfungsi sebagai web server nginx yang menyajikan resep khusus untuk jenis sayuran yang mereka tangani. Untuk mengaktifkan web server pada masing-masing worker, lakukan deployment website menggunakan sumber yang tersedia di sayur_webserver_nginx. Tambahkan konfigurasi untuk log error ke file /var/log/nginx/error.log dan log access ke file /var/log/nginx/access.log.

> _Bayam, Brokoli, and Buncis each function as nginx web servers that serve special recipes for the type of vegetables they handle. To activate the web server on each worker, do the deployment using the resources available in sayur_webserver_nginx. Add configuration for error log to the file /var/log/nginx/error.log and access log to the file /var/log/nginx/access.log._

**Answer:**

- Screenshot

  `Put your screenshot in here`
![Screenshot 2024-10-02 212754](https://github.com/user-attachments/assets/9b748426-da6c-4adb-8862-9f021355618e)
![Screenshot 2024-10-02 212806](https://github.com/user-attachments/assets/eba0a7a9-6a64-42ed-a4f7-4c1708766aeb)
![Screenshot 2024-10-02 212817](https://github.com/user-attachments/assets/fce0c70d-f24d-4f18-ad1e-48ffed187026)


- Explanation
```
Lakukan semua command di bawah ini ke 3 webserver (ganti nama)

apt-get update
apt-get install nginx
apt-get install unzip
apt install nginx php php-fpm -y
wget -O 'var/www/sayur_webserver_nginx.zip' 'https://docs.google.com/uc?export=download&id=1tFDk7pKRQLd3BMUcyvfAfEL-drvIxdSl' 
unzip -o /var/www/sayur_webserver_nginx.zip -d /var/www

cd /etc/nginx/sites-available
nano buncis

Tambahkan:

server {

	listen 80;

	root "/var/www/sayur_webserver_nginx";

	index index.php index.html index.htm;
	server_name buncis;

	location / {
			try_files $uri $uri/ /index.php?$query_string;
	}

	# pass PHP scripts to FastCGI server
	location ~ \.php$ {
	include snippets/fastcgi-php.conf;
	fastcgi_pass unix:/var/run/php/php7.2-fpm.sock;
	}

location ~ /\.ht {
			deny all;
	}

	error_log /var/log/nginx/error.log;
	access_log /var/log/nginx/access.log;
}

ln -s /etc/nginx/sites-available/buncis /etc/nginx/sites-enabled
service nginx restart

Testing:

apt-get update
apt-get install lynx

lynx [ip webserver]

lynx 192.235.2.4

Jika tampilan masih default:
Di Webserver

cd /etc/nginx/sites-enabled
rm default
service nginx restart
lynx 192.235.2.4

Jika 502 Bad Gateway:
service php7.2-fpm start
service nginx restart
```


Instal Nginx di setiap worker
```
apt-get update
apt-get install bind9 nginx
```
```
echo '
zone "jarkom.site" {
	type master;	
	file "/etc/bind/jarkom/jarkom.site";
};

zone "2.168.192.in-addr.arpa" {
	type master;
	file "/etc/bind/jarkom/2.168.192.in-addr.arpa";
};'
```

Konfigurasi Nginx di server `BrokoliWebServer`
```
apt-get update && apt-get install nginx php php-fpm -y
mkdir /var/www/jarkom
touch /var/www/jarkom/index.php

echo '<?php
$hostname = gethostname();
$date = date("Y-m-d H:i:s");
$php_version = phpversion();
$username = get_current_user();

echo "Hello World! <br>";
echo "Saya adalah: $username<br>";
echo "Saat ini berada di : $hostname<br>";
?>' > /var/www/jarkom/index.php

touch /etc/nginx/sites-available/jarkom

echo 'server {
	listen 8002;

	root /var/www/jarkom;

	index index.php index.html index.htm;
	sever_name _;

	location / {
			try_files $uri $uri/ /index.php?$query_string;
	}

	# pass PHP scripts to FastCGI server
	location ~ \.php$ {
	include snippets/fastcgi-php.conf;
	fastcgi_pass unix:/var/run/php/php7.0-fpm.sock;
	}

location ~ /\.ht {
			deny all;
	}

	error_log /var/log/nginx/jarkom_error.log
	access_log /var/log/nginx/jarkom_access.log
}' > /etc/nginx/sites-available/jarkom

ln -s /etc/nginx/sites-available/jarkom /etc/nginx/sites-enabled
rm -rf /etc/nginx/sites-enabled/default

service php7.0-fpm start
service php7.0-fpm restart
service nginx restart
nginx -t
```

Konfigurasi Nginx di server `BuncisWebServer`
```
apt-get update && apt-get install nginx php php-fpm -y
mkdir /var/www/jarkom
touch /var/www/jarkom/index.php

echo '<?php
$hostname = gethostname();
$date = date("Y-m-d H:i:s");
$php_version = phpversion();
$username = get_current_user();

echo "Hello World! <br>";
echo "Saya adalah: $username<br>";
echo "Saat ini berada di: $hostname<br>";
echo "Versi PHP yang saya gunakan: $php_version<br>";
echo "Tanggal saat ini: $date<br>";
?>' > /var/www/jarkom/index.php

touch /etc/nginx/sites-available/jarkom

echo 'server {
	listen 8001;

	root /var/www/jarkom;

	index index.php index.html index.htm;
	sever_name _;

	location / {
			try_files $uri $uri/ /index.php?$query_string;
	}

	# pass PHP scripts to FastCGI server
	location ~ \.php$ {
	include snippets/fastcgi-php.conf;
	fastcgi_pass unix:/var/run/php/php7.0-fpm.sock;
	}

location ~ /\.ht {
			deny all;
	}

	error_log /var/log/nginx/jarkom_error.log
	access_log /var/log/nginx/jarkom_access.log
}' > /etc/nginx/sites-available/jarkom

ln -s /etc/nginx/sites-available/jarkom /etc/nginx/sites-enabled
rm -rf /etc/nginx/sites-enabled/default

service php7.0-fpm start
service php7.0-fpm restart
service nginx restart
nginx -t
```

Konfigurasi Nginx di server `BayamWebServer`
```
apt-get update && apt-get install nginx php php-fpm -y
mkdir /var/www/jarkom
touch /var/www/jarkom/index.php

echo '<?php
$hostname = gethostname();
$date = date("Y-m-d H:i:s");
$php_version = phpversion();
$username = get_current_user();

echo "Hello World! <br>";
echo "Saya adalah: $username<br>";
echo "Saat ini berada di: $hostname<br>";
echo "Versi PHP yang saya gunakan: $php_version<br>";
echo "Tanggal saat ini: $date<br>";
?>' > /var/www/jarkom/index.php

touch /etc/nginx/sites-available/jarkom

echo 'server {
	listen 8003;

	root /var/www/jarkom;

	index index.php index.html index.htm;
	sever_name _;

	location / {
			try_files $uri $uri/ /index.php?$query_string;
	}

	# pass PHP scripts to FastCGI server
	location ~ \.php$ {
	include snippets/fastcgi-php.conf;
	fastcgi_pass unix:/var/run/php/php7.0-fpm.sock;
	}

location ~ /\.ht {
			deny all;
	}

	error_log /var/log/nginx/jarkom_error.log
	access_log /var/log/nginx/jarkom_access.log
}' > /etc/nginx/sites-available/jarkom

ln -s /etc/nginx/sites-available/jarkom /etc/nginx/sites-enabled
rm -rf /etc/nginx/sites-enabled/default

service php7.0-fpm start
service php7.0-fpm restart
service nginx restart
nginx -t
```

Lakukan pengetesan pada node client lain (TOMAT atau TAUGE).  

`Put your screenshot in here`

<br>

## Soal 10

> Pada masing masing worker nginx, akan terdapat beberapa hal yang perlu diperbaiki pada resource yang diberikan untuk bisa menampilkan resep saat halaman dimuat. Analisis kesalahan yang ada di resource melalui file /var/log/nginx/error.log dan perbaiki hingga halaman bisa menampilkan resep sesuai dengan worker nya.

> _On each nginx worker, there will be several things that need to be fixed in the resources provided to be able to display recipes when the page is loaded. Analyze the errors in the resource through the /var/log/nginx/error.log file and fix it until the page can display recipes according to its worker._

**Answer:**

- Screenshot

  `Put your screenshot in here`
  ![image](https://github.com/user-attachments/assets/34005fc6-2bdf-4624-ba4c-809fe12f0a65)
![image](https://github.com/user-attachments/assets/6ac8c486-ee19-4194-be65-358abba5fd62)


- Explanation

  `Put your explanation in here`
```
  Dari log, kita bisa mendapat informasi yaitu hostname tidak ditemukan. Kemudian cek index.php dan baca line yang melakukan error log ke file error log. Dari situ bisa didapatkan bahwa terdapat kesalahan dalam penulisan nama hostname. Ketika dicocokkan dengan Lynx, ternyata pada lynx ditampilkan bahwa nama hostname yang sedang terhubung adalah BayamWebServer, sedangkan pada index.php, nama hostname dalam switch casenya adalah Bayam saja. Maka, ganti semua nama hostname dengan menambahkan WebServer di akhirnya.

Kemudian, coba lynx ke ip webserver lagi. Ternyata, resep belum bisa ditampilkan, kemudian dari itu dapat ditemukan bahwa ternyata dalam if yang ada dalam switchcase, nama filenya tidak sesuai, dimana seharusnya resep1.php, namun yang tertulis adalah resep_1.php. Oleh karena itu, kita perlu mengganti nama file yang ada dari resep1.php hingga resep3.php.

cd /var/www/sayur_webserver_nginx
nano index.php
![Screenshot 2024-10-02 214119](https://github.com/user-attachments/assets/0d3ae951-0caf-4f8a-bb92-f4c0b3a76b8c)

service nginx restart

Kemudian, lakukan lynx lagi ke ip webserver yang diinginkan, dan resep masakan sudah berhasil ditampilkan dengan baik.
```


<br>

## Soal 11

> Setelah website berhasil dideploy pada masing-masing worker (Bayam, Brokoli, dan Buncis) dan halaman dapat menampilkan resep sayuran yang sesuai,  buatlah custom access log ke file /var/log/nginx/access.log di masing-masing web server worker menggunakan format log tertentu seperti di bawah:
> - Tanggal dan waktu akses dalam format standar log.
Nama worker yang sedang dilayani (misalnya: Bayam, Brokoli, atau Buncis).
> - Alamat IP klien yang mengakses website.
> - Metode HTTP dan URI yang diakses oleh klien.
> - Status respons HTTP yang diberikan oleh server.
> - Jumlah byte yang dikirimkan dalam respons.
> - Waktu yang dihabiskan oleh server untuk menangani permintaan.
> <br> </br>
> Contoh format log yang sesuai: 
[01/Oct/2024:11:30:45 +0000] Jarkom Node Bayam Access from 192.168.1.15 using method "GET /resep/bayam HTTP/1.1" returned stat


> _After successfully deploying the website on each worker (Bayam, Brokoli, and Buncis) and ensuring the pages display the appropriate vegetable recipes, create a custom access log file at /var/log/nginx/access.log on each web server worker using a specific log format as described below:_
> - _Access date and time in standard log format._
> - _Name of the worker serving the request (e.g., Bayam, Brokoli, or Buncis)._
> - _Client IP address accessing the website._
> - _HTTP method and URI accessed by the client._
> - _HTTP response status provided by the server.__
> - _Number of bytes sent in the response.
> - _Time taken by the server to handle the request._
> <br> </br>
> _Example of the appropriate log format:
[01/Oct/2024:11:30:45 +0000] Jarkom Node Bayam Access from 192.168.1.15 using method "GET /resep/bayam HTTP/1.1" returned status 200 with 2567 bytes sent in 0.038 seconds_


**Answer:**

- Screenshot

  `Put your screenshot in here`
  ![Screenshot 2024-10-02 221545](https://github.com/user-attachments/assets/3083c1a0-05c2-4afc-8696-648122f03a71)


- Explanation

  `Put your explanation in here`

```  
cd /etc/nginx/sites-available
nano buncis

Tambahkan di luar dari server:

log_format custom_access_log '[$time_local] Jarkom Node Buncis Access from $remote_addr using method "$request" returned status $status with $body_bytes_sent bytes sent in $request_time seconds';

[$time_local]: Menyimpan waktu dan tanggal akses dalam format lokal (misalnya, [01/Oct/2024:11:30:45 +0000]).
$remote_addr: Menunjukkan alamat IP klien yang mengirim permintaan ke server. 
"$request": Bagian ini mencatat metode HTTP dan URI yang diakses oleh klien. Variabel $request menyimpan seluruh permintaan klien, termasuk metode (GET, POST, dll.), URI yang diminta, dan versi protokol (misalnya, "GET /index.php HTTP/1.1").
$status: Menyimpan status HTTP yang diberikan oleh server setelah menangani permintaan. Misalnya, status 200 untuk sukses, 404 untuk tidak ditemukan, 500 untuk kesalahan internal server, dll.
$body_bytes_sent bytes sent: Menunjukkan jumlah byte yang dikirim oleh server ke klien sebagai respons.
$request_time seconds: Menyimpan waktu yang dibutuhkan server untuk menangani permintaan dari saat diterima hingga respons selesai.
![Screenshot 2024-10-02 220817](https://github.com/user-attachments/assets/df650e35-7e05-449a-86dd-a9d59315e5c1)
Lalu, ubah access_log yang sudah ada di server dengan menambahkan custom_access_log di akhirnya agar access_log yang tercatat sesuai dengan format yang sudah dicustom tadi.
![Screenshot 2024-10-02 220858](https://github.com/user-attachments/assets/938b9c48-5fc6-4991-a458-b229b98152d0)
Lalu, ketika kita melihat acccess lognya di /var/log/nginx/access.log, maka akan nampak bahwa custom_access_log kita telah berjalan dengan baik.
```

<br>

## Soal 12

> Informasi vitamin pada sayur brokoli akan ditampilkan pada subdomain vitamin.brokoli.yyy.com di node brokoli, buatlah DocumentRoot yang disimpan pada /var/www/vitamin.brokoli.yyy. Konfigurasikan webserver dengan nama server vitamin.brokoli.yyy.com dan server alias www.vitamin.brokoli.yyy.com. Lakukan konfigurasi Apache Web Server pada Brokoli dengan menggunakan sumber yang tersedia di [sini](https://docs.google.com/uc?export=download&id=1QbGkKXo3jt4c68AdVAkl1hD4LolTUPg2).

> _For information on vitamins in brokoli will be displayed on the vitamin.brokoli.yyy.com subdomain on the brokoli node, create a DocumentRoot stored in /var/www/vitamin.brokoli.yyy. Configure the web server with the server name vitamin.brokoli.yyy.com and server alias www.vitamin.brokoli.yyy.com. Configure the Apache Web Server on Brokoli using [this resource](https://docs.google.com/uc?export=download&id=1QbGkKXo3jt4c68AdVAkl1hD4LolTUPg2)._

**Answer:**

- Screenshot

  `Put your screenshot in here`
  ![Screenshot 2024-10-02 224539](https://github.com/user-attachments/assets/69442bb6-629b-4e04-98b4-309c162abf9b)


- Explanation

  `Put your explanation in here`
 	 ```
  	apt-get install apache2
	apt-get install php
	
	cd /etc/apache2/sites-available
	
	cp 000-default.conf vitamin.brokoli.f04.com.conf
	
	nano vitamin.brokoli.f04.com.conf
	
	Tambahkan
	ServerName vitamin.brokoli.f04.com
	ServerAlias www.vitamin.brokoli.f04.com
	
	a2ensite vitamin.brokoli.f04.com
	service apache2 restart
   ![Screenshot 2024-10-02 224313](https://github.com/user-attachments/assets/dc275705-d082-4ee4-a9a0-aeda2e594c88)
	Selanjutnya:
	
	cd /
	wget -O 'var/www/vitamin.brokoli.f04.zip' 'https://docs.google.com/uc?export=download&id=1QbGkKXo3jt4c68AdVAkl1hD4LolTUPg2' 
	
	unzip -o /var/www/vitamin.brokoli.f04.zip -d /var/www/
	
	mv /var/www/vitamin.brokoli.yyy.com /var/www/vitamin.brokoli.f04
	
	Tomat (Testing):
	lynx vitamin.brokoli.f04.com atau lynx www.vitamin.brokoli.f04.com

	```

<br>

## Soal 13

> Pada subdomain vitamin.brokoli.yyy.com, terdapat subfolder /nutrisi yang menyediakan informasi tentang berbagai vitamin dalam brokoli, seperti Vitamin A, C, dan K. Aktifkan directory listing untuk folder /nutrisi, dan buatlah rewrite rule di Apache untuk memperbaiki URL agar halaman seperti www.vitamin.brokoli.yyy.com/nutrisi/vitamin_a.php dapat diakses hanya dengan www.vitamin.brokoli.yyy.com/nutrisi/vitamin_a. Pastikan setiap halaman vitamin dapat diakses langsung melalui url yang telah disederhanakan.

> _On the vitamin.brokoli.yyy.com subdomain, there is a /nutrisi subfolder that provides information about various vitamins in brokoli, such as Vitamin A, C, and K. Activate directory listing for the /nutrisi folder, and create a rewrite rule in Apache to fix the URL so that pages like www.vitamin.brokoli.yyy.com/nutrisi/vitamin_a.php can be accessed only with www.vitamin.brokoli.yyy.com/nutrisi/vitamin_a. Make sure each vitamin page can be accessed directly through the simplified url._

**Answer:**

- Screenshot

  `Put your screenshot in here`
  ![Screenshot 2024-10-02 225719](https://github.com/user-attachments/assets/ce60ef60-8583-476d-9a5e-3234055748c4)
![Screenshot 2024-10-02 231807](https://github.com/user-attachments/assets/a10c1989-e882-4116-a4ec-9cf7db7ff193)


- Explanation

```
a2enmod rewrite
service apache2 restart

cd /var/www/vitamin.brokoli.f04/nutrisi

nano .htaccess

Tambahkan:
 RewriteEngine On
 RewriteCond %{REQUEST_FILENAME} !-d
 RewriteRule ^([^\.]+)$ $1.php [NC,L]

cd /etc/apache2/sites-available

nano vitamin.brokoli.f04.com.

Tambahkan:

 <Directory /var/www/vitamin.brokoli.f04/nutrisi>
     Options +FollowSymLinks -Multiviews
     AllowOverride All
 </Directory>
![Screenshot 2024-10-02 234831](https://github.com/user-attachments/assets/6bc62b74-750e-415e-b9ec-d0d07dfbf85b)
service apache2 restart
lynx www.vitamin.brokoli.f04.com/nutrisi/

```


Pada Brokoli Web Server ketikkan sesuai syntax di bawah ini 
```
echo '<VirtualHost *:80>
	ServerAdmin webmaster@localhost
	DocumentRoot /var/www/vitamin.brokoli.f04
	ServerName vitamin.brokoli.f04.com
	ServerAlias www.vitamin.brokoli.f04.com

	<Directory /var/www/vitamin.brokoli.f04/public/>
		Options +Indexes
	</Directory>

	<Directory /var/www/vitamin.brokoli.f04/secret/>
		Options -Indexes
	</Directory>

	ErrorLog ${APACHE_LOG_DIR}/error.log
	CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>' > /etc/apache2/sites-available/parikesit.abimanyu.a08.com.conf

a2enmod rewrite vitamin.brokoli.f04.com.conf
a2ensite vitamin.brokoli.f04.com.conf
service apache2 restart

rm -rf /var/www/vitamin.brokoli.f04
mkdir var/www/vitamin.brokoli.f04
wget 'https://drive.usercontent.google.com/download?id=1LdbYntiYVF_NVNgJis1GLCLPEGyIOreS&export=download&authuser=0&confirm=t&uuid=7440274a-d695-44db-8cd9-70df5bbf7c96&at=APZUnTWw6S5Rd4s_a6CHfvUKTqQG:1696947964978'
unzip -j /var/www/vitamin.brokoli.f04/vitamin_brokoli.zip -d /var/www/vitamin.brokoli.f04
rm -rf /var/www/vitamin.brokoli.f04/vitamin_brokoli.zip

mv /var/www/vitamin.brokoli.f04/vitamin.brokoli.yyy.com/public
mv /var/www/vitamin.brokoli.f04/vitamin.brokoli.yyy.com/error
mkdir /var/www/vitamin.brokoli.f04/secret
cp /var/www/vitamin.brokoli.f04/error/403.html
rm -rf /var/www/vitamin.brokoli.f04/vitamin.brokoli.yyy.com
```

Command yang dituliskan dalam directory public adalah `Option +Indexes` yang mana directory tersebut dapat diakses secara bebas

Command yang dituliskan dalam directory secret adalah `Option -Indexes` yang man directory tersebut tidak dapat diakses oleh pengguna

Tes akses directory public 

`Put your screenshot in here`

Tes akses directory secret 

`Put your screenshot in here`

<br>

## Soal 14

> Tambahkan alias untuk folder /public/images/ pada subdomain www.vitamin.brokoli.yyy.com agar folder tersebut dapat diakses langsung melalui url www.vitamin.brokoli.yyy.com/img.

> _Add an alias for the /public/images/ folder on the www.vitamin.brokoli.yyy.com subdomain so that the folder can be accessed directly through the url www.vitamin.brokoli.yyy.com/img._

**Answer:**

- Screenshot

  `Put your screenshot in here`
![Screenshot 2024-10-02 232702](https://github.com/user-attachments/assets/cb03b1a1-476c-4749-8e05-a369137221ef)

- Explanation

  `Put your explanation in here`
```
  cd /etc/apache2/sites-available

nano vitamin.brokoli.f04.com.

Tambahkan:

 <Directory /var/www/vitamin.brokoli.f04/public/images>
     Options +Indexes
 </Directory>

 Alias "/img" "/var/www/vitamin.brokoli.f04/public/images"
![Screenshot 2024-10-02 233904](https://github.com/user-attachments/assets/b7c0e1bb-bdbf-44f3-b4a5-0adf01d2082d)
service apache2 restart

lynx www.vitamin.brokoli.f04.com/img

```

<br>

## Soal 15

> Karena terdapat resep rahasia di file /secret/recipe_secret.txt pada subdomain www.vitamin.brokoli.yyy.com, konfigurasikan folder /secret agar tidak dapat diakses oleh pengguna (dengan menampilkan 403 Forbidden).

> _Because there is a secret recipe in the /secret/recipe_secret.txt file on the www.vitamin.brokoli.yyy.com subdomain, configure the /secret folder so that it cannot be accessed by users (by displaying 403 Forbidden)._

**Answer:**

- Screenshot

  `Put your screenshot in here`
  ![Screenshot 2024-10-02 234451](https://github.com/user-attachments/assets/36034dd9-6ade-4b76-948a-eb07a4d52d33)


- Explanation

  `Put your explanation in here`
```
  cd /etc/apache2/sites-available

nano vitamin.brokoli.f04.com.

Tambahkan:

 <Directory /var/www/vitamin.brokoli.f04/secret>
     Options -Indexes
 </Directory>
![Screenshot 2024-10-02 235007](https://github.com/user-attachments/assets/d21c068a-1fdd-4654-b378-cd0b5b2b0d27)
lynx www.vitamin.brokoli.f04.com/secret

```

<br>

## Soal 16

> Karena dinilai terlalu panjang coba ubah konfigurasi www.vitamin.brokoli.yyy.com/public/js menjadi www.vitamin.brokoli.yyy.com/js

> _Since it is considered too long, change the configuration from www.vitamin.brokoli.yyy.com/public/js to www.vitamin.brokoli.yyy.com/js._

**Answer:**

- Screenshot

  `Put your screenshot in here`
  ![Screenshot 2024-10-02 235427](https://github.com/user-attachments/assets/b01287e6-074d-41c9-bf4b-2b033fde7cbd)


- Explanation
```
cd /etc/apache2/sites-available
nano vitamin.brokoli.f04.com.

Tambahkan:

 <Directory /var/www/vitamin.brokoli.f04/public/js>
     Options +Indexes
 </Directory>

 Alias "/js" "/var/www/vitamin.brokoli.f04/public/js"
![Screenshot 2024-10-02 235348](https://github.com/user-attachments/assets/a7c049fd-3e93-4642-ab81-631df213bc6d)
lynx www.vitamin.brokoli.f04.com/js
```




Lakukan perintah sesuai syntax di bawah ini di file config vitamin
```
Alias "/js" "/var/www/vitamin.brokoli.f04/public/js"
```

Lakukan pengetesan pada node client apakah `vitamin.brokoli.f04.com/js` dapat diakses mengarah langsung ke `/public/js`

`Put your screenshot in here`

<br>

## Soal 17

> Supaya Web kita aman terkendali maka ubah konfigurasi www.k1.vitamin.brokoli.yyy.com menjadi hanya bisa di akses oleh port 9696 dan 8888

> _To keep our web secure, configure www.k1.vitamin.brokoli.yyy.com to only be accessible through ports 9696 and 8888._

**Answer:**

- Screenshot

  `Put your screenshot in here`
  ![Screenshot 2024-10-03 004948](https://github.com/user-attachments/assets/cfb93d7b-5a14-43f3-9130-b8cd10e6cb53)

- Explanation
```
cd /etc/apache2/sites-available
cp 000-default.conf k1.vitamin.brokoli.f04.com.conf

Ganti port dan DocumentRoot:

nano k1.vitamin.brokoli.f04.com.conf
![Screenshot 2024-10-03 003318](https://github.com/user-attachments/assets/c0acfbc4-f001-4aee-86a6-fa1e69fc4860)

cd /etc/apache2
nano ports.conf

Tambahkan:
Listen 9696
Listen 8888
![Screenshot 2024-10-03 003539](https://github.com/user-attachments/assets/2986de5e-c78d-4a07-a428-6e75392a4f71)

cd /
 
wget -O 'var/www/k1.vitamin.brokoli.f04.zip' 'https://docs.google.com/uc?export=download&id=1SRnelY4XrtmhJg_Ly1nUJo1Jf91SnmtB' 

unzip -o /var/www/k1.vitamin.brokoli.f04.zip -d /var/www/

mv /var/www/k1.vitamin.brokoli.yyy.com /var/www/k1.vitamin.brokoli.f04

cd /etc/apache2/sites-available/

a2ensite k1.vitamin.brokoli.f04.conf

service apache2 restart

lynx  k1.vitamin.brokoli.f04.com:8080
atau
lynx  k1.vitamin.brokoli.f04.com:9696

![Screenshot 2024-10-03 004948](https://github.com/user-attachments/assets/cfb93d7b-5a14-43f3-9130-b8cd10e6cb53)

Konfigurasi telah berjalan dengan baik, hanya saja ketika kita melakukan lynx k1.vitamin.brokoli.f04.com tanpa port tertentu (default 80), maka akan tetap menampilkan page default dari apache. Untuk membatasinya, maka kita dapat melakukan konfigurasi:


cd /etc/apache2/sites-available/
nano 000-default.conf

Comment bagian ServerAdmin dan DocumentRoot, lalu tambahkan ServerName dan Redirect 403 / agar ketika k1.vitamin.brokoli.f04.com diakses dengan port bawaan, maka akan menghasilkan forbidden

![Screenshot 2024-10-03 005044](https://github.com/user-attachments/assets/6b106562-589d-47da-a0a5-4ffd0bcce90a)
lynx k1.vitamin.brokoli.f04.com
![Screenshot 2024-10-03 005322](https://github.com/user-attachments/assets/c26d4877-7e9f-4d2b-8361-61154fd3eebc)

```



Buat domain `k1.vitamin.brokoli.f04.com` lalu atur port untuk listen ke port 9696 dan 8888 di file config sesuai syntax di bawah ini
```
mkdir /var/www/k1.vitamin.brokoli.f04

touch /etc/apache2/sites-available/k1.vitamin.brokoli.f04.com.conf

echo '<VirtualHost *:9696 *:8888>
        ServerAdmin webmaster@localhost
        DocumentRoot /var/www/k1.vitamin.brokoli.f04
        ServerName k1.vitamin.brokoli.f04.com
        ServerAlias www.k1.vitamin.brokoli.f04.com

        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>' > /etc/apache2/sites-available/k1.vitamin.brokoli.f04.com.conf
```

Setting konfigurasi port milik apache di `/etc/apache2/ports.conf` untuk listen ke port 9696 dan 8888 sesuai syntax di bawah ini
```
echo '# If you just change the port or add more ports here, you will likely also
# have to change the VirtualHost statement in
# /etc/apache2/sites-enabled/000-default.conf

Listen 80
Listen 9696
Listen 8888

<IfModule ssl_module>
        Listen 443
</IfModule>

<IfModule mod_gnutls.c>
        Listen 443
</IfModule>

# vim: syntax=apache ts=4 sw=4 sts=4 sr noet' > /etc/apache2/ports.conf
```

Download resource untuk k1.vitamin.brokoli sesuai syntax yang sama seperti sebelumnya. Kemudian enable site dan restart service apache seeprti di bawah ini
```
wget

rm -rf /var/www/k1.vitamin.brokoli.f04/k1_vitamin_brokoli.zip

a2ensite k1.vitamin.brokoli.f04.com.conf
service apache2 restart
```

Lakukan pengetesan pada node client apakah bisa diakses atau tidak untuk domain `k1.vitamin.brokoli.f04.com`

`Put your screenshot in here`

<br>

## Soal 18

> Lanjutkan dari nomor sebelumnya buatlah autentikasi dengan username “Seblak” dan password “sehatyyy” dengan yyy adalah kode kelompok. Letakkan Document Root pada /var/www/k1.vitamin.brokoli.yyy.

> _Continuing from the previous point, create authentication with the username “Seblak” and the password “sehatyyy” where yyy is the group code. Set the Document Root to /var/www/k1.vitamin.brokoli.yyy._

**Answer:**

- Screenshot

  `Put your screenshot in here`
  
Jika auth benar:
![Screenshot 2024-10-03 004948](https://github.com/user-attachments/assets/c9ead97b-4f1a-4e8c-aedf-cdce53c8486f)
Jika auth salah:
![Screenshot 2024-10-03 010906](https://github.com/user-attachments/assets/c41bbf67-bafa-46f9-b2f5-dd93d9e9bd50)

- Explanation

```
cd /etc/apache2/sites-available
nano k1.vitamin.brokoli.f04.com.conf

Tambahkan:

<Directory /var/www/k1.vitamin.brokoli.f04>
		AuthType Basic
		AuthName "Restricted Content"
		AuthUserFile /etc/apache2/.htpasswd
		Require valid-user 
</Directory>

![Screenshot 2024-10-03 010317](https://github.com/user-attachments/assets/b6776fd7-3b62-44d3-ba1a-6241a5fc6064)

Save lalu exit.

Kemudian, ketikkan:
htpasswd -c -b /etc/apache2/.htpasswd Seblak sehatf04

service apache2 restart

lynx k1.vitamin.brokoli.f04.com:8888
![Screenshot 2024-10-03 010537](https://github.com/user-attachments/assets/168e8e82-3efc-4a77-bb88-a687761490c3)

Jika auth benar:
![Screenshot 2024-10-03 004948](https://github.com/user-attachments/assets/c9ead97b-4f1a-4e8c-aedf-cdce53c8486f)
Jika auth salah:
![Screenshot 2024-10-03 010906](https://github.com/user-attachments/assets/c41bbf67-bafa-46f9-b2f5-dd93d9e9bd50)


```


Tambahkan command sesuai syntax di bawah ini untuk memberikan authentifikasi pada saat mengakses k1.brokoli.f04.com di file confif k1.vitamin.brokoli.f04
```
<Directory /var/www/k1.vitamin.brokoli.f04>
		AuthType Basic
		AuthName "Restricted Content"
		AuthUserFile /etc/apache2/.htpasswd
		Require valid-user 
</Directory>
```

Tambahkan line sesuai syntax di bawah ini untuk membuat sebuah username dan password yang harus dimasukkan saat akan mengakses k1.vitamin
```
htpasswd -c -b /etc/apache2/.htpasswd Seblak sehatf04
```

Perintah untuk menjawab soal 17 dan 18
```
mkdir /var/www/k1.vitamin.brokoli.f04

touch /etc/apache2/sites-available/k1.vitamin.brokoli.f04.com.conf

echo '<VirtualHost *:9696 *:8888>
	ServerAdmin webmaster@localhost
	DocumentRoot /var/www/k1.vitamin.brokoli.f04
	ServerName k1.vitamin.brokoli.f04.com
	ServerAlias www.k1.vitamin.brokoli.f04.com

	<Directory /var/www/k1.vitamin.brokoli.f04>
		AuthType Basic
		AuthName "Restricted Content"
		AuthUserFile /etc/apache2/.htpasswd
		Require valid-user 
	</Directory>

	ErrorLog ${APACHE_LOG_DIR}/error.log
	CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>' > /etc/apache2/sites-available/k1.vitamin.brokoli.f04.com.conf

htpasswd -c -b /etc/apache2/.htpasswd Seblak sehatf04

a2enmod rewrite k1.vitamin.brokoli.f04.com.conf
a2ensite k1.vitamin.brokoli.f04.com.conf
service apache2 restart

echo '# If you just change the port or add more ports here, you will likely also
# have to change the VirtualHost statement in
# /etc/apache2/sites-enabled/000-default.conf

Listen 80
Listen 9696
Listen 8888

<IfModule ssl_module>
	Listen 443
</IfModule>

<IfModule mod_gnutls.c>
	Listen 443
</IfModule>

# vim: syntax=apache ts=4 sw=4 sts=4 sr noet' > /etc/apache2/ports.conf

wget

unzip -j /var/www/k1.vitamin.brokoli.f04/k1_vitamin_brokoli.zip -d /var/www/k1.vitamin.brokoli.f04

rm -rf /var/www/k1.vitamin.brokoli.f04/k1_vitamin_brokoli.zip
```

Lakukan pengetesan pada node client apakah authentifikasi yang kita terapkan sudah masuk atau belum

`Put your screenshot in here`

<br>

## Soal 19

> Konfigurasikan agar setiap kali IP Brokoli diakses dengan lynx, secara otomatis akan dialihkan ke www.brokoli.yyy.com (alias).

> _Configure it so that every time Brokoli's IP is accessed using lynx, it is automatically redirected to www.brokoli.yyy.com (alias)._

**Answer:**

- Screenshot

  `Put your screenshot in here`

- Explanation
```
service apache2 stop
service nginx restart

Testing (Tomat):
lynx 192.235.2.3
```

Pada Brokoli Web Server ketikkan sesuai syntax di bawah ini 
```
echo '<VirtualHost *:80>
	ServerAdmin webmaster@localhost
	DocumentRoot /var/www/html

	ErrorLog ${APACHE_LOG_DIR}/error.log
	CustomLog ${APACHE_LOG_DIR}/access.log combined

	Redirect / http://www.brokoli.f04.com/
</VirtualHost>' > /etc/apache2/sites-available/000-default.conf

service apache2 restart
```

Lakukan pengetesan pada node client apakah akan ke redirect apabila kita mengaksess IP Brokoli 

 `Put your screenshot in here`

<br>

## Soal 20

> Karena jumlah pengunjung website www.vitamin.brokoli.yyy.com semakin meningkat dan terdapat banyak gambar random, ubah permintaan gambar yang mengandung substring "vitamin" agar diarahkan ke file vitamin.png.

> _Since the number of visitors to www.vitamin.brokoli.yyy.com is increasing and there are many random images, redirect image requests that contain the substring "vitamin" to the file vitamin.png._

**Answer:**

- Screenshot

  `Put your screenshot in here`

- Explanation
```
service nginx stop

a2enmod rewrite
service apache2 restart

cd /etc/apache2/sites-available
nano vitamin.brokoli.f04.com.conf

Tambahkan:
RewriteEngine On
RewriteCond %{REQUEST_URI} .*vitamin.*\.(jpg|jpeg|png|gif)$ [NC]
RewriteRule .* /public/images/vitamin.png [L]

service apache2 restart

Testing (Tomat):
apt-get install caca-utils

(image to text library)

lynx www.vitamin.brokoli.f04.com/img/sayur-vitamin-k.jpg
lynx www.vitamin.brokoli.f04.com/img/vitamin.png

Bandingkan bahwa gambarnya sudah sama

```


Rewrite modul dari vitamin untuk me-redirect user ke brokoli.png apabila user request gambar dengan kata brokoli menggunakan modul rewrite di file config vitamin sesuai syntax di bawah ini
```
<Directory /var/www/vitamin.brokoli.f04>
		Options +FollowSymLinks -Multiviews
		AllowOverride All
</Directory>

RewriteEngine On
RewriteCond %{REQUEST_URI} brokoli
RewriteCond %{REQUEST_URI} !^/public/images/brokoli\.png
RewriteRule ^(.+)\.(png|jpg|jpeg|webp|gif)$ /brokoli.png [L,R=301]
```

Tambahkan command sesuai syntax di bawah ini untuk dapat mengaplikasikan hasil reqrite modul yang telah kita tambahkan
```
a2enmod rewrite vitamin.brokoli.f04.com.conf
```

Lakukan pengetesan pada node client apakah modul rewrite kita sudah berjalan atau belum

`Put your screenshot in here`

<br>
  
## Problems

## Revisions (if any)
