# Pemrograman Berbasis Perangkat Bergerak - Ringkasan Materi UAS

# Ringkasan singkat

## BAB 1: Dasar-Dasar Asynchronous Programming

### Promise Chaining
**Konsep:** Mekanisme untuk menjalankan operasi asinkron secara berurutan, di mana operasi kedua bergantung pada hasil operasi pertama.

**Alternatif Modern:** `async/await` - sintaks yang lebih bersih untuk Promise Chaining.

**Yang BUKAN Promise Chaining:**
- **nodemon:** Utilitas untuk memantau perubahan file dan restart server Node.js
- **generic:** Fitur TypeScript untuk membuat komponen reusable dengan tipe data berbeda
- **union type:** Fitur TypeScript untuk variabel dengan beberapa kemungkinan tipe (contoh: `string | number`)

---

## BAB 2: Aplikasi Hybrid & Ionic

### Arsitektur Aplikasi Hybrid
**Definisi:** Aplikasi berbasis web (HTML, CSS, JavaScript) yang dibungkus dalam wadah native.

**Komponen Kunci:**
- **Native API Plugins:** Jembatan untuk mengakses fitur low-level sistem operasi (kamera, GPS, file system)
- **WebView:** Komponen WAJIB dalam bundle aplikasi hybrid - berfungsi sebagai browser mini untuk me-render konten web

### Capacitor
**Fungsi:** Runtime dan cross-platform bridge yang dikembangkan Ionic untuk mengakses fungsionalitas native perangkat.

**Kegunaan:**
- Akses sistem level rendah (aras rendah)
- Mendukung iOS, Android, dan Web secara seragam
- Pengganti modern dari Apache Cordova

### Stencil
**Definisi:** Compiler yang dikembangkan Ionic untuk membangun Web Components.

**Kegunaan:**
- Membuat custom elements berkinerja tinggi
- Berjalan di semua framework (React, Vue, Vanilla JS)
- Digunakan untuk komponen UI inti Ionic

---

## BAB 3: TypeScript & Generics

### Generic Constraints
**Cara Filtering/Pembatasan Tipe Generic:**
```typescript
interface HasLength {
  length: number;
}

function processData<T extends HasLength>(data: T) {
  // T harus memiliki properti length
}
```
**Metode:** Menggunakan `interface` dan `extends`

### TypeScript Configuration

#### Decorator Support
**Setting di `tsconfig.json`:**
```json
{
  "compilerOptions": {
    "experimentalDecorators": true
  }
}
```

#### JSON Module Import
**Setting untuk import file JSON:**
```json
{
  "compilerOptions": {
    "resolveJsonModule": true
  }
}
```

---

## BAB 4: Express.js & RESTful API

### Routing di Express

#### Route Definition
**Komponen:** `route` - mendefinisikan pola URL dan metode HTTP

**Contoh:**
```javascript
app.get('/', (req, res) => { ... })
```
**Maksud:** Mengekspos endpoint di `http://server:port/`

**Komponen MVC/MVVM:**
- **Route:** Mendefinisikan pola URL
- **Controller:** Logika bisnis
- **Model:** Interaksi dengan data/database
- **View:** Tampilan UI (template engine atau komponen Vue)

### RESTful API Endpoint

#### Paket yang Diperlukan (TypeScript)
```bash
npm install express @types/express
```
**Penjelasan:**
- `express`: Framework web Node.js
- `@types/express`: Type definitions untuk TypeScript

#### Mengakses Endpoint
**Tools yang dapat digunakan:**
- Semua HTTP client
- Postman
- curl
- wget

#### HTTP Methods (BUKAN Standar)
**Yang BUKAN HTTP method:** `QUERY`

**HTTP Methods Standar:**
- GET
- POST
- PUT
- PATCH
- DELETE
- HEAD
- OPTIONS

#### Format Respons API
**Kemungkinan Format:**
- JSON (paling umum)
- HTML
- XML
- Plain text
- File biner (PNG, JPEG, PDF, CSS, JavaScript)

**Kesimpulan:** Bisa dalam format apa saja, tergantung Content-Type

### Axios Response

#### Struktur Response yang Berhasil (Fulfilled)
```javascript
const response = await axios.get('/api/data');
const data = response.data; // Payload utama
```

**Properties Objek Response:**
- `response.data` - Payload/isi respons (yang dibutuhkan)
- `response.status` - HTTP status code
- `response.headers` - HTTP headers

#### Memeriksa Tipe File
**Cara:** `response.headers['content-type']`

