# MODULE 7: REGRESI LINEAR (LINEAR REGRESSION)
## Prediksi Nilai Kontinyu (Predicting Continuous Values)

---

## 7.1 KONSEP DASAR

### Apa Itu Linear Regression?
Linear Regression adalah algoritma pembelajaran tersupervisi (supervised) yang digunakan untuk **memprediksi nilai kontinyu** berdasarkan satu atau lebih variabel input.

**Tujuan:** Mencari garis lurus terbaik yang menunjukkan hubungan antara X (input) dan Y (output).

### Formula Dasar
```
Y = a + b*X + error

Dimana:
- Y = Variabel yang ingin diprediksi (output/dependent variable)
- X = Variabel input untuk memprediksi (input/independent variable)
- a = Intercept (nilai Y saat X=0)
- b = Slope/Koefisien (perubahan Y per unit X)
- error = Selisih antara prediksi dan nilai aktual
```

### Contoh Real-Life
```
Gaji = 3,000,000 + 500,000 * Pengalaman + error

Interpretasi:
- Intercept (a) = 3,000,000 = Gaji baseline (tanpa pengalaman)
- Slope (b) = 500,000 = Setiap 1 tahun pengalaman → gaji naik 500,000
- Contoh: Orang dengan 5 tahun pengalaman → Gaji = 3,000,000 + 500,000*5 = 5,500,000
```

---

## 7.2 TRAIN-TEST SPLIT (PEMBAGIAN DATA)

### Mengapa Harus Dibagi?

**Masalah:** Jika kita melatih dan menguji model pada DATA YANG SAMA, model hanya akan "menghafal" pola, bukan benar-benar belajar. Ini disebut **OVERFITTING**.

**Solusi:** Bagi data menjadi 2 bagian:
- **Training Set (80%)** = Data untuk mengajarkan model
- **Testing Set (20%)** = Data baru untuk menguji akurasi model

**Analogi:** Seperti mengajar soldiermu di training ground, tapi mengujinya di pertempuran nyata dengan kondisi berbeda.

### Parameter train_test_split
```python
from sklearn.model_selection import train_test_split

X_train, X_test, y_train, y_test = train_test_split(
    X, y, test_size=0.2, random_state=42
)
```

**Parameter Penting:**

1. **test_size=0.2**
   - Berarti 20% data untuk testing, 80% untuk training
   - Jika ada 100 data points → 80 training, 20 testing
   - Bisa diubah ke 0.3 (30% testing) jika data terbatas

2. **random_state=42**
   - "Seed" untuk reprodusibilitas
   - Memastikan split SELALU SAMA setiap kali dijalankan
   - Angka (42, 123, 999) tidak penting, yang penting konsistensi
   - Konsep sama dengan np.random.seed() di NumPy

---

## 7.3 ALUR IMPLEMENTASI LENGKAP

### Step 1: Import Libraries
```python
from sklearn.linear_model import LinearRegression
from sklearn.metrics import mean_squared_error, r2_score
from sklearn.model_selection import train_test_split
import numpy as np
import pandas as pd
```

### Step 2: Persiapan Data
```python
# Contoh: Prediksi gaji berdasarkan tahun pengalaman
np.random.seed(42)
pengalaman = np.array([[1], [2], [3], [4], [5], [6], [7], [8], [9], [10]])
gaji = 3000000 + pengalaman*500000 + np.random.normal(0, 200000, (10, 1))
```

**Penjelasan:**
- Membuat data simulasi dengan 10 orang
- Pengalaman: 1-10 tahun
- Gaji: baseline 3juta + 500rb per tahun + noise random

### Step 3: Bagi Data (Train-Test Split)
```python
X_train, X_test, y_train, y_test = train_test_split(
    pengalaman, gaji, test_size=0.2, random_state=42
)
```

**Hasil (dengan 10 data):**
- X_train: ~8 data untuk training
- X_test: ~2 data untuk testing

### Step 4: Training Model
```python
model = LinearRegression()
model.fit(X_train, y_train)
```

**Apa yang terjadi:**
- Model melihat X_train dan y_train
- Menghitung nilai a (intercept) dan b (slope) yang optimal
- Setelah ini, model "tahu" cara memprediksi

### Step 5: Prediksi
```python
y_pred_test = model.predict(X_test)
```

