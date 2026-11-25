# Data Cleaning and Preprocessing

## Project Overview

Data cleaning is an essential step in the data science workflow. Raw datasets often contain missing values, duplicate records, inconsistent information, and unusual observations that can affect the accuracy of data analysis.

This project demonstrates a systematic data cleaning and preprocessing workflow using Python and Pandas. The objective is to identify data quality issues, apply appropriate cleaning strategies, detect outliers, encode categorical variables, and compare the dataset before and after cleaning.

## Dataset

**Dataset:** Titanic Passenger Dataset

**Source:** [Titanic Dataset on GitHub](https://github.com/datasciencedojo/datasets/blob/master/titanic.csv)

The dataset contains 891 passenger records with information such as:

- Passenger class
- Age
- Sex
- Ticket fare
- Embarkation port
- Number of siblings and spouses
- Number of parents and children
- Survival status

The dataset contains genuine missing values, particularly in Age, Cabin, and Embarked.

## Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Google Colab
- Jupyter Notebook

## Project Workflow

### 1. Data Loading and Inspection

The dataset is loaded using Pandas. Initial inspection is performed using:

- `info()`
- `head()`
- `describe()`
- `isnull().sum()`
- `duplicated().sum()`

This helps identify data types, missing values, duplicate records, and statistical characteristics.

### 2. Duplicate Handling

Exact duplicate rows are identified using Pandas `duplicated()`.

If duplicate records are present, they are removed using `drop_duplicates()`. Records that share individual values are not automatically treated as duplicates.

### 3. Missing Value Treatment

Different strategies are applied based on the characteristics of each column.

| Column | Strategy | Reason |
|---|---|---|
| Age | Median imputation by passenger class and sex | Preserves group-level age patterns and reduces sensitivity to extreme values |
| Embarked | Mode imputation | Suitable for a nominal categorical variable with few missing values |
| Cabin | Column removal | A large proportion of values are missing |
| Other columns | Retained if complete | Avoids unnecessary modifications |

### 4. Outlier Detection

The Interquartile Range (IQR) method is used to identify potential numerical outliers.

The formula is:

`IQR = Q3 - Q1`

Lower Bound:

`Q1 - 1.5 * IQR`

Upper Bound:

`Q3 + 1.5 * IQR`

Box plots are also generated to visually inspect unusual values.

Statistically unusual but realistic observations are retained. An outlier is not automatically considered a data-entry error.

### 5. Categorical Encoding

Categorical variables are converted into numerical representations.

- **One-Hot Encoding:** Applied to nominal variables such as Sex and Embarked.
- **Ordinal Encoding:** Applied to Pclass because passenger classes have a meaningful order.
- **Target Variable:** Survived is retained as a binary 0/1 variable.

Identifier and high-cardinality text columns such as PassengerId, Name, and Ticket are excluded from the final modelling-ready dataset.

### 6. Before and After Comparison

The project compares the original and cleaned datasets using:

- Number of rows and columns
- Missing value counts
- Duplicate counts
- Numerical summary statistics
- Final encoded dataset structure

This demonstrates the impact of the cleaning and preprocessing operations.

## Project Files

| File | Description |
|---|---|
| `Data_Cleaning_Milestone.ipynb` | Complete Google Colab/Jupyter notebook |
| `README.md` | Project documentation |
| `titanic_cleaned_encoded.csv` | Cleaned and encoded dataset generated after execution |

## How to Run the Project

1. Download or clone this repository.
2. Open `Data_Cleaning_Milestone.ipynb` using Google Colab or Jupyter Notebook.
3. Run all cells from top to bottom.
4. Inspect the cleaning reports, visualisations, and before-after comparisons.
5. Download the generated cleaned CSV file.

An internet connection is required to load the original dataset from its public source.

## Key Learnings

- Understanding and identifying real-world data quality issues.
- Handling missing values using justified, column-specific strategies.
- Detecting potential outliers using the IQR method.
- Identifying and removing exact duplicate records.
- Applying appropriate categorical encoding techniques.
- Comparing datasets before and after preprocessing.
- Documenting data-cleaning decisions for reproducibility.

## Conclusion

This project demonstrates a structured approach to cleaning and preprocessing a real-world dataset. It highlights the importance of understanding data quality before performing analysis or building machine learning models.

Using Python, Pandas, NumPy, and Matplotlib, the workflow transforms raw passenger information into a cleaner, encoded dataset suitable for further analytical tasks.

---

**Project Category:** Data Science | Data Cleaning | Data Preprocessing

**Tools:** Python | Pandas | NumPy | Matplotlib | Google Colab
