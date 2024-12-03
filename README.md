# HIV Knowledge and AIDS-Related Deaths Analysis

This repository contains a Python script that analyzes the relationship between **comprehensive, correct knowledge of HIV** and **annual AIDS-related deaths** in the **West and Central Africa** region. The data is extracted from the `preAdo_DF` and `Epid_DF` datasets, which contain information on HIV knowledge and AIDS-related deaths by age, sex, and year.

## Purpose
The purpose of this analysis is to examine whether there is a correlation between the level of education (knowledge of HIV) and the number of annual AIDS-related deaths in the West and Central Africa region. We focus on the age group of **15-19 years** and analyze how sex and year affect the relationship between these two indicators.

## Dataset Description

1. **`preAdo_DF` Dataset**:
   - Contains data on the percentage of the population with comprehensive, correct knowledge of HIV by various disaggregation categories (age, sex, education, marital status, residence, wealth quintile, etc.).
   
2. **`Epid_DF` Dataset**:
   - Contains data on the estimated number of annual AIDS-related deaths, as well as the estimated number of people living with HIV, broken down by age group, sex, and region.

## Steps

### 1. **Data Filtering**:
   We filter the datasets for the region "West and Central Africa", focusing on the following:
   - The indicator for **comprehensive, correct knowledge of HIV** (`preAdo_DF`).
   - The indicator for **annual AIDS-related deaths** (`Epid_DF`).
   - Age group **15-19** years.
   - The analysis excludes "Both" sex category to examine the relationship separately for male and female populations.

### 2. **Data Merging**:
   - We merge the filtered datasets (`preAdo_DF` and `Epid_DF`) on common columns: **Year** and **Sex**.
   - This merge allows us to compare the percentage of individuals with correct HIV knowledge (education) with the number of annual AIDS-related deaths for each year and sex.

### 3. **Pearson Correlation**:
   - A **Pearson correlation** is calculated between two columns:
     - **Education**: Percentage with comprehensive, correct knowledge of HIV.
     - **Death**: Number of annual AIDS-related deaths.
   - The correlation tells us whether there is a linear relationship between the level of education and the number of deaths due to AIDS.

### 4. **Interpretation**:
   - The Pearson correlation value will help understand if **better HIV education** correlates with **fewer AIDS-related deaths**.
   - A **negative correlation** suggests that higher education levels (knowledge of HIV) could be associated with fewer deaths, supporting the idea that increasing HIV education could potentially reduce AIDS-related mortality.

## Code Breakdown

### 1. **Data Filtering**:
   The datasets are filtered for the required conditions, focusing on "West and Central Africa", age group **15-19**, and excluding "Both" sex for detailed analysis by sex.

```python
DF1 = preAdo_DF[
    (preAdo_DF["UNICEF Region"] == "West and Central Africa") &  # Filter by region: West and Central Africa
    (preAdo_DF["Indicator"] == "Per cent with comprehensive, correct knowledge of HIV") &  # Filter by indicator: HIV knowledge
    (preAdo_DF["Sex"] != "Both") &  # Exclude "Both" sex category
    (preAdo_DF["DISAGG_CATEGORY"] == "Age") &  # Filter by age disaggregation
    (preAdo_DF["DISAGG"] == "15-19")  # Focus on age group 15-19
]