**Contoh:**
- `application/json`
- `image/png`
- `text/html`

---

## BAB 5: Vue.js Fundamentals

### Instalasi Vue

#### CDN vs NPM
**Persamaan:** Instalasi Vue menggunakan CDN pada dasarnya sama dengan **NPM**

**Perbedaan Teknis:**
- **CDN:** Global Build, variabel global `Vue`
- **NPM:** Module Build (ES Modules), perlu bundler

### Vue Options API

#### Methods
**Fungsi:** Mendefinisikan fungsi untuk event handler (seperti button click)

**Contoh:**
```vue
<script>
export default {
  methods: {
    handleClick() {
      // logika tombol
    }
  }
}
</script>
```

#### Props
**Fungsi:** Mendefinisikan atribut yang diterima komponen dari parent

**Tujuan:** Komunikasi data dari parent ke child component

#### Lifecycle Hooks
**Definisi:** Kode yang dijalankan pada fase tertentu dari siklus hidup komponen

**Contoh Hooks:**
- `created` - setelah instance dibuat
- `mounted` - setelah DOM di-mount
- `updated` - setelah data berubah
- `unmounted` - sebelum dihancurkan

#### Computed Properties
**Kegunaan:** Fungsi yang menghasilkan nilai berdasarkan perubahan data reaktif

**Karakteristik:**
- Otomatis mendeteksi dependensi
- Di-cache dan dijalankan ulang saat dependensi berubah
- **HARUS mengembalikan nilai (return value)**

**Perbedaan dengan Methods:**
- Computed: Harus return value, di-cache, reaktif otomatis
- Methods: Tidak harus return, dipanggil manual, tidak di-cache

---

## BAB 6: Vue Router

### Membuat Router
**Fungsi:** `createRouter` (Vue Router v4)

**Contoh:**
```javascript
import { createRouter, createWebHistory } from 'vue-router';

const router = createRouter({
  history: createWebHistory(),
  routes: [...]
});
```

### Router Components

#### Menampilkan Route
**Component:** `<router-view>` - placeholder untuk render komponen sesuai URL

#### Navigasi Link
**Component:** `<router-link>` - untuk navigasi internal

**Named Router:**
```vue
<router-link :to="{ name: 'Awal' }">Home</router-link>
```

### Nested Routes (Rute Turunan)
**Properti:** `children`

**Contoh:**
```javascript
{
  path: '/user',
  component: User,
  children: [
    { path: 'profile', component: UserProfile },
    { path: 'posts', component: UserPosts }
  ]
}
```

### Route Parameters
**Akses di Template:** `$route.params.namaParameter`

**Contoh:**
```vue
<template>
  <div>NPP: {{ $route.params.npp }}</div>
</template>

<!-- Route: /pegawai/:npp -->
```

**Perbedaan:**
- `$route` - objek rute aktif (berisi params, query, path)
- `$router` - instance router global (untuk navigasi programmatic)

### History Mode

#### createWebHistory
**Karakteristik:**
- URL bersih: `/user/profile`
- Bagus untuk SEO
- Perlu konfigurasi server (fallback ke index.html)

#### createWebHashHistory
**Karakteristik:**
- URL dengan hash: `/#/user/profile`
- Tidak perlu konfigurasi server
- Kurang optimal untuk SEO

---

## BAB 7: Vue Directives

### Direktif Kondisional
**Direktif yang Valid:**
- `v-if` - render kondisional (add/remove dari DOM)
- `v-else-if` - kondisi alternatif
- `v-else` - kondisi default
- `v-show` - toggle CSS display

**Yang BUKAN Kondisional:** `v-bind` (untuk binding atribut)

### Direktif Looping
**Direktif:** `v-for` - untuk iterasi array/objek

**Contoh:**
```vue
<li v-for="item in items" :key="item.id">
  {{ item.nama }}
</li>
```

### Interpolasi Teks

**Yang Valid:**
```vue
{{ nama }}
{{ ok ? 'Ya' : 'Tidak' }}
{{ pesan.toLowerCase() }}
```

**Yang TIDAK Valid:**
```vue
<p v-text></p>  <!-- Harus ada nilai/ekspresi -->
```

### Event Modifiers

#### .once Modifier
**Fungsi:** Event handler hanya dipanggil satu kali

**Contoh:**
```vue
<button @click.once="handleClick">Klik Saya</button>
```

#### Event Handler yang Valid
**Contoh:**
```vue
@click="counter += 1, funct1(2, 1)"
@click="counter += 1, next += 1"
@click="func1(2, 1), func2()"
```

