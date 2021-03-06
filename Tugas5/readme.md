# **Tugas 5 PKSJ - Analisa Penetration Testing Menggunakan Metasploit dan Metasploitable**


## Pendahuluan

Tugas ini dibuat untuk menyelesaikan Tugas 5 yaitu "Analisa Penetration Testing Menggunakan Metasploit dan Metasploitable" pada matakuliah Perancangan Keamanan & Sistem Jaringan (PKSJ) Semester Ganjil 2016/2017, Teknik Informatika ITS, Surabaya.
 
Anggota Kelompok
- Ardi Nusawan      5113100096
- Gian Sebastian A. 5113100132
- Ronauli Sidabukke 5113100142


## Dasar Teori

**1. Penetration Testing**

**Penetration Testing** adalah serangan yang dilakukan secara sengaja kepada sistem dengan tujuan mencari celah keamanan dari sistem yang dapat diperbaiki atau dieksploitasi oleh penyerang. Terdapat beberapa tahapan yang dilakukan dalam penetration testing, tahapan-tahapan tersebut adalah sebagai berikut :

* **Preinteractions**
Tahap dimana seorang atau sekelompok tester menetapkan tujuan, resources, kegiatan dan aturan dari penetration test yang akan dilakukan.

* **Intelligence Gathering**
Tahap dimana seorang atau sekelompok tester berusaha mengumpulkan sebanyak mungkin informasi mengenai target yang bisa didapatkan dengan berbagai metode dan berbagai media. Hal yang perlu dijadikan dasar dalam pengumpulan informasi adalah : karakteristik sistem jaringan, cara kerja sistem jaringan, dan metode serangan yang bisa digunakan.

* **Threat Modeling**
Tahap dimana seorang atau sekelompok tester mencari celah keamanan (vulnerabilities) berdasarkan informasi yang berhasil dikumpulkan pada tahap sebelumnya. Pada tahap ini seorang tester tidak hanya mencari celah keamanan, tetapi juga menentukan celah yang paling efektif untuk digunakan.

* **Vulnerability Analysis**
Tahap dimana seorang atau sekelompok tester mengkombinasikan informasi mengenai celah keamanan yang ada dengan metode serangan yang bisa dilakukan untuk melakukan serangan yang paling efektif.

* **Exploitation**
Tahap dimana seorang pentester melakukan serangan pada target. Walaupun demikian tahap ini kebanyakan dilakukan dengan metode brute force tanpa memiliki unsur presisi. Seorang pentester profesional hanya akan melakukan exploitation ketika dia sudah mengetahui secara pasti apakah serangan yang dilakukan akan berhasil atau tidak. Namun tentu saja ada kemungkinan tidak terduga dalam sistem keamanan target. Walaupun begitu, sebelum melakukan serangan, pentester harus tahu kalau target mempunyai celah keamanan yang bisa digunakan. Melakukan serangan secara membabi-buta dan berharap sukses bukanlah metode yang produktif. Seorang pentester profesional selalu menyempurnakan analisisnya terlebih dahulu sebelum melakukan serangan yang efektif.

* **Post Exploitation**
Tahap dimana seorang pentester berhasil masuk ke dalam sistem jaringan target dan kemudian melakukan analisis infrastruktur yang ada. Pada tahap ini seorang pentester mempelajari bagian-bagian di dalam sistem dan menentukan bagian yang paling critical bagi target. Disini seorang pentester harus bisa menghubungkan semua bagian-bagian sistem yang ada untuk menjelaskan dampak serangan / kerugian yang paling besar yang bisa terjadi pada target.

* **Reporting**
Reporting adalah bagian penting dalam kegiatan penetration testing. Seorang pentester menggunakan report (laporan) untuk menjelaskan pada client mengenai pentesting yang dilakukan seperti : apa yang dilakukan, bagaimana cara melakukannya, resiko yang bisa terjadi dan yang paling utama adalah cara untuk memperbaiki sistemnya.


**2. Metasploit**

