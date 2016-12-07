# **Tugas 5 PKSJ - Analisa Exploit dengan Metasploitable, Metasploit dan Nmap**


## Pendahuluan

Tugas ini dibuat untuk menyelesaikan Tugas 5 yaitu "Analisa Exploit dengan Metasploitable, Metasploit Nmap" pada matakuliah Perancangan Keamanan & Sistem Jaringan (PKSJ) Semester Ganjil 2016/2017, Teknik Informatika ITS, Surabaya
 
Anggota Kelompok
- Ardi Nusawan      5113100096
- Gian Sebastian A. 5113100132
- Ronauli Sidabukke 5113100142


## Dasar Teori

**1. Metasploit**

**Metasploit** adalah sebuah framework, sebagai platform pengembangan untuk menciptakan alat keamanan dan eksploitasi. Kerangka ini digunakan oleh profesional keamanan jaringan untuk melakukan tes penetrasi, administrator sistem untuk memverifikasi instalasi patch, vendor produk untuk melakukan pengujian regresi, dan peneliti keamanan di seluruh dunia. Kerangka ditulis dalam bahasa pemrograman Ruby dan termasuk komponen yang ditulis dalam C dan assembler.. ([sumber](https://aakdhimas.wordpress.com/2011/08/09/apa-sih-metasploit-untuk-apa-sih/))
 
**2. Metasploit**

* **Metasploitable**  adalah mesin secara sengaja rentan virtual Linux. VM ini dapat digunakan untuk melakukan pelatihan keamanan, alat tes keamanan, dan praktek penetrasi Versi pengujian umum teknik ini 2 dari mesin virtual yang tersedia untuk di-download dari Sourceforge dan kapal dengan kerentanan bahkan lebih dari gambar asli ([sumber](http://ch06-blackers.blogspot.co.id/2013/04/5-vulnerable-distro-untuk-berlatih.html))


## Langkah Instalasi  Metasploitable

1. Download file .vmdk Metasploitable dari [link berikut](http://sourceforge.net/projects/metasploitable)  
 ![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/Screenshot_InstalasiMetasploitable-RunningMetasploit/Screenshot_1.jpg)

2. Setelah selesai didownload, extract file ke dalam folder bebas, dan pastikan ada file berekstensi .vmdk dalam hasil kompresi.  
 ![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/Screenshot_InstalasiMetasploitable-RunningMetasploit/Screenshot_2.jpg)

3. Setelah itu, buka VirtualBox. Buat VM baru dengan nama Metasploitable, OS Type Linux dan versi Ubuntu 32 bit  
 ![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/Screenshot_InstalasiMetasploitable-RunningMetasploit/Screenshot_3.jpg)

4. Masukkan ukuran RAM dari VM yang kita inginkan, misal 1 GB  
 ![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/Screenshot_InstalasiMetasploitable-RunningMetasploit/Screenshot_4.jpg)

5. Pada opsi selanjutnya, pilih *use an existing virtual hard drive*, dan browse ke file .vmdk yang tadi telah diekstrak   
 ![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/Screenshot_InstalasiMetasploitable-RunningMetasploit/Screenshot_5.jpg)

6. Setelah VM Selesai dibuat, mulai jalankan VM dengan cara klik tombol start pada panel atas Virtualbox.  
 ![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/Screenshot_InstalasiMetasploitable-RunningMetasploit/Screenshot_6.jpg)

7. Jendela yang menampilkan *console* vm akan tampil. Untuk test, masuk dengan menggunakan akun msfadmin , password : msfadmin (*account* default)  
 ![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/Screenshot_InstalasiMetasploitable-RunningMetasploit/Screenshot_7.jpg)

8. Jika berhasil, maka anda berhasil login ke dalam metasploitable  
 ![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/Screenshot_InstalasiMetasploitable-RunningMetasploit/Screenshot_8.jpg)

  Setelah berhasil, kita perlu men-*setting* konfigurasi jaringan pada Virtualbox agar VM Metasploitable juga mendapatkan IP dari DHCP, sehingga testing bisa dilakukan lewat IP tersebut.

  Langkah-langkahnya adalah sebagai berikut :

1. Masuk ke pengaturan / *Preferences* pada menubar Virtualbox, dari menu File. Pilih nama dari *interface* jaringan yang dihubungkan dengan VM.   
 ![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/Screenshot_InstalasiMetasploitable-RunningMetasploit/Screenshot_9.jpg)

2. Setelah selesai , ketikkan *dhclient* pada Metasploitable untuk meminta alamat IP ulang dari DHCP server. Jika berhasil, maka hasil keluaran ifconfig akan sesuai dengan subnet jaringan yang *interface* yang tadi dipilih.  
 ![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/Screenshot_InstalasiMetasploitable-RunningMetasploit/Screenshot_10.jpg)

##Instalasi Open VAS

Untuk vulnerability scanning, kita dapat menggunakan tools Open VAS , yaitu tools *open source* untuk *scan vulnerabilities* langsung ke komputer target. Oleh karena itu, kami menyertakan instalasi OpenVAS

1. Kita dapat mengetikkan perintah **# apt-get install openvas**  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/Screenshot_InstalasiMetasploitable-RunningMetasploit/Screenshot_14.jpg)

2. Pilih OK untuk *enable* redis unix socket (konfigurasi openvas)  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/Screenshot_InstalasiMetasploitable-RunningMetasploit/Screenshot_15.jpg)

3. Lorem ipsum  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/Screenshot_InstalasiMetasploitable-RunningMetasploit/Screenshot_16.jpg)

4. Lorem ipsum  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/Screenshot_InstalasiMetasploitable-RunningMetasploit/Screenshot_17.jpg)

5. Lorem ipsum  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/Screenshot_InstalasiMetasploitable-RunningMetasploit/Screenshot_18.jpg)

6. Lorem ipsum  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/Screenshot_InstalasiMetasploitable-RunningMetasploit/Screenshot_19.jpg)

