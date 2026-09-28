# 🏥 Healthcare Data Analysis Using Python

## 📌 Project Overview

This project focuses on **Healthcare Data Analysis using Python, Pandas, Matplotlib, and Seaborn**.

The project uses a healthcare dataset containing patient information, medical conditions, admission details, billing amounts, medical codes, and admission/discharge dates.

The notebook performs **data loading, data inspection, data cleaning, date processing, feature engineering, and exploratory data analysis (EDA)** to understand healthcare-related information.

---

## 🎯 Objectives

The main objectives of this project are:

* Load and explore the healthcare dataset.
* Understand the structure and data types of the dataset.
* Identify and handle missing values.
* Convert admission and discharge dates into proper datetime format.
* Calculate the number of hospital stay days.
* Analyze different admission types.
* Analyze medical conditions.
* Explore billing amount statistics.
* Compare admission types with medical conditions.
* Calculate average patient age for different medical conditions.
* Create an urgency category based on admission type.

---

## 🛠️ Technologies Used

* **Python**
* **Jupyter Notebook**
* **Pandas**
* **Matplotlib**
* **Seaborn**

---

## 📂 Dataset

The dataset contains **500 patient records** and **9 attributes**.

### Dataset Columns

| Column              | Description                                    |
| ------------------- | ---------------------------------------------- |
| `Patient_ID`        | Unique identifier for each patient             |
| `Gender`            | Gender of the patient                          |
| `Age`               | Age of the patient                             |
| `Medical_Condition` | Medical condition diagnosed                    |
| `Admission_Date`    | Date of hospital admission                     |
| `Admission_Type`    | Type of hospital admission                     |
| `Medical_Code`      | Medical/ICD code associated with the condition |
| `Billing_Amount`    | Healthcare billing amount                      |
| `Discharge_Date`    | Date of hospital discharge                     |

---

## 🔍 Project Workflow

### 1. Import Required Libraries

The following Python libraries are used:

```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
```

---

### 2. Load the Dataset

The healthcare CSV dataset is loaded using Pandas.

```python
df = pd.read_csv("healthcare_raw.csv")
```

---

### 3. Explore the Dataset

The project checks the dataset using:

* Dataset display
* Column names
* First few records
* Last few records
* Dataset shape
* Descriptive statistics
* Dataset information
* Data types

Examples:

```python
df.head()
df.tail()
df.shape
df.describe()
df.info()
df.dtypes
```

---

### 4. Missing Value Analysis

Missing values are checked throughout the dataset.

```python
df.isnull().sum()
```

The `Medical_Code` column contains missing values, which are handled by replacing them with `"Unknown"`.

```python
df['Medical_Code'] = df['Medical_Code'].fillna('Unknown')
```

This prevents missing medical codes from affecting further analysis.

---

### 5. Date Conversion

The `Admission_Date` and `Discharge_Date` columns are converted from text format into datetime format.

```python
df['Admission_Date'] = pd.to_datetime(df['Admission_Date'])
df['Discharge_Date'] = pd.to_datetime(df['Discharge_Date'])
```

This allows date-based calculations and analysis.

---

### 6. Data Cleaning

Admission types are standardized by removing unnecessary spaces and converting the values to lowercase.

```python
df['Admission_Type'] = (
    df['Admission_Type']
    .str.strip()
    .str.lower()
)
```

This creates consistent values such as:

* `emergency`
* `urgent`
* `routine`

---

### 7. Calculate Hospital Stay

A new feature called `Hos_Stay_Days` is created to calculate how many days each patient stayed in the hospital.

```python
df["Hos_Stay_Days"] = (
    df['Discharge_Date'] - df['Admission_Date']
).dt.days
```

This provides useful information about patient hospitalization duration.

---

## 📊 Exploratory Data Analysis

### Medical Conditions

The frequency of different medical conditions is analyzed using:

```python
df["Medical_Condition"].value_counts()
```

This helps identify how frequently different medical conditions appear in the dataset.

---

### Admission Types

Admission types are analyzed using:

```python
df['Admission_Type'].value_counts()
```

This provides the distribution of patients across different admission categories.

---

### Billing Amount Analysis

Statistical information about healthcare billing amounts is obtained using:

```python
df['Billing_Amount'].describe()
```

This provides values such as:

* Count
* Mean
* Standard deviation
* Minimum
* Maximum
* Quartiles

---

### Hospital Stay Analysis

The calculated hospital stay duration is analyzed using:

```python
df['Hos_Stay_Days'].describe()
```

This helps understand the distribution of hospital stay durations.

---

### Admission Type vs Medical Condition

A cross-tabulation is created to examine the relationship between admission types and medical conditions.

```python
pd.crosstab(
    df['Admission_Type'],
    df['Medical_Condition']
)
```

This helps understand how different medical conditions are distributed across admission types.

---

### Average Age by Medical Condition

The average age of patients for each medical condition is calculated using:

```python
df.groupby('Medical_Condition')['Age'].mean()
```

This provides an age-based comparison across medical conditions.

---

## 🚨 Urgency Category

A new column named `Urgency_Category` is created based on the admission type.

```python
df['Urgency_Category'] = df['Admission_Type'].map({
    'emergency': 'Emergency',
    'routine': 'Elective',
    'urgent': 'Urgent'
})
```

The resulting categories are:

| Admission Type | Urgency Category |
| -------------- | ---------------- |
| Emergency      | Emergency        |
| Urgent         | Urgent           |
| Routine        | Elective         |

The distribution can be checked using:

```python
df['Urgency_Category'].value_counts()
```

---

## 📈 Key Features of the Project

* Healthcare dataset exploration
* Data cleaning
* Missing-value handling
* Date conversion
* Feature engineering
* Hospital stay calculation
* Admission analysis
* Medical condition analysis
* Billing analysis
* Cross-tabulation
* Group-based analysis
* Urgency classification

---

## 📁 Project Structure

```text
Healthcare-Data-Analysis/
│
├── healthcare_raw.csv
├── Healthcare_Data_Analysis.ipynb
└── README.md
```
---

## 💡 Learning Outcomes

Through this project, the following concepts were practiced:

* Working with CSV datasets using Pandas
* DataFrame inspection
* Data cleaning and preprocessing
* Handling missing values
* Datetime conversion
* Feature engineering
* Descriptive statistics
* GroupBy operations
* Value counts
* Cross-tabulation
* Healthcare data analysis

---

## 👨‍💻 Author

**Samrabinson P**

BCA Student | Python | Java | Data Analytics | Full Stack Development

---
