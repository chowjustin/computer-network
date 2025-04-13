[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/1zoHyFGp)
| Name           | NRP        | Kelas     |
| ---            | ---        | ----------|
| Agnes Priscilla S.H | 5025221295 | Jaringan Komputer F |
| Justin Chow | 5025231087 | Jaringan Komputer F |

## Put your topology config image here!

![Screenshot 2024-10-22 223732](https://github.com/user-attachments/assets/f9584bbd-8939-42eb-a881-a7ba3cb010ff)

<br>

> Template testing report: https://docs.google.com/document/d/17T0fsnh_4zZTrG-lELDJ88intrc9mkwCzZ_s-23JLCc/edit?usp=sharing

## Put your testing report here! 
> The report is sent in PDF format, uploaded to Drive, and set to public view.

`put the link here`

## Soal 0

> Pada perlombaan akhir tahun kali ini, semua worker dan client ikut serta di dalamnya sebagai perwakilan dari masing-masing asrama. Persiapan yang dilakukan untuk perlombaan ini adalah dengan setup semua network configuration yang sesuai dengan tabel peran diatas. Khusus untuk client menggunakan konfigurasi dari DHCP Server.

> _For the end-of-year competition, all the workers and clients participate, representing their respective houses. The preparation includes setting up the network configuration as per the table above, with clients using DHCP Server configuration_

**Answer**

- Dumbledore:

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

  auto eth4
  iface eth4 inet static
	      address 192.235.4.1
	      netmask 255.255.255.0

  auto eth5
  iface eth4 inet static
	      address 192.235.5.1
	      netmask 255.255.255.0

  auto eth6
  iface eth4 inet static
	      address 192.235.6.1
	  netmask 255.255.255.0

  up iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE -s 192.235.0.0/16
  ```

- SeverusSnape:

  ```
  auto eth0
  iface eth0 inet static
	      address 192.235.3.2
	      netmask 255.255.255.0
	      gateway 192.235.3.1
  ```

- McGonagall:

  ```
  auto eth0
  iface eth0 inet static
	      address 192.235.3.3
	      netmask 255.255.255.0
	      gateway 192.235.3.1
  ```

- Hagrid:

  ```
  auto eth0
  iface eth0 inet static
	      address 192.235.4.2
	      netmask 255.255.255.0
	      gateway 192.235.4.1
  ```

- Voldemort:

  ```
  auto eth0
  iface eth0 inet static
	      address 192.235.4.3
	      netmask 255.255.255.0
	      gateway 192.235.4.1
  ```

- Dementor:

  ```
  auto eth0
  iface eth0 inet static
	      address 192.235.4.4
	      netmask 255.255.255.0
	      gateway 192.235.4.1
  ```

- HarryPotter:

  ```
  auto eth0
  iface eth0 inet static
	      address 192.235.1.2
	      netmask 255.255.255.0
	      gateway 192.235.1.1
  ```

- RonWeasley:

  ```
  auto eth0
  iface eth0 inet static
	      address 192.235.1.3
	      netmask 255.255.255.0
	      gateway 192.235.1.1
  ```

- HermioneGranger:

  ```
  auto eth0
  iface eth0 inet static
	      address 192.235.1.4
	      netmask 255.255.255.0
	      gateway 192.235.1.1
  ```

- LunaLovegood:

  ```
  auto eth0
  iface eth0 inet static
	      address 192.235.6.4
	      netmask 255.255.255.0
	      gateway 192.235.6.1
  ```

- FiliusFlitwick:

  ```
  auto eth0
  iface eth0 inet static
	      address 192.235.6.3
	      netmask 255.255.255.0
	      gateway 192.235.6.1
  ```

- ChoChang:

  ```
  auto eth0
  iface eth0 inet static
	      address 192.235.6.2
	      netmask 255.255.255.0
	      gateway 192.235.6.1
  ```

- DracoMalfoy:

  ```
  auto eth0
  iface eth0 inet dhcp
  ```

- AstoriaGreengrass:

  ```
  auto eth0
  iface eth0 inet dhcp
  ```

- SusanBones:

  ```
  auto eth0
  iface eth0 inet dhcp
  ```

- HannahAbbott:

  ```
  auto eth0
  iface eth0 inet dhcp
  ```

## Soal 1

> Melakukan registrasi subdomain untuk PHP worker bernama gryffindor.hogwarts.yyy.com yang mengarah ke alamat IP load balancer Voldemort dan untuk laravel worker bernama ravenclaw.hogwarts.yyy.com yang mengarah ke alamat IP load balancer Dementor. Seluruh domain ini berkumpul dalam suatu ruang atau folder bernama hogwarts

> _Registering subdomains for the PHP workers named gryffindor.hogwarts.yyy.com, pointing to the IP Voldemort load balancer, and for the Laravel workers named ravenclaw.hogwarts.yyy.com, pointing to the IP Dementor load balancer. All domains are gathered in a folder named "hogwarts."_

**Answer:**

- Screenshot

Test `gryffindor.hogwarts.f04.com`

![image](https://github.com/user-attachments/assets/95e4ce7d-d7ba-420b-a775-67b70dff48eb)

Test `ravenclaw.hogwarts.f04.com`

![image](https://github.com/user-attachments/assets/57a6fb61-03ea-41a1-8e3f-35927bc636ca)

- Configuration

Buat direktori `hogwarts` dalam `/etc/bind` untuk menempatkan file konfigurasi subdomain

```
mkdir -p /etc/bind/hogwarts
```

Buat dua file DNS baru yaitu `gryffindor.hogwarts.f04.com` dan `ravenclaw.hogwarts.f04.com` sebagai tempat konfigurasi subdomain

```
cp /etc/bind/db.local /etc/bind/hogwarts/gryffindor.hogwarts.f04.com
cp /etc/bind/db.local /etc/bind/hogwarts/ravenclaw.hogwarts.f04.com
```

Tambahkan zone untuk subdomain `ravenclaw.hogwarts.f04.com` dan `gryffindor.hogwarts.f04.com` ke dalam file `named.conf.local` 

```
echo '
zone "ravenclaw.hogwarts.f04.com" {
    type master;
    file "/etc/bind/hogwarts/ravenclaw.hogwarts.f04.com";
};

zone "gryffindor.hogwarts.f04.com" {
    type master;
    file "/etc/bind/hogwarts/gryffindor.hogwarts.f04.com";
};
' > /etc/bind/named.conf.local
```

Buat data zone untuk `gryffindor.hogwarts.f04.com` dengan mengatur `IP Voldemort 192.235.4.3`

```
echo ';
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     gryffindor.hogwarts.f04.com. root.gryffindor.hogwarts.f04.com. (
                        2024102111    ; Serial
                        604800        ; Refresh
                        86400         ; Retry
                        2419200       ; Expire
                        604800 )      ; Negative Cache TTL
;
@               IN      NS      gryffindor.hogwarts.f04.com.
@               IN      A       192.235.4.3 ; IP Voldemort' > /etc/bind/hogwarts/gryffindor.hogwarts.f04.com
```

Buat data zone untuk `ravenclaw.hogwarts.f04.com` dengan mengatur `IP Dementor 192.235.4.4`

```
echo ';
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     ravenclaw.hogwarts.f04.com. root.ravenclaw.hogwarts.f04.com. (
                        2024102111    ; Serial
                        604800        ; Refresh
                        86400         ; Retry
                        2419200       ; Expire
                        604800 )      ; Negative Cache TTL
;
@               IN      NS      ravenclaw.hogwarts.f04.com.
@               IN      A       192.235.4.4 ; IP Dementor' > /etc/bind/hogwarts/ravenclaw.hogwarts.f04.com
```

Konfigurasi `named.conf.options` mengatur opsi BIND untuk DNS dengan pengaturan seperti forwarders, allow-query, dan pengaturan lainnya untuk memastikan akses DNS berjalan lancar

```
echo 'options {
        directory "/var/cache/bind";

        forwarders {
                192.168.122.1;
        };

        // dnssec-validation auto;
        allow-query{any;};
        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; };
}; ' >/etc/bind/named.conf.options