7. Lorem ipsum  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/Screenshot_InstalasiMetasploitable-RunningMetasploit/Screenshot_20.jpg)

8. Lorem Ipsum  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/Screenshot_InstalasiMetasploitable-RunningMetasploit/Screenshot_21.jpg)

9. Kita masukkan IP target seperti di gambar berikut   
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/Screenshot_InstalasiMetasploitable-RunningMetasploit/Screenshot_22.jpg)

10. Kita dapat melihat hasil *scanning*	nya seperti gambar berikut  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/Screenshot_InstalasiMetasploitable-RunningMetasploit/Screenshot_23.jpg)

11. Lorem Ipsum  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/Screenshot_InstalasiMetasploitable-RunningMetasploit/Screenshot_24.jpg)

##Penggunaan Metasploit

Untuk penggunaan metasploit, pada Kali Linux sudah terinstall secara bawaan, dan untuk mengaksesnya dapat menggunakan perintah msfconsole  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/Screenshot_InstalasiMetasploitable-RunningMetasploit/Screenshot_25.png)


## Intelligence Gathering Process

1. Untuk memulai analisa *exploit* apa saja yang bisa diterapkan, kita dapat melihat *list* port terbuka di Metasploitable. Lakukan perintah nmap -O < IP Metasploitable >  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/Screenshot_InstalasiMetasploitable-RunningMetasploit/Screenshot_11.jpg)

2. Setelah selesai , kita dapat melihat detail OS metasploitable seperti versi kernel, dkk. Dari versi tersebut, kita dapat mencari *vulnerabilities* yang ada di website cvedetails.com    
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/Screenshot_InstalasiMetasploitable-RunningMetasploit/Screenshot_12.jpg)

3. Lorem Ipsum  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/Screenshot_InstalasiMetasploitable-RunningMetasploit/Screenshot_13.jpg)


## Exploit SSH Login PubKey


