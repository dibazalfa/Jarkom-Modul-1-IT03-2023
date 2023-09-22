# Jarkom-Modul-1-IT09-2023


## Soal 1 (Addressing)

User melakukan berbagai aktivitas dengan menggunakan protokol FTP. Salah satunya adalah menggunggah suatu file. 

a. Berapakah sequence number (raw) pada packet yang menunjukkan aktivitas tersebut?
b. Berapakah acknowledge number (raw) pada packet yang menunjukkan aktivitas tersebut?
c. Berapakah sequence number (raw) pada packet yang menunjukkan response dari aktivitas tersebut?
d. Berapakah acknowledge number (raw) pada packet yang menunjukkan response dari aktivitas tersebut?

**Cara Pengerjaan**
1. Di soal dikatakan bahwa user menggunakan protokol FTP, maka lakukan filter menggunakan **ftp || ftp-data** untuk mencari data pada protokol FTP
<p align="center">
<img src="https://github.com/dibazalfa/Jarkom-Modul-1-IT09-2023/assets/103043684/fd032604-c760-4bc9-b0ca-ba518f4f0aaf"/>
</p>

3. Karena user melakukan unggah file, maka cari kata kunci STOR. STOR merupakan perintah untuk meng-upload file ke FTP server
4. Ditemukan sequence number (raw) dan acknowledge number (raw) pada aktivitas STOR (unggah file)
![Alt Text]()
5. Kemudian, pindah ke paket response di bawahnya dan ditemukan sequence number (raw) dan acknowledgement number (raw) untuk responsenya
![Alt Text]()
6. Jawab di server nc kemudian dapatkan flagnya
![Alt Text]()

Flag : `Jarkom2023{y0u_r_g00d_4t_4dr3ssing_GnDxKwH33799943}`

## Soal 2 (Stream)

Sebutkan web server yang digunakan pada portal praktikum Jaringan Komputer!

**Cara Pengerjaan**
1. Lakukan filter HTTP, kemudian cari HTTP GET
2. Klik kanan dan follow TCP Stream
![Alt Text]()
3. Setelah terbuka, cari server yang ada
![image](https://github.com/dibazalfa/Jarkom-Modul-1-IT09-2023/assets/103043684/b18e01bd-509e-4ab7-b8be-715178361949)


Flag : `Jarkom2023{9unic0rn_1s_ztceT614q46DQ3N_c00l}`

## Soal 3 (Analysis)

Dapin sedang belajar analisis jaringan. Bantulah Dapin untuk mengerjakan soal berikut:
a. Berapa banyak paket yang tercapture dengan IP source maupun destination address adalah 239.255.255.250 dengan port 3702
b. Protokol layer transport apa yang digunakan? 

**Cara Pengerjaan**
1. Gunakan filter **ip.addr == 239.255.255.250 and udp.port == 3702**
2. ip.addr digunakan untuk memeriksa paket yang memiliki alamat IP yang sama
3. udp.port digunakan untuk memeriksa paket yang memiliki port tujuan yang menggunakan protokol UDP
![Alt Text]()
4. Dengan filter sebut, cari jumlah paketnya dan ditemukan total 21 paket
5. Selain itu, protokol layer yang digunakan adalah UDP 
6. Masukkan jawaban pada server nc dan dapatkan flagnya
![Alt Text]()

Flag : `Jarkom2023{4nalyz3_is_0763_BmChDiBlCzR_gr3at}`

## Soal 4 (Addressing)

Berapa nilai checksum yang didapat dari header pada paket nomor 130?

**Cara Pengerjaan**
1. Cari paket dengan nomor 130 
2. Buka user datagram protocol
3. Cari checksums
![Alt Text]()

Flag : `Jarkom2023{ch3cksum_is_u5eful_0xgx18}`

## Soal 7 (Filtering)

Berapa jumlah packet yang menuju IP 184.87..193.88

**Cara Pengerjaan**
1. Packet difilter berdasarkan paket tujuan menggunakan **ip.dst == 184.87.193.88**. Karena **ip.dst** berfungsi untuk mencari paket yang menuju ke alamat IP 
2. Hitung jumlah paket yang ditemukan, ditemukan 6 paket 
![Alt Text]()

Flag : `Jarkom2023{LST1rHE802XchNkC76_4n0th3r_f1lt3ringb}`

## Soal 8 (Filtering)

Berikan kueri filter sehingga wireshark hanya mengambil semua protokol paket yang menuju port 80!(Jika terdapat lebih dari 1 port, maka urutkan sesuai dengan abjad)

**Cara Pengerjaan** 
1. Kueri filter yang digunakan adalah **tcp.dstport == 80 || udp.dstport == 80**
2. dst digunakan untuk memfilter paket berdasarkan alamat IP/port tujuan
3. tcp.dstport == 80 digunakan untuk mencari paket yang menggunakan protokol TCP dengan port tujuan 80
4. udp.dstport == 80 diguanakan untuk mencari paket yang menggunakan protokol UDP dengan port tujuan 80 
5. || merupakan operator OR. Jadi, di antara dua kondisi, cukup salah satu yang memenuhi atau keduanya
![Alt Text]()

Flag : `Jarkom2023{qu3ryyyyying_089399_DiQlRxPvDtD_15_fun}`

## Soal 9 (Filtering)

Berikan kueri filter sehingga wireshark hanya mengambil paket yang berasal dari alamat 10.51.40.1 tetapi tidak menuju ke alamat 10.39.55.34

**Cara Pengerjaan**
1. Buka terminal masukkan nc 10.21.78.111 7272
2. Menggunakan filter ekspresi **ip.src == 10.51.40.1 && ip.dst != 10.39.55.34** kueri filter standar yang digunakan dalam Wireshark
3. ip.src == 10.51.40.1 untuk memfilter paket ip source yang berasal dari alamat 10.51.40.1
4. ip.dst != 10.39.55.34 untuk memfilter paket yang tidak menuju ke ip destinasi 10.39.55.34

<img src="https://i.ibb.co/VJ1HQYK/image20.png"/>

Flag : `Jarkom2023{y3s_its_OjNjQgRjOkS_qu3ry1ng}`

## Soal 10 (Stream)

Sebutkan kredensial yang benar ketika user mencoba login menggunakan Telnet!

**Cara Pengerjaan**
1. Upload file pcap wireshark yang diberikan
2. Pada kolom filter tuliskan **telnet**
3. Cari setiap paket sampai ditemukan kredensial yang benar

<img src="https://i.ibb.co/2yWR3T6/image17.png"/>


<img src="https://i.ibb.co/vYvxgqF/image23.png"/>

Flag : `Jarkom2023{t3lnet_is_y5yA9ACyx89BCBy07_N0tSecu2e}`