**Yang TIDAK Valid:**
```vue
@click="<template></template>"  <!-- Bukan ekspresi JavaScript -->
```

---

## BAB 8: Vue Single File Component (SFC)

### Definisi
**SFC:** Format file `.vue` yang menggabungkan:
- `<template>` - struktur HTML
- `<script>` - logika JavaScript/TypeScript
- `<style>` - styling CSS

### Scoped CSS
**Syntax:** `<style scoped>`

**Fungsi:**
- CSS hanya berlaku pada template komponen tersebut
- Mencegah style "bocor" ke komponen lain
- Menggunakan atribut data unik (contoh: `data-v-xxxxxx`)

---

## BAB 9: Vue Class Component

### Decorator

#### Fungsi Utama
**Kegunaan:** Metadata Programming - menambahkan anotasi dan metaprogramming ke class/method/property

#### Decorator Versions
**Vue Class Component v7.x.x:** `@Component`
**Vue Class Component v8.x.x:** `@VueComponent`

### Penempatan Komponen dalam Class

#### Event Handler
**Lokasi:** Definisi class yang di-export default

**Contoh:**
```typescript
export default class MyComponent extends Vue {
  handleClick() {
    // event handler
  }
}
```

#### Props
**Lokasi:** Definisi class (sebagai property dengan decorator `@Prop`)

**Contoh:**
```typescript
import { Prop } from 'vue-property-decorator';

export default class MyComponent extends Vue {
  @Prop() nama!: string;
}
```

#### Data dari @Options
**Cara Akses:** Harus didefinisikan ulang di class menggunakan method `data()`

---

## BAB 10: Tooling & CLI

### YARGS (Command Line Arguments)

#### Library CLI Parser
**Yang Valid:**
- commander
- yargs
- minimist

**Yang BUKAN:** commandliner

#### Opsi Wajib
**Setting:** `demandOption: true`

**Contoh:**
```javascript
yargs.option('nama', {
  demandOption: true,
  describe: 'Nama pengguna'
});
```

#### Mengakses Argumen
**Cara:** `argv.nama` (dot notation)

**Contoh:**
```javascript
const argv = yargs.argv;
console.log(argv.nama);
```

### NPM Scripts

#### Definisi Script
**Lokasi:** Bagian `scripts` di `package.json`

**Contoh:**
```json
{
  "scripts": {
    "serve": "vue-cli-service serve",
    "build": "vue-cli-service build"
  }
}
```

#### Passing Arguments
**Karakter:** `--` (double dash)

**Contoh:**
```bash
npm run build -- --env=production
```

### Axios Instance

#### Membuat Instance
**Fungsi:** `axios.create()`

**Contoh:**
```javascript
const api = axios.create({
  baseURL: 'https://api.example.com',
  timeout: 5000
});
```

### File System (fs/promises)

#### Write File dengan Array
**Hasil:** Array akan dikonversi menjadi string

**Untuk JSON:** Gunakan `JSON.stringify(array)`

#### Fungsi writeFile
```javascript
await fs.writeFile(f, data);
```
**Maksud:** Menuliskan isi `data` ke file dengan nama file sesuai nilai variabel `f`

---

## BAB 11: Vue CLI & Project Setup

### Membuat Proyek Vue dengan TypeScript
**Cara:** Pilih "Manually select features" → pilih TypeScript

**Alasan:** Untuk konfigurasi eksplisit dan kontrol penuh atas fitur

### Migrasi JavaScript ke TypeScript
**Best Practice:** Ubah secara bertahap dengan menambahkan fitur TypeScript, kemudian konversi manual file per file

**Alasan:**
- Mengurangi risiko error massal
- Lebih mudah di-debug
- Migrasi lebih terkontrol

---

## BAB 12: Ionic Framework

### Ionic CLI Commands

#### Menjalankan Aplikasi
**Command:** `ionic serve`

**Fungsi:**
- Build aplikasi dalam mode development
- Jalankan di browser (localhost:8100)
- Live reload otomatis

#### Starter Templates
**Nama:** **Starter** (bukan template, instance, atau component)

**Jenis Starter:**
- `blank` - aplikasi kosong
- `tabs` - navigasi tabs
- `sidemenu` - hamburger menu

**Yang BUKAN Starter:** `my-first-app` (ini nama proyek)

#### Membuat Proyek Vue
**Command:** `ionic start namaApp tabs --type=vue`

atau

`ionic start namaApp --starter=vue`

#### Nama Direktori
**Input:** `ionic start "aplikasi saya"`
**Output:** Direktori bernama `aplikasi-saya` (spasi diganti dash)