**Penjelasan:**
- Menggunakan model yang sudah trained
- Memberikan X_test (data baru) yang belum pernah dilihat
- Model mengeluarkan prediksi untuk setiap X_test

### Step 6: Evaluasi Model
```python
mse = mean_squared_error(y_test, y_pred_test)
rmse = np.sqrt(mse)
r2 = r2_score(y_test, y_pred_test)

print(f"Intercept (a): {model.intercept_[0]:,.0f}")
print(f"Slope (b): {model.coef_[0][0]:,.0f}")
print(f"\nPerformansi:")
print(f"MSE: {mse:,.0f}")
print(f"RMSE: {rmse:,.0f}")
print(f"R² Score: {r2:.4f}")
```

---

## 7.4 METRIK EVALUASI

### 1. Mean Squared Error (MSE)

**Formula:**
```
MSE = Rata-rata dari (prediksi - aktual)²
```

**Contoh:**
```
Prediksi: [5juta, 6juta]
Aktual:   [5.2juta, 5.8juta]
Error:    [0.2juta, 0.2juta]
Error²:   [0.04juta², 0.04juta²]
MSE = (0.04 + 0.04) / 2 = 0.04juta²
```

**Interpretasi:**
- Semakin KECIL MSE = semakin BAIK
- Menghukum error besar lebih keras (karena dikuadratkan)
- Satuan = kuadrat dari variabel target (sulit dipahami)

### 2. Root Mean Squared Error (RMSE)

**Formula:**
```
RMSE = √MSE
```

**Contoh:**
```
MSE = 0.04juta²
RMSE = √0.04juta² = 0.2juta
```

**Interpretasi:**
- Satuan SAMA dengan variabel target (mudah dipahami)
- RMSE = 200,000 → "Rata-rata prediksi kita salah 200,000"
- Semakin KECIL RMSE = semakin BAIK

### 3. R-Squared (R²)

**Formula:**
```
R² = 1 - (SS_residual / SS_total)
```

**Rentang:** 0 hingga 1 (bisa negatif jika sangat buruk)

**Interpretasi:**
```
R² = 0.8  → Model menjelaskan 80% variasi Y
          → 20% dipengaruhi faktor lain

R² = 1.0  → Prediksi sempurna (jarang terjadi di real-world)
R² = 0.5  → Model menjelaskan hanya 50%
R² = 0.0  → Model tidak berguna (sama dengan menebak rata-rata)
R² < 0    → Model lebih buruk dari sekadar menebak (sangat buruk)
```

**Contoh Interpretasi:**
```
Jika memprediksi Gaji dengan R² = 0.75:
- 75% perbedaan gaji bisa dijelaskan oleh pengalaman
- 25% dipengaruhi faktor lain: skill, sertifikat, lokasi, koneksi
```

**Standar Kualitas (tidak mutlak, tergantung konteks):**
```
R² ≥ 0.7  = Sangat baik
R² 0.5-0.7 = Cukup baik
R² < 0.5  = Perlu improvement
```

---

## 7.5 KODE LENGKAP (COPY-PASTE READY)
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
```

---

## 7.6 RINGKASAN POIN PENTING

✅ **Linear Regression adalah metode untuk MEMPREDIKSI nilai kontinyu**

✅ **Formula: Y = a + b*X**
   - a = intercept (Y saat X=0)
   - b = slope (perubahan Y per unit X)

✅ **WAJIB bagi data 80% training, 20% testing**
   - Hindari overfitting
   - Test pada data "baru" yang belum pernah dilihat

✅ **3 Metrik Evaluasi:**
   - MSE = rata-rata error kuadrat (kecil = baik)
   - RMSE = akar MSE (satuan sama dengan Y, mudah dipahami)
   - R² = % variasi Y yang dijelaskan X (0-1, besar = baik)

✅ **random_state=42 untuk reprodusibilitas hasil**

---

## QUICK CHECKLIST SEBELUM PRESENTASI

- [ ] Pahami formula Y = a + b*X
- [ ] Tahu kenapa perlu train-test split
- [ ] Bisa menjelaskan intercept dan slope
- [ ] Mengerti 3 metrik: MSE, RMSE, R²
- [ ] Bisa membaca output model.intercept_ dan model.coef_
- [ ] Tahu interpretasi R² (% variasi yang dijelaskan)
