# Log-Based Anomaly Detection Framework

This project demonstrates a simple pipeline for detecting Denial-of-Service (DoS) attacks using a combination of clustering and classification techniques applied to simulated network log data.

## 📂 Structure
(Structure.png)

log-anomaly-detection/
├── data/
│ └── log_sample.csv # Sample log dataset (1000 records)
├── notebooks/
│ └── log_anomaly_detection_notebook.ipynb 
| └── log_anomaly_detection_v2_SMOTE.ipynb # Full end-to-end experiment
├── models/ # (Optional) Save trained models
├── results/ # (Optional) Save evaluation outputs
└── README.md


## 🚀 How it Works

1. **Load and Preprocess Logs**:
   - Standardize `.log` data into structured `.csv`
   - Encode categorical fields (e.g., protocol, flags)
   - Normalize features

2. **Unsupervised Clustering (K-Means)**:
   - Detect anomalies without labels
   - Flag outliers as potentially malicious

3. **Supervised Classification (Random Forest)**:
   - Train model on labeled samples
   - Evaluate using metrics: Accuracy, Precision, Recall, ROC-AUC

4. **Output**:
   - Confusion Matrix, Classification Report, ROC Score

## 📊 Evaluation Metrics

- Accuracy
- Precision / Recall / F1 Score
- ROC AUC
- Confusion Matrix

## Pipeline Diagram

┌──────────────┐        ┌───────────────────────────┐
│ Raw Logs     │──────▶│ Preprocessing + Feature    │
│ (.log / CSV) │        │ Selection (CFS, RFE)      │
└──────────────┘        └─────────────┬─────────────┘
                                      │
                                      ▼
                         ┌────────────┴────────────┐
                         │  Clustering (KMeans,    │
                         │     DBSCAN - Outliers)  │
                         └────────────┬────────────┘
                                      │
                                      ▼
                         ┌────────────┴────────────┐
                         │  Classification (RF,    │
                         │     SVM, DT, etc.)      │
                         └────────────┬────────────┘
                                      │
                                      ▼
                         ┌────────────┴────────────┐
                         │  Evaluation (F1, AUC,   │
                         │     Precision, Recall)  │
                         └─────────────────────────┘

## ⚙️ Requirements

Install dependencies with:

```bash
pip install pandas numpy scikit-learn matplotlib seaborn jupyter