### Ionic dengan Capacitor
**Capacitor:** Bukan UI framework, tapi **tooling/runtime** untuk packaging aplikasi web menjadi native

**UI Frameworks untuk Ionic:**
- Vue
- React
- Angular

### Mode Platform
**Android:** Mode `md` (Material Design)
**iOS:** Mode `ios`

**Bukan mode:** `sm`, `xs` (ini breakpoint ukuran layar)

---

## BAB 13: Ionic Components & Layout

### Single Page Layout
**Komponen Inti (wajib):**
- `IonPage` - container utama (WAJIB)
- `IonHeader` - bagian atas (opsional)
- `IonContent` - konten utama (opsional)
- `IonFooter` - bagian bawah (opsional)

### Tabs Layout
**Urutan Definisi:** `ion-tabs` → `ion-tab-bar` → `ion-tab-button`

### Menu Layout
**Atribut untuk halaman utama:** `content-id`

**Item Menu dengan URL:**
```vue
<ion-menu-item href="URL"></ion-menu-item>
```

### Split Pane Layout

#### Atribut when
**`when="sm"`:** Pemisah berada pada breakpoint sm

#### Layar Kecil
**Behavior:** Panel kiri akan menutupi panel kanan (overlay)

---

## BAB 14: Responsive Grid System

### Komponen Inti
**Struktur:** `IonGrid` → `IonRow` → `IonColumn` (atau `IonCol`)

**Hierarki:**
```vue
<ion-grid>
  <ion-row>
    <ion-col>Content</ion-col>
  </ion-row>
</ion-grid>
```

### Grid Properties

#### Offset
**Mulai dari kolom ke-6:** `<ion-col offset="5">`

**Penjelasan:** Mengosongkan 5 kolom pertama (1-5), mulai di kolom 6

#### Pull
**Pull="2":** Memindahkan kolom ke kiri

**Perhitungan:**
- Total kolom: 12
- Kolom dibuat: 3
- Pull="2" pada kolom ke-3
- **Hasil:** Kolom ke-3 akan mulai berada pada kolom 9

### Grid Configuration
**Setting di `variables.css`:** `--ion-grid-columns`

**Default:** 12 kolom

### Pernyataan yang SALAH tentang Grid
**SALAH:** "Jumlah kolom tiap baris harus sama"

**BENAR:**
- Urutan: ion-grid → ion-row → ion-col
- Tidak ada jumlah baris maksimal
- Looping diletakkan pada `<ion-col>`

### Looping pada Grid
**Penempatan v-for:** Pada `ion-col` (atau `ion-column`)

**Contoh:**
```vue
<ion-row>
  <ion-col v-for="item in items" :key="item.id">
    {{ item.name }}
  </ion-col>
</ion-row>
```

---

## BAB 15: Ionic Styling & Theming

### Menambahkan Halaman Baru (Starter Blank)
**Langkah:**
1. Definisi halaman baru (buat file `.vue`)
2. Mengatur rute (tambah di router)
3. Import komponen di `App.vue`

### Link Navigation
**Cara menampilkan link:**
- `ion-router-link` (untuk internal routing)
- `<a href="..."></a>` (untuk URL eksternal atau internal)

### Asset Images
**Lokasi Default:** `src/assets/`

**Alternatif (public):** `public/assets/` (untuk static files)

### Image Component
**Komponen:** `IonImg`

**Bukan:** IonImage, IonPic, IonPicture

**Keunggulan:**
- Lazy loading otomatis
- Caching lebih baik
- Optimasi performa mobile

### Custom Color Definition
**Lokasi:** `:root` dan `.ion-color-{WARNA}` di `variables.css`

**Contoh:**
```css
:root {
  --ion-color-custom: #ff6b6b;
}

.ion-color-custom {
  --ion-color-base: var(--ion-color-custom);
  --ion-color-contrast: #ffffff;
}
```

---

## BAB 16: Error Handling & Global Configuration

### Global Error Handler
**Lokasi:** `src/main.ts`

**Contoh:**
```typescript
app.config.errorHandler = (err, instance, info) => {
  console.error('Global error:', err);
};
```

**Parameter yang berisi teks error:** `err`

### Custom Port
**Command:** `ionic serve --port=8080`

---

## CATATAN PENTING

### REST (Representational State Transfer)
**Prinsip:**
- Stateless
- Client-Server architecture
- Cacheable
- Uniform interface

### WebView
**Fungsi:** Komponen WAJIB dalam aplikasi hybrid untuk me-render konten web

