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

* **Serangan Menggunakan Browser**

	Misal, pada satu skenario serangan jenis Path Traversal, kita mengakses {host}/x?id=../../../etc/passwd , attacker akan mendapatkan tampilan seperti ini :
![Analisa](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Analysis/3.png)

	Padahal, sebenarnya yang diakses adalah file dari data/virtualdocs/linux/etc/passwd (ssh dulu ke dalam docker dengan command : docker exec -it {nama docker} /bin/bash)
![Analisa](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Analysis/4.png)

	Contoh serangan jenis SQL Injection (URL yang dipakai {host}/.br/components/com_forum/editor/home.php?path=SELECT%20database()%20AND%201%3D1%20--%20) :  
![Analisa](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Screenshot_Analisis_Glastopf_Zap/33.png)

* **Serangan Menggunakan Zaproxy**

	1. Jalankan Zaproxy, masukkan alamat host yang ingin di attack  
![Analisa](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Screenshot_Analisis_Glastopf_Zap/0_1.png)

	2. Zaproxy akan menjalankan Spider agar secara otomatis dapat menemukan URL lain yang terdapat pada host  
![Analisa](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Screenshot_Analisis_Glastopf_Zap/0_2.png)

	3. Setelah Spider selesai, Zaproxy akan menjalan Active Scan untuk melakukan berbagai macam serangan terhadap host  
![Analisa](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Screenshot_Analisis_Glastopf_Zap/0_3.png)

	4. Window teratas menampilkan log dari Glasoptf yang di tail  
![Analisa](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Screenshot_Analisis_Glastopf_Zap/0_4.png)

	5. Serangan-serangan yang dilakukan oleh Zaproxy dikategorikan berdasarkan jenisnya untuk dianalisa lebih lanjut  
![Analisa](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Screenshot_Analisis_Glastopf_Zap/0_5.png)

	6. Active Scan telah berhasil dilakukan pada host  
