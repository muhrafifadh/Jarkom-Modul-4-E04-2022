# Jarkom-Modul-3-E04-2022
Laporan Resmi Praktikum Jarkom Modul 4 untuk kelompok E04.

# Anggota Kelompok
Anggota  | NRP
---------|-------
Muhammad Afif Dwi Ardiansyah | 5025201212
Muhammad Rafif Fadhil Naufal | 5025201273
M Labib Alfaraby | 5025201083
### List

## Pembagian Subnet

<img width="482" alt="Frame 2" src="https://user-images.githubusercontent.com/81162174/204088760-c77f0962-92bd-4731-8d5f-2656760bfbe0.png">


## VLSM(Variable Length Subnet Masking)

Menentukan jumlah alamat IP yang dibutuhkan oleh tiap subnet dan  melabel netmask berdasarkan jumlah IP yang dibutuhkan.

| Subnet | Alias | Jumlah IP  | Netmask |
| --- | --- | --- | --- |
| A1 | Guideau - The Minister | 1001 | /22 |
| A2 | The Minister - The Order | 2 | /21 |
| A3 | The Minister - The Dauntless | 2 | /30 |
| A4 | The Dauntless - Phamora - Johan | 251 | /22 |
| A5 | The Order - Ashaf | 51 | /22 |
| A6 | The Order - The Resonance | 2 | /30 |
| A7 | Matt Cougat - The Instrument | 121 | /30 |
| A8 | Keith - The Firefist - The Queen | 212 | /22 |
| A9 | The Resonance - The Magical | 2 | /23 |
| A10 | The Resonance - The Instrument | 2 | /28 |
| A11 | The Instrument - The Profound | 2 | /30 |
| A12 | The Instrument - The Firefist | 2 | /24 |
| A13 | The Firefist - Oakleaf | 5011 | /22 |
| A14 | The Magical - Haines - Corvekt | 271 | /30 |
| A15 | The Profound - Spendrow | 121 | /30 |
| A16 | The Profound - Heiga | 25 | /30 |
| A17 | The Resonance - Beast | 2 | /30 |
| A18 | The Profound - Spendrow | 2 | /30 |
| Total |  | 2618 | /20 |

### Pohon IP

Subnet besar yang dibentuk memiliki NID 192.194.0.0 dengan netmask /20 sehingga pembagian IP berdasarkan NID dan netmask dihitung sesuai dengan pohon berikut.

<img width="1698" alt="Frame 1" src="https://user-images.githubusercontent.com/81162174/204088675-af3e6f5d-f14b-4886-9bd9-319875d19e81.png">


Pada VLSM ini diturunkan sesuai dengan length atasnya sehingga ketika /20 akan diturunkan menjadi /21, dan pembagian IPnya mengikuti tabel. Kemudian jika ada subnet yang bisa diassign, maka kita langsung mengassign. Hal ini dilakukan berulang" sampai semua subnet selesai di assign.

### Subnet + IP

Selanjutnya menyesuaikan pembagian IP sesuai dengan subnet yang telah dibagi berdasarkan pohon diatas pada topologi. Setelah itu akan didapatkan pembagian IP untuk tiap nodenya.

### Hasil Pembagian IP per node

