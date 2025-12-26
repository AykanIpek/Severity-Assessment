🧬 inflammation-severity-assessment

This project applies machine learning techniques to assess inflammation severity from histopathology-derived cellular features. The study focuses on both multi-class severity score prediction and binary inflammation classification, demonstrating a complete medical machine learning pipeline including preprocessing, exploratory data analysis (EDA), imbalance handling, feature selection, model optimisation, and interpretability.

---

📂 Project Structure

📁 inflammation-severity-assessment  
│── data/                # Clinical and histopathology feature datasets  
│── notebooks/           # Jupyter notebooks for EDA, modelling, and evaluation  
│── src/                 # Python scripts for preprocessing, training, and validation  
│── results/             # Model outputs, plots, metrics, and figures  
│── README.md            # Project documentation  

---

🔑 Key Stages

### 1. Data Processing
- Cleaned and structured histopathology feature data  
- Handled missing values using KNN-based imputation  
- Standardised numerical features  
- Defined multi-class and binary target variables  
- Preserved patient identifiers for grouped validation  

---

### 2. Exploratory Data Analysis (EDA)
- Analysed feature distributions and data types  
- Examined severity score distribution and class imbalance  
- Investigated correlations between tissue-region features  
- Validated the need for grouped cross-validation and imbalance-aware learning  

---

### 3. Modelling & Prediction

#### Task 1 – Severity Score Prediction
- Multi-class classification (severity scores: 0–5)  
- Models evaluated:
  - Logistic Regression  
  - Decision Tree  
  - Random Forest  
  - XGBoost  
  - k-Nearest Neighbours  
  - AdaBoost  

#### Task 2 – Binary Inflammation Classification
- Binary target definition:
  - Score < 3 → No inflammation  
  - Score ≥ 3 → Inflammation present  
- Cost-sensitive learning applied to address class imbalance  

---

### 4. Cross-Validation Strategy
- Applied **5-fold GroupKFold cross-validation**
- Grouping based on patient IDs to prevent data leakage
- Ensured patient-level separation between training and test sets  

---

### 5. Handling Class Imbalance
- Synthetic oversampling methods (e.g. SMOTE) were not used due to:
  - Risk of patient-level information leakage  
  - Generation of clinically unrealistic synthetic samples  
- Instead, imbalance was handled using:
  - `class_weight='balanced'`  
  - `scale_pos_weight` for XGBoost  

---

### 6. Feature Selection
- Sequential Forward Feature Selection (SFS)  
- Top 10 most informative features selected using Random Forest  
- Models retrained using reduced feature sets to assess robustness  

---

### 7. Hyperparameter Tuning
- Applied **HalvingRandomSearchCV**  
- Nested within GroupKFold cross-validation  
- Optimised using balanced accuracy  

---

### 8. Model Interpretability
- SHAP (SHapley Additive exPlanations) used for global feature importance  
- PCA-based visualisation applied to inspect model decision boundaries  
- Improved transparency and clinical interpretability  

---

⚙️ Tools & Libraries

- Programming Language: Python  
- Data Handling: Pandas, NumPy  
- Visualisation: Matplotlib, Seaborn  
- Machine Learning: Scikit-learn, XGBoost  
- Imbalanced Learning: Imbalanced-learn  
- Interpretability: SHAP  

---

🚀 How to Run

Clone the repository:

git clone https://github.com/AykanIpek/Severity-Assessment.git  
cd Severity-Assessment  

Install dependencies:

pip install -r requirements.txt  

Run the notebook or scripts:

jupyter notebook notebooks/Inflammation Severity Assessment.ipynb  

---

📊 Results
- Binary classification achieved more stable performance than multi-class prediction  
- Ensemble models with imbalance-aware learning performed best  
- Feature selection improved interpretability with minimal performance loss  

---

📌 Future Improvements
- Investigate ordinal classification for severity scores  
- Explore deep learning approaches for feature representation  
- Validate models on external clinical datasets  
- Deploy a clinical decision-support prototype  

---

📧 Author: Aykan Ipek  
🎓 London South Bank University
