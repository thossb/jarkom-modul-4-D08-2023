# 🖥🖥 Jarkom-Modul-4-D08-2023 🖥🖥

Nama Anggota | NRP
------------------- | --------------		
Timothy Hosia Budianto | 5025211098
Arif Nugraha Santosa | 5025211048

## Problem CIDR dengan GNS3
- pertama subnet di kelompokkan dan digabungkan seperti gambar di bawah
![image](https://github.com/thossb/jarkom-modul-4-D08-2023/assets/90438426/2b3331fe-fab9-43cd-898d-da8bd5e309e7)
- link gns : https://drive.google.com/file/d/1gIK1_YBB3VEAqkO0yveMyvRhctwKlmey/view?usp=sharing
- Langkkah penggabungannya adalah sebagai berikut

![image](https://github.com/thossb/jarkom-modul-4-D08-2023/assets/90438426/9bda1b07-5b3e-4616-ba68-9952b29ae200)
- setelah itu kita akan membuat ip/subnet tree untuk mendapatkan ip tiap node nya
![image](https://github.com/thossb/jarkom-modul-4-D08-2023/assets/90438426/f0ffa135-733f-4fdd-b088-7cabd5e9bc82)
- link miro : https://miro.com/app/board/uXjVNI4708I=/?share_link_id=299592889559I
- setelah dapat pembagian ip, sekarang kita assign ip tiap node
![image](https://github.com/thossb/jarkom-modul-4-D08-2023/assets/90438426/43b90170-b378-4e6b-9bd8-dd4e04fc8ee7)
![image](https://github.com/thossb/jarkom-modul-4-D08-2023/assets/90438426/1573c63e-96dd-444c-9b36-17a8cb009bef)
![image](https://github.com/thossb/jarkom-modul-4-D08-2023/assets/90438426/3b2422f6-3833-4943-be7c-e702b52be015)
- lalu kita konfigurasi ip tiap node di gns, lalu perpindah kita lakukan routing
- berikut link konfigurasi ip tiap node : https://docs.google.com/document/d/1a7ROE30dU5uKLNO18B8nhtG-gM1ttSDy_YoHVvwN4nU/edit?usp=sharing
- setelah itu kita kinfigurasi routing agar semuanya terhubung, berikut konfigurasu nya
```
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


