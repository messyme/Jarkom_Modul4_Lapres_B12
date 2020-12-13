# Jarkom_Modul4_Lapres_B12

1. 05111840000057 - Maisie Chiara Salsabila
2. 05111840000062 - Geizka Wahyu Fahriza

![testestes](/Praktikum 4/Soal Shift Modul 4.jpg)

## VLSM (Variable Length Subnet Masking) - CPT
1. Pembagian subnet:<br>
  ![testestes](/Praktikum 4/Pembagian Subnet VLSM.jpg)
  ![testestes](/Praktikum 4/Netmask VLSM.jpg)

2. Tree pembagian IP:<br>
  ![testestes](/Praktikum 4/IP Tree.jpg)
  ![testestes](/Praktikum 4/IP Tree VLSM.jpg)
  ![testestes](/Praktikum 4/vlsm-1.jpg)
  ![testestes](/Praktikum 4/vlsm-2.jpg)
<br><br><br>

## CIDR (Classless Inter Domain Routing) - UML
1. Pembagian subnet:<br>
  ![testestes](/Praktikum 4/Pembagian Subnet CIDR - 1.jpg)
  ![testestes](/Praktikum 4/Pembagian Subnet CIDR - 2.jpg)
  ![testestes](/Praktikum 4/Pembagian Subnet CIDR - 3.jpg)
  ![testestes](/Praktikum 4/Pembagian Subnet CIDR - 4.jpg)
  ![testestes](/Praktikum 4/Pembagian Subnet CIDR - 5.jpg)
  ![testestes](/Praktikum 4/Pembagian Subnet CIDR - 6.jpg)

2. Tree pembagian IP:<br>
  ![testestes](/Praktikum 4/IP Tree CIDR.jpg)
  ![testestes](/Praktikum 4/IP Tree CIDR 2.jpg)

3. Membuat file ```topologi.sh```
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
  
4. Pada UML, setting interface pada setiap UML dengan menjalankan perintah ```nano /etc/network/interfaces``` kemudian gunakan perintah ```service networking restart``` untuk merestart network. Untuk UML yang merupakan router, juga harus di-uncomment pada perintah ```net.ipv4.ip_forward=1``` agar dapat meneruskan route nantinya. Hal ini dilakukan dengan cara mengedit pada ```nano /etc/sysctl.conf```, dan untuk mengaktifkan perubahan baru, gunakan ```sysctl -p```. Berikut setting file ```/etc/network/interfaces``` untuk setiap UML:
  **SURABAYA**
  ```
  
  ```
  **PASURUAN**
  ```
  
  ```
  **MOJOKERTO**
  ```
  
  ```
  **SAMPANG**
  ```
  
  ```
  **PROBOLINGGO**
  ```
  
  ```
  **SIDOARJO**
  ```
  
  ```
  **BANYUWANGI**
  ```
  
  ```
  **JEMBER**
  ```
  
  ```
  **BONDOWOSO**
  ```
  
  ```
  **BATU**
  ```
  
  ```
  **KEDIRI**
  ```
  
  ```
  **JOMBANG**
  ```
  
  ```
  **MADIUN**
  ```
  
  ```
  **BOJONEGORO**
  ```
  
  ```
  **NGANJUK**
  ```
  
  ```
  **MALANG**
  ```
  
  ```
  **BLITAR**
  ```
  
  ```
  **LUMAJANG**
  ```
  
  ```
  **TULUNGAGUNG**
  ```
  
  ```
