# **Tugas 1 PKSJ - Ganjil 2016/2017**


## Pendahuluan

Tugas ini dibuat untuk menyelesaikan Tugas 1 pada matakuliah Perancangan Keamanan & Sistem Jaringan (PKSJ) Semester Ganjil 2016/2017, Teknik Informatika ITS, Surabaya
 
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

**2. Tools yang digunakan**

### Basic Tool

* **Wordpress**, adalah sebuah aplikasi sumber terbuka (open source) yang sangat populer digunakan sebagai mesin blog (blog engine). WordPress dibangun dengan bahasa pemrograman PHP dan basis data (database) MySQL. PHP dan MySQL, keduanya merupakan perangkat lunak sumber terbuka (open source software) ( [link](https://id.wikipedia.org/wiki/WordPress) )

### Plugin yang diinstal & Kelemahannya *

* **CP Reservation Calendar 1.1.6** adalah plugin wordpress untuk reservasi suatu tempat. Kelemahan pada plugin ini terdapat pada file dex_reservations.php, pada fungsi berikut

''' 
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
'''

Kelemahannya adalah parameter [ CP_CALENDAR_ID ] yang tidak divalidasi / *escape parameter* . Sumber : ([exploit-db](https://www.exploit-db.com/exploits/38187/))

* **League Manager 3.9.11**


* **Video Player 1.5.16**

*Cracking Tool*

* **SQLMap**, adalah tools opensource yang mendeteksi dan melakukan exploit pada bug SQL injection secara otomatis. dengan melakukan serangan SQL injection seorang attacker dapat mengambil alih serta memanipulasi sebuah database di dalam sebuah server. ( [link](www.sqlmap.org) )

* **WPScan** Lorem Ipsum [link](Lorem ipsum)


## Uji Penetrasi 1


#### 1. Langkah Instalasi Wordpress
  1. Lorem Ipsum
![Lorem Ipsum]()


#### 2. Langkah Instalasi Plugin Wordpress


##### Plugin CP Reservation Calendar 1.1.6

  1. Lorem Ipsum
![Image]()

##### Plugin League Manager 3.9.11

  1. Lorem Ipsum
![Image]()

##### Plugin Video Manager 1.5.16

  1. Lorem Ipsum
![Image]()




#### 3. Langkah Uji Penetrasi SQL Injection 

Pada tahap ini, kami melakukan uji penetrasi berikut :

1. Plugin X dengan tools Y

2. Plugin X dengan tools Y

3. Plugin X dengan tools Y


##### 1. Plugin X dengan tools Y

##### 2. Plugin X dengan tools Y

##### 3. Plugin X dengan tools Y


## 4. Kesimpulan dan Saran

  1. 




