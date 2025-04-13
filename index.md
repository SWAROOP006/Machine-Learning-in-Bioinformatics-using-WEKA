---
Title: Machine Learning In Bioinformatics using WEKA software
---

# Welcome to My Bioinformatics Project

This GitHub Page showcases:

- Feature extraction from protein sequences using R.
- Machine learning analysis on breast cancer dataset using Weka.

👉 Explore the full project below!
# Protein Feature Extraction & Breast Cancer ML Analysis

This repository contains two main components related to bioinformatics and machine learning:

1. **Protein Feature Extraction using R**
2. **Breast Cancer Classification using Machine Learning (Weka)**

---

## 📁 Files Included

- `protein_feature_extraction.R`: R script to extract multiple features from protein sequences using `protr`, `Peptides`, and `foreign` packages. Outputs are saved as `.csv` and `.arff` files for use in machine learning.
- `JYOTHI_SWAROOP_ML_ASSIGNMENT.pdf`: A detailed machine learning assignment using the Breast Cancer Wisconsin dataset analyzed through Weka.

---

## 🔬 1. Protein Feature Extraction (R Script)

The R script performs the following:

- Reads protein sequences from FASTA files.
- Filters valid sequences using `protcheck`.
- Extracts various protein descriptors using:
  - `extractDC`, `extractTC`, `extractCTDC`, `extractCTDD`, `extractCTDT`, `extractAPAAC`, `extractAAC`
- Saves feature matrices for each descriptor in `.csv` format.
- Combines positive/negative classes and exports them as `.arff` files for ML tools like Weka.

**Packages used**:
- `protr`
- `Peptides`
- `foreign`

---

## 🧠 2. Machine Learning Assignment (Weka)

The assignment explores classification models applied to the **Breast Cancer Wisconsin** dataset. The goal is to predict tumor recurrence based on morphological features.

### 🧪 Models Evaluated:
- **IBk (k-Nearest Neighbors)** – Best performer
- **Naïve Bayes**
- **Support Vector Machine (SMO)**

### 🔍 Key Findings:
| Model | Accuracy | Recall | F1-Score | ROC AUC | PRC AUC |
|-------|----------|--------|----------|---------|---------|
| IBk (k=1) | 72.37% | 0.724 | 0.697 | 0.628 | 0.686 |
| Naïve Bayes | 71.67% | 0.717 | 0.708 | 0.701 | 0.741 |
| SMO (SVM) | 69.58% | 0.696 | 0.600 | 0.509 | 0.586 |

- **Best overall**: IBk (k-NN), especially for recall—critical in medical diagnosis.
- **Naïve Bayes** handled noise and missing values well.
- **SVM** underperformed due to data characteristics and model assumptions.

---

## 🧬 Biological Relevance

- Machine learning helps predict recurrence risk, aiding early diagnosis and personalized treatment.
- Protein features extracted can be applied to similar predictive modeling tasks.
- Bioinformatics + ML provides a powerful toolset for computational biology.

---

## ✅ How to Use

### For R Script:
1. Ensure required R packages are installed: `protr`, `Peptides`, `foreign`.
2. Update file paths in the script if needed.
3. Run the script to generate `.csv` and `.arff` files for your sequences.

### For Weka Assignment:
1. Open Weka GUI.
2. Load the `.arff` files.
3. Apply classifiers under the "Classify" tab.
4. Evaluate results using 10-fold cross-validation.

---

## 📌 Author
**Jyothi Swaroop C**  
Machine Learning in Bioinformatics – Assignment & R-based Feature Extraction

---

## 📬 Contact
Feel free to reach out if you have any questions or want to collaborate!

