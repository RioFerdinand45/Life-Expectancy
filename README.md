# 📊 Life Expectancy Data Analysis & Regression Modeling

Proyek ini bertujuan untuk menganalisis faktor-faktor sosio-ekonomi, imunisasi, dan mortalitas yang memengaruhi angka harapan hidup (*Life Expectancy*) di berbagai negara, serta membangun model regresi mesin (*Machine Learning Regression*) untuk memprediksi angka harapan hidup berdasarkan indikator kesehatan global dari World Health Organization (WHO).

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
  - Dilakukan penanganan nilai ekstrem pada kolom `Adult Mortality`, `BMI`, dan `GDP` menggunakan metode *Interquartile Range* (IQR) *clipping* (pembatasan batas atas dan bawah).
- **Pemeriksaan Duplikasi:** Mengonfirmasi bahwa tidak terdapat baris data ganda pada dataset.
- **Encoding & Seleksi Fitur:**
  - Kolom `Status` dikonversi menjadi numerik menggunakan `LabelEncoder`.
  - Kolom `Country` dihapus dari data pemodelan karena bersifat pengenal unik kontekstual yang tidak digunakan langsung pada regresi numerik.
- **Standarisasi Fitur:**
  - Seluruh fitur prediktor numerik ditransformasi menggunakan `StandardScaler` agar memiliki distribusi dengan rata-rata 0 dan varians 1. Kolom target `Life expectancy` dipertahankan dalam skala aslinya.

### 2. Eksplorasi Visualisasi Data (EDA)
- Pembuatan distribusi histogram dan *Kernel Density Estimation* (KDE) untuk kolom target `Life expectancy` guna memahami sebaran angka harapan hidup global.

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