**Metasploit** adalah sebuah framework, sebagai platform pengembangan untuk menciptakan alat keamanan dan eksploitasi. Kerangka ini digunakan oleh profesional keamanan jaringan untuk melakukan penetration testing, administrator sistem untuk memverifikasi instalasi patch, vendor produk untuk melakukan pengujian regresi, dan peneliti keamanan di seluruh dunia. Kerangka ditulis dalam bahasa pemrograman Ruby dan termasuk komponen yang ditulis dalam C dan assembler. ([sumber](https://aakdhimas.wordpress.com/2011/08/09/apa-sih-metasploit-untuk-apa-sih/))

Beberapa modul dari Metasploit yang kami gunakan adalah sebagai berikut :

* **usermap_script**
Modul ini memanfaatkan Remote Command Injection vulnerability pada Samba versi 3.0.20 - 3.0.25rc3 ketika mengaktifkan opsi konfigurasi 'usernamep map script'. Dengan menginputkan username yang mengandung karakter shell, penyerang dapat mengeksekusi perintah sewenang-wenang. Autentikasi tidak diperlukan untuk mengeksploitasi vulnerability ini, karena opsi 'username map script' memetakan username sebelum autentikasi dilakukan. ([sumber](https://www.rapid7.com/db/modules/exploit/multi/samba/usermap_script))

* **ssh_login_pubkey**
SSH Login Pubkey adalah modul Metasploit untuk melakukan impersonate login ke komputer-komputer dalam subnet menggunakan private key yang telah diambil dari komputer target. ([sumber](https://www.offensive-security.com/metasploit-unleashed/scanner-ssh-auxiliary-modules/))

**3. Metasploitable**

**Metasploitable**  adalah mesin virtual Linux yang sengaja dirancang agar memiliki banyak vulnerabilities. VM ini dapat digunakan untuk melakukan pelatihan keamanan, alat tes keamanan, dan praktek penetration testing. Image file dari Metasploitable dapat diunduh pada [Sourceforge](https://sourceforge.net/projects/metasploitable/files/Metasploitable2/). ([sumber](http://ch06-blackers.blogspot.co.id/2013/04/5-vulnerable-distro-untuk-berlatih.html))

**4. Tools Lainnya**

* **Nmap**
Nmap (Network Mapper) adalah sebuah program open source yang berguna untuk mengesksplorasi jaringan. Nmap didesain untuk dapat melakukan scan jaringan yang besar, juga dapat digunakan untuk melakukan scan host tunggal. Nmap menggunakan paket IP untuk menentukan host-host yang aktif dalam suatu jaringan, port-port yang terbuka, sistem operasi yang dipunyai, tipe firewall yang dipakai, dll.

* **OpenVAS**
OpenVAS (Open Vulnerability Assessment System) merupakan alat bantu yang banyak digunakan untuk mencari celah keamanan  dan menguji keamanan sebuah sistem. OpenVAS masih satu keluarga dengan Nessus (tools yang banyak digunakan untuk melakukan scanning pada web),namun OpenVAS dikembangkan dengan cara yang berbeda dan bersifat free. Konon kabarnya OpenVAS dikembangkan dari versi free dari Nessus. Tools ini banyak digunakan dan termasuk top 5 open source tools di bidang security.

* **John the Ripper**
John the Ripper adalah password cracker yang cepat tersedia untuk system operasi Unix, Windows, DOS, BeOS, dan OpenVMS. Tujuan utamanya adalah untuk mendeteksi password Unix yang lemah. Selain 3 sandi jenis hash yang paling umum ditemukan di berbagai sistem Unix, John the Ripper juga mendukung untuk Windows LM hash, ditambah dengan crypt hash yang lain. Terdapat 3 metode yang dilakukan John the Ripper untuk mendekripsi password yaitu Single Crack (mencari password paling lemah dari seluruh password), Wordlist, dan Incremental (mencoba kombinasi karakter apapun).

* **Ingreslock**
Ingreslock adalah layanan turunan dari database Ingres yang menggunakan TCP 1524 (Transmission Control Protocol). Namun yang menjadi masalah adalah pada port 1524 rentan disusupi backdoor yang mengeksploitasi servis RPC (Remote Procedure Call).

## Langkah Instalasi  Metasploitable

1. Download file .vmdk Metasploitable dari [link berikut](http://sourceforge.net/projects/metasploitable)  
 ![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/Screenshot_InstalasiMetasploitable-RunningMetasploit/Screenshot_1.jpg)

2. Setelah selesai didownload, extract file ke dalam folder bebas, dan pastikan ada file berekstensi .vmdk dalam folder hasil ekstraksi  
 ![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/Screenshot_InstalasiMetasploitable-RunningMetasploit/Screenshot_2.jpg)

3. Setelah itu, buka VirtualBox. Buat VM baru dengan OS Type Linux dan versi Ubuntu 32 bit  
 ![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/Screenshot_InstalasiMetasploitable-RunningMetasploit/Screenshot_3.jpg)

4. Masukkan ukuran RAM dari VM yang kita inginkan, misal 1 GB  
 ![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/Screenshot_InstalasiMetasploitable-RunningMetasploit/Screenshot_4.jpg)

5. Pada opsi selanjutnya, pilih *Use an existing virtual hard drive*, dan browse ke file Metasploitable.vmdk yang telah diekstrak pada langkah 2  
 ![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/Screenshot_InstalasiMetasploitable-RunningMetasploit/Screenshot_5.jpg)

6. Setelah VM selesai dibuat, mulai jalankan VM dengan cara klik tombol Start / Mulai pada menubar VirtualBox  
 ![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/Screenshot_InstalasiMetasploitable-RunningMetasploit/Screenshot_6.jpg)

7. Jendela yang menampilkan VM akan tampil. Untuk login, masuk dengan menggunakan akun msfadmin (akun default) dengan password : msfadmin  
 ![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/Screenshot_InstalasiMetasploitable-RunningMetasploit/Screenshot_7.jpg)

8. Anda berhasil login ke dalam VM Metasploitable  
 ![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/Screenshot_InstalasiMetasploitable-RunningMetasploit/Screenshot_8.jpg)

  Setelah berhasil, kita perlu men-*setting* konfigurasi jaringan pada VirtualBox agar VM Metasploitable juga mendapatkan IP dari DHCP

  Langkah-langkahnya adalah sebagai berikut :

1. Masuk ke Pengaturan / *Preferences* VM Metasploitable pada menubar VirtualBox. Pilih opsi terpasang pada Adaptor Ter-bridge dan tentukan nama dari *interface* jaringan yang dihubungkan dengan VM, kemudian pilih opsi Ijinkan Semua pada Mode Promiscuous  
 ![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/Screenshot_InstalasiMetasploitable-RunningMetasploit/Screenshot_9.jpg)

2. Ketikkan *dhclient* pada VM Metasploitable untuk meminta alamat IP ulang dari DHCP server. Jika berhasil, maka hasil keluaran ifconfig akan sesuai dengan subnet jaringan *interface* yang dipilih  
 ![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/Screenshot_InstalasiMetasploitable-RunningMetasploit/Screenshot_10.jpg)

## Langkah Instalasi OpenVAS

Untuk tahap vulnerability analysis, dapat menggunakan bantuan tools OpenVAS, yaitu *free software* untuk *scan vulnerabilities* langsung ke komputer target. Oleh karena itu, kami menyertakan langkah-langkah instalasi OpenVAS.

1. Ketikkan perintah **apt-get install openvas** untuk memulai proses instalasi  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/Screenshot_InstalasiMetasploitable-RunningMetasploit/Screenshot_14.jpg)

2. Pilih OK untuk mengaktifkan redis unix socket agar OpenVAS scanner dapat mengakses redis database  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/Screenshot_InstalasiMetasploitable-RunningMetasploit/Screenshot_15.jpg)

3. Tunggu proses instalasi selesai, jika sudah maka pada baris akhir akan openvas akan menggenerate password 
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/Screenshot_InstalasiMetasploitable-RunningMetasploit/Screenshot_17.jpg)

4. Setelah proses instalasi selesai, jalankan dengan perintah **openvas-setup** 
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/Screenshot_InstalasiMetasploitable-RunningMetasploit/Screenshot_16.jpg)

5. Untuk melihat port apa saja yang terbuka dan memastikan apakah openvas telah berjalan, jalankan perintah **netstat -antp**. Openvas mempunyai 3 servis yang dijalankan, yakni **openvasmd(openvas manager),  openvassd(melakukan inspeksi pada remote host), dan openvas gsad(openvas GUI yang dapat dijalankan dari web )**.  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/Screenshot_InstalasiMetasploitable-RunningMetasploit/Screenshot_18.jpg)

6. Jika ketika aplikasi tersebut belum berjalan, dapat menjalankan dengan perintah **openvas-stasr**  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/Screenshot_InstalasiMetasploitable-RunningMetasploit/Screenshot_19.jpg)

7. Akses openvas GUI pada browser dengan mengunjungi **https://localhost:9392**. Jika muncul sertifikat tidak valid, silahkan tambahkan sertifikat pada exceptions.  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/Screenshot_InstalasiMetasploitable-RunningMetasploit/Screenshot_20.jpg)

8. Login dengan kredensial Username **admin** dan password yang telah digenerate ketika menginstall openvas  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/Screenshot_InstalasiMetasploitable-RunningMetasploit/Screenshot_21.jpg)


## Langkah Penetration Testing

### Preinteractions

Kami melakukan diskusi terlebih dahulu mengenai tools-tools yang akan digunakan untuk melakukan penetration testing (Metasploit, OpenVAS, dll), lingkup (Metasploit) dan tujuan dari penetration testing.

### Intelligence Gathering

Untuk memulai analisa *exploit* apa saja yang dapat diterapkan, kita dapat melihat *list* port yang terbuka dan versi kernel yang digunakan pada Metasploitable menggunakan tool Nmap. Gunakan perintah **nmap -O < IP Metasploitable >**  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/Screenshot_InstalasiMetasploitable-RunningMetasploit/Screenshot_11.jpg)

