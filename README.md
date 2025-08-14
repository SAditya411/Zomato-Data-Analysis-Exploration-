# 🍽️ Zomato Data Analysis & Exploration  

![SQL](https://img.shields.io/badge/SQL-Server-blue)  
![Data Cleaning](https://img.shields.io/badge/Data-Cleaning-green)  
![Data Analysis](https://img.shields.io/badge/Data-Analysis-orange)  
![License](https://img.shields.io/badge/License-MIT-yellow)  

---

## 📑 Table of Contents  
1. [Project Overview](#project-overview)  
2. [Dataset](#dataset)  
3. [Data Cleaning Process](#data-cleaning-process)  
4. [Data Analysis Queries](#data-analysis-queries)  
5. [Insights & Findings](#insights--findings)  
6. [How to Run](#how-to-run)  
7. [Future Improvements](#future-improvements)  
8. [License](#license)  

---

## 📌 Project Overview  
This project involves cleaning, exploring, and analyzing **Zomato restaurant data** to uncover key insights using **SQL Server**.  

Objectives include:  
- Identifying top cuisines and cities  
- Understanding restaurant distribution  
- Analyzing the effect of table booking & delivery options on ratings  
- Finding the best high-rated & cost-effective restaurants  

---

## 📂 Dataset  

**File:** `Zomato_Dataset.csv`  
**Size:** ~9,551 rows × 21 columns  

**Sample Preview:**  

| RestaurantID | RestaurantName       | CountryName | City       | Cuisines          | Rating | Votes | Average_Cost_for_two | Has_Table_booking | Has_Online_delivery |
|--------------|---------------------|-------------|------------|-------------------|--------|-------|----------------------|-------------------|----------------------|
| 6317637      | Dominos Pizza       | India       | Delhi      | Pizza, Fast Food  | 4.1    | 1200  | 600                  | Yes               | Yes                  |
| 5482651      | KFC                 | India       | Mumbai     | Fast Food         | 3.9    | 980   | 500                  | No                | Yes                  |

---

## 🧹 Data Cleaning Process (`ZOMATO_DATA_EXPLORATION.sql`)  
- Removed **duplicates** based on `RestaurantID`.  
- Deleted **invalid rows** with incorrect `CountryCode`.  
- Joined **CountryCode** with country names.  
- Fixed **misspelled city names**.  
- Dropped unnecessary columns: `Address`, `LocalityVerbose`, `Switch_to_order_menu`.  
- Converted `Votes`, `Average_Cost_for_two`, and `Rating` to correct data types.  
- Created `RATE_CATEGORY` column (POOR, GOOD, GREAT, EXCELLENT) based on ratings.  

---

## 📊 Data Analysis Queries (`ZOMATO_DATA_ANALYSIS.sql`)  
Example analyses performed:  
1. **Restaurant Distribution** by country with percentage share.  
2. **Online Delivery Analysis** by country.  
3. **Top Localities in India** with max/min restaurants.  
4. **Popular Cuisines** in top restaurant areas.  
5. **Table Booking & Rating Comparison** in Connaught Place.  
6. **Best Value Restaurants** with high ratings and affordable costs.  

**Example Query:**  
```sql
SELECT COUNTRY_NAME, COUNT(RestaurantID) AS Restaurant_Count
FROM ZomatoData1
GROUP BY COUNTRY_NAME
ORDER BY Restaurant_Count DESC;
