# **Tugas 1 PKSJ - Ganjil 2016/2017**


## Pendahuluan

Tugas ini dibuat untuk menyelesaikan Tugas 1 pada matakuliah Perancangan Keamanan & Sistem Jaringan (PKSJ) Semester Ganjil 2016/2017, Teknik Informatika ITS, Surabaya
 
Anggota Kelompok
- Ardi Nusawan      5113100096
- Gian Sebastian A. 5113100132
- Ronauli Sidabukke 5113100142

### Penjelasan Tugas
**Uji penetrasi 1 :**
* Instal sebuah virtual OS dengan Ubuntu server
* Instal SSH server dengan konfigurasi default
* Instal satu lagi virtual OS dengan OS bebas, misalnya Kali Linux atau Ubuntu Desktop
* Pastikan tools untuk SSH brute force attack sudah terinstal
* Lakukan uji penetrasi 1: dengan THC-Hydra atau Ncrack dan catat hasil uji penetrasi 

**Uji penetrasi 2:**
* Instal fail2ban pada Ubuntu server yang telah diinstal SSH servernya
* Konfigurasilah SSH server agar tidak default lagi
* Lakukan uji penetrasi 2 dengan tools yang sama dan catat hasilnya


## Dasar Teori

**1. OS yang digunakan**

* **Ubuntu Server** adalah ubuntu yang  didesain untuk di install di server. Perbedaan mendasar, di Ubuntu Server tidak tersedia GUI. Jika anda menggunakan ubuntu server artinya anda harus bekerja dengan perintah perintah di layar hitam ayng sering disebut konsole. Jika anda datang dari windows, maka tampilan ubuntu server seperti DOS ([sumber](http://www.candra.web.id/mengenal-ubuntu-server/))
 
* **Kali Linux** adalah distribusi berlandasan distribusi Debian GNU/Linux untuk tujuan forensik digital dan di gunakan untuk pengujian penetrasi, yang dipelihara dan didanai oleh Offensive Security. Kali juga dikembangkan oleh  Offensive Security sebagai penerus BackTrack Linux. Kali menyediakan pengguna dengan mudah akses terhadap koleksi yang besar dan komprehensif untuk alat yang berhubungan dengan keamanan, termasuk port scanner untuk password cracker. ([sumber](http://gudanglinux.com/glossary/kali-linux/))

**2. Tools yang digunakan**

*Cracking Tool*

* **Hydra**, adalah salah satu tools brute force *password* dapat dicompile/digunakan Linux, Windows/Cygwin, Solaris 11, FreeBSD 8.1, OpenBSD, OSX, QNX/Blackberry. Tutorial instalasi dan penggunaannya dapat diliat pada website resminya ( [link](https://www.thc.org/thc-hydra/) )

    b. Patator, adalah salah satu tools untuk *brute force* password yang lebih baru dari Medusa maupun Hydra. Pada repository resminya, patator ditulis menggunakan bahasa Python dan bersifat *multithread*, dan dituliskan untuk memperbaiki *predesesor* / pendahulunya seperti Hydra atau Medusa. Untuk petunjuk penggunaan & instalasi, dapat dilihat pada [link repository berikut](https://github.com/lanjelot/patator)
    
*Defending Tool*

* **Fail2Ban** adalah package keamanan yang digunakan untuk mencegah serangan brute-force dan DDoS pada linux. Fail2ban bekerja dengan memonitor jumlah kegagalan login untuk selanjutnya memblok ip address dari login yang gagal tersebut.[(sumber)](https://kpunikomlipi.wordpress.com/2012/07/30/konfigurasi-fail2ban-untuk-mengamankan-server/)


## Uji Penetrasi 1


#### 1. Langkah Instalasi Ubuntu Server


#### 2. Langkah Instalasi Kali Linux (OS untuk Penetrasi)

#### 3. Langkah Instalasi SSH Server

#### 4. Langkah Uji Penetrasi dengan SSH Brute Force Tools