### Threat Modeling

1. Dari hasil tahap sebelumnya dapat diketahui versi kernel yang digunakan Metasploitable. Dari versi tersebut, kita dapat mencari *vulnerabilities* yang ada di website cvedetails.com    
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/Screenshot_InstalasiMetasploitable-RunningMetasploit/Screenshot_12.jpg)

2. Berikut adalah daftar *vulnerabilities* pada Linux Kernel versi 2.6.9 yang digunakan Metasploitable. Jika pada score sangat tinggi dan higligh berwarna merah, maka dapat dipastikan bahwa celah tersebut sangat berbahaya.  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/Screenshot_InstalasiMetasploitable-RunningMetasploit/Screenshot_13.jpg)

### Vulnerability Analysis

1. Nyalakan OpenVAS dan login ke dalamnya melalui web browser. Masukkan IP target seperti di gambar berikut   
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/Screenshot_InstalasiMetasploitable-RunningMetasploit/Screenshot_22.jpg)

2. Kita dapat melihat hasil *scanning*	nya seperti gambar berikut  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/Screenshot_InstalasiMetasploitable-RunningMetasploit/Screenshot_23.jpg)

3. Dapat dilihat pada hasil audit oleh openvas, terdapat beberapa celah yang dapat dieksploitasi  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/Screenshot_InstalasiMetasploitable-RunningMetasploit/Screenshot_24.jpg)