service named restart
```

- Explanation

<br>

## Soal 2

> Memberikan ketentuan khusus untuk DracoMalfoy dan AstoriaGreengrass yang mendapat range IP dari [Prefix IP].2.64 - [Prefix IP].2.65 dan [Prefix IP].2.100 - [Prefix IP].2.101

> Selain itu, untuk HannahAbbott dan SusanBones mendapat range IP dari [Prefix IP].5.50 - [Prefix IP].5.51 dan [Prefix IP].5.155 - [Prefix IP].5.156.


> _Special provisions are given to DracoMalfoy and AstoriaGreengrass, who are assigned the IP range from [Prefix IP].2.64 - [Prefix IP].2.65 and [Prefix IP].2.100 - [Prefix IP].2.101._

> _Additionally, HannahAbbott and SusanBones are assigned the IP range from [Prefix IP].5.50 - [Prefix IP].5.51 and [Prefix IP].5.155 - [Prefix IP].5.156._

**Answer:**

- Screenshot

Cek ip a `DracoMalfoy`

![image](https://github.com/user-attachments/assets/2dbcaa71-ea64-4498-846f-a99b6846ef9b)

Cek ip a `AstoriaGreengrass`

![image](https://github.com/user-attachments/assets/ac0ffc12-1419-4d21-9044-c4c3bece2a78)

Test `SusanBones`

![image](https://github.com/user-attachments/assets/8ddc74a6-420c-42ca-a313-82ecaffcf3c6)

Test `HannahAbbott`

![image](https://github.com/user-attachments/assets/4900c3de-c301-4c4c-aaa0-ce83ca39c13f)

- Configuration  

Di SeverusSnape masuk ke konfigurasi di `.bashrc`

```
echo 'nameserver 192.168.122.1' > /etc/resolv.conf
```

Lalu install DHCP Server

```
apt-get update
apt-get install isc-dhcp-server -y
```

Konfigurasi Interface DHCP Server

```
echo 'INTERFACESv4="eth0"' > /etc/default/isc-dhcp-server
```

File Konfigurasi DHCP `dhcpd.conf`

```
echo '
subnet 192.235.1.0 netmask 255.255.255.0 { }

subnet 192.235.2.0 netmask 255.255.255.0 {
    range 192.235.2.64 192.235.2.65;
    range 192.235.2.100 192.235.2.101;
    option routers 192.235.2.1;
    option broadcast-address 192.235.2.255;
    option domain-name-servers 192.235.3.3;
    default-lease-time 300;
    max-lease-time 6900;
}

subnet 192.235.3.0 netmask 255.255.255.0 { }

subnet 192.235.4.0 netmask 255.255.255.0 { }

subnet 192.235.5.0 netmask 255.255.255.0 {
    range 192.235.5.50 192.235.5.51;
    range 192.235.5.155 192.235.5.156;
    option routers 192.235.5.1;
    option broadcast-address 192.235.5.255;
    option domain-name-servers 192.235.3.3;
    default-lease-time 300;
    max-lease-time 6900;
}

subnet 192.235.6.0 netmask 255.255.255.0 { }
' > /etc/dhcp/dhcpd.conf

service isc-dhcp-server restart
```

Di Dumbledore Instalasi DHCP Relay

```
apt-get update
apt-get install isc-dhcp-relay -y
service isc-dhcp-relay start
```

Konfigurasi DHCP Relay dalam File `02.sh`

```
echo 'SERVERS="192.235.3.2"
INTERFACES="eth1 eth2 eth3 eth4 eth5 eth6"
OPTIONS=' > /etc/default/isc-dhcp-relay
```

Konfigurasi IP Forwarding

```
echo 'net.ipv4.ip_forward=1' > /etc/sysctl.conf
service isc-dhcp-relay restart
```

- Explanation

<br>

## Soal 3

> Khusus untuk HermioneGranger yang berada di switch 1 mendapat range IP dari
[Prefix IP].1.10 - [Prefix IP].1.15 dan [Prefix IP].1.20 - [Prefix IP].1.25

> Khusus untuk ChoChang yang berada di switch 6 mendapat range IP dari 
[Prefix IP].6.10 - [Prefix IP].6.15 dan [Prefix IP].6.20 - [Prefix IP].6.25


> _HermioneGranger, who is on switch 1, is assigned the IP range from [Prefix IP].1.10 - [Prefix IP].1.15 and [Prefix IP].1.20 - [Prefix IP].1.25._

> _ChoChang, who is on switch 6, is assigned the IP range from [Prefix IP].6.10 - [Prefix IP].6.15 and [Prefix IP].6.20 - [Prefix IP].6.25._

**Answer:**

- Screenshot

Test `HermioneGranger`

![image](https://github.com/user-attachments/assets/f13b361c-9021-4d4a-8c33-d3cbcb07b430)

Test `ChoChang`

![image](https://github.com/user-attachments/assets/bcad911c-6750-427e-8998-b9138f47a467)

- Configuration

Di SeverusSnape atur interface untuk DHCP server

```
echo 'INTERFACESv4="eth0"' > /etc/default/isc-dhcp-server
```

Atur file `/etc/dhcp/dhcpd.conf`

```
echo '
subnet 192.235.1.0 netmask 255.255.255.0 {
    range 192.235.1.10 192.235.1.15;
    range 192.235.1.20 192.235.1.25;
    option routers 192.235.1.1;
    option broadcast-address 192.235.1.255;
    option domain-name-servers 192.235.3.3;
    default-lease-time 300;
    max-lease-time 6900;
}

subnet 192.235.2.0 netmask 255.255.255.0 {
    range 192.235.2.64 192.235.2.65;
    range 192.235.2.100 192.235.2.101;
    option routers 192.235.2.1;
    option broadcast-address 192.235.2.255;
    option domain-name-servers 192.235.3.3;
    default-lease-time 300;
    max-lease-time 6900;
}

subnet 192.235.3.0 netmask 255.255.255.0 {
}

subnet 192.235.4.0 netmask 255.255.255.0 {
}

subnet 192.235.5.0 netmask 255.255.255.0 {
    range 192.235.5.50 192.235.5.51;
    range 192.235.5.155 192.235.5.156;
    option routers 192.235.5.1;
    option broadcast-address 192.235.5.255;
    option domain-name-servers 192.235.3.3;
    default-lease-time 300;
    max-lease-time 6900;
}

subnet 192.235.6.0 netmask 255.255.255.0 {
    range 192.235.6.10 192.235.6.15;
    range 192.235.6.20 192.235.6.25;
    option routers 192.235.6.1;
    option broadcast-address 192.235.6.255;
    option domain-name-servers 192.235.3.3;
    default-lease-time 300;
    max-lease-time 6900;
}
' >  /etc/dhcp/dhcpd.conf