### GraphQL
**Alternatif:** REST API - memungkinkan client meminta data spesifik yang dibutuhkan

---

***
# Ringkasan panjang
***

## 1.1 

Saat ini tersedia 2 platform besar untuk perangkat *mobile* yaitu Android serta iOS. Android menempati pangsa pasar tertinggi di seluruh dunia. Aplikasi untuk Android dikembangkan dengan menggunakan 2 teknik, yaitu *native* dan *hybrid*.

Aplikasi *native* adalah aplikasi yang dikembangkan secara langsung untuk dijalankan secara langsung dengan menggunakan ART (*Android Runtime*).

Aplikasi *hybrid* menyertakan *browser engine* di dalam aplikasi. *Browser engine* tersebut berfungsi untuk menghasilkan tampilan berbasis spesifikasi teknologi Web (HTML, CSS, JavaScript). Guna mendapatkan akses aras/level rendah/sistem, aplikasi *hybrid* menggunakan perangkat pembantu yang disebut *Native API plugins*.

Salah satu *framework* yang dapat digunakan untuk mengembangkan aplikasi *hybrid* adalah Ionic. Ionic memungkinkan seseorang pengembang aplikasi untuk dapat membangun aplikasi dengan menggunakan spesifikasi teknologi *Web* serta memakai *framework* antarmuka Angular, React, atau Vue; dengan menggunakan JavaScript dan/atau TypeScript sebagai bahasa pemrograman untuk Ionic.

## 1.2


TypeScript adalah bahasa pemrograman yang merupakan superset dari JavaScript. TypeScript mengenali dan dapat memproses sintaksis JavaScript. TypeScript melakukan berbagai penambahan pada sintaksis JavaScript sehingga berbagai kelemahan JavaScript yang selama ini menjadi keluhan dari berbagai pengembangan perangkat lunak dapat diperbaiki.

Kode sumber TypeScript akan dikompilasi menjadi JavaScript yang dapat dijalankan dengan menggunakan Node.js. Kompilator TypeScript dapat digunakan untuk mengompilasi kode sumber JavaScript maupun TypeScript.

Sebagai suatu bahasa pemrograman, TypeScript juga mempunyai konstruksi tersendiri yang sebenarnya merupakan perluasan dari JavaScript. Beberapa hal yang diubah dan diperbaiki dari JavaScript antara lain adalah penggunaan static typing dalam kode sumber, berbagai tipe data, penggunaan let dan variable scoping, OOP, interface, serta fasilitas modul. Kegiatan belajar ini mempelajari berbagai sintaks dan konstruksi dasar dari TypeScript, terutama bagian-bagian yang membedakan dengan JavaScript.

## 1.3 

Asynchronous programming atau non-blocking I/O adalah teknik pemrograman untuk mengantisipasi kemungkinan akan terjadi atau tidak terjadi sesuatu hal pada saat yang akan datang serta untuk mengerjakan proses secara konkuren jika dirasakan latensi untuk bagian tertentu akan signifikan (antara lain karena akses I/O). TypeScript mengantisipasi kedua hal tersebut dengan menggunakan konstruksi Promise serta async/await.

Suatu aplikasi pada umumnya terdiri atas sisi client/frontend maupun server/backend. Selain fullstack, TypeScript dapat juga digunakan hanya pada salah satu sisi saja. Jika digunakan sebagai backend, maka TypeScript akan digunakan untuk mengekspos suatu data dengan menggunakan protokol tertentu, yaitu RESTful API dan/atau GraphQL.

Dengan menggunakan RESTful API sebagai backend, maka TypeScript hanya memerlukan http server saja. Salah satu framework yang dapat digunakan untuk penyediaan http server untuk mengekspos suatu endpoint tertentu adalah Express. Express dapat diakses menggunakan TypeScript dengan mengatur paket-paket tertentu (menggunakan package.json) serta mengatur konfigurasi TypeScript dengan menggunakan tsconfig.json.

## 2.1 

Vue merupakan *framework* yang progresif dan bisa digunakan bersama dengan *framework* lainnya. Fungsi utama dari Vue adalah untuk membangun tampilan *frontend* maupun untuk membangun SPA (*Single-Page Application*). Vue bisa diinstal dengan menggunakan 3 cara: vue/cli, CDN, serta npm. Vue mempunyai fitur utama *rendering* deklaratif (didefinisikan apa yang diinginkan, dan bukan langkah-langkah yang harus dilakukan), direktif dan *event listener* untuk interaksi dengan pemakai aplikasi, struktur kendali, serta pembuatan komponen-komponen yang didefinisikan dengan menggunakan tag HTML.

