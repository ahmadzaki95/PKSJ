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

* **Intelligence Gathering**

* **Threat Modeling**

* **Vulnerability Analysis**

* **Exploitation**

* **Post Exploitation**

* **Reporting**

**2. Metasploit**

**Metasploit** adalah sebuah framework, sebagai platform pengembangan untuk menciptakan alat keamanan dan eksploitasi. Kerangka ini digunakan oleh profesional keamanan jaringan untuk melakukan penetration testing, administrator sistem untuk memverifikasi instalasi patch, vendor produk untuk melakukan pengujian regresi, dan peneliti keamanan di seluruh dunia. Kerangka ditulis dalam bahasa pemrograman Ruby dan termasuk komponen yang ditulis dalam C dan assembler. ([sumber](https://aakdhimas.wordpress.com/2011/08/09/apa-sih-metasploit-untuk-apa-sih/))

Beberapa modul dari Metasploit yang kami gunakan adalah sebagai berikut :

* **usermap_script**

* **ssh_login_pubkey**

**3. Metasploitable**

**Metasploitable**  adalah mesin virtual Linux yang sengaja dirancang agar memiliki banyak vulnerabilities. VM ini dapat digunakan untuk melakukan pelatihan keamanan, alat tes keamanan, dan praktek penetration testing. Image file dari Metasploitable dapat diunduh pada [Sourceforge](https://sourceforge.net/projects/metasploitable/files/Metasploitable2/). ([sumber](http://ch06-blackers.blogspot.co.id/2013/04/5-vulnerable-distro-untuk-berlatih.html))

**4. Tools Lainnya**

* **Nmap**

* **OpenVAS**

* **John the Ripper**

* **Ingreslock**


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


## Langkah Penetration Testing

### Preinteractions

### Intelligence Gathering

Untuk memulai analisa *exploit* apa saja yang bisa diterapkan, kita dapat melihat *list* port terbuka di Metasploitable. Lakukan perintah nmap -O < IP Metasploitable >  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/Screenshot_InstalasiMetasploitable-RunningMetasploit/Screenshot_11.jpg)

### Threat Modeling

1. Kita dapat melihat detail OS metasploitable seperti versi kernel, dkk. Dari versi tersebut, kita dapat mencari *vulnerabilities* yang ada di website cvedetails.com    
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/Screenshot_InstalasiMetasploitable-RunningMetasploit/Screenshot_12.jpg)

2. Lorem Ipsum  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/Screenshot_InstalasiMetasploitable-RunningMetasploit/Screenshot_13.jpg)

### Vulnerability Analysis

1. Kita masukkan IP target seperti di gambar berikut   
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/Screenshot_InstalasiMetasploitable-RunningMetasploit/Screenshot_22.jpg)

2. Kita dapat melihat hasil *scanning*	nya seperti gambar berikut  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/Screenshot_InstalasiMetasploitable-RunningMetasploit/Screenshot_23.jpg)

3. Lorem Ipsum  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/Screenshot_InstalasiMetasploitable-RunningMetasploit/Screenshot_24.jpg)

### Exploitation & Post Exploitation

Untuk penggunaan Metasploit, pada Kali Linux sudah terinstall secara bawaan, dan untuk mengaksesnya dapat menggunakan perintah **msfconsole**  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/Screenshot_InstalasiMetasploitable-RunningMetasploit/Screenshot_25.png)

* #### Exploit Menggunakan mount NFS(Network Files System) & Post Exploit Menggunakan ssh_login_pubkey

1. Pada hasil nmap , kita melihat ada open port NFS pada Metasploitable  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/ssh_login_pubkey/1.png)

2. Kita coba lihat di mount apa yang disediakan oleh komputer target, ternyata menyediakan langsung ke direktori root (/*)  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/ssh_login_pubkey/2.png)

3. Untuk bisa mengakses mount NFS, kita harus menyalakan service rpcbind  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/ssh_login_pubkey/3.png)

4. Kita buat folder sementara untuk mount NFS komputer target  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/ssh_login_pubkey/4.png)

5. Lalu kita mount folder yang telah kita buat ke NFS target  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/ssh_login_pubkey/5.png)

6. Jika berhasil, coba tes apakah sudah berhasil me-mount apa belum dengan cd ke folder sementara dan lakukan ls.  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/ssh_login_pubkey/6.png)

Tentu saja ini berbahaya, karena kita bisa melihat file apa saja yang ada di dalam komputer, bahkan file sensitif seperti key untuk ssh, file passwd dan lainlain.

Post exploit yang dirancang adalah dengan *impersonate* sebagai komputer target dengan private key yang kita ambil.

1. Kita ambil private key komputer target dengan copy file di ~/.ssh/id_rsa , misal ke file /tmp/r00tprivatekey  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/ssh_login_pubkey/7.png)

2. Kita masukkan public key kita ke komputer target dengan cat ~/.ssh/id_rsa.pub >> /tmp/target/home/msfadmin/.ssh/authorized_keys , ini dibutuhkan untuk SSH ke komputer target nantinya.  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/ssh_login_pubkey/pubkey.png)

3. Hasil cat file authorized_keys, untuk memastikan bahwa public key kita sudah masuk ke komputer target  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/ssh_login_pubkey/hasilcat.png)

4. Setelah ini, kita coba menggunakan metasploit auxiliary/scanner/ssh/ssh_login_pubkey untuk menyerang. Kita ketik use auxiliary/scanner/ssh/ssh_login_pubkey untuk menggunakan modul tersebut dalam console metasploit.  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/ssh_login_pubkey/10.png)

5. Kita coba lihat info dari exploit tersebut. Parameter yang dibutuhkan adalah KEY_PATH, USER, dan RHOSTS  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/ssh_login_pubkey/11.png)

6. Masukkan KEY_PATH atau file private key komputer server yang tadi telah kita copy  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/ssh_login_pubkey/12.png)

7. Masukkan USER yang kita inginkan, yaitu root  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/ssh_login_pubkey/13.png)

8. Masukkan RHOSTS yaitu subnet yang ingin kita bruteforce login dengan private key yang kita punya   
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/ssh_login_pubkey/rhosts.png)

9. Masukkan perintah run untuk menjalankan exploit.   
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/ssh_login_pubkey/success_otherpc.png)

10. Tampak bahwa metasploit sedang mencoba login dengan semua IP dalam subnet satu per satu.   
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/ssh_login_pubkey/run.png)

11. Jika ada yang berhasil, maka akan muncul tampilan seperti berikut.   
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/ssh_login_pubkey/success.png)

11. Pada bagian bawah, tampak bahwa metasploit telah membuka session ssh ke IP 192.168.43.12 di session 1   
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/ssh_login_pubkey/detailsuccess.png)

12. Kita masuk ke session 1 dengan perintah session -i 1   
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/ssh_login_pubkey/17.png)

13. Untuk memastikan apakah kita benar login sebagai root, ketikkan whoami  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/ssh_login_pubkey/whoami.png)

14. Kita dapat menjalankan perintah *shell* setelah melakukan session.Post Exploitnya sukses.   
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/ssh_login_pubkey/example.png)

### Reporting


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


