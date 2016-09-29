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

* **Patator**, adalah salah satu tools untuk *brute force* password yang lebih baru dari Medusa maupun Hydra. Pada repository resminya, patator ditulis menggunakan bahasa Python dan bersifat *multithread*, dan dituliskan untuk memperbaiki *predesesor* /pendahulunya seperti Hydra atau Medusa. Untuk petunjuk penggunaan & instalasi, dapat dilihat pada [link repository berikut](https://github.com/lanjelot/patator)
    
*Defending Tool*

* **Fail2Ban** adalah package keamanan yang digunakan untuk mencegah serangan brute-force dan DDoS pada linux. Fail2ban bekerja dengan memonitor jumlah kegagalan login untuk selanjutnya memblok ip address dari login yang gagal tersebut.[(sumber)](https://kpunikomlipi.wordpress.com/2012/07/30/konfigurasi-fail2ban-untuk-mengamankan-server/)

* **Google Authenticator** adalah sebuah aplikasi yang mengimplementasikan layanan *two-step verification* menggunakan  Time-based One-time Password Algorithm (TOTP) dan HMAC-based One-time Password Algorithm (HOTP), untuk kebutuhan otentikasi pengguna aplikasi mobile oleh Google. Selain itu dapat digunakan untuk menambah keamanan SSH server (menggunakan Google Authenticator PAM), yang bekerja dengan cara meminta kode verifikasi setiap kali ingin log in ke server. Kode verifikasi didapatkan dari *smartphone* anda yang sudah terinstalasi aplikasi Google Authenticator. [(sumber)](https://www.digitalocean.com/community/tutorials/how-to-protect-ssh-with-two-factor-authentication)


## Uji Penetrasi 1


#### 1. Langkah Instalasi Ubuntu Server
  1. Klik 'New' untuk membuat VM baru.    
![Install Ubuntu Server](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Ubuntu_Server/1.jpg)

  2. Masukkan nama, type, dan versi yang sesuai dengan OS yang ingin diinstall.    
![Install Ubuntu Server](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Ubuntu_Server/2.png)

  3. Masukkan RAM uang ingin dialokasikan untuk VM.   
![Install Ubuntu Server](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Ubuntu_Server/3.png)

  4. Pilih 'Buat harddisk sekarang'.   
![Install Ubuntu Server](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Ubuntu_Server/4.png)

  5. Pilih VDI, lalu kontinu.    
![Install Ubuntu Server](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Ubuntu_Server/5.jpeg)

  6. Pilih alokasi yang dinamis, lalu kontinu.    
![Install Ubuntu Server](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Ubuntu_Server/6.jpeg)

  7. Masukkan  size virtual disk yang diinginkan.   
![Install Ubuntu Server](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Ubuntu_Server/7.jpeg)

  8. Pilih tempat ISO dari ubuntu server.   
![Install Ubuntu Server](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Ubuntu_Server/8.jpeg)

  9. Pilih tempat ISO dari ubuntu server (2).    
![Install Ubuntu Server](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Ubuntu_Server/9.jpeg)

  10. Pilih Bahasa yang diinginkan.   
![Install Ubuntu Server](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Ubuntu_Server/10.jpeg)

  11. Pilih Install Ubuntu Server.   
![Install Ubuntu Server](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Ubuntu_Server/11.jpeg)

  12. Pilih bahasa yang ingin digunakan saat melakukan proses instalasi.   
![Install Ubuntu Server](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Ubuntu_Server/12.jpeg)

  13. Pilih negara anda.   
![Install Ubuntu Server](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Ubuntu_Server/13.jpeg)

  14. Pilih 'No' jika tidak ingin mengatur ulang layout keyboard.   
![Install Ubuntu Server](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Ubuntu_Server/14.jpeg)

  15. Pilih negara layout keyboard yang ingin digunakan. 
![Install Ubuntu Server](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Ubuntu_Server/15.jpeg)



  16. Pilih negara layout keyboard yang ingin digunakan (2).   
![Install Ubuntu Server](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Ubuntu_Server/16.jpeg)


  17. Bar progress proses penginstalan ubuntu server.   
![Install Ubuntu Server](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Ubuntu_Server/17.jpeg)


  18. Masukkan nama hostname yang diinginkan.   
![Install Ubuntu Server](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Ubuntu_Server/18.jpeg)


  19. Masukkan nama lengkap user ubuntu server.   
![Install Ubuntu Server](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Ubuntu_Server/19.jpeg)


  20. Masukkan nama username ubuntu server.   
![Install Ubuntu Server](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Ubuntu_Server/20.jpeg)


  21. Masukkan password.   
![Install Ubuntu Server](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Ubuntu_Server/21.jpeg)


  22. Reenter password.   
![Install Ubuntu Server](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Ubuntu_Server/22.jpeg)


  23. Pilih 'No' jika tidak ingin mengenkripsi 'home directory'. 
![Install Ubuntu Server](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Ubuntu_Server/23.jpeg)


  24. Progress bar instalasi.   
![Install Ubuntu Server](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Ubuntu_Server/24.jpeg)


  25. Jika lokasi yang tertera benar, pilih 'Yes'.  
![Install Ubuntu Server](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Ubuntu_Server/25.jpeg)


  26. Pilih 'use entire disk .. LVM'.   
![Install Ubuntu Server](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Ubuntu_Server/26.jpeg)


  27. Pilih partisi yang ingin dijadikan tempat instalasi.   
![Install Ubuntu Server](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Ubuntu_Server/27.jpeg)


  28. Pilih 'Yes'.   
![Install Ubuntu Server](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Ubuntu_Server/28.jpeg)


  29. Karena tadi di awal kita mengalokasikan 8GB untuk partisi, dan yg tertera juga sama, langsung saja klik 'Continue'   
![Install Ubuntu Server](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Ubuntu_Server/29.jpeg)


  30. Pilih 'yes' untuk melanjutkan proses instalasi.   
![Install Ubuntu Server](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Ubuntu_Server/30.jpeg)


  31. Progress bar instalasi ubuntu server.   
![Install Ubuntu Server](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Ubuntu_Server/31.jpeg)


  32. Klik continue jika tidak ingin mensetting proxy.   
![Install Ubuntu Server](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Ubuntu_Server/32.jpeg)


  33. Progress bar instalasi ubuntu server.  
![Install Ubuntu Server](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Ubuntu_Server/33.jpeg)


  34. Pilih install security update automatically.   
![Install Ubuntu Server](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Ubuntu_Server/34.jpeg)


  35. Klik Continue.   
![Install Ubuntu Server](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Ubuntu_Server/35.jpeg)


  36. Progress bar instalasi ubuntu server.   
![Install Ubuntu Server](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Ubuntu_Server/36.jpeg)


  37. Pilih 'Yes' untuk menginstall grub.   
![Install Ubuntu Server](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Ubuntu_Server/37.jpeg)


  38. Instalasi telah selesai, pilih 'Continue' untuk restart VM.   
![Install Ubuntu Server](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Ubuntu_Server/38.jpeg)


  39. Setelah restart VM, maka akan tampil halaman login berupa console terminal.   
![Install Ubuntu Server](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Ubuntu_Server/39.jpeg)


  40. Jika login berhasil, maka akan nampak welcome message seperti berikut :   
![Install Ubuntu Server](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Ubuntu_Server/40.jpeg)


  41. Langkah instalasi openssh server.   
![Install Ubuntu Server](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Ubuntu_Server/41.jpeg)




#### 2. Langkah Instalasi Kali Linux (OS untuk Penetrasi)


  1. Unduh ISO Kali Linux 32 bit /64 bit   
![Install Kali Linux](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Kali_Linux/0.png)


  2. Buka Oracle VM VirtualBox Manajer, kemudian pilih Baru untuk membuat mesin virtual baru    
![Install Kali Linux](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Kali_Linux/1.JPG)


  3. Masukkan nama dan sistem operasi yang sesuai     
![Install Kali Linux](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Kali_Linux/2.JPG)


  4. Atur ukuran memori yang diinginkan (disarankan mengalokasikan memori minimal 2048 MB untuk Kali Linux)    
![Install Kali Linux](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Kali_Linux/3.JPG)


  5. Pilih opsi pembuatan hard disk    
![Install Kali Linux](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Kali_Linux/4.JPG)


  6. Pilih opsi untuk menentukan tipe hard disk    
![Install Kali Linux](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Kali_Linux/5.JPG)


  7. Pilih opsi cara pengalokasian *storage* hard disk     
![Install Kali Linux](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Kali_Linux/6.JPG)


  8. Pilih lokasi dan ukuran hard disk    
![Install Kali Linux](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Kali_Linux/7.JPG)


  9. Pilih mesin virtual yang baru dibuat dan pilih Mulai    
![Install Kali Linux](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Kali_Linux/8.JPG)


  10. Pilih ISO Kali Linux yang di unduh pada langkah 1 untuk memulai proses instalasi
![Install Kali Linux](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Kali_Linux/9.JPG)


  11. Pilih opsi "Install"   
![Install Kali Linux](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Kali_Linux/10.JPG)


  12. Pilih bahasa  yang akan digunakan saat proses instalasi (menjadi bahasa *default* dari sistem)  
![Install Kali Linux](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Kali_Linux/11.JPG)


  13. Pilih benua tempat tinggalmu untuk menentukan *time zone*
![Install Kali Linux](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Kali_Linux/12.JPG)


  14. Pilih negara tempat tinggalmu untuk menentukan *time zone*   
![Install Kali Linux](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Kali_Linux/13.JPG)


  15. Pilih negara yang menjadi basis *locale* (Indonesia belum terdaftar)   
![Install Kali Linux](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Kali_Linux/14.JPG)


  16. Pilih *keymap* yang ingin digunakan   
![Install Kali Linux](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Kali_Linux/15.JPG)


  17. Masukkan nama *host*   
![Install Kali Linux](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Kali_Linux/16.JPG)


  18. Masukkan nama *domain* (jika ada)   
![Install Kali Linux](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Kali_Linux/17.JPG)


  19. Masukkan *password* untuk user "root"   
![Install Kali Linux](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Kali_Linux/18.JPG)


  20. Masukkan *password* untuk konfirmasi ulang   
![Install Kali Linux](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Kali_Linux/19.JPG)


  21. Pilih *time zone* yang ingin digunakan   
![Install Kali Linux](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Kali_Linux/20.JPG)


  22. Pilih opsi cara melakukan partisi disk   
![Install Kali Linux](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Kali_Linux/21.JPG)


  23. Pilih disk yang ingin dipartisi   
![Install Kali Linux](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Kali_Linux/22.JPG)


  24. Pilih skema partisi yang ingin digunakan   
![Install Kali Linux](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Kali_Linux/23.JPG)


  25. Tampilan rangkuman dari konfigurasi partisi disk yang akan dilakukan   
![Install Kali Linux](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Kali_Linux/24.JPG)


  26. Pilih "Yes" untuk menjalankan partisi pada disk yang bersangkutan   
![Install Kali Linux](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Kali_Linux/25.JPG)


  27. Tampilan proses instalasi sistem sedang berlangsung   
![Install Kali Linux](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Kali_Linux/26.JPG)


  28. Tampilan instalasi sistem telah berhasil   
![Install Kali Linux](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Kali_Linux/27.JPG)


  29. Masukkan *username* (*default*-nya "root")   
![Install Kali Linux](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Kali_Linux/28.JPG)


  30. Masukkan *password* yang dimasukkan pada langkah 19   
![Install Kali Linux](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Kali_Linux/29.JPG)


  31. Buka terminal dan masukkan perintah "sudo apt-get -y update && sudo apt-get -y upgrade" agar semua aplikasi yang ter-*install* memiliki versi terbaru   
![Install Kali Linux](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Kali_Linux/30.JPG)



#### 3. Langkah Instalasi SSH Server

  1. Pada terminal server, kita ketikkan : sudo apt-get install openssh-server . Lalu masukkan password untuk *root*  
![Install SSH Server](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Openssh_Server/1.png)

  2. Untuk mengecek bisa mengetik: service ssh status. Jika sudah berhasil, maka muncul seperti dibawah ini :  
![Install SSH Server](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Openssh_Server/2.png)  



#### 4. Langkah Uji Penetrasi dengan SSH Brute Force Tools

Pada tahap ini, kami melakukan uji penetrasi (tanpa *defense tools* di sisi server) dengan 4 skenario untuk setiap *attack tools*, yaitu :
1. Dengan username "root" dan password "root"
2. Dengan username "ardi" dan password "12344321"
3. Dengan username di file username.txt dan password di file password_list.txt ( pada list password tidak ada password yang benar)
4. Dengan username di file username.txt dan password di file password_list_true.txt ( pada list password terdapat password yang benar.

* **Dengan Patator**  

  **Skenario 1** : Dengan username "root" dan password "root"

  Dilakukan dengan perintah : patator ssh_login host=10.151.34.170 port=3022 user=root password=root  
Hasilnya berupa pesan "Authentication failed" karena user dan password nya salah

  ![Patator Skenario 1](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Bruteforce_Attack%20(No%20Countermeasures)/patator_1.JPG)

  **Skenario 2** : Dengan username "ardi" dan password "12344321"

  Dilakukan dengan perintah : patator ssh_login host=10.151.34.170 port=3022 user=ardi password=12344321  
Hasilnya berupa pesan informasi dari SSH yang dipenetrasi karena user dan passwordnya benar

  ![Patator Skenario 2](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Bruteforce_Attack%20(No%20Countermeasures)/patator_2.JPG)

  **Skenario 3** : Dengan username di file username.txt dan password di file password_list.txt 

  Dilakukan dengan perintah : patator ssh_login host=10.151.34.170 port=3022 user=FILE0 password=FILE1 0=/root/Desktop/list_user_pass/username.txt 1=/root/Desktop/list_user_pass/password_list.txt

  ![Patator Skenario 3](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Bruteforce_Attack%20(No%20Countermeasures)/patator_3.JPG)

  Hasilnya berupa daftar pesan "Authentication failed" dari kombinasi user dan password yang salah

  ![Patator Skenario 3](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Bruteforce_Attack%20(No%20Countermeasures)/patator_4.JPG)

  **Skenario 4** : Dengan username di file username.txt dan password di file password_list_true.txt

  Dilakukan dengan perintah : patator ssh_login host=10.151.34.170 port=3022 user=FILE0 password=FILE1 0=/root/Desktop/list_user_pass/username.txt 1=/root/Desktop/list_user_pass/password_list_true.txt 

  ![Patator Skenario 4](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Bruteforce_Attack%20(No%20Countermeasures)/patator_5.JPG)

  Hasilnya berupa pesan informasi dari SSH yang dipenetrasi menggunakan kombinasi user dan password yang benar

  ![Patator Skenario 4](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Bruteforce_Attack%20(No%20Countermeasures)/patator_6.JPG)

  Baris terakhir dari hasil perintah yang diinputkan tidak menunjukkan perbedaan apabila SSH berhasil dipenetrasi atau gagal, sehingga tentunya tidak efektif karena hasil tiap kombinasi user dan password harus dilihat satu per satu

  ![Patator Skenario 4](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Bruteforce_Attack%20(No%20Countermeasures)/patator_7.JPG)

  Untuk mengatasi hal tersebut, ditambahkan perintah : -x ignore:fgrep='Authentication failed' agar setiap kombinasi user dan password yang menghasilkan pesan "Authentication Failed" tidak ditampilkan

  ![Patator Skenario 4](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Bruteforce_Attack%20(No%20Countermeasures)/patator_8.JPG)



* **Dengan NCrack**

  **Skenario 1** : Dengan username "root" dan password "root"

  Dilakukan dengan perintah ncrack --user root --pass root 10.151.34.170 -p ssh:3022 -vvv

  ![Ncrack Skenario 1](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Bruteforce_Attack%20(No%20Countermeasures)/ncrack_sk1.png)

  **Skenario 2** : Dengan username "ardi" dan password "12344321"

  Dilakukan dengan perintah : ncrack --user ardi --pass 12344321 10.151.34.170 -p ssh:3022. Hasilnya adalah sebagai berikut :

  ![Ncrack Skenario 2](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Bruteforce_Attack%20(No%20Countermeasures)/ncrack_sk2.png)

  **Skenario 3** : Dengan username di file username.txt dan password di file password_list.txt 

  Dilakukan dengan perintah : ncrack -U list_user_pass/username.txt -P list_user_pass/password_list.txt 10.151.34.170 -p ssh:3022 

  ![Ncrack Skenario 3](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Bruteforce_Attack%20(No%20Countermeasures)/ncrack_sk3.png)

  **Skenario 4** : Dengan username di file username.txt dan password di file password_list_true.txt

  Dilakukan dengan perintah : ncrack -U list_user_pass/username.txt -P list_user_pass/password_list_true.txt 10.151.34.170 -p ssh:3022 

  ![Ncrack Skenario 4](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Bruteforce_Attack%20(No%20Countermeasures)/ncrack_sk4.png)



* **Dengan Hydra**

  **Skenario 1** : Dengan username "root" dan password "root"

  ![Hydra Skenario 1](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Bruteforce_Attack%20(No%20Countermeasures)/hydra_sk1.png)

  **Skenario 2** : Dengan username "ardi" dan password "12344321"

  ![Hydra Skenario 2](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Bruteforce_Attack%20(No%20Countermeasures)/hydra_sk2.png)

  **Skenario 3** : Dengan username di file username.txt dan password di file password_list.txt 

  ![Hydra Skenario 3](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Bruteforce_Attack%20(No%20Countermeasures)/hydra_sk3.png)

  **Skenario 4** : Dengan username di file username.txt dan password di file password_list_true.txt

  ![Hydra Skenario 4](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Bruteforce_Attack%20(No%20Countermeasures)/hydra_sk4.png)



## Uji Penetrasi 2


#### 1. Langkah Konfigurasi Fail2Ban

  1. Karena pada layar virtualbox tidak dapat copy-paste, saya masuk ke ubuntu server dengan ssh.  
  ![Installing Fail2Ban](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Fail2Ban/1.jpeg)

  2. Buka file konfigurasi fail2ban dengan 'sudo nano /etc/fail2ban/jail.conf'.
  ![Installing Fail2Ban](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Fail2Ban/2.jpeg)

  3. Terlihat pada gambar, kita akan meng-ignore alamat local kita   
  ![Installing Fail2Ban](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Fail2Ban/3.jpeg)

  4. Bantime berfungsi untuk mengatur waktu waktu ban, disini kita menting selama 600 menit.   
  ![Installing Fail2Ban](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Fail2Ban/4.jpeg)

  5. Findtime berfungsi mirip dengan bantime, dan maxretry adalah jumlah kegagalan memasukkan password sebelum di banned.   
  ![Installing Fail2Ban](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Fail2Ban/5.jpeg)

  6. Destemail adalah alamat email yang ditujukan pika terdapat pesan banned, sendername adalah nama pengirim yang akan tarter pada email, dan mta adalah konfigurasi email service apa yang akan digunakan.   
  ![Installing Fail2Ban](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Fail2Ban/6.jpeg)

  7. Pada action = %(action_)s , fail2ban akan menggunakan settingan yg kita sudah atur dibagian header [DEFAULT].   
  ![Installing Fail2Ban](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Fail2Ban/7.jpeg)

  8. Berikut adalah filter yang tersedia pada fail2ban.   
  ![Installing Fail2Ban](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Fail2Ban/8.jpeg)

  9. Pada gambar, kami menggaktifkan  [nginx-http-auth]. Ini tanya sebagai permisalan jika kita menginstal nginx dan ingin menghindari serangan brute force 
  ![Installing Fail2Ban](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Fail2Ban/9.jpeg)

10 . Pada gambar, kami menginstal ngnx (web server), sendmail (until mengirim email), dan iptables-persisten (untuk menjaga settingan iptables agar ketiga machine di restart settingan fail2ban tidak whiling)   
  ![Installing Fail2Ban](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Fail2Ban/10.jpeg)

  11 . Lalu kita memasukkan settingan iptables seperti berikut :   
  ![Installing Fail2Ban](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Fail2Ban/11.jpeg)

  12 . Dan menggunakan perintah ‘sudo iptables -S’ untuk melihat settingan iptables yang telah diperbaharui   
  ![Installing Fail2Ban](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Fail2Ban/12.jpeg)

  13 . Lalu dents perintah berikut untuk menyimpan settingan firewall pada saat booting agar mash tetap :    
  ![Installing Fail2Ban](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Fail2Ban/13.jpeg)

  14 . Lalu mengaktifkan fail2ban   
  ![Installing Fail2Ban](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Fail2Ban/14.jpeg)

  15 . Jika kita melakukan ‘sudo iptables -S’, maka dalat dilihat port 22 telah dilindungi oleh fail2ban   
  ![Installing Fail2Ban](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Fail2Ban/15.jpeg)

  16 . Saya mencoba mengganti settingan menjadi 1800 menit (30 menit).   
  ![Installing Fail2Ban](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Fail2Ban/16.jpeg)

  17 . Jika terdapat banned, maka fail2ban akan langsung mengemail ke email saya.   
  ![Installing Fail2Ban](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Fail2Ban/17.jpeg)

  18 . Namun jika kita menggunakan setingan default, maka kita akan kesulitan dalam mendeteksi serangan karena tidak tercatat di log   
  ![Installing Fail2Ban](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Fail2Ban/18.jpeg)

  19 . Maka kami mengganti settingan seperti berikut, agar memudahkan dalam melihat serangan (tercatat dalam bentuk log file).  
  ![Installing Fail2Ban](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Fail2Ban/19.jpeg)

  20 . Setelah semua selesai, maka kami merestart fail2ban agar konfigurasi yang telah di setting dapat berjalan.  
  ![Installing Fail2Ban](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Fail2Ban/20.jpeg)

  21 . Dapat dilihat pada gambar, bahwa fail2ban telah terkonfigurasi dengan baik pada iptables  
  ![Installing Fail2Ban](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Fail2Ban/21.jpeg)

  22 . Berikut adalah iptables yang telah mereject IP yang mencoba brute force (Terdapat tulisan REJECT yang tidak ada pada iptables sebelumnya)   
  ![Installing Fail2Ban](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Fail2Ban/22.jpeg)
  


#### 2. Langkah Konfigurasi Google Authenticator

  1. Install Google Authenticator menggunakan perintah : apt-get install libpam-google-authenticator  
![Konfigurasi Google Authenticator](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Konfigurasi_Google_Authenticator/1.png)


  2. Untuk menggunakan Google Authenticator harus mengedit 2 file konfigurasi, salah satunya yaitu file konfigurasi sshd  
![Konfigurasi Google Authenticator](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Konfigurasi_Google_Authenticator/2.png)


  3. Tambahkan baris : auth required pam_google_authenticator.so di file sshd, yang fungsinya untuk mengaktifkan kebutuhan autentikasi dari Google Authenticator saat log in ke server  
![Konfigurasi Google Authenticator](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Konfigurasi_Google_Authenticator/3.png)


  4. Edit file konfigurasi sshd_config  
![Konfigurasi Google Authenticator](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Konfigurasi_Google_Authenticator/4.png)


  5. Cari dan ubah baris ChallengeResponseAuthentication no menjadi yes pada file sshd_config agar Google Authenticator dapat mengirimkan *challenge* dan mengecek *response*-nya  
![Konfigurasi Google Authenticator](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Konfigurasi_Google_Authenticator/5.png)


  6. Konfigurasi Google Authenticator menggunakan perintah : google-authenticator. Kemudian jawab pertanyaan selanjutnya dengan y  
![Konfigurasi Google Authenticator](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Konfigurasi_Google_Authenticator/6.png)


  7. Catat *secret key* dan *emergency scratch codes* yang didapat, *secret key* digunakan untuk proses autentikasi dan *emergency scratch codes* digunakan untuk log in ke server dalam keadaan darurat (*smartphone* hilang). Jawab pertanyaan selanjutnya dengan y, pertanyaan yang lain dapat dijawab sesuai kebutuhan  
![Konfigurasi Google Authenticator](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Konfigurasi_Google_Authenticator/7.png)


  8. Restart SSH server  
![Konfigurasi Google Authenticator](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Konfigurasi_Google_Authenticator/8.png)


  9. Install aplikasi Google Authenticator pada *smartphone*, kemudian jalankan aplikasi yang akan menampilkan *view* seperti di gambar, pilih "Enter a provided key"  
<img src="https://raw.githubusercontent.com/ronayumik/PKSJ/master/Konfigurasi_Google_Authenticator/9.png" alt="Konfigurasi Google Authenticator" width="300"> 


  10. Masukkan nama akun terserah anda dan masukkan *secret key* yang didapatkan pada langkah 7. Terdapat 2 pilihan konfigurasi yang mengatur bagaimana token akan dihasilkan yaitu "Time-based" dan "Token-based". Dalam "Time-based" token yang dihasilkan akan valid dalam 30 detik, sedangkan dalam "Token-based" token yang dihasilkan akan valid hingga anda meminta token selanjutnya  
<img src="https://raw.githubusercontent.com/ronayumik/PKSJ/master/Konfigurasi_Google_Authenticator/10.png" alt="Konfigurasi Google Authenticator" width="300">


  11. Setiap kali anda ingin log in ke server via SSH, gunakan token yang didapatkan dari Google Authenticator pada *smartphone* anda  
<img src="https://raw.githubusercontent.com/ronayumik/PKSJ/master/Konfigurasi_Google_Authenticator/11.png" alt="Konfigurasi Google Authenticator" width="300">


  12. Seperti yang terlihat pada gambar, setiap kali ingin melakukan log in ke server via SSH dibutuhkan kode verifikasi. Pada contoh kasus seperti pada gambar, telah dicoba untuk memasukkan kode verifikasi dan password yang salah, kode verifikasi yang benar namun password salah dan kode verifikasi yang salah namun password benar. Karena tidak ada kombinasi yang benar maka IP yang mengakses akan di ban selama 30 detik  
![Konfigurasi Google Authenticator](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Konfigurasi_Google_Authenticator/12.png)


  13. Jika IP yang akan mengakses server masuk dalam daftar ban, maka ketika log in tidak akan dimintai kode verifikasi, sehingga tidak mungkin dapat log in karena selain password juga dibutuhkan kode verifikasi  
![Konfigurasi Google Authenticator](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Konfigurasi_Google_Authenticator/13.png)



#### 3. Langkah Konfigurasi SSH Server (agar tidak default)

  1. Untuk mengkonfigurasi, maka ubah file di /etc/ssh/sshd_config
![Konfigurasi SSH Server](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Openssh_Server/4.png)


  2. Mendisable Root Login dengan password. Login *root* hanya bisa login dengan menggunakan *SSH key*. Untuk membuatnya, maka diedit di bagian "PermitRootLogin yes" menjadi "PermitRootLogin without-password"  
![Konfigurasi SSH Server](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Openssh_Server/6.png)


  3. Mendisable Password Authentication, berarti hanya SSH dengan SSH key yang bisa dijalankan. Cari baris yang berisi "PasswordAuthentication" , dan ubah menjadi seperti berikut :  
![Konfigurasi SSH Server](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Openssh_Server/9.png)


  4. Setelah selesai, ketik baris berikut untuk mereload pengaturan SSH yang telah diubah & merestart SSH *service* :
![Konfigurasi SSH Server](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Openssh_Server/7.png)


  5. Jika settingannya sudah berhasil, jika anda SSH ke komputer server dengan menggunakan password ( SSH server belum terdaftar ), maka akan muncul sebagai berikut :
![Konfigurasi SSH Server](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Installing_Openssh_Server/10.png)


#### 4. Langkah Uji Penetrasi dengan SSH Brute Force Tools

Pada tahap ini, kami melakukan uji penetrasi (dengan *defense tools* di sisi server) dengan skenario yang berbeda untuk setiap *attack tools*, yaitu :

* **Patator Menyerang SSH Server yang Menggunakan Google Authenticator**

1. Dilakukan dengan perintah : patator ssh_login host=192.168.116.1 port=3022 user=ubuntu password=reverse  
Dapat dilihat seperti pada gambar, meskipun user dan password yang dimasukkan sudah benar, namun serangan yang dilakukan tetap gagal dengan pesan "Authentication failed"
![Patator & Google Authenticator](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Bruteforce_Attack%20(With%20Countermeasures)/patator_1.png)


2. Dilakukan dengan perintah : patator ssh_login host=192.168.116.1 port=3022 user=FILE0 password=FILE1 0=/root/Desktop/list_user_pass/username.txt 1=/root/Desktop/list_user_pass/password_list_true.txt -x ignore:fgrep='Authentication failed'  
Dapat dilihat seperti pada gambar, meskipun kombinasi user dan password yang benar terdapat pada *dictionary* yang diinputkan, namun serangan yang dilakukan tetap gagal (semua pesan serangan yang dihasilkan berisi "Authentication failed")
![Patator & Google Authenticator](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Bruteforce_Attack%20(With%20Countermeasures)/patator_2.png)



* **Ncrack Menyerang SSH Server yang Menggunakan SSH Key**
* **Hydra Menyerang SSH Server yang Menggunakan Fail2Ban**


## Kesimpulan dan Saran


