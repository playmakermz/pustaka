# MANUAL CALCULATION GUIDE FOR STATISTICS EXAM
## Mean, Median, Standard Deviation, Pie Chart, Bar Chart, Tree Diagram

---

## 1. MEAN (Rata-rata)

### Definition
Mean adalah nilai rata-rata dari semua data. Dihitung dengan menjumlahkan semua nilai dan dibagi dengan jumlah data.

### Formula
```
Mean = (x₁ + x₂ + x₃ + ... + xₙ) / n

Dimana:
- x₁, x₂, x₃, ... xₙ = setiap nilai data
- n = jumlah data total
```

### Contoh Manual Calculation

**Data: Panjang Kelopak Bunga Irish**
```
Data: 5.2, 5.8, 6.1, 4.9, 6.3, 5.5, 6.0 cm

Langkah 1: Jumlahkan semua nilai
5.2 + 5.8 + 6.1 + 4.9 + 6.3 + 5.5 + 6.0 = 41.8

Langkah 2: Hitung jumlah data
n = 7

Langkah 3: Bagi jumlah dengan n
Mean = 41.8 / 7 = 5.97 cm
```

### Interpretasi
Rata-rata panjang kelopak bunga Irish di fountain adalah 5.97 cm.

---

## 2. MEDIAN (Nilai Tengah)

### Definition
Median adalah nilai yang terletak di tengah-tengah data setelah data diurutkan dari terkecil ke terbesar.

### Formula & Prosedur

**Jika n (jumlah data) GANJIL:**
```
Median = nilai di posisi ke-(n+1)/2
```

**Jika n (jumlah data) GENAP:**
```
Median = (nilai posisi ke-n/2 + nilai posisi ke-(n/2 + 1)) / 2
```

### Contoh 1: Data Ganjil

**Data: 5.2, 5.8, 6.1, 4.9, 6.3, 5.5, 6.0 cm**

Langkah 1: Urutkan dari terkecil ke terbesar
```
4.9, 5.2, 5.5, 5.8, 6.0, 6.1, 6.3
pos1 pos2 pos3 pos4 pos5 pos6 pos7
```

Langkah 2: Hitung posisi median
```
n = 7 (ganjil)
Posisi median = (7+1)/2 = 4
```

Langkah 3: Ambil nilai di posisi ke-4
```
Median = 5.8 cm
```

### Contoh 2: Data Genap

**Data: 5.2, 5.8, 6.1, 4.9, 6.3, 5.5 cm**

Langkah 1: Urutkan
```
4.9, 5.2, 5.5, 5.8, 6.1, 6.3
pos1 pos2 pos3 pos4 pos5 pos6
```

Langkah 2: Hitung posisi
```
n = 6 (genap)
Posisi 1 = 6/2 = 3 → nilai = 5.5
Posisi 2 = (6/2) + 1 = 4 → nilai = 5.8
```

Langkah 3: Rata-rata kedua nilai tengah
```
Median = (5.5 + 5.8) / 2 = 11.3 / 2 = 5.65 cm
```

### Interpretasi
Setengah dari bunga memiliki kelopak lebih pendek dari 5.65 cm, setengahnya lagi lebih panjang.

---

## 3. SIMPANGAN BAKU (Standard Deviation)

### Definition
Simpangan baku mengukur seberapa jauh data tersebar dari rata-ratanya. Semakin besar nilai, semakin tersebar datanya.

### Formula
```
Langkah-Langkah Perhitungan:

Langkah 1: Hitung MEAN (x̄)
   x̄ = jumlah semua data / n

Langkah 2: Hitung DEVIASI (selisih setiap data dari mean)
   d₁ = x₁ - x̄
   d₂ = x₂ - x̄
   ... dan seterusnya

Langkah 3: Kuadratkan setiap deviasi
   d₁² = (x₁ - x̄)²
   d₂² = (x₂ - x̄)²
   ... dan seterusnya

Langkah 4: Jumlahkan semua kuadrat deviasi
   Σ(d²) = d₁² + d₂² + ... + dₙ²

Langkah 5: Bagi dengan (n-1) untuk sampel atau n untuk populasi
   Variance = Σ(d²) / (n-1)    [untuk sampel]
   atau
   Variance = Σ(d²) / n        [untuk populasi]

Langkah 6: Akar kuadrat variance
   Std Dev = √Variance
```

