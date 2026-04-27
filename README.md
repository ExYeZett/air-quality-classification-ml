# Klasifikasi Tingkat Kualitas Udara Menggunakan Metode KNN & Naive Bayes

## 🎯 Tentang Project

Project ini merupakan implementasi machine learning untuk **klasifikasi tingkat kualitas udara** menggunakan dua algoritma utama:
- **K-Nearest Neighbors (KNN)** 
- **Gaussian Naive Bayes**

Tujuan project adalah mengembangkan model prediktif yang akurat untuk mengklasifikasikan tingkat kualitas udara ke dalam 4 kategori: **Good (Baik)**, **Moderate (Sedang)**, **Poor (Buruk)**, dan **Hazardous (Berbahaya)**.

---

## 👥 Tim Pengembang

| No. | Nama | NIM |
|-----|------|-----|
| 1 | Satrio Aji Nugroho | 103062300080 |
| 2 | Metha Anastasya | 103062300083 |
| 3 | Muhammad Rizky Hadi Prawiro | 103062300090 |

---

## 🌍 Latar Belakang Masalah

Polusi udara merupakan masalah lingkungan yang semakin mendesak di banyak wilayah dunia, termasuk di kawasan Asia Tenggara. Berdasarkan laporan dari **IQAir tahun 2022**, beberapa kota di Asia Tenggara seperti:
- Jakarta
- Hanoi
- Nan

Sering kali tercatat memiliki **kualitas udara yang sangat buruk**, yang dapat berdampak negatif pada:
- ❌ Kesehatan masyarakat
- ❌ Ekosistem lingkungan
- ❌ Produktivitas ekonomi

### Pentingnya Penelitian Ini

Mengingat dampaknya yang luas, penting untuk:
1. **Memantau** kualitas udara secara berkelanjutan
2. **Mengklasifikasikan** tingkat kualitas udara dengan akurat
3. **Merancang** kebijakan pengendalian polusi yang lebih efektif

---

## 📊 Dataset

### Sumber Data
Dataset yang digunakan berisi **parameter kualitas udara** dari berbagai stasiun monitoring.

### Fitur Dataset
Dataset terdiri dari fitur-fitur berikut yang relevan dengan kualitas udara:
- **PM2.5**: Partikel halus (micrograms/m³)
- **PM10**: Partikel kasar (micrograms/m³)
- **NO₂**: Nitrogen Dioksida (ppb)
- **SO₂**: Sulfur Dioksida (ppb)
- **O₃**: Ozon (ppb)
- **CO**: Karbon Monoksida (ppm)
- Dan parameter-parameter kualitas udara lainnya

### Target Variable
**Air Quality** dikategorikan ke dalam 4 kelas:
- 🟢 **Good**: Kualitas udara baik
- 🟡 **Moderate**: Kualitas udara sedang
- 🟠 **Poor**: Kualitas udara buruk
- 🔴 **Hazardous**: Kualitas udara berbahaya

### Penanganan Imbalanced Data
- **Teknik**: Random Undersampling
- **Hasil**: Setiap kelas seimbang dengan 400 sampel untuk training
- **Tujuan**: Meningkatkan performa model pada minority class

---

## 🔧 Metodologi

### 1. Data Preprocessing
```
Data Raw
    ↓
Encoding Target Variable
    ↓
Pemisahan Features (X) & Target (y)
    ↓
Train-Test Split (80:20 dengan Stratification)
    ↓
Random Undersampling (Balance Classes)
    ↓
Feature Scaling (StandardScaler)
    ↓
Data Siap untuk Modeling
```

### 2. Tahapan Preprocessing

#### A. Encoding Target Variable
- Mengkonversi label tekstual menjadi numerik menggunakan `LabelEncoder`
- Mapping: Good→0, Moderate→1, Poor→2, Hazardous→3

#### B. Feature-Target Separation
- Memisahkan features (X) dari target variable (y)
- X: semua kolom kecuali 'Air Quality'
- y: kolom 'Air Quality Encoded'