service isc-dhcp-server restart
```

Ubah konfigurasi pada network di Hermione dan ChoChang

```
nano /etc/network/interfaces
```

Ubah menjadi 

```
auto eth0
iface eth0 inet dhcp
```

- Explanation

<br>

## Soal 4

> Menetapkan batasan waktu untuk DHCP server dalam peminjaman alamat IP untuk client melalui switch 2 selama 5 menit sedangkan client yang melalui switch 5 selama 20 menit. Untuk switch 1 dan switch 6 memiliki batas waktu 10 menit. Alokasi waktu maksimal peminjaman alamat IP selama 100 menit. 

> _The DHCP server's lease time for IP addresses is set as follows: Clients connected through switch 2 have a lease time of 5 minutes, Clients connected through switch 5 have a lease time of 20 minutes, Switches 1 and 6 have a lease time of 10 minutes, The maximum lease time for IP addresses is set at 100 minutes._

**Answer:**

- Screenshot

Test `SusanBones`

![image](https://github.com/user-attachments/assets/2e7b99cf-75c7-4e19-a497-e122566e40db)

Test `DracoMalfoy`

![image](https://github.com/user-attachments/assets/97b12e6c-016a-4035-8d9e-249b94657d84)

- Configuration 

Di SeverusSnape konfigurasi tiap subnet 

```
echo '
subnet 192.235.1.0 netmask 255.255.255.0 {
    range 192.235.1.10 192.235.1.15;
    range 192.235.1.20 192.235.1.25;
    option routers 192.235.1.1;
    option broadcast-address 192.235.1.255;
    option domain-name-servers 192.235.3.3;
    default-lease-time 600;
    max-lease-time 6000; 
}

subnet 192.235.2.0 netmask 255.255.255.0 {
    range 192.235.2.64 192.235.2.65;
    range 192.235.2.100 192.235.2.101;
    option routers 192.235.2.1;
    option broadcast-address 192.235.2.255;
    option domain-name-servers 192.235.3.3;
    default-lease-time 300; 
    max-lease-time 6000;
}

subnet 192.235.3.0 netmask 255.255.255.0 {
}

subnet 192.235.4.0 netmask 255.255.255.0 {
}

subnet 192.235.5.0 netmask 255.255.255.0 {
    range 192.235.5.50 192.235.5.51;
    range 192.235.5.155 192.235.5.156;
    option routers 192.235.5.1;
    option broadcast-address 192.235.5.255;
    option domain-name-servers 192.235.3.3;
    default-lease-time 1200; 
    max-lease-time 6000; 
}

subnet 192.235.6.0 netmask 255.255.255.0 {
    range 192.235.6.10 192.235.6.15;
    range 192.235.6.20 192.235.6.25;
    option routers 192.235.6.1;
    option broadcast-address 192.235.6.255;
    option domain-name-servers 192.235.3.3;
    default-lease-time 600;
    max-lease-time 6000;
}
' >  /etc/dhcp/dhcpd.conf

service isc-dhcp-server restart
```

- Explanation

<br>

## Soal 5

> Memastikan bahwa semua CLIENT, HermioneGranger, dan ChoChang harus menggunakan konfigurasi dari DHCP server, menerima DNS dari Professor McGonagall dan dapat akses internet. Khusus untuk HermioneGranger dan ChoChang mendapatkan IP Statis dari DHCP dengan [Prefix IP].x.14. hint: fixed address


> _Ensure that all CLIENT, HermioneGranger, and ChoChang use DHCP server configurations, receive DNS from Professor McGonagall, and can access the internet. HermioneGranger and ChoChang must receive static IPs from DHCP with the address [Prefix IP].x.14 (hint: fixed address)._

**Answer:**

- Screenshot

Cek hwaddress dengan ip a `HermioneGranger`

![image](https://github.com/user-attachments/assets/8ce8a491-a7e3-48a4-9d73-67f6543ee798)

Cek hwaddress dengan ip a `ChoChang`

![image](https://github.com/user-attachments/assets/9d638055-25ce-470a-8551-d4d97e83a018)

Akses internet di `DracoMalfoy`

![image](https://github.com/user-attachments/assets/c862b66e-c600-48e9-aec2-940d4e374735)

- Configuration

Di SeverusSnape setting DHCP Server

```
echo '
subnet 192.235.1.0 netmask 255.255.255.0 {
    range 192.235.1.10 192.235.1.15;
    range 192.235.1.20 192.235.1.25;
    option routers 192.235.1.1;
    option broadcast-address 192.235.1.255;
    option domain-name-servers 192.235.3.3;
    default-lease-time 600;
    max-lease-time 6000; 
}
host HermioneGranger{
    hardware ethernet 7a:42:d0:bc:9b:10;
    fixed-address 192.235.1.14;
}
subnet 192.235.2.0 netmask 255.255.255.0 {
    range 192.235.2.64 192.235.2.65;
    range 192.235.2.100 192.235.2.101;
    option routers 192.235.2.1;
    option broadcast-address 192.235.2.255;
    option domain-name-servers 192.235.3.3;
    default-lease-time 300; 
    max-lease-time 6000;
}
subnet 192.235.3.0 netmask 255.255.255.0 {
}
subnet 192.235.4.0 netmask 255.255.255.0 {
}
subnet 192.235.5.0 netmask 255.255.255.0 {
    range 192.235.5.50 192.235.5.51;
    range 192.235.5.155 192.235.5.156;
    option routers 192.235.5.1;
    option broadcast-address 192.235.5.255;
    option domain-name-servers 192.235.3.3;
    default-lease-time 1200; 
    max-lease-time 6000; 
}
subnet 192.235.6.0 netmask 255.255.255.0 {
    range 192.235.6.10 192.235.6.15;
    range 192.235.6.20 192.235.6.25;
    option routers 192.235.6.1;
    option broadcast-address 192.235.6.255;
    option domain-name-servers 192.235.3.3;
    default-lease-time 600;
    max-lease-time 6000;
}
host ChoChang{
    hardware ethernet ba:1b:0f:e8:b3:dc;
    fixed-address 192.235.6.14;
}
' >  /etc/dhcp/dhcpd.conf

service isc-dhcp-server restart
```

Edit configuration di bawah DHCP pada HermioneGranger 

```
nano /etc/network/interfaces
hwaddress ether 7a:42:d0:bc:9b:10
```

Edit configuration di bawah DHCP pada ChoChang

```
nano /etc/network/interfaces
hwaddress ether ba:1b:0f:e8:b3:dc
```

- Explanation

1. Memastikan Konfigurasi DHCP dan IP Statis

2. Cek MAC Address dengan `ip a`

3. Akses Internet di Client

<br>

## Soal 6

> Dimulai dari asrama Gryffindor yang menjadi PHP worker, mereka harus melakukan deployment untuk website berikut menggunakan PHP 7.4.

> _The Gryffindor house, represented by the PHP workers, must deploy the following website using PHP 7.4._

**Answer:**

- Screenshot

Test `HarryPotter`

![image](https://github.com/user-attachments/assets/634813be-2635-4a06-a7b5-3b8e89b85c26)

Test `RonWeasley`

![image](https://github.com/user-attachments/assets/c2dd4eed-4d6e-4f1c-9338-f095c4893c0f)

Test `HermioneGranger`

![image](https://github.com/user-attachments/assets/33cf8ef0-c110-4ae8-9082-d21ff2035497)

- Configuration

Tentukan nameserver, install repository, PHP 7.4, dan Nginx di `HarryPotter, RonWeasley, HermioneGranger`

```
echo 'nameserver 192.168.122.1' > /etc/resolv.conf
apt-get update
apt-get install software-properties-common
add-apt-repository ppa:ondrej/php
apt-get update
apt-get install php7.4-mbstring php7.4-xml php7.4-cli php7.4-common php7.4-intl php7.4-opcache php7.4-readline php7.4-mysql php7.4-fpm php7.4-curl unzip wget -y
apt-get install nginx -y
```

Buat direktori dan unduh file website

```
mkdir -p /var/www/gryffindor
wget -O '/var/www/gryffindor/gryffindor.zip' 'https://drive.google.com/uc?export=download&id=17R4Zcxm3emHq21WdMJzSfCxO8FHqvATM'
apt-get install unzip
unzip -o /var/www/gryffindor/gryffindor.zip -d /var/www/gryffindor
rm /var/www/gryffindor/gryffindor.zip
```

Konfigurasi Nginx di Harry Potter

```
echo 'server {

    listen 8001;

    root /var/www/gryffindor/;

    index index.php;
    server_name 192.235.1.3;

    location / {
            try_files $uri $uri/ /index.php?$query_string;
    }

    # pass PHP scripts to FastCGI server
    location ~ \.php$ {
    include snippets/fastcgi-php.conf;
    fastcgi_pass unix:/var/run/php/php7.4-fpm.sock;
    }

location ~ /\.ht {
            deny all;
    }

    error_log /var/log/nginx/harrypotter_error.log;
    access_log /var/log/nginx/harrypotter_access.log;
}' > /etc/nginx/sites-available/gryffindor.f04.com

ln -s /etc/nginx/sites-available/gryffindor.f04.com /etc/nginx/sites-enabled/

service php7.4-fpm start
service nginx restart
```

Konfigurasi Nginx di RonWeasley

```
echo 'server {

    listen 8002;

    root /var/www/gryffindor/;

    index index.php;
    server_name 192.235.1.3;

    location / {
            try_files $uri $uri/ /index.php?$query_string;
    }

    # pass PHP scripts to FastCGI server
    location ~ \.php$ {
    include snippets/fastcgi-php.conf;
    fastcgi_pass unix:/var/run/php/php7.4-fpm.sock;
    }

location ~ /\.ht {
            deny all;
    }

    error_log /var/log/nginx/ronweasly_error.log;
    access_log /var/log/nginx/ronweasly_access.log;
}' > /etc/nginx/sites-available/gryffindor.f04.com

ln -s /etc/nginx/sites-available/gryffindor.f04.com /etc/nginx/sites-enabled/

service php7.4-fpm start
service nginx restart
```

Konfigurasi Nginx di HermioneGranger

```
echo 'server {

    listen 8003;

    root /var/www/gryffindor/;

    index index.php;
    server_name 192.235.1.14;

    location / {
            try_files $uri $uri/ /index.php?$query_string;
    }

    # pass PHP scripts to FastCGI server
    location ~ \.php$ {
    include snippets/fastcgi-php.conf;
    fastcgi_pass unix:/var/run/php/php7.4-fpm.sock;
    }

location ~ /\.ht {
            deny all;
    }

    error_log /var/log/nginx/granger_error.log;
    access_log /var/log/nginx/granger_access.log;
}' > /etc/nginx/sites-available/gryffindor.f04.com


ln -s /etc/nginx/sites-available/gryffindor.f04.com /etc/nginx/sites-enabled/

service php7.4-fpm start
service nginx restart
```

- Explanation

1. Atur nameserver agar sistem dapat mengakses jaringan internet dengan alamat nameserver

2. Perbarui daftar paket agar dapat mengakses versi terbaru dari paket-paket di dalam repositori 

3. Download file aplikasi yang akan dideploy di lokasi yang ditentukan

4. Buat Konfigurasi untuk Nginx pada masing-masing Node 

<br>

## Soal 7

> Khusus perlombaan ini, Voldemort sudah jinak dan dia menjadi load balancer untuk para penghuni asrama Gryffindor yang menjadi worker PHP. Aturlah agar Voldemort dapat membagi pekerjaan kepada worker PHP secara optimal. Sebagai pengetesan awal, terapkan algoritma round robin dan lakukan test index.php menggunakan apache benchmark dengan 1000 request dan 100 request/second. Lakukan test sebanyak 3 kali lalu hitung rata-rata dan standar deviasi dari time/request

> _Voldemort, who is now reformed, becomes the load balancer for the Gryffindor PHP workers. Optimize Voldemort to distribute tasks to the PHP workers. For the initial test, apply the round-robin algorithm and test it to the index.php page using Apache Benchmark with 1,000 requests and 100 requests/second. Do the test 3 times and calculate the mean and standard deviation of time/request._

**Answer:**

- Screenshot

![image](https://github.com/user-attachments/assets/27b301b4-2e8c-43ed-a813-ec66a297c31e)

![image](https://github.com/user-attachments/assets/9e7e2441-c805-4bbb-b21d-5beeb194d643)

![image](https://github.com/user-attachments/assets/c37254e4-240f-4fba-a3c4-2f9b0728d278)

![image](https://github.com/user-attachments/assets/6d97fe1e-2046-483a-85c5-c7bd080a93b0)

- Configuration

Di Voldemort atur DNS dan Nginx

```
echo 'nameserver 192.168.122.1' > /etc/resolv.conf
apt-get install nginx -y
apt-get install apache2-utils
```

Konfigurasi Nginx untuk load balancing

```
cp /etc/nginx/sites-available/default.conf /etc/nginx/sites-available/gryffindor.f04.com
echo ‘
upstream gryffindor{
        server 192.235.1.2:8001;
        server 192.235.1.3:8002;
        server 192.235.1.14:8003;
}

