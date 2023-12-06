# 🖥️🖥️ Jarkom-Modul-4-D08-2023 🖥️🖥️

Nama Anggota | NRP
------------------- | --------------		
Timothy Hosia Budianto | 5025211098
Arif Nugraha Santosa | 5025211048

## 🟩🟩 LINK PROJECT 🟩🟩 
__PKT VLSM:__ [VLSM PKT D08](https://drive.google.com/file/d/1uYfPfVMBkqEj-0JNkC3dewWqfpeQV-Yp/view?usp=sharing)<br>
__GNS3 CIDR:__ [CIDR GNS3 D08](https://drive.google.com/file/d/1gIK1_YBB3VEAqkO0yveMyvRhctwKlmey/view?usp=sharing)<br>
__TREE VLSM:__ [Tree VLSM D08](https://drive.google.com/file/d/17ej-LO1PCHJkDfk7AEsO6os2MxRL-Diu/view?usp=sharing)<br>
__TREE CIDR:__ [Tree CIDR D08](https://drive.google.com/file/d/1cnMaacD1mONb-nF0Q8T4DpSt_pkiA8yg/view?usp=sharing)<br>
__DETAIL IP:__ [Tabel IP D08](https://docs.google.com/spreadsheets/d/1Lgq0Sz7B0TTtIRlqcLAwGYDS7Eg_C8UXXyhWM1G7EXA/edit?usp=sharing)<br>
__DETAIL IP GNS3:__ [IP GNS3 D08](https://docs.google.com/document/d/1a7ROE30dU5uKLNO18B8nhtG-gM1ttSDy_YoHVvwN4nU/edit?usp=sharing)



## 🟩🟩 JAWABAN SUBNETTING VLSM KELOMPOK D08 🟩🟩 
__Prefix IP Kelompok D08: 192.195.x.x__

### 🟢 Topologi pada Cisco Packet Tracer
![image](/assets/images/topologi.png)


Inti utama dari penggunaan teknik VLSM adalah untuk mengefisienkan pembagian IP di dalam jaringan. Besar netmask disesuaikan dengan banyaknya komputer/ host yang membutuhkan alamat IP.

### 🟢 Langkah 1️⃣
Tentukan jumlah alamat IP yang dibutuhkan oleh tiap subnet dan lakukan labelling netmask berdasarkan jumlah IP yang dibutuhkan.

Seperti yang kita lihat berdasarkan topologi di atas, setiap subnet sudah dibagi penamaannya dengan format _Ax_. Dimana x merupakan nomor subnet ke-x. Berikut adalah kebutuhan IP Address / Host yang dibutuhkan pada tiap tiap subnet.

Nama Subnet	| Rute | Jumlah IP | Netmask
----------- | ---- | --------- | -------
A1 | Aura - Frieren	| 2	| /30
A2 | Frieren - Switch3 - LakeKorridor | 25 | /27
A3 | Frieren - Flamme	| 2	| /30
A4 | Flamme - Fern	| 2	| /30
A5 | Fern - Switch4 - LaubHills & AppetitRegion	| 1023	| /21
A6 | Flamme - Switch5 - RohrRoad | 1001 | /22
A7 | Flamme - Himmel | 2 | /30
A8 | Himmel - Switch6 - SchwerMountains | 6 | /29
A9 | Aura - Eisen | 2 | /30
A10 | Eisen - Switch1 - Richter & Revolte | 3 | /29
A11 | Eisen - Linie | 2 | /30
A12 | Linie - Lawine | 2 | /30
A13 | Lawine - Switch7 - BredtRegion & Heiter | 31 | /26
A14 | Heiter - Switch8 - Sein & RiegelCanyon | 512 | /22
A15 | Linie - Switch11 - GranzChannel | 255 | /23
A16 | Eisen - Lugner | 2 | /30
A17 | Lugner - Switch10 - TurkRegion | 1001 | /22
A18 | Lugner - Switch9 - GlobeForest | 251 | /24
A19 | Eisen - Switch0 - Stark | 2 | /30
A20 | Aura - Denken | 2 | /30
A21 | Denken - Switch2 - RoyalCapital & WileRegion | 127 | /24
|  | Total | 4255 | /19

__Berikut adalah link untuk tabel lebih jelasnya:__
[Tabel Rute!](https://docs.google.com/spreadsheets/d/1Lgq0Sz7B0TTtIRlqcLAwGYDS7Eg_C8UXXyhWM1G7EXA/edit?usp=sharing)

Didapatkan total IP yang dibutuhkan sebanyak 4255 IP Address, maka dari itu kita akan menggunakan prefix /19 yang mana memiliki 8190 usable IP. 

Dari prefix tersebut akan dibuat sebuah major network yaitu __192.195.0.0/19__

### 🟢 Langkah 2️⃣
Tentukan jumlah alamat IP yang dibutuhkan oleh tiap subnet dan lakukan labelling netmask berdasarkan jumlah IP yang dibutuhkan.

Jumlah IP yang dibutuhkan adalah 4255 IP Addresses. Sehingga kita akan menggunakan major network yaitu __192.195.0.0/19__ sebagai puncak IP pembagiannya.

Berikut adalah tree/pohon pembagian IPnya.

![image](/assets/images/VLSM.drawio.png)

__Untuk gambar lebih jelasnya dapat diakses pada link berikut:__ [Tree VLSM D08](https://drive.google.com/file/d/17ej-LO1PCHJkDfk7AEsO6os2MxRL-Diu/view?usp=sharing)

Dari tree tersebut, kita gunakan data kebutuhan host IP per subnet untuk menentukan Network ID mana yang akan digunakan per subnetnya sesuai kebutuhan kita.

### 🟢 Langkah 3️⃣

Dari tree tersebut, kita subnetting dengan menggunakan pohon tersebut untuk pembagian IP sesuai dengan kebutuhan masing-masing subnet yang ada.

Network ID | Netmask | Jumlah Host | Nama Subnet | Prefix | Broadcast ID
---------- | ------- | ----------- | ----------- | ------ | ---------- | 
192.195.0.0 | 255.255.248.0 | 2,046 | A5 | /21 | 192.195.7.255
192.195.8.0 | 255.255.252.0 | 1,022 | A6 | /22 | 192.195.11.255
192.195.12.0 | 255.255.252.0 | 1,022 | A14 | /22 | 192.195.15.255
192.195.16.0 | 255.255.252.0 | 1,022 | A17 | /22 | 192.195.19.255
192.195.20.0 | 255.255.254.0 | 510 | A15 | /23 | 192.195.21.255
192.195.22.0 | 255.255.255.0 | 254 | A18 | /24 | 192.195.22.255
192.195.23.0 | 255.255.255.0 | 254 | A21 | /24 | 192.195.23.255
192.195.24.0 | 255.255.255.192 |62 | A13 | /26 | 192.195.24.63
192.195.24.64 | 255.255.255.224 | 30 | A2 | /27 | 192.195.24.95
192.195.24.96 | 255.255.255.248 | 6 | A8 | /29 | 192.195.24.103
192.195.24.104 | 255.255.255.248 | 6 | A10 | /29 | 192.195.24.111
192.195.24.112 | 255.255.255.252 | 2 | A1 | /30 | 192.195.24.115
192.195.24.116 | 255.255.255.252 | 2 | A3 | /30 | 192.195.24.119
192.195.24.120 | 255.255.255.252 | 2 | A4 | /30 | 192.195.24.123
192.195.24.124 | 255.255.255.252 | 2 | A7 | /30 | 192.195.24.127
192.195.24.128 | 255.255.255.252 | 2 | A9 | /30 | 192.195.24.131
192.195.24.132 | 255.255.255.252 | 2 | A11 | /30 | 192.195.24.135
192.195.24.136 | 255.255.255.252 | 2 | A12 | /30 | 192.195.24.139
192.195.24.140 | 255.255.255.252 | 2 | A16 | /30 | 192.195.24.143
192.195.24.144 | 255.255.255.252 | 2 | A19 | /30 | 192.195.24.147
192.195.24.148 | 255.255.255.252 | 2 | A20 | /30 | 192.195.24.151

__Berikut adalah link untuk tabel lebih jelasnya:__
[Tabel Perhitungan VLSM!](https://docs.google.com/spreadsheets/d/1Lgq0Sz7B0TTtIRlqcLAwGYDS7Eg_C8UXXyhWM1G7EXA/edit?usp=sharing)

### 🟢 Langkah 4️⃣

Setelah kita mendapatkan Network ID, Netmask, Broadcast ID, dan seluruh informasi mengenai tiap-tiap subnet. Kita dapat mengassign tiap-tiap IP berdasarkan interface setiap device yang berada di suatu subnet.

Untuk menentukan IP Address tiap interface, pastikan kita mengetahui nama interface yang terhubung dalam suatu subnet dari sebuah device. Kemudian berikan IP Address sesuai dengan range usable IP per prefixnya dan pastikan IP Address yang kita berikan berada dalam range Network ID dan Broadcast ID subnet tersebut.

#### 👇🏻 Network ID tiap Subnet

Sama seperti langkah 3, namun diurutkan berdasarkan nama prefixnya.

Nama Subnet | Network ID | Netmask | Prefix | Jumlah Host | Broadcast ID
----------- | ---------- | ------- | ------ | ----------- | ---------
A1 | 192.195.24.112 | 255.255.255.252 | /30 | 2   | 192.195.24.115
A2 | 192.195.24.64 | 255.255.255.224 | /27 | 30   | 192.195.24.95
A3 | 192.195.24.116 | 255.255.255.252 | /30 | 2   | 192.195.24.119
A4 | 192.195.24.120 | 255.255.255.252 | /30 | 2   | 192.195.24.123
A5 | 192.195.0.0 | 255.255.248.0 | /21 | 2,046   | 192.195.7.255
A6 | 192.195.8.0 | 255.255.252.0 | /22 | 1,022   | 192.195.11.255
A7 | 192.195.24.124 | 255.255.255.252 | /30 | 2   | 192.195.24.127
A8 | 192.195.24.96 | 255.255.255.248 | /29 | 6   | 192.195.24.103
A9 | 192.195.24.128 | 255.255.255.252 | /30 | 2   | 192.195.24.131
A10 | 192.195.24.104 | 255.255.255.248 | /29 | 6   | 192.195.24.111
A11 | 192.195.24.132 | 255.255.255.252 | /30 | 2   | 192.195.24.135
A12 | 192.195.24.136 | 255.255.255.252 | /30 | 2   | 192.195.24.139
A13 | 192.195.24.0 | 255.255.255.192 | /26 | 62   | 192.195.24.63
A14	| 192.195.12.0 | 255.255.252.0 | /22 | 1,022   | 192.195.15.255
A15	| 192.195.20.0 | 255.255.254.0 | /23 | 510   | 192.195.21.255
A16 | 192.195.24.140 | 255.255.255.252 | /30 | 2   | 192.195.24.143
A17	| 192.195.16.0 | 255.255.252.0 | /22 | 1,022   | 192.195.19.255
A18	| 192.195.22.0 | 255.255.255.0 | /24 | 254   | 192.195.22.255
A19	| 192.195.24.144 | 255.255.255.252 | /30 | 2   | 192.195.24.147
A20	| 192.195.24.148 | 255.255.255.252 | /30 | 2   | 192.195.24.151
A21	| 192.195.23.0 | 255.255.255.0 | /24 | 254   | 192.195.23.255

#### 👇🏻 Pembagian IP Per Node

Berikut adalah pembagian IP per node berdasarkan interfacesnya dan subnet interfacesnya.

Nama Node | Interface | IP Address | Jumlah Host | Network ID | Netmask | Broadcast ID | Nama Subnet
--------- | --------- | ---------- | ----------- | ---------- | ------- | ------------ | -----------
Aura | Eth1/0 | 192.195.24.113 | 2 | 192.195.24.112 | 255.255.255.252 | 192.195.24.115 | A1
Frieren | Eth1/0 | 192.195.24.114 | 2 | 192.195.24.112 | 255.255.255.252 | 192.195.24.115 | A1
Frieren | Eth1/1 | 192.195.24.65 | 30 | 192.195.24.64 | 255.255.255.224 | 192.195.24.95 | A2
LakeKorridor | Fa0 | 192.195.24.66 | 30 | 192.195.24.64 | 255.255.255.224 | 192.195.24.95 | A2
Frieren | Eth1/2 | 192.195.24.117 | 2 | 192.195.24.116 | 255.255.255.252 | 192.195.24.119 | A3
Flamme | Eth1/0 | 192.195.24.118 | 2 | 192.195.24.116 | 255.255.255.252 | 192.195.24.119 | A3
Flamme | Eth1/2 | 192.195.24.121 | 2 | 192.195.24.120 | 255.255.255.252 | 192.195.24.123 | A4
Fern | Eth1/0 | 192.195.24.122 | 2 | 192.195.24.120 | 255.255.255.252 | 192.195.24.123 | A4
Fern | Eth1/1 | 192.195.1.1 | 2,046 | 192.195.0.0 | 255.255.248.0 | 192.195.7.255 | A5
AppetitRegion | Fa0 | 192.195.2.1 | 2,046 | 192.195.0.0 | 255.255.248.0 | 192.195.7.255 | A5
LaubHills | Fa0 | 192.195.3.1 | 2,046 | 192.195.0.0 | 255.255.248.0 | 192.195.7.255 | A5
Flamme | Eth1/1 | 192.195.9.1 | 1,022 | 192.195.8.0 | 255.255.252.0 | 192.195.11.255 | A6
RohrRoad | Fa0 | 192.195.10.1 | 1,022 | 192.195.8.0 | 255.255.252.0 | 192.195.11.255 | A6
Flamme | Eth1/3 | 192.195.24.125 | 2 | 192.195.24.124 | 255.255.255.252 | 192.195.24.127 | A7
Himmel | Eth1/0 | 192.195.24.126 | 2 | 192.195.24.124 | 255.255.255.252 | 192.195.24.127 | A7
Himmel | Eth1/1 | 192.195.24.97 | 6 | 192.195.24.96 | 255.255.255.248 | 192.195.24.103 | A8
SchwerMountains | Fa0 | 192.195.24.98 | 6 | 192.195.24.96 | 255.255.255.248 | 192.195.24.103 | A8
Aura | Eth1/1 | 192.195.24.129 | 2 | 192.195.24.128 | 255.255.255.252 | 192.195.24.131 | A9
Eisen | Eth1/0 | 192.195.24.130 | 2 | 192.195.24.128 | 255.255.255.252 | 192.195.24.131 | A9
Eisen | Fa0/1 | 192.195.24.105 | 6 | 192.195.24.104 | 255.255.255.248 | 192.195.24.111 | A10
Richter | Fa0 | 192.195.24.107 | 6 | 192.195.24.104 | 255.255.255.248 | 192.195.24.111 | A10
Revolte | Fa0 | 192.195.24.108 | 6 | 192.195.24.104 | 255.255.255.248 | 192.195.24.111 | A10
Eisen | Eth1/3 | 192.195.24.133 | 2 | 192.195.24.132 | 255.255.255.252 | 192.195.24.135 | A11
Linie | Eth1/0 | 192.195.24.134 | 2 | 192.195.24.132 | 255.255.255.252 | 192.195.24.135 | A11
Linie | Eth1/2 | 192.195.24.137 | 2 | 192.195.24.136 | 255.255.255.252 | 192.195.24.139 | A12
Lawine | Eth1/0 | 192.195.24.138 | 2 | 192.195.24.136 | 255.255.255.252 | 192.195.24.139 | A12
Lawine | Eth1/1 | 192.195.24.1 | 62 | 192.195.24.0 | 255.255.255.192 | 192.195.24.63 | A13
BredtRegion | Fa0 | 192.195.24.2 | 62 | 192.195.24.0 | 255.255.255.192 | 192.195.24.63 | A13
Heiter | Eth1/0 | 192.195.24.3 | 62 | 192.195.24.0 | 255.255.255.192 | 192.195.24.63 | A13
Heiter | Eth1/1 | 192.195.13.1 | 1,022 | 192.195.12.0 | 255.255.252.0 | 192.195.15.255 | A14
ReigelCanyon | Fa0 | 192.195.14.1 | 1,022 | 192.195.12.0 | 255.255.252.0 | 192.195.15.255 | A14
Sein | Fa0 | 192.195.15.1 | 1,022 | 192.195.12.0 | 255.255.252.0 | 192.195.15.255 | A14
Linie | Eth1/1 | 192.195.20.1 | 510 | 192.195.20.0 | 255.255.254.0 | 192.195.21.255 | A15
GranzChannel | Fa0 | 192.195.21.1 | 510 | 192.195.20.0 | 255.255.254.0 | 192.195.21.255 | A15
Eisen | Eth1/2 | 192.195.24.141 | 2 | 192.195.24.140 | 255.255.255.252 | 192.195.24.143 | A16
Lugner | Eth1/0 | 192.195.24.142 | 2 | 192.195.24.140 | 255.255.255.252 | 192.195.24.143 | A16
Lugner | Eth1/1 | 192.195.16.1 | 1,022 | 192.195.16.0 | 255.255.252.0 | 192.195.19.255 | A17
TurkRegion | Fa0 | 192.195.16.2 | 1,022 | 192.195.16.0 | 255.255.252.0 | 192.195.19.255 | A17
Lugner | Eth1/2 | 192.195.22.1 | 254 | 192.195.22.0 | 255.255.255.0 | 192.195.22.255 | A18
GrobeForest | Fa0 | 192.195.22.2 | 254 | 192.195.22.0 | 255.255.255.0 | 192.195.22.255 | A18
Eisen | Eth1/1 | 192.195.24.145 | 2 | 192.195.24.144 | 255.255.255.252 | 192.195.24.147 | A19
Stark | Fa0 | 192.195.24.146 | 2 | 192.195.24.144 | 255.255.255.252 | 192.195.24.147 | A19
Aura | Eth1/2 | 192.195.24.149 | 2 | 192.195.24.148 | 255.255.255.252 | 192.195.24.151 | A20
Denken | Eth1/0 | 192.195.24.150 | 2 | 192.195.24.148 | 255.255.255.252 | 192.195.24.151 | A20
Denken | Eth1/1 | 192.195.23.1 | 254 | 192.195.23.0 | 255.255.255.0 | 192.195.23.255 | A21
RoyalCapital | Fa0 | 192.195.23.2 | 254 | 192.195.23.0 | 255.255.255.0 | 192.195.23.255 | A21
WilleRegion | Fa0 | 192.195.23.3 | 254 | 192.195.23.0 | 255.255.255.0 | 192.195.23.255 | A21

__Berikut adalah link untuk tabel lebih jelasnya:__
[Tabel Pembagian IP VLSM!](https://docs.google.com/spreadsheets/d/1Lgq0Sz7B0TTtIRlqcLAwGYDS7Eg_C8UXXyhWM1G7EXA/edit?usp=sharing)

__Note: Jangan lupa untuk memasukan IP Gateway tiap client kepada router yang terhubung dengannya.__<br>
Setelah menentukan IP tiap interface pada node, kita akan melakukan routing.

### 🟢 Langkah 5️⃣

Setelah setiap interfaces mendapatkan IP, kita akan melakukan static routing. Sebelum melakukan routing, pastikan setiap interface pada setiap node sudah menyala dan status duplexnya diubah menjadi __Full Duplex__ atau biarkan Auto saja. Seperti pada gambar di bawah.

![image](/assets/images/5_1.png)

Setelah dipastikan seluruh router dan clientnya dapat terhubung. Lakukan static routing dengan menekan tombol __Static__ pada masing-masing router.

![image](/assets/images/5_2.png)

Kemudian isilah __Network ID__ dan __Netmask__ tujuan kita routing. Dan isilah next hop dengan IP Address interface router yang menuju ke arah Network yang ingin kita route.

Saya akan mencontohkan salah satu contoh untuk melakukan routing dari A5 menuju A8

![image](/assets/images/contoh_1.png)

#### Penjelasan Singkat Routing pada CPT

Pada subnet A5, berikut adalah list IPnya:

Nama Node | Interface | IP Address | Jumlah Host | Network ID | Netmask | Broadcast ID | Nama Subnet
--------- | --------- | ---------- | ----------- | ---------- | ------- | ------------ | -----------
Fern | Eth1/1 | 192.195.1.1 | 2,046 | 192.195.0.0 | 255.255.248.0 | 192.195.7.255 | A5
AppetitRegion | Fa0 | 192.195.2.1 | 2,046 | 192.195.0.0 | 255.255.248.0 | 192.195.7.255 | A5
LaubHills | Fa0 | 192.195.3.1 | 2,046 | 192.195.0.0 | 255.255.248.0 | 192.195.7.255 | A5

Dan pada subnet A8, berikut adalah list IPnya:

Nama Node | Interface | IP Address | Jumlah Host | Network ID | Netmask | Broadcast ID | Nama Subnet
--------- | --------- | ---------- | ----------- | ---------- | ------- | ------------ | -----------
Himmel | Eth1/1 | 192.195.24.97 | 6 | 192.195.24.96 | 255.255.255.248 | 192.195.24.103 | A8
SchwerMountains | Fa0 | 192.195.24.98 | 6 | 192.195.24.96 | 255.255.255.248 | 192.195.24.103 | A8

Perhatikan bahwa jalan A5 menuju A8 akan melalui A4 ➡️ A7 dan begitu pula sebaliknya.

Nama Node | Interface | IP Address | Jumlah Host | Network ID | Netmask | Broadcast ID | Nama Subnet
--------- | --------- | ---------- | ----------- | ---------- | ------- | ------------ | -----------
Flamme | Eth1/2 | 192.195.24.121 | 2 | 192.195.24.120 | 255.255.255.252 | 192.195.24.123 | A4
Fern | Eth1/0 | 192.195.24.122 | 2 | 192.195.24.120 | 255.255.255.252 | 192.195.24.123 | A4
Flamme | Eth1/3 | 192.195.24.125 | 2 | 192.195.24.124 | 255.255.255.252 | 192.195.24.127 | A7
Himmel | Eth1/0 | 192.195.24.126 | 2 | 192.195.24.124 | 255.255.255.252 | 192.195.24.127 | A7

Masukan perintah-perintah berikut ke dalam CLI router:

Apabila router belum masuk ke global configuration mode. Maka gunakan command
```
Router> enable
```
kemudian,
```
Router# configure terminal
```
Apabila router sudah masuk dalam mode
```
Router(config)# 
```

Maka masukan command di bawah ini pada setiap node.

#### Fern:
```
ip route 192.195.24.96 255.255.255.248 192.195.24.121
```

Keterangan: 
- 192.195.24.96 adalah Network ID dari A8.
- 255.255.255.248 adalah Netmask dari A8.
- 192.195.24.121 adalah IP Flamme yang mengarah ke A8 (Terhubung dengan Fern).

#### Flamme:
```
ip route 192.195.24.96 255.255.255.248 192.195.24.126
ip route 192.195.0.0 255.255.248.0 192.195.24.122
```
Keterangan: 
- 192.195.24.96 adalah Network ID dari A8.
- 255.255.255.248 adalah Netmask dari A8.
- 192.195.24.126 adalah Himmel yang mengarah ke A8 (Terhubung dengan Flamme).
- 192.195.0.0 adalah Network ID dari A5.
- 255.255.248.0 adalah Netmask dari A5.
- 192.195.24.122 adalah Fern yang mengarah ke A5 (Terhubung dengan Flamme).

#### Himmel:
```
ip route 192.195.0.0 255.255.248.0 192.195.24.125
```
Keterangan: 
- 192.195.0.0 adalah Network ID dari A5.
- 255.255.248.0 adalah Netmask dari A5.
- 192.195.24.125 adalah IP Flamme yang mengarah ke A5 (Terhubung dengan Himmel).

Lakukan hal yang sama sehingga setiap subnet akan terhubung. Berikut adalah gambar hasil routing per router:

#### Aura:
![image](/assets/images/aura.png)

#### Frieren:
![image](/assets/images/frieren.png)

#### Flamme:
![image](/assets/images/flamme.png)

#### Fern:
![image](/assets/images/fern.png)

#### Himmel:
![image](/assets/images/himmel.png)

#### Denken:
![image](/assets/images/denken.png)

#### Eisen:
![image](/assets/images/eisen.png)

#### Lugner:
![image](/assets/images/lugner.png)

#### Linie:
![image](/assets/images/linie.png)

#### Lawine:
![image](/assets/images/lawine.png)

#### Heiter:
![image](/assets/images/heiter.png)

__Berikut adalah file .pkt:__ [D08 VLSM PKT](https://drive.google.com/file/d/1uYfPfVMBkqEj-0JNkC3dewWqfpeQV-Yp/view?usp=sharing)

### ⭕ Testing

![image](/assets/images/ping.png)

## 🟩🟩 JAWABAN SUBNETTING CIDR KELOMPOK D08 🟩🟩 

### 🟢 Topologi pada GNS3

- Pertama subnet di kelompokkan dan digabungkan seperti gambar di bawah.

![image](https://github.com/thossb/jarkom-modul-4-D08-2023/assets/90438426/2b3331fe-fab9-43cd-898d-da8bd5e309e7)

- Langkah penggabungannya adalah sebagai berikut.

![image](https://github.com/thossb/jarkom-modul-4-D08-2023/assets/90438426/9bda1b07-5b3e-4616-ba68-9952b29ae200)

- Setelah itu kita akan membuat IP/subnet tree untuk mendapatkan IP tiap node nya.

![image](https://github.com/thossb/jarkom-modul-4-D08-2023/assets/90438426/f0ffa135-733f-4fdd-b088-7cabd5e9bc82)

__Gambar Tree yang lebih jelas:__ https://miro.com/app/board/uXjVNI4708I=/?share_link_id=299592889559I

- Setelah dapat pembagian ip, sekarang kita assign ip tiap node

![image](https://github.com/thossb/jarkom-modul-4-D08-2023/assets/90438426/43b90170-b378-4e6b-9bd8-dd4e04fc8ee7)
![image](https://github.com/thossb/jarkom-modul-4-D08-2023/assets/90438426/1573c63e-96dd-444c-9b36-17a8cb009bef)
![image](https://github.com/thossb/jarkom-modul-4-D08-2023/assets/90438426/3b2422f6-3833-4943-be7c-e702b52be015)

- Lalu kita masukan IP yang sudah dibuat tersebut ke dalam setiap interfaces pada setiap node yang ada.

__DETAIL IP GNS3:__ [IP GNS3 D08](https://docs.google.com/document/d/1a7ROE30dU5uKLNO18B8nhtG-gM1ttSDy_YoHVvwN4nU/edit?usp=sharing)

- Setelah itu kita lakukan routing agar semua node terhubung, berikut konfigurasinya.

```sh
—--------------------------------------------

A1 > A2 = AURA - FRIEREN - LK
(AURA) route add -net 192.195.64.0 netmask 255.255.255.224 gw 192.195.128.2

A1 > A3 = AURA - FRIEREN - FLAMME
(AURA) route add -net 192.195.32.0 netmask 255.255.255.252 gw 192.195.128.2

A1> A4 = AURA - FRIEREN - FLAMME - FERN
(AURA) route add -net 192.195.8.0 netmask 255.255.255.252 gw 192.195.128.2
(FRIEREN) route add -net 192.195.8.0 netmask 255.255.255.252 gw 192.195.32.2

A1 > A5 = AURA - FRIEREN - FLAMME - FERN - LH/AR
(AURA) route add -net 192.195.0.0 netmask 255.255.248.0 gw 192.195.128.2
(FRIEREN) route add -net 192.195.0.0 netmask 255.255.248.0 gw 192.195.32.2
(FLAMME) route add -net 192.195.0.0 netmask 255.255.248.0 gw 192.195.8.2

A1 > A6 = AURA - FRIEREN - FLAMME - RR
(AURA) route add -net 192.195.16.0 netmask 255.255.252.0 gw 192.195.128.2
(FRIEREN) route add -net 192.195.16.0 netmask 255.255.252.0 gw 192.195.32.2

A1 > A7 = AURA - FRIEREN - FLAMME - HIMMEL
(AURA) route add -net 192.195.28.0 netmask 255.255.255.252 gw 192.195.128.2
(FRIEREN) route add -net 192.195.28.0 netmask 255.255.255.252 gw 192.195.32.2

A1 > A8 = AURA - FRIEREN - FLAMME - HIMMEL - SM
(AURA) route add -net 192.195.28.0 netmask 255.255.255.252 gw 192.195.128.2
(FRIEREN) route add -net 192.195.24.0 netmask 255.255.255.248 gw 192.195.32.2
(FLAMME) route add -net 192.195.24.0 netmask 255.255.255.248 gw 192.195.28.2

—------------------------------
A9 > A10 = AURA - EISEN - RICHTER/REVOLTE
(AURA) route add -net 192.197.64.0 netmask 255.255.255.248 gw 192.198.0.2

A9 > A11 = AURA - EISEN - LINIE
(AURA) route add -net 192.197.32.0 netmask 255.255.255.252 gw 192.198.0.2

A9 > A12 = AURA - EISEN - LINIE - LAWINE
(AURA) route add -net 192.197.8.0 netmask 255.255.255.252 gw 192.198.0.2
(EISEN) route add -net 192.197.8.0 netmask 255.255.255.252 gw 192.197.32.2

A9 > A13 = AURA - EISEN - LINIE - LAWINE - BR/HEITER
(AURA) route add -net 192.197.4.0 netmask 255.255.255.192 gw 192.198.0.2
(EISEN) route add -net 192.197.4.0 netmask 255.255.255.192 gw 192.197.32.2
(LINIE) route add -net 192.197.4.0 netmask 255.255.255.192 gw 192.197.8.2

A9 > A14 = AURA - EISEN - LINIE - LAWINE - SEIN/RC
(AURA) route add -net 192.197.0.0 netmask 255.255.252.0 gw 192.198.0.2
(EISEN) route add -net 192.197.0.0 netmask 255.255.252.0 gw 192.197.32.2
(LINIE) route add -net 192.197.0.0 netmask 255.255.252.0 gw 192.197.8.2
(LAWINE) route add -net 192.197.0.0 netmask 255.255.252.0 gw 192.197.4.2

A9 > A15 = AURA - EISEN - LINIE - GC
(AURA) route add -net 192.197.16.0 netmask 255.255.254.0 gw 192.198.0.2
(EISEN) route add -net 192.197.16.0 netmask 255.255.254.0 gw 192.197.32.2

A9 > A16 = AURA - EISEN - LUGNER
(AURA) route add -net 192.197.160.0 netmask 255.255.255.252 gw 192.198.0.2

A9 > A17 = AURA - EISEN - LUGNER - TR
(AURA) route add -net 192.197.128.0 netmask 255.255.252.0 gw 192.198.0.2
(EISEN) route add -net 192.197.128.0 netmask 255.255.252.0 192.197.160.2

A9 > A18 = AURA - EISEN - LUGNER - GF
(AURA) route add -net 192.197.144.0 netmask 255.255.255.0 gw 192.198.0.2
(EISEN) route add -net 192.197.144.0 netmask 255.255.255.0 gw 192.197.160.2

A9 > A19 = AURA - EISEN - STARK
(AURA) route add -net 192.197.192.0 netmask 255.255.255.252 gw 192.198.0.2

—----------------------
A20 > A21 = AURA - DENKEN - RC/WR 
(AURA) route add -net 192.196.0.0 netmask 255.255.255.0 gw 192.196.128.2


CONCUSSION
AURA
route add -net 192.195.64.0 netmask 255.255.255.224 gw 192.195.128.2
route add -net 192.195.32.0 netmask 255.255.255.252 gw 192.195.128.2
route add -net 192.195.8.0 netmask 255.255.255.252 gw 192.195.128.2
route add -net 192.195.0.0 netmask 255.255.248.0 gw 192.195.128.2
route add -net 192.195.16.0 netmask 255.255.252.0 gw 192.195.128.2
route add -net 192.195.28.0 netmask 255.255.255.252 gw 192.195.128.2
route add -net 192.195.24.0 netmask 255.255.255.248 gw 192.195.128.2
route add -net 192.197.64.0 netmask 255.255.255.248 gw 192.198.0.2
route add -net 192.197.32.0 netmask 255.255.255.252 gw 192.198.0.2
route add -net 192.197.8.0 netmask 255.255.255.252 gw 192.198.0.2
route add -net 192.197.4.0 netmask 255.255.255.192 gw 192.198.0.2
route add -net 192.197.0.0 netmask 255.255.252.0 gw 192.198.0.2
route add -net 192.197.16.0 netmask 255.255.254.0 gw 192.198.0.2
route add -net 192.197.160.0 netmask 255.255.255.252 gw 192.198.0.2
route add -net 192.197.128.0 netmask 255.255.252.0 gw 192.198.0.2
route add -net 192.197.144.0 netmask 255.255.255.0 gw 192.198.0.2
route add -net 192.197.192.0 netmask 255.255.255.252 gw 192.198.0.2
route add -net 192.196.0.0 netmask 255.255.255.0 gw 192.196.128.2

FRIEREN
route add -net 192.195.8.0 netmask 255.255.255.252 gw 192.195.32.2
route add -net 192.195.0.0 netmask 255.255.248.0 gw 192.195.32.2
route add -net 192.195.16.0 netmask 255.255.252.0 gw 192.195.32.2
route add -net 192.195.28.0 netmask 255.255.255.252 gw 192.195.32.2
route add -net 192.195.24.0 netmask 255.255.255.248 gw 192.195.32.2

FLAMME
route add -net 192.195.0.0 netmask 255.255.248.0 gw 192.195.8.2
route add -net 192.195.24.0 netmask 255.255.255.248 gw 192.195.28.2

EISEN
route add -net 192.197.8.0 netmask 255.255.255.252 gw 192.197.32.2
route add -net 192.197.4.0 netmask 255.255.255.192 gw 192.197.32.2
route add -net 192.197.0.0 netmask 255.255.252.0 gw 192.197.32.2
route add -net 192.197.16.0 netmask 255.255.254.0 gw 192.197.32.2
route add -net 192.197.128.0 netmask 255.255.252.0 gw 192.197.160.2
route add -net 192.197.144.0 netmask 255.255.255.0 gw 192.197.160.2

LINIE
route add -net 192.197.4.0 netmask 255.255.255.192 gw 192.197.8.2
route add -net 192.197.0.0 netmask 255.255.252.0 gw 192.197.8.2

LAWINE
route add -net 192.197.0.0 netmask 255.255.252.0 gw 192.197.4.2

```

- Hasil dan testing, kita bisa melakukan ping / traceroute ke node lain . Contoh Hasilnya adalah sebagai berikut

![image](https://github.com/thossb/jarkom-modul-4-D08-2023/assets/90438426/4064d783-2378-4f69-93ca-3d7bd15d447c)

![image](https://github.com/thossb/jarkom-modul-4-D08-2023/assets/90438426/c61c2aae-7be1-43c7-914e-ac58b4a6281b)


