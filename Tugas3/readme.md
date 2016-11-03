# **Tugas 3 PKSJ - Analisa Malware Menggunakan Cuckoo Sandbox**


## Pendahuluan


Tugas ini dibuat untuk menyelesaikan Tugas 3 yaitu "Analisa Malware Menggunakan Cuckoo Sandbox" pada matakuliah Perancangan Keamanan & Sistem Jaringan (PKSJ) Semester Ganjil 2016/2017, Teknik Informatika ITS, Surabaya
 
Anggota Kelompok
- Ardi Nusawan      5113100096
- Gian Sebastian A. 5113100132
- Ronauli Sidabukke 5113100142


## Dasar Teori

**1. Cuckoo Sandbox**

**Cuckoo Sandbox** dalam tiga kata, adalah sistem analisa malware. Cuckoo dapat melakukan analisa perilaku dan jenis malware dengan menjalankan malware tersebut dalam sebuah sistem yang akan menjadi *sandbox* (biasanya virtual) yang akan dimonitoring perilakunya. Analisa dapat dilakukan pada tipe file executables Windows, file DLL, dokumen PDF, dokumen Office, halaman website, script PHP, dll. Cuckoo dapat menampilkan analisa API calls yang dijalankan proses yang terinfeksi malware, file apa saja yang diakses/dibuat/dihapus oleh malware, menyimpan memori dan network dumps dari proses malware, bahkan screenshoot dari OS ketika malware dijalankan([sumber](https://www.cuckoosandbox.org/))

**2. Malware yang dianalisis**
 
* **PDF** atau Portable Document Format adalah sebuah format file yang diciptakan oleh Adobe System, Inc. File jenis ini sangat populer dan banyak digunakan terutama dalam bentuk e-book karena dapat dengan mudah dibuka menggunakan berbagai aplikasi gratis. Website resmi Adobe menyatakan : "PDFs can contain links and buttons, form fields, audio, video, and business logic", disini berarti konten tersebut bisa saja memuat *malicious program* yang membahayakan pembaca PDF tersebut. ([sumber](https://acrobat.adobe.com/us/en/why-adobe/about-adobe-pdf.html))
* **Sumber Malware** yang kami gunakan berasal dari [Contagio](http://contagiodump.blogspot.co.id/), merupakan website yang kontennya adalah sampel-sampel dari berbagai malware. Untuk membuka zip dari file malware tersebut dibutuhkan password yang didapatkan dengan cara mengkontak pemilik web melalui email. Link yang digunakan untuk mengunduh file malware sedang diperbaharui dan untuk sementara file malware dapat dicari pada [Dropbox](https://www.dropbox.com/sh/i6ed6v32x0fp94z/AAAQvOsOvbWrOs8T3_ZTXqQya?dl=0) milik pemilik web.
* **APT_military procurement.pdf** adalah malicious PDF pertama yang kami analisis, file terletak dalam 30APTpdfcuckoo.zip ([sumber](https://www.dropbox.com/sh/i6ed6v32x0fp94z/AAB7nUZTiI6Xk0i6Zg663kDga/CVE?dl=0))
* **APT_ATT11990.pdf** adalah malicious PDF kedua yang kami analisis, file terletak dalam 30APTpdfcuckoo.zip ([sumber](https://www.dropbox.com/sh/i6ed6v32x0fp94z/AAB7nUZTiI6Xk0i6Zg663kDga/CVE?dl=0))
* **100621.pdf** adalah malicious PDF ketiga yang kami analisis, file terletak dalam ^CVE-2010-1297 PDF 2010-06-21 E3F5EF4FA17B4E08…73728 100621.zip ([sumber](https://www.cuckoosandbox.org/))
* **IPR in China FINAL.pdf** adalah malicious PDF keempat yang kami analisis, file terletak dalam CVE-2009-0927 CVE-2007-5659 PDF 2010-04-02 C497C…in China final.zip ([sumber](https://www.cuckoosandbox.org/))


## Langkah Instalasi Cuckoo Sandbox


 1. Download File Zip dari ([sini](https://github.com/cuckoosandbox/cuckoo))
![Install Cuckoo Sandbox](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/Instalasi_Cuckoo/1.png)

2. Setelah download selesai, *unzip* file cuckoo-master.zip di folder. ([sini](https://github.com/cuckoosandbox/cuckoo))
![Install Cuckoo Sandbox](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas3/Instalasi_Cuckoo/1.png)
 
 	Jika sudah selesai, anda dapat memindahkan folder cuckoo ke folder mana yang lebih mudah diakses (dalam contoh ini, dipindahkan ke ~/cuckoo)
    
3. Untuk konfigurasi cuckoo, lakukan langkah berikut :
    

## Analisis Malware



## Kesimpulan dan Saran