Semua aplikasi Vue dan komponen yang berada di dalamnya merupakan instan yang berada dalam suatu *lifecycle* tertentu. Vue mendefinisikan *lifecycle hooks* yang memungkinkan pemrogram untuk menambahkan kode sumber pada suatu tahap tertentu di *lifecycle*.

## 2.2

Navigasi dalam suatu tampilah di Vue diwujudkan dalam bentuk router. Vue menyediakan suatu pustaka khusus untuk mengelola router, yaitu: Vue Router. Vue juga menyediakan fasilitas untuk membuat tampilan berdasarkan template. Template bekerja dengan interpolasi teks dengan isi dari data maupun ekspresi JavaScript. Template berupa elemen HTML dan merupakan elemen yang valid dari HTML maupun XML.

Dalam elemen tersebut, Vue juga menyediakan direktif yang digunakan untuk melakukan sesuatu terkait dengan elemen HTML yang didefinisikan bersama direktif tersebut. Beberapa direktif digunakan antara lain untuk data binding. Data binding bisa digunakan untuk property, array, hal-hal yang sifatnya kondisional, serta class dan style.

## 2.3

Suatu event adalah kejadian yang muncul dan terkait dengan aktivitas di antarmuka pemakai. Tidak semua event harus ditangani, hanya yang dikehendaki oleh pemrogram saja. Vue mempunyai fasilitas untuk menangani event tersebut dalam bentuk event handler yang bisa diwujudkan dalam bentuk ekspresi JavaScript maupun fungsi; baik fungsi yang dengan atau tanpa argumen maupun fungsi yang hanya berjumlah satu maupun lebih dari satu. Selain itu, Vue juga memungkinkan mengakses DOM secara langsung. Jika dikehendaki, Vue menyediakan modifier bagi direktif untuk penanganan elemen lebih lanjut.

Komponen pada Vue biasanya diwujudkan dalam bentuk single file components, yaitu satu file .vue yang di dalamnya terdapat template, script, serta style yang berhubungan langsung dengan komponen tersebut untuk mendapatkan fungsionalitas dan tampilan khusus dari komponen. Komponen pada Vue biasanya diletakkan pada direktori src/components. Untuk menggunakan komponen, import file .vue dan kemudian daftarkan komponen tersebut di root component.

## 3.1 

TypeScript bisa digunakan juga untuk membangun aplikasi berbasis command line / shell dengan mendayagunakan pustaka standar dari Node.js (dengan menginstall @types/node) serta berbagai pustaka Node.js yang ada di npm (banyak diantaranya sudah mempunyai definisi types - misal @types/yargs). Untuk yang belum tersedia types, maka bisa digunakan perintah-perintah dari JavaScript.

## 3.2 

Suatu aplikasi terdiri atas sisi *client / frontend* dan sisi *server / backend*. Sisi *backend* menyediakan sumber daya yang bisa diakses oleh *frontend* untuk kebutuhan data, sementara sisi *frontend* menyediakan tampilan antarmuka ke pemakai. Istilah yang lebih spesifik untuk *server* yang menyediakan Web API dan bisa diakses untuk kebutuhan data disebut dengan *endpoint*.

Suatu *endpoint* bisa dibangun dengan menggunakan suatu *framework* ataupun pustaka yang menyediakan layanan HTTP. Jika menggunakan HTTP untuk keperluan utama pembuatan *endpoint* serta pengaksesannya dari sisi *frontend*, maka mekanisme tersebut disebut dengan RESTful API. Dari sisi *frontend*, diperlukan pustaka HTTP *client* yang bisa digunakan untuk mengirimkan berbagai *method* dari HTTP (*GET*, *POST*, *PUT*, *DELETE*, dan lain-lain). Di JavaScript / TypeScript, pustaka yang bisa digunakan adalah axios.

## 3.3

Sejak versi 2.5, Vue merupakan *software* yang mendukung TypeScript. Vue versi 3 dibangun dengan menggunakan TypeScript dan TypeScript merupakan bahasa utama. Salah satu unsur yang intensif digunakan di Vue adalah tentang *decorator* yang merupakan deklarasi khusus yang akan mengacu ke suatu fungsi.

*Decorator* banyak digunakan di Vue sehingga perlu pemahaman tentang *decorator*. *Decorator* memungkinkan pemrogram untuk mengatur injeksi ke unit dari kode sumber jika diperlukan ada hal tertentu yang diperlukan oleh unit tersebut di luar inti dari unit tersebut.

