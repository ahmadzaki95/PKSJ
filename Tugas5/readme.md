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


## Intelligence Gathering Process

1. Untuk memulai analisa *exploit* apa saja yang bisa diterapkan, kita dapat melihat *list* port terbuka di Metasploitable. Lakukan perintah nmap -O < IP Metasploitable >  
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/Screenshot_InstalasiMetasploitable-RunningMetasploit/Screenshot_11.jpg)

2. Setelah selesai , kita dapat melihat detail OS metasploitable seperti versi kernel, dkk. Dari versi tersebut, kita dapat mencari *vulnerabilities* yang ada di website cvedetails.com    
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/Screenshot_InstalasiMetasploitable-RunningMetasploit/Screenshot_12.jpg)

3. Lorem Ipsum
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas5/Screenshot_InstalasiMetasploitable-RunningMetasploit/Screenshot_13.jpg)


## Analisa Hasil

Glastopf akan mencatat semua request yang dilakukan pada host, terlihat dari file log/glastopf.log , dari file tersebut dapat dianalisis untuk mengetahui apabila ada request yang malicious
![Analisa](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Analysis/1.jpg)

Glastopf juga memiliki database ( SQLite3 ) yang berisi data dummy dan event log yang dapat dilihat pada file db/glastopf.db , seperti pada gambar berikut :
![Analisa](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Analysis/2.jpg)
![Analisa](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Analysis/7.jpg)

* **Serangan Menggunakan Browser**

	Misal, pada satu skenario serangan jenis Path Traversal, kita mengakses {host}/x?id=../../../etc/passwd , attacker akan mendapatkan tampilan seperti ini :
![Analisa](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Analysis/3.jpg)

	Padahal, sebenarnya yang diakses adalah file dari data/virtualdocs/linux/etc/passwd (ssh dulu ke dalam docker dengan command : docker exec -it {nama docker} /bin/bash)
![Analisa](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Analysis/4.jpg)

	Contoh serangan jenis SQL Injection (URL yang dipakai {host}/.br/components/com_forum/editor/home.php?path=SELECT%20database()%20AND%201%3D1%20--%20) :  
![Analisa](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Screenshot_Analisis_Glastopf_Zap/33.jpg)

* **Serangan Menggunakan Zaproxy**

	1. Jalankan Zaproxy, masukkan alamat host yang ingin di attack  
![Analisa](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Screenshot_Analisis_Glastopf_Zap/0_1.jpg)

	2. Zaproxy akan menjalankan Spider agar secara otomatis dapat menemukan URL lain yang terdapat pada host  
![Analisa](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Screenshot_Analisis_Glastopf_Zap/0_2.jpg)

	3. Setelah Spider selesai, Zaproxy akan menjalan Active Scan untuk melakukan berbagai macam serangan terhadap host  
![Analisa](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Screenshot_Analisis_Glastopf_Zap/0_3.jpg)

	4. Window teratas menampilkan log dari Glasoptf yang di tail  
![Analisa](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Screenshot_Analisis_Glastopf_Zap/0_4.jpg)

	5. Serangan-serangan yang dilakukan oleh Zaproxy dikategorikan berdasarkan jenisnya untuk dianalisa lebih lanjut  
![Analisa](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Screenshot_Analisis_Glastopf_Zap/0_5.jpg)

	6. Active Scan telah berhasil dilakukan pada host  
