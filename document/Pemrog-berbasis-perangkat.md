# Pemrogramahn berbasis perangkat bergerak

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

## Axios

Soal Pertama: Membuat Instansi Axios
Soal: Instance dari axios bisa dibuat menggunakan .... A. new axiosInstance() B. new axiosHttpClient() C. axios.httpClient() D. axios.create()

Jawaban
D. axios.create()

Penjelasan (Fokus pada Tooling/TypeScript)
Untuk membuat instansi custom dari Axios (biasanya untuk mengatur base URL, headers, atau timeout yang berbeda dari global default), fungsi yang digunakan adalah axios.create(config). * Instansi ini sangat berguna dalam proyek TypeScript/Vue.js untuk membuat client API yang terpisah untuk layanan yang berbeda (misalnya, satu untuk API internal dan satu untuk API eksternal).

2. Soal Kedua: Melihat Tipe File dari URL
Soal: Jika ingin melihat tipe file yang diambil dari URL menggunakan axios, maka pemrogram bisa gunakan .... A. response object B. response.headers['content-type'] C. response.headers['file-type'] D. response.data

Jawaban
B. response.headers['content-type']

Penjelasan (Fokus pada HTTP Protocol)
Ketika Axios (atau HTTP client mana pun) mengambil data dari URL, informasi tentang jenis data yang dikirimkan (misalnya application/json, image/png, text/html) terkandung dalam HTTP Response Headers.

Header standar yang digunakan untuk menunjukkan tipe media data adalah Content-Type.

Dalam objek respons Axios, header diakses melalui properti response.headers. Oleh karena itu, nilainya diakses melalui response.headers['content-type'].


## FSwrite

Soal Pertama: Hasil Penulisan Array ke File
Soal: Jika menyimpan data dalam bentuk array ke suatu file menggunakan fs/promises - writeFile, hasilnya adalah .... A. error B. array tertulis di file C. array akan dikonversi lebih dulu ke object sebelum ditulis D. array akan dikonversi menjadi string

Jawaban
D. array akan dikonversi menjadi string

Penjelasan (Fokus pada Node.js/File System)
Fungsi fs.writeFile (atau fs/promises.writeFile) di Node.js menerima data yang akan ditulis.

Jika data yang diberikan adalah array atau object JavaScript (bukan Buffer atau string), Node.js akan secara internal memanggil .toString() pada array tersebut.

Hasil dari .toString() pada array adalah string yang berisi elemen-elemen array yang dipisahkan oleh koma. Oleh karena itu, array akan dikonversi menjadi string sebelum ditulis ke file. (Jika ingin menyimpan array sebagai JSON, harus di-stringifikasi secara eksplisit menggunakan JSON.stringify()).

2. Soal Kedua: Fungsi Kode Sumber await fs.writeFile(f, data);
Soal: Potongan kode sumber berikut: await fs.writeFile(f, data); digunakan untuk .... A. memeriksa apakah nama file sesuai isi f bisa ditulisi B. memeriksa dan menuliskan isi data ke file bernama 'f' C. menuliskan isi dari data ke file dengan nama file 'f' D. menuliskan isi dari data ke file dengan nama sesuai isi f

Jawaban
C. menuliskan isi dari data ke file dengan nama file 'f'

Penjelasan (Fokus pada Node.js/TypeScript)
Dalam sintaks Node.js fs.writeFile(path, data, options), argumen pertama (f dalam contoh ini) mewakili jalur (path) atau nama file tempat penulisan data.

Argumen kedua (data dalam contoh ini) adalah konten atau data yang ingin ditulis.

Oleh karena itu, kode tersebut melakukan tindakan menuliskan isi dari variabel data ke file yang namanya ditentukan oleh variabel f.

## NPM RUN
Soal Pertama: Penempatan Definisi Script npm run
Soal: Untuk membuat supaya npm run bisa menjalankan script sesuai keinginan kita, maka definisi script tersebut diletakkan pada .... A. bagian scripts di package.json B. bagian scripts di tsconfig.json C. Bagian exec-scripts di tsconfig.json D. Bagian exec-scripts di package.json

Jawaban
A. bagian scripts di package.json

Penjelasan (Fokus pada Tooling)
Semua perintah yang dapat dijalankan melalui npm run <nama-perintah> harus didefinisikan dalam objek scripts yang terletak di dalam file package.json. * Misalnya, jika Anda ingin menjalankan server pengembangan Vue/Ionic, Anda akan mendefinisikan: "serve": "vue-cli-service serve" di dalam bagian scripts.

2. Soal Kedua: Karakter untuk Melewatkan Argumen ke npm run
Soal: Supaya argumen dari yargs bisa terbaca saat menggunakan npm run, maka karakter yang harus digunakan adalah .... A. " B. -- C. ' D. "argumen"

Jawaban
B. --

Penjelasan (Fokus pada Tooling)
Ketika menjalankan npm run <perintah>, npm akan mengonsumsi argumen yang ada.

Untuk meneruskan argumen tambahan dari command line kepada script yang sedang dijalankan (misalnya, script yang menggunakan yargs), Anda harus menggunakan pemisah ganda (--).

Contoh: npm run build -- --env=production

