<img width="817" height="688" alt="image" src="https://github.com/user-attachments/assets/c5f51c5a-2607-41ff-9def-bb38f4236e8e" /># Pemrogramahn berbasis perangkat bergerak

## mengenai ASYNC

<img width="750" height="415" alt="image" src="https://github.com/user-attachments/assets/7ff55c88-b1f7-496e-8dbc-c0f912645259" />


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

## Pertanyaan: Komponen yang selalu disertakan dalam bundle aplikasi hybrid adalah ....

Jawaban yang benar adalah B. webview.

Penjelasan
Aplikasi Hybrid (seperti yang dibuat dengan Ionic dan Vue.js) pada dasarnya adalah aplikasi web yang dijalankan di lingkungan mobile.

Webview adalah komponen kunci yang selalu disertakan. Ini berfungsi sebagai browser mini (tanpa chrome atau UI browser standar) yang disematkan di dalam container aplikasi native (Android/iOS).

Tugas utama webview adalah me-render dan menampilkan semua kode aplikasi web Anda (HTML, CSS, dan logika Vue/TypeScript) kepada pengguna di perangkat mobile. Tanpa webview, aplikasi hybrid tidak dapat berfungsi atau menampilkan konten webnya.

## Bagian dari Express yang digunakan untuk mendefinisikan pola URL yang diakses oleh user adalah:

C. route

Penjelasan Singkat
Dalam Express.js (dan konsep MVC/MVVM pada umumnya, yang juga relevan dengan Vue.js/Ionic):

Route (Rute): Bertanggung jawab untuk mendefinisikan pola URL dan metode HTTP (GET, POST, PUT, DELETE, dll.) yang akan merespons permintaan. Ini menghubungkan URL tertentu ke fungsi handler yang sesuai.

Controller: Berisi logika bisnis utama yang menangani permintaan setelah route mengarahkannya.

Model: Mewakili data dan logika yang berinteraksi dengan database atau sumber data lainnya.

View: (Dalam konteks Express.js, ini sering berarti mesin template seperti Pug atau EJS) Bertanggung jawab untuk menyajikan data dalam format yang dapat dilihat oleh pengguna (HTML). (Dalam konteks Vue.js/Ionic, "View" adalah komponen Vue yang merender UI).

## Untuk mengakses RESTful API endpoint, dapat digunakan ....

A. semua yang dapat berfungsi sebagai http-client B. postman C. curl D. wget

Jawaban
A. semua yang dapat berfungsi sebagai http-client

## Soal Ketiga: Paket untuk Membangun RESTful API dengan TypeScript
Soal:

Paket yang diperlukan untuk membangun RESTful API endpoint menggunakan TypeScript adalah ....

A. nodemon B. express C. concurrently D. @types/express dan express

Jawaban
D. @types/express dan express

## Soal Keempat: Membaca File JSON dalam Import di TypeScript
Soal:

Supaya dapat membaca file JSON secara langsung dalam import, maka TypeScript memerlukan konfigurasi di tsconfig.json ....

A. tidak perlu konfigurasi apapun, secara default sudah dapat langsung import json B. "jsonImport": true C. "jsonModuleResolver": true D. "resolveJsonModule": true

Jawaban
D. "resolveJsonModule": true

Penjelasan (Fokus pada TypeScript)
Secara default, TypeScript (seperti JavaScript/Node.js lama) tidak memperlakukan file .json sebagai modul yang dapat di-import.

## Kegunaan app.get('/', (req, res) => { ... })
Soal:

Bagian kode sumber route di express untuk server: app.get('/', (req, res) => { ... }) digunakan untuk mengekspos ....

A. http://server:port/resources B. http://server:port/api C. http://server:port/ D. root directory filesystem (/)

Jawaban
C. http://server:port/

Penjelasan
Dalam routing Express.js, string pertama dalam fungsi route (yaitu '/' dalam contoh ini) menentukan jalur (path) URL yang akan dipetakan ke handler tersebut.