server {
        listen 80;
        server_name gryffindor.hogwarts.f04.com;

        location / {
                proxy_pass http://hogwarts.f04.com;
        }
}
‘ > /etc/nginx/sites-available/gryffindor.f04.com
```

Aktifkan Konfigurasi Load Balancing Gryffindor

```
ln -s /etc/nginx/sites-available/gryffindor.f04.com /etc/nginx/sites-enabled/
```

Gnati DNS Resolusi

```
echo 'nameserver 192.235.3.2' > /etc/resolv.conf
```

Install alat di Client untuk Benchmark

```
apt-get update && apt-get install apache2-utils
apt-get install apache2-utils
apt install less -y
apt-get install htop -y
```

Lakukan benchmark dan tampilkan hasilnya

```
mkdir /root/benchmark
cd /root/benchmark
ab -n 1000 -c 100 -g output.data https://gryffindor.hogwarts.f04.com/
cat out.data
less out.data
```

- Explanation

<br>

## Soal 8

> Dalam penilaian akhir tahun ini, dibutuhkan algoritma terbaik, cobalah tes 3 algoritma load balancer dengan menggunakan jmeter. Jmeter perlu melakukan login, akses home, dan terakhir logout. Lakukan test dengan 300 thread dan 3 sec ramp up period. Lakukan test sebanyak 3 kali per algoritma, lalu hitung rata-rata dan standar deviasi dari response time. (username: wingardium, password: leviosa)


> _For the final assessment, try three different load-balancing algorithms using JMeter with 300 threads and a 3-second ramp-up period. Jmeter have to be able to login, access homepage, and logout. Do the test 3 times for each algorithm, then calculate the mean and standard deviation of response time. (username: wingardium, password: leviosa)_

**Answer:**

- Screenshot

  `Put your screenshot in here`

- Configuration

Buka JMeter

```
https://github.com/arsitektur-jaringan-komputer/Modul-Jarkom/tree/master/Modul-3/Jmeter
```

Di DracoMalfoy setting awal di terminal 

```
cd /root/jmeter/bin
nano 08.jmx
```

Isi 08.jmx dengan script XML

```
<?xml version="1.0" encoding="UTF-8"?>
<jmeterTestPlan version="1.2" properties="5.0" jmeter="5.6.3">
  <hashTree>
    <TestPlan guiclass="TestPlanGui" testclass="TestPlan" testname="Test Plan">
      <elementProp name="TestPlan.user_defined_variables" elementType="Arguments" guiclass="ArgumentsPanel" testclass="Arguments" testname="User Defined Variables">
        <collectionProp name="Arguments.arguments"/>
      </elementProp>
    </TestPlan>
    <hashTree>
      <ThreadGroup guiclass="ThreadGroupGui" testclass="ThreadGroup" testname="Thread Group">
        <intProp name="ThreadGroup.num_threads">300</intProp>
        <intProp name="ThreadGroup.ramp_time">3</intProp>
        <boolProp name="ThreadGroup.same_user_on_next_iteration">true</boolProp>
        <stringProp name="ThreadGroup.on_sample_error">continue</stringProp>
        <elementProp name="ThreadGroup.main_controller" elementType="LoopController" guiclass="LoopControlPanel" testclass="LoopController" testname="Loop Controller">
          <stringProp name="LoopController.loops">3</stringProp>
          <boolProp name="LoopController.continue_forever">false</boolProp>
        </elementProp>
      </ThreadGroup>
      <hashTree>
        <HTTPSamplerProxy guiclass="HttpTestSampleGui" testclass="HTTPSamplerProxy" testname="HTTP Request">
          <stringProp name="HTTPSampler.domain">gryffindor.hogwarts.f04.com</stringProp>
          <stringProp name="HTTPSampler.protocol">http</stringProp>
          <stringProp name="HTTPSampler.path">/php/login.php</stringProp>
          <boolProp name="HTTPSampler.follow_redirects">true</boolProp>
          <stringProp name="HTTPSampler.method">POST</stringProp>
          <boolProp name="HTTPSampler.use_keepalive">true</boolProp>
          <boolProp name="HTTPSampler.postBodyRaw">true</boolProp>
          <elementProp name="HTTPsampler.Arguments" elementType="Arguments">
            <collectionProp name="Arguments.arguments">
              <elementProp name="" elementType="HTTPArgument">
                <boolProp name="HTTPArgument.always_encode">false</boolProp>
                <stringProp name="Argument.value">
                  {"username": "wingardium", "password": "leviosa"}
                </stringProp> 
                <stringProp name="Argument.metadata">=</stringProp>
                <boolProp name="HTTPArgument.use_equals">true</boolProp>
              </elementProp>
            </collectionProp>
          </elementProp>
        </HTTPSamplerProxy>
        <hashTree/>
        <ResultCollector guiclass="ViewResultsFullVisualizer" testclass="ResultCollector" testname="View Results Tree">
          <boolProp name="ResultCollector.error_logging">false</boolProp>
          <objProp>
            <name>saveConfig</name>
            <value class="SampleSaveConfiguration">
              <time>true</time>
              <latency>true</latency>
              <timestamp>true</timestamp>
              <success>true</success>
              <label>true</label>
              <code>true</code>
              <message>true</message>
              <threadName>true</threadName>
              <dataType>true</dataType>
              <encoding>false</encoding>
              <assertions>true</assertions>
              <subresults>true</subresults>
              <responseData>false</responseData>
              <samplerData>false</samplerData>
              <xml>false</xml>
              <fieldNames>true</fieldNames>
              <responseHeaders>false</responseHeaders>
              <requestHeaders>false</requestHeaders>
              <responseDataOnError>false</responseDataOnError>
              <saveAssertionResultsFailureMessage>true</saveAssertionResultsFailureMessage>
              <assertionsResultsToSave>0</assertionsResultsToSave>
              <bytes>true</bytes>
              <sentBytes>true</sentBytes>
              <url>true</url>
              <threadCounts>true</threadCounts>
              <idleTime>true</idleTime>
              <connectTime>true</connectTime>
            </value>
          </objProp>
          <stringProp name="filename"></stringProp>
        </ResultCollector>
        <hashTree/>
      </hashTree>
    </hashTree>
  </hashTree>
</jmeterTestPlan>
```

Jalankan JMeter

```
./jmeter -n -t 08.jmx -l 08-result.csv -e -o ../../jmeter-output
```

Akses Output 

```
cd ../../jmeter-output
```

- Explanation

1. Coba tiga algoritma load balancer yang berbeda untuk menentukan algoritma terbaik berdasarkan response time

2. Setiap algoritma diuji tiga kali, dengan JMeter melakukan login, akses halaman home, dan logout

3. Untuk setiap uji coba, catat response time rata-rata dan standar deviasi dari seluruh permintaan 

4. Atur JMeter, 300 thread (simulasi pengguna) dengan periode ramp-up 3 detik untuk menghindari beban mendadak pada server

5. Tambahkan elemen `ResultCollector` untuk menyimpan hasil pengujian

6. Simpan hasil uji dalam bentuk file CSV (08-result.csv) dan output HTML pada direktori jmeter-output untuk analisis lebih lanjut

<br>

## Soal 9

> Tidak semua IP dapat akses asrama Gryffindor melalui IP Load balancer Voldemort. Untuk itu, berikan akses pada load balancer Voldemort. Autentikasi akan memerlukan username: “jarkom” dan password: “modul3”. Simpan file autentikasi pada  /etc/nginx/secretchamber 

> _Not all IPs can access Gryffindor's house through Voldemort’s load balancer. Grant access to the Voldemort load balancer. Authentication will require username: “jarkom” and password: “modul3”. Save the authentication file in /etc/nginx/secretchamber._

**Answer:**

- Screenshot

Test `DracoMalfoy`

![image](https://github.com/user-attachments/assets/ab89c991-120a-4fe6-93df-d3c51bf8b6ac)

![image](https://github.com/user-attachments/assets/c0d4da18-1c40-4268-9fc5-ec0e6247b0d7)

![image](https://github.com/user-attachments/assets/c2d6b9ed-c08d-4157-9e9e-e1cbcf0160e2)

![image](https://github.com/user-attachments/assets/a02e66fb-3157-4064-bb4b-13eebf15182f)

- Configuration 

Di Voldemort konfigurasi upstream untuk load balancing

```
echo 'upstream gryffindor{
        server 192.235.1.1:8001;
        server 192.235.1.2:8002;
        server 192.235.1.14:8003;
}
```

Konfigurasi server untuk Nginx:

```
server {
        listen 80;
        server_name gryffindor.hogwarts.f04.com 192.235.4.3;

        location / {
                proxy_pass http://gryffindor;
                auth_basic "Restricted Access";
                auth_basic_user_file /etc/nginx/secretchamber;
        }
}
' > /etc/nginx/sites-available/gryffindor.f04.com
```

Buat symbolic link untuk mengaktifkan konfigurasi

```
ln -s /etc/nginx/sites-available/gryffindor.f04.com /etc/nginx/sites-enabled/