![Analisa](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Screenshot_Analisis_Glastopf_Zap/34.png)

	7. Contoh salah satu serangan Cross Site Scripting (XSS). XSS merupakan salah satu jenis serangan injeksi code (code injection attack). XSS dilakukan oleh penyerang dengan cara memasukkan kode HTML atau client script code lainnya ke suatu situs. ([sumber](https://id.wikipedia.org/wiki/XSS))  
![Analisa](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Screenshot_Analisis_Glastopf_Zap/1.png)

	8. Request dari Zaproxy sebagai berikut, dengan parameter body dan code yang diinject adalah '"< script >1< /script >"   
![Analisa](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Screenshot_Analisis_Glastopf_Zap/2.png)

	9. Response yang diberikan oleh Glastopf kepada Zaproxy, dapat dilihat bahwa untuk melakukan XSS dilakukan eksploitasi escape character yang tidak di filter dengan baik    
![Analisa](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Screenshot_Analisis_Glastopf_Zap/3.png)

	10. Request dari attacker dapat dilihat pada glastopf.log    
![Analisa](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Screenshot_Analisis_Glastopf_Zap/4.png)

	11. Serangan lain yang terlihat adalah Path Traversal Attack, dimana serangan ini dapat menampilkan / mengakses folder yang berada di luar folder/subfolder *web application* yang ada. Pada gambar ini, tampak Zaproxy sedang menyerang dengan memasukkan parameter /index.php , yang berarti jika berhasil seharusnya menampilkan isi file dari index.php  
![Analisa](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Screenshot_Analisis_Glastopf_Zap/5.png)

	12. Detail Header Request pada gambar berikut :  
![Analisa](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Screenshot_Analisis_Glastopf_Zap/6.png)

	13. Tampak response dari request tersebut OK (kode : 200), namun tidak tampak bahwa server mereturn script php (tidak ada tag php / code php tampak dari gambar ), namun pengujian ini berhasil pada contoh awal yang diberikan di awal subbab ini (path traversal ke /etc/passwd)  
![Analisa](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Screenshot_Analisis_Glastopf_Zap/7.png)

	14.  Berikut adalah log akses dari glastopf   
![Analisa](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Screenshot_Analisis_Glastopf_Zap/8.png)

	15. Selanjutnya adalah **Remote OS Command Injection** , dimana tujuan dari attack ini adalah mengeksekusi perintah dalam OS host lewat *vulnerable* application, termasuk juga web application. Ini mungkin dilakukan dengan mengirimkan argumen beserta end command, diconcat dengan command OS (misal : ls pada linux)  
![Analisa](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Screenshot_Analisis_Glastopf_Zap/9.png)

	16. Detail header serangan  
![Analisa](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Screenshot_Analisis_Glastopf_Zap/10.png)

	17. Tampak hasilnya tetap 200 OK , namun semestinya jika sukses, perintah ini tidak mengembalikan perintah apapun, dan selanjutnya server tidak akan lagi dapat diakses karena sudah dalam kondisi sleep.  
![Analisa](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Screenshot_Analisis_Glastopf_Zap/11.png)

	18. Log dari Glastopf seperti gambar berikut :  
![Analisa](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Screenshot_Analisis_Glastopf_Zap/12.png)

	19. Serangan selanjutnya adalah SQL injection untuk DB Oracle, yaitu memasukkan nilai %27 (') pada parameter id  
![Analisa](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Screenshot_Analisis_Glastopf_Zap/13.png)

	20. Detail header serangan  
![Analisa](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Screenshot_Analisis_Glastopf_Zap/14.png)

	21. Response dari server. Jika berhasil, ada error SQL (jika perkiraan SQL salah), atau mengembalikan halaman yang telah ter-otorisasi, dalam kasus ini mengembalikan halaman HTML (zaproxy mendeteksi bahwa SQL injection berhasil)  
![Analisa](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Screenshot_Analisis_Glastopf_Zap/15.png)

	22. Log dari glastopf  
![Analisa](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Screenshot_Analisis_Glastopf_Zap/16.png)

	23. Serangan selanjutnya adalah SQL injection dengan parameter yang berbeda , dimana mengakses semua file php di folder webserver dan menginject nilai layout dengan parameter 'and '1' = '1'  
![Analisa](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Screenshot_Analisis_Glastopf_Zap/17.png)

	24. Detail Header Request  
![Analisa](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Screenshot_Analisis_Glastopf_Zap/18.png)

	25. Response dari Glastopf, kurang lebih kemungkinannya sama dengan nomor 21  
![Analisa](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Screenshot_Analisis_Glastopf_Zap/19.png)

	26. Log dari file glastopf  
![Analisa](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Screenshot_Analisis_Glastopf_Zap/20.png)

	27. Serangan selanjutnya adalah Application error disclosure [penjelasan](https://www.acunetix.com/vulnerabilities/web/application-error-message), dimana ini bertujuan untuk menampilkan pesan error yang akan menampilkan informasi *vulnerable* seperti letak file yang terkena exception ( misal, menganalisa framework apa yg digunakan dengan pattern file dan exception yang dihasilkan)   
![Analisa](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Screenshot_Analisis_Glastopf_Zap/21.png)

	28. Detail header request  
![Analisa](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Screenshot_Analisis_Glastopf_Zap/22.png)

	29. Response yang dihasilkan (200 OK). Tampak bahwa Glastopf mereturn error 'You have an error in your SQL syntax near ...' namun tidak menampilkan error lain yang semestinya dimunculkan jika server adalah benar-benar server (bukan honeypot) , seperti error/warning khas PHP
![Analisa](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Screenshot_Analisis_Glastopf_Zap/23.png)

	30. Log akses dari Glastopf seperti berikut  
![Analisa](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Screenshot_Analisis_Glastopf_Zap/24.png)

	31. Selanjutnya adalah directory browsing, yaitu serangan untuk me-list direktori apa saja yang ada didalam webserver tersebut. Hal ini tentu saja berbahaya, dimana attacker dapat melihat file-file yang memuat *vulnerable* information, seperti alur authentikasi (dari nama file), file-file backup, assets dll.  
![Analisa](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Screenshot_Analisis_Glastopf_Zap/25.png)

	32. Detail header request  
![Analisa](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Screenshot_Analisis_Glastopf_Zap/26.png)

	33. Response yang dihasilkan.  
![Analisa](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Screenshot_Analisis_Glastopf_Zap/27.png)

	34. Log pada file Glastopf  
![Analisa](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Screenshot_Analisis_Glastopf_Zap/28.png)

	35. Selanjutnya adalah [X-Frame options Header](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-Frame-Options) [not set](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-Frame-Options), dimana jika server tidak mereturn X-Frame-Options, kemungkinan besar dapat diattack dengan [Clickjacking](http://javascript.info/tutorial/clickjacking) / Ui Redress attack.      
![Analisa](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Screenshot_Analisis_Glastopf_Zap/29.png)

	36.  Detail header request 
![Analisa](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Screenshot_Analisis_Glastopf_Zap/30.png)

	37. Response dari server  
![Analisa](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Screenshot_Analisis_Glastopf_Zap/31.png)

	38. Log dalam glastopf  
![Analisa](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Screenshot_Analisis_Glastopf_Zap/32.png)


## Kesimpulan dan Saran

* 