### Exploitation & Post Exploitation

Untuk penggunaan Metasploit, pada Kali Linux sudah terinstall secara bawaan, dan untuk mengaksesnya dapat menggunakan perintah **msfconsole**  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/Screenshot_InstalasiMetasploitable-RunningMetasploit/Screenshot_25.png)

* #### Exploit Menggunakan usermap_script & Post Exploit Menggunakan John The Ripper

1. Jika sudah masuk pada **msfconsole**, ketikkan perintah **use exploit/multi/samba/usermap_script** untuk menggunakan modul usermap_script  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/Screenshot_Exploit_usermap_script/1.jpg)

2. Gunakan opsi **show options** untuk melihat opsi konfigurasi pada modul  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/Screenshot_Exploit_usermap_script/2.jpg)

3. Tetapkan IP dari host target yang akan di eksploit  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/Screenshot_Exploit_usermap_script/3.jpg)

4. Gunakan perintah **exploit** untuk memulai proses eksploitasi, jika berhasil maka ada pemberitahuan seperti **Command shell session 1 opened ...** dan anda dapat mulai melakukan Remote Command Injection ke komputer target  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/Screenshot_Exploit_usermap_script/4.jpg)

Post Exploit yang akan dilakukan adalah menggunakan tool John The Ripper untuk meng-*crack* list password yang tersimpan pada file shadow komputer target