Jalur '/' secara universal melambangkan root path atau jalur utama (homepage) dari sebuah server.

Jika server berjalan pada http://server:port, maka route app.get('/') akan merespons permintaan yang ditujukan ke alamat lengkap http://server:port/

## Instalasi Vue menggunakan CDN
Soal:

Pada dasarnya instalasi Vue yang dibuat menggunakan CDN sama dengan ....

A. npm B. vue/cli C. vue@next D. .tar.gz

Jawaban
A. npm

Penjelasan (Fokus pada Vue.js)
Instalasi Vue.js dapat dilakukan dengan beberapa cara:

CDN (Content Delivery Network): Anda menambahkan tag <script> ke file HTML Anda. Ini mengunduh library Vue.js yang sudah terkompilasi dalam format Global Build (yang diekspos sebagai variabel global seperti Vue). Ini adalah cara termudah untuk membuat prototyping atau mengintegrasikan Vue ke dalam proyek HTML/JS yang sudah ada.

NPM (Node Package Manager) / Bundler: Anda menginstal Vue sebagai modul menggunakan npm install vue atau yarn add vue. Saat Anda meng-import Vue dalam proyek Anda, Anda akan menggunakan Module Build (ES Modules) yang harus diproses oleh bundler seperti Webpack, Vite, atau Rollup.

## Mendefinisikan Fungsi Button di Vue.js
Soal:

Untuk mendefinisikan suatu fungsi yang bisa dikerjakan oleh button pada saat di-klik, maka di dalam root component kita gunakan ....

A. created B. mounted C. methods D. updated

Jawaban
C. methods

Penjelasan (Fokus pada Vue.js)
Dalam Vue Options API (yang masih relevan di Vue 3):

methods: Ini adalah objek tempat Anda mendefinisikan fungsi-fungsi JavaScript kustom yang ingin Anda panggil di dalam template komponen, termasuk fungsi yang terikat pada event pengguna seperti klik tombol (@click atau v-on:click).

## Fungsi Props dalam Vue.js
Soal:

Props berfungsi untuk ....

A. mendefinisikan komponen. B. mendefinisikan atribut yang akan digunakan oleh komponen. C. mendefinisikan method yang akan digunakan oleh komponen. D. mendefinisikan nilai kembalian dari data.

Jawaban
B. mendefinisikan atribut yang akan digunakan oleh komponen.

Penjelasan (Fokus pada Vue.js)
Dalam Vue.js, Props (Properties) adalah mekanisme utama untuk mengomunikasikan data dari komponen induk (parent) ke komponen anak (child).

Props pada dasarnya adalah custom attribute yang Anda definisikan pada komponen anak ketika Anda menggunakannya di template komponen induk.

## Definisi Kode Sumber pada Fase Siklus Hidup
Soal:

Pemrogram bisa mendefinisikan berbagai kode sumber yang bisa dijalankan pada suatu fase tertentu dari siklus hidup instan aplikasi dan komponen. Definisi pada fase tertentu tersebut disebut dengan ....

A. component hooks B. component filtering C. component creation D. lifecycle hooks.

Jawaban
D. lifecycle hooks.

Penjelasan (Fokus pada Vue.js/Ionic)
Dalam framework modern seperti Vue.js dan Ionic (yang sering menggunakan konsep komponen yang sama), setiap komponen atau instan aplikasi memiliki siklus hidup (yaitu tahapan dari saat dibuat hingga dihancurkan).

## Fungsi untuk Membuat Rute (Vue Router)
Soal: Untuk membuat routing, kita bisa menggunakan paket Vue Router. Dalam paket tersebut, terdapat fungsi untuk membuat rute, yaitu .... A. createRouter B. createRoute C. createRoutes D. addRoute

Jawaban: A. createRouter

