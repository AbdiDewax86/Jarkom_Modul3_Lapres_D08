# Jarkom_Modul3_Lapres_D08
#### Soal 1
Untuk membuat topologi, maka dibuat file topo.sh di UML utama dengan konfigurasi berikut:

![alt text](images/1.png)
## DHCP
#### Soal 2
Untuk membuat UML SURABAYA sebagai relay, maka perlu diinstall isc-dhcp-relay, dengan perintah:
``` apt-get install isc-dhcp-relay ```

Setelah selesai install, dilakukan konfigurasi di /etc/default/isc-dhcp-relay.
Target server diatur menjadi server TUBAN, dan interface yang ditambahkan adalah semua interface yang menghubungken subnet2 ke SURABAYA, yaitu eth1, eth2, dan eth3:

![alt text](images/2-1.png)

Setelah dilakukan setup, operasi dipindah ke server TUBAN. Dimulai dengan menginstall isc-dhcp-server, dengan perintah:
``` apt-get install isc-dhcp-server ```

Setelah selesai install, dilakukan konfigurasi di /etc/default/isc-dhcp-server.
Interfaces diisi interface yang menghubungkan subnet tempat TUBAN dan relay SURABAYA.

![alt text](images/2-2.png)

Setelah dilakukan setup, dilakukan konfigurasi di /etc/dhcp/dhcpd.conf
Dlm file, ditambah subnet tempat TUBAN berada. Tidak perlu mengisi apapun.

![alt text](images/2-3.png)
#### Soal 3
Untuk mengatur dhcp untuk client, maka ditambahkan subnet2 client dlm /etc/dhcp/dhcpd.conf di server TUBAN

![alt text](images/2-4.png)

Untuk mengatur range di subnet 1, maka ditambahkan argumen berikut:
``` range 192.168.0.10 192.168.0.100;
range 192.168.0.110 192.168.0.200;
```

Setelah dilakukan konfigurasi, dilakukan restart pada server TUBAN:
``` service isc-dhcp-server restart ```

Setelah restart DHCP server, maka pindah ke client2 dlm subnet 1 (SIDOARJO & GRESIK) dan ganti konfigurasi /etc/network/interfaces
Comment/Hapus iface, address, gateway, dan netmask, lalu diganti dengan line berikut:
``` iface eth0 inet dhcp ```

Setelah diganti, dilakukan perintah berikut di UML Client:
``` service networking restart ```

untuk merestart networking pada Client

Restart dilakukan sebanyak 2 kali agar terlihat perubahan pada client.
Setelah restart, dilakukan cek IP client dengan perintah ifconfig pada tiap client.

![alt text](images/3-1.png)
![alt text](images/3-2.png)
#### Soal 4
Untuk mengatur range di subnet 3, maka ditambahkan argumen berikut:
``` range 192.168.1.50 192.168.1.70; ```

DHCP server restart dilakukan setelah konfigurasi seperti biasa

Setelah restart DHCP server, maka pindah ke client2 dlm subnet 3 (MADIUN & BANYUWANGI) dan ganti konfigurasi /etc/network/interfaces sebagaimana konfigurasi yang telah dilakukan di subnet 1.
Setelah konfigurasi interface, maka dilakukan restart sebagaimana langkah yang telah dilakukan juga di subnet 1.
Lalu dilakukan pengecekan IP pula dengan perintah ifconfig.

![alt text](images/4-1.png)
![alt text](images/4-2.png)
#### Soal 5
Untuk mengatur DNS Server client, maka ditambahkan argumen berikut dlm /etc/dhcp/dhcpd.conf pada tiap subnet:
``` option domain-name-servers 10.151.79.74, 202.46.129.2; ```

DHCP server restart dilakukan setelah konfigurasi seperti biasa

Setelah restart DHCP server, langsung dilakukan networking restart dlm client.
Setelah client restart, dapat dilakukan pengecekan pada /etc/resolv.conf pada tiap client untuk melihat apakah DNS server dikenali client, dengan perintah:
``` cat /etc/resolv.conf ```

![alt text](images/5-1.png)
![alt text](images/5-2.png)
![alt text](images/5-3.png)
![alt text](images/5-4.png)
#### Soal 6
Untuk mengatur batas waktu penggunaan IP untuk setiap client, maka dilakukan perintah berikut dlm /etc/dhcp/dhcpd.conf pada tiap subnet:
- Untuk subnet 1:
``` default-lease-time 300;
max-lease-time 300;
```

- Untuk subnet 3:
``` default-lease-time 600;
max-lease-time 600;
```

Waktu berupa satuan detik.
DHCP server restart dilakukan setelah konfigurasi seperti biasa

Setelah restart DHCP server, langsung dilakukan networking restart dlm client.
Terlihat pada saat restart, client2 pada subnet 1 dan subnet 3 memiliki renewal time yang berbeda:

![alt text](images/6-1.png)
![alt text](images/6-2.png)
![alt text](images/6-3.png)
![alt text](images/6-4.png)
## Proxy Server
#### Soal 7
![alt text](images/7-1.png)
![alt text](images/7-2.png)
#### Soal 8
![alt text](images/8-1.png)
![alt text](images/8-2.png)
![alt text](images/8-3.png)
![alt text](images/8-4.png)
#### Soal 9
![alt text](images/9-1.png)
![alt text](images/9-2.png)
#### Soal 10
![alt text](images/10-1.png)
![alt text](images/10-2.png)
#### Soal 11
![alt text](images/11.png)
#### Soal 12
![alt text](images/12-1.png)
![alt text](images/12-2.png)
