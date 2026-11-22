# Retail Customer Sales -- Exploratory Data Analysis (EDA)

A Python-based Exploratory Data Analysis project on retail customer
sales transactions from 2023--2024. The project covers data quality
assessment, cleaning, statistical profiling, outlier detection, feature
engineering, visualisation, and business analysis.

## Table of Contents

-   [Project Overview](#project-overview)
-   [Objectives](#objectives)
-   [Dataset Description](#dataset-description)
-   [Tools and Libraries](#tools-and-libraries)
-   [Repository Structure](#repository-structure)
-   [Analysis Workflow](#analysis-workflow)
-   [Data Cleaning](#data-cleaning)
-   [Exploratory Data Analysis](#exploratory-data-analysis)
-   [Outlier Detection](#outlier-detection)
-   [Feature Engineering](#feature-engineering)
-   [Key Business Findings](#key-business-findings)
-   [Data Validation](#data-validation)
-   [How to Run](#how-to-run-the-project)
-   [Deliverables](#project-deliverables)
-   [Author](#author)

## Project Overview

Retail businesses generate information about customers, products,
transactions, payments, sales, costs, profits, deliveries, and customer
satisfaction. Analysing these records can reveal patterns in product
performance, regional contribution, customer segments, and payment
preferences.

This project performs EDA on a retail customer sales dataset covering
2023--2024. The original dataset contains **7,084 rows and 24 columns**.
After cleaning and feature engineering, the final analytical dataset
contains **7,000 rows and 27 columns**.

The work is implemented in a Python Jupyter Notebook. The repository
includes the original and cleaned datasets, visual outputs, an insights
report, and a project synopsis.

## Objectives

-   Inspect dataset structure, columns, data types, and summary
    information.
-   Identify missing values, duplicate records, inconsistent categories,
    and invalid values.
-   Clean and prepare the dataset using documented rules.
-   Perform descriptive statistical analysis on eight numerical
    variables.
-   Explore numerical and categorical variables through univariate
    analysis.
-   Detect potential outliers using the Interquartile Range (IQR)
    method.
-   Create additional analytical features through feature engineering.
-   Answer business questions using grouping and aggregation.
-   Present findings through charts, a notebook, and written reports.

## Dataset Description

-   **Dataset:** `retail_customer_sales_dataset.csv`
-   **Period:** 2023--2024
-   **Original dimensions:** 7,084 rows × 24 columns
-   **Cleaned dimensions:** 7,000 rows × 27 columns

The dataset contains transaction-level retail information, including
customer details, product information, order and delivery dates, payment
information, sales, cost, profit, ratings, and satisfaction details.

The original dataset is stored in `data/`. The cleaned dataset is stored
in `outputs/`.

## Tools and Libraries

  -----------------------------------------------------------------------
  Tool / Library                      Purpose
  ----------------------------------- -----------------------------------
  Python 3                            Main programming language

  Jupyter Notebook                    Interactive analysis environment

  Visual Studio Code                  Development environment

  Pandas                              Data loading, cleaning,
                                      transformation, grouping, and
                                      aggregation

  NumPy                               Numerical operations

  Matplotlib                          Data visualisation

  Seaborn                             Statistical visualisation

  missingno                           Missing-value pattern inspection
  -----------------------------------------------------------------------

## Repository Structure

``` text
EDA_Project_2026M01410010/
│
├── .venv/                                      # Local Python environment (not committed)
├── data/
│   └── retail_customer_sales_dataset.csv       # Original dataset
├── notebooks/
│   └── EDA_Analysis.ipynb                       # Main EDA notebook
├── outputs/
│   ├── age_boxplot.png
│   ├── income_boxplot.png
│   ├── profit_boxplot.png
│   ├── sales_boxplot.png
│   ├── numerical_histograms.png
│   ├── sales_by_product_category.png
│   ├── sales_by_region.png
│   ├── sales_by_customer_segment.png
│   ├── sales_by_payment_method.png
│   ├── average_customer_rating_by_category.png
│   └── cleaned_retail_customer_sales.csv       # Cleaned dataset
├── reports/
│   ├── 2026M01410010_Ajay_Pratap_Singh_Chauhan_Insights_Report_Updated.docx
│   └── 2026M01410010_Retail_Customer_Sales_EDA_Project_Synopsis.docx
├── .gitignore
└── README.md
```

The `.venv/` directory is for the local development environment and
should not be uploaded to GitHub. The `.gitignore` file should exclude
the virtual environment, Python cache files, Jupyter checkpoints, and
local environment files.

## Analysis Workflow

1.  **Data loading and inspection:** Load the CSV and inspect
    dimensions, columns, data types, summaries, missing values, and
    duplicates.
2.  **Data quality audit:** Identify incomplete, duplicated,
    inconsistent, invalid, and date-related records.
3.  **Data cleaning:** Apply documented cleaning and standardisation
    rules.
4.  **Statistical profiling:** Calculate descriptive statistics for the
    required numerical variables.
5.  **Univariate analysis:** Examine numerical and categorical
    distributions.
6.  **Outlier detection:** Apply IQR-based thresholds to selected
    numerical variables.
7.  **Feature engineering:** Create additional features for delivery and
    financial analysis.
8.  **Business analysis:** Use group-wise aggregation to answer business
    questions.
9.  **Visualisation and validation:** Generate charts and verify the
    final cleaned dataset.

## Data Cleaning

The cleaning process documented in the notebook includes: - Removing
exact duplicate rows. - Standardising inconsistent `Gender` and `Region`
labels. - Treating `Age` values outside 18--100 as invalid. - Treating
`Discount` values outside 0--1 as invalid. - Imputing missing numerical
values using the median. - Filling missing `Satisfaction_Level` values
using the mode. - Parsing date fields and checking delivery dates
against order dates. - Handling missing delivery dates using the median
delivery interval. - Rechecking duplicates after categorical
standardisation.

Potential outliers are not automatically removed. They are retained
where there is no separate evidence that the values are erroneous, since
unusually high values may represent genuine customer or transaction
behaviour.

## Exploratory Data Analysis

### Numerical Analysis

Descriptive statistics are calculated for eight numerical variables:
`Age`, `Income`, `Quantity`, `Unit_Price`, `Discount`, `Sales`, `Cost`,
and `Profit`.

The measures include mean, median, mode, standard deviation, variance,
quartiles, Interquartile Range (IQR), P90, and P95.

### Univariate Analysis

The notebook examines numerical distributions for `Age`, `Income`,
`Sales`, and `Profit` using histograms and box plots. It also explores
categorical distributions for `Gender`, `Region`, `Product_Category`,
`Customer_Segment`, and `Payment_Method`.

## Outlier Detection

Potential outliers are identified using the IQR method:

-   `IQR = Q3 − Q1`
-   Lower bound = `Q1 − 1.5 × IQR`
-   Upper bound = `Q3 + 1.5 × IQR`

Outlier counts calculated on the final 7,000-row dataset:

  Variable     IQR Outlier Count
  ---------- -------------------
  Age                         10
  Income                     278
  Sales                      632
  Profit                     640

These counts represent observations outside the IQR thresholds; they do
not automatically indicate incorrect data.

## Feature Engineering

Three additional features are created:

  ------------------------------------------------------------------------------
  Feature                 Calculation                    Purpose
  ----------------------- ------------------------------ -----------------------
  `Delivery_Days`         `Delivery_Date − Order_Date`   Measures delivery
                                                         duration in days.

  `Total_Cost`            `Cost × Quantity`              Estimates cost for the
                                                         purchased quantity,
                                                         based on the dataset's
                                                         `Cost` field.

  `Profit_Margin`         `(Profit ÷ Sales) × 100`       Measures profit as a
                                                         percentage of sales.
  ------------------------------------------------------------------------------

## Key Business Findings

Five business questions are answered using group-wise aggregation:

  -----------------------------------------------------------------------
  Business Question                   Finding
  ----------------------------------- -----------------------------------
  Which product category generates    **Electronics** --- ₹37,639,557.39
  the highest total sales?            

  Which region contributes the        **East** --- ₹20,018,192.35
  highest total sales?                

  Which customer segment has the      **Corporate** --- ₹11,140.59
  highest average transaction sales?  

  Which payment method records the    **Cash on Delivery** ---
  highest total sales?                ₹16,275,494.33

  Which category has the highest      **Electronics** --- 3.12 out of 5
  average customer rating?            
  -----------------------------------------------------------------------

### Additional Segment Comparison

The notebook also compares total sales by customer segment. This is
different from average transaction sales. Corporate has the highest
**average transaction sales**, while Consumer has the highest
**aggregate segment sales** in the analysed dataset.

## Data Validation

The final cleaned dataset passed these checks:

  Validation Check                                    Result
  -------------------------------- -------------------------
  Final dataset dimensions           7,000 rows × 27 columns
  Missing values                                           0
  Exact duplicate rows                                     0
  Unique `Transaction_ID` values                       7,000
  `Age` values outside 18--100                             0
  `Discount` values outside 0--1                           0
  Negative `Delivery_Days`                                 0

## How to Run the Project

### 1. Clone the Repository

Replace `YOUR-USERNAME` with your GitHub username.

``` bash
git clone https://github.com/YOUR-USERNAME/retail-customer-sales-eda.git
cd retail-customer-sales-eda
```

### 2. Create a Virtual Environment (Recommended)

``` bash
python -m venv .venv
```

Activate it on Windows:

``` bash
.venv\\Scripts\\activate
```

### 3. Install Required Libraries

``` bash
pip install pandas numpy matplotlib seaborn missingno jupyter
```

### 4. Open and Run the Notebook

Open the project folder in Visual Studio Code. Open
`notebooks/EDA_Analysis.ipynb`, select the Python interpreter from the
project's `.venv` environment, and run the notebook cells in order.

**Note:** The notebook uses relative file paths based on the project
folder structure. Keep `data/`, `notebooks/`, and `outputs/` in their
documented locations when running it.

## Project Deliverables

-   **Jupyter Notebook:** Complete EDA workflow and code.
-   **Original Dataset:** Source retail customer sales CSV.
-   **Cleaned Dataset:** Validated dataset containing 7,000 rows and 27
    columns.
-   **Visual Outputs:** Histograms, box plots, and business analysis
    charts.
-   **Insights Report:** Statistical results, visual analysis, business
    findings, and validation.
-   **Project Synopsis:** Problem, objectives, requirements,
    methodology, and outcomes.

## Author

**Ajay Pratap Singh Chauhan**\
MCA \| Data Analytics\
Roll Number: `2026M01410010`

------------------------------------------------------------------------

*This repository contains an academic data analytics project prepared as
part of the HCLTech Career Shaper Program.*
