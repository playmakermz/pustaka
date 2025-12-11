# Pemrograman Berbasis Perangkat Bergerak - Ringkasan Materi UAS

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