#### C. Train-Test Split
- Rasio: 80% training, 20% testing
- Menggunakan stratification untuk menjaga distribusi kelas

#### D. Undersampling
- Mengidentifikasi kelas minoritas (Hazardous: 400 sampel)
- Mengurangi sampel kelas mayoritas ke 400 sampel per kelas
- Total training set: 1600 sampel (400 × 4 kelas)

#### E. Feature Scaling
- Menggunakan `StandardScaler` untuk normalisasi
- Sangat penting untuk KNN karena menggunakan jarak euclidean

---

## 🤖 Model Machine Learning

### Model 1: K-Nearest Neighbors (KNN)

#### Teori Matematika
KNN adalah algoritma **non-parametrik** yang bekerja berdasarkan prinsip:

1. **Euclidean Distance**:
   $$d(p, q) = \sqrt{\sum_{i=1}^{n} (q_i - p_i)^2}$$

2. **Prinsip Kerja**:
   - Hitung jarak ke semua data training
   - Temukan k tetangga terdekat
   - Tentukan kelas mayoritas dari k tetangga
   - Klasifikasikan data baru ke kelas mayoritas

#### Hyperparameter Tuning
- **GridSearchCV** dengan StratifiedKFold (k=5)
- **Scoring**: balanced_accuracy
- **Parameter yang dioptimalkan**:
  - `n_neighbors`: Jumlah tetangga terdekat
  - `weights`: uniform atau distance
  - `metric`: euclidean, manhattan, atau minkowski

#### Hasil Terbaik KNN
```
Best Parameters: 
  - n_neighbors: 10
  - weights: distance
  - metric: manhattan

Cross-Validation Balanced Accuracy: 0.9150 (91.50%)
Test Accuracy: 0.9300 (93.00%)
Test Balanced Accuracy: 0.8967 (89.67%)
```

---

### Model 2: Gaussian Naive Bayes

#### Teori Matematika
Naive Bayes adalah algoritma probabilistik berbasis **Teorema Bayes**:

$$P(C|X) = \frac{P(X|C) \cdot P(C)}{P(X)}$$

Dimana:
- P(C|X): Probabilitas kelas C diberikan fitur X
- P(X|C): Likelihood fitur X diberikan kelas C
- P(C): Prior probability kelas C

#### Asumsi
- Setiap fitur **independen** terhadap fitur lainnya
- Distribusi fitur mengikuti **Gaussian (Normal) Distribution**

#### Hyperparameter Tuning
- **GridSearchCV** dengan StratifiedKFold (k=5)
- **Scoring**: balanced_accuracy
- **Parameter yang dioptimalkan**:
  - `var_smoothing`: Laplace smoothing untuk menghindari zero probability

#### Hasil Terbaik Naive Bayes
```
Best Parameters:
  - var_smoothing: 1e-10

Cross-Validation Balanced Accuracy: 0.8912 (89.12%)
Test Accuracy: 0.9100 (91.00%)
Test Balanced Accuracy: 0.8865 (88.65%)
```

---

## 📈 Hasil dan Perbandingan

### Perbandingan Performa Model

| Metrik | KNN | Naive Bayes |
|--------|-----|------------|
| **Test Accuracy** | 93.00% | 91.00% |
| **Balanced Accuracy** | 89.67% | 88.65% |
| **Best Parameters** | n_neighbors=10, weights=distance, metric=manhattan | var_smoothing=1e-10 |
| **Training Speed** | Lebih lambat | Lebih cepat |
| **Prediksi Speed** | Lambat (lazy learner) | Cepat |

### Confusion Matrix Insights

#### KNN Performance per Kelas
- **Good**: 94% recall
- **Moderate**: 89% recall
- **Poor**: 88% recall
- **Hazardous**: 81% recall

#### Naive Bayes Performance per Kelas
- **Good**: 93% recall
- **Moderate**: 88% recall
- **Poor**: 86% recall
- **Hazardous**: 82% recall