1. Pada hasil nmap , kita melihat ada open port NFS pada Metasploitable  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/ssh_login_pubkey/1.png)

2. Kita coba lihat di mount apa yang disediakan oleh komputer target, ternyata menyediakan langsung ke direktori root (/*)  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/ssh_login_pubkey/2.png)

3. Untuk bisa mengakses mount NFS, kita harus menyalakan service rpcbind  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/ssh_login_pubkey/3.png)

4. Kita buat folder sementara untuk mount NFS komputer target  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/ssh_login_pubkey/4.png)

5. Lalu kita mount folder yang telah kita buat ke NFS target  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/ssh_login_pubkey5.png)

6. Jika berhasil, coba tes apakah sudah berhasil me-mount apa belum dengan cd ke folder sementara dan lakukan ls.  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/ssh_login_pubkey/6.png)

Tentu saja ini berbahaya, karena kita bisa melihat file apa saja yang ada di dalam komputer, bahkan file sensitif seperti key untuk ssh, file passwd dan lainlain.

Post exploit yang dirancang adalah dengan mengambil private SSH key komputer target, dan dengan metasploit kita dapat mengakses komputer target dengan hak akses root **tanpa wordlist dan bruteforce**,  dengan menggunakan metasploit.

1. Kita ambil private key komputer target dengan copy file di ~/.ssh/id_rsa , misal ke file /tmp/r00tprivatekey  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/ssh_login_pubkey/7.png)

2. Kita ingin menanam private keys di komputer target, namun kita harus punya hak akses untuk manage file di folder home user target. Untuk mensiasatinya, kita masukkan key (namun sebenarnya adalah path folder) kita ke file *authorized_keys* komputer target.  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/ssh_login_pubkey/8.png)

3. Hasil cat file authorized_keys  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/ssh_login_pubkey/9.png)

4. Setelah ini, kita coba menggunakan metasploit auxiliary/scanner/ssh/ssh_login_pubkey untuk menyerang. Kita ketik use auxiliary/scanner/ssh/ssh_login_pubkey untuk menggunakan modul tersebut dalam console metasploit.  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/ssh_login_pubkey/10.png)

5. Kita coba lihat info dari exploit tersebut. Parameter yang dibutuhkan adalah KEY_PATH, USER, dan RHOSTS  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/ssh_login_pubkey/11.png)

6. Masukkan KEY_PATH atau file private key komputer server yang tadi telah kita copy  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/ssh_login_pubkey/12.png)

7. Masukkan USER yang kita inginkan, yaitu root  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/ssh_login_pubkey/13.png)

8. Masukkan RHOSTS yaitu IP Komputer target  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/ssh_login_pubkey/14.png)

9. Masukkan perintah run untuk menjalankan exploit.   
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/ssh_login_pubkey/15.png)

10. Pada bagian bawah, tampak bahwa metasploit telah membuka session ssh di session 1   
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/ssh_login_pubkey/16.png)

11. Kita masuk ke session 1 dengan perintah session -i 1   
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/ssh_login_pubkey/17.png)

12. Untuk memastikan apakah kita benar login sebagai root, kita ketikkan perintah id  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/ssh_login_pubkey/30.png)

13. Coba masukkan perintah lain seperti uname -a , dan perintah lain. Selamat ! Kita sudah bisa mengakses root di komputer target!   
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/ssh_login_pubkey/18.png)
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/ssh_login_pubkey/19.png)
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/ssh_login_pubkey/20.png)




## Kesimpulan dan Saran

### Kesimpulan
1. Lorem Ipsum
2. Lorem Ipsum

### Saran
**Login ke sistem dan memantau keadaan server setiap hari** 
*  Mengecek sukses/gagal login pada hari itu
*  rootkit checks (rkhunter, rootkitchck)

**Mencegah Bots dan Backdoors**
*  Memonitor semua koneksi yang keluar
*  Memonitor semua port yang terbuka
*  Memonitor request yang masuk
*  Menetapkan tindakan preventif apabila terdapat anomali pada network / sistem

