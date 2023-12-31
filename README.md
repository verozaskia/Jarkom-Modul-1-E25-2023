# Jarkom-Modul-1-E25-2023
Berikut adalah Repository dari Kelompok E25 untuk pengerjaan Praktikum Modul 1 Jaringan Komputer. Dalam Repository ini terdapat Anggota Kelompok, Dokumentasi serta Penjelasan tiap soal, Screenshot Output, dan Kendala yang dialami.

# Anggota Kelompok
| Nama | NRP |
| --- | --- |
| Ketut Arda Putra Mahotama Sadha | 5025211235 |
| Zakia Kolbi | 5025211049 |

# Dokumentasi dan Penjelasan Soal
Berikut adalah dokumentasi yang berisi source code dari tiap soal dan penjelasan terkait perintah yang digunakan.

# SOAL NOMOR 1
User melakukan berbagai aktivitas dengan menggunakan protokol FTP. Salah satunya adalah mengunggah suatu file.
- Berapakah sequence number (raw) pada packet yang menunjukkan aktivitas tersebut? 
- Berapakah acknowledge number (raw) pada packet yang menunjukkan aktivitas tersebut? 
- Berapakah sequence number (raw) pada packet yang menunjukkan response dari aktivitas tersebut?
- Berapakah acknowledge number (raw) pada packet yang menunjukkan response dari aktivitas tersebut?

# Penyelesaian Soal Nomor 1
Kita dapat menggunakan filter `ftp.request.command == STOR`
Pada bagian Transmission Protocol Control, kita dapat melihat nilai sequence number (raw) dan juga acknowledge number (raw).

