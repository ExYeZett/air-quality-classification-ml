# Changelog

Semua perubahan penting dalam project ini akan didokumentasikan dalam file ini.

Format ini berdasarkan [Keep a Changelog](https://keepachangelog.com/en/1.0.0/), dan project ini mengikuti [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.0.0] - 2026-04-27

### Added
- **Initial Release** dengan implementasi lengkap classification model
- K-Nearest Neighbors (KNN) dengan hyperparameter tuning
  - Best parameters: n_neighbors=10, weights=distance, metric=manhattan
  - Test Accuracy: 93.00%
  - Balanced Accuracy: 89.67%
  
- Gaussian Naive Bayes dengan hyperparameter tuning
  - Best parameters: var_smoothing=1e-10
  - Test Accuracy: 91.00%
  - Balanced Accuracy: 88.65%

- Data Preprocessing Pipeline
  - Label encoding untuk target variable
  - Train-test split dengan stratification (80:20)
  - Random undersampling untuk handling imbalanced data
  - StandardScaler untuk feature normalization

- Model Evaluation
  - Confusion matrices visualization
  - Classification reports dengan precision, recall, F1-score
  - Cross-validation dengan StratifiedKFold
  - GridSearchCV untuk hyperparameter tuning

- Dokumentasi
  - Comprehensive README.md dengan teori dan metodologi
  - CONTRIBUTING.md untuk guidelines kontribusi
  - LICENSE file (MIT License)
  - requirements.txt untuk dependencies
  - .gitignore untuk version control
  - CHANGELOG.md ini

### Features
- Jupyter notebook yang lengkap dan well-documented
- 39 cells dengan kombinasi markdown dan Python code
- Data exploration dan visualization
- Model comparison dan analysis
- Clear output dan interpretable results

### Documentation
- Complete mathematical background untuk KNN dan Naive Bayes
- Step-by-step explanation of preprocessing pipeline
- Detailed methodology dan hasil analisis
- Troubleshooting guide
- Installation instructions

---

## Planning untuk Versions Mendatang

### [1.1.0] - Planned
- [ ] Add feature importance analysis
- [ ] Add SHAP values untuk model interpretability
- [ ] Add ROC-AUC curve analysis
- [ ] Implement ensemble methods (Voting, Stacking)
- [ ] Add deep learning comparison
- [ ] Performance optimization

### [1.2.0] - Planned
- [ ] Web API wrapper menggunakan Flask/FastAPI
- [ ] Create prediction pipeline untuk production
- [ ] Add model serialization (joblib/pickle)
- [ ] Add batch prediction capability
- [ ] Create web dashboard menggunakan Streamlit

### [2.0.0] - Planned
- [ ] Multi-language support (Indonesia, English)
- [ ] Real-time prediction system
- [ ] Integration dengan monitoring system
- [ ] Advanced visualization dashboard
- [ ] Mobile app integration

---

## Notes untuk Contributors

Ketika menambahkan fitur baru atau improvements:
1. Update CHANGELOG.md dengan kategori yang sesuai (Added, Changed, Fixed, Removed, Deprecated)
2. Gunakan format:
   ```
   - [Brief description] (related issue/PR if applicable)
   ```
3. Keep entries concise dan user-focused
4. Date akan ditambahkan saat release

---

## Release History

### Version 1.0.0
- **Released**: 2026-04-27
- **Status**: ✅ Stable
- **Focus**: Initial implementation dengan dua classification models

---

## Maintenance Status

- **Current Version**: 1.0.0
- **Actively Maintained**: ✅ Yes
- **Latest Update**: 2026-04-27
- **Next Planned Release**: TBD

---

## Reporting Changes

Jika Anda menemukan bugs atau ingin suggest changes:
1. Create Issue dengan label yang sesuai
2. PR akan direview dan merged jika appropriate
3. Changes akan di-document dalam CHANGELOG
4. New version akan dirilis sesuai Semantic Versioning

---

**Last Updated**: 2026-04-27
