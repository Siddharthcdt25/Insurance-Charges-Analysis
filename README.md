# 🏥 Insurance Charges Prediction

A Machine Learning project to predict medical insurance charges based on patient demographic and health-related features. This project covers the complete ML pipeline — from Exploratory Data Analysis (EDA) to Model Training and Evaluation.

---

## 📁 Project Structure

```
Insurance-Charges-Analysis/
│
├── 📓 P1_insurance.ipynb             # EDA, Data Cleaning & Feature Engineering
├── 📓 Insurance_model.ipynb          # Model Training & Evaluation
├── 📄 insurance.csv                  # Raw Dataset
├── 📄 final_df.csv                   # Processed Dataset (bridge between notebooks)
└── 📄 README.md
```

---

## 📌 Project Overview

Insurance companies need to estimate medical charges for customers based on various factors. This project builds a **Linear Regression model** that predicts insurance charges using features like age, BMI, smoking status, and region.

---

## 📊 Dataset

- **File:** `insurance.csv`
- **Features:**

| Column | Description |
|--------|-------------|
| `age` | Age of the primary beneficiary |
| `sex` | Gender of the beneficiary (male/female) |
| `bmi` | Body Mass Index |
| `children` | Number of children/dependents |
| `smoker` | Smoking status (yes/no) |
| `region` | Residential region in the US |
| `charges` | Individual medical costs billed *(Target Variable)* |

---

## 🔍 Phase 1 — EDA & Feature Engineering (`P1_insurance.ipynb`)

### ✅ Exploratory Data Analysis (EDA)
- Checked dataset shape, datatypes, and null values using `.info()`, `.describe()`, `.isnull().sum()`
- Visualized distributions of numerical features: **age, bmi, children, charges** using histplots and boxplots
- Analyzed categorical features: **sex, smoker, children** using countplots
- Plotted a **Correlation Heatmap** to understand feature relationships

### ✅ Data Cleaning & Preprocessing
- Removed **duplicate rows**
- **Label Encoded** categorical features:
  - `sex` → `is_female` (male=0, female=1)
  - `smoker` → `is_smoker` (no=0, yes=1)
- **One-Hot Encoded** the `region` column (drop_first=True)

### ✅ Feature Engineering
- Created a new feature **`bmi_category`** by binning BMI values:
  - Underweight → BMI < 18.5
  - Normal → BMI 18.5–24.9
  - Overweight → BMI 25–29.9
  - Obese → BMI ≥ 30
- One-Hot Encoded `bmi_category` (drop_first=True)

### ✅ Feature Scaling
- Applied **StandardScaler** on continuous features: `age`, `bmi`, `children`

### ✅ Feature Selection
- **Pearson Correlation** used for numerical features vs target (`charges`)
- **Chi-Square Test** used for categorical features vs target
- Final selected features:

```
age, is_female, bmi, children, is_smoker, region_southeast, bmi_category_Obese
```

---

## 🤖 Phase 2 — Model Training & Evaluation (`Insurance_model.ipynb`)

### ✅ Model Used
- **Linear Regression** (from `sklearn.linear_model`)

### ✅ Train-Test Split
- Test size: **20%**
- Random state: **42**

### ✅ Model Evaluation Metrics
- **R² Score** — Measures goodness of fit
- **Adjusted R² Score** — Accounts for number of features used

---

## 🛠️ Technologies Used

| Tool | Purpose |
|------|---------|
| Python | Programming Language |
| Pandas | Data Manipulation |
| NumPy | Numerical Operations |
| Matplotlib & Seaborn | Data Visualization |
| Scikit-learn | ML Modeling & Preprocessing |
| SciPy | Statistical Tests (Pearson, Chi-Square) |
| JupyterLab | Development Environment |

---

## 🚀 How to Run This Project

1. **Clone the repository**
```bash
git clone https://github.com/your-username/Insurance-Charges-Analysis.git
cd Insurance-Charges-Analysis
```

2. **Install required libraries**
```bash
pip install pandas numpy matplotlib seaborn scikit-learn scipy
```

3. **Run Notebook 1 first** (EDA & Feature Engineering)
```bash
jupyter lab P1_insurance.ipynb
```

4. **Run Notebook 2** (Model Training & Evaluation)
```bash
jupyter lab Insurance_model.ipynb
```

> ⚠️ Make sure to run **Notebook 1 first** as it generates `final_df.csv` which is used by Notebook 2.

## 📄 License

This project is open source and available under the [MIT License](LICENSE).