![1 cara1](https://github.com/verozaskia/Jarkom-Modul-1-E25-2023/assets/108173647/36a63aa1-91e1-4612-8341-f3dd9f84b674)

Lalu, untuk melihat response dari packet, kita dapat right-click pada baris packet, lalu memilih bagian follow lalu TCP Stream.

<img width="960" alt="1 cara2" src="https://github.com/verozaskia/Jarkom-Modul-1-E25-2023/assets/108173647/481e9112-aa93-46ea-8e2e-ef9da0b88dfe">

Pada bagian TCP Stream, kita dapat menekan command yang terdapat setelah STOR. Dengan itu, kita akan langsung terforward ke response dari STOR tersebut. Disini kita dapat mencari sequence number (raw) dan acknowledge number (raw)-nya.

<img width="960" alt="1 cara3" src="https://github.com/verozaskia/Jarkom-Modul-1-E25-2023/assets/108173647/ac23cd47-fc1f-4a72-8bef-6f5189735bbe">

![1 cara4](https://github.com/verozaskia/Jarkom-Modul-1-E25-2023/assets/108173647/287425cd-b8cb-4202-bd5f-bac5747a99cd)

Hasil :

<img width="671" alt="1 jwb" src="https://github.com/verozaskia/Jarkom-Modul-1-E25-2023/assets/108173647/8621d9a7-6245-440a-89d6-70c0cdf5c899">

# SOAL NOMOR 2
Sebutkan web server yang digunakan pada portal praktikum Jaringan Komputer!

# Penyelesaian Soal Nomor 2
Yang pertama kita lakukan adalah melakukan filter `ip.addr == 10.21.78.111`

<img width="960" alt="Screenshot_8" src="https://github.com/verozaskia/Jarkom-Modul-1-E25-2023/assets/108173647/9ea47b1a-2022-48b7-8471-4df38313b83c">

Lalu, kita dapat melakukan stream HTTP pada bagian GET.

<img width="960" alt="Screenshot_5" src="https://github.com/verozaskia/Jarkom-Modul-1-E25-2023/assets/108173647/a2c7488e-f719-4346-bde6-d8f7b3d9816e">

Setelah itu, dapat dilihat server yang digunakan adalah gunicorn.

![2 cara3](https://github.com/verozaskia/Jarkom-Modul-1-E25-2023/assets/108173647/93063113-0f57-4a7a-9592-df7e045f855e)

Hasil :

<img width="673" alt="2 jwb" src="https://github.com/verozaskia/Jarkom-Modul-1-E25-2023/assets/108173647/8d84e11f-fc1d-412f-9cab-e1b95d69fa7c">

# SOAL NOMOR 3
Dapin sedang belajar analisis jaringan. Bantulah Dapin untuk mengerjakan soal berikut:
- Berapa banyak paket yang tercapture dengan IP source maupun destination address adalah 239.255.255.250 dengan port 3702?
- Protokol layer transport apa yang digunakan?

# Penyelesaian Soal Nomor 3
Untuk menyelesaikan soal ini, kita perlu melalukan filter dengan 
`ip.addr == 239.255.255.250 && (udp.port == 3702 || tcp.port == 3702)`

![3 cara](https://github.com/verozaskia/Jarkom-Modul-1-E25-2023/assets/108173647/a9ada023-39bc-4890-8d48-c8bf887d824e)

Hasil :

<img width="672" alt="3 jwb" src="https://github.com/verozaskia/Jarkom-Modul-1-E25-2023/assets/108173647/de881f4a-a318-4881-bd58-6867f72cc4db">

# SOAL NOMOR 4
Berapa nilai checksum yang didapat dari header pada paket nomor 130?

# Penyelesaian Soal Nomor 4
Kita perlu mencari detail packet dengan nomor 130, lalu didapatkan hasil 0x18e5 dari Checksum yang terdapat pada bagian User Datagram Protocol

![4 cara](https://github.com/verozaskia/Jarkom-Modul-1-E25-2023/assets/108173647/8b871513-5ccb-4ea3-b3ac-924bc41b731d)

Hasil :

<img width="675" alt="4 jwb" src="https://github.com/verozaskia/Jarkom-Modul-1-E25-2023/assets/108173647/15701557-eb3e-472a-b328-4ed5351435c9">

# SOAL NOMOR 5
Elshe menemukan suatu file packet capture yang menarik. Bantulah Elshe untuk menganalisis file packet capture tersebut.
- Berapa banyak packet yang berhasil di capture dari file pcap tersebut?
- Port berapakah pada server yang digunakan untuk service SMTP?
- Dari semua alamat IP yang tercapture, IP berapakah yang merupakan public IP?

# Penyelesaian Soal Nomor 5
Melakukan Follow TCP Stream dan analisis seluruh conversation. Disini ditemukan text
```
I send u a p45sword of a zip file, but you should decode it in Base64.

Here is the p45sword:

NWltcGxlUGFzNXdvcmQ=
```
![image](https://github.com/verozaskia/Jarkom-Modul-1-E25-2023/assets/114855785/e2752f8f-658e-43b4-a4d7-8054b23b9bea)

Berdasarkan instruksi text tersebut, dilakukan decrypt base64

![image](https://github.com/verozaskia/Jarkom-Modul-1-E25-2023/assets/114855785/c3321b65-d9a1-46c3-986c-780da221492a)

Hasil decryptnya yaitu 5implePa5word akan digunakan untuk membuka zip yang berisi command nc untuk menjawab pertanyaan soal 5 dan juga mendapatkan flag

![image](https://github.com/verozaskia/Jarkom-Modul-1-E25-2023/assets/114855785/b9ac2843-0488-4511-9168-ae948c18873b)

### Kendala saat mengerjakan :
Menggunakan bait pada packet 14 yang berisi string base64 yang menghasilkan jawaban salah karena password yang sebenarnya bukan itu.

# SOAL NOMOR 6
Seorang anak bernama Udin Berteman dengan SlameT yang merupakan seorang penggemar film detektif. sebagai teman yang baik, Ia selalu mengajak slamet untuk bermain valoranT bersama. suatu malam, terjadi sebuah hal yang tak terdUga. ketika udin mereka membuka game tersebut, laptop udin menunjukkan sebuah field text dan Sebuah kode Invalid bertuliskan "server SOURCE ADDRESS 7812 is invalid". ketika ditelusuri di google, hasil pencarian hanya menampilkan a1 e5 u21. jiwa detektif slamet pun bergejolak. bantulah udin dan slamet untuk menemukan solusi kode error tersebut.

# Penyelesaian Soal Nomor 6
Ketika dianalisis text soal, bisa dilihat ada beberapa kata yang "berbeda" dibandingkan kata-kata lainnya. Kata-kata yang berbeda tersebut memiliki huruf kapital yang semestinya tidak ada disana. Jika semua huruf besar dari kata-kata yang berbeda tersebut digabungkan serta "SOURCE ADDRESS" pada error message, didapatkan "SUBSTITUSI SOURCE ADDRESS" dan diikuti angka 7812. Dengan informasi sebelumnya, ditemukan source address dari packet no 7812 yaitu 104.18.14.101. 

![image](https://github.com/verozaskia/Jarkom-Modul-1-E25-2023/assets/114855785/5d0160ad-ed43-4810-b881-daa0c3caac3d)

Menurut soal, hasil pencarian di google untuk error message yaitu a1 e5 u21 yang dapat ditangkap sebagai A adalah huruf pertama, E adalah huruf ke 5, dan U adalah huruf ke 21. Ketika dilakukan substitusi kepada angka-angka pada source address didapatkan JDRNJA

![image](https://github.com/verozaskia/Jarkom-Modul-1-E25-2023/assets/114855785/7a72f11a-5b63-425c-935a-48e28e10189f)

### Kendala saat pengerjaan
Kendala yang dialami selama pengerjaan soal ini yaitu bagaimana substitusi source address karena menurut kami ip address hanya memiliki 4 angka.

# SOAL NOMOR 7
Berapa jumlah packet yang menuju IP 184.87.193.88?

# Penyelesaian Soal Nomor 7
Untuk menampilkannya dapat menggunakan filter `ip.dst == 184.87.193.88`
dapat dilihat dibagian displayed ada 6 paket.

<img width="960" alt="7 cara" src="https://github.com/verozaskia/Jarkom-Modul-1-E25-2023/assets/108173647/2d532fd1-67a2-4bd9-888d-60268dcb60d9">

Hasil :

<img width="672" alt="7 jwb" src="https://github.com/verozaskia/Jarkom-Modul-1-E25-2023/assets/108173647/a71b7a9c-41e7-4f54-bfdf-a5ac545b1b37">

# SOAL NOMOR 8
Berikan kueri filter sehingga wireshark hanya mengambil semua protokol paket yang menuju port 80! (Jika terdapat lebih dari 1 port, maka urutkan sesuai dengan abjad)

# Penyelesaian Soal Nomor 8
Untuk menampilkan paket yang menuju port 80 dapat menggunakan filter 
`tcp.dstport == 80 || udp.dstport == 80`

<img width="960" alt="8 cara" src="https://github.com/verozaskia/Jarkom-Modul-1-E25-2023/assets/108173647/d36adee9-10c8-46ff-8820-7f0675005ce8">

Hasil :

<img width="960" alt="8 jwb" src="https://github.com/verozaskia/Jarkom-Modul-1-E25-2023/assets/108173647/01753df6-ed5f-4727-8e18-f559915ab735">

# SOAL NOMOR 9
Berikan kueri filter sehingga wireshark hanya mengambil paket yang berasal dari alamat 10.51.40.1 tetapi tidak menuju ke alamat 10.39.55.34!

# Penyelesaian Soal Nomor 9
Untuk menampilkannya dapat menggunakan filter `ip.src == 10.51.40.1 && ip.dst != 10.39.55.34`
<img width="960" alt="9 cara" src="https://github.com/verozaskia/Jarkom-Modul-1-E25-2023/assets/108173647/ba880068-6cb8-45e7-90ad-1953d8c56a39">

Hasil :

<img width="674" alt="9 jwb" src="https://github.com/verozaskia/Jarkom-Modul-1-E25-2023/assets/108173647/483ec636-5021-45c1-ad07-13db14655586">

### Kendala saat mengerjakan :
Meskipun menjawab dengan benar, tetapi di awal praktikum, jawaban tersebut dianggap salah.

# SOAL NOMOR 10
Sebutkan kredensial yang benar ketika user mencoba login menggunakan Telnet

# Penyelesaian Soal Nomor 10
Pertama kita dapat melakukan filter `telnet`

<img width="960" alt="10 cara1" src="https://github.com/verozaskia/Jarkom-Modul-1-E25-2023/assets/108173647/4c0d6a95-dae8-4d4a-839a-ffb6ced10a70">

lalu, dicari yang memiliki format username:password pada tcp streamnya. dari username dan
password yang ada hanya `dhafin:kesayangannyak0k0` yang memunculkan flag

<img width="960" alt="10 cara2" src="https://github.com/verozaskia/Jarkom-Modul-1-E25-2023/assets/108173647/af3b21e8-ce76-4de4-9f6b-9d1eceeb5ac0">

Hasil :

<img width="674" alt="10 jwb" src="https://github.com/verozaskia/Jarkom-Modul-1-E25-2023/assets/108173647/b283045a-40b9-41b7-b968-c960677051b7">

### Kendala saat mengerjakan :
Kami masih melakukan cara manual untuk menemukan `username:password` yaitu dengan membuka tcp stream satu persatu







