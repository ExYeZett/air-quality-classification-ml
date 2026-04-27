# Panduan Kontribusi

Terima kasih telah tertarik untuk berkontribusi pada project Air Quality Classification! Dokumen ini menjelaskan cara berkontribusi dengan efektif.

## Code of Conduct

Proyek ini menerima kontribusi dari semua orang. Kami berkomitmen untuk menyediakan lingkungan yang ramah dan menghormati semua kontributor.

## Cara Berkontribusi

### 1. Report Issues
Jika Anda menemukan bug atau masalah:

1. **Cek Issue yang Sudah Ada**
   - Cek apakah issue sudah dilaporkan sebelumnya

2. **Buat Issue Baru**
   - Judul yang jelas dan deskriptif
   - Deskripsi detail tentang issue
   - Steps untuk reproduce
   - Expected behavior vs actual behavior
   - Screenshots atau error messages jika relevan
   - Versi Python dan library yang digunakan

### 2. Suggest Improvements
Untuk saran fitur atau improvement:

1. Jelaskan use case Anda
2. Jelaskan solusi yang Anda usulkan
3. Jelaskan alternatif yang Anda pertimbangkan
4. Jelaskan dampak potensial

### 3. Pull Request

#### Setup Development Environment

```bash
# Clone repository
git clone https://github.com/username/air-quality-classification.git
cd air-quality-classification

# Buat virtual environment
python -m venv venv

# Activate virtual environment
# Windows:
venv\Scripts\activate
# Mac/Linux:
source venv/bin/activate

# Install dependencies
pip install -r requirements.txt

# Install dev dependencies (optional)
pip install pytest jupyter-notebook
```

#### Membuat Pull Request

1. **Create a Feature Branch**
   ```bash
   git checkout -b feature/nama-fitur
   # atau
   git checkout -b fix/nama-bug-fix
   ```

2. **Make Your Changes**
   - Ikuti coding style yang konsisten
   - Tambahkan comments untuk kode yang kompleks
   - Update dokumentasi jika diperlukan

3. **Test Your Changes**
   - Jalankan notebook dan pastikan tidak ada errors
   - Test dengan different parameter combinations
   - Pastikan output sesuai harapan

4. **Commit Your Changes**
   ```bash
   git add .
   git commit -m "Deskripsi singkat tentang perubahan"
   # Contoh:
   git commit -m "Add data validation in preprocessing step"
   git commit -m "Fix: Correct confusion matrix labels"
   git commit -m "Docs: Update README with new results"
   ```

5. **Push to Your Fork**
   ```bash
   git push origin feature/nama-fitur
   ```

6. **Create Pull Request**
   - Berikan judul yang jelas
   - Jelaskan perubahan yang dibuat
   - Reference any related issues
   - Berikan context yang cukup untuk reviewer

#### Commit Message Guidelines

Gunakan format ini untuk commit messages:

```
<type>: <subject>

<body>

<footer>
```

**Types:**
- `feat`: Fitur baru
- `fix`: Bug fix
- `docs`: Dokumentasi
- `style`: Formatting, style changes
- `refactor`: Code refactoring
- `test`: Test-related changes
- `chore`: Build, dependencies, atau maintenance

**Subject:**
- Gunakan imperative mood ("add" bukan "added")
- Jangan capitalize subject
- Tidak ada periode di akhir
- Maksimal 50 karakter

**Contoh:**
```
feat: add hyperparameter tuning for naive bayes

Add GridSearchCV with StratifiedKFold for finding optimal
var_smoothing parameter for Gaussian Naive Bayes model.

Closes #42
```

## Coding Style Guide

### Python Code Style
- Follow PEP 8 guidelines
- Use 4 spaces for indentation
- Max line length: 100 characters
- Use meaningful variable names
- Add docstrings untuk functions dan classes

### Notebook Style
- Organize code into logical cells
- Add markdown cells untuk explanations
- Use clear section headers (##, ###)
- Avoid very long cells (break them up)
- Clear variable names
- Include comments untuk complex logic

### Variable Naming
```python
# Good
feature_scaler = StandardScaler()
best_k_value = 10
accuracy_scores = []

# Bad
fs = StandardScaler()
bk = 10
scores = []
```

## Documentation Standards

### Docstring Format
```python
def train_knn_model(X_train, y_train, n_neighbors=5):
    """
    Train a K-Nearest Neighbors classifier.
    
    Parameters
    ----------
    X_train : array-like, shape (n_samples, n_features)
        Training feature matrix
    y_train : array-like, shape (n_samples,)
        Training target vector
    n_neighbors : int, default=5
        Number of neighbors to use
        
    Returns
    -------
    model : KNeighborsClassifier
        Trained KNN model
        
    Examples
    --------
    >>> knn = train_knn_model(X_train, y_train, n_neighbors=10)
    >>> predictions = knn.predict(X_test)
    """
    model = KNeighborsClassifier(n_neighbors=n_neighbors)
    model.fit(X_train, y_train)
    return model
```

## Testing

### Sebelum Submit PR:
1. Test dengan different hyperparameters
2. Verify reproducibility dengan random_state yang fixed
3. Check untuk edge cases
4. Validate output format dan types

### Running Tests
```bash
# Run notebook cells
jupyter nbconvert --to notebook --execute Air_Quality_Classification_KNN_NaiveBayes.ipynb
```

## Review Process

1. **Automated Checks**
   - Code linting
   - Notebook execution

2. **Manual Review**
   - Maintainer akan review code
   - Suggestions atau questions akan diberikan
   - Iterative improvements

3. **Approval & Merge**
   - Setelah approval, PR akan di-merge

## Improvement Ideas

Kami terbuka untuk improvements dalam areas berikut:

### Code Improvements
- [ ] Refactor preprocessing pipeline
- [ ] Add more visualization options
- [ ] Implement additional algorithms
- [ ] Add cross-validation strategies
- [ ] Performance optimizations

### Documentation
- [ ] Translate to English
- [ ] Add video tutorials
- [ ] Create example notebooks
- [ ] Improve inline comments
- [ ] Add troubleshooting guide

### Features
- [ ] Add real-time prediction
- [ ] Create API wrapper
- [ ] Add model serialization
- [ ] Create web dashboard
- [ ] Add comparison with deep learning models

### Testing
- [ ] Add unit tests
- [ ] Add integration tests
- [ ] Add performance benchmarks
- [ ] Add edge case tests

## Getting Help

- **Questions**: Buka Discussion atau Issue
- **Bug Reports**: Submit Issue dengan detail
- **Feature Requests**: Buat Feature Request Issue
- **Documentation**: Improve README atau add new docs

## Project Structure

```
project/
├── README.md              # Main documentation
├── CONTRIBUTING.md        # This file
├── LICENSE               # MIT License
├── requirements.txt      # Dependencies
├── .gitignore           # Git ignore rules
│
├── Air_Quality_Classification_KNN_NaiveBayes.ipynb  # Main notebook
├── data/                # Dataset folder
├── results/             # Output results
└── models/              # Saved models
```

## Questions?

- Check existing Issues dan Discussions
- Review README.md untuk context
- Hubungi maintainer jika diperlukan

---

**Terima kasih atas kontribusi Anda!** 🎉

Kontribusi Anda membantu membuat project ini lebih baik untuk semua orang.

