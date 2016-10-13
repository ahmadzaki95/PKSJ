# **Tugas 2 PKSJ - Ganjil 2016/2017**


## Pendahuluan

Tugas ini dibuat untuk menyelesaikan Tugas 2 pada matakuliah Perancangan Keamanan & Sistem Jaringan (PKSJ) Semester Ganjil 2016/2017, Teknik Informatika ITS, Surabaya
 
Anggota Kelompok
- Ardi Nusawan      5113100096
- Gian Sebastian A. 5113100132
- Ronauli Sidabukke 5113100142

## Dasar Teori

**1. OS yang digunakan**

* **Ubuntu Server** adalah ubuntu yang  didesain untuk di install di server. Perbedaan mendasar, di Ubuntu Server tidak tersedia GUI. Jika anda menggunakan ubuntu server artinya anda harus bekerja dengan perintah perintah di layar hitam ayng sering disebut konsole. Jika anda datang dari windows, maka tampilan ubuntu server seperti DOS ([sumber](http://www.candra.web.id/mengenal-ubuntu-server/))
 
* **Kali Linux** adalah distribusi berlandasan distribusi Debian GNU/Linux untuk tujuan forensik digital dan di gunakan untuk pengujian penetrasi, yang dipelihara dan didanai oleh Offensive Security. Kali juga dikembangkan oleh  Offensive Security sebagai penerus BackTrack Linux. Kali menyediakan pengguna dengan mudah akses terhadap koleksi yang besar dan komprehensif untuk alat yang berhubungan dengan keamanan, termasuk port scanner untuk password cracker. ([sumber](http://gudanglinux.com/glossary/kali-linux/))

**2. Wordpress dan plugin yang diinstal**

* **Wordpress**, adalah sebuah aplikasi sumber terbuka (open source) yang sangat populer digunakan sebagai mesin blog (blog engine). WordPress dibangun dengan bahasa pemrograman PHP dan basis data (database) MySQL. PHP dan MySQL, keduanya merupakan perangkat lunak sumber terbuka (open source software) ( [link](https://id.wikipedia.org/wiki/WordPress) )

* **CP Reservation Calendar 1.1.6** adalah plugin Wordpress untuk reservasi suatu tempat. Kelemahan pada plugin ini terdapat pada file dex_reservations.php, pada fungsi berikut

``` 
function dex_reservations_get_option ($field, $default_value)
{
    global $wpdb, $dex_option_buffered_item, $dex_option_buffered_id;
    if ($dex_option_buffered_id == CP_CALENDAR_ID)
        $value = $dex_option_buffered_item->$field;
    else
    {
       $myrows = $wpdb->get_results( "SELECT * FROM ".DEX_RESERVATIONS_CONFIG_TABLE_NAME." WHERE id=".CP_CALENDAR_ID );
       $value = $myrows[0]->$field;
       $dex_option_buffered_item = $myrows[0];
       $dex_option_buffered_id  = CP_CALENDAR_ID;
    }
    if ($value == '' && $dex_option_buffered_item->calendar_language == '')
        $value = $default_value;
    return $value;
}
```

Kelemahannya adalah parameter [ CP_CALENDAR_ID ] yang tidak divalidasi / *escape parameter* . Sumber : ([exploit-db](https://www.exploit-db.com/exploits/38187/))

* **League Manager 3.9.1.1**

* **Video Player 1.5.16** adalah plugin Wordpress untuk menambahkan, mengatur dan menampilkan video. Ternyata plugin ini dapat dieksploitasi menggunakan blind SQL Injection. Pada referensi disebutkan bahwa dengan menggunakan multiple blind SQL Injenction, user yang dapat login ke dashboard Wordpress dapat mengekstrak informasi dari user lainnya, seperti panjang password bahkan seluruh hash password dari user tersebut.  

![Skenario WPScan dan Mitmproxy](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_SQLInjection_WPScan_VideoPlayer/Screenshot_4.jpg)

Kelemahan terdapat pada fungsi show_tag(), spider_video_select_playlist(), dan spider_video_select_video(). Penulis mencoba untuk mencegah SQL Injection dengan memanggil fungsi esc_sql() dan esc_html() pada parameter order_by yang berfungsi membersihkan string dari karakter - karakter seperti ' " < > , . Namun parameter POST order_by sendiri tidak di quote ketika digunakan dengan query ORDER BY, sehingga masih dapat dieksploitasi menggunakan SQL Injection.  
Sumber : ([link](https://sumofpwn.nl/advisory/2016/multiple_sql_injection_vulnerabilities_in_wordpress_video_player.html))

![Skenario WPScan dan Mitmproxy](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_SQLInjection_WPScan_VideoPlayer/Screenshot_5.jpg)

**3. Tools yang digunakan**

* **SQLMap**, adalah tool opensource yang mendeteksi dan melakukan exploit pada bug SQL injection secara otomatis. dengan melakukan serangan SQL injection seorang attacker dapat mengambil alih serta memanipulasi sebuah database di dalam sebuah server. ( [link](www.sqlmap.org) )

* **WPScan** adalah tool bawaan yang disediakan oleh Kali Linux, yang berfungsi untuk memindai tingkat atau masalah keamanan dari CMS (Content Management System) Wordpress. ( [link](http://tools.kali.org/web-applications/wpscan) )  
```
Help :

 Some values are settable in a config file, see the example.conf.json

 --update                            Update to the database to the latest version.
 --url       | -u <target url>       The WordPress URL/domain to scan.
 --force     | -f                    Forces WPScan to not check if the remote site is running WordPress.
 --enumerate | -e [option(s)]        Enumeration.
   option :
     u        usernames from id 1 to 10
     u[10-20] usernames from id 10 to 20 (you must write [] chars)
     p        plugins
     vp       only vulnerable plugins
     ap       all plugins (can take a long time)
     tt       timthumbs
     t        themes
     vt       only vulnerable themes
     at       all themes (can take a long time)
   Multiple values are allowed : "-e tt,p" will enumerate timthumbs and plugins
   If no option is supplied, the default is "vt,tt,u,vp"
```

* **Mitmproxy** adalah tool yang mempunyai program konsol interaktif yang memungkinkan traffic HTTP  untuk di-intercept, diperiksa, dan dimodifikasi. Gunakan shortcut key **?** di layar Mitmproxy manapun untuk melihat dokumentasi cara penggunaan. ( [link](http://docs.mitmproxy.org/en/latest/mitmproxy.html) )  


## Langkah Instalasi Wordpress & Plugin


#### 1. Langkah Instalasi Wordpress pada Kali Linux

  1. Pastikan LAMP (Linux, Apache, MySQL, and PHP) stack sudah terinstal


  2. Login ke MySQL milik user **root**  
![Instal Wordpress](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_Instalasi_WordPress/Screenshot_1.jpg)


  3. Membuat database yang akan digunakan Wordpress  
![Instal Wordpress](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_Instalasi_WordPress/Screenshot_2.jpg)


  4. Membuat user untuk mengoperasikan database Wordpress  
![Instal Wordpress](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_Instalasi_WordPress/Screenshot_3.jpg)


  5. Memberikan hak akses ke database untuk user yang baru dibuat  
![Instal Wordpress](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_Instalasi_WordPress/Screenshot_4.jpg)


  6. Flush aturan hak akses yang telah ditetapkan agar MySQL yang sedang berjalan dapat mengetahui perubahan aturan hak akses, kemudian keluar dari MySQL  
![Instal Wordpress](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_Instalasi_WordPress/Screenshot_5.jpg)


  7. Unduh versi terbaru dari Wordpress  
![Instal Wordpress](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_Instalasi_WordPress/Screenshot_6.jpg)


  8. Ekstrak file yang telah diunduh, yang menghasilkan direktori bernama **wordpress**  
![Instal Wordpress](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_Instalasi_WordPress/Screenshot_7.jpg)


  9. Unduh library tambahan seperti php5-gd agar dapat bekerja dengan gambar (upload, resizing) pada Wordpress   
![Instal Wordpress](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_Instalasi_WordPress/Screenshot_8.jpg)


  10. Pindah ke direktori **wordpress** (dihasilkan dari langkah ke 8), kemudian salin contoh file konfigurasi default yang sudah tersedia agar menjadi file konfigurasi dari Wordpress   
![Instal Wordpress](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_Instalasi_WordPress/Screenshot_9.jpg)


  11. Buka file konfigurasi menggunakan teks editor, kemudian ubah nilai dari 'DB_NAME', 'DB_USER'dan 'DB_PASSWORD' sesuai dengan nilai yang telah anda tentukan pada langkah 3 dan 4  
![Instal Wordpress](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_Instalasi_WordPress/Screenshot_10.jpg)


  12. Contoh tampilan dari konfigurasi Wordpress yang digunakan pada tutorial  
![Instal Wordpress](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_Instalasi_WordPress/Screenshot_11.jpg)


  13. Salin isi dari direktori **wordpress** ke **/var/www/html/**  
![Instal Wordpress](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_Instalasi_WordPress/Screenshot_12.jpg)


  14. Ubah hak kepemilikan dari file dan direktori Wordpress ke user yang berhak mengaksesnya  
![Instal Wordpress](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_Instalasi_WordPress/Screenshot_13.jpg)


  15. Buat direktori **uploads** dibawah direktori **wp-content** untuk menyimpan file yang diunggah, kemudian ubah hak kepemilikan (grup) dari direktori **uploads** ke web server agar web server dapat membuat file dan direktori dibawah direktori tersebut, sehingga user dapat mengunggah file ke Wordpress   
![Instal Wordpress](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_Instalasi_WordPress/Screenshot_14.jpg)


  16. Buka web browser, kemudian masukkan alamat Wordpress anda, jika Wordpress berjalan maka akan muncul tampilan seperti di gambar, kemudian pilih bahasa yang akan digunakan Wordpress  
![Instal Wordpress](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_Instalasi_WordPress/Screenshot_15.jpg)


  17. Masukkan data-data yang akan digunakan untuk membuat akun admin pertama dari Wordpress  
![Instal Wordpress](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_Instalasi_WordPress/Screenshot_16.jpg)


  18. Tampilan instalasi Wordpress telah berhasil dilakukan  
![Instal Wordpress](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_Instalasi_WordPress/Screenshot_17.jpg)


  19. Login ke Wordpress anda menggunakan akun admin yang telah dibuat  
![Instal Wordpress](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_Instalasi_WordPress/Screenshot_18.jpg)


  20. Tampilan dashboard dari Wordpress  
![Instal Wordpress](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_Instalasi_WordPress/Screenshot_19.jpg)


#### 2. Langkah Instalasi Plugin Wordpress


* ##### Plugin CP Reservation Calendar 1.1.6

  1. Di command line/terminal/ SSH komputer webserver, pastikan anda berada di direktori wordpress anda  
  ```
  $ cd {direktori web server}/{nama folder tempat wordpress diinstal}

  $ cd /var/www/html/wordpress
  ```
  
  2. Pindah ke folder plugins dengan masukkan perintah berikut (jika pada Linux)  
  ```
  $ cd wp-content/plugins
  ```
  
  3. Untuk mendownload plugin CP Reservation Calendar versi 1.1.6 (jika install langsung dari halaman WP-Admin maka yang terinstall adalah versi paling baru) , masukkan perintah berikut :  
  ```
  $ wget https://downloads.wordpress.org/plugin/cp-reservation-calendar.1.1.6.zip
  ```
  
  4. Jika download sudah selesai , *unzip* file tersebut dengan memasukkan perintah berikut :  
  ```
  $ unzip cp-reservation-calendar.1.1.6.zip  
  ```  
  Jika unzip belum terinstall, install dengan masukkan perintah berikut :  
  ```
  # apt-get install unzip
  ```
  
  5. Setelah selesai, login ke dalam wordpress yang telah diinstall. Setelah itu, pada sidebar bagian Plugins, klik di bagian Installed Plugin.  
  ![Instal Cp-Res](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshow_Instalasi_Plugin_CPRes/1.png)

  6. Klik 'Activate' pada plugin Cp Reservation Calendar.  
  ![Instal Cp-Res](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshow_Instalasi_Plugin_CPRes/2.png)

  7. Setelah diaktivasi , agar dapat di-injection, maka kita harus memasukkan konten CP Reservation calendar ke dalam wordpress agar dapat diakses. Maka, kita akan membuat post baru berisi konten CP Reservation Calendar. Klik sidebar Post , lalu klik Add New.  
  ![Instal Cp-Res](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshow_Instalasi_Plugin_CPRes/3.png)

  8. Setelah muncul halaman add new Post, klik icon kecil bergambar Kalender di sebelah tombol 'Add Media' untuk menambahkan konten Cp Reservation Calendar  
  ![Instal Cp-Res](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshow_Instalasi_Plugin_CPRes/4.png)  
  Jika sudah , maka akan muncul tulisan berikut di bagian isi Post. Setelah muncul , Klik Publish Post di sebelah kanan.  
  ![Instal Cp-Res](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshow_Instalasi_Plugin_CPRes/5.png)

  9. Jika berhasil, maka akan muncul post kira-kira seperti gambar berikut di halaman Wordpress anda.  
  ![Instal Cp-Res](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshow_Instalasi_Plugin_CPRes/6.png)


* ##### Plugin League Manager 3.9.1.1

  1. Unduh plugin Wordpress League Manager versi 3.9.1.1 di https://wordpress.org/plugins/leaguemanager/developers/
![Install League Manager](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_Instalasi_Plugin_LeagueManager/1.jpeg)

  2. Login ke Wordpress anda, pada dashboard navigasi ke menu Plugins, kemudian pilih Add New  
![Instal Video Player](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_Instalasi_Plugin_LeagueManager/2.jpeg)

  3. Unggah file yang diunduh pada langkah 1, kemudian pilih Install Now untuk menginstal plugin  
![Instal Video Player](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_Instalasi_Plugin_LeagueManager/3.jpeg)

  4. Lalu klik Install Now  
![Instal Video Player](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_Instalasi_Plugin_LeagueManager/4.jpeg)

  5. Tampilan ketika plugin berhasi diinstal, pilih Activate Plugin  
![Instal Video Player](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_Instalasi_Plugin_LeagueManager/5.jpeg)

  6. Tampilan dari daftar plugin yang sedang aktif, dapat dilihat plugin League Manager sudah aktif. Untuk menggunakan plugin, navigasi ke menu League Manager, kemudian buatlah pertandingan.
![Instal Video Player](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_Instalasi_Plugin_LeagueManager/6.jpeg)

* ##### Plugin Video Player 1.5.16

  1. Unduh plugin Wordpress Video Player versi 1.5.16 di https://wordpress.org/plugins/player/developers/  
![Instal Video Player](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_Instalasi_Plugin_VideoPlayer/Screenshot_1.jpg)

  2. Login ke Wordpress anda, pada dashboard navigasi ke menu Plugins, kemudian pilih Add New  
![Instal Video Player](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_Instalasi_Plugin_VideoPlayer/Screenshot_2.jpg)

  3. Unggah file yang diunduh pada langkah 1, kemudian pilih Install Now untuk menginstal plugin  
![Instal Video Player](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_Instalasi_Plugin_VideoPlayer/Screenshot_3.jpg)

  4. Jika terdapat error seperti di gambar, lakukan langkah 5 - 7, jika tidak maka lanjut ke langkah 8  
![Instal Video Player](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_Instalasi_Plugin_VideoPlayer/Screenshot_4.jpg)

  5. Buka Ubuntu Server tempat Wordpress di deploy, buka file **php.ini** yang terletak pada /etc/php5/apache2/ dengan teks editor  
![Instal Video Player](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_Instalasi_Plugin_VideoPlayer/Screenshot_5.jpg)

  6. Ubah nilai dari **upload_max_filesize** sesuai besar file maksimal yang dapat diunggah yang anda inginkan (misal 64M)  
![Instal Video Player](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_Instalasi_Plugin_VideoPlayer/Screenshot_6.jpg)

  7. Ubah nilai dari **post_max_filesize** sesuai besar data maksimal yang dapat di POST yang anda inginkan (misal 64M)  
![Instal Video Player](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_Instalasi_Plugin_VideoPlayer/Screenshot_7.jpg)

  8. Tampilan ketika plugin berhasi diinstal, pilih Activate Plugin  
![Instal Video Player](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_Instalasi_Plugin_VideoPlayer/Screenshot_8.jpg)

  9. Tampilan dari daftar plugin yang sedang aktif, dapat dilihat plugin Video Player sudah aktif. Untuk menggunakan plugin, navigasi ke menu Video Player, kemudian pilih Video Player  
![Instal Video Player](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_Instalasi_Plugin_VideoPlayer/Screenshot_9.jpg)

  10. Pilih Add a player untuk menambahkan player yang dapat memutar playlist video  
![Instal Video Player](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_Instalasi_Plugin_VideoPlayer/Screenshot_10.jpg)

  11. Masukkan Priority (prioritas), Title (judul), Theme (desain) dan Playlist dari player, kemudian pilih Save untuk menyimpan player. Playlist yang digunakan pada tutorial menggunakan playlist bawaan dari plugin  
![Instal Video Player](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_Instalasi_Plugin_VideoPlayer/Screenshot_11.jpg)

  12. Tampilan player yang sudah tersimpan  
![Instal Video Player](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_Instalasi_Plugin_VideoPlayer/Screenshot_12.jpg)

  13. Pada dashboard navigasi ke menu Posts, kemudian pilih post yang berjudul Hello World! (default dari Wordpress) untuk mengedit post tersebut  
![Instal Video Player](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_Instalasi_Plugin_VideoPlayer/Screenshot_13.jpg)

  14. Untuk menampilkan plugin Video Player pada post, pilih Insert Spider Video Player  
![Instal Video Player](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_Instalasi_Plugin_VideoPlayer/Screenshot_14.jpg)

  15. Pilih player yang ingin ditampilkan  
![Instal Video Player](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_Instalasi_Plugin_VideoPlayer/Screenshot_15.jpg)

  16. Video Player telah ditambahkan pada post  
![Instal Video Player](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_Instalasi_Plugin_VideoPlayer/Screenshot_16.jpg)

  17. Tampilan Video Player pada Wordpress  
![Instal Video Player](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_Instalasi_Plugin_VideoPlayer/Screenshot_17.jpg)


#### 3. Langkah Uji Penetrasi SQL Injection 

Pada tahap ini, kami melakukan uji penetrasi berikut :

1. Plugin Video Player 1.5.16 dengan tools WPScan dan Mitmproxy

2. Plugin CP Reservation Calendar 1.1.6 dengan tool SQLMap

3. Plugin X dengan tools Y


##### 1. Plugin Video Player 1.5.16 dengan tools WPScan dan Mitmproxy

  1. Tutorial ini menggunakan Kali Linux, sehingga WPScan sudah terinstal. Gunakan perintah
**wpscan --url < alamat situs Wordpress anda >** untuk melakukan pemindaian kelemahan dari situs Wordpress anda. Jika muncul pertanyaan seperti di gambar, maka dianjurkan untuk memperbaharui database dari WPScan dengan memasukkan **Y** 
![Skenario WPScan dan Mitmproxy](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_SQLInjection_WPScan_VideoPlayer/Screenshot_1.jpg)


  2. Gunakan perintah **wpscan --url < alamat situs Wordpress anda > --enumerate vp** untuk memindai plugin yang memiliki kelemahan  
![Skenario WPScan dan Mitmproxy](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_SQLInjection_WPScan_VideoPlayer/Screenshot_2.jpg)


  3. Tampilan daftar plugin yang memiliki kelemahan (hasil pindai) beserta referensi yang mendukung pernyataan tersebut. Pada tutorial ini akan dilakukan blind SQL Injection terhadap plugin Wordpress Video Player versi 1.5.16, sehingga akan digunakan salah satu referensi ([link](https://sumofpwn.nl/advisory/2016/multiple_sql_injection_vulnerabilities_in_wordpress_video_player.html)) yang tersedia.  
![Skenario WPScan dan Mitmproxy](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_SQLInjection_WPScan_VideoPlayer/Screenshot_3.jpg)


  4. Gunakan perintah **mitmproxy --host** untuk menjalankan Mitmproxy yang menampilkan nama host  
![Skenario WPScan dan Mitmproxy](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_SQLInjection_WPScan_VideoPlayer/Screenshot_6.jpg)


  5. Tekan key **i** pada keyboard anda, masukkan perintah **~m POST** agar semua POST request yang ditangkap oleh Mitmproxy dapat di-intercept  
![Skenario WPScan dan Mitmproxy](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_SQLInjection_WPScan_VideoPlayer/Screenshot_7.jpg)


  6. Pasang penerusan port pada VirtualBox Kali Linux, menggunakan port 8080 karena Mitmproxy melakukan listen pada port tersebut secara default  
![Skenario WPScan dan Mitmproxy](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_SQLInjection_WPScan_VideoPlayer/Screenshot_8.jpg)


  7. Setting proxy pada browser yang ingin mengakses Wordpress dengan alamat host Kali Linux dan port sesuai dengan port host yang ditentukan pada penerusan port di langkah 6   
![Skenario WPScan dan Mitmproxy](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_SQLInjection_WPScan_VideoPlayer/Screenshot_9.jpg)


  8. Tampilan Mitmproxy yang meng-intercept request POST ketika user melakukan login ke Wordpress. Tulisan berwarna jingga menandakan request tersebut ditahan pada proxy server, kemudian request tersebut dapat dilihat dan di-edit datanya, setelah itu dapat diteruskan ke server tujuan  
![Skenario WPScan dan Mitmproxy](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_SQLInjection_WPScan_VideoPlayer/Screenshot_10.jpg)


  9. Pada dashboard Wordpress, navigasi ke menu Video Player, kemudian pilih Tags, pada tabel yang berisi daftar tag, klik Order untuk mengirimkan request POST yang tujuannya untuk melakukan pengurutan tag berdasarkan nilai ordering  
![Skenario WPScan dan Mitmproxy](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_SQLInjection_WPScan_VideoPlayer/Screenshot_11.jpg)


  10. Tampilan request POST yang dikirimkan pada langkah 9, tekan key **e** pada keyboard untuk melihat detil request tersebut  
![Skenario WPScan dan Mitmproxy](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_SQLInjection_WPScan_VideoPlayer/Screenshot_12.jpg)


  11. Tampilan detil dari request, dapat dilihat form yang dikirim dan responsenya. Tekan key **e** kemudian key **f** pada keyboard untuk mengedit form dari request  
![Skenario WPScan dan Mitmproxy](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_SQLInjection_WPScan_VideoPlayer/Screenshot_13.jpg)


  12. Akan dilakukan blind SQL Injection dengan mengubah nilai dari key **order_by** dengan SQL query   
![Skenario WPScan dan Mitmproxy](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_SQLInjection_WPScan_VideoPlayer/Screenshot_14.jpg)


  13. SQL query yang ditampilkan pada gambar berfungsi untuk mengecek panjang dari username user dengan id 1, jika panjangnya berada di range 3 - 5, maka **name** akan dijadikan nilai dari **order_by**, sedangkan jika panjangnya berada di luar range maka **id** akan dijadikan nilai dari **order_by**  
![Skenario WPScan dan Mitmproxy](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_SQLInjection_WPScan_VideoPlayer/Screenshot_15.jpg)


  14. Teruskan request POST yang telah di-edit dengan menekan key **a** pada keyboard  
![Skenario WPScan dan Mitmproxy](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_SQLInjection_WPScan_VideoPlayer/Screenshot_16.jpg)


  15. Tampilan tabel daftar tag yang diurutkan berdasarkan nama, bukan berdasarkan id atau ordering, sehingga dapat dipastikan bahwa panjang username berada di range 3 - 5  
![Skenario WPScan dan Mitmproxy](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_SQLInjection_WPScan_VideoPlayer/Screenshot_17.jpg)


  16. Informasi panjang username dapat diolah lebih lanjut untuk melakukan blind SQL Injection selanjutnya, yang bertujuan untuk mendapatkan setiap karakter dari username tersebut. Contohnya SQL query seperti pada gambar, yang berfungsi untuk mengecek apakah karakter pertama dari username user dengan id 1 memiliki nilai ASCII yang berada di range 102 - 104  
![Skenario WPScan dan Mitmproxy](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_SQLInjection_WPScan_VideoPlayer/Screenshot_18.jpg)


##### 2. Plugin CP Reservation Calendar 1.1.6 dengan tool SQLMap

  Seperti yang dibahas dalam link ([exploit-db](https://www.exploit-db.com/exploits/38187/)) ini, kelemahan terdapat pada link **http://localhost/wordpress/?action=dex_reservations_check_posted_data** , pada file wpcontent/plugins/cp-reservation-calendar/dex_reservations.php

  Pada fungsi *dex_reservations_check_posted_data*, terdapat *malicious code* dimana parameter POST dex_item langsung didefine sebagai variabel tanpa di*escape* atau di*sanitize* terlebih dahulu.

  ![Skenario CPRes dan SQLMap](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_SQLInj_CPRes/1.png)

  Dan variabel tersebut langsung dieksekusi dengan SQL Query pada fungsi dex_reservation_get_option()

  ![Skenario CPRes dan SQLMap](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_SQLInj_CPRes/2.png)

  Maka dengan SQL Map, kita dapat melakukan SQL Injection dengan parameter berikut :

  url = http://{alamat web wordpress}?action=dex_reservations_check_posted_data
  parameter yang akan diinjeksi : dex_item
  data yang dikirimkan : dex_reservations_post=1&dex_item=1 (kedua parameter ini dibutuhkan agar tidak keluar dari fungsi dex_reservations_check_posted_data, karena pengecekan dilakukan jika kedua parameter tersebut kosong)

  1. Maka dengan SQLMap, kita masukkan perintah berikut :  
  ```
  $ sqlmap --url="http://{alamat web wordpress}/?action=dex_reservations_check_posted_data" --data="dex_reservations_post=1&dex_item=1" -p dex_item --level=5 --risk=3

  ```

  2. Tunggu script berjalan. Jika sudah selesai, maka SQLMap akan menginfokan arsitektur yang digunakan oleh server target , seperti gambar berikut :  
  ![Skenario CPRes dan SQLMap](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_SQLInj_CPRes/4.png)


  3. Untuk mempermudah SQLMap dalam menscan, maka kita dapat menambahkan parameter dbms pada injection selanjutnya. Misalkan pada skenario ini, kita ingin mendapatkan data users dalam wordpress tersebut, karena wordpress biasanya menggunakan tabel wp_users untuk menyimpan daftar users, maka kita dapat mencoba meng*inject* dengan perintah berikut :  
  ```
  $ sqlmap --url="http://192.168.56.1:81/wordpress/?action=dex_reservations_check_posted_data" --data="dex_reservations_post=1&dex_item=1" -p dex_item --dbms="MySQL" --level=5 --risk=3 -T wp_users --dump

  ```

  4. Jika berhasil ,Selamat, anda akan mendapatkan data users dengan password yang masih di-enkripsi / di salt. Lalu SQLMap akan 'menanyakan' apakah anda ingin mencoba meng-crack password dengan dictionary yang ada.  
  ![Skenario CPRes dan SQLMap](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_SQLInj_CPRes/5.png)

  5. Jika anda ingin mengcrack passwordnya , maka anda dapat memasukkan data dictionary file tersebut. Dan jika anda beruntung file dictionary tersebut memuat password yang benar dari users tersebut, akan SQLMap akan menginfokannya seperti berikut :  
  ![Skenario CPRes dan SQLMap](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_SQLInj_CPRes/6.png)  Password berada di kolom user_pass dan password yang telah didekripsi terdapat di dalam tanda kurung()


##### 3. Plugin League Manager dengan tool SQLMap
  1. Seperti yang dibahas dalam  ([exploit-db](https://www.exploit-db.com/exploits/37182/)), kelemahan terdapat pada Unauthenticated SQLi (http://localhost/?match=1).

  2. Kita mencoba menggunakan SQLMap untuk mengecek apakah parameter /?match=1 bisa diinject :  
  ![Skenario League Manager dan SQLMap](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshoot_SQLInjection_SQLMap_LeagueManager/1.jpg).

  3. Terlihat bahwa parameter 'match' mengandung 'vulnerable' :  
  ![Skenario League Manager dan SQLMap](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshoot_SQLInjection_SQLMap_LeagueManager/2.jpg).

  4. Karena terdapat beberapa 'vulnerable', seperti error-based, AND/OR time-based blind, dan Union query, kami mencoba untuk melihat isi tabel nya :  
  ![Skenario League Manager dan SQLMap](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshoot_SQLInjection_SQLMap_LeagueManager/5.jpeg).

  5. Kami menemukan nama tabel dan dapat melihat struktur table dari dataase tersebut :  
  ![Skenario League Manager dan SQLMap](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshoot_SQLInjection_SQLMap_LeagueManager/6.jpeg).

  6. Kami melakukan dump pada database wordpress dan table wp_users, terlihat pada gambar SQLMap menemukan data user :  
  ![Skenario League Manager dan SQLMap](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshoot_SQLInjection_SQLMap_LeagueManager/9.png).

  7. (2) Kami melakukan dump pada database wordpress dan table wp_users, terlihat pada gambar SQLMap menemukan data user :  
  ![Skenario League Manager dan SQLMap](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshoot_SQLInjection_SQLMap_LeagueManager/10.png).

  8. SQLMap melakukan brute force dekript password pada tabel wp_users. Terlihat password yang di dekript berada disebelah password asli yang di salt oleh wordpress :  
  ![Skenario League Manager dan SQLMap](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshoot_SQLInjection_SQLMap_LeagueManager/11.png).

## 4. Kesimpulan dan Saran

  1. 


