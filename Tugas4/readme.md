# **Tugas 3 PKSJ - Analisa Malware Menggunakan Cuckoo Sandbox**


## Pendahuluan

Tugas ini dibuat untuk menyelesaikan Tugas 3 yaitu "Analisa Malware Menggunakan Cuckoo Sandbox" pada matakuliah Perancangan Keamanan & Sistem Jaringan (PKSJ) Semester Ganjil 2016/2017, Teknik Informatika ITS, Surabaya
 
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

7. Reboot / restart server .

8. Untuk mengetes apakah docker sudah dapat berjalan dengan benar ,   dapat dijalankan perintah : docker run hello-world. Jika berhasil, tampilannya akan seperti berikut :
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Installing_Glastopf/5.png)

Jika sudah berhasil, maka kita lanjutkan dengan instalasi Glastopf, dengan merujuk pada dokumentasi dari Glastopf ([berikut](http://www.binushacker.net/hacker-tools-zed-attack-proxy.html))

9. Clone file dari Github Glastopf dengan perintah : git clone https://github.com/mushorg/glastopf.git atau git@github.com:mushorg/glastopf.git
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Installing_Glastopf/6.png)

10. cd ke directory glastopf dengan perintah : cd glastopf

11. Run perintah berikut : docker build --rm --tag glastopf .
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

Untuk instalasi Zaproxy sendiri cukup mudah, untuk Windows sudah ada *installer* yang mudah diinstal. Untuk OS Linux, pastikan di pc anda sudah terinstall Java 7 atau keatas. Untuk instalasi pada windows, dapat mengikuti tahapan berikut :

1. Download file installer dari halaman ([wiki Zaproxy di Github](https://github.com/zaproxy/zaproxy/wiki/Downloads)) , atau klik ([link berikut](https://github.com/zaproxy/zaproxy/releases/download/2.5.0/ZAP_2.5.0_Windows.exe))
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Installing_Zaproxy/1.png)

2. Jika sudah selesai, *double* klik pada installer Zaproxy dan klik Next Next seperti biasa:
 ![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Installing_Zaproxy/2.png)

 ![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Installing_Zaproxy/3.png)

3. Setelah selesai, anda dapat melihat launcher / icon Zaproxy pada menu di 
![Install](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas4/Installing_Glastopf/4.png)


## Analisis Malware

* **APT_military procurement.pdf**

1. Berikut adalah keterangan mengenai malicious PDF yang dianalisis   
![Analisis APT_military procurement.pdf](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_analyses/22/shots/1.PNG)

2. Berikut adalah rangkuman file-file yang diakses/dibuat/dihapus oleh malware  
![Analisis APT_military procurement.pdf](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_analyses/22/shots/2.PNG)

3. Daftar Dropped Files dari langkah 2 didapatkan dari analysis.log  
![Analisis APT_military procurement.pdf](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_analyses/22/shots/3.PNG)

4. Malware hanya bekerja pada localhost, sehingga analisa network tidak ditampilkan  
![Analisis APT_military procurement.pdf](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_analyses/22/shots/4.PNG)

5. Berikut adalah daftar lengkap dari file, folder dan registry yang diakses/dibuat/dihapus oleh malware  
![Analisis APT_military procurement.pdf](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_analyses/22/shots/5.PNG)

	![Analisis APT_military procurement.pdf](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_analyses/22/shots/6.PNG)

	![Analisis APT_military procurement.pdf](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_analyses/22/shots/7.PNG)

	![Analisis APT_military procurement.pdf](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_analyses/22/shots/8.PNG)

6. Mutex yang dibuat oleh malware (biasanya mutex dibuat oleh malware untuk mencegah dua instansi malware berjalan bersamaan)  
![Analisis APT_military procurement.pdf](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_analyses/22/shots/9.PNG)

7. Beberapa hasil screenshot dari Cuckoo pada Guest OS saat menjalankan malware  
![Analisis APT_military procurement.pdf](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_analyses/22/shots/0001.jpg)
![Analisis APT_military procurement.pdf](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_analyses/22/shots/0002.jpg)
![Analisis APT_military procurement.pdf](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_analyses/22/shots/0003.jpg)
![Analisis APT_military procurement.pdf](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_analyses/22/shots/0004.jpg)
![Analisis APT_military procurement.pdf](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_analyses/22/shots/0005.jpg)

8. Cuckoo mengirimkan malware ke website [VirusTotal](https://www.virustotal.com/) untuk mendeteksi jenis malware (dibantu oleh berbagai software anti-virus)  
![Analisis APT_military procurement.pdf](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_analyses/22/shots/10.PNG)

9. Dari berbagai hasil deteksi software anti-virus, akan kami ambil 2 contoh hasil deteksi malware dari 2 software anti-virus yaitu Microsoft dan Symantec   
![Analisis APT_military procurement.pdf](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_analyses/22/shots/11.PNG)

	Jenis malware yang terdeteksi oleh Microsoft adalah "Exploit:Win32/Pdfjsc.XD", malware ini termasuk jenis dari malicious PDF yang mengeksploitasi kerentanan dalam Adobe Acrobat dan Adobe Reader, malware ini bekerja dengan mengunduh dan menjalankan file sewenang-wenang ([sumber](http://www.microsoft.com/security/portal/threat/encyclopedia/entry.aspx?Name=Exploit%3aWin32%2fPdfjsc))  
    
    Jenis malware yang terdeteksi oleh Symantec adalah "Trojan.Pidief", malware ini termasuk jenis Trojan yang mengeksploitasi kerentanan dalam Adobe Acrobat dan Adobe Reader, malware ini bekerja dengan mengunduh malware tambahan ke komputer yang terinfeksi ([sumber](https://www.symantec.com/security_response/writeup.jsp?docid=2009-121708-1022-99))

* **APT_ATT11990.pdf**

1. Berikut adalah keterangan mengenai malicious PDF yang dianalisis  
![Analisis APT_ATT11990.pdf](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_analyses/23/shots/1.PNG)

2. Berikut adalah rangkuman file-file yang diakses/dibuat/dihapus oleh malware  
![Analisis APT_ATT11990.pdf](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_analyses/23/shots/2.PNG)

3. Malware hanya bekerja pada localhost, sehingga analisa network tidak ditampilkan  
![Analisis APT_ATT11990.pdf](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_analyses/23/shots/3.PNG)

4. Berikut adalah daftar lengkap dari file, folder dan registry yang diakses/dibuat/dihapus oleh malware  
![Analisis APT_ATT11990.pdf](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_analyses/23/shots/4.PNG)

	![Analisis APT_ATT11990.pdf](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_analyses/23/shots/5.PNG)

5. Beberapa hasil screenshot dari Cuckoo pada Guest OS saat menjalankan malware  
![Analisis APT_ATT11990.pdf](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_analyses/23/shots/0001.jpg)
![Analisis APT_ATT11990.pdf](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_analyses/23/shots/0002.jpg)
![Analisis APT_ATT11990.pdf](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_analyses/23/shots/0003.jpg)
![Analisis APT_ATT11990.pdf](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_analyses/23/shots/0004.jpg)
![Analisis APT_ATT11990.pdf](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_analyses/23/shots/0005.jpg)

6. Cuckoo mengirimkan malware ke website [VirusTotal](https://www.virustotal.com/) untuk mendeteksi jenis malware (dibantu oleh berbagai software anti-virus)  
![Analisis APT_ATT11990.pdf](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_analyses/23/shots/6.PNG)

7. Dari berbagai hasil deteksi software anti-virus, akan kami ambil 2 contoh hasil deteksi malware dari 2 software anti-virus yaitu Microsoft dan Symantec  
![Analisis APT_ATT11990.pdf](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_analyses/23/shots/7.PNG)

	Jenis malware yang terdeteksi oleh Microsoft adalah "Exploit:JS/ShellCode.AG", malware ini termasuk jenis objek JavaScript yang melakukan tindakan malicious, malware ini bekerja dengan menjalankan kode malicious sewenang-wenang ([sumber](http://www.microsoft.com/security/portal/threat/encyclopedia/entry.aspx?Name=Exploit:JS/ShellCode.gen))  
    
    Jenis malware yang terdeteksi oleh Symantec adalah "Bloodhound.Pdexe", malware ini termasuk jenis dari malicious PDF yang didalamnya mengandung embedded executable file yang bersifat malicious ([sumber](https://www.symantec.com/security_response/writeup.jsp?docid=2008-092604-1756-99))

* **100621.pdf**

1. Berikut adalah keterangan mengenai malicious PDF yang dianalisis  
![Analisis 100621.pdf](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_analyses/24/shots/1.PNG)

2. Berikut adalah rangkuman file-file yang diakses/dibuat/dihapus oleh malware  
![Analisis 100621.pdf](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_analyses/24/shots/2.PNG)

3. Malware hanya bekerja pada localhost, sehingga analisa network tidak ditampilkan  
![Analisis 100621.pdf](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_analyses/24/shots/3.PNG)

4. Berikut adalah daftar lengkap dari file, folder dan registry yang diakses/dibuat/dihapus oleh malware  
![Analisis 100621.pdf](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_analyses/24/shots/4.PNG)

	![Analisis 100621.pdf](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_analyses/24/shots/5.PNG)

5. Beberapa hasil screenshot dari Cuckoo pada Guest OS saat menjalankan malware  
![Analisis 100621.pdf](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_analyses/24/shots/0001.jpg)
![Analisis 100621.pdf](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_analyses/24/shots/0002.jpg)
![Analisis 100621.pdf](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_analyses/24/shots/0003.jpg)
![Analisis 100621.pdf](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_analyses/24/shots/0004.jpg)
![Analisis 100621.pdf](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_analyses/24/shots/0005.jpg)

6. Cuckoo mengirimkan malware ke website [VirusTotal](https://www.virustotal.com/) untuk mendeteksi jenis malware (dibantu oleh berbagai software anti-virus)  
![Analisis 100621.pdf](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_analyses/24/shots/6.PNG)

7. Dari berbagai hasil deteksi software anti-virus, akan kami ambil 2 contoh hasil deteksi malware dari 2 software anti-virus yaitu Avast dan Baidu  
![Analisis 100621.pdf](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_analyses/24/shots/7.PNG)

	Jenis malware yang terdeteksi oleh Avast adalah "JS:Pdfka-gen [Expl]", malware ini termasuk jenis objek JavaScript Trojan yang melakukan tindakan malicious, malware ini bekerja dengan menjalankan kode malicious dan file registery sewenang-wenang untuk merusak komputer yang terinfeksi ([sumber](http://fixingcomputervirus.blogspot.sg/2013/02/best-way-to-remove-jspdfka-genexpl.html))  
    
    Jenis malware yang terdeteksi oleh Baidu adalah "JS.Exploit.pdfka.cg", malware ini termasuk jenis objek JavaScript yang melakukan tindakan malicious, malware ini memanfaatkan stack-based buffer overflow di Adobe Reader and Adobe Acrobat untuk menjalankan kode malicious sewenang-wenang ([sumber](http://www.virusradar.com/en/JS_Exploit.Pdfka/description))

* **IPR in China FINAL.pdf**

1. Berikut adalah keterangan mengenai malicious PDF yang dianalisis  
![Analisis IPR in China FINAL.pdf](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_analyses/25/shots/1.PNG)

2. Berikut adalah rangkuman file-file yang diakses/dibuat/dihapus oleh malware  
![Analisis IPR in China FINAL.pdf](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_analyses/25/shots/2.PNG)

3. Malware hanya bekerja pada localhost, sehingga analisa network tidak ditampilkan  
![Analisis IPR in China FINAL.pdf](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_analyses/25/shots/3.PNG)

4. Berikut adalah daftar lengkap dari file, folder dan registry yang diakses/dibuat/dihapus oleh malware  
![Analisis IPR in China FINAL.pdf](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_analyses/25/shots/4.PNG)

	![Analisis IPR in China FINAL.pdf](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_analyses/25/shots/5.PNG)

5. Beberapa hasil screenshot dari Cuckoo pada Guest OS saat menjalankan malware  
![Analisis IPR in China FINAL.pdf](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_analyses/25/shots/0001.jpg)
![Analisis IPR in China FINAL.pdf](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_analyses/25/shots/0002.jpg)
![Analisis IPR in China FINAL.pdf](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_analyses/25/shots/0003.jpg)
![Analisis IPR in China FINAL.pdf](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_analyses/25/shots/0004.jpg)
![Analisis IPR in China FINAL.pdf](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_analyses/25/shots/0005.jpg)

5. Cuckoo mengirimkan malware ke website [VirusTotal](https://www.virustotal.com/) untuk mendeteksi jenis malware (dibantu oleh berbagai software anti-virus)  
![Analisis IPR in China FINAL.pdf](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_analyses/25/shots/6.PNG)

6. Dari berbagai hasil deteksi software anti-virus, akan kami ambil 2 contoh hasil deteksi malware dari 2 software anti-virus yaitu Microsoft dan Symantec  
![Analisis IPR in China FINAL.pdf](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_analyses/25/shots/7.PNG)

	Jenis malware yang terdeteksi oleh Microsoft adalah "Exploit:JS/Mult.CM", malware ini termasuk jenis objek JavaScript yang melakukan tindakan malicious, malware ini bekerja dengan mengunduh malware atau software lain yang tidak diinginkan ke komputer yang terinfeksi ([sumber](http://www.microsoft.com/security/portal/threat/encyclopedia/entry.aspx?name=EXPLOIT:JS/MULT.CM))  
    
    Jenis malware yang terdeteksi oleh Symantec adalah "Bloodhound.Flash.9", malware ini mengeksploitasi kerentanan dalam Adobe Flash Player untuk melakukan tindakan malicious atau tindakan yang tidak diinginkan ([sumber](https://www.symantec.com/security_response/writeup.jsp?docid=2011-050208-1645-99))

## Kesimpulan dan Saran

* Dengan menggunakan Cuckoo Sandbox, analisis malware dapat dilakukan dengan mudah dan aman. Pengguna tidak perlu lagi menggunakan data binary untuk menganalisis malware, semua analisa telah dilakukan oleh Cuckoo Sandbox dengan GUI yang interaktif dan mudah dipahami. Selain dapat menganalisa perilaku dari malware, Cuckoo Sandbox juga mengupload malware ke VirusTotal, sehingga pengguna dapat mengetahui jenis dari malware tersebut (dapat dicari informasi lebih lanjut mengenai jenis malware tersebut)
* Untuk menghindari atau mengurangi resiko terkena malware, pastikan agar selalu memperbaharui versi dari software, anti-virus, OS dan mengunduh file hanya dari sumber yang terpercaya
*  Untuk mengurangi resiko terserang malicious PDF, dapat dilakukan beberapa hal berikut :
	*  Matikan plugin PDF untuk web browser
	*  Konfigurasi PDF reader untuk tidak menjalankan file lampiran yang bertipe non-PDF dengan aplikasi eksternal / aplikasi lain
	*  Menonaktifkan Acrobat JavaScript di Adobe Reader karena banyak malware yang menggunakan fitur ini untuk mengeksekusi kode malicious
	*  Menggunakan fitur Protected Mode dan Protected View yang membuka PDF dalam sebuah "sandbox" (mengisolasi PDF dari komputer dan dunia luar)