1. Ketikkan perintah **cat /etc/passwd** , dapat dilihat beberapa username yang kemungkinan dapat dilakukan untuk login ke komputer target  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/Screenshot_Exploit_usermap_script/5.jpg)

2. Salin isi dari /etc/passwd pada langkah 5 dan simpan pada sebuah file sembarang pada komputer anda  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/Screenshot_Exploit_usermap_script/6.jpg)

3. Ketikkan perintah **cat /etc/shadow** , dapat dilihat beberapa username dan password yang dienkripsi yang kemungkinan dapat dilakukan untuk login ke komputer target  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/Screenshot_Exploit_usermap_script/7.jpg)

4. Salin isi dari /etc/shadow pada langkah 7 dan simpan pada sebuah file sembarang pada komputer anda  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/Screenshot_Exploit_usermap_script/8.jpg)

5. Gunakan perintah **unshadow PASSWORD-FILE SHADOW-FILE** untuk menggabungkan file passwd (langkah 6) dan shadow (langkah 8) agar dapat digunakan John  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/Screenshot_Exploit_usermap_script/9.jpg)

6. Berikut isi dari file yang digabungkan pada langkah 9  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/Screenshot_Exploit_usermap_script/10.jpg)

7. Gunakan perintah **john UNSHADOW-FILE** untuk memulai proses *cracking*, jika berhasil maka keluaran yang dihasilkan adalah list password yang telah berhasil di-*crack*  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/Screenshot_Exploit_usermap_script/11.jpg)

8. Gunakan perintah **john --show UNSHADOW-FILE** untuk melihat kembali list password yang telah berhasil di-*crack*  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/Screenshot_Exploit_usermap_script/12.jpg)

9. Lakukan SSH ke komputer target dengan username dan password yang berhasil di-*crack*  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/Screenshot_Exploit_usermap_script/13.jpg)


* #### Exploit Menggunakan mount NFS(Network File System) & Post Exploit Menggunakan ssh_login_pubkey

1. Pada hasil nmap, kita melihat ada open port NFS pada Metasploitable  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/ssh_login_pubkey/1.png)

