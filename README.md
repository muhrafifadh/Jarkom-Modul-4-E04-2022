# Jarkom-Modul-4-E01-2021

- Clarence 05111940000104
- Nur Putra Khanafi 05111940000020
- Husnan 05111940007002

### List

1. [Problem VLSM dengan CPT](https://github.com/nurputrak/Jarkom-Modul-4-E01-2021#vlsmvariable-length-subnet-masking)
2. [Problem CIDR dengan GNS3](https://github.com/nurputrak/Jarkom-Modul-4-E01-2021#CIDR)

## Pembagian Subnet

![image](https://user-images.githubusercontent.com/55318172/143030727-cda6d42a-9925-4d7e-b819-5525f7c7bb8e.png)

## VLSM(Variable Length Subnet Masking)

Menentukan jumlah alamat IP yang dibutuhkan oleh tiap subnet dan  melabel netmask berdasarkan jumlah IP yang dibutuhkan.

| Subnet | Alias | Jumlah IP  | Netmask |
| --- | --- | --- | --- |
| A1 | jipangu - pucci | 101 | /25 |
| A2 | court - calm - pucc | 2021 | /21 |
| A3 | pucc - wat7 | 2 | /30 |
| A4 | ciph - wat7 | 701 | /22 |
| A5 | blueno - foosha | 1001 | /22 |
| A6 | wat7 - foosha | 2 | /30 |
| A7 | foosha - guanhao | 2 | /30 |
| A8 | jabra - guanhao | 521 | /22 |
| A9 | guan - alabas - maingate | 502 | /23 |
| A10 | alaba - jorge | 13 | /28 |
| A11 | guan - oimo | 2 | /30 |
| A12 | enies - seast - oimo | 252 | /24 |
| A13 | seast - elena | 721 | /22 |
| A14 | foosha -doriki | 2 | /30 |
| A15 | oimo - fukurou | 2 | /30 |
| Total |  | 5845 | /19 |

### Pohon IP

Subnet besar yang dibentuk memiliki NID 192.200.0.0 dengan netmask /19 sehingga pembagian IP berdasarkan NID dan netmask dihitung sesuai dengan pohon berikut.

![image](https://user-images.githubusercontent.com/55318172/143030798-3d3986c7-0c44-43ff-90b6-57713392ed79.png)

Pada VLSM ini diturunkan sesuai dengan length atasnya sehingga ketika /19 akan diturunkan menjadi /20, dan pembagian IPnya mengikuti tabel. Kemudian jika ada subnet yang bisa diassign, maka kita langsung mengassign. Hal ini dilakukan berulang" sampai semua subnet selesai di assign.

### Subnet + IP

Selanjutnya menyesuaikan pembagian IP sesuai dengan subnet yang telah dibagi berdasarkan pohon diatas pada topologi. Setelah itu akan didapatkan pembagian IP untuk tiap nodenya.

![image](https://user-images.githubusercontent.com/55318172/143030843-8acda53c-1d70-41b2-8c21-3597a420d949.png)


### Hasil Pembagian IP per node

| Subnet | Node | IP | Subnet Mask | Length |
| --- | --- | --- | --- | --- |
| A1 | Pucci | 192.200.27.1 | 255.255.255.128 | /25 |
| A1 | Jipangu | 192.200.27.2 | 255.255.255.128 |  |
| A2 | Pucci | 192.200.0.1 | 255.255.248.0 | /21 |
| A2 | Courtyard | 129.200.0.2 | 255.255.248.0 |  |
| A2 | Calmbelt | 129.200.0.3 | 255.255.248.0 |  |
| A3 | Pucci | 192.200.27.145 | 255.255.255.252 | /30 |
| A3 | Water7 | 192.200.27.146 | 255.255.255.252 |  |
| A4 | Water7 | 192.200.8.1 | 255.255.252.0 | /22 |
| A4 | Cipher | 192.200.8.2 | 255.255.252.0 |  |
| A5 | Foosha | 192.200.12.1 | 255.255.252.0 | /22 |
| A5 | Blueno | 192.200.12.2 | 255.255.252.0 |  |
| A6 | Water7 | 192.200.27.149 | 255.255.255.252 | /30 |
| A6 | Foosha | 192.200.27.150 | 255.255.255.252 |  |
| A7 | Foosha | 192.200.27.153 | 255.255.255.252 | /30 |
| A7 | Guanhao | 192.200.27.154 | 255.255.255.252 |  |
| A8 | Guanhao | 192.200.16.1 | 255.255.252.0 | /22 |
| A8 | Jabra | 192.200.16.2 | 255.255.252.0 |  |
| A9 | Guanhao | 192.200.24.1 | 255.255.254.0 | /23 |
| A9 | Alabasta | 192.200.24.2 | 255.255.254.0 |  |
| A9 | Maingate | 192.200.24.3 | 255.255.254.0 |  |
| A10 | Alabasta | 192.200.27.129 | 255.255.255.240 | /28 |
| A10 | Jorge | 192.200.27.130 | 255.255.255.240 |  |
| A11 | Guanhao | 192.200.27.157 | 255.255.255.252 | /30 |
| A11 | Oimo | 192.200.27.158 | 255.255.255.252 |  |
| A12 | Oimo | 192.200.26.1 | 255.255.255.0 | /24 |
| A12 | Seastone | 192.200.26.2 | 255.255.255.0 |  |
| A12 | Enieslobby | 192.200.26.3 | 255.255.255.0 |  |
| A13 | Seastone | 192.200.20.1 | 255.255.252.0 | /22 |
| A13 | Elena | 192.200.20.2 | 255.255.252.0 |  |
| A14 | Foosha | 192.200.27.161 | 255.255.255.252 | /30 |
| A14 | Doriki | 192.200.27.162 | 255.255.255.252 |  |
| A15 | Oimo | 192.200.27.165 | 255.255.255.252 | /30 |
| A15 | Fukurou | 192.200.27.166 | 255.255.255.252 |  |

### Assignment pada CPT

![image](https://user-images.githubusercontent.com/55318172/143670080-b97f4a5e-f411-4da8-92b1-075a74395b6b.png)

Contoh pada pucci, kita menambahkan IP dan Subnet Mask sesuai dengan pembagian yang telah dilakukan, dengan IP ditambah 1 dari subnetnya. Hal ini diassign untuk semua router, client dan server.

Pada server & Client ditambahkan juga gateway yang mengarah ke router terdekat.

![image](https://user-images.githubusercontent.com/55318172/143670107-2f9e5fff-ea11-4712-9006-abdbd4e99d52.png)


### Menambah Ethernet

Karena default hanya memiliki 2 port ethernet, maka kita bisa menambah port pada tab physical

![image](https://user-images.githubusercontent.com/55318172/143670287-44136d1e-15cb-4508-819d-aad0e9fa92bc.png)

Contoh pada foosha kami menambah 3 port lagi karena butuh terkoneksi 5 cabang

### Routing

Pada routing berikut adalah config" yang berada pada router.

#### Pucci

![image](https://user-images.githubusercontent.com/55318172/143670128-dfb5e35d-356e-49e5-8e28-7d2de7280a99.png)

0.0.0.0 berarti mengambil semua pesan dan diarahkan ke next hop.

#### Water7

![image](https://user-images.githubusercontent.com/55318172/143670137-3f45dd8f-b680-4b8b-bac1-4fb0925a422d.png)

Pada water7 kita mengarahkan ke subnet 27.0 dan 20.0 dengan next hop ke pucci.

#### Seastone

![image](https://user-images.githubusercontent.com/55318172/143670149-3ea5851c-ec70-48f6-adf4-639589da104c.png)


#### Oimo

![image](https://user-images.githubusercontent.com/55318172/143670163-9a1130b7-6923-4d12-b157-c0904ab3ec1f.png)

Pada Oimo ditambahkan routing untuk ke subnet Elena

#### Alabasta

![image](https://user-images.githubusercontent.com/55318172/143670177-1a786a5b-b228-4ccc-9936-bee498307cea.png)

#### Guanhao

![CleanShot 2021-11-27 at 13 06 10](https://user-images.githubusercontent.com/55318172/143670188-ce53921b-852e-4553-9693-8d247c430267.png)

Guanhao memiliki tanggung jawab untuk mengarahkan subnet" di bawah Oimo dan subnet di kanan guanhao yaitu jorge

#### Foosha

![image](https://user-images.githubusercontent.com/55318172/143670215-706b09d7-bbf4-494c-9fec-54216ae4defa.png)

Karena kita sudah melakukan routing banyak di Guanhao dan Water7, Foosha akan bertugas untuk mensortir request yang masuk dan mengarahkan antara ke guanhao atau water7

### VLSM Routing Check 

https://user-images.githubusercontent.com/55318172/143031251-1e2bdc97-7a13-49dc-8a0d-4f90056357ab.mp4

## CIDR

Menggabungkan subnet-subnet paling bawah dalam topologi yaitu dimulai dari subnet yang paling jauh dari internet(gambar awan).

#### Kondisi Awal

![image](https://user-images.githubusercontent.com/55318172/143031393-5d270e7e-9c79-477c-bcc0-4225c9198df3.png)

#### Gabungan Pertama(Subnet B)

1. Penggabungan 1 yaitu subnet A1 dan A2 menghasilkan B1 dengan netmask /20 yaitu satu tingkat dari netmask terbesar yang diambil yaitu /21 dari A2.
2. Penggabungan 2 yaitu subnet A12 dan A13 menghasilkan B2 dengan netmask /21 (satu tingkat dari /22).
3. Penggabungan 3 yaitu subnet A9 dan A10 menghasilkan B3 dengan netmask /22 (satu tingkat dari /23).

![image](https://user-images.githubusercontent.com/55318172/143031408-3d7fe57e-8559-4034-ad8d-9de585c52619.png)

#### Gabungan Kedua(Subnet C)

1. Penggabungan 1 yaitu subnet B1 dan A3 menghasilkan C1 dengan netmask /19 yaitu satu tingkat dari netmask terbesar yang diambil yaitu /20 dari B1.
2. Penggabungan 2 yaitu subnet B2 dan A15 menghasilkan C2 dengan netmask /20.
3. Penggabungan 3 yaitu subnet B3 dan A8 menghasilkan B3 dengan netmask /21.

![image](https://user-images.githubusercontent.com/55318172/143031429-62803a1a-cb51-4b1e-b541-b12658d80e4e.png)

#### Gabungan Ketiga(Subnet D)

1. Penggabungan 1 yaitu subnet C1 dan A4 menghasilkan D1 dengan netmask /18 yaitu satu tingkat dari netmask terbesar yang diambil yaitu /19 dari C1.
2. Penggabungan 2 yaitu subnet C2 dan A11 menghasilkan D2 dengan netmask /19.

![image](https://user-images.githubusercontent.com/55318172/143031448-6e47724a-4b41-4418-a486-ed84a17fc963.png)

#### Gabungan Keempat(Subnet E)

1. Penggabungan 1 yaitu subnet D1 dan A6 menghasilkan E1 dengan netmask /17 yaitu satu tingkat dari netmask terbesar yang diambil yaitu /18 dari D1.
2. Penggabungan 2 yaitu subnet D2 dan C3 menghasilkan E2 dengan netmask /18.

![image](https://user-images.githubusercontent.com/55318172/143031467-09182464-4e0d-4dfb-9114-798ce77990b1.png)

#### Gabungan Kelima(Subnet F)

1. Penggabungan 1 yaitu subnet E1 dan A5 menghasilkan F1 dengan netmask /16 yaitu satu tingkat dari netmask terbesar yang diambil yaitu /17 dari E1.
2. Penggabungan 2 yaitu subnet E2 dan A7 menghasilkan F2 dengan netmask /17.

![image](https://user-images.githubusercontent.com/55318172/143031507-354f3610-5eb8-45d2-951c-46fce3168096.png)

#### Gabungan Keenam(Subnet G)

Pada step ini hanya terjadi satu penggabungan yaitu subnet F2 dan A14 menghasilkan G1 dengan netmask /16 yaitu satu tingkat dari netmask terbesar yang diambil yaitu /17 dari F2.

![image](https://user-images.githubusercontent.com/55318172/143031532-8c0800ac-703d-4917-ab26-1969a7bb5f7e.png)

#### Gabungan Ketujuh(Subnet H)

Step terakhir yaitu menggabungkan dua kelompok F1 dan G1 menjadi satu yaitu subnet H1 dengan netmask /15.

![image](https://user-images.githubusercontent.com/55318172/143031579-3d5f6775-46ff-4a14-b423-901617d70d39.png)

### Pohon IP

Dari penggabungan yang telah dilakukan, didapatkan pohon pembagian IP sebagai berikut.

![image](https://user-images.githubusercontent.com/55318172/143033944-8ba7468d-6cce-4ce0-9b47-609e05b19d47.png)


### Tabel Pembagian IP

Maka didapatkan hasil pembagian IP sesuai pada tabel berikut.

| Subnet | Node | IP | Subnet Mask | Length |
| --- | --- | --- | --- | --- |
| A1 | jipangu pucci | 192.201.8.0 | 255.255.255.128 | 25 |
| A2 | court, calm, puc | 192.201.0.0 | 255.255.248.0 | 21 |
| A3 | pucci water | 192.201.16.0 | 255.255.255.252 | 30 |
| A4 | cipher water | 192.201.32.0 | 255.255.252.0 | 22 |
| A5 | blueno foosh | 192.201.128.0 | 255.255.252.0 | 22 |
| A6 | foosh wat | 192.201.64.0 | 255.255.255.252 | 30 |
| A7 | foosh guan | 192.200.64.0 | 255.255.255.252 | 30 |
| A8 | guan jabra | 192.200.36.0 | 255.255.252.0 | 22 |
| A9 | guanhao maingate alabas | 192.200.32 .0 | 255.255.254.0 | 23 |
| A10 | alabas jorge | 192.200.34.0 | 255.255.255.240 | 28 |
| A11 | guan oimo | 192.200.16.0 | 255.255.255.252 | 30 |
| A12 | oimo enies seastone | 192.200.4.0 | 255.255.255.0 | 24 |
| A13 | seas elena | 192.200.0.0 | 255.255.252.0 | 22 |
| A14 | foosha doriki | 192.200.128.0 | 255.255.255.252 | 30 |
| A15 | fukurou oimo | 192.200.8.0 | 255.255.255.252 | 30 |

### Konfigurasi ETH

Pada network configuration, kita melakukan assignment dengan IP yang telah ditetapkan sesuai dengan subnet

#### Jipangu

```bash
auto eth0
iface eth0 inet static
address 192.201.8.2
netmask 255.255.255.128
gateway 192.201.8.1
```

#### Pucci

```bash
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.201.16.1
netmask 255.255.255.252
gateway 192.201.16.2

auto eth1
iface eth1 inet static
address 192.201.8.1
netmask 255.255.255.128

auto eth2
iface eth2 inet static
address 192.201.0.1
netmask 255.255.248.0
```

#### Courtyard

```bash
auto eth0
iface eth0 inet static
address 192.201.0.2
netmask 255.255.248.0
gateway 192.201.0.1
```

#### Calmbelt

```bash
auto eth0
iface eth0 inet static
address 192.201.0.3
netmask 255.255.248.0
gateway 192.201.0.1
```

#### Water7

```bash
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.201.64.1
netmask 255.255.255.252
gateway 192.201.64.2

auto eth1
iface eth1 inet static
address 192.201.32.1
netmask 255.255.252.0

auto eth2
iface eth2 inet static
address 192.201.16.2
netmask 255.255.255.252
```

#### Cipher

```bash
auto eth0
iface eth0 inet static
address 192.201.32.2
netmask 255.255.252.0
gateway 192.201.32.1
```

#### Foosha

```bash
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
address 192.201.128.1
netmask 255.255.252.0

auto eth2
iface eth2 inet static
address 192.201.64.2
netmask 255.255.255.252

auto eth3
iface eth3 inet static
address 192.200.128.1
netmask 255.255.255.252

auto eth4
iface eth4 inet static
address 192.200.64.1
netmask 255.255.255.252
```

#### Blueno

```bash
auto eth0
iface eth0 inet static
address 192.201.128.2
netmask 255.255.252.0
gateway 192.201.128.1
```

#### Doriki

```bash
auto eth0
iface eth0 inet static
address 192.200.128.2
netmask 255.255.255.252
gateway 192.200.128.1
```

#### Guanhao

```bash
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.200.64.2
netmask 255.255.255.252
gateway 192.200.64.1

auto eth1
iface eth1 inet static
address 192.200.36.1
netmask 255.255.252.0

auto eth2
iface eth2 inet static
address 192.200.32.1
netmask 255.255.254.0


auto eth3
iface eth3 inet static
address 192.200.16.1
netmask 255.255.255.252
```

#### Jabra

```bash
auto eth0
iface eth0 inet static
address 192.200.36.2
netmask 255.255.252.0
gateway 192.200.36.1
```

#### Maingate

```bash
auto eth0
iface eth0 inet static
address 192.200.32.3
netmask 255.255.254.0
gateway 192.200.32.1
```

#### Alabasta

```bash
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.200.32.2
netmask 255.255.254.0
gateway 192.200.32.1

auto eth1
iface eth1 inet static
address 192.200.34.1
netmask 255.255.255.240
```

#### Jorge

```bash
auto eth0
iface eth0 inet static
address 192.200.34.2
netmask 255.255.255.240
gateway 192.200.34.1
```

#### Oimo

```bash
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.200.16.2
netmask 255.255.255.252
gateway 192.200.16.1

auto eth1
iface eth1 inet static
address 192.200.8.1
netmask 255.255.255.252

auto eth2
iface eth2 inet static
address 192.200.4.1
netmask 255.255.255.0
```

#### EniesLobby

```bash
auto eth0
iface eth0 inet static
address 192.200.4.3
netmask 255.255.255.0
gateway 192.200.4.1
```

#### Seastone

```bash
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.200.4.2
netmask 255.255.255.0
gateway 192.200.4.1

auto eth1
iface eth1 inet static
address 192.200.0.1
netmask 255.255.252.0
```

#### Elena

```bash
auto eth0
iface eth0 inet static
address 192.200.0.2
netmask 255.255.252.0
gateway 192.200.0.1
```

### Routing

Routing yang dilakukan di GNS sama persis dengan di CPT, hanya saja syntax dan IPnya berbeda.

#### Pucci

```bash
route add -net 0.0.0.0 netmask 0.0.0.0 gw 192.201.16.2
```

#### Water7

```bash
route add -net 0.0.0.0 netmask 0.0.0.0 gw 192.201.64.2
route add -net 192.201.8.0 netmask 255.255.255.128 gw 192.201.16.1
route add -net 192.201.0.0 netmask 255.255.248.0 gw 192.201.16.1
route add -net 192.201.16.0 netmask 255.255.255.252 gw 192.201.16.1
```

#### Seastone

```bash
route add -net 0.0.0.0 netmask 0.0.0.0 gw 192.200.4.1
```

#### Oimo

```bash
route add -net 0.0.0.0 netmask 0.0.0.0 gw 192.200.16.1
route add -net 192.200.0.0 netmask 255.255.252.0 gw 192.200.4.2
```

#### Alabasta

```bash
route add -net 0.0.0.0 netmask 0.0.0.0 gw 192.200.32.1
```

#### Guanhao

```bash
route add -net 0.0.0.0 netmask 0.0.0.0 gw 192.200.64.1
route add -net 192.200.4.0 netmask 255.255.255.0 gw 192.200.16.2
route add -net 192.200.0.0 netmask 255.255.252.0 gw 192.200.16.2
route add -net 192.200.8.0 netmask 255.255.255.252 gw 192.200.16.2
route add -net 192.200.34.0 netmask 255.255.255.240 gw 192.200.32.2
# oimo-guan subnet
route add -net 192.200.16.0 netmask 255.255.255.252 gw 192.200.32.2
# doriki
route add -net 192.200.128.0 netmask 255.255.255.252 gw 192.200.64.1
```

#### Foosha

```bash
# bawah
route add -net 192.200.4.0 netmask 255.255.255.0 gw 192.200.64.2
route add -net 192.200.0.0 netmask 255.255.252.0 gw 192.200.64.2
route add -net 192.200.8.0 netmask 255.255.255.252 gw 192.200.64.2
route add -net 192.200.36.0 netmask 255.255.252.0 gw 192.200.64.2
route add -net 192.200.32.0 netmask 255.255.254.0 gw 192.200.64.2
route add -net 192.200.34.0 netmask 255.255.255.240 gw 192.200.64.2
route add -net 192.200.16.0 netmask 255.255.255.252 gw 192.200.64.2

# kiri
route add -net 192.201.8.0 netmask 255.255.255.128 gw 192.201.64.1
route add -net 192.201.0.0 netmask 255.255.248.0 gw 192.201.64.1
route add -net 192.201.32.0 netmask 255.255.252.0 gw 192.201.64.1
route add -net 192.201.16.0 netmask 255.255.255.252 gw 192.201.64.1
```



### Kendala Pengerjaan

1. Pada awalnya masih bingung dengan aturan dan arah penggabungan subnet pada CIDR.
2. Pada GNS sempat ada yang salah menurunkan dan lumayan sulit untuk dideteksi jadi cukup memakan waktu
