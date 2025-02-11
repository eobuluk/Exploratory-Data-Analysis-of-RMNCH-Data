# Exploratory Data Analysis of Maternal and Child Health Data
Exploratory Data Analysis (EDA) was conducted to better understand the RMNCH dataset and uncover key trends in reproductive, maternal, newborn, and child health. By exploring the data, I aimed to gain insights into the distribution and trends of essential health indicators like antenatal care (ANC) visits and deliveries, which are vital to improving maternal and child health outcomes in Southwest Uganda. The following steps outline the EDA process:

## Summary Statistics:
The first step was to generate summary statistics for the numerical columns in the dataset. This helped to identify the central tendencies, spread, and potential outliers in key variables such as ANC visits, deliveries, and postnatal care.

Below is the Python code that was used to generate the summary statistics:
```python
# Get summary statistics for numerical columns
df.describe()
```
![Summary Statistics Table](results/Summary_Statistics_Output.jpg)

This provided a high level overview of the RMNCH indicators. The key findings included:

- The average number of first ANC visits for women was 2,729, with significant regional variations from 852 to 7,258.
- On average, 777 women attended their first ANC visit in the first trimester, while some regions reported fewer visits.
- On average, 2,197 women received iron/folic acid during their first ANC visit, though regional disparities existed.
- An average of 3 maternal deaths were audited, and some regions reported no audits.
- For perinatal deaths audited, the average was 25.7, with large regional differences.
- On average, 294 caesarian sections were performed, with variation from region to region.

### Distribution of Total Antenatal care (ANC) Visits:
Antenatal care (ANC) visits is one of the key RMNCH indicators. I visualized the total number of ANC visits using a histogram with a kernel density estimate (KDE) in order to understand the distribution of this variable. Below is the Python code that was used to plot the distribution of the total ANC visits (New clients + Re-attendances):
```python
%matplotlib inline
import matplotlib.pyplot as plt
import seaborn as sns
# Set plot style
sns.set(style="whitegrid")
# Plot the distribution of 'Total ANC visits (New clients + Re-attendances)'
plt.figure(figsize=(10, 6))
sns.histplot(df['105-2.1 a3:total anc visits (new clients + re-attendances)'], kde=True, color='blue')
plt.title('Distribution of Total ANC Visits')
plt.xlabel('Total ANC Visits')
plt.ylabel('Frequency')
plt.show()
```
![Distribution of Total ANC Visits](results/Total_ANC_Visits.jpg)

### Trend of First Antenatal care (ANC) Visits:
To examine changes in access to maternal health services over time, I analyzed the trend of first antenatal care (ANC) visits for women across different years. The analysis grouped data by region to show variations in first ANC visits, a key indicator of access to maternal healthcare services. Below is the Python code that was used to plot the trend of first Antenatal care (ANC) visits:
```python
# Plot the trend of 'ANC 1st Visit for women' over the years
plt.figure(figsize=(10, 6))
sns.lineplot(data=df, x='year', y='105-2.1 a1:anc 1st visit for women', hue='region', marker='o')
plt.title('Trend of first Antenatal care visits by region')
plt.xlabel('Year')
plt.ylabel('ANC 1st Visit for Women')
plt.show()
```
![Trend of First ANC Visits](results/First_ANC_Visits.jpg)

## Data Quality Issues:
Upon reviewing the dataset, the following data quality concerns were identified and addressed:

## Missing Values:
Found in critical fields such as antenatal care visits and delivery records. Action Taken: Missing values were replaced with zeros for continuity in analysis, with consideration given to their implications for data integrity.

## Outliers:
Detected unusual spikes in indicators like Total ANC Visits and Deliveries. Action Taken: Flagged for further investigation to determine whether these represent data collection errors or meaningful anomalies.

## Inconsistent Formats:
Irregular date formats in the Period column hindered temporal analysis. Action Taken: Standardized all date formats to ensure consistency and enable accurate trend analysis. By resolving these issues, the dataset was refined to ensure accuracy and reliability, providing a strong foundation for deeper analysis.