*Decorator* diawali dengan tanda @. Dengan menggunakan *vue-cli*, pemrogram bisa membuat instan aplikasi Vue berbasis TypeScript dari awal maupun mengkonversi proyek JavaScript Vue ke TypeScript.


## 4.1

Ionic merupakan software framework yang bisa digunakan untuk membangun aplikasi lintas platform untuk Android, iOS, maupun PWA. Untuk membangun aplikasi menggunakan Ionic, pemrogram bisa menggunakan ionic cli yang merupakan tool utama untuk mengelola proyek.

Dengan menggunakan ionic cli, pemrogram bisa membuat proyek Ionic baru maupun mengatur berbagai fitur yang ada di dalam proyek tersebut. Setelah membuat suatu proyek berdasarkan starter tertentu, diperlukan IDE untuk membangun aplikasi Ionic.

Banyak IDE maupun editor teks yang bisa digunakan, tetapi Visual Studio Code menyediakan dukungan yang kuat untuk Ionic maupun ekosistem pembentuknya (Vue, JavaScript, TypeScript). Setelah selesai melakukan konfigurasi dari Visual Studio Code, perlu mengetahui beberapa tools maupun software yang bisa digunakan untuk membangun aplikasi Ionic, seperti Apache Cordova, Capacitor, Stencil, dan lain-lain.

## 4.2 

Paket *ionic cli* merupakan paket yang digunakan untuk mengelola proyek pembuatan aplikasi berbasis Ionic. Dengan menggunakan *ionic cli*, pemrogram bisa membuat kerangka aplikasi berdasarkan *template* tertentu, menjalankan aplikasi, mengelola komponen yang ada di dalam aplikasi, dan berbagai fitur lain untuk mengelola proyek.

Saat membuat kerangka aplikasi, pemrogram harus menentukan apakah akan menggunakan Angular, React, atau Vue. Jika memilih menggunakan Vue, maka pada bagian *src* akan dibuat struktur aplikasi seperti instan aplikasi Vue yang telah dipelajari sebelumnya.

Kerangka aplikasi yang dibuat menggunakan *ionic cli* merupakan kerangka aplikasi yang berbasis TypeScript sehingga sebaiknya pemrogram menggunakan TypeScript untuk membangun aplikasi Ionic. Jika terpaksa menggunakan JavaScript, maka bisa mengatur 2 hal di *tsconfig.json*, yaitu *allowJs* menjadi *true* dan *strict* menjadi *false*.

## 4.3

Suatu event adalah kejadian yang muncul dan terkait dengan aktivitas di antarmuka pemakai. Tidak semua event harus ditangani, hanya yang dikehendaki oleh pemrogram saja. Vue mempunyai fasilitas untuk menangani event tersebut dalam bentuk event handler yang bisa diwujudkan dalam bentuk ekspresi JavaScript maupun fungsi; baik fungsi yang dengan atau tanpa argumen maupun fungsi yang hanya berjumlah satu maupun lebih dari satu. Selain itu, Vue juga memungkinkan mengakses DOM secara langsung. Jika dikehendaki, Vue menyediakan modifier bagi direktif untuk penanganan elemen lebih lanjut.

Komponen pada Vue biasanya diwujudkan dalam bentuk single file components, yaitu satu file .vue yang di dalamnya terdapat template, script, serta style yang berhubungan langsung dengan komponen tersebut untuk mendapatkan fungsionalitas dan tampilan khusus dari komponen. Komponen pada Vue biasanya diletakkan pada direktori src/components. Untuk menggunakan komponen, import file .vue dan kemudian daftarkan komponen tersebut di root component.

## 5.1


Ionic menggunakan berbagai teknik untuk peletakan berbagai komponen melalui layout tertentu. Ada beberapa teknik layout: single page (layar terbagi menjadi tiga bagian: header, content / isi, dan footer), tabs (layar terbagi menjadi tab bar untuk meletakkan komponen dan bagian content / isi), side menu (layar terbagi menjadi side menu yang berada di samping dan default-nya tersembunyi, harus merupakan anak dari suatu halaman), dan split pane (layar terbagi dua yaitu sebelah kiri dan kanan, layar sebelah kiri akan tersembunyi atau muncul tergantung pada ukuran layar).

Untuk layout yang sifatnya custom, bisa digunakan responsive grid yang membuat tampilan menjadi suatu grid yang terbagi menjadi baris dan kolom membentuk tabel.

## 5.2 