### Contoh Manual Calculation

**Data: 5.2, 5.8, 6.1, 4.9, 6.3, 5.5 cm**

**Langkah 1: Hitung Mean**
```
Mean = (5.2 + 5.8 + 6.1 + 4.9 + 6.3 + 5.5) / 6
     = 33.8 / 6
     = 5.633 cm
```

**Langkah 2 & 3: Hitung (x - mean)²**
```
x₁ = 5.2  → (5.2 - 5.633)² = (-0.433)² = 0.187
x₂ = 5.8  → (5.8 - 5.633)² = (0.167)² = 0.028
x₃ = 6.1  → (6.1 - 5.633)² = (0.467)² = 0.218
x₄ = 4.9  → (4.9 - 5.633)² = (-0.733)² = 0.537
x₅ = 6.3  → (6.3 - 5.633)² = (0.667)² = 0.445
x₆ = 5.5  → (5.5 - 5.633)² = (-0.133)² = 0.018
```

**Langkah 4: Jumlahkan semua kuadrat**
```
Σ(x - mean)² = 0.187 + 0.028 + 0.218 + 0.537 + 0.445 + 0.018
             = 1.433
```

**Langkah 5: Hitung Variance (gunakan n-1=5 untuk sampel)**
```
Variance = 1.433 / 5 = 0.287
```

**Langkah 6: Akar kuadrat**
```
Std Dev = √0.287 = 0.536 cm
```

### Interpretasi
Rata-rata bunga menyimpang 0.536 cm dari rata-rata panjang kelopak (5.633 cm). Nilai ini menunjukkan penyebaran data adalah sedang.

---

## 4. DIAGRAM LINGKARAN (Pie Chart) - Perhitungan Manual

### Definition
Diagram lingkaran menampilkan persentase setiap kategori dari total 100%.

### Formula
```
Langkah 1: Hitung TOTAL semua data
   Total = n₁ + n₂ + n₃ + ... + nₖ

Langkah 2: Hitung PERSENTASE setiap kategori
   Persentase = (nilai kategori / Total) × 100%

Langkah 3: Ubah ke DERAJAT untuk diagram (opsional untuk menggambar)
   Derajat = (nilai kategori / Total) × 360°

Langkah 4: Gambar lingkaran dengan sudut-sudut sesuai perhitungan
```

### Contoh Manual Calculation

**Data: Tipe Irish Flowers di Fountain**
```
Merah   : 30 bunga
Putih   : 45 bunga
Ungu    : 25 bunga
Total   : 100 bunga
```

**Langkah 2: Hitung Persentase**
```
Merah  = (30 / 100) × 100% = 30%
Putih  = (45 / 100) × 100% = 45%
Ungu   = (25 / 100) × 100% = 25%

Verifikasi: 30% + 45% + 25% = 100% ✓
```

**Langkah 3: Hitung Derajat (untuk menggambar)**
```
Merah  = (30 / 100) × 360° = 108°
Putih  = (45 / 100) × 360° = 162°
Ungu   = (25 / 100) × 360° = 90°

Verifikasi: 108° + 162° + 90° = 360° ✓
```

**Langkah 4: Visualisasi (cara menggambar)**
```
1. Gambar lingkaran dengan jangka
2. Mulai dari garis horizontal (0°)
3. Gunakan busur derajat untuk mengukur:
   - Merah: 0° sampai 108°
   - Putih: 108° sampai 270° (108° + 162°)
   - Ungu: 270° sampai 360° (270° + 90°)
4. Warnai setiap bagian sesuai kategori
5. Tulis label dan persentase
```

