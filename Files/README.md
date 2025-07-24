# 🌍 External Debt Analysis (Excel-Based Analysis)

This project presents an interactive and advanced Excel analysis with graphical representations, analysing external debt trends using data from the World Bank's International Debt Statistics (IDS). The project focuses on debt sustainability, regional risk comparison, and key financial indicators such as debt-to-GNI ratios and reserve adequacy

---

## 📊 Project Objective

To explore how external debt has evolved across low and middle-income countries between 2013 and 202, and assess their debt sustainability through key indicators such as:
- Total external debt
- Debt-to-GNI ratios
- Regional and income group comparisons
- Total reserves and debt servicing capacity

---

## 🧰 Tools Used

- **Microsoft Excel**: Core tool for data analysis and visualization
- **Power Query**: Used to clean and transform raw data
- **Power Pivot**: Used to model data relationships and create DAX measures
- **PivotTables and PivotCharts**: Used to create dynamic visuals and trends
- **DAX Measures**: Used to calculate total debt, further filter the values, and ratios like Debt-to-GNI

---

## 📁 Excel File Components

| Sheet Name | Description |
|------------|-------------|
| `Top 10 countries` | Highlights the top 10 countries with the highest external debt in the most recent year and past year with a slicer |
| `Debt to GNI` | Tracks debt sustainability over time by comparing total debt to GNI (national income) across regions |
| `Sub-Saharan VS South Asia` | Regional analysis comparing external debt trends between Sub-Saharan Africa and South Asia |
| `Income Group` | Breaks down borrowing patterns by World Bank income classification (low, lower-middle, upper-middle) |
| `Total Reserves` | Examines countries’ total reserves vs debt obligations to assess repayment capacity |

---

## 📌 Key Questions Answered

1. **Which countries hold the highest external debt?**
2. **How has the debt-to-GNI ratio evolved across time and regions? **
3. **Are Sub-Saharan African countries accumulating more debt than South Asia?**
4. **What income level has the highest debt?**
5. **How do reserves compare to debt service, and what does that say about solvency? **


## 🔧 Analysis Breakdown