Argumen --env=production akan diteruskan kepada script build, yang kemudian dapat di-parse oleh library seperti yargs atau alat bundler.

## restfull API endpoint

Soal Pertama: HTTP Method yang Bukan Standar
Soal: Berikut ini adalah HTTP method yang bisa dikirimkan ke RESTful API endpoint, kecuali .... A. GET B. PUT C. PATCH D. QUERY

Jawaban
D. QUERY

Penjelasan (Fokus pada Protokol HTTP)
Protokol HTTP mendefinisikan method standar untuk berinteraksi dengan sumber daya (resources) pada RESTful API.

GET, PUT, dan PATCH semuanya adalah method HTTP standar yang digunakan untuk mengambil data, memperbarui seluruh sumber daya, dan memperbarui sebagian sumber daya, berturut-turut.

QUERY bukanlah method HTTP standar yang diakui oleh RFC HTTP. Metode yang relevan seringkali adalah HEAD, POST, DELETE, OPTIONS, selain yang disebutkan di atas.

2. Soal Kedua: Cara Mengambil Data JSON dari Server
Soal: Cara mengambil data dari server dalam format JSON supaya bisa diekspos di RESTful API endpoint adalah .... A. menggunakan pustaka fs di Node.js B. menempatkan file tersebut di src/resources, maka secara otomatis akan disertakan dalam kode sumber di controller. C. langsung diambil / dibaca menggunakan import. D. menggunakan pustaka khusus untuk mengolah data JSON.

Jawaban
D. menggunakan pustaka khusus untuk mengolah data JSON.

Penjelasan (Fokus pada Backend Node.js/TypeScript)
Dalam konteks server (seperti Express.js, yang sering digunakan dengan TypeScript), RESTful API endpoint perlu mengirimkan respons JSON yang benar.

## Restfull API

Soal Pertama: Format Serialisasi Data sebagai Respons API
Soal: Berikut adalah format serialisasi data yang dikirimkan sebagai respons ke client yang telah mengirimkan HTTP method dengan argumen resources .... A. harus JSON B. bisa JSON atau file-file standar di Web (HTML, CSS, PNG, dan lain-lain). C. harus JSON atau HTML atau file teks biasa. D. bisa dalam format apa saja

Jawaban
B. bisa JSON atau file-file standar di Web (HTML, CSS, PNG, dan lain-lain).

Penjelasan (Fokus pada REST/HTTP)
Meskipun JSON sangat umum digunakan untuk data terstruktur pada RESTful API, respons dari endpoint pada dasarnya adalah stream data HTTP yang memiliki Content-Type yang ditentukan.

Respons dapat berupa plain text, XML, HTML (untuk server-side rendering), atau data biner seperti gambar (PNG, JPEG) atau file CSS/JavaScript. Pilihan yang paling akurat adalah bahwa respons dapat berupa JSON (data terstruktur) atau file-file standar Web (data biner atau teks).

2. Soal Kedua: Hasil Berhasil (Fulfilled) dari Axios
Soal: Jika mengirimkan request ke RESTful API endpoint menggunakan axios, maka hasilnya jika berhasil (fulfilled) adalah .... A. response.data B. response C. response berupa serialisasi JSON D. status

Jawaban
A. response.data

Penjelasan (Fokus pada Axios/TypeScript)
Ketika Axios berhasil (janji/Promise di-fulfilled), ia mengembalikan objek respons. Objek respons ini memiliki properti seperti status, headers, dan data.

Properti response.data berisi payload (isi) dari respons server, yang merupakan data yang sebenarnya Anda butuhkan (biasanya objek JSON yang telah di-parse menjadi objek JavaScript/TypeScript).

3. Soal Ketiga: Penempatan Kode Sumber Koneksi Data di Vue
Soal: Dalam instan aplikasi Vue, kode sumber untuk koneksi pengambilan data ke RESTful API endpoint diletakkan pada .... A. di src/index.ts B. di semua komponen dan bagian yang memerlukan data dari RESTful API endpoint C. di direktori root src/ saja D. di src/components

Jawaban
B. di semua komponen dan bagian yang memerlukan data dari RESTful API endpoint

Penjelasan (Fokus pada Vue.js/Arsitektur)
Meskipun best practice adalah menggunakan layanan terpisah (service layer atau store seperti Pinia/Vuex) untuk mengelola logika fetching API, implementasi kode yang memicu pengambilan data (misalnya, memanggil apiService.fetchData()) pada akhirnya diletakkan di komponen (<script>) atau bagian aplikasi (store, router guard) yang secara langsung membutuhkan data tersebut.

Oleh karena itu, kode koneksi (atau pemanggilan fungsi koneksi) tersebar di semua bagian aplikasi yang memerlukan interaksi dengan API.

## Memeriksa Tipe Data dari Endpoint
Soal: Jika ingin memeriksa tipe dari data yang berasal dari suatu endpoint, kita bisa menggunakan .... A. response.headers['content-type'] B. response.header['content-type'] C. response.headers['file-type'] D. response.header['file-type']

Jawaban
A. response.headers['content-type']