![save 1](https://user-images.githubusercontent.com/81162174/204089843-3f46a602-1c71-44d0-af61-e19cdbf667c4.png)
![save2](https://user-images.githubusercontent.com/81162174/204089849-cafe4017-024c-47b6-8573-751d20568f87.png)
![save 3](https://user-images.githubusercontent.com/81162174/204089851-08bc91d4-b2b8-44e1-8f6a-d8be13fcb6bb.png)

### Assignment pada CPT


Contoh pada The Minister di router, kita menambahkan IP dan Subnet Mask sesuai dengan pembagian yang telah dilakukan, dengan IP ditambah 1 dari subnetnya. Hal ini diassign untuk semua router, client dan server.
![image](https://user-images.githubusercontent.com/96496752/204092701-e92d658e-25f5-4c87-bfba-b43b419bf4ce.png)

Contoh pada Guideau di Host / client

![image](https://user-images.githubusercontent.com/96496752/204092749-02a65e2c-d51e-4a5b-8dd0-ca7441c60198.png)

Pada server & Client ditambahkan juga gateway yang mengarah ke router terdekat.

![image](https://user-images.githubusercontent.com/55318172/143670107-2f9e5fff-ea11-4712-9006-abdbd4e99d52.png)


### Menambah Ethernet

Karena default hanya memiliki 2 port ethernet, maka kita bisa menambah port pada tab physical

![image](https://user-images.githubusercontent.com/96496752/204092805-856c3305-db48-473f-8eb4-37f24b2dec84.png)

Contoh pada foosha kami menambah 3 port lagi karena butuh terkoneksi 5 cabang

### Routing

Pada routing berikut adalah config" yang berada pada router.

#### The Minister

![image](https://user-images.githubusercontent.com/96496752/204092907-0c0547dc-c7de-42a6-9061-78590d1ceef6.png)

0.0.0.0 berarti mengambil semua pesan dan diarahkan ke next hop di tambah ke subnet A4

#### The Dauntless

![image](https://user-images.githubusercontent.com/96496752/204092967-3eafea58-9a04-4834-8f0f-e2094970baaf.png)

0.0.0.0 berarti mengambil semua pesan dan diarahkan ke next hop

#### The Order

![image](https://user-images.githubusercontent.com/96496752/204093017-81c10921-f20e-4bd9-9ea1-85a7e3392ace.png)

routing 0.0.0.0 melalui The resonance dan routing ke setiap subnet sebelumnya, A1, A3, A4

#### The Resonance

![image](https://user-images.githubusercontent.com/96496752/204093055-88ed0195-1d1a-4911-96a8-701877e4eff3.png)

routing 0.0.0.0 melalui The Order dan routing ke setiap subnet sebelumnya, A14, A7, A11, A15, A16, A12, A8, A18, A13

#### The Instrument

![image](https://user-images.githubusercontent.com/96496752/204093135-3bef98af-177c-4405-be26-a2b6c07b1e0d.png)

routing 0.0.0.0 melalui The Resonance dan routing ke setiap subnet sebelumnya,  A11, A15, A16, A12, A8, A18, A13

#### The Magical
![image](https://user-images.githubusercontent.com/96496752/204093159-31aaa627-06d8-41d0-9b47-accf7be25644.png)

routing 0.0.0.0 melalui The Resonance 

#### The Profound

![image](https://user-images.githubusercontent.com/96496752/204093290-fdad629e-0476-419c-8dfc-e6631da47edb.png)

routing 0.0.0.0 melalui The Instrument

#### The Firefist

![image](https://user-images.githubusercontent.com/96496752/204093200-7961cca3-79c1-45fb-9ae2-f8ab4967ed29.png)

routing 0.0.0.0 melalui The Instrumetn dan routing setiap subnet sebelumnya, A18

#### The Queen

![image](https://user-images.githubusercontent.com/96496752/204093307-37b8cc02-dd6b-4d9a-a63a-7c6f6da28d11.png)

routing 0.0.0.0 melalui The Firefist

### VLSM Routing Check 

https://user-images.githubusercontent.com/96496752/204093598-687bd9a0-a772-49a1-a45b-91b10052d708.mp4

## CIDR

Menggabungkan subnet-subnet paling bawah dalam topologi yaitu dimulai dari subnet yang paling jauh dari internet(gambar awan).

#### Kondisi Awal

![CIDR-Tree-Halaman-1 drawio](https://user-images.githubusercontent.com/81162174/204090109-686efae8-f8e2-49d6-81c5-760edf28948a.png)


#### Gabungan Pertama(Subnet)
![CIDR-Tree-Salinan Halaman-1 drawio](https://user-images.githubusercontent.com/81162174/204090371-93ee0258-de20-4b3f-837b-896b63565131.png)
![CIDR-Tree-Salinan Salinan Halaman-1 drawio](https://user-images.githubusercontent.com/81162174/204090384-9bab1e50-cd82-4cbe-9540-53886cbe0779.png)
![CIDR-Tree-Salinan Salinan Salinan Halaman-1 drawio](https://user-images.githubusercontent.com/81162174/204090413-854151ca-59f3-4f84-a2bf-c27a121298e2.png)
![image](https://user-images.githubusercontent.com/87472849/204093914-49f46849-a5e1-4ee4-9677-0e6e17884143.png)
![CIDR-Tree-Salinan Salinan Salinan Salinan Halaman-1 drawio](https://user-images.githubusercontent.com/81162174/204090429-dfb979b3-42db-4ffb-b0a7-cedc4547b058.png)
![CIDR-Tree-Salinan Salinan Salinan Salinan Salinan Halaman-1 drawio (1)](https://user-images.githubusercontent.com/81162174/204090447-1e25c018-6d5c-4c80-9d62-964634f7b4ec.png)

### Pohon IP

Dari penggabungan yang telah dilakukan, didapatkan pohon pembagian IP sebagai berikut.

![CIDR-Tree drawio](https://user-images.githubusercontent.com/81162174/204090551-0bea5790-92aa-41b6-8f3e-b6e7de730613.png)

<a href="https://drive.google.com/file/d/1uCfcb8_hHL_zB6cdXFmk0VOu0aGSAN9n/view?usp=share_link">Link gambar pohon CIDR</a>

# Tabel Pembagian IP

Maka didapatkan hasil pembagian IP sesuai pada tabel berikut.

| Subnet |  IP | Subnet Mask | Length |
| --- | --- | --- | --- |
| A1 | 192.194.66.0 | 255.255.252.0 |192.194.19.255 | 22 |
| A2 | 192.194.72.0 | 255.255.255.252 | 192.194.0.3 | 30 |
| A3 | 192.194.65.0 | 255.255.255.252 | 192.194.0.7 | 30 |
| A4 | 192.194.64.0 | 255.255.255.0 | 192.194.2.255 | 24 |
| A5 | 192.194.80.0 | 255.255.255.192 | 192.194.0.127 || 26 |
| A6 | 192.194.32.0 | 255.255.255.252 | 192.194.0.11 | 30 |
| A7 | 192.194.10.0 | 255.255.255.128 | 192.194.1.127 | 25 |
| A8 | 192.194.0.0 | 255.255.255.0 | 192.194.3.255 | 24 |
| A9 | 192.194.18.0 | 255.255.255.252 | 192.194.0.15 | 30 |
| A10 | 192.194.24.0 | 255.255.255.252 | 192.194.0.19 | 30 |
| A11 | 192.194.9.0 | 255.255.255.252 | 192.194.0.23 | 30 |
| A12 | 192.194.4.0 | 255.255.255.252 | 192.194.0.27 | 30 |
| A13 | 192.194.2.0 | 255.255.254.0 | 192.194.5.255 | 23 |
| A14 | 192.194.16.0 | 255.255.254.0 | 192.194.9.255 | 23 |
| A15 | 192.194.8.0 | 255.255.255.128 | 192.194.1.255 | 25 |
| A16 | 192.194.0.128 | 255.255.255.128 | 192.194.0.255 | 25 |
| A17 | 192.194.16.0 | 255.255.254.0 | 192.194.0.255 | 30 |
| A18 | 192.194.1.0 | 255.255.254.0 | 192.194.0.255 | 30 |

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