### 📌 1. Data Cleaning (Power Query)
- Imported the **International Debt Statistics (IDS)** dataset from an Excel file after downloading from the World Bank, using **Get and Transform Data**.
- Selected the Data and Country – metadata table and clicked transform to clean the data in the data query editor.

 ![](https://github.com/Codesbyeni/EXternal-Debt-Analysis/blob/49f233eedf1230a43eb81b2b752db28656fc3c06/Debt%20Analysis%20Git/Screenshot%202025-06-27%20154926.png)
- Removed the Counterpart-Area Name and Counterpart-Area Code columns because it was repetitive and not relevant for this analysis. Also removed the columns for the years 1970 – 2000 because it is irrelevant for the purpose of this analysis, and I removed the years 2026 – 2031 because I didn’t want to deal with the forecast for this analysis.

![](https://github.com/Codesbyeni/EXternal-Debt-Analysis/blob/49f233eedf1230a43eb81b2b752db28656fc3c06/Debt%20Analysis%20Git/Screenshot%202025-06-27%20160540.png) 
- Unpivoted wide-format year columns (`1970–2031`) into two tidy columns:  
  ` Year | Value` This makes it easier to analyse the values.

 ![](https://github.com/Codesbyeni/EXternal-Debt-Analysis/blob/49f233eedf1230a43eb81b2b752db28656fc3c06/Debt%20Analysis%20Git/Screenshot%202025-06-27%20160755.png)
- Filtered to retain only relevant indicators:
I went through the Series – Metadata table and selected 14 out of …series that I found relevant to this analysis. Using the series code, I filtered the series code column, keeping the relevant series. Some of these series include:
  - `DT.DOD.DECT.CD` — *External debt stocks, total (current US$)*
  - `DT.TDS.DECT.CD`— *Total Debt Service (Current US$)*
  - `FI.RES.TOTL.CD` — *Total reserves (current US$)*

 ![](https://github.com/Codesbyeni/EXternal-Debt-Analysis/blob/49f233eedf1230a43eb81b2b752db28656fc3c06/Debt%20Analysis%20Git/Screenshot%202025-06-27%20163535.png)

- loaded the `"Country - Metadata"` sheet in the Power Query editor, cleaned the data and filtered the code column for codes that are do not refer to countries or regions.

 ![](https://github.com/Codesbyeni/EXternal-Debt-Analysis/blob/49f233eedf1230a43eb81b2b752db28656fc3c06/Debt%20Analysis%20Git/Screenshot%202025-07-11%20141720.png)
I loaded the data and added it to the data model.



### 📌 2. Data Modelling (Power Pivot)
- Created relationships between:
  - `Debt Data` table and `Country Metadata` table (via `Country Code`)
    
   ![](https://github.com/Codesbyeni/EXternal-Debt-Analysis/blob/49f233eedf1230a43eb81b2b752db28656fc3c06/Debt%20Analysis%20Git/Screenshot%202025-06-27%20164429.png)
 - Defined key **DAX measures**, such as:
  - `Total Debt (Country)`
    
  ![](https://github.com/Codesbyeni/EXternal-Debt-Analysis/blob/49f233eedf1230a43eb81b2b752db28656fc3c06/Debt%20Analysis%20Git/Screenshot%202025-07-11%20150943.png)
  - `Total GNI (Region)`
    
  ![](https://github.com/Codesbyeni/EXternal-Debt-Analysis/blob/49f233eedf1230a43eb81b2b752db28656fc3c06/Debt%20Analysis%20Git/Screenshot%202025-07-11%20151338.png)
  - `Debt-to-GNI Ratio (region)`
    
  ![](https://github.com/Codesbyeni/EXternal-Debt-Analysis/blob/49f233eedf1230a43eb81b2b752db28656fc3c06/Debt%20Analysis%20Git/Screenshot%202025-07-11%20151434.png)
  - `Debt Service (country)`
   
- Created a calculated column (`IsCountry`) to filter region aggregates when needed
  
  ![](https://github.com/Codesbyeni/EXternal-Debt-Analysis/blob/49f233eedf1230a43eb81b2b752db28656fc3c06/Debt%20Analysis%20Git/Screenshot%202025-07-11%20152555.png)


### 📌 3. Visualisation (PivotTables & Charts)
Created an Excel dashboard with interactive visuals:

| Sheet Name               | Focus                                         |
|--------------------------|-----------------------------------------------|
| `Top 10 countries`       | Bar chart showing top 10 debtor countries     |
| `Debt to GNI`            | Year-over-year comparison of debt as % of GNI |
| `Sub Saharan VS South Asia` | Regional debt trend comparison           |
| `Income Group`           | Borrowing patterns by income classification   |
| `Total Reserves`         | Comparison of debt vs reserve adequacy        |

---
![](https://github.com/Codesbyeni/EXternal-Debt-Analysis/blob/49f233eedf1230a43eb81b2b752db28656fc3c06/Debt%20Analysis%20Git/Screenshot%202025-07-15%20125931.png)
## 📊 Key Findings

### 🔹 Top 10 Debtor Countries
 
 ![](https://github.com/Codesbyeni/EXternal-Debt-Analysis/blob/49f233eedf1230a43eb81b2b752db28656fc3c06/Debt%20Analysis%20Git/Screenshot%202025-07-16%20114224.png)
- Countries like **China**, **India**, **Brazil**, and **Mexico** have the highest external debt in absolute terms.
- However, high debt does not always imply high vulnerability — income and reserves matter.

### 🔹 Debt-to-GNI Ratio Insights

 ![](https://github.com/Codesbyeni/EXternal-Debt-Analysis/blob/49f233eedf1230a43eb81b2b752db28656fc3c06/Debt%20Analysis%20Git/Screenshot%202025-07-16%20114236.png)
- The Debt to GNI Ratio has changed over the years. It's a way to assess a nation's ability to manage its debt obligations. 
- The **East Asia and Pacific** region has the lowest ratio of **17%** which suggests a sustainable debt situation.  **Europe and Central Asia**, followed by **Sub-Saharan** Africa, have the highest ratio of **54%** and **44%** respectively, indicating potential risks. 

### 🔹 Regional Debt Patterns

 ![](https://github.com/Codesbyeni/EXternal-Debt-Analysis/blob/49f233eedf1230a43eb81b2b752db28656fc3c06/Debt%20Analysis%20Git/Screenshot%202025-07-16%20114305.png)
- **Sub-Saharan Africa** is rapidly accumulating external debt, nearly **doubling** from **2013 to 2023**, indicating rising borrowing needs but also increasing vulnerability to debt distress, especially given weaker economic buffers and reliance on non-concessional loans.
- **South Asia**’s debt is growing more gradually, suggesting a more stable borrowing pattern led by India, with relatively stronger income and reserves to support
- The two regions are now separated by less than $100B, compared to 0ver $100B in 2013.
- **Sub-Saharan Africa** saw rapid debt growth post-2010, likely from infrastructure loans and bilateral borrowing.
- **South Asia**, led by India, saw more stable growth in both debt and GNI.

### 🔹 Income Group Trends

 ![](https://github.com/Codesbyeni/EXternal-Debt-Analysis/blob/49f233eedf1230a43eb81b2b752db28656fc3c06/Debt%20Analysis%20Git/Screenshot%202025-07-16%20114318.png)
- **Lower-middle income countries** accumulated the largest share of debt, highlighting expanded borrowing access but also greater exposure to repayment challenges.
- **Upper-middle income **, which contains only china, maintained stronger debt service capabilities.

### 🔹 Reserves vs Debt

 ![](https://github.com/Codesbyeni/EXternal-Debt-Analysis/blob/49f233eedf1230a43eb81b2b752db28656fc3c06/Debt%20Analysis%20Git/Screenshot%202025-07-16%20114344.png)
- **China and India** hold significantly larger foreign reserves than the rest, with China exceeding **$3.5T**, indicating strong financial buffers to cover external obligations, especially in contrast to their relatively low debt service burden.
- Countries **like Thailand, Mexico, and Indonesia** maintain modest reserves while managing relatively higher debt service levels, signalling greater liquidity pressure and reduced fiscal flexibility if external shocks or repayment spikes occur.
---


## 🔍 Data Source

- **World Bank International Debt Statistics (IDS)**  
  [IDS Website](https://datacatalog.worldbank.org/dataset/international-debt-statistics)

This dataset provides country-level data on external debt, debt servicing, lender types, currency composition, and borrower institutions across low and middle-income countries.

---

## 🚀 How to Use

1. Open the Excel file `External Debt Analysis.xlsx`
2. Navigate between the sheets to explore different dimensions of debt analysis
3. Use slicers and filters in the Dashboard to customize the view by year and region
4. Extend the dashboard by connecting updated IDS datasets
