# PYTHON_DIWALI_SALES_ANALYSIS_PROJECT
# 🛍️ Diwali Sales Data Analysis Project

This project presents a complete end-to-end analysis of retail Diwali sales data using Python, Pandas, Matplotlib, and Seaborn. The primary aim is to extract actionable business insights that help identify key customer demographics and product trends for targeted business expansion.

---

## 🎯 Project Objectives

* Clean and transform raw sales data from a CSV file.
* Perform detailed **exploratory data analysis (EDA)** to discover sales patterns.
* Use visualizations to understand customer segmentation and product performance.
* Help businesses identify top-performing customer segments and focus areas for marketing and inventory.
* Apply mathematical and statistical formulas to derive meaningful business KPIs such as total revenue, average order value, customer segmentation trends, and product performance metrics.

---

## 📦 Dataset Information

* **Total Rows:** 11,251 records before cleaning; 11,239 after cleaning.
* **Columns:** User demographics, product details, sales amount, and quantity ordered.
* **Key Fields:**

  * Gender
  * Age & Age Group
  * Marital Status
  * State & Zone
  * Occupation
  * Product Category
  * Orders and Sales Amount

---

## 🔧 Data Cleaning & Preparation

* Removed unrelated columns (`Status`, `unnamed1`).
* Handled missing values in the `Amount` column.
* Converted data types for numerical analysis.
* Renamed columns for readability (e.g., `Marital_Status` → `Shaadi`).
* Extracted custom age bins using:

  ```python
  df['Age_Group'] = pd.cut(df['Age'], bins=[0, 18, 25, 35, 45, 55, 100],
                            labels=['<18', '18-25', '26-35', '36-45', '46-55', '55+'])
  ```
* Cleaned and filtered out null entries using:

  ```python
  df.dropna(inplace=True)
  ```
* Converted object columns to numeric for analysis:

  ```python
  df['Amount'] = df['Amount'].astype(int)
  ```

---

## 📊 Key Insights

### 👥 Gender Analysis

* Majority of buyers are **female**.
* **Females contribute higher total sales** compared to males.

  ```python
  df.groupby('Gender')['Amount'].sum().sort_values(ascending=False)
  ```

### 📅 Age Group Trends

* Highest sales are from the **26-35 years age group**.
* Particularly **females aged 26-35** show the most purchasing activity.

  ```python
  df.groupby(['Age_Group', 'Gender'])['Amount'].sum().unstack().plot(kind='bar')
  ```

### 🌍 Geographic Distribution

* **Top states by orders and revenue:**

  * Uttar Pradesh
  * Maharashtra
  * Karnataka

  ```python
  df.groupby('State')['Orders'].sum().sort_values(ascending=False).head(10)
  ```

### 💍 Marital Status

* **Married women** are the most active and highest-spending customer segment.

  ```python
  df.groupby(['Shaadi', 'Gender'])['Amount'].sum().sort_values(ascending=False)
  ```

### 👩‍💼 Occupation

* Most customers work in:

  * IT Sector
  * Healthcare
  * Aviation

  ```python
  df.groupby('Occupation')['Amount'].sum().sort_values(ascending=False)
  ```

### 📦 Product Preferences

* **Top product categories by sales:**

  * Food
  * Clothing
  * Electronics

  ```python
  df.groupby('Product_Category')['Amount'].sum().sort_values(ascending=False)
  ```
* Popular products received high repeat orders.

---

## 📐 Formulas and Calculations

* **Total Revenue:**

  ```python
  total_revenue = df['Amount'].sum()
  ```

* **Average Order Value (AOV):**

  ```python
  aov = df.groupby('User_ID')['Amount'].sum().mean()
  ```

* **Conversion Rate by Gender:**

  ```python
  df.groupby('Gender')['User_ID'].nunique() / df['User_ID'].nunique()
  ```

* **Sales Contribution by State:**

  ```python
  (df.groupby('State')['Amount'].sum() / df['Amount'].sum()) * 100
  ```

* **Order Frequency per User:**

  ```python
  df.groupby('User_ID')['Orders'].count().mean()
  ```

---

## 📈 Tools Used

* **Python**: Data analysis and logic
* **Pandas & NumPy**: Data cleaning and transformation
* **Matplotlib & Seaborn**: Visualization and storytelling
* **Jupyter Notebook**: For documenting analysis step-by-step

---

## ✅ Final Business Conclusion

> “**Married women aged 26–35 from Uttar Pradesh, Maharashtra, and Karnataka working in IT, Healthcare, or Aviation are the top buyers, mostly purchasing products in Food, Clothing, and Electronics.**”

These findings can help the business target marketing campaigns, manage inventory, and improve customer retention.

---

## 🙌 Thank You!

For queries, feedback, or collaboration, feel free to connect.

---


## 🙌 Thank You!

For queries, feedback, or collaboration, feel free to connect.

---
