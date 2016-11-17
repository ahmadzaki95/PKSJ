# **Tugas 4 PKSJ - Analisa Honeypot (Glastopf) dan Zaproxy**


## Pendahuluan

Tugas ini dibuat untuk menyelesaikan Tugas 4 yaitu "Analisa Honeypot : Glastopf" pada matakuliah Perancangan Keamanan & Sistem Jaringan (PKSJ) Semester Ganjil 2016/2017, Teknik Informatika ITS, Surabaya
 
Anggota Kelompok
- Ardi Nusawan      5113100096
- Gian Sebastian A. 5113100132
- Ronauli Sidabukke 5113100142


## Dasar Teori

**1. Honeypot**

**Honeypot** adalah security resource yang yang sengaja dibuat untuk diselidiki, diserang, atau dikompromikan (Firrar Utdirartatmo, 2005:1). Pada umumnya Honeypot berupa komputer, data, atau situs jaringan yang terlihat seperti bagian dari jaringan, tapi sebenarnya terisolasi dan dimonitor. ([sumber](www.kajianpustaka.com/2014/07/pengertian-dan-klasifikasi-honeypot.html))

**2. Our Arsenal**
 
* **Glastopf** adalah sebuah web honeypot yang akan mengemulasikan error-error yang umum terjadi pada aplikasi web. Tujuannya adalah untuk memancing hacker yang sering menggunakan tool untuk mengotomatisasi proses hacking. Ketika Glastopf sudah berjalan dan dibuka melalui web browser, akan ada sebuah form login, beberapa baris kata, dan sebuah form untuk menulis komentar. ([sumber](http://baskoroadi.web.id/page/2/))
* **Zaproxy**, atau Zed Attack Proxy adalah alat penetrasi testing terpadu untuk menemukan kerentanan dalam aplikasi web. Hal ini dirancang untuk digunakan oleh orang-orang dengan berbagai pengalaman keamanan dan dengan demikian sangat ideal untuk para pengembang dan pentester yang baru untuk melakukan kegiatan pentest. ZAP menyediakan scanner otomatis serta satu set alat yang memungkinkan untuk menemukan kerentanan keamanan website secara manual. ([sumber](http://www.binushacker.net/hacker-tools-zed-attack-proxy.html))


## Langkah Instalasi Glastopf dengan menggunakan Docker

Untuk instalasi Docker, kami merujuk dari tutorial DigitalOcean ([ini](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-16-04)) , dengan tahapan berikut :

1. Update *package database* dengan perintah : apt-get update  

2. Tambahkan GPG Key untuk Official Docker Repository dengan perintah : sudo apt-key adv --keyserver hkp://p80.pool.sks-keyservers.net:80 --recv-keys 58118E89F3A912897C070ADBF76221572C52609D  
 ![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Installing_Glastopf/1.png)

3. Dan tambahkan repository Docker ke daftar sources APT dng perintah : sudo apt-add-repository 'deb https://apt.dockerproject.org/repo ubuntu-xenial main'  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Installing_Glastopf/2.png)

4. Kembali update *package database* : sudo apt-get update  

5. Install docker dengan perintah : sudo apt-get install docker-engine  
 ![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Installing_Glastopf/4.png)

6. Agar docker dapat digunakan oleh username anda tanpa harus mengganti *prilege* ke root , masukkan perintah berikut : sudo usermod -aG docker $(whoami)  

7. Reboot / restart server  

8. Untuk mengetes apakah docker sudah dapat berjalan dengan benar ,   dapat dijalankan perintah : docker run hello-world. Jika berhasil, tampilannya akan seperti berikut :  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Installing_Glastopf/5.png)

    Jika sudah berhasil, maka kita lanjutkan dengan instalasi Glastopf, dengan merujuk pada dokumentasi dari Glastopf ([berikut](http://www.binushacker.net/hacker-tools-zed-attack-proxy.html))  

9. Clone file dari Github Glastopf dengan perintah : git clone https://github.com/mushorg/glastopf.git atau git@github.com:mushorg/glastopf.git  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Installing_Glastopf/6.png)

10. cd ke directory glastopf dengan perintah : cd glastopf  

11. Run perintah berikut : docker build --rm --tag glastopf  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Installing_Glastopf/7.png)

    Perintah ini akan menarik / *pull* file docker glastopf , sehingga akan berlangsung cukup lama tergantung kualitas kecepatan internet anda. Jika berhasil , maka akan muncul seperti berikut :  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Installing_Glastopf/8.png)

12. Jika sudah selesai , buat sebuah folder bebas, misal pada contoh ini nama foldernya adalah honeypot dengan perintah : mkdir {nama folder}  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Installing_Glastopf/9.png)

13. Untuk menjalankan docker Glastopf , kita masukkan perintah berikut : docker run --detach --publish 80:80 --volume honeypot:/opt/honeypot glastopf  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Installing_Glastopf/10.png)

14. Untuk melihat apakah sudah benar berjalan atau tidak, anda dapat melihat lewat browser dengan memasukkan alamat : localhost (karena portnya 80 sehingga tidak perlu dimasukkan portnya). Jika sudah benar, maka akan muncul halaman seperti berikut . Jika anda refresh, maka konten didalamnya juga ikut berubah.  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Installing_Glastopf/11.png)


## Langkah Instalasi Zaproxy

Untuk instalasi Zaproxy sendiri cukup mudah, untuk Windows sudah ada *installer* yang mudah diinstal. Untuk OS Linux, pastikan di pc anda sudah terinstall Java 7 atau keatas. Untuk instalasi pada Windows, dapat mengikuti tahapan berikut :

1. Download file installer dari halaman [wiki Zaproxy di Github](https://github.com/zaproxy/zaproxy/wiki/Downloads) , atau klik [link berikut](https://github.com/zaproxy/zaproxy/releases/download/2.5.0/ZAP_2.5.0_Windows.exe)  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Installing_Zaproxy/1.png)

2. Jika sudah selesai, *double* klik pada installer Zaproxy dan klik Next Next seperti biasa:  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Installing_Zaproxy/2.png)
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Installing_Zaproxy/3.png)

3. Setelah selesai, anda dapat melihat launcher / icon Zaproxy pada menu di  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Installing_Zaproxy/4.png)


## Analisa Hasil

Glastopf akan mencatat semua request yang dilakukan pada host, terlihat dari file log/glastopf.log , dari file tersebut dapat dianalisis untuk mengetahui apabila ada request yang malicious
![Analisa](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Analysis/1.png)

Glastopf juga memiliki database ( SQLite3 ) yang berisi data dummy dan event log yang dapat dilihat pada file db/glastopf.db , seperti pada gambar berikut :
![Analisa](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Analysis/2.png)
![Analisa](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Analysis/7.png)

* **Contoh Serangan Menggunakan Browser**

	Misal, pada satu skenario serangan jenis Path Traversal, kita mengakses {host}/x?id=../../../etc/passwd , attacker akan mendapatkan tampilan seperti ini :
![Analisa](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Analysis/3.png)

	Padahal, sebenarnya yang diakses adalah file dari data/virtualdocs/linux/etc/passwd (ssh dulu ke dalam docker dengan cara : docker exec -it {nama docker} /bin/bash)
![Analisa](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Analysis/4.png)

	Contoh serangan jenis SQL Injection :  
![Analisa](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Screenshot_Analisis_Glastopf_Zap/33.png)

* **Serangan Menggunakan Zaproxy**



## Kesimpulan dan Saran

* 
