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
### soal 8.  
kueri filter sehingga wireshark hanya mengambil semua protokol paket yang menuju port 80 adalah dengan kueri
```
tcp.dstport == 80 || udp.dstport == 80
```
berikut gambar dari pengerjaan soal
![image](https://github.com/aptarr/Jarkom-Modul-1-F05-2023/assets/114988957/54beb07e-4c65-4162-8fd5-f01d9e3de370)  

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






