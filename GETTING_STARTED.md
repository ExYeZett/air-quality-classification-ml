# 🚀 Getting Started Guide

Panduan singkat untuk menjalankan Air Quality Classification project Anda dengan cepat.

## 📋 Prerequisites

Pastikan Anda sudah menginstall:
- **Python 3.7+** ([download](https://www.python.org/downloads/))
- **pip** (package manager, biasanya sudah included dengan Python)
- **Git** (untuk clone repository) - [download](https://git-scm.com/)

Cek instalasi Anda:
```bash
python --version
pip --version
git --version
```

---

## ⚡ Quick Start (5 Menit)

### Step 1: Clone atau Download Repository
```bash
# Clone dari GitHub
git clone https://github.com/username/air-quality-classification.git
cd air-quality-classification

# ATAU download sebagai ZIP dan extract ke folder
```

### Step 2: Setup Virtual Environment
```bash
# Create virtual environment
python -m venv venv

# Activate virtual environment
# Windows:
venv\Scripts\activate

# macOS/Linux:
source venv/bin/activate
```

### Step 3: Install Dependencies
```bash
pip install -r requirements.txt
```

### Step 4: Launch Jupyter Notebook
```bash
jupyter notebook
```

Jupyter akan terbuka di browser. Click file `Air_Quality_Classification_KNN_NaiveBayes.ipynb`

### Step 5: Run the Notebook
- Klik menu **Cell** → **Run All** untuk menjalankan semua cells
- Atau jalankan cell per cell dengan **Shift + Enter**
- Tunggu sampai selesai dan lihat hasil output

---

## 📁 File Structure

```
air-quality-classification/
├── README.md                              # Dokumentasi lengkap
├── GETTING_STARTED.md                     # Panduan ini
├── CONTRIBUTING.md                        # Cara berkontribusi
├── CHANGELOG.md                           # History perubahan
├── LICENSE                                # MIT License
├── requirements.txt                       # Dependencies
├── .gitignore                            # Git ignore rules
│
├── Air_Quality_Classification_KNN_NaiveBayes.ipynb  # Main notebook (JALANKAN INI!)
│
├── data/                                  # Folder data
│   └── air_quality_data.csv              # Dataset (optional)
│
├── results/                               # Output folder (created after running)
│   ├── confusion_matrices/
│   ├── model_comparison.png
│   └── evaluation_metrics.txt
│
└── models/                                # Saved models folder (optional)
    ├── knn_model.pkl
    └── naive_bayes_model.pkl
```

---

## 🎯 What You'll Learn

Setelah menjalankan notebook ini, Anda akan memahami:

✅ **Data Science Workflow**
- Data loading dan exploration
- Preprocessing dan feature scaling
- Train-test split
- Handling imbalanced data

✅ **Machine Learning Models**
- K-Nearest Neighbors (KNN) algorithm
- Gaussian Naive Bayes algorithm
- How to tune hyperparameters
- Model evaluation dan comparison

✅ **Python Libraries**
- pandas untuk data manipulation
- scikit-learn untuk ML algorithms
- matplotlib & seaborn untuk visualization
- numpy untuk numerical computing

---

## 📊 What the Notebook Does

| Step | Deskripsi | Output |
|------|-----------|--------|
| 1 | **Load Libraries** | Import semua library yang diperlukan |
| 2 | **Load Data** | Baca dataset air quality |
| 3 | **Explore Data** | Lihat statistics dan distribution data |
| 4 | **Preprocess** | Clean, encode, scale data |
| 5 | **Undersample** | Handle imbalanced classes |
| 6 | **Train KNN** | Build dan train KNN model |
| 7 | **Evaluate KNN** | Lihat performa KNN |
| 8 | **Train Naive Bayes** | Build dan train Naive Bayes model |
| 9 | **Evaluate NB** | Lihat performa Naive Bayes |
| 10 | **Compare Models** | Bandingkan kedua model |

---

## 🔍 Understanding the Results

### Setelah Running Notebook, Anda akan Melihat:

#### 1. **Data Overview**
```
Dataset shape: (n_samples, n_features)
Class distribution: Good, Moderate, Poor, Hazardous
Missing values: None
```

#### 2. **Confusion Matrices**
Visual representation yang menunjukkan:
- True Positives (diagonal)
- False Positives (sebelah kanan)
- False Negatives (bawah)
- True Negatives (kiri)

#### 3. **Accuracy Scores**
```
KNN Accuracy: 93.00% ✅
Naive Bayes Accuracy: 91.00% ✅
```

#### 4. **Model Comparison**
Table yang membandingkan:
- Test Accuracy
- Balanced Accuracy
- Best Parameters
- Training Speed
- Prediction Speed

---

## ⚙️ Customization Tips

### Jika Ingin Mengubah Parameter:

#### 1. Ubah K Value untuk KNN
```python
# Di cell KNN model building
knn_model = KNeighborsClassifier(n_neighbors=15)  # Ubah dari 10 ke 15
```

#### 2. Ubah Train-Test Split
```python
# Di cell preprocessing
X_train, X_test, y_train, y_test = train_test_split(
    X_undersampled, y_undersampled, test_size=0.3, random_state=42  # Ubah dari 0.2 ke 0.3
)
```

#### 3. Gunakan Dataset Lain
```python
# Di cell data loading
df = pd.read_csv('path/to/your/dataset.csv')
```

---

## 🐛 Troubleshooting

### ❌ Error: `ModuleNotFoundError: No module named 'pandas'`
```bash
# Solution: Install missing library
pip install pandas
```

### ❌ Error: `NameError: name 'df' is not defined`
```
✅ Solution: Run data loading cell dulu (paling awal)
Pastikan urutan cells dijalankan dari atas ke bawah
```

### ❌ Error: `FileNotFoundError: 'air_quality_data.csv' not found`
```
✅ Solution: Pastikan file dataset ada di folder yang sama atau ubah path
Atau gunakan dataset bawaan jika tersedia
```

### ❌ Slow Performance atau Memory Issues
```bash
# Solution: Reduce dataset size atau upgrade RAM
# Atau jalankan hanya cell tertentu yang Anda butuhkan
```

---

## 📚 Learning Resources

### Inside This Repository
- **README.md** - Dokumentasi lengkap (baca ini!)
- **CONTRIBUTING.md** - Cara berkontribusi ke project
- **Notebook comments** - Penjelasan detail di setiap cell

### External Resources
- [scikit-learn Documentation](https://scikit-learn.org/)
- [Pandas Tutorial](https://pandas.pydata.org/docs/)
- [Matplotlib Guide](https://matplotlib.org/)
- [YouTube ML Tutorials](https://youtube.com)

### Books (Optional)
- "Introduction to Statistical Learning" by James et al.
- "Hands-On Machine Learning" by Aurélien Géron
- "Python Machine Learning" by Sebastian Raschka

---

## 💡 Next Steps

Setelah familiar dengan project ini:

### 1. **Explore the Code**
- Pahami setiap cell di notebook
- Modify parameters dan lihat hasilnya
- Try dengan dataset berbeda

### 2. **Enhance the Project**
- Add new features
- Try ensemble methods
- Improve accuracy
- Lihat file CONTRIBUTING.md

### 3. **Deploy the Model**
- Save model menggunakan pickle/joblib
- Create API wrapper
- Build web dashboard
- Lihat CHANGELOG untuk future plans

### 4. **Share Knowledge**
- Document your findings
- Contribute improvements
- Help other learners
- Star repository jika helpful! ⭐

---

## 🎓 Key Concepts to Understand

Sebelum jalankan notebook, pelajari concepts ini:

### 1. **Classification**
Proses memprediksi kategori/label dari data baru
- Input: Features (X)
- Output: Category/Label (y)
- Contoh: Predict air quality class

### 2. **Supervised Learning**
Training model dengan labeled data (feature + target)
- Pro: Akurat jika data good
- Con: Membutuhkan labeled data

### 3. **Train-Test Split**
Membagi data menjadi training (buat model) dan testing (evaluate)
- Typical split: 80% train, 20% test
- Tujuan: Evaluate model pada unseen data

### 4. **Imbalanced Data**
Ketika ada ketidakseimbangan jumlah samples di setiap class
- Problem: Model bias ke majority class
- Solution: Undersampling, oversampling, atau class weights

### 5. **Hyperparameter Tuning**
Optimize model performance dengan mengubah parameters
- GridSearchCV: Try semua kombinasi parameters
- Cross-validation: More reliable performance estimate

---

## 📞 Support & Help

### Jika Ada Masalah:
1. **Baca README.md** - Mungkin sudah ada jawaban
2. **Check GitHub Issues** - Lihat issue yang sudah ada
3. **Create New Issue** - Jika belum ketemu solusi
4. **Read Error Messages** - Biasanya error message sangat informatif!

### Contributing:
Jika Anda menemukan bug atau improvement, lihat **CONTRIBUTING.md**

---

## ✅ Checklist

Pastikan sudah completed sebelum jalankan:

- [ ] Python 3.7+ installed
- [ ] Git installed
- [ ] Virtual environment created
- [ ] Dependencies installed (`pip install -r requirements.txt`)
- [ ] Jupyter notebook installed
- [ ] Data file tersedia (jika diperlukan)
- [ ] Menggunakan correct notebook file

---

## 🎉 You're Ready!

Anda sudah siap menjalankan project ini! 

**Next: Buka terminal, navigate ke folder project, dan jalankan `jupyter notebook`**

---

**Happy Learning! 🚀**

Jika project ini membantu Anda, please consider:
- ⭐ Star repository
- 🔀 Fork untuk customize
- 👥 Share dengan teman
- 💬 Give feedback

**Questions?** Lihat README.md atau buat Issue di GitHub.

