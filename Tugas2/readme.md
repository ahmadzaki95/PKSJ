# **Tugas 2 PKSJ - Ganjil 2016/2017**


## Pendahuluan

Tugas ini dibuat untuk menyelesaikan Tugas 2 pada matakuliah Perancangan Keamanan & Sistem Jaringan (PKSJ) Semester Ganjil 2016/2017, Teknik Informatika ITS, Surabaya
 
Anggota Kelompok
- Ardi Nusawan      5113100096
- Gian Sebastian A. 5113100132
- Ronauli Sidabukke 5113100142

### Penjelasan Tugas

Tugas ini adalah 

## Dasar Teori

**1. OS yang digunakan**

* **Ubuntu Server** adalah ubuntu yang  didesain untuk di install di server. Perbedaan mendasar, di Ubuntu Server tidak tersedia GUI. Jika anda menggunakan ubuntu server artinya anda harus bekerja dengan perintah perintah di layar hitam ayng sering disebut konsole. Jika anda datang dari windows, maka tampilan ubuntu server seperti DOS ([sumber](http://www.candra.web.id/mengenal-ubuntu-server/))
 
* **Kali Linux** adalah distribusi berlandasan distribusi Debian GNU/Linux untuk tujuan forensik digital dan di gunakan untuk pengujian penetrasi, yang dipelihara dan didanai oleh Offensive Security. Kali juga dikembangkan oleh  Offensive Security sebagai penerus BackTrack Linux. Kali menyediakan pengguna dengan mudah akses terhadap koleksi yang besar dan komprehensif untuk alat yang berhubungan dengan keamanan, termasuk port scanner untuk password cracker. ([sumber](http://gudanglinux.com/glossary/kali-linux/))

**2. Wordpress dan plugin yang diinstal**

* **Wordpress**, adalah sebuah aplikasi sumber terbuka (open source) yang sangat populer digunakan sebagai mesin blog (blog engine). WordPress dibangun dengan bahasa pemrograman PHP dan basis data (database) MySQL. PHP dan MySQL, keduanya merupakan perangkat lunak sumber terbuka (open source software) ( [link](https://id.wikipedia.org/wiki/WordPress) )

* **CP Reservation Calendar 1.1.6** adalah plugin wordpress untuk reservasi suatu tempat. Kelemahan pada plugin ini terdapat pada file dex_reservations.php, pada fungsi berikut

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

* **Video Player 1.5.16**

**3. Tools yang digunakan**

* **SQLMap**, adalah tools opensource yang mendeteksi dan melakukan exploit pada bug SQL injection secara otomatis. dengan melakukan serangan SQL injection seorang attacker dapat mengambil alih serta memanipulasi sebuah database di dalam sebuah server. ( [link](www.sqlmap.org) )

* **WPScan** Lorem Ipsum [link](Lorem ipsum)

* **Mitmproxy** Lorem Ipsum [link](Lorem ipsum)


## Langkah Instalasi Wordpress & Plugin


#### 1. Langkah Instalasi Wordpress
  1. Lorem Ipsum
![Instal Wordpress](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_Instalasi_WordPress/Screenshot_1.jpg)


  2. Lorem Ipsum
![Instal Wordpress](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_Instalasi_WordPress/Screenshot_2.jpg)


  3. Lorem Ipsum
![Instal Wordpress](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_Instalasi_WordPress/Screenshot_3.jpg)


  4. Lorem Ipsum
![Instal Wordpress](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_Instalasi_WordPress/Screenshot_4.jpg)


  5. Lorem Ipsum
![Instal Wordpress](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_Instalasi_WordPress/Screenshot_5.jpg)


  6. Lorem Ipsum
![Instal Wordpress](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_Instalasi_WordPress/Screenshot_6.jpg)


  7. Lorem Ipsum
![Instal Wordpress](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_Instalasi_WordPress/Screenshot_7.jpg)


  8. Lorem Ipsum
![Instal Wordpress](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_Instalasi_WordPress/Screenshot_8.jpg)


  9. Lorem Ipsum
![Instal Wordpress](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_Instalasi_WordPress/Screenshot_9.jpg)


  10. Lorem Ipsum
![Instal Wordpress](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_Instalasi_WordPress/Screenshot_10.jpg)


  11. Lorem Ipsum
![Instal Wordpress](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_Instalasi_WordPress/Screenshot_11.jpg)


  12. Lorem Ipsum
![Instal Wordpress](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_Instalasi_WordPress/Screenshot_12.jpg)


  13. Lorem Ipsum
![Instal Wordpress](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_Instalasi_WordPress/Screenshot_13.jpg)


  14. Lorem Ipsum
![Instal Wordpress](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_Instalasi_WordPress/Screenshot_14.jpg)


  15. Lorem Ipsum
![Instal Wordpress](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_Instalasi_WordPress/Screenshot_15.jpg)


  16. Lorem Ipsum
![Instal Wordpress](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_Instalasi_WordPress/Screenshot_16.jpg)


  17. Lorem Ipsum
![Instal Wordpress](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_Instalasi_WordPress/Screenshot_17.jpg)


  18. Lorem Ipsum  
![Instal Wordpress](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_Instalasi_WordPress/Screenshot_18.jpg)


  19. Lorem Ipsum
![Instal Wordpress](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_Instalasi_WordPress/Screenshot_19.jpg)


#### 2. Langkah Instalasi Plugin Wordpress


* ##### Plugin CP Reservation Calendar 1.1.6

  1. Lorem Ipsum
![Image]()

* ##### Plugin League Manager 3.9.1.1

  1. Lorem Ipsum
![Image]()

* ##### Plugin Video Player 1.5.16

  1. Lorem Ipsum
![Instal Video Player](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_Instalasi_Plugin_VideoPlayer/Screenshot_1.jpg)


  2. Lorem Ipsum
![Instal Video Player](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_Instalasi_Plugin_VideoPlayer/Screenshot_2.jpg)


  3. Lorem Ipsum
![Instal Video Player](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_Instalasi_Plugin_VideoPlayer/Screenshot_3.jpg)


  4. Lorem Ipsum
![Instal Video Player](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_Instalasi_Plugin_VideoPlayer/Screenshot_4.jpg)


  5. Lorem Ipsum
![Instal Video Player](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_Instalasi_Plugin_VideoPlayer/Screenshot_5.jpg)


  6. Lorem Ipsum
![Instal Video Player](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_Instalasi_Plugin_VideoPlayer/Screenshot_6.jpg)


  7. Lorem Ipsum
![Instal Video Player](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_Instalasi_Plugin_VideoPlayer/Screenshot_7.jpg)


  8. Lorem Ipsum
![Instal Video Player](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_Instalasi_Plugin_VideoPlayer/Screenshot_8.jpg)


  9. Lorem Ipsum
![Instal Video Player](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_Instalasi_Plugin_VideoPlayer/Screenshot_9.jpg)


  10. Lorem Ipsum
![Instal Video Player](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_Instalasi_Plugin_VideoPlayer/Screenshot_10.jpg)


  11. Lorem Ipsum
![Instal Video Player](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_Instalasi_Plugin_VideoPlayer/Screenshot_11.jpg)


  12. Lorem Ipsum
![Instal Video Player](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_Instalasi_Plugin_VideoPlayer/Screenshot_12.jpg)


  13. Lorem Ipsum
![Instal Video Player](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_Instalasi_Plugin_VideoPlayer/Screenshot_13.jpg)


  14. Lorem Ipsum
![Instal Video Player](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_Instalasi_Plugin_VideoPlayer/Screenshot_14.jpg)


  15. Lorem Ipsum  
![Instal Video Player](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_Instalasi_Plugin_VideoPlayer/Screenshot_15.jpg)


  16. Lorem Ipsum
![Instal Video Player](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_Instalasi_Plugin_VideoPlayer/Screenshot_16.jpg)


  17. Lorem Ipsum
![Instal Video Player](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_Instalasi_Plugin_VideoPlayer/Screenshot_17.jpg)


#### 3. Langkah Uji Penetrasi SQL Injection 

Pada tahap ini, kami melakukan uji penetrasi berikut :

1. Plugin Video Player 1.5.16 dengan tools WPScan dan Mitmproxy

2. Plugin X dengan tools Y

3. Plugin X dengan tools Y


##### 1. Plugin Video Player 1.5.16 dengan tools WPScan dan Mitmproxy

  1. Lorem Ipsum
![Skenario WPScan dan Mitmproxy](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_SQLInjection_WPScan_VideoPlayer/Screenshot_1.jpg)


  2. Lorem Ipsum
![Skenario WPScan dan Mitmproxy](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_SQLInjection_WPScan_VideoPlayer/Screenshot_2.jpg)


  3. Lorem Ipsum
![Skenario WPScan dan Mitmproxy](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_SQLInjection_WPScan_VideoPlayer/Screenshot_3.jpg)


  4. Lorem Ipsum
![Skenario WPScan dan Mitmproxy](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_SQLInjection_WPScan_VideoPlayer/Screenshot_4.jpg)


  5. Lorem Ipsum
![Skenario WPScan dan Mitmproxy](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_SQLInjection_WPScan_VideoPlayer/Screenshot_5.jpg)


  6. Lorem Ipsum
![Skenario WPScan dan Mitmproxy](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_SQLInjection_WPScan_VideoPlayer/Screenshot_6.jpg)


  7. Lorem Ipsum
![Skenario WPScan dan Mitmproxy](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_SQLInjection_WPScan_VideoPlayer/Screenshot_7.jpg)


  8. Lorem Ipsum
![Skenario WPScan dan Mitmproxy](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_SQLInjection_WPScan_VideoPlayer/Screenshot_8.jpg)


  9. Lorem Ipsum
![Skenario WPScan dan Mitmproxy](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_SQLInjection_WPScan_VideoPlayer/Screenshot_9.jpg)


  10. Lorem Ipsum
![Skenario WPScan dan Mitmproxy](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_SQLInjection_WPScan_VideoPlayer/Screenshot_10.jpg)


  11. Lorem Ipsum
![Skenario WPScan dan Mitmproxy](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_SQLInjection_WPScan_VideoPlayer/Screenshot_11.jpg)


  12. Lorem Ipsum
![Skenario WPScan dan Mitmproxy](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_SQLInjection_WPScan_VideoPlayer/Screenshot_12.jpg)


  13. Lorem Ipsum
![Skenario WPScan dan Mitmproxy](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_SQLInjection_WPScan_VideoPlayer/Screenshot_13.jpg)


  14. Lorem Ipsum
![Skenario WPScan dan Mitmproxy](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_SQLInjection_WPScan_VideoPlayer/Screenshot_14.jpg)


  15. Lorem Ipsum
![Skenario WPScan dan Mitmproxy](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_SQLInjection_WPScan_VideoPlayer/Screenshot_15.jpg)


  16. Lorem Ipsum
![Skenario WPScan dan Mitmproxy](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_SQLInjection_WPScan_VideoPlayer/Screenshot_16.jpg)


  17. Lorem Ipsum
![Skenario WPScan dan Mitmproxy](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_SQLInjection_WPScan_VideoPlayer/Screenshot_17.jpg)


  18. Lorem Ipsum
![Skenario WPScan dan Mitmproxy](https://raw.githubusercontent.com/ronayumik/PKSJ/master/Tugas2/Screenshot_SQLInjection_WPScan_VideoPlayer/Screenshot_18.jpg)


##### 2. Plugin X dengan tools Y

##### 3. Plugin X dengan tools Y


## 4. Kesimpulan dan Saran

  1. 