### Temuan Utama

✅ **Keberhasilan**:
- KNN mencapai akurasi 93%, lebih baik dari Naive Bayes (91%)
- Undersampling berhasil meningkatkan recall pada kelas minoritas (Hazardous)
- Balanced accuracy menunjukkan performa yang konsisten di semua kelas

⚠️ **Tantangan**:
- Target akurasi >97% belum tercapai
- Masih ada kebingungan antara kelas Poor dan Hazardous
- Asumsi independensi fitur pada Naive Bayes mungkin tidak sepenuhnya terpenuhi

### Rekomendasi

1. **Untuk Produksi**: Gunakan **KNN** dengan parameters optimal (n_neighbors=10)
2. **Untuk Real-time**: Gunakan **Naive Bayes** (lebih cepat)
3. **Improvement**: Pertimbangkan ensemble methods atau deep learning untuk akurasi >97%

---

## 🚀 Cara Menjalankan

### Prerequisites
- Python 3.7 atau lebih tinggi
- Jupyter Notebook atau Jupyter Lab
- Library: pandas, numpy, scikit-learn, matplotlib, seaborn

### Langkah-langkah

1. **Clone atau Download Repository**
   ```bash
   git clone https://github.com/username/air-quality-classification.git
   cd air-quality-classification
   ```

2. **Install Dependencies**
   ```bash
   pip install -r requirements.txt
   ```

3. **Buka Jupyter Notebook**
   ```bash
   jupyter notebook Air_Quality_Classification_KNN_NaiveBayes.ipynb
   ```

4. **Jalankan Sel-sel Kode**
   - Mulai dari sel pertama (import libraries)
   - Jalankan setiap sel secara berurutan
   - Perhatikan output untuk memastikan tidak ada error

5. **Interpretasi Hasil**
   - Lihat confusion matrix untuk performa detail
   - Bandingkan accuracy dan balanced accuracy
   - Review best parameters untuk setiap model

---

## 📦 Requirement

### Libraries
```
pandas>=1.3.0
numpy>=1.21.0
scikit-learn>=0.24.0
matplotlib>=3.4.0
seaborn>=0.11.0
imbalanced-learn>=0.8.0
jupyter>=1.0.0
ipython>=7.0.0
```

### Versi Python
- Python 3.7, 3.8, 3.9, 3.10, atau 3.11

### Hardware Minimum
- RAM: 4GB
- Storage: 500MB untuk dataset dan output
- Processor: Dual-core CPU

---

## 📁 Struktur Project

```
air-quality-classification/
│
├── README.md                                          # Dokumentasi project
├── requirements.txt                                   # Python dependencies
│
├── Air_Quality_Classification_KNN_NaiveBayes.ipynb   # Main notebook
│
├── data/                                              # Folder dataset
│   └── air_quality_data.csv                          # Dataset mentah
│
├── results/                                           # Output results (opsional)
│   ├── confusion_matrices/                           # Confusion matrix images
│   ├── model_comparison.png                          # Perbandingan model
│   └── evaluation_metrics.txt                        # Metrics detail
│
└── models/                                            # Saved models (opsional)
    ├── knn_model.pkl
    └── naive_bayes_model.pkl
```

---

## 📊 Output Notebook

Notebook akan menghasilkan:

1. **Data Exploration**
   - Dataset overview dan statistics
   - Class distribution visualization

2. **Preprocessing Results**
   - Feature scaling visualization
   - Before-after undersampling comparison

3. **Model Training Metrics**
   - Best hyperparameters untuk setiap model
   - Cross-validation scores

4. **Evaluation Results**
   - Confusion matrices (visual)
   - Classification reports
   - Accuracy dan balanced accuracy scores

5. **Comparison Analysis**
   - Bar charts perbandingan model
   - Performance insights dan rekomendasi

---

## 🎓 Metodologi Pembelajaran

