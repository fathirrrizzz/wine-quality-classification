# Klasifikasi Kualitas Anggur

Sebuah proyek Pembelajaran Mesin (*Machine Learning*) untuk mengklasifikasikan kualitas anggur berdasarkan sifat fisikokimia menggunakan Python. Proyek ini dikembangkan sebagai bagian dari Ujian Tengah Semester (UTS) Data Mining.

## Gambaran Umum Proyek

Klasifikasi kualitas anggur adalah tugas pembelajaran mesin yang bertujuan untuk memprediksi kualitas anggur berdasarkan karakteristik fisikokimianya.

Proyek ini menggunakan algoritma pembelajaran terawasi (*supervised learning*) untuk mengklasifikasikan kualitas anggur menggunakan sifat-sifat kimia seperti tingkat keasaman, kadar gula, klorida, densitas, pH, sulfat, dan alkohol.

Alur kerjanya mencakup analisis data eksploratif, prapemrosesan data, pelatihan model, perbandingan model, penyetelan hiperparameter (*hyperparameter tuning*), evaluasi, dan prediksi pada data pengujian yang belum pernah dilihat.

## Tujuan

- Mengeksplorasi dan memahami dataset kualitas anggur.
- Melakukan pembersihan dan prapemrosesan data.
- Mengidentifikasi hubungan antara sifat fisikokimia dan kualitas anggur.
- Membangun dan membandingkan berbagai algoritma klasifikasi.
- Mengevaluasi kinerja model menggunakan metrik klasifikasi yang sesuai.
- Memilih model dengan kinerja terbaik untuk memprediksi kualitas anggur.
- Menghasilkan prediksi untuk dataset pengujian.

## Deskripsi Dataset

Dataset terdiri dari dua file utama:

| Dataset | Deskripsi |
|---|---|
| `data_training.csv` | Dataset pelatihan yang berisi fitur fisikokimia dan label kualitas anggur. |
| `data_testing.csv` | Dataset pengujian yang berisi fitur fisikokimia tanpa label kualitas. |

Dataset ini berisi 11 fitur fisikokimia:

1. Keasaman tetap (*Fixed acidity*)
2. Keasaman mudah menguap (*Volatile acidity*)
3. Asam sitrat (*Citric acid*)
4. Gula sisa (*Residual sugar*)
5. Klorida (*Chlorides*)
6. Sulfur dioksida bebas (*Free sulfur dioxide*)
7. Total sulfur dioksida (*Total sulfur dioxide*)
8. Densitas (*Density*)
9. pH
10. Sulfat (*Sulphates*)
11. Alkohol (*Alcohol*)

Variabel targetnya adalah `quality`, yang mewakili klasifikasi kualitas anggur.

## Alur Kerja Proyek

### 1. Pemahaman Data dan Analisis Data Eksploratif (EDA)
Analisis awal memeriksa struktur dataset, statistik deskriptif, distribusi target, nilai yang hilang (*missing values*), observasi duplikat, dan hubungan antar variabel.

Visualisasi mencakup histogram, diagram kotak (*boxplots*), analisis korelasi, dan perbandingan fitur antar kelas kualitas anggur.

### 2. Prapemrosesan Data
Tahap prapemrosesan meliputi:
- Memeriksa dan menangani nilai yang hilang (*missing values*).
- Mengidentifikasi observasi yang berulang.
- Memeriksa tipe data dan konsistensi.
- Memeriksa potensi pencilan (*outliers*).
- Menyiapkan fitur untuk algoritma klasifikasi.
- Menerapkan penskalaan (*scaling*) jika diperlukan oleh model.

### 3. Pengembangan Model
Beberapa algoritma klasifikasi dievaluasi dan dibandingkan untuk mengidentifikasi model yang cocok untuk dataset ini.

Perbandingan model mencakup berbagai pendekatan, seperti:
- Regresi Logistik (*Logistic Regression*)
- K-Nearest Neighbors (KNN)
- Support Vector Machine (SVM)
- Pohon Keputusan (*Decision Tree*)
- Hutan Acak (*Random Forest*)
- Naive Bayes
- Gradient Boosting
- XGBoost
- LightGBM

Pemilihan akhir didasarkan pada hasil evaluasi, bukan dengan asumsi bahwa satu algoritma akan selalu memberikan kinerja terbaik.

### 4. Evaluasi Model
Kinerja model dievaluasi menggunakan metrik klasifikasi, termasuk:
- Akurasi (*Accuracy*)
- Presisi (*Precision*)
- Recall (*Recall*)
- F1-Score
- Matriks Kebingungan (*Confusion Matrix*)
- Validasi Silang (*Cross-validation*)

Karena kelas target tidak seimbang (*imbalanced*), metrik evaluasi rata-rata makro (*macro-averaged*) dan kinerja per-kelas juga dipertimbangkan.

### 5. Prediksi
Model yang terpilih digunakan untuk memprediksi label kualitas anggur pada dataset pengujian.

Output prediksi mengikuti format pengumpulan yang diperlukan dan hanya berisi dua kolom:

| Id | Quality |
|---|---|
| 1 | Kelas yang diprediksi |
| 2 | Kelas yang diprediksi |

## Hasil Eksperimen

Berdasarkan implementasi notebook saat ini:

| Evaluasi | Hasil |
|---|---:|
| Observasi pelatihan awal | 857 |
| Observasi setelah pembersihan | 781 |
| Observasi holdout (data cadangan) | 157 |
| Observasi pengujian | 286 |
| Jumlah fitur | 11 |
| Model kandidat | 19 |
| Model yang dipilih | SVM dengan Kernel RBF |
| Akurasi Validasi Silang 5-Fold | 59,95% |
| Akurasi Holdout | 56,69% |

SVM dengan Kernel RBF dipilih berdasarkan perbandingan model yang dilakukan di dalam notebook.

Hasil ini menunjukkan bahwa klasifikasi kualitas anggur tetap menjadi tantangan, terutama karena variabel target memiliki distribusi kelas yang tidak seimbang (*imbalanced class distribution*).

```text
wine-quality-classification/
│
├── README.md
├── requirements.txt
├── .gitignore
├── Klasifikasi_Kualitas_Anggur.ipynb
└── hasilprediksi_025.csv
```

## Instalasi
Clone repositori ini:
```bash
git clone https://github.com/YOUR-USERNAME/wine-quality-classification.git
```

Arahkan ke direktori proyek:
```
cd wine-quality-classification
```
Instal dependensi yang diperlukan:
```
pip install -r requirements.txt
```
Buka notebook menggunakan Jupyter Notebook atau JupyterLab:
jupyter notebook

Output Prediksi
File prediksi akhir harus mengikuti persyaratan tugas.
Nama file yang diperlukan:
```
hasilprediksi_025.csv
```
Kolom yang diperlukan:
- Id
- Quality

Output hanya boleh berisi dua kolom ini dan mengikuti templat pengumpulan yang telah disediakan.

Keterbatasan:
- Variabel target memiliki distribusi kelas yang tidak seimbang (imbalanced).
- Jumlah observasi yang tersedia untuk beberapa kelas kualitas relatif kecil.
- Kinerja klasifikasi dapat bervariasi tergantung pada model dan strategi prapemrosesan yang digunakan.
- Hasil evaluasi mewakili dataset dan pengaturan eksperimen yang digunakan khusus dalam proyek ini.