service nginx restart
```

Di terminal Voldemort tambahkan file autentikasi dengan username dan password

```
htpasswd -c -b /etc/nginx/secretchamber jarkom modul3
service nginx restart
```

- Explanation

<br>

## Soal 10

> Setelah menambahkan autentikasi ke Gryffindor, coba testing ulang dengan menggunakan JMeter (algoritma round robin) serta skenario, thread, dan ramp up period yang sama seperti no 8 (300 thread, 3 sec ramp up period, login-home-logout). Kali ini, coba juga jumlah worker yang berbeda: 3 worker, 2 worker, dan 1 worker. 

> _After adding authentication to Gryffindor, retest using JMeter (round-robin algorithm) with the same scenario, thread, and ramp up period as number 8 (300 thread, 3 sec ramp up period, login-home-logout). This time, test with different numbers of workers: 3 workers, 2 workers, and 1 worker._

**Answer:**

- Screenshot

  `Put your screenshot in here`

- Configuration

Set Konfigurasi Awal JMeter dan Worker

1. Di DracoMalfoy `cd /root/jmeter/bin`

2. Isi nano 10.jmx dengan `(sama seperti no 8)`

3. Lalu `./jmeter -n -t 10.jmx -l 10-3worker.csv -e -o ../../jmeter-3worker`

Konfigurasi Worker Kedua

1. Matikan salah satu worker

2. Di Voldemort 

```
nano /etc/nginx/sites-available/gryffindor.f04.com
ln -s /etc/nginx/sites-available/gryffindor.f04.com /etc/nginx/sites-enabled/
service nginx restart
```

![image](https://github.com/user-attachments/assets/d2e86fa4-463a-40f9-9f37-0b8b7c944e43)

Kembali ke client DracoMalfoy `./jmeter -n -t 10.jmx -l 10-2worker.csv -e -o ../../jmeter-2worker`

Konfigurasi Worker Ketiga

1. Matikan salah satu worker lagi

2. Di Voldemort 

```
nano /etc/nginx/sites-available/gryffindor.f04.com
ln -s /etc/nginx/sites-available/gryffindor.f04.com /etc/nginx/sites-enabled/
service nginx restart
```

Kembali ke client DracoMalfoy `./jmeter -n -t 10.jmx -l 10-1worker.csv -e -o ../../jmeter-1worker`

Ambil data hasil pengujian di `/root/JMeter`, dan `cat statistics.json`

- Explanation

<br>

## Soal 11

> Hogwarts juga bekerjasama dengan ITS dalam perlombaan ini. Untuk itu, setiap request pada Voldemort yang mengandung /informatika pada akhir url akan di proxy passing menuju halaman https://www.its.ac.id/informatika/id/beranda/ 

> _Hogwarts has also partnered with ITS for this competition. Any request to Voldemort containing /informatika at the end of the URL should be proxied to the page at https://www.its.ac.id/informatika/id/beranda/._


**Answer:**

- Screenshot

Test DracoMalfoy

![image](https://github.com/user-attachments/assets/8ec985e6-5106-470f-adb1-62590c8ff654)

- Configuration

Di Voldemort buat file konfigurasi dengan upstream dan pengaturan server 

```
echo 'upstream gryffindor{
        server 192.235.1.1:8001;
        server 192.235.1.2:8002;
        server 192.235.1.14:8003;
}

server {
        listen 80;
        server_name gryffindor.hogwarts.f04.com 192.235.4.3;

location /informatika {
proxy_pass https://www.its.ac.id/informatika/id/beranda/;
}

        location / {
                proxy_pass http://gryffindor;
        	    auth_basic "Restricted Access";
        	    auth_basic_user_file /etc/nginx/secretchamber;
        }
}' > /etc/nginx/sites-available/gryffindor.f04.com

ln -s /etc/nginx/sites-available/gryffindor.f04.com /etc/nginx/sites-enabled/

service nginx restart
```

- Explanation

1. Buat load balancer dengan beberapa server backend

2. Tetapkan alamat server untuk menerima permintaan HTTP

3. Tetapkan otentikasi dasar dengan pesan "Restricted Access" dan file pengguna yang berisi kredensial

<br>

## Soal 12

> Selain butuh autentikasi dalam pengaksesan asrama Gryffindor melalui LB Voldemort, juga perlu dibatasi dengan pembatasan IP.  LB Voldemort hanya boleh diakses oleh client dengan IP [Prefix IP].2.64, [Prefix IP].2.100, [Prefix IP].5.50, dan [Prefix IP].5.155. hint: (fixed in dulu clientnya) 


> _In addition to requiring authentication for access to Gryffindor through Voldemort’s load balancer, IP restrictions also need to be enforced. Voldemort's load balancer can only be accessed by clients with IPs: [Prefix IP].2.64, [Prefix IP].2.100, [Prefix IP].5.50, and [Prefix IP].5.155. (hint: fixed client IPs first)._

**Answer:**

- Screenshot

  `Put your screenshot in here`

- Configuration

 Di Voldemort buat Nginx configuration
 
 ```
 echo 'upstream gryffindor{
        server 192.235.1.1:8001;
        server 192.235.1.2:8002;
        server 192.235.1.14:8003;
}

server {
        listen 80;
        server_name gryffindor.hogwarts.f04.com 192.235.4.3;

allow 192.235.2.64;  
allow 192.235.2.100;  
allow 192.235.5.50; 
allow 192.235.5.155;   
deny all;  

location /informatika {
proxy_pass https://www.its.ac.id/informatika/id/beranda/;
}

        location / {
                proxy_pass http://gryffindor;
                auth_basic "Restricted Access";
                auth_basic_user_file /etc/nginx/secretchamber;
        }
}' > /etc/nginx/sites-available/gryffindor.f04.com

ln -s /etc/nginx/sites-available/gryffindor.f04.com /etc/nginx/sites-enabled/

service nginx restart
```

Di SeverusSnape buat DHCP configuration

```
echo '
subnet 192.235.1.0 netmask 255.255.255.0 {
    range 192.235.1.10 192.235.1.15;
    range 192.235.1.20 192.235.1.25;
    option routers 192.235.1.1;
    option broadcast-address 192.235.1.255;
    option domain-name-servers 192.235.3.3;
    default-lease-time 600;
    max-lease-time 6000; 
}
host HermioneGranger{
    hardware ethernet 7a:42:d0:bc:9b:10;
    fixed-address 192.235.1.14;
}
subnet 192.235.2.0 netmask 255.255.255.0 {
    range 192.235.2.64 192.235.2.65;
    range 192.235.2.100 192.235.2.101;
    option routers 192.235.2.1;
    option broadcast-address 192.235.2.255;
    option domain-name-servers 192.235.3.3;
    default-lease-time 300; 
    max-lease-time 6000;
}
host DracoMalfoy{
    hardware ethernet 9a:d2:82:12:bd:e0;
    fixed-address 192.235.2.64;
}
host AstoriaGreengrass{
    hardware ethernet f2:d6:b1:d8:07:54;
    fixed-address 192.235.2.100;
}
subnet 192.235.3.0 netmask 255.255.255.0 {
}
subnet 192.235.4.0 netmask 255.255.255.0 {
}
subnet 192.235.5.0 netmask 255.255.255.0 {
    range 192.235.5.50 192.235.5.51;
    range 192.235.5.155 192.235.5.156;
    option routers 192.235.5.1;
    option broadcast-address 192.235.5.255;
    option domain-name-servers 192.235.3.3;
    default-lease-time 1200; 
    max-lease-time 6000; 
}
host SusanBones{
    hardware ethernet 3e:58:4f:b7:cc:f8;
    fixed-address 192.235.5.50;
}
host HannahAbbott{
    hardware ethernet c6:cc:93:a0:b2:0e;
    fixed-address 192.235.5.155;
}
subnet 192.235.6.0 netmask 255.255.255.0 {
    range 192.235.6.10 192.235.6.15;
    range 192.235.6.20 192.235.6.25;
    option routers 192.235.6.1;
    option broadcast-address 192.235.6.255;
    option domain-name-servers 192.235.3.3;
    default-lease-time 600;
    max-lease-time 6000;
}
host ChoChang{
    hardware ethernet ba:1b:0f:e8:b3:dc;
    fixed-address 192.235.6.14;
}
' >  /etc/dhcp/dhcpd.conf

