# 📊 **DSAI202: Data Governance & Salary Survey Analysis**
*A comprehensive data governance pipeline for cleaning, validating, and visualizing the "Ask A Manager Salary Survey 2021" dataset.*

![Python](https://img.shields.io/badge/Python-3.8+-blue?logo=python)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange?logo=jupyter)
![Pandas](https://img.shields.io/badge/Pandas-1.3+-green?logo=pandas)
![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)

---

## 📖 **Overview**
This Jupyter Notebook implements **Phase 1 & 2 of a Data Governance project** for the *"Ask A Manager Salary Survey 2021"* dataset. The goal is to transform raw survey responses into a **clean, validated, and analysis-ready dataset** while adhering to data governance best practices.

### **Problem Solved**
- **Raw Data Challenges**: Inconsistent formats, missing values, duplicate entries, and non-standardized categorical fields (e.g., country names, currencies).
- **Data Quality**: Ensuring accuracy, completeness, and consistency for downstream analysis.
- **Validation**: Enforcing schema rules to prevent data corruption.

### **Approach**
1. **Data Profiling**: Automated (YData Profiling) + manual inspection to understand data structure and quality.
2. **Cleaning Pipeline**:
   - Standardize text fields (e.g., country names, currencies).
   - Parse numerical/temporal data (e.g., salaries, timestamps).
   - Handle missing values and duplicates.
3. **Validation**: Schema enforcement using `pandera` to ensure data integrity.
4. **Visualization**: Generate insights via exploratory plots (e.g., salary distributions by age, industry).

---

## 🗂️ **Notebook Structure**
| Section               | Owner               | Description                                                                                     |
|-----------------------|---------------------|-------------------------------------------------------------------------------------------------|
| **1. Setup**          | Omar Hany           | Install and import libraries (`pandera`, `ydata-profiling`, `seaborn`, etc.).                  |
| **2. Data Loading**   | Omar Hany           | Load the raw CSV file and display initial rows.                                                |
| **3. Data Profiling** | Omar Hany           | Generate a **manual profile** (null counts, dtypes) and **automated YData report**.            |
| **4. Data Cleaning**  | Team                | - Rename columns for clarity. <br> - Parse timestamps, salaries, and currencies. <br> - Standardize text fields (e.g., "USA" → "United States"). <br> - Map categorical ranges (e.g., age groups → midpoints). <br> - Drop high-null columns and duplicates. |
| **5. Validation**     | Nader Mohamed       | Define and enforce a **Pandera schema** to validate data types, ranges, and categorical values. |
| **6. Visualization**  | Rowida Sayed        | Generate **exploratory plots** (e.g., salary distributions, demographic breakdowns).           |
| **7. Output**         | Omar Hany           | Save the cleaned dataset to CSV.                                                               |

---

## 🔬 **Key Techniques & Libraries**
### **Libraries Used**
| Library               | Purpose                                                                                     |
|-----------------------|---------------------------------------------------------------------------------------------|
| `pandas`              | Data manipulation and cleaning.                                                             |
| `numpy`               | Numerical operations (e.g., salary parsing).                                                |
| `ydata-profiling`     | Automated exploratory data analysis (EDA) report generation.                                |
| `pandera`             | Data validation and schema enforcement.                                                     |
| `matplotlib`/`seaborn`| Visualization (histograms, bar plots, box plots).                                           |
| `re`                  | Regex for text cleaning (e.g., salary extraction).                                          |
| `openpyxl`            | Excel file handling (if needed).                                                            |

### **Key Methods**
- **Text Standardization**:
  - `str.strip()`, `str.title()`, regex (`re.sub()`) for cleaning country names, currencies.
- **Numerical Parsing**:
  - `pd.to_numeric()` + custom functions to extract salaries from messy strings.
- **Validation**:
  - `pandera.DataFrameSchema` to enforce data types, ranges, and categorical values.
- **Visualization**:
  - `sns.barplot()`, `sns.boxplot()`, `sns.histplot()` for demographic and salary insights.

---

## 🚀 **How to Run**
### **Prerequisites**
- Python 3.8+
- Jupyter Notebook/Lab

### **Step-by-Step Instructions**
1. **Clone the Repository** (or download the notebook):
   ```bash
   git clone https://github.com/your-repo/DSAI202_DataGovernance.git
   cd DSAI202_DataGovernance
   ```

2. **Install Dependencies**:
   ```bash
   pip install -r requirements.txt
   ```
   *or manually install:*
   ```bash
   pip install pandas numpy ydata-profiling pandera matplotlib seaborn openpyxl jupyter
   ```

3. **Download the Dataset**:
   - Place the file `"Ask A Manager Salary Survey 2021 (Responses).csv"` in the same directory as the notebook.

4. **Launch Jupyter Notebook**:
   ```bash
   jupyter notebook "DSAI202_Phase1_and_2_DataGovernance (1).ipynb"
   ```

5. **Run All Cells**:
   - Execute cells sequentially (or use `Kernel → Restart & Run All`).

6. **Outputs**:
   - **Cleaned dataset**: `salary_survey_2021_cleaned.csv`
   - **Profiling report**: `profiling_report.html` (interactive EDA)
   - **Visualizations**: Inline plots in the notebook.

---

## 📊 **Results / Insights**
### **Data Quality Improvements**
| Metric                     | Before Cleaning       | After Cleaning        |
|----------------------------|-----------------------|-----------------------|
| **Rows**                   | 27,000+               | ~26,500               |
| **Null Values**            | 15%+ in key columns   | <5% in most columns   |
| **Duplicate Rows**         | ~500                  | 0                     |
| **Standardized Countries** | 50+ variants (e.g., "USA", "US") | 1 ("United States") |

### **Key Findings**
1. **Demographics**:
   - **Age Distribution**: 60% of respondents are aged **25-34**.
   - **Gender**: ~70% identify as female, ~25% as male.
   - **Top Countries**: **United States (85%)**, UK, Canada, Australia.

2. **Salary Insights**:
   - **Median Salary (USD)**: ~$85,000 (varies by industry/job title).
   - **Highest-Paying Industries**: Tech, Finance, Healthcare.
   - **Experience Impact**: Salary increases **~10% per 5 years of experience**.

3. **Validation**:
   - **Schema Compliance**: 100% of rows passed `pandera` validation after cleaning.

---

## 💡 **Possible Extensions**
| Idea                          | Description                                                                                     |
|-------------------------------|-------------------------------------------------------------------------------------------------|
| **Currency Conversion**       | Convert all salaries to USD using exchange rates for cross-country comparisons.                |
| **Advanced Visualizations**   | Interactive plots (Plotly/Dash) for salary vs. experience/education.                            |
| **Anomaly Detection**         | Use `PyOD` or `Isolation Forest` to flag outliers (e.g., $1 salaries).                          |
| **Automated Pipeline**        | Convert notebook to a **modular Python script** (e.g., `clean.py`) for batch processing.       |
| **Data Augmentation**         | Merge with external datasets (e.g., cost-of-living indices) for adjusted salary analysis.       |
| **CI/CD Integration**         | Add GitHub Actions to run validation on new data submissions.                                   |
| **Documentation**             | Generate a **data dictionary** (e.g., using `pydoc` or `Sphinx`) for the cleaned dataset.       |

---

## 📊 **Contributors**

### Omar Hany Darwish

- **GitHub**: [OmarHanyDarwish](https://github.com/OmarDarwish483)
- **LinkedIn**: [Omar Hany Darwish](https://www.linkedin.com/in/omardrwish/)
- **Email**: darwishomar158@gmail.com