### Concepts Diterapkan
- ✅ Supervised Learning (Classification)
- ✅ Imbalanced Data Handling (Undersampling)
- ✅ Hyperparameter Tuning (GridSearchCV)
- ✅ Cross-Validation (StratifiedKFold)
- ✅ Feature Scaling (StandardScaler)
- ✅ Model Evaluation (Accuracy, Precision, Recall, F1-score)

### Algoritma Utama
- ✅ K-Nearest Neighbors (KNN)
- ✅ Gaussian Naive Bayes

### Tools & Libraries
- ✅ Python 3
- ✅ scikit-learn (Machine Learning)
- ✅ pandas (Data Manipulation)
- ✅ numpy (Numerical Computing)
- ✅ matplotlib & seaborn (Visualization)
- ✅ imbalanced-learn (Class Imbalance)

---

## 💡 Key Insights

### 1. Pentingnya Undersampling
Random undersampling berhasil menyeimbangkan distribusi kelas dan meningkatkan recall pada minority class hingga 81-84%.

### 2. Distance-Weighted KNN
Parameter `weights='distance'` pada KNN memberikan hasil yang lebih baik dibandingkan uniform weights karena memberikan pengaruh lebih besar pada tetangga yang lebih dekat.

### 3. Manhattan Distance
Metrik manhattan (`metric='manhattan'`) untuk KNN lebih efektif dibandingkan euclidean pada dataset ini.

### 4. Trade-offs
- **KNN**: Akurasi tinggi tetapi lambat dalam prediksi (lazy learner)
- **Naive Bayes**: Lebih cepat tetapi akurasi sedikit lebih rendah

### 5. Balanced Accuracy
Menggunakan balanced accuracy lebih informatif dibandingkan simple accuracy pada dataset dengan imbalanced classes.

---

## 🔍 Troubleshooting

### Masalah: `NameError: name 'df' is not defined`
**Solusi**: Pastikan sel data loading sudah dijalankan sebelum menjalankan preprocessing cells.

### Masalah: `ModuleNotFoundError`
**Solusi**: Install required libraries dengan:
```bash
pip install -r requirements.txt
```

### Masalah: Memory Error pada dataset besar
**Solusi**: Kurangi ukuran dataset atau tingkatkan RAM sistem Anda.

### Masalah: Akurasi rendah
**Solusi**: 
- Periksa kualitas data
- Coba dengan preprocessing yang berbeda
- Adjust hyperparameters
- Gunakan ensemble methods

---

## 📚 Referensi & Bacaan Lanjutan

### Dataset Sources
- [UCI Machine Learning Repository](https://archive.ics.uci.edu/)
- [Kaggle Air Quality Datasets](https://www.kaggle.com/)
- [IQAir Database](https://www.iqair.com/)

### Materi Pembelajaran
1. Hastie, T., Tibshirani, R., & Friedman, J. (2009). "The Elements of Statistical Learning"
2. James, G., Witten, D., Hastie, T., & Tibshirani, R. (2013). "An Introduction to Statistical Learning"
3. Scikit-learn Official Documentation: https://scikit-learn.org/

### Algorithm References
- **KNN**: Cover, T. M., & Hart, P. E. (1967). "Nearest neighbor pattern classification"
- **Naive Bayes**: Zhang, H. (2004). "The optimality of Naive Bayes"

---

## 📝 License

Project ini dilisensikan di bawah **MIT License** - lihat file LICENSE untuk detail.

---

## 📧 Kontak & Support

Jika ada pertanyaan atau saran mengenai project ini, silakan:
- 📧 Hubungi tim pengembang
- 🐛 Buat Issue di GitHub
- 💬 Diskusikan di Discussion board

---

## 🙏 Acknowledgments

Terima kasih kepada:
- Semua contributor yang telah membantu project ini
- Dataset providers dan open-source community
- Pandas, scikit-learn, dan matplotlib development teams

---

**Last Updated**: April 2026

