# 🏠 Home Sales Analysis with PySpark

![PySpark](https://img.shields.io/badge/PySpark-Big%20Data-orange?logo=apachespark)
![Python](https://img.shields.io/badge/Python-Data%20Processing-blue?logo=python)
![Google Colab](https://img.shields.io/badge/Google%20Colab-Notebook-blue?logo=googlecolab&logoColor=white)
![AWS](https://img.shields.io/badge/AWS-S3%20Data-green?logo=amazonaws)

## 📌 Project Overview
This project leverages **PySpark** to analyze home sales data efficiently at scale. The dataset is sourced from an **AWS S3 bucket**, loaded into a **Spark DataFrame**, and queried using **SparkSQL**.

### 🚀 **Key Tasks Completed**
✅ Load & preprocess real estate data  
✅ Compute **average home prices** based on multiple conditions  
✅ Improve performance with **caching & partitioning**  
✅ Utilize **Parquet format** for optimized storage and retrieval  
✅ Compare **runtime improvements** with different query approaches  

---

## 📂 **Dataset Information**
- **Source**: [AWS S3 - Home Sales Data](https://2u-data-curriculum-team.s3.amazonaws.com/dataviz-classroom/v1.2/22-big-data/home_sales_revised.csv)
- **Columns:**
  - **Property Details:** `bedrooms`, `bathrooms`, `floors`, `sqft_living`, `view`, etc.
  - **Sale Information:** `date_sold`, `price`, `waterfront`, etc.
  - **Build Information:** `date_built`

---

## 🔧 **Setup & Installation**
### 1️⃣ Install Dependencies
```bash
pip install pyspark findspark
```

### 2️⃣ Run the Script
Ensure to run the file on Google Colab:
```bash
Home_Sales_main_code_colab.ipynb
```

---

## 🔍 **Key Queries & Results**
### 🏠 **1. Average Price of Four-Bedroom Homes Per Year**
```sql
SELECT YEAR(date) AS year_sold, ROUND(AVG(price), 2) AS avg_price
FROM home_sales
WHERE bedrooms = 4
GROUP BY year_sold
ORDER BY year_sold;
```
| Year Sold | Avg Price ($) |
|-----------|--------------|
| 2019      | 300,263.70   |
| 2020      | 298,353.78   |
| 2021      | 301,819.44   |
| 2022      | 296,363.88   |

---

### 🛠 **2. Cached vs. Uncached Query Performance**
| Query Type | **Uncached Runtime** | **Cached Runtime** |
|------------|------------------|----------------|
| Avg Price by View (≥ $350K) | ⏳ 0.95 sec | ⚡ 0.47 sec |
| Partitioned Data Query | ⏳ 0.93 sec | ⚡ Optimized |

Caching significantly reduces processing time, improving **query speed by ~50%**.

---

## 📊 **Performance Optimization Techniques**
✅ **Caching tables** improves query efficiency  
✅ **Partitioning by `date_built`** enhances retrieval speeds  
✅ **Using Parquet format** reduces storage overhead  

---

## 📄 **License**
MIT License. Free to use and modify.

---