Ionic menyediakan fasilitas untuk mengatur tema maupun mengatur berbagai tampilan serta fungsionalitas grafis lainnya. Pengaturan tersebut dilakukan dengan menggunakan CSS serta variabel CSS. Pengaturan tersebut bisa dilakukan untuk keseluruhan aplikasi dengan cara membuat suatu file CSS dan kemudian meng-import file tersebut pada src/main.ts.

Selain itu, pengaturan juga bisa dilakukan untuk setiap komponen di keseluruhan aplikasi maupun per single file component. Pengaturan bisa meliputi perintah CSS secara langsung maupun variabel CSS. Pengaturan utama untuk keseluruhan aplikasi akan dilakukan pada :root sementara untuk pengaturan sesuai device bisa dilakukan pada .ios maupun .md. Pengaturan .md dilakukan untuk device Android maupun dan selain iOS.

## 5.3 

Ionic menyediakan banyak komponen yang bisa digunakan untuk membangun antamuka pemakai. Secara umum, komponen-komponen antarmuka tersebut menggunakan frontend framework sesuai dengan yang digunakan saat membuat rerangka aplikasi baru sehingga ada kemungkinan tetap bisa menggunakan atribut dari Vue misalnya jika pemrogram menggunakan Vue, misal penggunaan v-model untuk Vue.

Ionic juga menyediakan berbagai properties maupun methods untuk berbagai komponen tersebut. Kegiatan Belajar 3 menampilkan komponen-komponen yang banyak digunakan saat membangun aplikasi.

## 6.1 

Untuk memulai proyek aplikasi Ionic, install ionic cli serta ionic lab. Paket ionic cli digunakan untuk mengelola proyek aplikasi Ionic, sementara paket ionic lab digunakan untuk preview hasil pada platform browser maupun mobile phone (Android dan iOS).

Setelah install paket-paket tersebut, pemrogram dapat menggunakan editor/IDE apa saja, tetapi yang mempunyai dukungan paling bagus adalah Visual Studio Code dengan berbagai extensions yang digunakan untuk proyek Ionic/Vue maupun Web. Untuk memulai, Ionic menyediakan berbagai starter project yang dapat diinstall dengan ionic cli.

Ada 4 starter project untuk proyek Ionic/Vue: blank, tabs, sidemenu, dan list. Masing-masing starter project mempunyai kekhususan untuk tipe aplikasi tertentu

## 6.2 

Setiap aplikasi yang dibangun menggunakan Ionic selalu mempunyai layout tertentu. Jika menggunakan responsive grid, maka layar akan dibagi menjadi tabel grid yang terdiri atas baris dan kolom. Ionic menyediakan tag ion-grid, ion-row, dan ion-col untuk keperluan tersebut.

Jika ingin menggunakan menu, gunakan split pane dan kemudian definisikan ion-button-menu serta ion-menu dan ion-toggle-menu. Menu akan ditampilkan menggunakan <ion-list> dan <ion-item>. Untuk kembali ke halaman awal setelah memunculkan suatu halaman baru, gunakan ion-back-button.

## 6.3

Membuat aplikasi, selain melibatkan algoritma proses bisnis, juga melibatkan perancangan layout dari aplikasi serta penempatan komponen-komponen antarmuka pada layout tersebut. Setelah tampilkan antarmuka, perlu dipahami cara menangani jika terdapat event tertentu terkait antarmuka tersebut. Setiap komponen antarmuka pada Ionic, mempunyai event serta event handler sendiri-sendiri dengan cara penanganan yang berbeda-beda antara frontend framework satu dengan lainnya.

Sebagai contoh, ion-checkbox mempunyai event IonChange, tetapi ion-button tidak mempunyai IonChange. Saat menggunakan tipe Vue, pemrogram juga harus memahami bagaimana Vue menangani event, misalnya untuk ion-button pemrogram dapat menggunakan directive v-on atau @click yang merupakan bawaan dari Vue.

## TIPS UJIAN

1. **Hafalkan struktur hierarki** (Grid, Tabs, Router)
2. **Pahami perbedaan konsep** (computed vs methods, $route vs $router)
3. **Ingat nama komponen yang tepat** (IonImg, bukan IonImage)
4. **Perhatikan syntax exact** (createRouter, bukan createRoute)
5. **Pahami TypeScript config** (experimentalDecorators, resolveJsonModule)
6. **Ingat HTTP concepts** (methods, headers, Content-Type)
7. **Pahami lifecycle** (created, mounted, updated)
8. **Ingat Ionic CLI commands** (serve, start, build)

---

**Semoga berhasil di UAS! 🎓**
