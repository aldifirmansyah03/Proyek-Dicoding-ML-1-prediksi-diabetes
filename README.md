# 📘 Laporan Proyek Machine Learning Expert Dicoding: Prediksi Diabetes Menggunakan Data Klinis

## 🩺 Domain Proyek: Kesehatan Preventif dan Deteksi Dini Diabetes

Diabetes adalah salah satu penyakit kronis paling umum di dunia yang berdampak besar terhadap kesehatan masyarakat dan sistem pelayanan kesehatan. Menurut International Diabetes Federation (IDF), pada tahun 2024 diperkirakan ada sekitar 589 juta orang dewasa yang hidup dengan diabetes, dan jumlah ini dapat mencapai 853 juta pada tahun 2050. Di Indonesia sendiri, jumlah penderita diperkirakan meningkat dari 19,5 juta (2021) menjadi 28,6 juta pada 2045.

Melihat urgensinya, proyek ini berfokus pada pembangunan sistem prediksi diabetes menggunakan algoritma machine learning berbasis data klinis pasien. Dengan pendekatan prediktif ini, sistem diharapkan dapat membantu proses skrining awal secara otomatis, mempercepat diagnosis, dan mendukung kebijakan kesehatan berbasis data.

---

## 🎯 Business Understanding

### Problem Statement

1. Bagaimana cara mempersiapkan data klinis agar siap digunakan dalam pemodelan machine learning?
2. Algoritma apa yang paling efektif dalam memprediksi kemungkinan seseorang menderita diabetes berdasarkan data demografis dan medis?

### Goals

* Menyusun pipeline preprocessing yang efisien dan akurat.
* Membangun dan mengevaluasi model klasifikasi biner untuk prediksi status diabetes.
* Memilih model terbaik berdasarkan performa dan error terkecil.

### Solution Statement

Solusi dilakukan melalui tahapan berikut:

* **Preprocessing**:

  * Menghapus kolom tidak relevan (`clinical_notes`).
  * Menggabungkan kolom `race` menjadi satu kategori.
  * Menangani outlier dengan metode IQR.
  * Encoding fitur kategorikal dan standarisasi fitur numerik.
  * Membagi data ke dalam set training dan testing (90:10).
* **Modeling**:

  * Menggunakan 3 algoritma: **K-Nearest Neighbor**, **Random Forest**, dan **AdaBoost**.
  * Evaluasi menggunakan metrik **Mean Squared Error (MSE)**.

---

## 📊 Data Understanding

### Dataset

Dataset yang digunakan berasal dari [Kaggle: Diabetes Clinical Dataset (100K Rows)](https://www.kaggle.com/datasets/ziya07/diabetes-clinical-dataset100k-rows), dengan total 100.000 baris dan 12 kolom. Dataset ini mewakili data klinis pasien dari berbagai ras dan lokasi di Amerika Serikat.

### Fitur Utama

* `age`, `bmi`, `hbA1c_level`, `blood_glucose_level`
* `gender`, `smoking_history`, `race`, `location`
* `hypertension`, `heart_disease`, `diabetes`

### EDA & Pembersihan Data

* Tidak ditemukan **missing value**.
* **Outliers** dibersihkan dengan metode IQR.
* Distribusi data dianalisis melalui visualisasi histogram, boxplot, pairplot, dan heatmap korelasi.
* Ketidakseimbangan kelas ditemukan (mayoritas pasien tidak diabetes), dan dipertimbangkan dalam interpretasi hasil.

---

## 🧹 Data Preparation

1. **Encoding**
   Fitur kategorikal diubah menjadi numerik menggunakan LabelEncoder (`gender`, `race`, `smoking_history`, `location`).
2. **Standardisasi**
   Fitur numerik (`age`, `bmi`, `hbA1c_level`, `blood_glucose_level`) distandarisasi menggunakan `StandardScaler`.
3. **Splitting**
   Dataset dibagi menjadi **training (90%)** dan **testing (10%)**.

Total data final yang digunakan setelah cleaning: **66.511 baris**.

---

## 🧠 Modeling

Tiga model diterapkan dan dibandingkan:

| Algoritma         | Parameter Utama                |
| ----------------- | ------------------------------ |
| **KNN**           | k = 10                         |
| **Random Forest** | n\_estimators = 50, depth = 16 |
| **AdaBoost**      | learning\_rate = 0.05          |

Setiap model dievaluasi dengan metrik **Mean Squared Error (MSE)** pada data training dan testing.

---

## ✅ Evaluation

### Hasil Evaluasi (dalam ribuan)

| Model             | MSE Train    | MSE Test     |
| ----------------- | ------------ | ------------ |
| KNN               | 0.000035     | 0.000034     |
| **Random Forest** | **0.000016** | **0.000016** |
| AdaBoost          | 0.000053     | 0.000048     |

> **Kesimpulan**:
> Random Forest adalah model dengan akurasi terbaik dan generalisasi tinggi, ditunjukkan dari nilai MSE terendah di kedua set data.

### Visualisasi Evaluasi

Hasil MSE divisualisasikan menggunakan bar chart untuk memperjelas perbandingan antar model.

---

## 🧾 Kesimpulan

Model prediksi diabetes berbasis **Random Forest** menunjukkan performa terbaik dalam proyek ini. Pipeline yang dibangun mampu menangani data real-world dengan ukuran besar, kompleksitas fitur, dan ketidakseimbangan kelas. Sistem ini dapat dikembangkan lebih lanjut menjadi aplikasi klinis untuk mendukung dokter dan tenaga kesehatan dalam skrining awal pasien berisiko diabetes.

---

## 📚 Referensi

1. Kemenkes RI (2024). [Saatnya Mengatur Si Manis](https://sehatnegeriku.kemkes.go.id/baca/blog/20240110/5344736/saatnya-mengatur-si-manis/)
2. IDF Diabetes Atlas. [Global Report](https://diabetesatlas.org/data-by-location/global/)
3. DQLab, Trivusi, IBM, AWS – Dokumentasi algoritma KNN, RF, AdaBoost, Boosting