![Analisa](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Screenshot_Analisis_Glastopf_Zap/34.jpg)

	7. Contoh salah satu serangan **Cross Site Scripting (XSS)**. XSS merupakan salah satu jenis serangan injeksi code (code injection attack). XSS dilakukan oleh penyerang dengan cara memasukkan kode HTML atau client script code lainnya ke suatu situs. ([sumber](https://id.wikipedia.org/wiki/XSS))  
![Analisa](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Screenshot_Analisis_Glastopf_Zap/1.jpg)

	8. Request dari Zaproxy sebagai berikut, dengan parameter body dan code yang diinject adalah '"< script >1< /script >"   
![Analisa](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Screenshot_Analisis_Glastopf_Zap/2.jpg)

	9. Response yang diberikan oleh Glastopf kepada Zaproxy, dapat dilihat bahwa untuk melakukan XSS dilakukan eksploitasi escape character yang tidak di filter dengan baik    
![Analisa](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Screenshot_Analisis_Glastopf_Zap/3.jpg)

	10. Request dari attacker dapat dilihat pada glastopf.log    
![Analisa](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Screenshot_Analisis_Glastopf_Zap/4.jpg)

	11. Serangan lain yang dilakukan adalah **Path Traversal**, dimana serangan ini dapat menampilkan / mengakses folder yang berada di luar folder / subfolder *web application* yang ada. Pada gambar ini, tampak Zaproxy sedang menyerang dengan memasukkan /index.php pada parameter principal , yang berarti jika berhasil seharusnya menampilkan isi file dari index.php  
![Analisa](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Screenshot_Analisis_Glastopf_Zap/5.jpg)

	12. Detail header request  
![Analisa](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Screenshot_Analisis_Glastopf_Zap/6.jpg)

	13. Tampak response dari request tersebut OK (kode : 200), namun tidak tampak bahwa server mereturn script php (tidak ada tag php / code php tampak dari gambar ), namun pengujian ini berhasil pada contoh kasus lain yang diberikan di awal subbab ini (Path Traversal ke /etc/passwd)  
![Analisa](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Screenshot_Analisis_Glastopf_Zap/7.jpg)

	14.  Malicious request tersebut tercatat pada glastopf.log  
![Analisa](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Screenshot_Analisis_Glastopf_Zap/8.jpg)

	15. Selanjutnya adalah **Remote OS Command Injection** , dimana tujuan dari attack ini adalah mengeksekusi perintah dalam OS host lewat *vulnerable* application, termasuk juga web application. Ini mungkin dilakukan dengan mengirimkan argumen beserta end command, diconcat dengan command OS. Pada kasus ini command sleep akan di-inject pada parameter id  
![Analisa](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Screenshot_Analisis_Glastopf_Zap/9.jpg)

	16. Detail header request  
![Analisa](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Screenshot_Analisis_Glastopf_Zap/10.jpg)

	17. Tampak response-nya tetap 200 OK , namun semestinya jika sukses, server akan tertidur / sleep selama 5 detik sebelum dapat mengembalikan response ke attacker  
![Analisa](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Screenshot_Analisis_Glastopf_Zap/11.jpg)

	18. Malicious request tersebut tercatat pada glastopf.log  
![Analisa](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Screenshot_Analisis_Glastopf_Zap/12.jpg)

	19. Serangan selanjutnya adalah **SQL injection - Oracle**, dengan memasukkan nilai %27 atau (') pada parameter id untuk memanfaatkan eksploitasi escape character yang tidak di filter dengan baik  
![Analisa](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Screenshot_Analisis_Glastopf_Zap/13.jpg)

	20. Detail header request  
![Analisa](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Screenshot_Analisis_Glastopf_Zap/14.jpg)

	21. Response dari server. Jika berhasil, ada error SQL (jika SQL statement salah), atau mengembalikan halaman yang telah ter-otorisasi, dalam kasus ini mengembalikan halaman HTML  
![Analisa](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Screenshot_Analisis_Glastopf_Zap/15.jpg)

	22. Malicious request tersebut tercatat pada glastopf.log  
![Analisa](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Screenshot_Analisis_Glastopf_Zap/16.jpg)

	23. Serangan selanjutnya adalah **SQL Injection** dengan parameter yang berbeda , dengan melakukan injeksi pada parameter layout dengan nilai 'AND '1' = '1'-- (menambahkan SQL statement yang nilainya selalu TRUE) 
![Analisa](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Screenshot_Analisis_Glastopf_Zap/17.jpg)

	24. Detail header request  
![Analisa](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Screenshot_Analisis_Glastopf_Zap/18.jpg)

	25. Response dari server. Jika berhasil, ada error SQL (jika SQL statement salah), atau mengembalikan halaman yang telah ter-otorisasi, dalam kasus ini mengembalikan halaman HTML  
![Analisa](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Screenshot_Analisis_Glastopf_Zap/19.jpg)

	26. Malicious request tersebut tercatat pada glastopf.log  
![Analisa](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Screenshot_Analisis_Glastopf_Zap/20.jpg)

	27. Serangan selanjutnya adalah **Application Error Disclosure** , dimana serangan ini bertujuan untuk menampilkan pesan error yang akan menampilkan informasi *vulnerable* seperti letak file yang terkena exception (misal, menganalisa framework apa yg digunakan dengan pattern file dan exception yang dihasilkan) ([sumber](https://www.acunetix.com/vulnerabilities/web/application-error-message))  
![Analisa](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Screenshot_Analisis_Glastopf_Zap/21.jpg)

	28. Detail header request  
![Analisa](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Screenshot_Analisis_Glastopf_Zap/22.jpg)

	29. Response dari server. Tampak bahwa Glastopf menampilkan error 'You have an error in your SQL syntax near ...' pada halaman view  
![Analisa](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Screenshot_Analisis_Glastopf_Zap/23.jpg)

	30. Malicious request tersebut tercatat pada glastopf.log  
![Analisa](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Screenshot_Analisis_Glastopf_Zap/24.jpg)

	31. Selanjutnya adalah **Directory Browsing**, yaitu serangan untuk me-list direktori apa saja yang ada didalam webserver tersebut. Hal ini tentu saja berbahaya, dimana attacker dapat melihat file-file yang memuat *vulnerable* information, seperti alur authentikasi (dari nama file), file-file backup, assets dll  
![Analisa](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Screenshot_Analisis_Glastopf_Zap/25.jpg)

	32. Detail header request  
![Analisa](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Screenshot_Analisis_Glastopf_Zap/26.jpg)

	33. Response dari server  
![Analisa](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Screenshot_Analisis_Glastopf_Zap/27.jpg)

	34. Malicious request tersebut tercatat pada glastopf.log  
![Analisa](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Screenshot_Analisis_Glastopf_Zap/28.jpg)

	35. Selanjutnya adalah [X-Frame Options Header Not Set](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-Frame-Options) , dimana jika server tidak mereturn X-Frame-Options, kemungkinan besar dapat diserang dengan [Clickjacking](http://javascript.info/tutorial/clickjacking) / UI Redress Attack  
![Analisa](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Screenshot_Analisis_Glastopf_Zap/29.jpg)

	36.  Detail header request  
![Analisa](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Screenshot_Analisis_Glastopf_Zap/30.jpg)

	37. Response dari server, dapat dilihat bahwa header response tidak memiliki parameter X-Frame-Options  
![Analisa](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Screenshot_Analisis_Glastopf_Zap/31.jpg)

	38. Request dari attacker tercatat pada glastopf.log  
![Analisa](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Screenshot_Analisis_Glastopf_Zap/32.jpg)


## Kesimpulan dan Saran

### Kesimpulan
1. Glastopf mampu menipu bots, namun belum tentu jika yang menyerang adalah manusia. Hacker dengan pengalaman menengah seharusnya tahu bahwa yang diserang adalah sebuah Honeypot (dari respon yang diberikan server)
2. Zaproxy adalah tools yang digunakan untuk mengetahui celah keamanan dari aplikasi web, berbagai serangan brute force seperti XSS, SQL Injection, Remote File Inclusion, dll akan dilakukan untuk mencari celah tersebut. Hasil serangan juga ditampilkan agar dapat dianalisa lebih lanjut

### Saran
**Login ke sistem dan memantau keadaan server setiap hari** 
*  Mengecek sukses/gagal login pada hari itu
*  rootkit checks (rkhunter, rootkitchck)

**Mencegah Bots dan Backdoors**
*  Memonitor semua koneksi yang keluar
*  Memonitor semua port yang terbuka
*  Memonitor request yang masuk
*  Menetapkan tindakan preventif apabila terdapat anomali pada network / sistem