### Interpretasi
- Bunga putih mendominasi (45%)
- Bunga merah adalah 30%
- Bunga ungu adalah 25% terkecil

---

## 5. DIAGRAM BATANG (Bar Chart) - Perhitungan Manual

### Definition
Diagram batang menampilkan data kategorikal dengan tinggi batang mewakili frekuensi atau nilai.

### Prosedur Manual
```
Langkah 1: Tentukan SKALA sumbu Y
   - Lihat nilai tertinggi di data
   - Tentukan interval yang sesuai (5, 10, 20, 50, dll)

Langkah 2: Gambar SUMBU X dan Y
   - Sumbu X: kategori data
   - Sumbu Y: skala frekuensi

Langkah 3: Gambar BATANG untuk setiap kategori
   - Lebar batang sama
   - Tinggi batang sesuai dengan data
   - Jarak antar batang sama

Langkah 4: Label dengan JUDUL, NAMA SUMBU, dan NILAI
```

### Contoh Manual Calculation & Penggambaran

**Data: Frekuensi Irish Flowers Berdasarkan Ukuran Kelopak**
```
Kategori Ukuran    Frekuensi
─────────────────  ──────────
Sangat Kecil (3-4) : 5 bunga
Kecil (4-5)        : 15 bunga
Sedang (5-6)       : 35 bunga
Besar (6-7)        : 30 bunga
Sangat Besar (7-8) : 15 bunga
```

**Langkah 1: Tentukan Skala**
```
Nilai tertinggi = 35
Skala yang cocok: 0, 5, 10, 15, 20, 25, 30, 35, 40
Interval = 5
```

**Langkah 2-4: Visualisasi (cara menggambar)**
```
     Frekuensi
     40 │
     35 │        ╔════╗
     30 │        ║    ║        ╔════╗
     25 │        ║    ║        ║    ║
     20 │        ║    ║        ║    ║        ╔════╗
     15 │ ╔════╗ ║    ║ ╔════╗ ║    ║ ╔════╗ ║    ║
     10 │ ║    ║ ║    ║ ║    ║ ║    ║ ║    ║ ║    ║
      5 │ ║    ║ ║    ║ ║    ║ ║    ║ ║    ║ ║    ║
      0 └─╚════╝─╚════╝─╚════╝─╚════╝─╚════╝─╚════╝───► Ukuran Kelopak
        Sangat  Kecil Sedang  Besar  Sangat
        Kecil                         Besar
```

### Interpretasi
- Kebanyakan bunga berukuran sedang (35 bunga)
- Distribusi cukup simetris dengan dua puncak di "Sedang" dan "Besar"
- Hanya sedikit bunga dengan ukuran ekstrem (sangat kecil/besar)

---

## 6. POHON DIAGRAM (Tree Diagram) - Perhitungan Manual

### Definition
Pohon diagram menunjukkan semua kemungkinan hasil dari suatu peristiwa yang berurutan (probabilitas/kombinasi).

### Prosedur Manual
```
Langkah 1: Identifikasi PERISTIWA dan CABANG
   - Berapa tahap peristiwa?
   - Berapa kemungkinan di setiap tahap?

Langkah 2: Gambar GARIS CABANG
   - Setiap cabang = satu kemungkinan
   - Dimulai dari titik awal (root)

Langkah 3: Label SETIAP CABANG
   - Tulis kemungkinan/outcome
   - Tulis probabilitas (jika ada)

Langkah 4: Hitung HASIL AKHIR
   - Jika probabilitas: kalikan sepanjang jalur
   - Jika kombinasi: catat semua kemungkinan
```

### Contoh 1: Pohon Diagram Warna Bunga (Kombinasi)

**Situasi: Memilih 2 bunga secara berturut-turut dari 3 warna (M=Merah, P=Putih, U=Ungu)**

**Gambar Pohon:**
```
                    ┌─ M ─→ Putih
         ┌─ M ─┬─ P ─→ Ungu
         │     └─ U ─→ Putih
         │
Start ───┼─ P ─┬─ M ─→ Ungu
         │     └─ U ─→ Merah
         │
         └─ U ─┬─ M ─→ Putih
               └─ P ─→ Merah
```

**Langkah 4: Catat Semua Kemungkinan**
```
1. Merah → Putih
2. Merah → Ungu
3. Putih → Merah
4. Putih → Ungu
5. Ungu → Merah
6. Ungu → Putih

Total = 6 kemungkinan
```

### Contoh 2: Pohon Diagram Probabilitas

**Situasi: Melempar koin 2 kali**

**Data:**
```
P(Heads) = 1/2
P(Tails) = 1/2
```

**Gambar Pohon:**
```
                  1/2
         ┌─ H ────────→ HH (Heads-Heads)
         │              Probabilitas = 1/2 × 1/2 = 1/4
         │    1/2
Awal ────┼─ T ────────→ HT (Heads-Tails)
         │              Probabilitas = 1/2 × 1/2 = 1/4
         │
         │    1/2
         └─ H ────────→ TH (Tails-Heads)
         │    1/2       Probabilitas = 1/2 × 1/2 = 1/4
         │
         └─ T ────────→ TT (Tails-Tails)
                1/2     Probabilitas = 1/2 × 1/2 = 1/4

Total Probabilitas = 1/4 + 1/4 + 1/4 + 1/4 = 1 ✓
```

**Perhitungan:**
```
Untuk setiap cabang akhir:
P(hasil) = P(cabang 1) × P(cabang 2)

Contoh:
P(HH) = P(Heads pada lemparan 1) × P(Heads pada lemparan 2)
      = 1/2 × 1/2
      = 1/4 = 0.25 = 25%
```

### Interpretasi
Kemungkinan mendapat dua heads = 25%
Kemungkinan mendapat satu heads satu tails = 50% (HT + TH)
Kemungkinan mendapat dua tails = 25%

---

## QUICK REFERENCE TABLE

| Konsep | Formula | Catatan |
|--------|---------|---------|
| Mean | Σx / n | Paling mudah, paling terpengaruh outlier |
| Median | Nilai tengah setelah diurutkan | Tahan outlier, cocok untuk data skewed |
| Std Dev | √[Σ(x-mean)² / (n-1)] | Langkah: hitung mean → deviasi → kuadrat → rata-rata → akar |
| Pie Chart % | (nilai / total) × 100% | Total harus = 100% |
| Pie Chart ° | (nilai / total) × 360° | Total harus = 360° |
| Bar Chart | Plot tinggi sesuai frekuensi | Pastikan skala konsisten |
| Tree Diagram | Kalikan probabilitas sepanjang jalur | P(A dan B) = P(A) × P(B) |

---

## TIPS UNTUK EXAM

✓ **Selalu tulis langkah-langkah** — jangan langsung jawaban
✓ **Verifikasi hasil** — apakah mean logis? apakah persentase = 100%?
✓ **Gunakan kalkulator dengan bijak** — tapi pastikan bisa hitung manual
✓ **Gambar dengan rapi** — diagram yang jelas memudahkan penilaian
✓ **Tulis interpretasi** — angka saja tidak cukup, jelaskan maknanya
✓ **Periksa kembali** — sebelum serahkan kertas

---

## CONTOH SOAL KOMPREHENSIF (Praktik)

Diberikan data panjang kelopak 10 bunga Irish:
```
5.2, 5.8, 6.1, 4.9, 6.3, 5.5, 6.0, 5.7, 6.2, 5.4 cm
```

**Pertanyaan:**
1. Hitung Mean
2. Hitung Median
3. Hitung Simpangan Baku
4. Buat diagram batang untuk kategori:
   - Kecil (< 5.5 cm)
   - Sedang (5.5 - 6.0 cm)
   - Besar (> 6.0 cm)

*(Jawaban disiapkan terpisah untuk kamu periksa setelah mencoba)*

---

Semoga panduan ini membantu persiapan exam mu, Caelus!