Penjelasan (Fokus pada HTTP Protocol/Axios)
Ketika client (seperti yang dibuat dengan Vue.js dan TypeScript menggunakan Axios) menerima respons dari API endpoint, informasi tentang jenis data yang diterima (misalnya JSON, XML, atau teks) selalu terkandung dalam HTTP Response Headers.

## Alternatif Penggunaan RESTful API
Soal: Selain menggunakan RESTful API untuk endpoint, pemrogram juga bisa menggunakan .... A. Apache Flink B. Event processing C. GraphQL D. Service Oriented Architecture

Jawaban
C. GraphQL

Penjelasan (Fokus pada Konsep API)
RESTful API adalah gaya arsitektur yang sangat umum, namun memiliki alternatif utama dalam dunia backend dan client-side (seperti Vue.js/TypeScript).

GraphQL adalah bahasa kueri untuk API dan runtime untuk memenuhi kueri tersebut dengan data yang ada. Keuntungan utamanya adalah client dapat meminta hanya data yang mereka butuhkan, yang menjadikannya alternatif yang populer dan efisien untuk REST, terutama pada aplikasi mobile seperti yang dibuat dengan Ionic.

## Menampilkan Data JSON dari Endpoint ke Halaman Web (Vue)
Soal: Hasil request ke endpoint dengan format JSON bisa ditampilkan ke halaman Web dengan cara .... A. langsung dikonversikan ke list yang bisa diakses oleh Vue B. langsung dimasukkan ke template menggunakan <script>...</script> C. langsung dimasukkan ke array untuk ditampilkan ke template menggunakan v-for D. dikonversikan terlebih dahulu ke TypedArray, setelah itu baru masukkan ke template

Jawaban
C. langsung dimasukkan ke array untuk ditampilkan ke template menggunakan v-for

Penjelasan (Fokus pada Vue.js Reaktivitas)
Ketika Vue/Axios menerima respons JSON dari endpoint, data JSON tersebut secara otomatis di-parse menjadi objek atau array JavaScript/TypeScript (misalnya, response.data).

## Kegunaan Decorator
Soal: Decorator digunakan untuk .... A. mengubah arah eksekusi di Vue B. Metadata Programming C. mengatur supaya nilai kembalian di Vue sesuai dengan yang diinginkan pemrogram D. meniadakan subclassing yang tidak diperlukan.

Jawaban
B. Metadata Programming

Penjelasan (Fokus pada TypeScript)
Decorator adalah fitur eksperimental (tapi umum digunakan) di TypeScript yang memungkinkan Anda menambahkan anotasi dan sintaks metaprogramming ke kelas, method, properti, atau parameter.

Tujuannya adalah untuk Metaprogramming—yaitu, menulis kode yang memproses atau memanipulasi kode lain (seperti menambahkan metadata atau perilaku tambahan) pada waktu desain (design time). * Dalam konteks Vue dan TypeScript, Decorator seperti @Component digunakan untuk secara otomatis membaca dan memproses metadata kelas dan mengubahnya menjadi objek opsi komponen Vue standar.

2. Soal Kedua: Penggantian @Component di Vue-Class-Component v8.x.x
Soal: Pada vue-class-component versi 8.x.x, @Component digantikan dengan .... A. @Class B. @Options C. @VueClass D. @VueComponent

Jawaban
D. @VueComponent

Penjelasan (Fokus pada Vue.js/TypeScript)
Dalam upaya untuk meningkatkan kompatibilitas dengan Vue 3 dan mengadopsi penamaan yang lebih jelas, library vue-class-component (yang memungkinkan penulisan komponen Vue menggunakan kelas TypeScript) mengganti decorator utama @Component menjadi @VueComponent pada versi 8.x.x.

## Vue dan vue ke ts
Soal Pertama: Implikasi Penggunaan Sintaks Kelas Vue-CLI
Soal: Saat menggunakan vue-cli, implikasi dari menjawab Yes untuk penggunaan sintaksis model kelas untuk komponen di proyek Vue adalah .... A. pemrograman tidak bisa menggunakan @Component karena harus diganti dengan class B. pemrograman bisa memilih versi vue-class-component C. paket vue-class-component versi stabil di-install dan bisa digunakan D. paket vue-class-component versi terakhir / beta di-install dan bisa digunakan.

Jawaban
D. paket vue-class-component versi terakhir / beta di-install dan bisa digunakan.

Penjelasan (Fokus pada Vue.js/TypeScript Tooling)
Ketika Vue CLI menanyakan apakah akan menggunakan sintaks kelas (class model), ini menyiapkan proyek untuk menggunakan TypeScript bersama dengan library vue-class-component (atau sejenisnya).

Vue CLI cenderung menginstal versi library yang paling baru atau yang direkomendasikan saat itu, yang seringkali merupakan versi terbaru/beta agar sesuai dengan fitur Vue 3. Class Model memungkinkan developer Vue/TypeScript untuk menulis komponen dengan sintaks kelas yang lebih familiar bagi developer berorientasi objek.

