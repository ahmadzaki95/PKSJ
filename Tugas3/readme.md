# **Tugas 3 PKSJ - Analisa Malware Menggunakan Cuckoo Sandbox**


## Pendahuluan

Tugas ini dibuat untuk menyelesaikan Tugas 3 yaitu "Analisa Malware Menggunakan Cuckoo Sandbox" pada matakuliah Perancangan Keamanan & Sistem Jaringan (PKSJ) Semester Ganjil 2016/2017, Teknik Informatika ITS, Surabaya
 
Anggota Kelompok
- Ardi Nusawan      5113100096
- Gian Sebastian A. 5113100132
- Ronauli Sidabukke 5113100142


## Dasar Teori

**1. Cuckoo Sandbox**

**Cuckoo Sandbox** dalam tiga kata, adalah sistem analisa malware. Cuckoo dapat melakukan analisa perilaku dan jenis malware dengan menjalankan malware tersebut dalam sebuah sistem yang akan menjadi *sandbox* (biasanya virtual) yang akan dimonitoring perilakunya. Analisa dapat dilakukan pada tipe file executables Windows, file DLL, dokumen PDF, dokumen Office, halaman website, script PHP, dll. Cuckoo dapat menampilkan analisa API calls yang dijalankan proses yang terinfeksi malware, file apa saja yang diakses/dibuat/dihapus oleh malware, menyimpan memori dan network dumps dari proses malware, bahkan screenshoot dari OS ketika malware dijalankan. ([sumber](https://www.cuckoosandbox.org/))

**2. Malware yang dianalisis**
 
* **PDF** atau Portable Document Format adalah sebuah format file yang diciptakan oleh Adobe System, Inc. File jenis ini sangat populer dan banyak digunakan terutama dalam bentuk e-book karena dapat dengan mudah dibuka menggunakan berbagai aplikasi gratis. Website resmi Adobe menyatakan : "PDFs can contain links and buttons, form fields, audio, video, and business logic", disini berarti konten tersebut bisa saja memuat *malicious program* yang membahayakan pembaca PDF tersebut. ([sumber](https://acrobat.adobe.com/us/en/why-adobe/about-adobe-pdf.html))
* **Sumber Malware** yang kami gunakan berasal dari [Contagio](http://contagiodump.blogspot.co.id/), merupakan website yang kontennya adalah sampel-sampel dari berbagai malware. Untuk membuka zip dari file malware tersebut dibutuhkan password yang didapatkan dengan cara mengkontak pemilik web melalui email. Link yang digunakan untuk mengunduh file malware sedang diperbaharui dan untuk sementara file malware dapat dicari pada [Dropbox](https://www.dropbox.com/sh/i6ed6v32x0fp94z/AAAQvOsOvbWrOs8T3_ZTXqQya?dl=0) milik pemilik web.
* **APT_military procurement.pdf** adalah malicious PDF pertama yang kami analisis, file terletak dalam 30APTpdfcuckoo.zip ([sumber](https://www.dropbox.com/sh/i6ed6v32x0fp94z/AAB7nUZTiI6Xk0i6Zg663kDga/CVE?dl=0))
* **APT_ATT11990.pdf** adalah malicious PDF kedua yang kami analisis, file terletak dalam 30APTpdfcuckoo.zip ([sumber](https://www.dropbox.com/sh/i6ed6v32x0fp94z/AAB7nUZTiI6Xk0i6Zg663kDga/CVE?dl=0))
* **100621.pdf** adalah malicious PDF ketiga yang kami analisis, file terletak dalam ^CVE-2010-1297 PDF 2010-06-21 E3F5EF4FA17B4E08…73728 100621.zip ([sumber](https://www.cuckoosandbox.org/))
* **IPR in China FINAL.pdf** adalah malicious PDF keempat yang kami analisis, file terletak dalam CVE-2009-0927 CVE-2007-5659 PDF 2010-04-02 C497C…in China final.zip ([sumber](https://www.cuckoosandbox.org/))


## Langkah Instalasi Cuckoo Sandbox

1. Download File Zip dari ([sini](https://github.com/cuckoosandbox/cuckoo)) lalu tempatkan di folder home anda  
![Install Cuckoo Sandbox](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_installation/0.png)

2. Install python menggunakan perintah **sudo apt-get install python**  

3. Install python sqlalchemy sebagai toolkit database untuk python menggunakan perintah **sudo apt-get install python-sqlalchemy**  
 ![Install Python SqlAlchemy](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_installation/1.png)

4. Install python pip untuk memenage dependesi python yang diperlukan menggunakan perintah **sudo apt-get install python-pip**  

5. Install dependensi python lainnya yang diperlukan menggunakan perintah **sudo pip install dpkt jinja2 pymongo bottle pefile**  
 ![Install Dependensi](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_installation/2.png)

6. Install lagi dependensi python lainnya yang diperlukan menggunakan perintah **sudo apt-get install build-essential git libpcre3 libpcre3-dev libpcre++-dev**  
 ![Install Dependensi](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_installation/3.png)

7. Install python pydeep dengan mengclone dari https://github.com/kbandla/pydeep.git  
 ![Install Python Pydeep](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_installation/4.png)

8. Install python pydeep, setelah mengclone lalu di build  
 ![Install Python Pydeep](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_installation/5.png)

9. Install yara dengan mengclone dari https://github.com/VirusTotal/yara.git  
 ![Install Yara](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_installation/6.png)

10. Install tcpdump menggunakan perintah **sudo apt install tcpdump**  
 ![Install TCPDump](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_installation/7.png)

11. Untuk memberikan hak akses cucko mengakses binary tanpa root menggunakan perintah **sudo setcap cap_net_raw,cap_net_admin=eip /usr/sbin/tcpdump**  
 ![Hak Akses](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_installation/8.png)

12. Masuk ke dalam folder tempat cuckoo diunduh, lalu install dependensi yang dibutuhkan menggunakan perintah **sudo pip install -r requirements.txt**  
 ![Install Requirement Cuckoo](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_installation/10.png)

13. Setelah semua terinstal, lalu setting networking VM pada VirtualBox(selanjutnya disebut Guest OS) agar dapat terhubung dengan Host OS. Pilih File > Preferences  
 ![Setting Networking](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_installation/11.png)

14. Pilih Network, tentukan alamat IPv4 dari host  
 ![Setting Networking](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_installation/12.png)

15. Pilih Settings pada Guest OS, lalu klik Network. Pilih adapter 1, lalu ganti Attached to dari NAT dengan Host-only Adapter, dan pilih nama vboxnet0  
 ![Setting Networking](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_installation/13.png)

16. Buat shared folder untuk mengirim data dari Host OS ke Guest OS dengan menjalankan Guest OS, lalu klik Device > Shared Folders > Shared Folders Settings  
 ![Setting Shared Folder](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_installation/14.png)

17. Lalu pada Settings di Guest OS pilih Shared Folders, klik add shared folder  
 ![Setting Shared Folder](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_installation/15.png)

18. Tentukan terlebih dahulu folder yang akan di share dengan guest OS. Lalu atur Folder Path sesuai dengan tempat folder berada dan Folder Name seusai dengan nama folder yang akan dibagikan  
 ![Setting Shared Folder](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_installation/16.png)

19. Pada Guest OS, klik Start > Klik Kanan Pada My Computer > Map Network Drive. Lalu pilih Drive yang diinginkan serta Pada box Folder masukkan \\vboxsrv\'nama folder yang di share'  
 ![Setting Shared Folder](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_installation/17.png)

20. Jika berhasil, maka tampak seperti berikut  
 ![Setting Shared Folder](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_installation/18.png)

21. Melalui shared folder, copy agent.py ke C:\Python27. Sebelumnya install terlebih dahulu Python 2.7 dan Adobe Reader pada Guest OS  
 ![Setting Agent.py](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_installation/19.png)

22. Pindahkan agent.py ke folder Start Up agar program tetap dijalankan setiap booting dengan menaruhnya pada C:\Document  and Settings\'nama user'\Start Menu\Programs\Startup. Ubah extensi file dari agent.py menjadi agent.pyw. Ini bertujuan agar ketika program dijalankan, program tidak memunculkan window. Program ini sebagai jembatan penghubung antara Guest OS dengan Host OS sebagai media pengiriman virus  
 ![Setting Agent.py](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_installation/20.png)

23. Periksa apakah agent.pyw sudah berjalan dengan command Start > Run > ketik cmd > ketik 'netsat -aon'. Jika port 8000 terbuka, maka Guest OS siap untuk menerima file malicious  
 ![Setting Agent.py](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_installation/21.png)

24. Atur iptables pada Host OS untuk membuka koneksi antara Host OS dengan vboxnet0 (Guest OS)  
 ![Setting Agent.py](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_installation/22.png)
 ![Setting Agent.py](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_installation/23.png)

25. Gunakan Snapshot untuk menyimpan state image saat ini.  
	Ketika cuckoo dijalankan, maka secara otomatis akan menggunakan snapshot ini. Ini bertujuan ketika menjalankan serangkaian test, cukup menjalankan VM dari snapshoot dan Guest OS akan kembali bersih seperti sedia kala  
 ![Setting Agent.py](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_installation/24.png)

26. Jalankan Cuckoo pada Host OS dengan perintah ./cuckoo.py. Cuckoo sandbox akan otomatis menjalankan VM, dan menunggu file diterima oleh agent.pyw pada Guest OS  
 ![Menjalankan Sanbox](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_installation/26.png)

27. Pada Host, jalankan perintah untuk mengirim malicious file ke Guest OS seperti pada gambar berikut :  
 ![Menjalankan Sanbox](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_installation/27.png)

28. Ketika Cuckoo Sandbox telah selesai menganalisis malicious file, maka akan ada text berwarna biru muda seperti "Task #26: analysis procedure complete"  
 ![Menjalankan Sanbox](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_installation/28.png)
 

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

7. Cuckoo mengirimkan malware ke website [VirusTotal](https://www.virustotal.com/) untuk mendeteksi jenis malware (dibantu oleh berbagai software anti-virus)  
![Analisis APT_military procurement.pdf](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_analyses/22/shots/10.PNG)

8. Dari berbagai hasil deteksi software anti-virus, akan kami ambil 2 contoh hasil deteksi malware dari 2 software anti-virus yaitu Microsoft dan Symantec   
![Analisis APT_military procurement.pdf](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_analyses/22/shots/11.PNG)

	Jenis malware yang terdeteksi oleh Microsoft adalah "Exploit:Win32/Pdfjsc.XD", malware ini termasuk jenis dari malicious PDF yang mengeksploitasi kerentanan dalam Adobe Acrobat dan Adobe Reader, malware ini bekerja dengan mengunduh dan menjalankan file sewenang-wenang ([sumber](http://www.microsoft.com/security/portal/threat/encyclopedia/entry.aspx?Name=Exploit%3aWin32%2fPdfjsc))  
    
    Jenis malware yang terdeteksi oleh Symantec adalah "Trojan.Pidief", malware ini termasuk jenis Trojan yang mengeksploitasi kerentanan dalam Adobe Acrobat dan Adobe Reader, malware ini bekerja dengan mengunduh malware tambahan ke komputer yang diserang ([sumber](https://www.symantec.com/security_response/writeup.jsp?docid=2009-121708-1022-99))

* **APT_ATT11990.pdf**

1. Lorem ipsum  
![Analisis APT_ATT11990.pdf](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_analyses/23/shots/1.PNG)

2. Lorem ipsum  
![Analisis APT_ATT11990.pdf](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_analyses/23/shots/2.PNG)

3. Lorem ipsum  
![Analisis APT_ATT11990.pdf](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_analyses/23/shots/3.PNG)

4. Lorem ipsum  
![Analisis APT_ATT11990.pdf](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_analyses/23/shots/4.PNG)

5. Lorem ipsum  
![Analisis APT_ATT11990.pdf](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_analyses/23/shots/5.PNG)

6. Lorem ipsum  
![Analisis APT_ATT11990.pdf](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_analyses/23/shots/6.PNG)

7. Lorem ipsum  
![Analisis APT_ATT11990.pdf](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_analyses/23/shots/7.PNG)

* **100621.pdf**

1. Lorem ipsum  
![Analisis 100621.pdf](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_analyses/24/shots/1.PNG)

2. Lorem ipsum  
![Analisis 100621.pdf](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_analyses/24/shots/2.PNG)

3. Lorem ipsum  
![Analisis 100621.pdf](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_analyses/24/shots/3.PNG)

4. Lorem ipsum  
![Analisis 100621.pdf](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_analyses/24/shots/4.PNG)

5. Lorem ipsum  
![Analisis 100621.pdf](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_analyses/24/shots/5.PNG)

6. Lorem ipsum  
![Analisis 100621.pdf](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_analyses/24/shots/6.PNG)

7. Lorem ipsum  
![Analisis 100621.pdf](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_analyses/24/shots/7.PNG)

* **IPR in China FINAL.pdf**

1. Lorem ipsum  
![Analisis IPR in China FINAL.pdf](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_analyses/25/shots/1.PNG)

2. Lorem ipsum  
![Analisis IPR in China FINAL.pdf](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_analyses/25/shots/2.PNG)

3. Lorem ipsum  
![Analisis IPR in China FINAL.pdf](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_analyses/25/shots/3.PNG)

4. Lorem ipsum  
![Analisis IPR in China FINAL.pdf](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_analyses/25/shots/4.PNG)

5. Lorem ipsum  
![Analisis IPR in China FINAL.pdf](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_analyses/25/shots/5.PNG)

6. Lorem ipsum  
![Analisis IPR in China FINAL.pdf](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_analyses/25/shots/6.PNG)

7. Lorem ipsum  
![Analisis IPR in China FINAL.pdf](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/cuckoo_analyses/25/shots/7.PNG)


## Kesimpulan dan Saran