2. Kita coba lihat path mount apa yang disediakan oleh komputer target, ternyata menyediakan langsung ke direktori root (/*)  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/ssh_login_pubkey/2.png)

3. Untuk bisa mengakses mount NFS, kita harus menyalakan service rpcbind  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/ssh_login_pubkey/3.png)

4. Kita buat folder sementara untuk mount NFS komputer target  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/ssh_login_pubkey/4.png)

5. Lalu kita mount folder yang telah kita buat dengan NFS target  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/ssh_login_pubkey/5.png)

6. Berhasil melakukan mount dengan target  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/ssh_login_pubkey/6.png)

Tentu saja ini berbahaya, karena kita bisa melihat dan mengambil file apa saja yang ada di dalam komputer, bahkan file sensitif seperti key untuk ssh, file passwd, dll.

Post Exploit yang dirancang adalah dengan *impersonate* sebagai komputer target dengan private key yang kita ambil.

1. Kita ambil private key komputer target dengan copy file di ~/.ssh/id_rsa , misal ke file /tmp/r00tprivatekey  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/ssh_login_pubkey/7.png)

2. Setelah ini, kita coba menggunakan modul Metasploit ssh_login_pubkey untuk menyerang. Ketikkan **use auxiliary/scanner/ssh/ssh_login_pubkey** untuk menggunakan modul tersebut dalam msfconsole  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/ssh_login_pubkey/10.png)

3. Kita coba lihat info dari exploit tersebut. Parameter yang dibutuhkan adalah KEY_PATH, USER, dan RHOSTS  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/ssh_login_pubkey/11.png)

4. Masukkan KEY_PATH atau file private key komputer server yang tadi telah kita copy  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/ssh_login_pubkey/12.png)

5. Masukkan USER yang kita inginkan, yaitu root  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/ssh_login_pubkey/13.png)

6. Masukkan RHOSTS yaitu subnet yang ingin kita lakukan login dengan private key yang kita punya  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/ssh_login_pubkey/rhosts.png)

7. Masukkan perintah run untuk menjalankan exploit. Tampak bahwa Metasploit sedang mencoba login dengan semua IP dalam subnet satu per satu  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/ssh_login_pubkey/run.png)

8. Jika ada yang berhasil, maka akan muncul tampilan seperti berikut  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/ssh_login_pubkey/success_otherpc.png)

9. Pada bagian bawah, tampak bahwa metasploit telah membuka session ssh ke IP 192.168.43.12 di session 1  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/ssh_login_pubkey/detailsuccess.png)

10. Kita masuk ke session 1 dengan perintah session -i 1  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/ssh_login_pubkey/17.png)

11. Untuk memastikan apakah kita benar login sebagai root, ketikkan whoami  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/ssh_login_pubkey/whoami.png)

12. Kita dapat menjalankan perintah *shell* setelah melakukan session. Kita dapat melakukan post exploit lain seperti mengubah password user, dll  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/ssh_login_pubkey/example.png)

* #### Exploit Menggunakan Ingreslock & Post Exploit menampilkan pesan pada console ketika pengguna login

1. Pada saat dilakukan audit dengan OpenVas, terdapat backdoor Ingreslock pada Remote Host  
![Ingreslock](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/Screenshot_Exploit_Ingreslock/Screenshot_1.jpg)

2. Jika di klik, maka akan menampilkan keterangan mengenai backdoor tersebut  
![Ingreslock](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/Screenshot_Exploit_Ingreslock/Screenshot_2.jpg)

3. Karena sudah terdapat backdoor yang tertanam pada Metasploitable, serangan dapat dilakukan dengan perintah **telnet [Remote Host] 1524**. Maka kita sudah dapat mengakses console dari remote HOST  
![Ingreslock](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/Screenshot_Exploit_Ingreslock/success.jpeg).

Post Exploit yang akan dilakukan adalah menampilkan pesan pada console ketika terdapat pengguna yang login, cara ini biasa dimanfaatkan penyerang untuk meninggalkan pesan yang bersifat provokatif atau memiliki tujuan lebih lanjut

4. Setelah masuk ke dalam console, buka file ~/.bashrc dan masukkan kata yang diinginkan, maka ketika terdapat pengguna yang masuk ke console, akan menampilkan pesan yang kita tulis  
![Ingreslock](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/SC_Post_Exploit_menambahkan%20data%20di%20bashrc/1.jpeg)

### Reporting

Dokumen yang kami tulis ini adalah report dari hasil penetration testing yang sudah kami lakukan.


## Kesimpulan dan Saran

### Kesimpulan

Penetration Testing adalah metode yang selalu dilakukan oleh penyerang ketika melakukan penetrasi ke sebuah sistem baik dengan tujuan mengeksploitasi atau memperbaiki celah keamanan yang ada. Metasploit dan Metasploitable merupakan tools yang cocok digunakan untuk melakukan uji coba penetration testing, karena Metasploitable memang dibuat khusus untuk mengevaluasi kinerja Metasploit.
 
### Saran
*   Penting dilakukan untuk selalu mengaudit sistem kita apakah terdapat celah ataupun tidak. Bisa dilakukan dengan aplikasi seperti OpenVAS. 
*   Selalu mengupdate kernel, aplikasi, dan OS agar berbagai celah yang ada dapat segera mendapatkan patch jika sudah tersedia.


