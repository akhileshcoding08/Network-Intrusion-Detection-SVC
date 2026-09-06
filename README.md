# Network Intrusion Detection using SVM

A machine learning project that classifies network traffic as **normal** or **anomalous (attack)** using a Support Vector Machine (SVM) classifier, trained on network connection data (NSL-KDD style dataset).

## 📌 Overview

Network intrusion detection systems (NIDS) monitor network traffic to identify malicious activity or policy violations. This project builds a supervised ML pipeline that:

- Loads and explores a labeled network traffic dataset (~25,000 records, 42 features)
- Cleans and preprocesses the data (encoding, scaling)
- Trains a Support Vector Classifier (SVC) to distinguish `normal` vs `anomaly` traffic
- Evaluates the model using accuracy, F1-score, and a classification report

**Result:** The model achieves **~99% accuracy** and **~99% F1-score** on the held-out test set.

## 📁 Repository Structure

```
├── Network_Data_SVM.ipynb     # Jupyter notebook with full analysis & model code
├── Network_data.csv           # Dataset (network connection records)
├── README.md                  # Project documentation (this file)
└── Network_Intrusion_Detection_Documentation.docx  # Detailed project report
```

## 📊 Dataset

The dataset contains **25,192 network connection records** with **42 columns**, including:

| Type | Example Columns |
|---|---|
| Categorical | `protocol_type`, `service`, `flag` |
| Numerical | `duration`, `src_bytes`, `dst_bytes`, `count`, `srv_count`, `serror_rate`, etc. |
| Target | `class` → `normal` or `anomaly` |

No missing values or duplicate rows are present in the dataset.

## 🛠️ Tech Stack

- **Python 3**
- **Pandas / NumPy** – data manipulation
- **Matplotlib / Seaborn** – data visualization (boxplots, correlation heatmap)
- **Scikit-learn** – preprocessing (`LabelEncoder`, `StandardScaler`), model (`SVC`), evaluation metrics
- **Jupyter Notebook** – development environment

## ⚙️ Installation & Setup

1. **Clone the repository**
   ```bash
   git clone https://github.com/<your-username>/network-intrusion-detection-svm.git
   cd network-intrusion-detection-svm
   ```

2. **Create a virtual environment (recommended)**
   ```bash
   python -m venv venv
   source venv/bin/activate      # On Windows: venv\Scripts\activate
   ```

3. **Install dependencies**
   ```bash
   pip install numpy pandas matplotlib seaborn scikit-learn jupyter
   ```

4. **Launch the notebook**
   ```bash
   jupyter notebook Network_Data_SVM.ipynb
   ```

## 🚀 Usage / Workflow

The notebook follows this pipeline:

1. **Load Data** – Read `Network_data.csv` into a Pandas DataFrame
2. **Explore Data (EDA)** – `df.info()`, `df.describe()`, missing-value & duplicate checks
3. **Visualize Data** – Boxplots for outlier detection, correlation heatmap
4. **Encode Categorical Features** – `LabelEncoder` applied to `protocol_type`, `service`, `flag`, `class`
5. **Feature/Target Split** – Separate `X` (features) and `y` (`class` label)
6. **Feature Scaling** – Standardize features using `StandardScaler`
7. **Train/Test Split** – 80% train / 20% test split (`random_state=42`)
8. **Model Training** – Fit a Support Vector Classifier (`SVC`) on the training data
9. **Prediction & Evaluation** – Predict on test data and evaluate using:
   - Accuracy Score
   - F1 Score
   - Classification Report (precision, recall, f1-score per class)

## 📈 Model Performance

| Metric | Score |
|---|---|
| Accuracy | ~99.05% |
| F1 Score | ~99.10% |
| Precision (both classes) | 0.99 |
| Recall (both classes) | 0.99 |

## 🔮 Future Improvements

- Hyperparameter tuning with `GridSearchCV` for the SVM kernel, `C`, and `gamma`
- Compare SVM against other algorithms (Random Forest, XGBoost, Neural Networks)
- Handle class imbalance with techniques like SMOTE if needed
- Deploy the trained model as a REST API for real-time intrusion detection
- Add cross-validation for more robust performance estimates

## 🙋 Contact

For questions or suggestions, feel free to open an issue or submit a pull request.
