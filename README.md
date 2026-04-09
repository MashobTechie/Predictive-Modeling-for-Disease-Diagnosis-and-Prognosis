 # Predictive Modeling for Disease Diagnosis and Prognosis
### A Stochastic Process Approach | Statistics 300L Project

---

## 📌 Project Overview
This project applies **stochastic process methods** and **classical statistical modeling** to a simulated Electronic Health Records (EHR) dataset of 2,000 patients. The goal is to predict disease diagnosis, model severity progression, and estimate patient outcomes — without relying on black-box machine learning algorithms.

---

## 📂 Files
| File | Description |
|------|-------------|
| `disease_stochastic_analysis.ipynb` | Main Jupyter notebook with full analysis |
| `disease_stochastic_analysis.py` | Plain Python version of the same analysis |
| `disease_diagnosis.csv` | Dataset (2,000 simulated patient records) |

---

## 📊 Dataset Description
The dataset contains simulated medical records with the following features:

| Column | Description |
|--------|-------------|
| `Patient_ID` | Unique patient identifier |
| `Age` | Patient age (years) |
| `Gender` | Male / Female |
| `Symptom_1/2/3` | Three reported symptoms per patient |
| `Heart_Rate_bpm` | Heart rate in beats per minute |
| `Body_Temperature_C` | Body temperature in Celsius |
| `Blood_Pressure_mmHg` | Systolic/Diastolic blood pressure |
| `Oxygen_Saturation_%` | Blood oxygen saturation level |
| `Diagnosis` | Diagnosed condition (Flu, Cold, Pneumonia, Bronchitis, Healthy) |
| `Severity` | Condition severity (Mild, Moderate, Severe) |
| `Treatment_Plan` | Suggested treatment based on severity |

---

## 🔬 Analysis Sections

### 1. Data Loading & Preprocessing
- Load the CSV dataset
- Parse `Blood_Pressure_mmHg` (string format `"120/80"`) into separate `Systolic_BP` and `Diastolic_BP` numeric columns
- Inspect data types, missing values, and distributions

### 2. Exploratory Data Analysis (EDA)
- Histograms of all sensor readings with mean markers
- Bar charts of diagnosis and severity distributions
- Boxplots of sensor readings grouped by diagnosis
- Pearson correlation heatmap
- Overall symptom frequency analysis

### 3. Markov Chain Modeling *(Core Stochastic Process Section)*
Models disease severity as a discrete-time Markov Chain with states:
> **Healthy → Mild → Moderate → Severe**

- Estimates the **Transition Probability Matrix (TPM)** from the data
- Computes the **Steady-State Distribution** (long-run probability of each severity state)
- Simulates individual patient disease progression paths
- Calculates **Mean First Passage Time** to the Severe state

### 4. Multinomial Logistic Regression
- Predicts diagnosis class (5 categories) from sensor readings + symptom flags
- 75/25 train-test split with feature standardization
- Outputs: confusion matrix, classification report, per-class ROC curves, feature importance

### 5. Ordinal Logistic Regression
- Models severity level (Mild/Moderate/Severe) using the **Proportional Odds Model**
- Respects the natural ordering of severity unlike standard multinomial regression
- Visualizes predicted severity probabilities as a function of body temperature

### 6. Statistical Hypothesis Testing
- **Kruskal-Wallis H-test**: Tests whether sensor readings differ significantly across diagnosis groups
- **Chi-Square test**: Tests whether gender is associated with diagnosis

### 7. Summary & Conclusions
- Interpretation of all results
- Key findings from each modeling approach

---

## ▶️ How to Run

### Option A: Google Colab (Recommended)
1. Go to [colab.research.google.com](https://colab.research.google.com)
2. Click **File → Upload notebook** and upload `disease_stochastic_analysis.ipynb`
3. Upload `disease_diagnosis.csv` to the Colab session files
4. Change the data loading line to:
   ```python
   df = pd.read_csv('disease_diagnosis.csv')
   ```
5. Click **Runtime → Run all**

### Option B: Local Jupyter
```bash
pip install notebook pandas numpy matplotlib seaborn scikit-learn scipy statsmodels
jupyter notebook
```
Place both the `.ipynb` and `.csv` files in the same folder, then open the notebook and run all cells.

### Option C: Plain Python
```bash
python disease_stochastic_analysis.py
```
Place the `.csv` file in the same folder. Plots will appear one at a time — close each to continue.

---

## 📦 Dependencies
```
pandas
numpy
matplotlib
seaborn
scikit-learn
scipy
statsmodels
```
Install all at once:
```bash
pip install pandas numpy matplotlib seaborn scikit-learn scipy statsmodels
```

---

## 🧠 Key Concepts Used
- **Markov Chains** — stochastic modeling of disease severity progression
- **Transition Probability Matrix** — estimated from patient severity data
- **Steady-State Distribution** — long-run behavior of the Markov Chain
- **Mean First Passage Time** — expected steps to reach the Severe state
- **Multinomial Logistic Regression** — multi-class disease diagnosis prediction
- **Ordinal Logistic Regression** — severity classification respecting outcome ordering
- **Kruskal-Wallis Test** — non-parametric comparison across diagnosis groups
- **Chi-Square Test** — testing association between categorical variables

---

## 👥 Project Info
- **Course**: Statistics 300L — Stochastic Processes
- **Topic**: Predictive Modeling for Disease Diagnosis and Prognosis
- **Data**: Simulated EHR dataset (2,000 patients)