Penjelasan (Fokus pada Vue.js): Dalam Vue Router versi 4 (standar untuk Vue 3 dan sering digunakan dengan proyek TypeScript), fungsi yang harus di-import dari paket vue-router untuk membuat instansi router adalah createRouter.

## Elemen untuk Menampilkan Routing
Soal: Elemen yang digunakan untuk menampilkan routing adalah .... A. router-link B. router-view C. route-link D. route-view

Jawaban: B. router-view

Penjelasan (Fokus pada Vue.js): Komponen <router-view> adalah elemen placeholder wajib dari Vue Router. Elemen ini berfungsi sebagai lokasi di mana komponen Vue yang sesuai dengan URL saat ini akan dirender atau ditampilkan.

## Atribut :to pada Vue Router
Soal: Atribut berikut ini :to="{ name: 'Awal' }" adalah .... A. variabel untuk view B. variabel untuk template C. direktif D. named router

Jawaban
D. named router

Penjelasan (Fokus pada Vue.js/Vue Router)
Atribut :to="{ name: 'Awal' }" digunakan pada komponen <router-link> dalam Vue Router.

Titik dua (:) di depan to menunjukkan v-bind atau shorthand untuk binding atribut dinamis, artinya nilai yang diberikan adalah ekspresi JavaScript.

Nilai yang diberikan ({ name: 'Awal' }) adalah objek yang mengacu pada sebuah rute yang telah didefinisikan dalam konfigurasi Vue Router menggunakan nama rute (name: 'Awal'), bukan jalurnya (path) secara langsung.

## Mengakses Route Parameter di Template Vue
Soal: Jika di dalam router didefinisikan /pegawai/:npp, maka kita bisa mengakses nilai npp di template menggunakan .... A. $router.params.npp B. $route.params.npp C. router.params.npp D. router.param.npp

Jawaban
B. $route.params.npp

Penjelasan (Fokus pada Vue.js/Vue Router)
$route vs. $router:

$router (dengan R besar) adalah instansi router global (digunakan untuk programmatic navigation seperti $router.push(...)).

$route (dengan R kecil) adalah objek rute yang aktif saat ini dan berisi informasi spesifik rute, termasuk path, query, dan parameter (params).

## Berikut adalah direktif yang digunakan untuk kondisional, kecuali .... A. v-if B. v-if-else C. v-bind D. v-show

Jawaban
C. v-bind

Penjelasan (Fokus pada Vue.js)
Dalam Vue.js, direktif (arahan) digunakan untuk memanipulasi DOM.

Direktif Kondisional: Direktif yang mengontrol apakah suatu elemen akan dirender atau ditampilkan berdasarkan kondisi Boolean.

v-if dan v-if-else: Digunakan untuk rendering kondisional. Elemen benar-benar dihapus/ditambahkan dari DOM.

v-show: Digunakan untuk menampilkan/menyembunyikan elemen dengan memanipulasi properti CSS display. Elemen tetap ada di DOM.

## Direktif untuk Menampilkan Array (Looping)
Soal: Untuk menampilkan suatu array, digunakan direktif .... A. v-model B. v-array C. v-for D. v-bind:array

Jawaban
C. v-for

Penjelasan (Fokus pada Vue.js)
Direktif v-for dalam Vue.js dirancang khusus untuk melakukan iterasi atau looping melalui daftar data (array atau objek) dan merender sekumpulan elemen atau komponen berdasarkan data tersebut. * Contoh penggunaan: <li v-for="item in arrayData" :key="item.id">{{ item.nama }}</li>

A. v-model: Digunakan untuk two-way data binding pada elemen formulir (form input).

B. v-array: Bukan direktif Vue.js yang standar.

D. v-bind:array: Digunakan untuk mengikat nilai array ke atribut HTML atau prop komponen, bukan untuk menampilkan seluruh isinya melalui looping.

## Interpolasi Teks yang Valid
Soal: Berikut adalah interpolasi teks yang valid dalam template, kecuali .... A. {{ nama }} B. {{ ok ? 'Ya' : 'Tidak' }} C. {{ pesan.toLowerCase() }} D. <p v-text></p>

