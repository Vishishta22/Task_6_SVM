# Task_7_SVM

#  Breast Cancer Classification using SVM

This project uses Support Vector Machines (SVM) to classify breast tumors as **malignant** or **benign** based on a variety of features derived from digitized images of fine needle aspirates (FNAs) of breast masses.

---

##  Dataset

- **Source**: `breast_cancer.csv` (based on the Wisconsin Breast Cancer Dataset)
- **Rows**: 569 instances
- **Target**: `diagnosis` column  
  - `M` → Malignant (encoded as 0)  
  - `B` → Benign (encoded as 1)
- **Features**: 30 numeric predictors like `radius_mean`, `texture_mean`, etc.

---

##  Project Tasks

### 1. Data Preprocessing
- Removed irrelevant columns like `id` and unnamed columns.
- Encoded diagnosis labels.
- Standardized feature values using `StandardScaler`.

### 2. Dimensionality Reduction (PCA)
- Applied PCA to reduce 30 features to 2 principal components for visualization.
- Plotted SVM decision boundaries in 2D space.

SVM Decision Boundary (PCA-reduced)

> The red and blue regions show the decision boundaries created by an RBF SVM classifier. The classes are reasonably well separated in PCA space, with some overlap. The PCA plot shows clear class separability with minimal overlap, validating the use of a non-linear kernel.

---

### 3. SVM Model Training & Evaluation

#### Linear SVM
- **Accuracy**: `0.9561`
- **Confusion Matrix**:
- [[41 2]
- [ 3 68]]


#### RBF SVM
- **Accuracy**: `0.9737`
- **Confusion Matrix**:
- [[41 2]
- [ 1 70]]


> Interpretation:

- The RBF kernel slightly outperforms the linear kernel.
- Misclassifications are minimal.
- RBF is better at handling non-linear boundaries.

---

### 4. Hyperparameter Tuning (GridSearchCV)

- **Parameters Tuned**: `C`, `gamma`
- **Best Params**: `{'C': 10, 'gamma': 0.01, 'kernel': 'rbf'}`
- **Best Score**: `0.9825`

> Interpretation:

- Tuning C and gamma significantly improved the model’s performance.
- The model generalizes well with fewer false positives and negatives.

---

### 5. Cross-Validation Results

- **Cross-validation Scores**: `[0.9737, 0.9737, 0.9825, 0.9737, 0.9911]`
- **Mean Accuracy**: `0.9789`

> Interpretation:

- The model is consistently accurate across different data splits.
- High mean CV accuracy confirms model robustness and reliability.

---

##  Conclusion

- RBF SVM with optimized parameters achieved the highest accuracy and lowest error rate.
- PCA visualization helped confirm the effectiveness of non-linear separation.
- The model is highly suitable for supporting medical diagnosis in real-world scenarios.
