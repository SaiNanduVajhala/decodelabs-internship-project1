# Project 1: Data Cleaning and Preprocessing
## E-Commerce Transactions Data Cleaning

This repository contains the first project of the Decode Labs Internship. The objective of this project is to clean, validate, and standardize a raw e-commerce transaction dataset (`Dataset for Data Analytics.xlsx`) to prepare it for subsequent Exploratory Data Analysis (EDA) and modeling tasks.

---

## Table of Contents
1. [Project Goal](#project-goal)
2. [Data Preprocessing Pipeline](#data-preprocessing-pipeline)
3. [Validation & Checks Completed](#validation--checks-completed)
4. [Output Dataset](#output-dataset)
5. [Prerequisites & Environment Setup](#prerequisites--environment-setup)
6. [How to Run the Code](#how-to-run-the-code)

---

## Project Goal
Before performing data analysis, it is critical to ensure data quality. Raw data often contains inconsistencies, missing values, incorrect datatypes, trailing spaces, and redundant rows. This project implements a Python-based preprocessing pipeline to clean and validate transaction records.

---

## Data Preprocessing Pipeline

The data cleaning process is implemented in [cleaning.ipynb](file:///c:/Users/nagendra%20prasad/Downloads/gpt2-code-prediction/Project_1_decode_labs_internship/cleaning.ipynb) and consists of the following steps:

1. **Setup & Importing Libraries**:
   * Uses `pandas` for advanced data manipulation and `numpy` for missing value handling.
   
2. **Handling Duplicates**:
   * Scans the dataset for duplicate rows and removes them using `drop_duplicates()` to avoid skewed statistics.

3. **Handling Missing Values (Imputation)**:
   * Inspects all columns for null values.
   * Fills missing entries in the `CouponCode` column with the string `'NONE'`, indicating that no coupon was used for the transaction.

4. **Data Type Standardization**:
   * Converts the `Date` column into a standardized pandas `datetime64[ns]` object using `to_datetime(errors='coerce')` to facilitate time-series grouping.

5. **Text Formatting & Standardization**:
   * Strips all leading and trailing whitespace from string-based categorical columns (`Product`, `PaymentMethod`, `OrderStatus`, `ReferralSource`, `CouponCode`) to avoid duplicate categories caused by formatting differences.

---

## Validation & Checks Completed

To verify that the dataset was cleaned properly without losing critical data, the notebook performs several integrity checks:

- **Constraint Verification**: Checks the `OrderID` column for duplicate identifiers to ensure each order is unique. No duplicate OrderIDs were found.
- **Mathematical Calculation Validation**: Validates that `TotalPrice` matches the expected mathematical formula:
  $$\text{TotalPrice} = \text{Quantity} \times \text{UnitPrice}$$
  The pipeline rounds the values and checks for any discrepancies greater than $\$0.05$. There are **zero mismatches** in the dataset, confirming the pricing calculations are correct.
- **Date Verification**: Confirms there are zero missing or invalid date values after parsing.

---

## Output Dataset

After the cleaning process, the standardized DataFrame is saved as:
* **[Cleaned_Dataset_for_Data_Analytics.xlsx](file:///c:/Users/nagendra%20prasad/Downloads/gpt2-code-prediction/Project_1_decode_labs_internship/Cleaned_Dataset_for_Data_Analytics.xlsx)**

This output contains 1,200 clean, validated rows ready for data analysis.

---

## Prerequisites & Environment Setup

Ensure you have Python (version 3.8 or higher) and the required packages installed:

```bash
pip install pandas openpyxl numpy
```

---

## How to Run the Code

1. Navigate to the project directory:
   `c:\Users\nagendra prasad\Downloads\gpt2-code-prediction\Project_1_decode_labs_internship`
2. Open the Jupyter Notebook:
   ```bash
   jupyter notebook cleaning.ipynb
   ```
3. Run all cells to execute the preprocessing steps and save the cleaned dataset.