service isc-dhcp-server restart
```

Test `lynx gryffindor.hogwarts.f04.com`

- Explanation

Kebutuhan autentikasi dan pembatasan akses

<br>

## Soal 13

> Pengaturan database yang dibutuhkan dalam perlombaan ini wajib diatur di Hagrid. Pastikan pengaturan database tersebut dapat diakses oleh Lunalovegood, FiliusFlitwick, dan ChoChang dengan menggunakan username: kelompokyyy dan password: passwordyyy 

> _Database setup for this competition is managed by Hagrid. Ensure that this database can be accessed by LunaLovegood, FiliusFlitwick, and ChoChang using the username: "kelompokyyy" and password: "passwordyyy”_

**Answer:**

- Screenshot

  `Put your screenshot in here`

- Configuration

 Di Hagrid atur nameserver

 ```
 echo 'nameserver 192.168.122.1' > /etc/resolv.conf
 ```

 Update paket dan instalasi MariaDB Server dan MariaDB Client

 ```
 apt-get update
 apt-get install mariadb-server -y
 ```

 Mulai service MariaDB dan masuk ke konsol MariaDB

 ```
 service mysql start
 mysql
 ```

 Buat user database dan database yang dibutuhkan serta memberikan izin

 ```
 CREATE USER 'kelompokf04'@'%' IDENTIFIED BY 'passwordf04';
 CREATE USER 'kelompokf04'@'localhost' IDENTIFIED BY 'passwordf04';
 CREATE DATABASE dbkelompokf04;
 GRANT ALL PRIVILEGES ON *.* TO 'kelompokf04'@'%';
 GRANT ALL PRIVILEGES ON *.* TO 'kelompokf04'@'localhost';
 FLUSH PRIVILEGES;
 ```

 Konfigurasi pada file `my.cnf`

 ```
 nano /etc/mysql/my.cnf
 ```

 Tambahkan 
 
 ```
 [mysqld]
 skip-networking=0
 skip-bind-address
 service mysql restart
 ```

 Di Lunalovegood, FiliusFitwick dan Chochang pindah ke worker  

 ```
 echo ‘nameserver 192.168.122.1’ > /etc/resolv.conf
 apt-get update
 apt-get install mariadb-client -y
 ```

 Hubungkan ke database dari server worker (Lunalovegood, FiliusFlitwick, dan ChoChang)

 ```
 mariadb --host=192.235.4.2 --port=3306 --user=kelompokf04 --password
 ```

 Masukkan password `passwordf04`

 Masukkan command `SHOW DATABASES;`

 ![image](https://github.com/user-attachments/assets/13acedb8-0440-41e7-860c-564d2f634a80)

 Di Hagrid

 ```
 mysql

 CREATE USER 'kelompokf04'@'%' IDENTIFIED BY 'passwordf04';
 CREATE USER 'kelompokf04'@'localhost' IDENTIFIED BY 'passwordf04';
 CREATE DATABASE dbkelompokf04;
 GRANT ALL PRIVILEGES ON *.* TO 'kelompokf04'@'%';
 GRANT ALL PRIVILEGES ON *.* TO 'kelompokf04'@'localhost';
 FLUSH PRIVILEGES;

 ctrl+c

 service mysql restart
 ```

- Explanation

<br>

## Soal 14

> Selain itu, untuk Lunalovegood, FiliusFlitwick, dan ChoChang memiliki website sesuai dengan https://github.com/lodaogos/laravel-jarkom-modul-3/tree/main  berikut. Jangan lupa melakukan instalasi PHP8.0 dan Composer! Pastikan database di Hagrid sudah ada isinya sekarang dan server Laravel sudah running di localhost!

> _Additionally, LunaLovegood, FiliusFlitwick, and ChoChang have websites following this GitHub link: Laravel Jarkom Modul 3. Install PHP 8.0 and Composer! Make sure Hagrid's data storage is populated, and the Laravel servers are running on localhost!_

**Answer:**

- Screenshot

Test `AstoriaGreengrass`

![image](https://github.com/user-attachments/assets/17cc7d31-3a71-4399-8447-6917488f8081)

- Configuration

Di Lunalovegood, FiliusFlitwick, dan ChoChang `.bashrc`

Instal software pendukung

```
apt-get install software-properties-common
add-apt-repository ppa:ondrej/php
apt-get install php8.0-mbstring php8.0-xml php8.0-cli php8.0-common php8.0-intl php8.0-opcache php8.0-readline php8.0-mysql php8.0-fpm php8.0-curl unzip wget -y
apt-get install nginx -y
```

Instal Composer

```
wget https://getcomposer.org/download/2.0.13/composer.phar
chmod +x composer.phar
mv composer.phar /usr/bin/composer
apt-get install git -y
```

Kloning Repository dan Instalasi Dependensi

```
git clone https://github.com/lodaogos/laravel-jarkom-modul-3.git
cd laravel-jarkom-modul-3
composer update
composer install
```

Konfigurasi `.env` Laravel

```
echo ‘
APP_NAME=Laravel
APP_ENV=local
APP_KEY=
APP_DEBUG=true
APP_URL=http://localhost

LOG_CHANNEL=stack
LOG_DEPRECATIONS_CHANNEL=null
LOG_LEVEL=debug

DB_CONNECTION=mysql
DB_HOST=192.235.4.2
DB_PORT=3306
DB_DATABASE=dbkelompokf04
DB_USERNAME=kelompokf04
DB_PASSWORD=passwordf04

BROADCAST_DRIVER=log
CACHE_DRIVER=file
FILESYSTEM_DISK=local
QUEUE_CONNECTION=sync
SESSION_DRIVER=file
SESSION_LIFETIME=120

MEMCACHED_HOST=127.0.0.1

REDIS_HOST=127.0.0.1
REDIS_PASSWORD=null
REDIS_PORT=6379

MAIL_MAILER=smtp
MAIL_HOST=mailpit
MAIL_PORT=1025
MAIL_USERNAME=null
MAIL_PASSWORD=null
MAIL_ENCRYPTION=null
MAIL_FROM_ADDRESS="hello@example.com"
MAIL_FROM_NAME="${APP_NAME}"

AWS_ACCESS_KEY_ID=
AWS_SECRET_ACCESS_KEY=
AWS_DEFAULT_REGION=us-east-1
AWS_BUCKET=
AWS_USE_PATH_STYLE_ENDPOINT=false

PUSHER_APP_ID=
PUSHER_APP_KEY=
PUSHER_APP_SECRET=
PUSHER_HOST=
PUSHER_PORT=443
PUSHER_SCHEME=https
PUSHER_APP_CLUSTER=mt1

VITE_PUSHER_APP_KEY="${PUSHER_APP_KEY}"
VITE_PUSHER_HOST="${PUSHER_HOST}"
VITE_PUSHER_PORT="${PUSHER_PORT}"
VITE_PUSHER_SCHEME="${PUSHER_SCHEME}"
VITE_PUSHER_APP_CLUSTER="${PUSHER_APP_CLUSTER}"
‘ > .env

php artisan migrate:fresh
php artisan db:seed --class=MusicsTableSeeder

