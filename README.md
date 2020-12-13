# Jarkom_Modul4_Lapres_B12

1. 05111840000057 - Maisie Chiara Salsabila
2. 05111840000062 - Geizka Wahyu Fahriza

![testestes](https://github.com/messyme/Jarkom_Modul4_Lapres_B12/blob/main/Praktikum%204/Soal%20Shift%20Modul%204.png)

### [VLSM (Variable Length Subnet Masking) - CPT](#vlsm)
### [CIDR (Classless Inter Domain Routing) - UML](#cidr)
<br><br><br><br>

<a name="vlsm"></a>
## VLSM (Variable Length Subnet Masking) - CPT
#### 1. Pembagian subnet:<br>
  ![testestes](https://github.com/messyme/Jarkom_Modul4_Lapres_B12/blob/main/Praktikum%204/Pembagian%20Subnet%20VLSM.png)
  ![testestes](https://github.com/messyme/Jarkom_Modul4_Lapres_B12/blob/main/Praktikum%204/Netmask%20VLSM.jpg)
<br><br>
#### 2. Tree pembagian IP:<br>
  ![testestes](https://github.com/messyme/Jarkom_Modul4_Lapres_B12/blob/main/Praktikum%204/IP%20Tree.jpg)
  ![testestes](https://github.com/messyme/Jarkom_Modul4_Lapres_B12/blob/main/Praktikum%204/IP%20Tree%20VLSM.jpg)
  ![testestes](https://github.com/messyme/Jarkom_Modul4_Lapres_B12/blob/main/Praktikum%204/vlsm-1.jpg)
  ![testestes](https://github.com/messyme/Jarkom_Modul4_Lapres_B12/blob/main/Praktikum%204/vlsm-2.jpg)
<br><br><br><br>

<a name="cidr"></a>
## CIDR (Classless Inter Domain Routing) - UML
#### 1. Pembagian subnet:<br>
  ![testestes](https://github.com/messyme/Jarkom_Modul4_Lapres_B12/blob/main/Praktikum%204/Pembagian%20Subnet%20CIDR%20-%201.png)
  ![testestes](https://github.com/messyme/Jarkom_Modul4_Lapres_B12/blob/main/Praktikum%204/Pembagian%20Subnet%20CIDR%20-%202.png)
  ![testestes](https://github.com/messyme/Jarkom_Modul4_Lapres_B12/blob/main/Praktikum%204/Pembagian%20Subnet%20CIDR%20-%203.png)
  ![testestes](https://github.com/messyme/Jarkom_Modul4_Lapres_B12/blob/main/Praktikum%204/Pembagian%20Subnet%20CIDR%20-%204.png)
  ![testestes](https://github.com/messyme/Jarkom_Modul4_Lapres_B12/blob/main/Praktikum%204/Pembagian%20Subnet%20CIDR%20-%205.png)
  ![testestes](https://github.com/messyme/Jarkom_Modul4_Lapres_B12/blob/main/Praktikum%204/Pembagian%20Subnet%20CIDR%20-%206.png)
<br><br>

#### 2. Tree pembagian IP:<br>
  ![testestes](https://github.com/messyme/Jarkom_Modul4_Lapres_B12/blob/main/Praktikum%204/IP%20Tree%20CIDR.png)
  ![testestes](https://github.com/messyme/Jarkom_Modul4_Lapres_B12/blob/main/Praktikum%204/IP%20Tree%20CIDR%202.png)
<br><br>

#### 3. Membuat file ```topologi.sh```
  ```
  # Switch
  uml_switch -unix switch1 > /dev/null < /dev/null &
  uml_switch -unix switch2 > /dev/null < /dev/null &
  uml_switch -unix switch3 > /dev/null < /dev/null &
  uml_switch -unix switch4 > /dev/null < /dev/null &
  uml_switch -unix switch5 > /dev/null < /dev/null &
  uml_switch -unix switch6 > /dev/null < /dev/null &
  uml_switch -unix switch7 > /dev/null < /dev/null &
  uml_switch -unix switch8 > /dev/null < /dev/null &
  uml_switch -unix switch9 > /dev/null < /dev/null &
  uml_switch -unix switch10 > /dev/null < /dev/null &
  uml_switch -unix switch11 > /dev/null < /dev/null &
  uml_switch -unix switch12 > /dev/null < /dev/null &
  uml_switch -unix switch13 > /dev/null < /dev/null &
  uml_switch -unix switch14 > /dev/null < /dev/null &
  uml_switch -unix switch15 > /dev/null < /dev/null &

  # Router
  xterm -T SURABAYA -e linux ubd0=SURABAYA,jarkom umid=SURABAYA eth0=tuntap,,,10.151.74.53 eth1=daemon,,,switch14 eth2=daemon,,,switch8 eth3=daemon,,,switch9 eth4=daemon,,,switch7 mem=64M &
  xterm -T PASURUAN -e linux ubd0=PASURUAN,jarkom umid=PASURUAN eth0=daemon,,,switch9 eth1=daemon,,,switch12 eth2=daemon,,,switch10 mem=64M &
  xterm -T PROBOLINGGO -e linux ubd0=PROBOLINGGO,jarkom umid=PROBOLINGGO eth0=daemon,,,switch10 eth1=daemon,,,switch13 eth2=daemon,,,switch11 mem=64M &
  xterm -T BATU -e linux ubd0=BATU,jarkom umid=BATU eth0=daemon,,,switch7 eth1=daemon,,,switch2 eth2=daemon,,,switch3 eth3=daemon,,,switch6 mem=64M &
  xterm -T MADIUN -e linux ubd0=MADIUN,jarkom umid=MADIUN eth0=daemon,,,switch2 eth1=daemon,,,switch1 mem=64M &
  xterm -T KEDIRI -e linux ubd0=KEDIRI,jarkom umid=KEDIRI eth0=daemon,,,switch6 eth1=daemon,,,switch15 eth2=daemon,,,switch5 mem=64M &
  xterm -T BLITAR -e linux ubd0=BLITAR,jarkom umid=BLITAR eth0=daemon,,,switch5 eth1=daemon,,,switch4 mem=64M &

  # Server
  xterm -T MALANG -e linux ubd0=MALANG,jarkom umid=MALANG eth0=daemon,,,switch15 mem=64M &
  xterm -T MOJOKERTO -e linux ubd0=MOJOKERTO,jarkom umid=MOJOKERTO eth0=daemon,,,switch14 mem=64M &

  # Klien
  xterm -T SAMPANG -e linux ubd0=SAMPANG,jarkom umid=SAMPANG eth0=daemon,,,switch8 mem=64M &
  xterm -T BONDOWOSO -e linux ubd0=BONDOWOSO,jarkom umid=BONDOWOSO eth0=daemon,,,switch11 mem=64M &
  xterm -T JEMBER -e linux ubd0=JEMBER,jarkom umid=JEMBER eth0=daemon,,,switch13 mem=64M &
  xterm -T BANYUWANGI -e linux ubd0=BANYUWANGI,jarkom umid=BANYUWANGI eth0=daemon,,,switch13 mem=64M &
  xterm -T SIDOARJO -e linux ubd0=SIDOARJO,jarkom umid=SIDOARJO eth0=daemon,,,switch12 mem=64M &
  xterm -T JOMBANG -e linux ubd0=JOMBANG,jarkom umid=JOMBANG eth0=daemon,,,switch2 mem=64M &
  xterm -T BOJONEGORO -e linux ubd0=BOJONEGORO,jarkom umid=BOJONEGORO eth0=daemon,,,switch1 mem=64M &
  xterm -T NGANJUK -e linux ubd0=NGANJUK,jarkom umid=NGANJUK eth0=daemon,,,switch3 mem=64M &
  xterm -T LUMAJANG -e linux ubd0=LUMAJANG,jarkom umid=LUMAJANG eth0=daemon,,,switch5 mem=64M &
  xterm -T TULUNGAGUNG -e linux ubd0=TULUNGAGUNG,jarkom umid=TULUNGAGUNG eth0=daemon,,,switch4 mem=64M &
  ```
  <br><br>
  
#### 4. Pada UML, setting interface pada setiap UML dengan menjalankan perintah ```nano /etc/network/interfaces``` kemudian gunakan perintah ```service networking restart``` untuk merestart network. Untuk UML yang merupakan router, juga harus di-uncomment pada perintah ```net.ipv4.ip_forward=1``` agar dapat meneruskan route nantinya. Hal ini dilakukan dengan cara mengedit pada ```nano /etc/sysctl.conf```, dan untuk mengaktifkan perubahan baru, gunakan ```sysctl -p```. Berikut setting file ```/etc/network/interfaces``` untuk setiap UML:
  **SURABAYA**
  ```
  auto eth0
  iface eth0 inet static
  address 10.151.74.54
  netmask 255.255.255.252
  gateway 10.151.74.53

  auto eth1
  iface eth1 inet static
  address 10.151.83.105
  netmask 255.255.255.252

  auto eth2
  iface eth2 inet static
  address 192.168.192.1
  netmask 255.255.252.0

  auto eth3
  iface eth3 inet static
  address 192.168.160.1
  netmask 255.255.255.252

  auto eth4
  iface eth4 inet static
  address 192.168.64.1
  netmask 255.255.255.252
  ```
  **PASURUAN**
  ```
  auto eth0
  iface eth0 inet static
  address 192.168.160.2
  netmask 255.255.255.252
  gateway 192.168.160.1

  auto eth1
  iface eth1 inet static
  address 192.168.32.1
  netmask 255.255.252.0

  auto eth2
  iface eth2 inet static
  address 192.168.16.1
  netmask 255.255.255.252
  ```
  **MOJOKERTO**
  ```
  auto eth0
  iface eth0 inet static
  address 10.151.83.106
  netmask 255.255.255.252
  gateway 10.151.83.105
  ```
  **SAMPANG**
  ```
  auto eth0
  iface eth0 inet static
  address 192.168.192.2
  netmask 255.255.252.0
  gateway 192.168.192.1
  ```
  **PROBOLINGGO**
  ```
  auto eth0
  iface eth0 inet static
  address 192.168.16.2
  netmask 255.255.255.252
  gateway 192.168.16.1

  auto eth1
  iface eth1 inet static
  address 192.168.0.1
  netmask 255.255.248.0

  auto eth2
  iface eth2 inet static
  address 192.168.8.1
  netmask 255.255.255.128
  ```
  **SIDOARJO**
  ```
  auto eth0
  iface eth0 inet static
  address 192.168.32.2
  netmask 255.255.252.0
  gateway 192.168.32.1
  ```
  **BANYUWANGI**
  ```
  auto eth0
  iface eth0 inet static
  address 192.168.0.2
  netmask 255.255.248.0
  gateway 192.168.0.1
  ```
  **JEMBER**
  ```
  auto eth0
  iface eth0 inet static
  address 192.168.3.234
  netmask 192.168.0.1
  gateway 255.255.248.0
  ```
  **BONDOWOSO**
  ```
  auto eth0
  iface eth0 inet static
  address 192.168.8.2
  netmask 255.255.255.128
  gateway 192.168.8.1
  ```
  **BATU**
  ```
  auto eth0
  iface eth0 inet static
  address 192.168.64.2
  netmask 255.255.255.252
  gateway 192.168.64.1

  auto eth1
  iface eth1 inet static
  address 192.168.144.1
  netmask 255.255.254.0

  auto eth2
  iface eth2 inet static
  address 192.168.148.1
  netmask 255.255.252.0

  auto eth3
  iface eth3 inet static
  address 192.168.136.1
  netmask 255.255.255.252
  ```
  **KEDIRI**
  ```
  auto eth0
  iface eth0 inet static
  address 192.168.136.2
  netmask 255.255.255.252
  gateway 192.168.136.1

  auto eth1
  iface eth1 inet static
  address 10.151.83.109
  netmask 255.255.255.252

  auto eth2
  iface eth2 inet static
  address 192.168.132.1
  netmask 255.255.255.0
  ```
  **JOMBANG**
  ```
  auto eth0
  iface eth0 inet static
  address 192.168.144.3
  netmask 255.255.254.0
  gateway 192.168.144.1
  ```
  **MADIUN**
  ```
  auto eth0
  iface eth0 inet static
  address 192.168.144.2
  netmask 255.255.254.0
  gateway 192.168.144.1

  auto eth1
  iface eth1 inet static
  address 192.168.146.1
  netmask 255.255.255.240
  ```
  **BOJONEGORO**
  ```
  auto eth0
  iface eth0 inet static
  address 192.168.146.2
  netmask 255.255.255.240
  gateway 192.168.146.1
  ```
  **NGANJUK**
  ```
  auto eth0
  iface eth0 inet static
  address 192.168.148.2
  netmask 255.255.252
  gateway 192.168.148.1
  ```
  **MALANG**
  ```
  auto eth0
  iface eth0 inet static
  address 10.151.83.110
  netmask 255.255.255.252
  gateway 10.151.83.109
  ```
  **BLITAR**
  ```
  auto eth0
  iface eth0 inet static
  address 192.168.132.2
  netmask 255.255.255.0
  gateway 192.168.132.1

  auto eth1
  iface eth1 inet static
  address 192.168.128.1
  netmask 255.255.252.0
  ```
  **LUMAJANG**
  ```
  auto eth0
  iface eth0 inet static
  address 192.168.132.3
  netmask 255.255.255.0
  gateway 192.168.132.1
  ```
  
  Pada **SURABAYA** gunakan perintah ```iptables –t nat –A POSTROUTING –o eth0 –j MASQUERADE –s 192.168.0.0/16``` agar UML dapat mengakses internet.
 <br><br>
 
#### 5. Pada router tambahkan route baru. Gunakan ```nano route.sh``` pada setiap UML router agar ketika UML direstart route tidak akan hilang.
  **SURABAYA**
  ```
  route add -net 192.168.128.0 netmask 255.255.192.0 gw 192.168.64.2
  route add -net 192.168.0.0 netmask 255.255.128.0 gw 192.168.160.2
  ```
  **PASURUAN**
  ```
  route add -net 192.168.0.0 netmask 255.255.224.0 gw 10.168.16.2
  ```
  **BATU**
  ```
  route add -net 192.168.144.0 netmask 255.255.252.0 gw 192.168.144.2
  route add -net 192.168.128.0 netmask 255.255.240.0 gw 192.168.136.2
  ```
  **KEDIRI**
  ```
  route add -net 192.168.128.0 netmask 255.255.252.0 gw 192.168.132.2
  ```
<br><br>

#### 6. Jalankan perintah ```source route.sh``` untuk menjalankan ```route.sh```
