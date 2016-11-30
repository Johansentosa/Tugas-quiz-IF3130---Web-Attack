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
![Alt text](https://raw.githubusercontent.com/Johansentosa/Tugas-quiz-IF3130-Web-Attack/master/images/home.png "http://infokumkm.surakarta.go.id/home.php")

