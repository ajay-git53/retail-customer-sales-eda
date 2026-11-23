# Retail Customer Sales -- Exploratory Data Analysis (EDA)

A Python-based Exploratory Data Analysis project on retail customer
sales transactions from 2023--2024. This project focuses on data quality
assessment, data cleaning, statistical profiling, outlier detection,
feature engineering, visualisation, and business-oriented analysis.

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
-   [How to Run the Project](#how-to-run-the-project)
-   [Project Files](#project-files)
-   [Author](#author)

## Project Overview

Retail businesses generate data related to customers, products,
transactions, payments, sales, costs, profits, deliveries, and customer
satisfaction. Analysing this information can help identify sales
patterns, understand customer segments, compare product and regional
performance, and support informed business decisions.

This project performs Exploratory Data Analysis (EDA) on a retail
customer sales dataset covering 2023--2024. The original dataset
contains **7,084 rows and 24 columns**. After data cleaning and feature
engineering, the final analytical dataset contains **7,000 rows and 27
columns**.

The project is implemented in Python using a Jupyter Notebook. It
includes the original dataset, cleaned dataset, visual outputs, an
insights report, and a project synopsis.

## Objectives

-   Inspect the dataset structure, columns, data types, and summary
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
-   Present findings through charts and a written insights report.

## Dataset Description

  Attribute                   Details
  --------------------------- -------------------------------------
  Dataset file                `retail_customer_sales_dataset.csv`
  Period covered              2023--2024
  Original dimensions         7,084 rows × 24 columns
  Final cleaned dimensions    7,000 rows × 27 columns
  Original dataset location   `data/`
  Cleaned dataset location    `outputs/`

The dataset contains transaction-level retail information, including
customer details, product information, order and delivery dates, payment
information, sales, cost, profit, ratings, and satisfaction details.

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

The repository is organised as follows:

``` text
EDA_Project_2026M01410010/
│
├── data/
│   └── retail_customer_sales_dataset.csv
│
├── notebooks/
│   └── EDA_Analysis.ipynb
│
├── outputs/
│   ├── age_boxplot.png
│   ├── average_customer_rating_by_category.png
│   ├── cleaned_retail_customer_sales.csv
│   ├── income_boxplot.png
│   ├── numerical_histograms.png
│   ├── profit_boxplot.png
│   ├── sales_boxplot.png
│   ├── sales_by_customer_segment.png
│   ├── sales_by_payment_method.png
│   ├── sales_by_product_category.png
│   └── sales_by_region.png
│
├── reports/
│   └── Insights_Report.docx
│
├── .gitignore
├── 2026M01410010_Ajay_Pratap_Singh_Chauhan_Retail_Customer_Sales_EDA_Project_Synopsis.docx
└── README.md
```

## Analysis Workflow

The project follows these stages:

1.  **Data loading and inspection:** Load the CSV and inspect
    dimensions, columns, data types, descriptive summaries, missing
    values, and duplicates.
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

The cleaning process documented in the notebook includes:

-   Removing exact duplicate rows.
-   Standardising inconsistent `Gender` and `Region` labels.
-   Treating `Age` values outside the range 18--100 as invalid.
-   Treating `Discount` values outside the range 0--1 as invalid.
-   Imputing missing numerical values using the median.
-   Filling missing `Satisfaction_Level` values using the mode.
-   Parsing date fields and checking delivery dates against order dates.
-   Handling missing delivery dates using the median delivery interval.
-   Rechecking duplicate rows after categorical standardisation.

Potential outliers are not automatically removed. They are retained
where there is no separate evidence that the values are erroneous, since
unusually high values may represent genuine customer or transaction
behaviour.

## Exploratory Data Analysis

### Numerical Analysis

Descriptive statistics are calculated for the following eight numerical
variables:

-   `Age`
-   `Income`
-   `Quantity`
-   `Unit_Price`
-   `Discount`
-   `Sales`
-   `Cost`
-   `Profit`

The statistical measures include mean, median, mode, standard deviation,
variance, quartiles, Interquartile Range (IQR), 90th percentile (P90),
and 95th percentile (P95).

### Univariate Analysis

The notebook examines numerical distributions for `Age`, `Income`,
`Sales`, and `Profit` using histograms and box plots. It also explores
categorical distributions for `Gender`, `Region`, `Product_Category`,
`Customer_Segment`, and `Payment_Method`.

## Outlier Detection

Potential outliers are identified using the Interquartile Range method:

-   `IQR = Q3 − Q1`
-   Lower bound = `Q1 − 1.5 × IQR`
-   Upper bound = `Q3 + 1.5 × IQR`

The outlier counts calculated on the final 7,000-row dataset are:

  Variable     IQR Outlier Count
  ---------- -------------------
  Age                         10
  Income                     278
  Sales                      632
  Profit                     640

These counts represent observations outside the IQR thresholds. They do
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

### Additional Customer Segment Analysis

The notebook also compares total sales by customer segment. This is a
different measure from average transaction sales. Corporate has the
highest **average transaction sales**, while Consumer has the highest
**aggregate segment sales** in the analysed dataset. These findings
should be interpreted separately.

## Data Validation

The final cleaned dataset passed the following checks:

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

Replace `YOUR-USERNAME` with your GitHub username:

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
.venv\Scripts\activate
```

### 3. Install the Required Libraries

``` bash
pip install pandas numpy matplotlib seaborn missingno jupyter
```

### 4. Open and Run the Notebook

1.  Open the cloned project folder in Visual Studio Code.
2.  Open `notebooks/EDA_Analysis.ipynb`.
3.  Select the Python interpreter from the environment you created.
4.  Run the notebook cells in order.

**Important:** The notebook uses relative paths based on the repository
layout. Keep the `data/`, `notebooks/`, and `outputs/` folders in the
locations shown above. If you run the notebook from a different working
directory, its relative file paths may need adjustment.

## Project Files

-   **`notebooks/EDA_Analysis.ipynb`** --- Main notebook containing the
    data loading, cleaning, analysis, visualisation, and validation
    workflow.
-   **`data/retail_customer_sales_dataset.csv`** --- Original source
    dataset.
-   **`outputs/cleaned_retail_customer_sales.csv`** --- Final cleaned
    dataset.
-   **`outputs/*.png`** --- Generated box plots, histograms, and
    business analysis charts.
-   **`reports/Insights_Report.docx`** --- Project insights report.
-   **`2026M01410010_Ajay_Pratap_Singh_Chauhan_Retail_Customer_Sales_EDA_Project_Synopsis.docx`**
    --- Formal project synopsis.
-   **`.gitignore`** --- Specifies files and folders excluded from Git
    tracking.

## Author

**Ajay Pratap Singh Chauhan**\
MCA \| Data Analytics\
Roll Number: `2026M01410010`

------------------------------------------------------------------------

*Academic project prepared as part of the HCLTech Career Shaper
Program.*
