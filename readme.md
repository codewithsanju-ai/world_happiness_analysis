# Global Happiness Report Analysis

**A Python-Based Data Analysis and Visualization Project Using Pandas, NumPy, Matplotlib, and Seaborn**

Global Happiness Report Analysis is a data analytics project that explores happiness scores and their associated economic, social, health, and freedom-related indicators across countries and geographical regions.

Using Python's data analysis and visualization libraries, this project performs data inspection, data quality checks, statistical analysis, regional comparisons, correlation analysis, and outlier exploration to identify meaningful patterns within the dataset.

---

## Table of Contents

- [Project Overview](#project-overview)
- [Key Features](#key-features)
- [Technologies Used](#technologies-used)
- [Dataset Description](#dataset-description)
- [Analysis Performed](#analysis-performed)
- [Data Visualization](#data-visualization)
- [Python Concepts Used](#python-concepts-used)
- [Project Structure](#project-structure)
- [Installation and Setup](#installation-and-setup)
- [How to Run](#how-to-run)
- [Learning Outcomes](#learning-outcomes)
- [Future Enhancements](#future-enhancements)
- [Author](#author)
- [License](#license)

## Project Overview

The objective of this project is to analyze a Global Happiness Report dataset and explore how happiness scores vary across countries and regions.

The project uses Pandas for data manipulation, NumPy for numerical operations, Matplotlib for plotting, and Seaborn for statistical visualization.

The analysis focuses on understanding regional happiness levels, examining relationships between numerical indicators, identifying potential data quality issues, and interpreting statistical patterns.

### Project Objectives

- Explore and understand the structure of the dataset.
- Identify missing values and duplicate records.
- Analyze numerical and categorical columns.
- Calculate average happiness scores by region.
- Compare regional GDP per capita indicators.
- Explore correlations between happiness-related factors.
- Investigate the relationship between GDP per capita and life expectancy.
- Examine happiness score distributions and potential outliers.
- Communicate findings through appropriate visualizations.

## Key Features

### 1. Data Loading and Inspection
- Import the dataset from a CSV file.
- Display dataset records and column names.
- Inspect data types using `dtypes`.
- Separate numerical and categorical columns.
- Generate descriptive statistics using `describe()`.
- Review dataset structure using `info()`.

### 2. Data Quality Analysis
- Identify missing values using `isna()`.
- Count missing values in each column.
- Detect duplicate records using `duplicated()`.
- Inspect data quality before further analysis.

### 3. Regional Happiness Analysis
- Group countries by geographical region.
- Calculate the average Happiness Score.
- Compare regional averages using a bar chart.
- Identify differences in happiness scores across regions.

### 4. Regional Economic Analysis
- Calculate the average GDP per capita indicator by region.
- Visualize regional economic indicator values using a pie chart.
- Explore differences in the dataset's economic measurements across regions.

### 5. Country-Level Filtering
- Filter countries belonging to a selected region.
- Display relevant country names, regions, and happiness scores.
- Practice conditional selection using Pandas `.loc[]`.

### 6. Correlation Analysis
- Calculate correlations among numerical columns.
- Visualize correlation coefficients with a heatmap.
- Explore positive and negative linear relationships between indicators.

### 7. GDP and Life Expectancy Analysis
- Compare Economy (GDP per Capita) with Health (Life Expectancy).
- Use a scatter plot to examine relationships between the two indicators.
- Identify visible patterns and variation across countries.

### 8. Outlier Exploration
- Compare Happiness Score distributions across regions.
- Use box plots to identify potential outliers.
- Examine differences in regional score distributions.

## Technologies Used

| Technology | Purpose |
|---|---|
| Python | Core programming language |
| Pandas | Data loading, filtering, grouping, and aggregation |
| NumPy | Numerical operations and array support |
| Matplotlib | Creating charts and customizing plots |
| Seaborn | Statistical visualization and correlation heatmaps |
| Jupyter Notebook | Interactive analysis and experimentation |

## Dataset Description

The project uses a CSV dataset named `happiness_report.csv` containing country-level happiness scores and related indicators.

| Column | Description |
|---|---|
| `Country` | Name of the country |
| `Region` | Geographical region |
| `Happiness Rank` | Country's happiness ranking |
| `Happiness Score` | Overall happiness score |
| `Standard Error` | Standard error associated with the happiness score |
| `Economy (GDP per Capita)` | GDP-related economic indicator |
| `Family` | Family and social support indicator |
| `Health (Life Expectancy)` | Health and life expectancy indicator |
| `**Freedom` | Freedom-related indicator; verify the exact CSV column name |
| `**Trust (Government Corruption)` | Trust and government corruption indicator; verify the exact CSV column name |

**Note:** The provided dataset text contains formatting artifacts in the Freedom and Trust column names. Use the exact column names from your actual CSV file.

## Analysis Performed

### 1. Dataset Inspection

The dataset is loaded into a Pandas DataFrame and examined using common inspection methods.

```python
df = pd.read_csv("happiness_report.csv")

print(df.columns)
print(df.dtypes)
print(df.describe())
df.info()
```

This helps understand the dataset's structure, data types, and statistical characteristics.

### 2. Missing Value Analysis

Missing values are inspected across all columns.

```python
print(df.isna().sum())
```

This identifies columns that may need additional cleaning.

### 3. Duplicate Record Detection

Duplicate rows are identified for further inspection.

```python
print(df[df.duplicated()])
```

This helps detect repeated records without automatically deleting potentially meaningful data.

### 4. Average Happiness Score by Region

The average Happiness Score is calculated for each region.

```python
region_happiness = (
    df.groupby("Region")["Happiness Score"]
      .mean()
      .reset_index()
)
```

**Objective:** Compare average happiness levels across geographical regions.

### 5. Regional GDP Analysis

The average GDP per capita indicator is calculated for each region.

```python
region_gdp = (
    df.groupby("Region")["Economy (GDP per Capita)"]
      .mean()
      .reset_index()
)
```

**Objective:** Explore regional differences in the economic indicator.

### 6. Regional Country Filtering

Countries from Western Europe are selected using conditional filtering.

```python
western_europe = df.loc[
    df["Region"] == "Western Europe",
    ["Country", "Region", "Happiness Score"]
]

print(western_europe)
```

**Objective:** Practice filtering records and selecting specific columns.

### 7. Numerical Correlation Analysis

A correlation matrix is calculated using numerical columns.

```python
corr = df.corr(numeric_only=True)
```

**Objective:** Examine the linear relationships between numerical indicators.

### 8. GDP vs Life Expectancy

A scatter plot compares GDP per capita with the health and life expectancy indicator.

```python
sns.scatterplot(
    data=df,
    x="Economy (GDP per Capita)",
    y="Health (Life Expectancy)"
)

plt.title("GDP vs Life Expectancy")
plt.tight_layout()
plt.show()
```

**Objective:** Explore whether higher GDP-related indicator values tend to occur alongside higher health indicator values.

### 9. Happiness Score Distribution by Region

A box plot compares the distribution of Happiness Scores across regions.

```python
sns.boxplot(
    data=df,
    x="Region",
    y="Happiness Score"
)

plt.title("Happiness Score Distribution by Region")
plt.xticks(rotation=90)
plt.tight_layout()
plt.show()
```

**Objective:** Compare regional distributions, medians, variability, and potential outliers.

## Data Visualization

The project includes the following visualizations:

| Visualization | Purpose |
|---|---|
| Bar Chart | Compare average Happiness Scores across regions |
| Pie Chart | Display regional shares of average GDP indicator values |
| Heatmap | Visualize correlations among numerical indicators |
| Scatter Plot | Explore the relationship between GDP and life expectancy |
| Box Plot | Compare score distributions and investigate potential outliers |

These visualizations complement the statistical analysis and help communicate patterns in the dataset.

## Python Concepts Used

- Reading CSV files with Pandas.
- Creating and inspecting DataFrames.
- Selecting columns by data type.
- Descriptive statistics and summary methods.
- Missing value and duplicate detection.
- Boolean indexing and `.loc[]`.
- Grouping and aggregation with `groupby()`.
- Correlation analysis with `.corr()`.
- Creating and customizing Matplotlib plots.
- Using Seaborn for statistical visualization.
- Interpreting distributions and potential outliers.

## Project Structure

```text
Global-Happiness-Report-Analysis/
│
├── happiness_report.csv
├── main.ipynb
└── README.md
```

- `happiness_report.csv` — Dataset used for the analysis.
- `main.ipynb` — Jupyter Notebook containing data inspection, analysis, and visualizations.
- `README.md` — Project documentation.

*Replace `main.ipynb` with your actual notebook or Python filename if it differs.*

## Installation and Setup

### Prerequisites

- Python 3.10 or later recommended.
- pip package manager.
- Visual Studio Code or Jupyter Notebook.

### Step 1: Clone the Repository

```bash
git clone <your-repository-url>
```

Replace `<your-repository-url>` with your GitHub repository URL.

### Step 2: Navigate to the Project Folder

```bash
cd Global-Happiness-Report-Analysis
```

### Step 3: Install Required Libraries

```bash
python -m pip install pandas numpy matplotlib seaborn jupyter
```

### Step 4: Open the Project

Open the project folder in Visual Studio Code or start Jupyter Notebook.

```bash
jupyter notebook
```

### Step 5: Load the Dataset

Keep `happiness_report.csv` in the project folder and load it using:

```python
import pandas as pd

df = pd.read_csv("happiness_report.csv")
```

### Step 6: Run the Analysis

Execute the notebook cells in order to inspect the data, perform the analysis, and generate the visualizations.

## Learning Outcomes

By completing this project, you can practice:

- Data exploration and preliminary data cleaning.
- Working with numerical and categorical data.
- Applying Pandas grouping and aggregation methods.
- Performing correlation analysis.
- Creating and interpreting different chart types.
- Exploring relationships among happiness-related indicators.
- Identifying potential outliers using statistical visualizations.
- Presenting data-driven observations in a structured format.

## Future Enhancements

- Add Top 10 and Bottom 10 country comparisons.
- Compare regional averages for GDP, Family, Health, and Freedom.
- Create separate scatter plots for multiple happiness-related indicators.
- Add histograms and distribution plots.
- Implement an improved data-cleaning workflow.
- Add validation for missing columns and unexpected data types.
- Export summary statistics and findings to CSV or Excel.
- Build an interactive dashboard using Streamlit or Plotly.
- Generate an automated report containing key observations.

## Limitations

- Correlation indicates association, not causation.
- Regional averages may hide differences between individual countries.
- Potential outliers require investigation before any removal.
- The findings are limited to the supplied dataset and its coverage.
- The dataset appears to correspond to the 2015 World Happiness Report; verify its source and year before presenting conclusions.

## Author

**Sanjay Kushwaha**

Python Learner | Data Analysis Enthusiast

## License

This project was created for educational and learning purposes. You may adapt and extend it for personal learning and further development.
