[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/s7OBVfDF)
| Name           | NRP        | Kelas     |
| ---            | ---        | ----------|
| xxxxxxx | xxxxxx | Jaringan Komputer (x) |
| Justin Chow | 5025231087 | Jaringan Komputer (F) |


## Put your topology config image here!

![image](https://github.com/user-attachments/assets/22d40bd4-3320-4670-9f23-4dc5e63f1d64)

## Put your VLSM calculation here!

![image](https://github.com/user-attachments/assets/94e17862-7767-4910-aa79-204fe902f142)

<b>Tree:</b>

![IP Tree Jarkom Modul 4 (1)](https://github.com/user-attachments/assets/7e31d064-5f56-46ef-9760-9765498000ed)

## Put your IP route here!

<b>SUBNETTING</b>

Heiji
```
auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
	address 192.235.0.9
	netmask 255.255.255.252

auto eth2
iface eth2 inet static
	address 192.235.0.13
	netmask 255.255.255.252
```

Agasa
```
auto eth0
iface eth0 inet static
	address 192.235.0.10
	netmask 255.255.255.252

auto eth1
iface eth1 inet static
	address 192.235.4.1
	netmask 255.255.252.0

auto eth2
iface eth2 inet static
	address 192.235.0.1
	netmask 255.255.255.252
```

Ran
```
auto eth0
iface eth0 inet static
	address 192.235.4.2
	netmask 255.255.252.0
	gateway 192.235.4.1
```

Kazuha
```
auto eth0
iface eth0 inet static
	address 192.235.0.2
	netmask 255.255.255.252

auto eth1
iface eth1 inet static
	address 192.235.0.5
	netmask 255.255.255.252

auto eth2
iface eth2 inet static
	address 192.235.8.1
	netmask 255.255.248.0
```

Sonoko
```
auto eth0
iface eth0 inet static
	address 192.235.0.6
	netmask 255.255.255.252
	gateway 192.235.0.5
```

Haibara
```
auto eth0
iface eth0 inet static
	address 192.235.8.2
	netmask 255.255.248.0
	gateway 192.235.8.1
```

Ayumi
```
auto eth0
iface eth0 inet static
	address 192.235.0.14
	netmask 255.255.255.252

auto eth1
iface eth1 inet static
	address 192.235.0.17
	netmask 255.255.255.252

auto eth2
iface eth2 inet static
	address 192.235.1.129
	netmask 255.255.255.128
```

Shinichi
```
auto eth0
iface eth0 inet static
	address 192.235.1.131
	netmask 255.255.255.128
	gateway 192.235.1.129
```

Conan
```
auto eth0
iface eth0 inet static
	address 192.235.1.130
	netmask 255.255.255.128
	gateway 192.235.1.129
```

Mitsuhiko
```
auto eth0
iface eth0 inet static
	address 192.235.0.18
	netmask 255.255.255.252

auto eth1
iface eth1 inet static
	address 192.235.0.21
	netmask 255.255.255.252

auto eth2
iface eth2 inet static
	address 192.235.2.1
	netmask 255.255.254.0
```

Megure
```
auto eth0
iface eth0 inet static
	address 192.235.0.22
	netmask 255.255.255.252
	gateway 192.235.0.21
```

Kogoro
```
auto eth0
iface eth0 inet static
	address 192.235.2.2
	netmask 255.255.254.0
	gateway 192.235.2.1
```

Genta
```
auto eth0
iface eth0 inet static
	address 192.235.2.128
	netmask 255.255.254.0
	gateway 192.235.2.1
```


<b>ROUTING</b>

Heiji
```
#Agasa
up route add -net 192.235.4.0 netmask 255.255.252.0 gw 192.235.0.10 #A1
up route add -net 192.235.0.0 netmask 255.255.255.252 gw 192.235.0.10 #A2
up route add -net 192.235.0.4 netmask 255.255.255.252 gw 192.235.0.10 #A3
up route add -net 192.235.8.0 netmask 255.255.248.0 gw 192.235.0.10 #A4

#Ayumi
up route add -net 192.235.1.128 netmask 255.255.255.128 gw 192.235.0.14 #A7
up route add -net 192.235.0.16 netmask 255.255.255.252 gw 192.235.0.14 #A8
up route add -net 192.235.0.20 netmask 255.255.255.252 gw 192.235.0.14 #A9
up route add -net 192.235.2.0 netmask 255.255.254.0 gw 192.235.0.14 #A10
```

Agasa
```
#Kazuha
up route add -net 192.235.0.4 netmask 255.255.255.252 gw 192.235.0.2 #A3
up route add -net 192.235.8.0 netmask 255.255.248.0 gw 192.235.0.2 #A4

#Heiji
up route add -net 0.0.0.0 netmask 0.0.0.0 gw 192.235.0.9 
```
Kazuha
```
#Agasa
up route add -net 0.0.0.0 netmask 0.0.0.0 gw 192.235.0.1 
```
Ayumi
```
#Mitsuhiko
up route add -net 192.235.0.20 netmask 255.255.255.252 gw 192.235.0.18 #A9
up route add -net 192.235.2.0 netmask 255.255.254.0 gw 192.235.0.18 #A10

#Heiji
up route add -net 0.0.0.0 netmask 0.0.0.0 gw 192.235.0.13 
```
Mitsuhiko
```
#Ayumi
up route add -net 0.0.0.0 netmask 0.0.0.0 gw 192.235.0.17 
```

## Soal 1

> Bagaimana cara mengkonfigurasi iptables pada router bernama 'Heiji' agar memungkinkan jaringan mengakses internet melalui interface eth0 menggunakan SNAT tanpa menggunakan MASQUERADE?

> _How to configure iptables on a router named ‘Heiji’ to allow the network to access the internet through interface eth0 using SNAT without using MASQUERADE?_

**Answer:**

- Screenshot

  Sebelum:
  <br>
  ![image](https://github.com/user-attachments/assets/6edb8fb5-6f5a-4764-8f8d-e433e93bb5ea)
  <br>
  Sesudah:
  <br>
  ![image](https://github.com/user-attachments/assets/f0bbd835-e412-49b2-9a66-72f3a5406c78)

- Configuration

    `iptables -t nat -A POSTROUTING -o eth0 -j SNAT --to-source $(hostname -I | tr ' ' '\n' | grep '^192\.168' | head -n 1)`

- Explanation

    Tujuan dari iptables berikut yaitu untuk mengganti IP dari source packet yang akan keluar melalui interface eth0 Heiji menuju keluar NAT. `hostname -I | tr ' ' '\n' | grep '^192\.168' | head -n 1` merupakan command yang digunakan untuk mendapatkan ip eth0 dari Heiji (IP yang terhubung ke internet).
    - `hostname -I` menampilkan semua alamat IP yang terasosiasi dengan hostname, yang dipisah oleh spasi.
    - `tr ' ' '\n'` mengubah setiap spasi menjadi baris baru .
    - `grep '^192\.168'` memfilter hanya baris yang diawali dengan 192.168 (ip eth0 yang terhubung ke internet).
    - `head -n 1` mengambil hanya baris pertama dari hasil filter.
    
    Output:
  <br>
    ![image](https://github.com/user-attachments/assets/786b7b1b-deaf-43a4-be72-dfbd14b8624f)

  

<br>

## Soal 2

> Kalian diminta untuk melakukan drop semua paket masuk TCP kecuali pada port 1744 pada node Shinichi.

> _You are asked to drop all incoming TCP packets except on port 1744 on Shinichi's node_

**Answer:**

- Screenshot

  ![image](https://github.com/user-attachments/assets/32edaae0-cadb-4b1b-9d8c-705d6174afab)
  - Pesan "Connection refused" berarti tidak ada layanan (service) yang mendengarkan (listening) di port tersebut.
  - Jika koneksi "stuck" di trying, itu menunjukkan bahwa paket menuju port tersebut di-drop atau diblokir oleh firewall tanpa memberi respons.


- Configuration

    ```
    iptables -A INPUT -p tcp --dport 1744 -j ACCEPT
    iptables -A INPUT -p tcp -j DROP
    /sbin/iptables-save
    ```

- Explanation
    
    - `-A INPUT` berguna untuk menambahkan aturan ke chain INPUT.
    - `-p tcp` menentukan protokol yang digunakan, dalam hal ini TCP.
    - `--dport 1744 j ACCEPT` berguna untuk menentukan port tujuan yang apabila paket memenuhi kriteria port, paket akan diterima.
    - `j DROP` berguna untuk menolak menolak (DROP) paket apabila tidak memenuhi kriteria.
    - `/sbin/iptables-save` untuk menyimpan konfigurasi iptables dan rule.


<br>

## Soal 3

> Lakukan pembatasan sehingga koneksi SSH pada semua Web Server hanya dapat dilakukan oleh user yang berada pada node Ran.

> _Make restrictions so that SSH connections to all Web Servers can only be made by users who are on the Ran node._

**Answer:**

- Screenshot

  Dari Ran:
  <br>
  ![image](https://github.com/user-attachments/assets/7e3de2d6-a536-49f9-8b5f-4bb5b4d0f9c1)
  <br>
  Dari Haibara:
  <br>
  ![image](https://github.com/user-attachments/assets/5548763d-674f-4e1b-892a-2941c9a59771)
  - Didapatkan response "Connection refused" dikarenakan belum terdapat service ssh yang di-enable.
  - Jika koneksi "stuck", itu menunjukkan bahwa paket menuju port tersebut di-drop atau diblokir oleh firewall tanpa memberi respons (DROP).
    
- Configuration
- 
  Di Semua WebServer (Conan, Megure, Sonoko):
  ```
  iptables -A INPUT -p tcp --dport 22 -m iprange --src-range 192.235.4.2-192.235.7.254 -j ACCEPT
  iptables -A INPUT -p tcp --dport 22 -j DROP
  /sbin/iptables-save
  ```
  
- Explanation

    - `-A INPUT` berguna untuk menambahkan aturan ke chain INPUT.
    - `-p tcp` menentukan protokol yang digunakan, dalam hal ini TCP.
    - `--dport 22 -m iprange --src-range 192.235.4.2-192.235.7.254 -j ACCEPT` berguna untuk menentukan port tujuan yang apabila paket memenuhi kriteria port, paket akan diterima, dalam hal ini adalah port 22 yang merupakan port default dari ssh.
    - `--src-range 192.235.4.2-192.235.7.254` adalah range alamat IP dari Ran yang akan kita izinkan paketnya untuk diterima.
    - `j DROP` berguna untuk menolak menolak (DROP) paket apabila tidak memenuhi kriteria.
    - `/sbin/iptables-save` untuk menyimpan konfigurasi iptables dan rule.


<br>

## Soal 4

> Semua subnet hanya dapat mengakses Web Server pada port 80 dan 443 (Conan, Sonoko, dan Megure) pada hari Senin-Jumat, pukul 07:00- 19:00.

> _All subnets can access the Web Server (Conan, Sonoko, and Megure) only on ports 80 and 443, from Monday to Friday, between 07:00-19:00._

**Answer:**

- Screenshot

  Di hari yang sesuai:
  <br>
  ![image](https://github.com/user-attachments/assets/bb52e97c-eaa3-46fd-a052-4a92e4d7d674)
  <br>
  Di hari yang tidak sesuai:
  <br>
  ![image](https://github.com/user-attachments/assets/28fe961b-2dc1-4bb4-9e6c-fe5d67975bc0)
  - Pesan "Connection refused" berarti tidak ada layanan (service) yang mendengarkan (listening) di port tersebut.
  - Jika koneksi "stuck", itu menunjukkan bahwa paket menuju port tersebut di-drop atau diblokir oleh firewall tanpa memberi respons.

- Configuration

  ```
  iptables -A INPUT -p tcp -m multiport --dports 80,443 -m time --timestart 07:00 --timestop 19:00 --weekdays Mon,Tue,Wed,Thu,Fri -j ACCEPT
  iptables -A INPUT -j DROP

  /sbin/iptables-save
  ```

- Explanation

    - `-A INPUT` berguna untuk menambahkan aturan ke chain INPUT.
    - `-p tcp` menentukan protokol yang digunakan, dalam hal ini TCP.
    - `-m multiport --dports 80,443` berguna untuk menentukan port tujuan yang akan diterima nantinya. `multiport` memungkinkan untuk langsung menambahkan beberapa rule dalam 1 line rule.
    - `time --timestart 07:00 --timestop 19:00 --weekdays Mon,Tue,Wed,Thu,Fri -j ACCEPT` untuk mengatur waktu dan hari yang menjadi kriteria paket untuk diterima (ditambah dengan aturan port yang sesuai dengan poin sebelumnya).
    - `j DROP` berguna untuk menolak menolak (DROP) paket apabila tidak memenuhi kriteria.
    - `/sbin/iptables-save` untuk menyimpan konfigurasi iptables dan rule.

<br>

## Soal 5

> Ternyata subnet Haibara memiliki akses tambahan, yaitu dapat mengakses Web Server pada port 80 dan 443 di luar hari Senin-Jumat (hari Sabtu dan Minggu), tanpa pembatasan waktu.

> _The Haibara subnet has additional access, allowing it to access the Web Server on ports 80 and 443 outside of Monday to Friday (on Saturday and Sunday), with no time restrictions._

**Answer:**

- Screenshot

  Di Weekdays dan Waktu yang Benar (Di Haibara):
  <br>
  ![image](https://github.com/user-attachments/assets/8b0487d2-d73e-4789-8660-06327e983a58)
  <br>
  Di Weekdays dan Waktu yang Salah (Di Haibara):
  <br>
  ![image](https://github.com/user-attachments/assets/0f9a403b-f3a4-40c0-aca2-e8624328a20a)
  <br>
  Di Weekend (Di Haibara):
  <br>
  ![image](https://github.com/user-attachments/assets/536877e9-307b-44dd-929e-df1acd2973b0)
  <br>

- Configuration
  
  ```
  iptables -I INPUT 3 -s 192.235.8.2/21 -p tcp -m multiport --dports 80,443 -m time --weekdays Sat,Sun -j ACCEPT
  /sbin/iptables-save
  ```

- Explanation

    - `-I INPUT 3` berguna untuk menambahkan aturan ke chain INPUT dengan urutan ke-3. Urutan ke-3 saya pilih karena terdapat 2 rule dari nomor 3 yang saya prioritaskan terlebih dahulu.
    - `-s 192.235.8.2/21` menentukan alamat IP dari Haibara yang akan di accept paketnya jika memenuhi kriteria.
    - `-m multiport --dports 80,443` berguna untuk menentukan port tujuan yang akan diterima nantinya. `multiport` memungkinkan untuk langsung menambahkan beberapa rule dalam 1 line rule.
    - `time --weekdays Sat,Sun -j ACCEPT` untuk mengatur hari yang menjadi kriteria paket untuk diterima, dalam hal ini Sabtu dan Minggu.
    - `/sbin/iptables-save` untuk menyimpan konfigurasi iptables dan rule.

<br>

## Soal 6

> Akses ke Web Server Conan, Sonoko, dan Megure pada port 80 dan 443 dilarang pada hari Jumat, pukul 11:00-13:00 (maklum, Jumatan rek).

> _Access to the Web Server (Conan, Sonoko, and Megure) on ports 80 and 443 is prohibited on Fridays between 11:00-13:00 (It's Friday prayer time)._

**Answer:**

- Screenshot

  Di waktu Jumatan, di Haibara:
  <br>
  ![image](https://github.com/user-attachments/assets/b7136014-2630-4be2-9f72-f80df8735d80)
  <br>
  Di waktu Jumatan, di Ran:
  <br>
  ![image](https://github.com/user-attachments/assets/9e75bf23-9e32-4b0d-9a0e-ff1cabab89a7)

- Configuration

  ```
  iptables -I INPUT 3 -p tcp -m multiport --dports 80,443 -m time --timestart 11:00 --timestop 13:00 --weekdays Fri -j REJECT
  /sbin/iptables-save
  ```

- Explanation

    - `-I INPUT 3` berguna untuk menambahkan aturan ke chain INPUT dengan urutan ke-3. Urutan ke-3 saya pilih karena terdapat 2 rule dari nomor 3 yang saya prioritaskan terlebih dahulu. Disini, rule dari nomor 5 akan turun ke nomor 4.
    - `-p tcp` menentukan protokol yang digunakan, dalam hal ini TCP.
    - `-m multiport --dports 80,443` berguna untuk menentukan port tujuan yang akan diterima nantinya. `multiport` memungkinkan untuk langsung menambahkan beberapa rule dalam 1 line rule.
    - `time --timestart 11:00 --timestop 13:00 --weekdays Fri -j DROP` untuk menolak paket pada hari Jumat, pukul 11:00-13:00.
    - `/sbin/iptables-save` untuk menyimpan konfigurasi iptables dan rule.


<br>

## Soal 7

> Tambahkan logging paket yang di-drop di setiap node server dan router.

> _Enable logging for dropped packets on every server node and router._

**Answer:**

- Screenshot

  ![image](https://github.com/user-attachments/assets/9662a3b2-f7f6-40ac-b071-2864cdfcc220)
  ![image](https://github.com/user-attachments/assets/d4ae85b0-5a81-40aa-9fff-f993fdd2fc22)

- Configuration

  Untuk WebServer:
  ```
  apt-get update
  apt-get install ulogd2 -y
  
  iptables -I INPUT 2 -p tcp -m tcp --dport 22 -j NFLOG --nflog-prefix "SSH-Drop: " --nflog-group 0
  iptables -I INPUT 4 -p tcp -m multiport --dports 80,443 -m time --timestart 11:00 --timestop 13:00 --weekdays Fri -j NFLOG --nflog-prefix "Jumatan-Drop: " --nflog-group 0
  iptables -I INPUT 8 -j NFLOG --nflog-prefix "WebServer-Drop: " --nflog-group 0
  /sbin/iptables-save

  service ulogd2 restart
  ```

- Explanation

    - `apt-get install ulogd2 -y` menginstall ulogd2 untuk melakukan logging terhadap paket yang didrop di webserver dan router.
    - `iptables -I INPUT 2 -p tcp -m tcp --dport 22 -j NFLOG --nflog-prefix "SSH-Drop: " --nflog-group 0` berguna untuk melakukan logging terhadap aturan nomor 3, dimana SSH pada semua Web Server hanya dapat dilakukan oleh user yang berada pada node Ran. 
    - `iptables -I INPUT 4 -p tcp -m multiport --dports 80,443 -m time --timestart 11:00 --timestop 13:00 --weekdays Fri -j NFLOG --nflog-prefix "Jumatan-Drop: " --nflog-group 0` berguna untuk melakukan logging terhadap aturan nomor 6 dimana Akses ke Web Server Conan, Sonoko, dan Megure pada port 80 dan 443 dilarang pada hari Jumat, pukul 11:00-13:00
    - `iptables -I INPUT 8 -j NFLOG --nflog-prefix "WebServer-Drop: " --nflog-group 0` berguna untuk melakukan logging default untuk paket yang didrop, selain 2 di atas.
    - `/sbin/iptables-save` untuk menyimpan konfigurasi iptables dan rule.
    - `service ulogd2 restart` berguna untuk merestart ulogd2 agar mendapat update aturan terbaru.

<br>

## Soal 8

> Untuk keperluan maintenance, pilih salah satu Subnet dan lakukan blokir terhadap semua request protokol ICMP (ping) dari luar subnet terhadap subnet tersebut.

> _For maintenance purposes, select one Subnet and block all ICMP (ping) protocol requests from outside the subnet to that subnet._

**Answer:**

- Screenshot

  Sebelum:
  <br>
  ![image](https://github.com/user-attachments/assets/8962ca0d-ba6f-4aeb-8992-59ebdf36aa24)
  <br>
  Setelah:
  <br>
  ![image](https://github.com/user-attachments/assets/552794f9-a520-4c1c-871b-880bb7e53f68)

- Configuration

  ```
  iptables -A INPUT -p icmp -d 192.235.2.0/23 -j REJECT
  iptables -A FORWARD -p icmp -d 192.235.2.0/23 -j REJECT
  /sbin/iptables-save
  ```

- Explanation
  
    - `INPUT` untuk memfilter paket yang menuju jaringan lokal.
    - `FORWARD` untuk memfilter paket yang diteruskan (melewati) firewall.
    - `-p icmp` menentukan protokol yang digunakan, dalam hal ini ICMP.
    - `192.235.2.0/23` adalah alamat subnet yang akan diberikan rules atau ketentuan.
    - `-j REJECT` berguna untuk menolak paket apabila tidak memenuhi kriteria.
    - `/sbin/iptables-save` untuk menyimpan konfigurasi iptables dan rule.

<br>

## Soal 9

> Untuk meningkatkan keamanan, setiap Web Server harus bisa melakukan blok terhadap IP yang melakukan scanning port dalam jumlah yang tidak wajar (maksimal 10 scan port) di dalam selang waktu 1 menit. 

> _To enhance security, each Web Server must be able to block IP addresses that perform an excessive number of port scans (a maximum of 10 port scans) within a 1-minute interval._

**Answer:**

- Screenshot

  ![image](https://github.com/user-attachments/assets/7fc5fb83-956b-476b-a0ca-430a8e29d21b)

- Configuration

  ```
  iptables -N portscan
  iptables -I INPUT 1 -m recent --name portscan --update --seconds 60 --hitcount 10 -j DROP
  iptables -I INPUT 2 -m recent --name portscan --set -j ACCEPT
  /sbin/iptables-save
  ```

- Explanation

  - `iptables -N portscan` berfungsi membuat chain baru dengan nama portscan untuk menangani aturan yang terkait dengan port scanning.
  - `iptables -I INPUT 1 -m recent --name portscan --update --seconds 60 --hitcount 10 -j DROP` berfungsi membatasi jumlah koneksi lebih dari 10 dari satu alamat IP dalam waktu 60 detik di chain INPUT, dan jika melanggar aturan, akan diblokir (DROP).
  - `iptables -I INPUT 2 -m recent --name portscan --set -j ACCEPT` berfungsi mencatat setiap koneksi yang diterima di chain INPUT sebagai koneksi yang sah dan mencatatnya dalam daftar portscan.
  - `/sbin/iptables-save` untuk menyimpan konfigurasi iptables dan rule.

<br>

## Soal 10

> Akses dari client ke WebServer Conan pada port 80 akan didistribusikan bergantian antara Web Server Conan dan Web Server Sonoko. Sebaliknya akses pada Web Server Sonoko pada port 443 akan didistribusikan bergantian antara Web Server Conan dan Web Server Sonoko. Lakukan evaluasi menggunakan Jmeter terhadap berbagai metode load balancing seperti Round-Robin dan lain-lainnya.

> _Client access to the Conan Web Server on port 80 should be alternated between the Conan Web Server and the Sonoko Web Server. Conversely, access to the Sonoko Web Server on port 443 should be alternated between the Conan Web Server and the Sonoko Web Server. (Evaluate various load balancing methods, such as Round-Robin and others, using JMeter.)_

**Answer:**

- Screenshot

    `Put your screenshot in here`

- Configuration

    `Put your configuration in here`

- Explanation

    `Put your explanation in here`


<br>
  
## Problems

## Revisions (if any)
