# Pemrogramahn berbasis perangkat bergerak

## mengenai ASYNC

<img width="792" height="527" alt="image" src="https://github.com/user-attachments/assets/349e2f3e-1daa-48a3-b748-2df4fbced6e9" />

## 


## Dalam pemrograman asinkron berbasis Promise di TypeScript

(dan JavaScript), ketika Anda memiliki serangkaian operasi asinkron yang harus dijalankan secara berurutan (di mana operasi kedua bergantung pada keberhasilan atau hasil dari operasi pertama), mekanisme yang digunakan adalah Promise Chaining.

Sebagai alternatif modern dari Promise Chaining, kita juga dapat menggunakan async/await (yang pada dasarnya hanya sintaks yang lebih bersih untuk Promise Chaining).

------------
[Pilihan salah]

a. nodemon: Ini adalah utilitas yang digunakan untuk memantau perubahan file dan memulai ulang server Node.js. Tidak ada hubungannya dengan menjalankan Promise secara berurutan di sisi klien (Vue/Ionic).

b. generic: Ini adalah fitur TypeScript (seperti <T>) yang memungkinkan Anda membuat komponen yang dapat digunakan kembali dengan jenis data yang berbeda. Ini adalah konsep pengetikan, bukan kontrol alur asinkron.

c. union type: Ini adalah fitur TypeScript (seperti string | number) yang memungkinkan variabel memiliki salah satu dari beberapa jenis data. Ini adalah konsep pengetikan, bukan kontrol alur asinkron.



## Aplikasi hybrid pada dasarnya adalah aplikasi berbasis web (HTML, CSS, JavaScript) yang dibungkus dalam wadah native.

Agar aplikasi hybrid dapat berinteraksi dengan fitur tingkat rendah (low level) atau fungsi sistem operasi spesifik (seperti kamera, GPS, atau file system), ia memerlukan jembatan. Jembatan ini disediakan oleh:

Native API Plugins: Ini adalah modul atau plugins yang ditulis menggunakan kode native (misalnya Java untuk Android atau Swift/Objective-C untuk iOS) yang mengekspos API perangkat keras atau sistem, sehingga dapat dipanggil oleh kode web (JavaScript) di dalam aplikasi hybrid tersebut.


## Untuk mengakses sistem aras rendah, Ionic menggunakan komponen dari Capacitor.

Penjelasan Singkat
Capacitor adalah runtime dan jembatan terbuka (cross-platform bridge) yang dikembangkan oleh tim Ionic.

Capacitor memungkinkan aplikasi web (seperti aplikasi yang dibuat dengan Ionic) untuk mengakses fungsionalitas native perangkat (seperti kamera, file system, dll.) pada iOS, Android, dan web dengan cara yang seragam dan modern.

Sebelum Capacitor, Ionic umumnya menggunakan Apache Cordova (yang kini juga masih didukung, tetapi Capacitor lebih modern).

## Salah satu bagian dari Ionic adalah Web components. Bagian ini dikembangkan oleh Ionic dengan menggunakan ....
Jawaban yang benar adalah B. stencil.

Penjelasan: Stencil adalah compiler yang dikembangkan oleh tim Ionic untuk membangun Web Components (custom elements). Ionic menggunakan Stencil untuk mengembangkan komponen UI mereka sendiri.

## Salah satu bagian dari Ionic adalah Web components. Bagian ini dikembangkan oleh Ionic dengan menggunakan ....
Jawaban yang benar adalah B. stencil.

Penjelasan: Stencil adalah compiler yang dikembangkan oleh tim Ionic untuk membangun Web Components (custom elements) yang berkinerja tinggi dan berjalan di semua framework (seperti React, Vue, atau Vanilla JS), dan ini digunakan untuk mengembangkan komponen UI inti Ionic.

## Suatu generics dapat di-extend untuk keperluan filtering kondisi tertentu yang dianggap valid untuk memanggil suatu fungsi dengan cara ....
Jawaban yang benar adalah C. menggunakan interface dan extends.

Penjelasan: Dalam TypeScript, untuk membatasi atau "filter" tipe data yang boleh digunakan oleh generic (generic constraints), kita menggunakan kata kunci extends yang diikuti oleh interface (atau class) yang mendefinisikan properti atau kondisi yang harus dipenuhi oleh tipe data generic tersebut.

***
# Catatan kecil

Point | Penjelasan
--- | ---
 webview | Komponen yang selalu disertakan dalam bundle aplikasi hybrid adalah:
