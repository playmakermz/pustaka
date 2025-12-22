# MODULE 2: DATA CLEANING & PREPARATION
## Quick Reference Guide for Caelus

### Core Principle:
**GIGO (Garbage In, Garbage Out)** – Jika data input buruk, tidak ada algoritma yang bisa menyelamatkan. 50-80% pekerjaan data science adalah membersihkan data, bukan modeling.

---

## Urutan Pengelolahan Dataset

### 1. ANALISA DATASET SECARA MANUAL

```python
import pandas as pd

df = pd.read_csv('file.csv')
print(df.head())           # Lihat 5 baris pertama
print(df.info())           # Tipe data & memory
print(df.describe())       # Statistik dasar
print(df.isnull().sum())   # Hitung nilai yang hilang
```

**Tujuan:** Pahami struktur, tipe data, dan masalah umum dalam dataset.

---

### 2. ATUR FORMAT ITEM STRINGS DALAM KOLOM
Mulai dari huruf besar kecil dan spasi kosong:

```python
# Hapus spasi di awal dan akhir
df['Name'] = df['Name'].str.strip()

# Kapitalisasi dengan benar (Title Case)
df['Name'] = df['Name'].str.title()

# Contoh: 'john doe' → 'John Doe'
# Contoh: '  john  ' → 'John'
```

**Tujuan:** Standarisasi format teks agar konsisten di seluruh dataset.

---

### 3. MENGURUSI DUPLIKAT PERSIS
Mulai dari ID dan seluruhnya:

```python
# Hapus duplikat yang benar-benar sama di semua kolom
df_clean = df.drop_duplicates(keep='first')  # Simpan kemunculan pertama

# Verifikasi
print(df.duplicated().sum())  # Harus menunjukkan 0
```

**Kunci:** Hapus duplikat persis secara otomatis. Jangan ragu karena ini adalah data yang identik 100%.

---

### 4. MENANDAI YANG MIRIP TETAPI BISA DI INVESTIGASI
(Suspicious Duplicates - sama di beberapa kolom, tapi ID berbeda):

```python
# Cari duplikat berdasarkan kolom tertentu
sus = df_clean[df_clean.duplicated(subset=['Col1', 'Col2'], keep=False)]
print(sus)  # TANDAI untuk review manual, jangan auto-remove

# Simpan ke file terpisah untuk investigasi
sus.to_csv('suspicious_duplicates.csv', index=False)
```

**Kunci:** Tandai untuk review manusia. Ini mungkin data berbeda dengan kebetulan sama, atau benar-benar duplikat yang perlu diteliti lebih lanjut.

---

### 5. MANAGE DAN MENGURUSI DATA YANG HILANG

Pilih strategi berdasarkan **tipe data**:

| Tipe Data | Strategi | Kode | Kapan |
|-----------|----------|------|-------|
| **Numerik** | Median | `df['col'].fillna(df['col'].median())` | Default untuk angka (tahan terhadap outlier) |
| **Numerik** | Mean | `df['col'].fillna(df['col'].mean())` | Hanya jika data sangat bersih & normal |
| **Kategori** | Mode (Paling sering) | `df['col'].fillna(df['col'].mode()[0])` | Untuk kategori (Warna, Region, Tipe) |
| **Nama/Teks** | Placeholder khusus | `df['col'].fillna('Unknown')` | Ketika perlu menandai data hilang |
| **Tanggal** | Drop baris ATAU isi default | `df.dropna(subset=['Date'])` | Jika sedikit; jika banyak, isi dengan hati-hati |

**Contoh implementasi:**

```python
# Amount (numerik) → Gunakan median
df_clean['Amount'] = df_clean['Amount'].fillna(df_clean['Amount'].median())

# Region (kategori) → Gunakan mode
df_clean['Region'] = df_clean['Region'].fillna(df_clean['Region'].mode()[0])

# Donor_Name (teks) → Gunakan placeholder
df_clean['Donor_Name'] = df_clean['Donor_Name'].fillna('Unknown_Donor')

# Donation_Date (tanggal) → Drop jika sedikit, isi jika banyak
df_clean = df_clean.dropna(subset=['Donation_Date'])
```

**Ingat - Mean vs Median (Real Example):**
- Usia: [18, 19, 20, 23, 300] (300 = error/outlier)
- **Mean** = (18+19+20+23+300)/5 = **76** ✗ (tidak masuk akal)
- **Median** = Nilai tengah = **20** ✓ (akurat)

**Aturan Robin:** Gunakan median ~90% waktu. Mean hanya untuk data yang sangat bersih.

---

### 6. PASTIKAN TIDAK ADA NILAI KOSONG

```python
print(df_clean.isnull().sum())  # Semua harus 0
```

Jika masih ada nilai kosong, kembali ke langkah 5. Pastikan setiap kolom bersih sebelum melanjutkan.

---

### 7. PRINT DAN SAVE DATA

```python
# Verifikasi status akhir
print(df_clean.head())         # Lihat hasil akhir
print(df_clean.info())         # Tipe data final
print(df_clean.isnull().sum()) # Konfirmasi no nulls
print(df_clean.duplicated().sum())  # Konfirmasi no duplicates

# Simpan data yang sudah dibersihkan
df_clean.to_csv('cleaned_data.csv', index=False)
print("✓ Data berhasil disimpan sebagai 'cleaned_data.csv'")
```

---

## RINGKASAN WORKFLOW LENGKAP:

1. ✓ Analisa dataset secara manual
2. ✓ Atur format item strings dalam kolom
3. ✓ Mengurusi duplikat persis
4. ✓ Menandai yang mirip tetapi bisa di investigasi
5. ✓ Manage dan mengurusi data yang hilang
6. ✓ Pastikan tidak ada nilai kosong
7. ✓ Print dan save data

---

## POIN PENTING:

✓ Selalu gunakan `df_clean` secara konsisten – jangan campur dataset bersih dan kotor
✓ Komentar harus sesuai dengan kode (jangan tulis "mean" tapi pakai "median")
✓ Duplikat persis = hapus otomatis. Duplikat mirip = tandai untuk review manual
✓ Data tanggal kosong? Drop atau isi dengan hati-hati sesuai konteks
✓ Nama tidak diketahui? Gunakan placeholder seperti 'Unknown_Donor' untuk menandai investigasi diperlukan
***