php artisan key:generate
php artisan jwt:secret
```

Nginx Virtual Host Configuration

```
echo’
server {

    listen 8001;

    root /laravel-jarkom-modul-3/public;

    index index.php index.html index.htm;
    server_name localhost;

    location / {
            try_files $uri $uri/ /index.php?$query_string;
    }

    # pass PHP scripts to FastCGI server
    location ~ \.php$ {
    include snippets/fastcgi-php.conf;
    fastcgi_pass unix:/var/run/php/php8.0-fpm.sock;
    }

location ~ /\.ht {
            deny all;
    }

    error_log /var/log/nginx/laravel_error.log;
    access_log /var/log/nginx/laravel_access.log;
}
‘ > /etc/nginx/sites-available/laravel
```

Symlink Nginx Virtual Host Configuration dan Permission untuk Laravel

```
ln -s /etc/nginx/sites-available/laravel /etc/nginx/sites-enabled/
chown -R www-data.www-data /laravel-jarkom-modul-3/storage
```

Service Management

```
service php8.0-fpm start
service nginx restart
```

Laravel Migration, Seeding, dan Generating Key

```
php artisan migrate:fresh
php artisan db:seed --class=MusicsTableSeeder
php artisan key:generate
php artisan jwt:secret
```

Di Client 

```
lynx 192.235.6.14:8001
lynx 192.235.6.3:8002
lynx 192.235.6.4:8003
```

- Explanation

<br>

## Soal 15

> Lakukan testing endpoint /register sebanyak 100 request dengan 10 request/second di salah satu worker menggunakan apache benchmark dari SusanBones! Kenapa failed 99x? Jelaskan! 

> _Test the /register endpoint with 100 requests and 10 requests per second on one of the workers using Apache Benchmark from SusanBones! Why did 99 tests fail? Explain!_

**Answer:**

- Screenshot

Test DracoMalfoy

![image](https://github.com/user-attachments/assets/6ee5770f-0a7b-40f3-8105-fa9ceb8ab506)

![image](https://github.com/user-attachments/assets/ca22acd7-a5f5-4689-b09c-2a0ca3afd78f)

- Configuration

Instal dan persiapan alat untuk melakukan benchmark 

```
apt-get update
apt-get install apache2-utils
apt install less -y
apt-get install htop -y
```

Buat direktori dan menavigasi ke direktori Benchmark

```
mkdir /root/benchmark
cd /root/benchmark
```

Buat file creds.json dengan konten JSON untuk payload request

```
echo '{
    "username": "nama",
    "password": "password"
}' > /root/benchmark/creds.json
```

Navigasi ke direktori Benchmark

```
cd /root/benchmark
```

Benchmarking pada endpoint/register menggunakan `ab` 

```
ab -n 100 -c 10 -g register.data -p creds.json -T application/json 
http://192.235.6.14:8001/api/auth/register
```

- Explanation

<br>

## Soal 16

> Lakukan juga testing pada endpoint /login sebanyak 100 request dengan 10 request/second di salah satu worker menggunakan apache benchmark dari SusanBones! Dapatkan token melalui responsenya juga!

> _Test the /login endpoint with 100 requests and 10 requests per second on one of the workers using Apache Benchmark from SusanBones! Collect the token from the response!_

**Answer:**

- Screenshot

  `Put your screenshot in here`

- Configuration

Arahkan terminal ke direktori `/root/benchmark`, tempat file benchmark dan output akan disimpan

Jalankan Apache Benchmark untuk menguji endpoint `/login`

```
ab -n 100 -c 10 -g login.data -p creds.json -T application/json http://192.235.6.14:8001/api/auth/login
```

Navigasi ke direktori Benchmark

```
cd /root/benchmark
cat login.data
less login.data
```

- Explanation

1. Pindahkan direktori lagi untuk melihat hasil benchmarking jika diperlukan `cd /root/benchmark/`

2. Tampilkan isi file login.data secara keseluruhan di terminal `cat login.data`

3. Tampilkan isi file `login.data` dalam mode interaktif, memungkinkan navigasi file dengan lebih mudah `less login.data`

<br>

## Soal 17

> Coba testing pada endpont /me sebanyak 100 request dengan 10 request/second di salah satu worker menggunakan apache benchmark dari SusanBones! Periksa responsenya apakah sudah sesuai dengan yang diloginkan? 

> _Test the /me endpoint with 100 requests and 10 requests per second on one of the workers using Apache Benchmark from SusanBones! Check if the response matches the logged-in user!_

**Answer:**

- Screenshot

  `Put your screenshot in here`

- Configuration

```
curl -X POST -H "Content-Type: application/json" -d @/root/benchmark/creds.json http://192.235.6.14:8001/api/auth/login >  /root/benchmark/token.json

token=$(jq -r '.token' /root/benchmark/token.json)

ab -n 100 -c 10 -H "Authorization: Bearer $token" http://192.235.6.14:8001/api/me
```

- Explanation

<br>

## Soal 18

> Mendekati tugas akhir perlombaan ini, mari seimbangkan kekuatan LunaLovegood, FiliusFlitwick, dan ChoChang untuk bekerja sama secara adil! Buatkan load balancer Laravel dengan Dementor dan implementasikan Proxy Bind untuk mengaitkan IP dari ketiga worker tersebut!

> _As the competition nears its end, balance the workload of LunaLovegood, FiliusFlitwick, and ChoChang! Create a Laravel load balancer using Dementor and implement Proxy Bind to link the IPs of the three workers!_

**Answer:**

- Screenshot

  `Put your screenshot in here`

- Configuration

  `Put your configuration in here`

- Explanation

<br>

## Soal 19

> Untuk menguatkan para Laravel Worker, coba implementasikan PHP-FPM pada LunaLovegood, FiliusFlitwick, dan ChoChang. Untuk testing kinerja naikkan: 
pm.max_children
pm.start_servers
pm.min_spare_servers
pm.max_spare_servers
sebanyak tiga percobaan dan lakukan analisis testing menggunakan apache benchmark sebanyak 100 request dengan 10 request/second atau menggunakan jmeter dengan 100 threads! (Pilih 1 metode testing)

> _To strengthen the Laravel workers, implement PHP-FPM on LunaLovegood, FiliusFlitwick, and ChoChang. For performance testing, adjust: pm.max_children, pm.start_servers, pm.min_spare_servers, pm.max_spare_servers. Run the tests three times and analyze the performance by using Apache Benchmark with 100 requests at a rate of 10 requests per second or using JMeter with 100 threads! (Choose 1 testing method)_

**Answer:**

- Screenshot

  `Put your screenshot in here`

- Configuration

  `Put your configuration in here`

- Explanation

<br>

## Soal 20

> Yey terakhir. Menurut Professor Dumbledore, sepertinya menggunakan PHP-FPM tidak cukup untuk meningkatkan performa worker-worker. Implementasikan Least-Conn pada Dementor. Lakukan analisis pada testing kinerja menggunakan apache benchmark sebanyak 100 request dengan 10 request/second atau menggunakan jmeter dengan 100 threads! (Pilih 1 metode testing)

> _Finally, Professor Dumbledore suggests that PHP-FPM might not be enough to improve the workers' performance. Implement the Least-Conn algorithm on Dementor. Analyze the performance by using Apache Benchmark with 100 requests at a rate of 10 requests per second or using JMeter with 100 threads! (Choose 1 testing method)_

**Answer:**

- Screenshot

  `Put your screenshot in here`

- Configuration

  `Put your configuration in here`

- Explanation

<br>
  
## Problems

## Revisions (if any)
