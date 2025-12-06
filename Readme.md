# Used Car Market Insights Dashboard (Dec 2023 – Dec 2024)

## **Project Overview**
This Power BI project analyzes **3,622 used car listings** to uncover trends in pricing, supply, demand, ownership, and vehicle features. The dashboard provides actionable insights for buyers, sellers, and market analysts, combining KPIs, visual trends, and advanced analytics.

**Key Objectives:**
- Understand market pricing and depreciation patterns  
- Identify supply trends by brand, fuel type, transmission, and ownership  
- Detect anomalies in odometer readings and pricing  

---

## **Dataset**
- Source: Kaggle – used_cars_dataset_v2
- Tool Used: Power BI (Power Query + Power BI Desktop)

---

## **Key Steps Performed**
1. **Data Cleaning & Preparation**  
   - Standardized fuel type, transmission, and owner categories  
   - Corrected inconsistent KM readings and removed duplicates  
   - Converted textual dates into proper date formats  

2. **Data Modeling**  
   - Created relationships between listings, brands, and time tables  
   - Built measures for KPIs and trend analysis  

3. **Dashboard Design**  
   - Multi-page layout with KPIs, market composition, pricing trends, odometer reliability, and executive summary  
   - Designed consistent UI/UX for readability and quick insights  

---

## **Key Business Questions Answered**
- What is the **average asking price** and how does it vary by brand, fuel type, and ownership?  
- Which **brand and model dominate the market**?  
- What are the **peak listing months** and seasonal trends?  
- How do **prices depreciate with car age**?  
- Which listings have **suspicious odometer readings**?  

---

## **Data Cleaning & Preparation**
- Handled missing or inconsistent values in KM Driven, Price, and Owner fields  
- Created derived columns such as Car Age and Price Buckets  
- Standardized categorical variables (Fuel Type, Transmission, Owner Type)  
- Ensured time intelligence functions work with proper Date tables  

---

## **Example DAX Measures**

```
Most_Brand_With_Count =
VAR BrandCounts =
    SUMMARIZE(
        'used_cars_dataset_v2',
        'used_cars_dataset_v2'[Brand],
        "CountBrand", COUNTROWS('used_cars_dataset_v2')
    )
VAR MaxCount = MAXX(BrandCounts, [CountBrand])
RETURN
CONCATENATEX(
    FILTER(BrandCounts, [CountBrand] = MaxCount),
    'used_cars_dataset_v2'[Brand] & " - " & [CountBrand] & " cars",
    ", "
)



Most_Active_Month_With_Count =
VAR MonthCounts =
    SUMMARIZE(
        'used_cars_dataset_v2',
        'used_cars_dataset_v2'[Month],
        "CountMonth", COUNTROWS('used_cars_dataset_v2')
    )
VAR MaxCount = MAXX(MonthCounts, [CountMonth])
RETURN
CONCATENATEX(
    FILTER(MonthCounts, [CountMonth] = MaxCount),
    FORMAT(DATE(2000, 'used_cars_dataset_v2'[Month], 1), "MMMM")
    & " - " & [CountMonth] & " cars",
    ", "
)
```

---

## **Repository Structure**

- `Data` → Raw dataset (CSV file from Kaggle)

-  Dashboard.pbix

-  Dashboard.pdf

- README.md

--- 

## **Workflow Summary**

- Load and clean raw data

- Transform and standardize columns with Power Query

- Build relationships and data model in Power BI

- Create KPIs, charts, and advanced measures using DAX

- Design multi-page dashboard with clear UI/UX

- Analyze insights, trends, and anomalies

---

## **Insights**

- **Average asking price:** ₹9.78 lakh

- **Top brand:** Maruti Suzuki (1,169 cars)

- **Peak listing month:** November (3,176 listings)

- **Suspicious odometer readings:** 178 flagged listings

- **Price depreciation:** Sharp drop in first 5 years, then stabilizes

E:\Data Analyst\Used Car\Image_page-0001.jpg
