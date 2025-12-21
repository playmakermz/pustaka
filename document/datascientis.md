# CATATAN DATA SCIENCE - PERSIAPAN UJIAN

[https://github.com/playmakermz/warkop-website/blob/main/document/DataScience/Data-management.md]

## BAB 1: PENGENALAN DATA SCIENCE

### Apa Itu Data Science?
Data Science adalah disiplin ilmu yang menggabungkan **statistika**, **programming**, dan **domain knowledge** untuk mengubah data mentah menjadi wawasan yang berguna dan dapat ditindaklanjuti.

### Mengapa Data Science Penting?
- Data telah menjadi aset yang sangat berharga di era digital
- Perusahaan membutuhkan keputusan berbasis data (data-driven decision)
- Membantu memprediksi masa depan dan menemukan pola tersembunyi

### Kenyataan Praktis di Lapangan
**Fakta Penting:** Para praktisi data science menghabiskan **50-80% waktu mereka** untuk membersihkan dan mempersiapkan data, bukan untuk modeling!

**Istilah Penting:** 
- **Garbage In, Garbage Out (GIGO)**: Jika input data buruk, output juga akan buruk. Tidak ada algoritma terbaik sekalipun bisa menyelamatkan data berkualitas rendah.

---

## BAB 2: DATA CLEANING & PERSIAPAN DATA

Ini adalah fase paling kritis dan memakan waktu dalam data science.

### 2.1 Membaca & Memahami Data dengan Pandas

**Pandas** adalah library Python untuk manipulasi data yang paling powerful.

```python
import pandas as pd
import numpy as np

# Membaca file CSV
df = pd.read_csv('data.csv')

# Melihat 5 baris pertama
print(df.head())

# Info umum tentang data
print(df.info())  # Tipe data, jumlah baris, memory usage

# Statistik dasar
print(df.describe())  # Mean, std, min, max, quartile
```

**Istilah Penting:**
- **DataFrame**: Tabel dua dimensi (baris & kolom) yang mirip spreadsheet
- **Index**: Nomor baris (default: 0, 1, 2, ...)
- **Kolom**: Nama variabel/feature

### 2.2 Menangani Data Hilang (Missing Values)

Data hilang terjadi ketika ada kolom yang kosong (NaN = Not a Number)

**4 Strategi Penanganan:**

#### Strategi 1: Penghapusan (Dropping)
```python
# Hapus baris yang ada missing value
df_clean = df.dropna()

# Hapus kolom yang lebih dari 50% kosong
df_clean = df.dropna(thresh=0.5)
```
✅ **Kelebihan:** Sederhana, tidak ada bias imputasi
❌ **Kekurangan:** Bisa kehilangan banyak data

---

#### Strategi 2: Imputasi dengan Mean/Median
```python
# Isi missing value dengan rata-rata
df['kolom'] = df['kolom'].fillna(df['kolom'].mean())

# Lebih baik: Isi dengan median (tahan outlier)
df['kolom'] = df['kolom'].fillna(df['kolom'].median())
```
✅ **Kelebihan:** Menjaga ukuran sampel
❌ **Kekurangan:** Mengurangi variasi data

**Istilah:**
- **Mean**: Rata-rata (= sum semua / jumlah data)
- **Median**: Nilai tengah setelah data diurutkan (tahan terhadap nilai ekstrem/outlier)

---

#### Strategi 3: Imputasi dengan Modus
```python
# Untuk data kategorikal - isi dengan nilai paling sering
mode_val = df['kolom'].mode()[0]  # Nilai yang paling sering muncul
df['kolom'] = df['kolom'].fillna(mode_val)
```

---

#### Strategi 4: Imputasi Maju/Mundur (Time Series)
```python
# Jika data adalah deret waktu, bisa isi dengan nilai sebelumnya
df['kolom'] = df['kolom'].fillna(method='ffill')  # Forward fill
```

**Contoh Lengkap Menangani Missing Values:**

```python
import pandas as pd
import numpy as np

# Buat data simulasi dengan missing values
data = {
    'ID': [1, 2, 3, 4, 5, 6],
    'Gaji': [5000000, np.nan, 6000000, 4500000, np.nan, 7000000],
    'Departemen': ['IT', 'HR', np.nan, 'IT', 'HR', 'Finance'],
    'Tahun_Pengalaman': [2, 3, 1, np.nan, 4, 5]
}

df = pd.DataFrame(data)
print("Data Awal:")
print(df)
print("\nJumlah Missing Values per Kolom:")
print(df.isnull().sum())

# Strategi yang berbeda untuk tiap kolom
df_fixed = df.copy()

# Gaji: Isi dengan median (angka yang tahan outlier)
df_fixed['Gaji'] = df_fixed['Gaji'].fillna(df_fixed['Gaji'].median())

# Departemen: Isi dengan modus (nilai yang paling sering)
df_fixed['Departemen'] = df_fixed['Departemen'].fillna(
    df_fixed['Departemen'].mode()[0]
)

# Tahun_Pengalaman: Isi dengan mean (rata-rata)
df_fixed['Tahun_Pengalaman'] = df_fixed['Tahun_Pengalaman'].fillna(
    df_fixed['Tahun_Pengalaman'].mean()
)

print("\nData Setelah Imputasi:")
print(df_fixed)
```

---

### 2.3 Menghapus Data Duplikat

**Duplikat** = Baris yang benar-benar identik atau memiliki ID yang sama

```python
# Deteksi duplikat
print(df.duplicated())  # Return True/False per baris

# Hapus duplikat
df_unique = df.drop_duplicates()

# Hapus duplikat berdasarkan kolom tertentu (misalnya ID)
df_unique = df.drop_duplicates(subset=['ID'])
```

**Kenapa Harus Dihapus?**
- Data duplikat membuat model "bias" terhadap pola yang berulang
- Mengganggu akurasi training

---

### 2.4 Binning & Smoothing (Mengurangi Noise)

**Noise** = Variasi acak yang tidak bermakna dalam data

#### Konsep Binning:
Membagi data numerik berkelanjutan (continuous) menjadi kategori diskrit (discrete)

**Contoh:**
- Usia 20-30 → "Muda"
- Usia 31-45 → "Produktif"  
- Usia 46-60 → "Senior"

**2 Tipe Binning:**

**1. Equal-Width Binning** (Lebar bin sama)
```python
# Membagi 0-100 menjadi 4 bin berukuran 25 poin
# Bin 1: 0-25, Bin 2: 25-50, Bin 3: 50-75, Bin 4: 75-100
df['Harga_Bin'] = pd.cut(df['Harga'], bins=4)
```

**2. Equal-Frequency Binning** (Jumlah data per bin sama)
```python
# Setiap bin berisi jumlah data yang sama (~25% data per bin)
df['Harga_Bin'] = pd.qcut(df['Harga'], q=4)
```

**Contoh Praktis:**

```python
import pandas as pd
import numpy as np

# Data harga yang berfluktuasi
harga = np.array([15, 18, 22, 25, 28, 32, 35, 38, 42, 45, 
                  48, 52, 55, 58, 62, 65, 68, 72, 75, 80])

df = pd.DataFrame({'Harga_Asli': harga})

# Equal-Width Binning
df['Harga_Bin_EW'] = pd.cut(df['Harga_Asli'], bins=4)

# Equal-Frequency Binning
df['Harga_Bin_EF'] = pd.qcut(df['Harga_Asli'], q=4)

print(df)
```

---

## BAB 3: STATISTIK DESKRIPTIF

Menggambarkan karakteristik data dengan angka-angka sederhana

### 3.1 Ukuran Tendensi Sentral (Pusat Data)

**Mean (Rata-rata):**
```
Mean = (x₁ + x₂ + x₃ + ... + xₙ) / n
```
- Sensitif terhadap outlier
- Gunakan untuk data normal

**Median (Nilai Tengah):**
- Nilai yang membagi data menjadi 2 bagian sama
- Tahan terhadap outlier
- Lebih baik untuk data skewed

**Modus (Paling Sering):**
- Nilai yang paling banyak muncul
- Satu-satunya untuk data kategorikal

**Contoh:**
```python
import pandas as pd

data = pd.Series([1, 2, 2, 3, 3, 3, 100])  # Ada outlier 100

print(f"Mean: {data.mean()}")      # 16.14 (tertarik outlier)
print(f"Median: {data.median()}")  # 3 (tahan outlier)
print(f"Modus: {data.mode()[0]}")  # 3
```

### 3.2 Ukuran Dispersi (Penyebaran Data)

**Range (Jangkauan):**
```
Range = Max - Min
```

**Varians (Variance):**
```
Variance = Rata-rata dari (setiap nilai - mean)²
```
- Semakin besar = data semakin tersebar

**Standar Deviasi (Standard Deviation):**
```
Std Dev = √Variance
```
- Satuan yang sama dengan data asli
- Lebih mudah diinterpretasi

```python
data = pd.Series([1, 2, 3, 4, 5])

print(f"Variance: {data.var()}")      # 2.5
print(f"Std Dev: {data.std()}")       # 1.58
```

### 3.3 Bentuk Distribusi Data

#### Skewness (Kemencengan)

**Skewness ≈ 0:** Distribusi simetris (bentuk lonceng normal)

**Skewness Positif (> 0):** Ekor ke kanan
- Contoh: Distribusi kekayaan (kebanyakan miskin, sedikit kaya)

**Skewness Negatif (< 0):** Ekor ke kiri
- Contoh: Nilai ujian mudah (kebanyakan tinggi, sedikit rendah)

```python
from scipy import stats

data = np.array([1, 2, 2, 3, 3, 3, 4, 5, 10])  # Right-skewed
print(f"Skewness: {stats.skew(data)}")  # Positif
```

#### Kurtosis (Keruncingan)

**Kurtosis ≈ 0 (Mesokurtic):** Normal, puncak sedang

**Kurtosis Positif (Leptokurtic):** Puncak tajam, ekor tebal
- Banyak outlier
- Berisiko tinggi

**Kurtosis Negatif (Platykurtic):** Puncak datar, ekor tipis
- Sedikit outlier
- Data merata

```python
# Kurtosis dalam scipy (excess kurtosis, normal = 0)
print(f"Kurtosis: {stats.kurtosis(data)}")
```

---

## BAB 4: DISTRIBUSI PROBABILITAS

Fungsi matematika yang menunjukkan kemungkinan terjadinya suatu peristiwa

### 4.1 Distribusi Normal (Gaussian)

**Karakteristik:**
- Bentuk lonceng simetris
- Mean = Median = Modus
- Diatur oleh 2 parameter: μ (mean) dan σ (std dev)
- **Central Limit Theorem**: Rata-rata dari banyak sampel akan normal, meski populasi asal tidak normal

**Contoh Real-life:**
- Tinggi badan manusia
- Skor IQ
- Bobot produk

```python
import numpy as np
import matplotlib.pyplot as plt
from scipy import stats

# Generate data normal
data = np.random.normal(loc=100, scale=15, size=10000)

plt.hist(data, bins=50, density=True, alpha=0.7)
plt.title('Distribusi Normal')
plt.show()
```

### 4.2 Distribusi Binomial

**Karakteristik:**
- Hanya 2 hasil mungkin: Sukses atau Gagal
- Diatur oleh: n (jumlah percobaan) dan p (peluang sukses)
- Diskrit (bukan kontinyu)

**Contoh Real-life:**
- Pelemparan koin 10x, berapa peluang dapat 7 gambar?
- A/B Testing website
- Pass/Fail dalam ujian

```python
# Peluang mendapat 5 kepala dari 10 pelemparan koin (p=0.5)
peluang = stats.binom.pmf(k=5, n=10, p=0.5)
print(f"Peluang: {peluang}")  # 0.246
```

### 4.3 Distribusi Poisson

**Karakteristik:**
- Menghitung kejadian dalam interval waktu/ruang tertentu
- Diatur oleh: λ (lambda = rata-rata kejadian)
- Diskrit

**Contoh Real-life:**
- Jumlah pengunjung toko per jam
- Jumlah email yang diterima per hari
- Jumlah accident per jalan dalam sebulan

```python
# Peluang terima 5 email jika rata-rata 3 email per jam
peluang = stats.poisson.pmf(k=5, mu=3)
print(f"Peluang: {peluang}")
```

---

## BAB 5: VISUALISASI DATA

### 5.1 Visualisasi Univariat (1 Variabel)

#### Histogram
```python
import matplotlib.pyplot as plt

data = [1, 1, 2, 2, 2, 3, 3, 3, 3, 4, 5, 6, 7, 8, 8, 9]

plt.hist(data, bins=5, edgecolor='black')
plt.title('Histogram')
plt.xlabel('Nilai')
plt.ylabel('Frekuensi')
plt.show()
```
**Gunakan untuk:** Melihat distribusi, modus, skewness

#### Boxplot
```python
import matplotlib.pyplot as plt
import numpy as np

data = np.array([1, 2, 3, 4, 5, 5, 5, 6, 7, 8, 9, 10, 15])

plt.boxplot(data)
plt.title('Boxplot')
plt.ylabel('Nilai')
plt.show()
```

**Bagian-bagian Boxplot:**
```
        Max
         |
    _____|_____
   |           |   Q3 (75%)
   |  ---|---  |   Median (50%)
   |___________|   Q1 (25%)
         |
        Min
```

**Outlier:** Titik yang jauh di atas/bawah kumis (whisker)

### 5.2 Visualisasi Multivariat (2+ Variabel)

#### Scatter Plot
```python
import matplotlib.pyplot as plt

x = [1, 2, 3, 4, 5]
y = [2, 4, 5, 4, 6]

plt.scatter(x, y)
plt.title('Scatter Plot')
plt.xlabel('X')
plt.ylabel('Y')
plt.show()
```
**Gunakan untuk:** Melihat hubungan/korelasi antar variabel

#### Correlation Heatmap
```python
import seaborn as sns
import matplotlib.pyplot as plt

# Buat korelasi matrix
corr = df[['Gaji', 'Pengalaman', 'Usia']].corr()

# Visualisasi
sns.heatmap(corr, annot=True, cmap='coolwarm')
plt.show()
```

**Interpretasi Warna:**
- 🔴 Merah (1.0) = Korelasi sempurna positif
- ⚪ Putih (0.0) = Tidak ada korelasi
- 🔵 Biru (-1.0) = Korelasi sempurna negatif

---

## BAB 6: UJI HIPOTESIS (Hypothesis Testing)

Metode formal untuk membuat keputusan berdasarkan data

### 6.1 Konsep Dasar

**Hipotesis Nol (H₀):** Asumsi default (status quo)
- Biasanya: "Tidak ada perbedaan" atau "Tidak ada pengaruh"

**Hipotesis Alternatif (H₁):** Apa yang ingin kita buktikan
- Contoh: "Ada perbedaan signifikan"

### 6.2 P-Value & Keputusan

**P-value:** Probabilitas mendapat hasil observasi JIKA H₀ benar

**Rule:**
```
Jika p-value < 0.05 → TOLAK H₀ (Ada perbedaan signifikan)
Jika p-value ≥ 0.05 → GAGAL TOLAK H₀ (Tidak ada bukti perbedaan)
```

**Analogi:**
- p-value = Seberapa aneh hasil kita jika H₀ benar
- p-value kecil = Hasil sangat aneh, mungkin H₀ salah

### 6.3 T-Test (Membandingkan 2 Rata-rata)

**Kapan digunakan:**
- Membandingkan 2 kelompok
- Data normal atau n > 30
- Contoh: Apakah gaji Pria ≠ gaji Wanita?

```python
from scipy import stats
import numpy as np

# Simulasi gaji 2 kelompok
gaji_pria = np.array([5000000, 5500000, 6000000, 5800000, 6200000])
gaji_wanita = np.array([4500000, 5000000, 5200000, 5100000, 5300000])

# H₀: Rata-rata gaji Pria = Rata-rata gaji Wanita
# H₁: Rata-rata gaji Pria ≠ Rata-rata gaji Wanita

t_stat, p_value = stats.ttest_ind(gaji_pria, gaji_wanita)

print(f"T-statistic: {t_stat:.4f}")
print(f"P-value: {p_value:.4f}")

if p_value < 0.05:
    print("✓ TOLAK H₀: Ada perbedaan signifikan gaji")
else:
    print("✗ GAGAL TOLAK H₀: Tidak ada bukti perbedaan gaji")
```

**Tipe T-Test:**

| Tipe | Kegunaan | Contoh |
|------|----------|--------|
| One-Sample | Bandingkan 1 sampel dengan nilai konstan | Apakah rata-rata tinggi mahasiswa = 170cm? |
| Two-Sample | Bandingkan 2 kelompok berbeda | Apakah gaji Pria ≠ Wanita? |
| Paired | Bandingkan 2 pengukuran dari orang sama | Berat sebelum & sesudah diet |

---

## BAB 7: REGRESI LINEAR (Prediksi)

Algoritma pembelajaran tersupervisi (supervised) untuk memprediksi nilai kontinyu

### 7.1 Konsep Dasar

**Tujuan:** Mencari garis lurus terbaik yang mewakili hubungan X → Y

**Formula:** 
```
Y = a + b*X + error

Dimana:
- a = Intercept (nilai Y saat X=0)
- b = Slope/Koefisien (perubahan Y per unit X)
- error = Selisih prediksi dengan aktual
```

**Contoh:**
```
Gaji = 3000000 + 500000*Pengalaman + error
- Setiap 1 tahun pengalaman → gaji +500rb
- Tanpa pengalaman → gaji dasar 3juta
```

### 7.2 Training & Testing

**Kenapa Harus Dibagi?**
- Training set: Untuk mengajarkan model
- Testing set: Untuk menguji akurasi di data baru (generalisasi)
- Jika tidak dibagi: Model hanya "menghafal" data training → Overfitting

```python
from sklearn.model_selection import train_test_split

# Pisahkan 80% training, 20% testing
X_train, X_test, y_train, y_test = train_test_split(
    X, y, test_size=0.2, random_state=42
)
```

### 7.3 Implementasi Lengkap

```python
from sklearn.linear_model import LinearRegression
from sklearn.metrics import mean_squared_error, r2_score
from sklearn.model_selection import train_test_split
import numpy as np
import pandas as pd

# 1. PERSIAPAN DATA
# Simulasi: Prediksi gaji berdasarkan tahun pengalaman
np.random.seed(42)
pengalaman = np.array([[1], [2], [3], [4], [5], [6], [7], [8], [9], [10]])
gaji = 3000000 + pengalaman*500000 + np.random.normal(0, 200000, (10, 1))

# 2. BAGI DATA
X_train, X_test, y_train, y_test = train_test_split(
    pengalaman, gaji, test_size=0.2, random_state=42
)

# 3. TRAINING MODEL
model = LinearRegression()
model.fit(X_train, y_train)

# 4. PREDIKSI
y_pred_test = model.predict(X_test)

# 5. EVALUASI
mse = mean_squared_error(y_test, y_pred_test)
rmse = np.sqrt(mse)
r2 = r2_score(y_test, y_pred_test)

print(f"Intercept (a): {model.intercept_[0]:,.0f}")
print(f"Slope (b): {model.coef_[0][0]:,.0f}")
print(f"\nPerformansi:")
print(f"MSE: {mse:,.0f}")
print(f"RMSE: {rmse:,.0f}")
print(f"R² Score: {r2:.4f}")

# Interpretasi:
# - Setiap 1 tahun pengalaman → gaji naik b
# - Model menjelaskan r2*100% variasi gaji
```

### 7.4 Metrik Evaluasi

**Mean Squared Error (MSE):**
```
MSE = Rata-rata dari (prediksi - aktual)²
```
- Menghukum error besar lebih keras
- Satuan = kuadrat dari variabel target

**Root Mean Squared Error (RMSE):**
```
RMSE = √MSE
```
- Satuan sama dengan variabel target
- Lebih mudah interpretasi

**R-Squared (R²):**
```
R² = 1 - (SS_residual / SS_total)
```
- Nilai 0-1 (bisa negatif jika model sangat buruk)
- **Interpretasi:** Model menjelaskan R²×100% variasi Y
- R² = 0.8 → Model menjelaskan 80% variasi
- R² = 1.0 → Prediksi sempurna

**Contoh Interpretasi:**
```
R² = 0.75
Berarti: 75% variasi gaji bisa dijelaskan oleh pengalaman
         25% dipengaruhi faktor lain (skill, sertifikat, dll)
```

---

## BAB 8: CLUSTERING (K-MEANS)

Algoritma pembelajaran tanpa supervisi (unsupervised) untuk mengelompokkan data

### 8.1 Konsep Dasar

**Tujuan:** Membagi data menjadi K kelompok yang mirip dalam satu cluster dan berbeda antar cluster

**Analogi:**
- Kasir toko mengelompokkan pelanggan: VIP, Regular, New
- Rumah sakit mengelompokkan pasien: Kritis, Sedang, Ringan
- Tidak ada label "benar/salah", murni explorasi

### 8.2 Algoritma K-Means

**Langkah-langkah:**

1. **Pilih K** (jumlah cluster)
2. **Tentukan centroid awal** (pusat cluster) secara random
3. **Assign data** ke centroid terdekat
4. **Update centroid** = rata-rata semua data dalam cluster
5. **Ulangi** langkah 3-4 sampai centroid stabil

**Istilah Penting:**
- **Centroid:** Pusat dari sebuah cluster
- **Inertia:** Total jarak semua data ke centroid terdekat mereka
- **Konvergen:** Centroid tidak berubah lagi

### 8.3 Pentingnya Scaling

**Masalah:**
```
Gaji (juta): 5, 6, 7
Usia: 25, 30, 35

Jarak Euclidean = √((5-6)² + (25-30)²) = √(1 + 2500) ≈ 50
Usia mendominasi meski skala berbeda 1000x!
```

**Solusi: StandardScaler**
```python
from sklearn.preprocessing import StandardScaler

# Standarisasi: (x - mean) / std
# Hasilnya: Mean=0, Std=1 untuk semua kolom

scaler = StandardScaler()
X_scaled = scaler.fit_transform(X)
```

### 8.4 Menentukan K Optimal

#### Elbow Method

```python
from sklearn.cluster import KMeans
import matplotlib.pyplot as plt

inertia_list = []
K_range = range(1, 10)

for k in K_range:
    kmeans = KMeans(n_clusters=k, random_state=42)
    kmeans.fit(X_scaled)
    inertia_list.append(kmeans.inertia_)

plt.plot(K_range, inertia_list, 'bo-')
plt.xlabel('Jumlah Cluster (K)')
plt.ylabel('Inertia')
plt.title('Elbow Method')
plt.show()
```

**Cara Membaca:**
- Cari titik "siku" di grafik
- Inertia turun tajam → Mulai flat → Pilih K di titik transisi
- Contoh: Jika siku di K=4, pilih K=4

#### Silhouette Analysis

**Silhouette Score:** Mengukur seberapa bagus cluster separation

```
Score 1: Sempurna (jauh dari cluster lain)
Score 0: Ambiguous (di perbatasan)
Score -1: Salah tempat (lebih dekat cluster lain)
```

```python
from sklearn.metrics import silhouette_score

silhouette_scores = []
for k in K_range:
    kmeans = KMeans(n_clusters=k, random_state=42)
    labels = kmeans.fit_predict(X_scaled)
    score = silhouette_score(X_scaled, labels)
    silhouette_scores.append(score)

# Pilih K dengan silhouette score tertinggi
best_k = K_range[silhouette_scores.index(max(silhouette_scores))]
```

### 8.5 Implementasi Lengkap K-Means

```python
from sklearn.cluster import KMeans
from sklearn.preprocessing import StandardScaler
from sklearn.metrics import silhouette_score
from sklearn.datasets import make_blobs
import matplotlib.pyplot as plt
import numpy as np

# 1. PERSIAPAN DATA
# Buat data simulasi: 200 titik, 3 kelompok alami
X, _ = make_blobs(n_samples=200, centers=3, random_state=42)

# 2. SCALING (WAJIB!)
scaler = StandardScaler()
X_scaled = scaler.fit_transform(X)

# 3. MENCARI K OPTIMAL
inertias = []
silhouettes = []
K_range = range(2, 8)

for k in K_range:
    kmeans = KMeans(n_clusters=k, n_init=10, random_state=42)
    kmeans.fit(X_scaled)
    inertias.append(kmeans.inertia_)
    silhouettes.append(silhouette_score(X_scaled, kmeans.labels_))

# Plot
fig, (ax1, ax2) = plt.subplots(1, 2, figsize=(12, 4))

ax1.plot(K_range, inertias, 'bo-')
ax1.set_xlabel('K')
ax1.set_ylabel('Inertia')
ax1.set_title('Elbow Method')

ax2.plot(K_range, silhouettes, 'ro-')
ax2.set_xlabel('K')
ax2.set_ylabel('Silhouette Score')
ax2.set_title('Silhouette Analysis')

plt.show()

# 4. TRAINING DENGAN K TERBAIK
best_k = 3  # Asumsi optimal
kmeans_final = KMeans(n_clusters=best_k, n_init=10, random_state=42)
labels = kmeans_final.fit_predict(X_scaled)

# 5. HASIL
print(f"Centroid:\n{kmeans_final.cluster_centers_}")
print(f"Label cluster setiap data:\n{labels[:20]}")  # 20 pertama
```

---

## CHEATSHEET UNTUK UJIAN

### 1. Data Cleaning

| Masalah | Solusi | Kode |
|---------|--------|------|
| Missing values | Median/Mean | `df['col'].fillna(df['col'].median())` |
| Data duplikat | Hapus | `df.drop_duplicates()` |
| Categorical | Encode | `pd.get_dummies(df)` |

### 2. Statistik

| Istilah | Formula | Kapan Pakai |
|---------|---------|-----------|
| Mean | Sum/n | Data normal |
| Median | Nilai tengah | Data skewed |
| Std Dev | √Variance | Ukur penyebaran |
| Skewness | Asimetri | Bentuk distribusi |

### 3. Testing

| Test | Untuk | H₀ |
|------|-------|-----|
| T-Test | 2 rata-rata | Mean A = Mean B |
| Chi-Square | Kategorikal | Kategori independen |

### 4. Modeling

| Model | Tujuan | Output |
|-------|--------|--------|
| Linear Regression | Prediksi kontinyu | Y = a + bX |
| K-Means | Clustering | K centroid, labels |

### 5. Metrik

| Metrik | Formula | Interpretasi |
|--------|---------|--------------|
| RMSE | √MSE | Semakin kecil semakin baik |
| R² | 1 - SS_res/SS_tot | % variasi dijelaskan |

---

## TIPS PENTING UNTUK UJIAN

✅ **PASTI DITANYA:**
1. Cara menangani missing values (kenapa & bagaimana)
2. Perbedaan Mean vs Median (kapan pakai)
3. Konsep p-value di hypothesis testing
4. Perbedaan supervised vs unsupervised learning
5. Cara menentukan K di K-Means (elbow method)
6. Interpretasi R² score

✅ **SERING DITANYA:**
7. Preprocessing data (scaling, binning)
8. Visualisasi data (histogram, scatter, heatmap)
9. Metrics evaluasi (MSE, RMSE, R²)
10. Mengapa train-test split penting

✅ **ALGORITHM YANG SERING DIMINTA KODE:**
- Handling missing values dengan berbagai strategi
- T-Test implementation
- Linear Regression (training & evaluasi)
- K-Means clustering (dengan scaling)

---

## RINGKASAN ALUR DATA SCIENCE

```
1. IMPORT & LOAD DATA
   ↓
2. DATA CLEANING (handling missing, duplikat, outlier)
   ↓
3. EDA (statistik, visualisasi, distribusi)
   ↓
4. HYPOTHESIS TESTING (validasi asumsi)
   ↓
5. PREPROCESSING (scaling, encoding)
   ↓
6. MODELING (training dengan train set)
   ↓
7. EVALUATION (test dengan test set)
   ↓
8. INSIGHT & DECISION MAKING
```

---

Semoga catatan ini lebih mudah dipahami! Selamat belajar! 🚀
