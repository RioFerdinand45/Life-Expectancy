# 📊 Life Expectancy Data Analysis & Regression Modeling

Proyek ini bertujuan untuk menganalisis faktor-faktor sosio-ekonomi, imunisasi, dan mortalitas yang memengaruhi angka harapan hidup (_Life Expectancy_) di berbagai negara, serta membangun model regresi mesin (_Machine Learning Regression_) untuk memprediksi angka harapan hidup berdasarkan indikator kesehatan global dari World Health Organization (WHO).

---

## 📌 Ringkasan Dataset

Dataset yang digunakan memuat informasi indikator kesehatan masyarakat dan ekonomi dari 193 negara.

- **Ukuran Data Raw:** 2.938 baris dan 22 kolom.
- **Tipe Data:** 16 atribut numerik (`float64`), 4 atribut integer (`int64`), dan 2 atribut kategorikal (`str`).
- **Fitur Utama:**
  - `Country` & `Year`: Nama negara dan tahun observasi (2000–2015).
  - `Status`: Status perkembangan negara (`Developing` vs `Developed`).
  - `Life expectancy`: Target prediksi (angka harapan hidup dalam tahun).
  - Indikator Kesehatan & Imunisasi: `Adult Mortality`, `infant deaths`, `Hepatitis B`, `Measles`, `BMI`, `under-five deaths`, `Polio`, `Diphtheria`, `HIV/AIDS`.
  - Indikator Ekonomi & Pendidikan: `percentage expenditure`, `Alcohol`, `Total expenditure`, `GDP`, `Population`, `thinness 1-19 years`, `thinness 5-9 years`, `Income composition of resources`, `Schooling`.

---

## 🛠️ Alur Kerja & Metodologi

Proyek ini diselesaikan melalui alur kerja analisis data terstruktur sebagai berikut:

### 1. Eksplorasi Data & Pra-pemrosesan (Data Preprocessing)

- **Pembersihan Nama Kolom:** Menghapuskan spasi berlebih pada seluruh nama atribut (`df.columns.str.strip()`).
- **Penanganan Missing Values:**
  - Nilai hilang pada variabel numerik (seperti `Hepatitis B`, `Population`, `GDP`, `Total expenditure`, dll.) diimputasi menggunakan nilai **median** masing-masing kolom.
  - Nilai hilang pada variabel kategorikal diimputasi menggunakan nilai **modus**.
- **Penanganan Outlier:**
  - Dilakukan penanganan nilai ekstrem pada kolom `Adult Mortality`, `BMI`, dan `GDP` menggunakan metode _Interquartile Range_ (IQR) _clipping_ (pembatasan batas atas dan bawah).
- **Pemeriksaan Duplikasi:** Mengonfirmasi bahwa tidak terdapat baris data ganda pada dataset.
- **Encoding & Seleksi Fitur:**
  - Kolom `Status` dikonversi menjadi numerik menggunakan `LabelEncoder`.
  - Kolom `Country` dihapus dari data pemodelan karena bersifat pengenal unik kontekstual yang tidak digunakan langsung pada regresi numerik.
- **Standarisasi Fitur:**
  - Seluruh fitur prediktor numerik ditransformasi menggunakan `StandardScaler` agar memiliki distribusi dengan rata-rata 0 dan varians 1. Kolom target `Life expectancy` dipertahankan dalam skala aslinya.

### 2. Eksplorasi Visualisasi Data (EDA)

- Pembuatan distribusi histogram dan _Kernel Density Estimation_ (KDE) untuk kolom target `Life expectancy` guna memahami sebaran angka harapan hidup global.

---

## 💻 Dependensi & Perpustakaan Python

Proyek ini dibangun menggunakan modul Python berikut:

```python
import pandas as pd
import numpy as np
import seaborn as sns
import matplotlib.pyplot as plt
import joblib
import sklearn
from sklearn.preprocessing import StandardScaler, LabelEncoder
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LinearRegression
from sklearn.ensemble import RandomForestRegressor, GradientBoostingRegressor
from sklearn.metrics import mean_absolute_error, mean_squared_error, r2_score
```

---

## 🚀 Menjalankan API Prediksi Secara Lokal

API Flask menyediakan endpoint `POST /predict` untuk memprediksi angka harapan hidup. Panduan ini menjalankan API di komputer lokal; alamat `127.0.0.1` **belum** membuat aplikasi dapat diakses melalui internet.

### 1. Siapkan environment dan dependensi

Buka Command Prompt di folder proyek, lalu jalankan:

```cmd
cd /d "C:\Users\X\Jupyter\Machine Learning Praktikum"
py -m venv .venv
.\.venv\Scripts\activate
python -m pip install pandas numpy seaborn matplotlib scikit-learn joblib Flask
```

Jika folder `.venv` sudah ada, lewati perintah `py -m venv .venv`. Pastikan notebook dan API menggunakan interpreter `.venv` yang sama.

### 2. Latih model dan simpan artefak

Buka `Life Expectancy.ipynb` di VS Code, pilih kernel `.venv`, lalu pilih **Restart Kernel and Run All**. Setelah sel training dan evaluasi dijalankan, sel terakhir menyimpan dua file berikut di folder proyek:

- `best_life_expectancy_model.joblib`
- `best_life_expectancy_scaler.joblib`

API memerlukan kedua file tersebut. Jika salah satu tidak ditemukan, jalankan notebook terlebih dahulu.

### 3. Jalankan server API

Di Command Prompt pertama, jalankan:

```cmd
cd /d "C:\Users\X\Jupyter\Machine Learning Praktikum"
.\.venv\Scripts\python.exe testing_deploy.py
```

Server berjalan pada `http://127.0.0.1:5000`. Biarkan jendela ini tetap terbuka selama API digunakan. Peringatan Flask bahwa server ini adalah development server normal untuk pengujian lokal, tetapi server ini tidak ditujukan untuk produksi.

### 4. Kirim data dan verifikasi prediksi

Buka Command Prompt kedua di folder proyek dan jalankan:

```cmd
cd /d "C:\Users\X\Jupyter\Machine Learning Praktikum"
curl.exe -i -X POST "http://127.0.0.1:5000/predict" -H "Content-Type: application/json" --data-binary "@data.json"
```

Jika berhasil, respons memuat status `HTTP/1.1 200 OK` dan prediksi, misalnya:

```json
{ "prediction": [75.0] }
```

`data.json` harus memiliki properti `data` yang berisi satu atau lebih baris; setiap baris harus berisi 20 nilai numerik dengan urutan fitur berikut:

1. `Year`
2. `Status` (hasil encoding: `Developed` = `0`, `Developing` = `1`)
3. `Adult Mortality`
4. `infant deaths`
5. `Alcohol`
6. `percentage expenditure`
7. `Hepatitis B`
8. `Measles`
9. `BMI`
10. `under-five deaths`
11. `Polio`
12. `Total expenditure`
13. `Diphtheria`
14. `HIV/AIDS`
15. `GDP`
16. `Population`
17. `thinness  1-19 years`
18. `thinness 5-9 years`
19. `Income composition of resources`
20. `Schooling`

API menerapkan scaler yang disimpan dari notebook sebelum menjalankan prediksi. Untuk menghentikan server, tekan `Ctrl+C` di Command Prompt pertama.