2. Soal Kedua: Migrasi Proyek JavaScript Skala Besar ke TypeScript
Soal: Dalam kaitan dengan migrasi proyek ke TypeScript, jika pemrogram sudah mempunyai aplikasi Vue berbasis JavaScript skala besar, maka sebaiknya .... A. ubah secara bertahap ke TypeScript dengan menambahkan fitur TypeScript dan kemudian sedikit demi sedikit mengubah secara manual B. ubah secara bertahap ke TypeScript dengan menambahkan fitur TypeScript dan ubah semua file .js ke .ts melalui vue-clie C. langsung saja tambahkan fitur TypeScript D. gunakan konfigurasi dari Babel

Jawaban
A. ubah secara bertahap ke TypeScript dengan menambahkan fitur TypeScript dan kemudian sedikit demi sedikit mengubah secara manual

Penjelasan (Fokus pada TypeScript/Migrasi)
Migrasi aplikasi skala besar dari JavaScript ke TypeScript sekaligus (misalnya, mengubah semua file .js ke .ts sekaligus) sangat berisiko dan akan menghasilkan banyak error kompilasi.

## Penempatan Event Handler pada Sintaks Kelas Vue
Soal: Pada sintaksis berbasis class, event handler diletakkan pada .... A. @Options B. @Component C. definisi class yang default akan di-export D. <script>...</script>

Jawaban
C. definisi class yang default akan di-export

Penjelasan (Fokus pada Vue.js/TypeScript Class Component)
Ketika menggunakan sintaks berbasis kelas (Class-based component) di Vue (misalnya, dengan vue-class-component atau Composition API dengan <script setup> yang lebih baru), event handler (seperti fungsi yang dipanggil oleh @click)

## Penempatan props pada Sintaks Kelas Vue (@)
Soal: Pada sintaksis berbasis class, props diletakkan pada .... A. <script>...</script> B. definisi class C. @Component jika di vue-class-component versi 7.x.x D. @Options jika di vue-class-component versi 8.0.0

Jawaban
B. definisi class (atau C, jika menggunakan decorator spesifik)

Penjelasan (Fokus pada Vue.js/TypeScript)
Dalam sintaks kelas Vue (menggunakan Class Component Decorator atau Composition API), props didefinisikan sebagai properti kelas itu sendiri.

Pendekatan Class Component Lama (Opsional): Dalam vue-class-component versi lama, props sering didefinisikan di dalam decorator @Component atau @Options (misalnya, @Component({ props: {...} })).

Pendekatan Class Component Baru/Vue 3: Props didefinisikan menggunakan decorator @Prop pada properti di dalam definisi class.

Karena pilihan B adalah yang paling umum dan akurat untuk mendefinisikan props sebagai properti yang typable di TypeScript, dan C/D mengacu pada versi library spesifik, definisi class adalah tempat fisik di mana properti props diletakkan.

2. Soal Kedua: Mengakses Data @Options di Sintaks Kelas
Soal: Supaya data yang didefinisikan di @Options bisa diakses di class, maka .... A. harus didefinisikan di class dengan menggunakan tanda ! B. harus diawali dengan this.$data C. harus diletakkan di constructor D. harus didefinisikan ulang secara persis menggunakan method data pada class

Jawaban
D. harus didefinisikan ulang secara persis menggunakan method data pada class

Penjelasan (Fokus pada Vue.js/TypeScript)
Dalam implementasi vue-class-component yang lebih lama (sebelum migrasi ke Vue 3/Composition API), ada dua cara untuk mendefinisikan state reaktif:

Menggunakan sintaks kelas dengan properti kelas (lebih disukai).

Menggunakan opsi data tradisional Vue yang dimasukkan melalui decorator (misalnya, @Options({ data() { return { ... } } })).

Jika data didefinisikan melalui opsi data tradisional (method data() yang dikembalikan sebagai objek), maka data tersebut akan digabungkan (mixed in) ke dalam instansi kelas. Untuk memastikan type checking yang benar dan ketersediaan di dalam class TypeScript, developer terkadang perlu mendefinisikan ulang properti tersebut di dalam kelas itu sendiri. Namun, dalam konteks Vue-CLI modern, state reaktif didefinisikan langsung sebagai properti kelas.

Berdasarkan pilihan yang ada, jika @Options digunakan, dan kita ingin data tersebut terikat ke class secara eksplisit, method data adalah tempat tradisional Vue Options API untuk mendefinisikan state.

## Proyek vue dan decorator

Soal Pertama: Membuat Proyek Vue Baru dengan TypeScript
Soal: Untuk membuat proyek baru berbasis TypeScript menggunakan vue-cli, sebaiknya kita pilih .... A. "manually select features" dan kemudian memilih TypeScript B. menggunakan preset Vue 3 secara otomatis sudah menyertakan TypeScript C. menggunakan preset Vue 3 kemudian install fitur tambahan TypeScript D. sementara menggunakan preset Vue 2 karena Vue 3 belum stabil

Jawaban
A. "manually select features" dan kemudian memilih TypeScript

Penjelasan (Fokus pada Vue-CLI/TypeScript)
Ketika menjalankan vue create <nama-proyek>, Vue CLI akan menampilkan pilihan preset.

Untuk memastikan konfigurasi proyek menyertakan TypeScript dan tooling terkait lainnya (seperti unit testing atau router), pilihan yang paling tepat adalah "Manually select features". Di sana, developer dapat secara eksplisit memilih fitur TypeScript untuk diintegrasikan ke dalam proyek Vue.