Jawaban
D. <p v-text></p>

Penjelasan (Fokus pada Vue.js)
Interpolasi Teks dalam template Vue.js adalah penggunaan kurung kurawal ganda ({{ ... }}) untuk menampilkan data. Ekspresi di dalamnya harus diselesaikan menjadi nilai string.

## CSS Scoped pada Template Vue
Soal: Untuk memastikan bahwa CSS untuk template hanya berlaku pada template tersebut, gunakan .... A. <style v-scoped=true> B. <style scoped> C. <style v-private=true> D. <style v-protected=true>

Jawaban
B. <style scoped>

Penjelasan (Fokus pada Vue.js)
CSS Scoped: Dalam Single-File Component (SFC) Vue (.vue file), menambahkan atribut scoped pada tag <style> akan secara otomatis membatasi aturan CSS hanya berlaku pada elemen yang ada di dalam template komponen saat ini. * Vue.js mencapai ini dengan menambahkan atribut data unik (e.g., data-v-xxxxxx) ke elemen template dan juga ke selector CSS yang dikompilasi, sehingga mencegah style tersebut "bocor" (leak) ke komponen lain.


# Event Modifier untuk Satu Kali Event
Soal: Modifier yang digunakan untuk menangani event hanya sekali saja adalah .... A. .stopFirst B. .first C. .stopAfterFirst D. .once

Jawaban
D. .once

Penjelasan (Fokus pada Vue.js)
Dalam Vue.js, Anda dapat menggunakan Event Modifiers (seperti .stop, .prevent, dll.) pada direktif v-on (atau shorthand-nya @) untuk memodifikasi perilaku event DOM.

.once adalah modifier yang memastikan bahwa event handler yang terkait hanya akan dipanggil satu kali saja. Setelah event dipicu dan handler dijalankan, listener akan

## Deskripsi Handler yang Benar (Vue.js Events)
Soal: Berikut adalah contoh deskripsi handler yang benar, kecuali .... A. "<template></template>" B. "counter += 1, funct1(2, 1)" C. "counter += 1, next += 1" D. "func1(2, 1), func2()"

Jawaban
A. "<template></template>"

Penjelasan (Fokus pada Vue.js Events)
Event handler yang didefinisikan pada direktif v-on (atau @ seperti @click, @change) harus berupa ekspresi JavaScript yang valid atau nama fungsi (method) yang ada di komponen. * B, C, D (Valid): Semua opsi ini adalah ekspresi JavaScript valid yang terdiri dari satu atau lebih pernyataan yang dipisahkan oleh koma (misalnya, menetapkan nilai (counter += 1) atau memanggil fungsi (funct1(2, 1))). Ini sering digunakan saat handler didefinisikan secara inline di template.

## Definisi Single File Component (SFC)
Soal: Meletakkan unsur-unsur template, script, serta style dalam satu file disebut dengan .... A. component definition B. component registration C. separation of concerns D. single file components

Jawaban
D. single file components

Penjelasan (Fokus pada Vue.js)
Single File Component (SFC) adalah format file khas Vue.js (ekstensi .vue) di mana definisi komponen (logika script), struktur tampilan (template), dan style (CSS) ditempatkan bersama dalam satu file yang terstruktur. * Konsep ini sangat sentral dalam pengembangan modern Vue, termasuk ketika menggunakan TypeScript dan membangun aplikasi dengan Ionic (yang didasarkan pada komponen).


## Penempatan Fungsi untuk Perubahan Reaktif
Soal: Supaya setiap perubahan atau pembaharuan bisa langsung mempunyai efek, maka sebaiknya suatu function diletakkan di .... A. created B. methods C. computed D. data()

Jawaban
C. computed

