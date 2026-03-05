# Titanic Data Analysis using Python

## 📌 Project Overview
This project performs **Exploratory Data Analysis (EDA)** on the Titanic dataset using Python libraries such as **Pandas, Seaborn, and Matplotlib**.  
The goal is to clean the dataset, handle missing values, analyze relationships between variables, and visualize the data.

---

## 📂 Dataset
The dataset used is the **Titanic dataset** provided by the Seaborn library.

It contains information about passengers such as:
- Passenger class
- Age
- Gender
- Fare
- Survival status
- Embark town
- Family members onboard

---

## 🛠️ Technologies Used

- Python
- Pandas
- Seaborn
- Matplotlib
- Jupyter Notebook / Google Colab

---

## 📊 Steps Performed

### 1️⃣ Import Libraries
```python
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt
```

### 2️⃣ Load Dataset
```python
df = sns.load_dataset("titanic")
```

### 3️⃣ Data Inspection
- `df.head()` – view first rows  
- `df.info()` – dataset structure  
- `df.describe()` – statistical summary  
- `df.columns` – view column names  

---

### 4️⃣ Handling Missing Values
Check missing values:

```python
df.isnull().sum()
```

Fill missing values:

```python
df["age"] = df["age"].fillna(0)
df["fare"] = df["fare"].fillna(df["fare"].mean())
```

---

### 5️⃣ Data Cleaning
Removed unnecessary columns:

```python
df.drop(["alive","who","embarked","deck"], axis=1, inplace=True)
```

Encoding categorical data:

```python
df["sex_code"] = df["sex"].map({"male":10, "female":9})
```

---

### 6️⃣ Correlation Analysis

```python
df[["pclass","survived"]].corr()
```

This helps understand relationships between variables.

---

### 7️⃣ Data Visualization

Histogram of Age:

```python
df["age"].hist()
```

Scatter Plot:

```python
plt.scatter(df["age"], df["fare"])
```

Fare Distribution:

```python
df["fare"].hist()
```

Box Plot for Fare:

```python
df.boxplot(column="fare")
```

---

### 8️⃣ Outlier Detection

Using **Interquartile Range (IQR)** method:

```python
q1 = df["fare"].quantile(0.25)
q3 = df["fare"].quantile(0.75)

iqr = q3 - q1

lower = q1 - 1.5 * iqr
upper = q3 + 1.5 * iqr
```

Detect outliers:

```python
outliers = df[df["fare"] > upper]
```

---

## 📈 Key Insights
- Passenger **class has correlation with survival**.
- **Fare values contain outliers**.
- Missing values existed mainly in **Age and Deck columns**.
- Data visualization helps understand the **distribution of passengers and ticket fares**.

---

## ▶️ How to Run the Project

1. Install required libraries

```bash
pip install pandas seaborn matplotlib
```

2. Open the notebook in **Jupyter Notebook or Google Colab**

3. Run all cells sequentially.

---

## 📁 Project Structure

```
titanic-analysis/
│
├── panda.ipynb
├── README.md
```

---

## 🎯 Learning Outcomes
- Data Cleaning
- Handling Missing Values
- Data Visualization
- Correlation Analysis
- Outlier Detection
- Exploratory Data Analysis (EDA)

---

## 📌 Author
**Airaa Sharif**

---

## ⭐ If you like this project
Give it a **star on GitHub** ⭐