2. Soal Kedua: Mengaktifkan Decorator di tsconfig.json
Soal: Suatu proyek berbasis Vue 3 dan TypeScript akan membaca file tsconfig.json. Di dalam file tersebut harus didefinisikan fasilitas untuk decorator, yaitu .... A. "experimentalDecorator": true B. "decorators": true C. "decorator": true D. "experimentalDecorators": true

Jawaban
D. "experimentalDecorators": true

Penjelasan (Fokus pada TypeScript)
Fitur Decorator dalam TypeScript pada dasarnya adalah fitur yang eksperimental.

Untuk mengaktifkan dukungan decorator (yang diperlukan oleh library seperti vue-class-component atau vue-property-decorator), developer harus mengatur opsi kompilator "experimentalDecorators": true di dalam bagian "compilerOptions" pada file tsconfig.json.

***
# Bab 4

## ionic

oal Pertama: Perintah untuk Menjalankan Aplikasi Ionic
Soal: Untuk menjalankan aplikasi Ionic, kita bisa menggunakan .... A. ionic cli B. ionic serve C. ionic start D. ionic run

Jawaban
B. ionic serve

Penjelasan (Fokus pada Ionic CLI)
Perintah ionic serve adalah perintah standar yang digunakan melalui Ionic CLI (Command Line Interface) untuk:

Membangun aplikasi dalam mode pengembangan (development mode).