Penjelasan (Fokus pada Vue.js Reaktivitas)
Dalam Vue.js, jika suatu fungsi atau properti data menghasilkan nilai yang bergantung pada perubahan data reaktif lainnya, fungsi tersebut harus ditempatkan di computed properti.

Computed Properties secara otomatis mendeteksi dependensi reaktif. Kapan pun dependensi data berubah, fungsi computed akan dijalankan ulang, memastikan hasil pembaharuan segera berlaku (immediate effect). * methods (B) adalah untuk menjalankan fungsi secara manual (misalnya, melalui event @click) dan tidak memiliki caching atau ketergantungan reaktif otomatis seperti computed.

## Perbedaan computed dengan methods
Soal: Salah satu perbedaan antara computed dengan methods adalah .... A. computed harus menghasilkan nilai kembalian, sementara methods tidak perlu. B. computed digunakan untuk elemen tertentu saja, sementara methods bisa untuk semua elemen. C. computed tidak perlu di-bind, sementara methods harus di-bind. D. computed bisa menggunakan argument, sementara methods tidak bisa.

Jawaban
A. computed harus menghasilkan nilai kembalian, sementara methods tidak perlu.

Penjelasan (Fokus pada Vue.js)
Perbedaan utama yang paling akurat di antara opsi yang tersedia adalah:

Computed: Fungsi computed harus selalu mengembalikan nilai (return value) karena tujuannya adalah menghasilkan properti data baru dari properti data yang sudah ada. Fungsi ini bertindak seperti properti yang di-cache.

Methods: Fungsi di dalam methods tidak harus menghasilkan nilai kembalian; fungsinya mungkin hanya menjalankan efek samping (side effect) seperti memanggil API atau memodifikasi properti data lain.

***
# Bab 3

## YARGS
Soal Pertama: Pustaka untuk Mengelola Argumen CLI (Kecuali)
Soal: Berikut adalah berbagai pustaka yang bisa digunakan untuk mengelola argumen dari command line, kecuali .... A. commandliner B. commander C. yargs D. minimalist

Jawaban
A. commandliner

Penjelasan (Fokus pada Tooling)
Pilihan B (commander), C (yargs), dan D (minimalist - kemungkinan merujuk pada minimist) adalah library Node.js yang sangat populer dan umum digunakan untuk mem-parsing argumen command line (command line arguments).

commandliner bukanlah nama paket standar atau umum yang dikenal dalam ekosistem Node.js/TypeScript untuk tujuan ini.

2. Soal Kedua: Argumen Wajib di yargs
Soal: Untuk memastikan bahwa suatu opsi argumen di yargs wajib, gunakan .... A. optionalDemand = true; B. optionalArgument = false; C. demandOption = true; D. demandArgument = false;

Jawaban
C. demandOption = true;

Penjelasan (Fokus pada Tooling)
Dalam library yargs, properti yang digunakan untuk menandai suatu opsi sebagai wajib (required) adalah demandOption.

Nilai harus diatur ke true untuk memberlakukan persyaratan ini.

3. Soal Ketiga: Mengambil Argumen di yargs
Soal: Untuk mengambil argumen di yargs (dengan asumsi argv adalah instan dari yargs), bisa menggunakan .... A. argv['nama'] B. argv.prototype.nama C. argv.nama D. argv[urutan]

Jawaban
C. argv.nama

Penjelasan (Fokus pada Tooling)
Ketika yargs telah mem-parsing argumen command line, hasil parsing (yang disimpan dalam variabel seperti argv) adalah objek yang propertinya sesuai dengan nama-nama argumen (atau alias-nya).

Argumen yang di-parse dapat diakses langsung sebagai properti pada objek argv menggunakan notasi titik, misalnya argv.nama, di mana nama adalah nama opsi yang didefinisikan atau diberikan oleh pengguna.

***
# Catatan kecil

Point | Penjelasan
--- | ---
 webview | Komponen yang selalu disertakan dalam bundle aplikasi hybrid adalah:
