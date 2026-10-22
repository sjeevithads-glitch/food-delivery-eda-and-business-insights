# food-delivery-eda-and-business-insights
Exploratory Data Analysis of Chennai food delivery orders using Python, including data cleaning, missing value treatment, outlier detection, correlation analysis, delivery performance insights, and business recommendations.



This project analyzes food delivery order data from Chennai to uncover patterns in customer orders, delivery performance, restaurant preparation times, and operational efficiency.

The project focuses on:

- Data Cleaning
- Missing Value Handling
- Duplicate Removal
- Data Standardization
- Statistical Analysis
- Outlier Detection
- Correlation Analysis
- Delivery Performance Insights
- Business Recommendations

---

## Business Objective

Food delivery platforms need to optimize delivery times and improve customer satisfaction.

This analysis aims to identify:

- Areas with slower deliveries
- Restaurant types with longer preparation times
- Delivery delays
- Data quality issues
- Opportunities for operational improvement

---

## Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn

---

## Dataset Features

The dataset contains information about:

- Order Value
- Delivery Time
- Preparation Time
- Customer Ratings
- Restaurant Type
- Delivery Area

---

## Data Cleaning

### Missing Value Analysis

```python
df.isna().mean() * 100
```

Calculated missing value percentages for each column.

### Missing Value Treatment

```python
df.fillna(method='ffill', inplace=True)
```

Forward fill was used to impute missing values.

### Duplicate Detection

```python
df.duplicated().sum()
```

Duplicate records were identified.

### Duplicate Removal

```python
df = df.drop_duplicates()
```

Removed duplicate observations from the dataset.

---

## Data Standardization

Area names contained inconsistent formatting.

Examples:

```text
OMR
Omr
O.M.R
```

These values were standardized:

```python
df['area'] = df['area'].replace({
    'Omr':'OMR',
    'O.M.R':'OMR'
})
```

This improves reporting accuracy.

---

## Descriptive Statistics

For all numerical variables the following metrics were calculated:

- Mean
- Median
- Mode
- Standard Deviation
- Minimum
- Maximum
- Skewness

### Statistics Generated

```python
Mean
Median
Mode
Standard Deviation
Minimum
Maximum
Skewness
```

These metrics help understand the underlying distribution of the data.

---

## Distribution Analysis

Histograms were used to analyze distributions of:

### Order Value

```python
plt.hist(df['order_value'])
```

### Delivery Time

```python
plt.hist(df['delivery_time_min'])
```

Used to identify:

- Typical order values
- Delivery time spread
- Potential skewness

---

## Outlier Detection

Outliers were detected using the Interquartile Range (IQR) method.

### Formula

```text
IQR = Q3 - Q1
```

### Outlier Boundaries

```text
Lower Fence = Q1 - 1.5 × IQR

Upper Fence = Q3 + 1.5 × IQR
```

Analyzed features:

- Delivery Time
- Order Value
- Rating

Boxplots were generated to visualize:

- Quartiles
- Whiskers
- Outliers

---

## Correlation Analysis

A correlation matrix was created for numerical variables.

```python
corr = df.corr(numeric_only=True)
```

### Heatmap

A Seaborn heatmap was used to visualize relationships between variables.

This helps identify:

- Strong correlations
- Weak correlations
- Potential drivers of delivery performance

---

## Business Insights

### 1. Slowest Delivery Area

```python
slowest_area =
df.groupby("area")
['delivery_time_min']
.mean()
.idxmax()
```

Identifies areas with the highest average delivery time.

### 2. Restaurant Type with Longest Preparation Time

```python
df.groupby("restaurant_type")
['prep_time_min']
.mean()
.idxmax()
```

Identifies restaurant categories causing delays.

### 3. Probability of Delayed Delivery

```python
(df['delivery_time_min'] > 45).mean()
```

Calculates the probability that delivery exceeds 45 minutes.

---

## Key Learnings

This project demonstrates:

- Data Cleaning Techniques
- Missing Value Imputation
- Data Standardization
- Exploratory Data Analysis (EDA)
- Statistical Analysis
- Outlier Detection Using IQR
- Correlation Analysis
- Business-Oriented Insights

---

## Future Enhancements

- Interactive Power BI Dashboard
- Delivery Time Prediction Model
- Demand Forecasting
- Customer Segmentation
- Restaurant Performance Scorecard
- Geographic Visualization of Delivery Areas

---

## Author

Jeevitha S


This project is particularly good for demonstrating EDA, statistics, data cleaning, and business analysis skills, while your Telecom Churn project demonstrates machine learning and predictive analytics. Having both on GitHub gives you a stronger portfolio.