Menjalankan aplikasi di browser secara lokal (biasanya pada http://localhost:8100).

Memantau perubahan file dan memuat ulang aplikasi secara otomatis (live reload).

ionic start (C) digunakan untuk membuat proyek baru, dan ionic run (D) digunakan untuk menjalankan aplikasi di perangkat nyata atau emulator.

2. Soal Kedua: Kerangka Aplikasi Ionic sebagai Template
Soal: Kerangka aplikasi Ionic yang bisa digunakan sebagai template disebut dengan .... A. starter B. template C. instance D. component

Jawaban
A. starter

Penjelasan (Fokus pada Ionic CLI)
Ketika Anda membuat proyek Ionic baru (menggunakan ionic start), Anda diminta untuk memilih Starter Template (kerangka awal).

Starter ini menyediakan template aplikasi yang sudah dikonfigurasi (misalnya tabs, sidemenu, blank) dan kerangka kerja UI (framework) yang dipilih (Vue, React, atau Angular).

3. Soal Ketiga: UI Framework yang BUKAN Pasangan Ionic
Soal: Berikut adalah UI framework yang bisa digunakan bersama dengan Ionic, kecuali .... A. react B. vue C. angular D. capactior

Jawaban
D. capactior

Penjelasan (Fokus pada Ionic Ecosystem)
Ionic adalah library komponen UI yang dirancang untuk bekerja dengan UI framework utama, yaitu Vue (B), React (A), dan Angular (C).

Capacitor adalah tooling (runtime) yang digunakan oleh Ionic untuk membawa aplikasi web yang sudah dibangun (menggunakan Vue, React, atau Angular) menjadi aplikasi native (iOS, Android). Capacitor adalah alat packaging (pembungkus), bukan UI framework yang digunakan untuk membangun user interface itu sendiri.

## Membuat Aplikasi Ionic Berbasis Vue
Soal: Untuk membuat aplikasi Ionic yang berbasis pada Vue, digunakan .... A. ionic cli serta ionic start dengan --type=vue B. vue cli C. ionic cli dan ionic start dengan --starter=vue D. ionic cli dan --starter=vue

Jawaban
C. ionic cli dan ionic start dengan --starter=vue

Penjelasan (Fokus pada Ionic/Vue CLI)
Untuk membuat proyek Ionic baru, Anda harus menggunakan Ionic CLI (ionic cli).

Perintah untuk memulai proyek adalah ionic start.

Untuk menentukan bahwa framework yang digunakan dalam proyek baru adalah Vue, Anda menggunakan opsi --type=vue atau --starter=vue (tergantung versi CLI, di mana --type atau --starter digunakan untuk menentukan framework). Pilihan C menggunakan sintaks yang paling umum, yang secara eksplisit menyebut ionic cli dan perintah lengkap ionic start dengan starter Vue.

## Perintah yang benar untuk membuat aplikasi Ionic baru menggunakan UI dari Vue adalah:

A. ionic start myApp tabs --type=vue

## Jawaban Soal Kedua (ionic start "aplikasi saya")
Soal: Saat membuat aplikasi Ionic menggunakan ionic start "aplikasi saya", direktori yang dihasilkan adalah ....

Jawaban yang Benar:

A. aplikasi-saya

## (Global Error Handling di Vue/Ionic/TypeScript)
Soal: Jika ingin menangani error secara global, bagian untuk menangani error di Ionic berada pada ....

Jawaban yang Benar (Paling Umum dalam Proyek Vue 3 + TypeScript):

A. src/main.ts

Penjelasan:
Dalam aplikasi Vue 3 (yang digunakan oleh Ionic CLI untuk proyek Vue):

src/main.ts adalah entry point (titik masuk) utama aplikasi Anda. Di sini Anda membuat dan me-mount instance aplikasi Vue.

## Mengubah Port Saat Menjalankan Aplikasi Ionic
Soal: Untuk menjalankan aplikasi Ionic pada port tertentu, pemrogram bisa menjalankan aplikasi tersebut dengan cara ....

Jawaban yang Benar:

C. ionic serve --port=angka

## Parameter Teks Error pada errorHandler Vue/TypeScript
Soal: Saat mendefinisikan errorHandler, bagian yang akan berisi teks error adalah ....

Jawaban yang Benar:

C. err

Penjelasan:
Ketika Anda mendefinisikan global error handler di Vue 3 (app.config.errorHandler),

***
# Bab 5

## Komponen inti yang harus di-import jika akan menggunakan single page layout adalah ....

Jawaban yang Benar:

C. IonPage, IonHeader, IonContent, IonFooter jika akan menggunakan header, content, dan footer

IonPage: Ini adalah komponen container utama yang wajib ada untuk setiap halaman di aplikasi Ionic. Ini memberikan konteks visual dan fungsional yang diperlukan oleh framework Ionic (misalnya, untuk transisi halaman dan safeguarding area).

## Urut-urutan definisi yang benar saat akan membuat layout tabs adalah ....

Jawaban yang Benar:

D. ion-tabs, ion-tab-bar, ion-tab-button

## Suatu menu harus merupakan bagian dari halaman. Atribut yang digunakan untuk menetapkan halaman utama dari suatu menu adalah ....

Jawaban yang Benar:

B. content-id

Penjelasan:
Dalam kerangka kerja Ionic (seperti IonMenu), untuk menghubungkan komponen menu ke halaman utama (konten) yang harus dikendalikan oleh menu tersebut, Anda menggunakan atribut content-id.

## Suatu item menu bisa ditetapkan untuk mengakses suatu URL tertentu dengan menggunakan ....

Jawaban yang Benar:

A. <ion-menu-item href="URL"></ion-menu-item>

## Saat membuat layout split pane, bisa digunakan atribut when. Jika menggunakan atribut when="sm", maka berarti ....

Jawaban yang Benar:

A. pemisah berada pada breakpoint sm

## Jika layar terlalu kecil untuk split pane, maka yang terjadi adalah ....

Jawaban yang Benar:

A. panel sebelah kiri akan menutupi panel sebelah kanan.

## grid 

Soal 1: Komponen Inti Responsive Grid
Soal: Komponen inti yang digunakan oleh layout responsive grid adalah ....

Jawaban yang Benar:

B. IonGrid, IonRow, IonColumn

Penjelasan:
Sistem Grid Ionic (berdasarkan Flexbox) memerlukan struktur hierarkis untuk berfungsi:

IonGrid: Ini adalah wadah utama (container) yang membungkus seluruh grid. Mirip dengan container di CSS framework lain.

IonRow: Ditempatkan di dalam IonGrid. Digunakan untuk membuat baris horizontal.

IonColumn (alias IonCol): Ditempatkan di dalam IonRow. Digunakan untuk membuat kolom vertikal dan menampung konten Anda.

Soal 2: Mengatur Posisi Kolom dengan Offset
Soal: Jika ingin me-render kolom mulai dari kolom ke-6, maka gunakan ....

Jawaban yang Benar:

B. <ion-col offset="5">

Penjelasan:
Total Kolom: Sistem Grid Ionic secara default memiliki 12 kolom.

offset: Atribut ini digunakan untuk memindahkan (menggeser) kolom ke kanan dengan meninggalkan spasi kosong sebelum kolom tersebut. Nilai offset adalah jumlah kolom yang akan dikosongkan.

Mulai dari Kolom ke-6: Untuk membuat kolom dimulai pada posisi kolom ke-6, Anda perlu mengosongkan 5 kolom sebelumnya.

Kolom yang dikosongkan: 5 kolom (Posisi 1, 2, 3, 4, 5)

Kolom dimulai: Posisi 6

Perintah: <ion-col offset="5">

pull (Opsi C): Digunakan untuk memindahkan kolom ke kiri (mengabaikan urutan logis).

size (Opsi D): Digunakan untuk menentukan lebar kolom, bukan posisinya.

Soal 3: Perhitungan Kolom dengan pull
Soal: Pada responsive grid, jika jumlah kolom default 12, jumlah kolom yang dibuat 3, maka jika pada kolom ke-3 diberikan perintah berikut: <ion-col pull="2">, maka kolom ke-4 tersebut akan mulai berada pada ....

Jawaban yang Benar:

B. kolom 9

Penjelasan:
Ini adalah soal yang sedikit kompleks dan memerlukan pemahaman tentang urutan default dan efek pull.

## Pengaturan jumlah kolom maksimal dalam suatu grid pada variables.css diatur menggunakan ....

Jawaban yang Benar:

A. --ion-grid-columns

## Jika pemakai menggunakan device Android, maka mode yang digunakan adalah ...." dengan pilihan jawaban: A. sm, B. md, C. xs, D. android.

Dalam konteks pengembangan aplikasi hybrid menggunakan Ionic (yang sering dikombinasikan dengan Vue.js dan TypeScript), Ionic secara otomatis mendeteksi platform yang digunakan (misalnya Android atau iOS) dan menerapkan styling dan mode yang sesuai.

Mode di Ionic mengacu pada tampilan dan nuansa (look and feel) komponen, yang biasanya disesuaikan agar sesuai dengan pedoman desain platform tertentu.

Secara default, jika aplikasi Ionic berjalan di perangkat Android, mode yang digunakan adalah 'md' (Material Design).

Jika berjalan di perangkat iOS, mode yang digunakan adalah 'ios'.

Pilihan 'xs' dan 'sm' adalah breakpoint ukuran layar (ekstra kecil dan kecil) yang biasa digunakan dalam sistem grid, bukan mode platform.

Oleh karena itu, jawaban yang paling tepat berdasarkan konvensi Ionic adalah:

B. md

## ntuk mendefinisikan warna baru untuk keseluruhan aplikasi, definisi dilakukan pada ....

untuk mendefinisikan warna baru untuk keseluruhan aplikasi (sehingga dapat digunakan oleh komponen Ionic) adalah:

A. :root dan .ion-color-{WARNA}

:root: Tempat untuk mendefinisikan Variabel CSS global (misalnya --ion-color-spesial: #ff0000;).

.ion-color-{WARNA}: Kelas helper yang harus dibuat Ionic agar komponen-komponennya dapat mengenali dan menerapkan warna tersebut saat properti color="{WARNA}" digunakan.

***

# BAB 6

## IONIC STARTER

[Soalnya]

Berikut adalah beberapa starter yang ada pada Ionic/Vue, kecuali .... A. blank B. my-first-app C. tabs D. sidemenu

Untuk menambahkan halaman pada starter Blank, hal yang perlu dilakukan adalah .... A. definisi halaman baru B. definisi halaman baru dan kemudian mengatur rute C. definisi rute D. definisi halaman baru, mengatur rute, import komponen pada App.vue

[Jawabannya]

B. my-first-app

D. definisi halaman baru, mengatur rute, import komponen pada App.vue

[Penjelasannya]

Soal 1: Starter pada Ionic/Vue
Pilihan A (blank), C (tabs), dan D (sidemenu) adalah nama-nama template starter resmi yang disediakan oleh Ionic CLI (Command Line Interface) saat membuat aplikasi baru, termasuk untuk framework Vue.

Blank: Aplikasi paling dasar tanpa tata letak apa pun.

Tabs: Aplikasi dengan navigasi berbasis tabs di bagian bawah.

Sidemenu: Aplikasi dengan menu geser (hamburger menu) di samping.

Pilihan B (my-first-app) BUKAN nama template starter, melainkan contoh nama proyek yang umum digunakan saat Anda menjalankan perintah ionic start. Nama starter yang tersedia adalah seperti blank, tabs, atau sidemenu.

Soal 2: Menambahkan Halaman pada Starter Blank
Untuk menampilkan halaman baru dalam aplikasi berbasis Vue dan Ionic, khususnya saat menggunakan starter Blank, ada tiga langkah inti yang harus dilakukan:

Definisi Halaman Baru: Membuat file komponen Vue (.vue) yang akan menjadi halaman baru Anda (misalnya, membuat <template>, <script>, dan <style>).

## Suatu rute dapat mempunyai rute turunan dengan mendefinisikan .... A. childComponents B. subRouter C. children D. childRouter

[Jawabannya]

C. children

[Penjelasannya]

Konsep "rute turunan" atau nested routes adalah fitur standar dalam pustaka routing populer pada ekosistem framework frontend seperti Vue Router (yang digunakan oleh Ionic/Vue) dan React Router.

Penggunaan children: Dalam konfigurasi routing pada Vue Router, untuk mendefinisikan rute yang bersarang (turunan) di bawah rute utama, Anda menggunakan array dengan nama properti children.

Struktur Kode (Contoh di Vue Router): Properti children didefinisikan di dalam objek rute utama dan berisi array objek-objek rute lain yang merupakan turunannya.

## Untuk menampilkan link ke suatu URL tertentu, dapat menggunakan .... A. ion-router saja. B. ion-router-link saja. C. ion-link dan ion-router. D. ion-router-link dan <a href="..."></a>

[Jawabannya]

D. ion-router-link dan <a href="..."></a>

[Penjelasannya]

Kesimpulan:

Karena soal menanyakan apa yang dapat digunakan untuk menampilkan link ke URL, baik ion-router-link (untuk internal) maupun elemen HTML standar <a> (untuk eksternal atau internal) adalah opsi yang valid. Oleh karena itu, pilihan D adalah yang paling lengkap dan benar secara teknis.

## Lokasi dari gambar-gambar yang dipakai dalam aplikasi Ionic adalah .... A. src/assets/ B. src/data/img C. public/assets/... D. bebas

[Jawabannya]

A. src/assets/

[Penjelasannya]

Dalam struktur proyek Ionic modern (terutama saat menggunakan Vue, React, atau Angular, yang didasarkan pada build tools seperti Webpack/Vite), praktik standar dan lokasi default untuk menyimpan asset seperti gambar, font, atau file statis lainnya adalah:

Meskipun C adalah lokasi yang valid untuk aset statis, A (src/assets/) adalah lokasi standar dan pilihan utama di mana developer Ionic/Vue/React menempatkan asset yang mereka impor dan gunakan dalam komponen, menjadikannya jawaban yang paling tepat untuk pertanyaan tentang lokasi default aset.

## Komponen yang digunakan untuk menampilkan gambar dalam Ionic adalah .... A. IonImg B. IonImage C. IonPic D. IonPicture

[Jawabannya]

A. IonImg

[Penjelasannya]

Komponen Resmi Ionic: Ionic Framework menyediakan serangkaian komponen UI yang dioptimalkan untuk performa dan tampilan native. Untuk menampilkan gambar, komponen yang didesain dan direkomendasikan secara resmi adalah ion-img (atau IonImg saat ditulis dalam format PascalCase untuk framework seperti Vue/React).

Fungsi ion-img: Komponen ini berfungsi sebagai wrapper untuk elemen HTML standar <img> tetapi menambahkan fitur-fitur seperti lazy loading dan penanganan caching yang lebih baik, membantu meningkatkan performa aplikasi seluler.

Kesalahan Pilihan Lain: Pilihan B, C, dan D (IonImage, IonPic, IonPicture) bukanlah nama komponen resmi yang disediakan oleh Ionic Framework untuk menampilkan gambar.

## Berikut adalah pernyataan-pernyataan yang benar tentang teknik layout grid, kecuali .... A. urutan tampilan: ion-grid - ion-row - ion-col B. jumlah kolom tiap baris harus sama. C. secara teoritis, tidak ada jumlah baris maksimal D. perulangan/looping diletakkan pada <ion-col>

[Jawabannya]

B. jumlah kolom tiap baris harus sama.

## Jika akan melakukan looping untuk mengakses sejumlah data yang tersedia untuk menempati kolom grid, maka v-for diletakkan pada .... A. ion-grid B. ion-row C. ion-column D. ion-col

[Jawabannya]

D. ion-col

[Penjelasannya]

Struktur Grid Ionic: Struktur dasar layout grid di Ionic adalah ion-grid (wadah) yang berisi satu atau lebih ion-row (baris), dan setiap baris berisi satu atau lebih ion-col (kolom). * ion-grid: Wadah utama. Looping di sini akan membuat grid baru, bukan kolom baru.

## Perbedaan antara CreateWebHistory dengan CreateWebHashHistory pada saat mendefinisikan router adalah .... A. sebenarnya sama saja, hanya beda tempat penyimpanan cache B. CreateWebHistory hanya menyimpan 1 cache, sementara CreateWebHashHistory bisa lebih dari satu C. CreateWebHistory lebih bagus dari sisi URL, bagus untuk SEO karena berpola /aaa/bbb/ccc. Sementara CreateWebHashHistory mengandung tanda #, kurang bagus untuk SEO D. CreateWebHistoy tidak disandikan, sementara CreateWebHashHistory disandikan dengan metode HashMap

[Jawabannya]

C. CreateWebHistory lebih bagus dari sisi URL, bagus untuk SEO karena berpola /aaa/bbb/ccc. Sementara CreateWebHashHistory mengandung tanda #, kurang bagus untuk SEO

[Penjelasannya]

Kedua fungsi ini (berasal dari Vue Router, yang digunakan pada Ionic/Vue) digunakan untuk menentukan mode sejarah (history mode) pada aplikasi Single Page Application (SPA).

CreateWebHistory (Mode History):

Menggunakan History API modern dari browser (HTML5).

Pola URL: Bersih, terlihat seperti situs web tradisional, misalnya: http://localhost:8080/user/profile.

Keuntungan: URL lebih clean dan sangat baik untuk Search Engine Optimization (SEO) karena crawler mesin pencari dapat dengan mudah mengindeks jalur (/user/profile).

Kekurangan: Membutuhkan konfigurasi server yang tepat agar semua jalur mengarah kembali ke index (index.html) aplikasi SPA. Jika tidak, saat pengguna me-refresh halaman di jalur non-root (/user/profile), server akan mengembalikan error 404.

CreateWebHashHistory (Mode Hash):

Menggunakan hash (#) di URL, memanfaatkan event hashchange pada browser.

Pola URL: Mengandung tanda pagar, misalnya: http://localhost:8080/#/user/profile.

Keuntungan: Tidak memerlukan konfigurasi server khusus karena browser mengabaikan bagian setelah # saat meminta file dari server.

Kekurangan: URL terlihat kurang profesional, dan secara historis, dianggap kurang optimal untuk SEO (meskipun Google kini lebih baik dalam mengindeks hashbangs).

Kesimpulan: Pilihan C secara akurat menjelaskan perbedaan utama antara kedua mode dari sisi penampilan URL, kegunaan SEO, dan format jalur yang mereka hasilkan.


***
# Catatan kecil

Point | Penjelasan
--- | ---
 Komponen yang selalu disertakan dalam bundle aplikasi hybrid adalah | :  webview 
 REST | adalah singkatan dari Representational State Transfer.
