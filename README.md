 ﻿# Jarkom-Modul-1-F05-2023

### soal 1.
a & b. 
Untuk mencari aktivitas protokol FTP yang menggunggah suatu file dapatq menggunakan filter
```
ftp.request.command == "STOR"
```
kemudian akan muncul satu packet yang melakukan aktivitas tersebut.  
![no1](https://github.com/aptarr/Jarkom-Modul-1-F05-2023/assets/114988957/ac6170c2-ae1e-434d-8f9b-9466fc2c6a2a)  
sequence number raw dan acknowledge number raw dapat ditemukan dalam packet tersebut.
c & d. 
untuk mencari packet yang merespons packet sebelumnnya, biasanya response dari packet STOR pada protokol FTP memiliki code 150
bisa dicari menggunakan kueri berikut
```
fpt.response.code == 150
```
akan muncul beberapa packet, yang kami gunakan adalah packet yang paling dekat time nya dengan paket sebelumnya yaitu packet nomor 149
![no1_2](https://github.com/aptarr/Jarkom-Modul-1-F05-2023/assets/114988957/675d609f-7b60-4b52-9536-9e3ff8e28b9a)  
sequence number raw dan acknowledge number raw dapat ditemukan dalam packet tersebut.
berikut gambar dari pengerjaan soal
![image](https://github.com/aptarr/Jarkom-Modul-1-F05-2023/assets/114988957/58c32ba8-a22f-4acf-9ee9-8ee6e0af6244)

### soal 2.
Untuk mencari webserver yang digukana praktikum JARKOM adalah menggunakan command berikut di terminal
```
curl -I http://10.21.78.111:8000/
```
dimana dari command tersebut akan menampilkan header dari url yang dituju seperti berikut
![image](https://github.com/aptarr/Jarkom-Modul-1-F05-2023/assets/116022017/c1ab277e-d992-4504-a458-f3da79b99496)
sehingga dari gambar diatas webserver yang digunakan adalah gunicorn.
berikut gambar dari pengerjaan soal
![image](https://github.com/aptarr/Jarkom-Modul-1-F05-2023/assets/116022017/ad950568-aeec-4687-9170-dba88e408b89)

### soal 3.
Untuk mencari berapa banyak paket dengn IP source dan destination 239.255.255.250 dengan post 3702 adalah dengan command filter berikut:
```
(ip.src == 239.255.255.250 or ip.dst == 239.255.255.250) and udp.port == 3702
```
sehingga didapatkan paket seperti berikut, dimana lingakaran merah merupakan jumlah paket yang terpilih
![image](https://github.com/aptarr/Jarkom-Modul-1-F05-2023/assets/116022017/fc12377f-a48e-49b3-801a-875f75e68fd6)
berikut gambar dari pengerjaan soal
![image](https://github.com/aptarr/Jarkom-Modul-1-F05-2023/assets/116022017/4143ed11-e9b9-41b8-8cca-1988d18d0fca)

### soal 4.
Nilai dari checksum yang didapat dari header pada paket nomor 130.  
Di dalam packet no 130 terdapat kata kunci checksum. valuenya adalah jawabannya
![no4](https://github.com/aptarr/Jarkom-Modul-1-F05-2023/assets/114988957/d4a6f537-7dd6-46c3-b52a-8a0b9039e890)  
berikut gambar dari pengerjaan soal
![image](https://github.com/aptarr/Jarkom-Modul-1-F05-2023/assets/114988957/1f6d4906-f3c3-4399-8aee-96c646fd32b6)  

### soal 5.
Untuk mencari no 5 pertama saya mencari paket yang memiliki kata kunci zip, kemudian dapat dilihat bahwa passwordnya di enkripsi dengan base64. Untuk mendapatkan passwordnya hanya dengan didecode menggunakan base64
![no5_1](https://github.com/aptarr/Jarkom-Modul-1-F05-2023/assets/114988957/52c2072d-e552-40c1-ac8a-82453714496c)  
a. Banyak Paket yang berhasil dicapture pada file tersebut ada 60 packet sesuai packet dengan nomor terbesar.  
b. Port yang digunakan untuk service SMTP adalah 25, saat mengkueri port tersebut maka packet dengan protocol SMTP akan muncul.
c. Alamat IP yang bersifat public biasanya tidak diawali dengan 10.x.x.x, 192.168.x.x yang biasanya digunakan untuk jaringan lokal jadi IP 74.53.140.153 digunakan sebagai jawabannya
![no5_2](https://github.com/aptarr/Jarkom-Modul-1-F05-2023/assets/114988957/a477a20d-948d-4d8c-b179-9b0b398533e7)  
berikut gambar dari pengerjaan soal
![image](https://github.com/aptarr/Jarkom-Modul-1-F05-2023/assets/114988957/3b698a93-a484-424e-90ce-51e281905029) 

### soal 6.
pada soal diberikat kalimat "server SOURCE ADDRESS 7812 is invalid", dimana dari kalimat tersebut kita dapat mencari paket dengan nomor 7812. Selain itu pada kalimat tersebut terdapat kalimat source addres sehingga pada paket nomor 7812 kita perlu melihat ip.src-nya. (paket 7812 adalah paket yang dihitamkan pada gambar)
![image](https://github.com/aptarr/Jarkom-Modul-1-F05-2023/assets/116022017/7eed0d39-55b9-4a1c-ab59-600d29b5ddc2)
didapatkan IP.SRC = 104.18.14.101 kemudian terdapat hint selanjutnya yaitu a1 e5 u21 yang mana artinya a == 1, e == 5, u == 21 sehingga dapat disimpulkan bahwa setiap angka urut dapat diartikan sebagai alpabet yang urut juga, dimana jika di decrypt akan menjadi seperti ini
a b c d e f g  h  i   j  k  l  m  n  o  p  q  r
1 2 3 4 5 6 7  8  9  10 11 12 13 14 15 16 17 18 

104.18.14.101 = jdrnja
berikut gambar dari pengerjaan soal
![image](https://github.com/aptarr/Jarkom-Modul-1-F05-2023/assets/116022017/5686b6b6-5e79-4c5c-b81f-924abddbc188)

### soal 7.
untuk mencari jumlah ip yang menuju ke 184.87.193.88 adalah dengan filter berikut:
```
ip.dst == 184.87.193.88
```
![image](https://github.com/aptarr/Jarkom-Modul-1-F05-2023/assets/116022017/402953b4-3517-46de-9e34-d4cdf61083ee)
sehingga dari filter tersebut dimana lingkaran merah merupakan jumlah paket dari filter
berikut gambar dari pengerjaan soal
![image](https://github.com/aptarr/Jarkom-Modul-1-F05-2023/assets/116022017/a1c838ee-7d5c-48c5-82b9-f6295b4855ca)

### soal 8.  
kueri filter sehingga wireshark hanya mengambil semua protokol paket yang menuju port 80 adalah dengan kueri
```
tcp.dstport == 80 || udp.dstport == 80
```
berikut gambar dari pengerjaan soal
![image](https://github.com/aptarr/Jarkom-Modul-1-F05-2023/assets/114988957/54beb07e-4c65-4162-8fd5-f01d9e3de370)  

### soal 9.
untuk memfilter alamat 10.51.40.1 tetapi tidak menuju ke alamat 10.39.55.34 adalah dengan menggunakan query berikut
```
ip.src == 10.51.40.1 && ip.dst != 10.39.55.34
```
berikut gambar dari pengerjaan soal
![image](https://github.com/aptarr/Jarkom-Modul-1-F05-2023/assets/116022017/5882453b-fed4-4f07-b147-45767012daf7)

### soal 10.
Untuk mencari kredensial user yang benar ketika user  mencoba login dengan telnet adalah dengan memfilter paket paket yang menggunakan telnet.
```
telnet && tcp.port == 23
```
kemudian karena format dari pesan yang terkirim di dalam telnet adalah username:password maka kami mencoba satu persat packet yang ada dengan format teresbut.
![soal10](https://github.com/aptarr/Jarkom-Modul-1-F05-2023/assets/114988957/9544bd14-a9ea-481c-be63-b124d5c93a19)  
pada packet nomor 81 percobaan berhasil dan soal terjawab.  
berikut gambar dari pengerjaan soal
![image](https://github.com/aptarr/Jarkom-Modul-1-F05-2023/assets/114988957/a502f032-6dc6-4cd4-a9a9-6e50ee1c8aba)
