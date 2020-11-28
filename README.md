# Jarkom_Modul3_Lapres_D08
#### Soal 1
Untuk membuat topologi, maka dibuat file topo.sh di UML utama dengan konfigurasi berikut:

![alt text](images/1.png)
## DHCP
#### Soal 2
Untuk membuat UML SURABAYA sebagai relay, maka perlu diinstall isc-dhcp-relay, dengan perintah:
> apt-get install isc-dhcp-relay

Setelah selesai install, dilakukan konfigurasi di /etc/default/isc-dhcp-relay.
Target server diatur menjadi server TUBAN, dan interface yang ditambahkan adalah semua interface yang menghubungken subnet2 ke SURABAYA, yaitu eth1, eth2, dan eth3:

![alt text](images/2-1.png)

Setelah dilakukan setup, operasi dipindah ke server TUBAN. Dimulai dengan menginstall isc-dhcp-server, dengan perintah:
> apt-get install isc-dhcp-server

Setelah selesai install, dilakukan konfigurasi di /etc/default/isc-dhcp-server.
Interfaces diisi interface yang menghubungkan subnet tempat TUBAN dan relay SURABAYA.

![alt text](images/2-2.png)

Setelah dilakukan setup, dilakukan konfigurasi di /etc/dhcp/dhcpd.conf
Dlm file, ditambah subnet tempat TUBAN berada. Tidak perlu mengisi apapun.

![alt text](images/2-3.png)
#### Soal 3
![alt text](images/3-1.png)
![alt text](images/3-2.png)
#### Soal 4
![alt text](images/4-1.png)
![alt text](images/4-2.png)
#### Soal 5
![alt text](images/5-1.png)
![alt text](images/5-2.png)
![alt text](images/5-3.png)
![alt text](images/5-4.png)
#### Soal 6
![alt text](images/6-1.png)
![alt text](images/6-2.png)
![alt text](images/6-3.png)
![alt text](images/6-4.png)
## Proxy Server
#### Soal 7
#### Soal 8
#### Soal 9
#### Soal 10
#### Soal 11
#### Soal 12
