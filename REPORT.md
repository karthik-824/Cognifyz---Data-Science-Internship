# Cognifyz Technologies — Data Science Internship Report

**Intern:** Karthik Kuru
**Organization:** Cognifyz Technologies
**Project:** Restaurant Data Analysis & Predictive Modeling
**GitHub:** [karthik-824/Cognifyz---Data-Science-Internship](https://github.com/karthik-824/Cognifyz---Data-Science-Internship)

---

## Table of Contents

1. [Executive Summary](#1-executive-summary)
2. [Project Overview](#2-project-overview)
3. [Dataset Overview](#3-dataset-overview)
4. [Level 1 — Data Exploration and Visualization](#4-level-1--data-exploration-and-visualization)
   - [Task 1: Data Exploration and Preprocessing](#task-1-data-exploration-and-preprocessing)
   - [Task 2: Descriptive Analysis](#task-2-descriptive-analysis)
   - [Task 3: Geospatial Analysis](#task-3-geospatial-analysis)
5. [Level 2 — Insights Enhancement](#5-level-2--insights-enhancement)
   - [Task 1: Table Booking and Online Delivery](#task-1-table-booking-and-online-delivery)
   - [Task 2: Price Range Analysis](#task-2-price-range-analysis)
   - [Task 3: Feature Engineering](#task-3-feature-engineering)
6. [Level 3 — Predictive Modeling and Advanced Analysis](#6-level-3--predictive-modeling-and-advanced-analysis)
   - [Task 1: Predictive Modeling](#task-1-predictive-modeling)
   - [Task 2: Customer Preference Analysis](#task-2-customer-preference-analysis)
   - [Task 3: Data Visualization](#task-3-data-visualization)
7. [Key Findings and Business Recommendations](#7-key-findings-and-business-recommendations)
8. [Technologies Used](#8-technologies-used)
9. [Conclusion](#9-conclusion)

---

## 1. Executive Summary

This report documents the work completed during the Data Science Internship at **Cognifyz Technologies**. The internship project involved an end-to-end analysis of a restaurant dataset encompassing over 9,500 records. The project was structured across three progressive levels — from foundational data exploration to advanced machine learning — delivering actionable insights into restaurant performance, customer preferences, and service offerings.

Key outcomes include:
- Identification of top-performing cities, cuisines, and service models.
- Discovery that table booking strongly correlates with higher customer ratings.
- Development of a Random Forest regression model achieving an **R² of 0.94**, accurately predicting restaurant aggregate ratings.

---

## 2. Project Overview

The project was divided into three levels of increasing complexity:

| Level | Focus Area | Notebook |
|:---:|:---|:---|
| **1** | Data Exploration, Descriptive Statistics, Geospatial Analysis | `Restaurant_Data_Analysis_Level_1.ipynb` |
| **2** | Service Analysis, Price Range Correlation, Feature Engineering | `Restaurant_Insights_Enhancement_Level_2.ipynb` |
| **3** | Predictive Modeling, Customer Preference Analysis, Advanced Visualization | `Restaurant_Data_Analysis_&_Predictive_Modeling_Level_3.ipynb` |

**Overall Objective:** Extract actionable insights from a restaurant dataset and build a predictive model to estimate restaurant ratings based on restaurant attributes and service offerings.

---

## 3. Dataset Overview

- **File:** `Dataset .csv`
- **Rows:** 9,551
- **Columns:** 21
- **Source:** Cognifyz Technologies

### Key Columns

| Column | Description |
|:---|:---|
| `Restaurant ID` | Unique identifier for each restaurant |
| `Restaurant Name` | Name of the restaurant |
| `Country Code` | Numeric code for the country |
| `City` | City where the restaurant is located |
| `Cuisines` | Type(s) of cuisine served |
| `Average Cost for two` | Average cost for two people |
| `Has Table booking` | Whether the restaurant accepts table bookings (Yes/No) |
| `Has Online delivery` | Whether online delivery is available (Yes/No) |
| `Price range` | Price range category (1–4, where 1 = Budget, 2 = Mid-range, 3 = Premium, 4 = Luxury) |
| `Aggregate rating` | Overall customer rating (0–5 scale) |
| `Votes` | Number of customer votes |
| `Latitude / Longitude` | Geographic coordinates of the restaurant |

### Data Quality

- **Duplicate rows:** 0
- **Missing values:** 9 records in the `Cuisines` column (removed during preprocessing)
- **Data type conversions:** Not required

---

## 4. Level 1 — Data Exploration and Visualization

### Task 1: Data Exploration and Preprocessing

**Objectives:**
- Understand the structure and dimensions of the dataset.
- Handle missing values to ensure data integrity.
- Analyze the distribution of the target variable (`Aggregate rating`).

**Findings:**

- The dataset contains **9,551 rows and 21 columns**.
- The only column with missing values was `Cuisines` (9 records), which were dropped as the count was negligible.
- No duplicate records were found.
- The `Aggregate rating` distribution revealed a notable class imbalance: **2,148 restaurants (22.5%) had a rating of 0.0**, which likely represents unrated restaurants rather than poor performers. Ratings between 3.0 and 3.9 were the most common among rated restaurants.

**Target Variable Distribution (Top Values):**

| Rating | Count |
|:---:|:---:|
| 0.0 | 2,148 |
| 3.2 | 522 |
| 3.1 | 519 |
| 3.4 | 495 |
| 3.3 | 483 |
| 3.5 | 480 |

---

### Task 2: Descriptive Analysis

**Objectives:**
- Calculate key statistical measures for numerical columns.
- Explore the distribution of categorical variables.
- Identify the top cuisines and cities by restaurant count.

**Statistical Summary (Key Numerical Columns):**

| Metric | Average Cost for two | Price Range | Aggregate Rating | Votes |
|:---|:---:|:---:|:---:|:---:|
| **Mean** | ~1,200 | 1.80 | 2.67 | ~157 |
| **Median** | ~400 | 2.00 | 3.20 | ~31 |
| **Std Dev** | ~16,129 | 0.91 | 1.52 | ~589 |

> *Note: The high standard deviation in "Average Cost for two" indicates significant price variation across restaurants.*

**Top 10 Cities by Restaurant Count:**

| Rank | City | Count |
|:---:|:---|:---:|
| 1 | New Delhi | 5,473 |
| 2 | Gurgaon | 1,118 |
| 3 | Noida | 1,080 |
| 4 | Faridabad | 251 |
| 5 | Ghaziabad | 25 |
| 6 | Ahmedabad | 21 |
| 7 | Guwahati | 21 |
| 8 | Amritsar | 21 |
| 9 | Bhubaneshwar | 21 |
| 10 | Lucknow | 21 |

**Top 10 Cuisines by Restaurant Count:**

| Rank | Cuisine | Count |
|:---:|:---|:---:|
| 1 | North Indian | 936 |
| 2 | North Indian, Chinese | 511 |
| 3 | Chinese | 354 |
| 4 | Fast Food | 354 |
| 5 | North Indian, Mughlai | 334 |
| 6 | Cafe | 299 |
| 7 | Bakery | 218 |
| 8 | North Indian, Mughlai, Chinese | 197 |
| 9 | Bakery, Desserts | 170 |
| 10 | Street Food | 149 |

---

### Task 3: Geospatial Analysis

**Objectives:**
- Visualize restaurant locations using latitude and longitude.
- Analyze the geographic distribution of restaurants.
- Explore correlations between restaurant location and rating.

**Findings:**

- Restaurant density is highest in **North America and South/Southeast Asia** (predominantly India).
- Within India, **New Delhi** accounts for over half of all records (5,473 restaurants), followed by Gurgaon and Noida.
- **Correlation Analysis:**
  - `Latitude` vs `Aggregate rating`: **No significant correlation**
  - `Longitude` vs `Aggregate rating`: **Negative correlation** — as longitude increases (moving eastward), average ratings tend to slightly decrease.

---

## 5. Level 2 — Insights Enhancement

### Task 1: Table Booking and Online Delivery

**Objectives:**
- Quantify the percentage of restaurants offering table booking and online delivery.
- Compare average ratings of restaurants with and without table booking.
- Analyze online delivery availability across different price ranges.

**Findings:**

| Service | Availability |
|:---|:---:|
| Table Booking | **12.12%** of restaurants |
| Online Delivery | **25.66%** of restaurants |

**Impact of Table Booking on Ratings:**

| Table Booking | Average Rating |
|:---|:---:|
| **Yes** | **3.44** |
| **No** | **2.56** |

> Restaurants that offer table booking have an average rating **0.88 points higher** than those that don't — a statistically meaningful difference indicating that full-service restaurants are rated more favorably.

**Online Delivery by Price Tier (based on Average Cost for two):**

| Cost Tier | Definition | No Delivery | Online Delivery Available |
|:---|:---|:---:|:---:|
| Low | Average Cost &lt; ₹500 | 85.9% | 14.1% |
| Medium | ₹500 ≤ Average Cost ≤ ₹1,000 | 56.6% | **43.4%** |
| High | Average Cost &gt; ₹1,000 | 71.9% | 28.1% |

> Note: These tiers are custom groupings derived from the `Average Cost for two` column, separate from the `Price range` (1–4 scale) column used in other analyses. Online delivery is most prevalent in the **medium cost tier**, suggesting that mid-range restaurants are best positioned to serve delivery-focused customers.

---

### Task 2: Price Range Analysis

**Objectives:**
- Identify the most common price range.
- Calculate average ratings per price range.
- Identify the color representing the highest average rating.

**Findings:**

| Price Range | Description | Average Rating |
|:---:|:---|:---:|
| **1** | Budget | 2.000 |
| **2** | Mid-range | 2.941 |
| **3** | Premium | 3.683 |
| **4** | Luxury | **3.818** |

- The **most common price range is 1** (budget), indicating most restaurants in the dataset cater to budget-conscious customers.
- Higher price ranges consistently achieve higher average ratings, with **Price Range 4 (Luxury)** earning the top average of **3.818**.

---

### Task 3: Feature Engineering

**Objectives:**
- Extract length-based features from text columns.
- Encode binary categorical variables for use in modeling.

**New Features Created:**

| Feature | Description |
|:---|:---|
| `Restaurant Name Length` | Number of characters in the restaurant name |
| `Address Length` | Number of characters in the restaurant's address |
| `Has Table Booking` (encoded) | Binary: 1 = Yes, 0 = No |
| `Has Online Delivery` (encoded) | Binary: 1 = Yes, 0 = No |

These engineered features were used as inputs in the Level 3 predictive models.

---

## 6. Level 3 — Predictive Modeling and Advanced Analysis

### Task 1: Predictive Modeling

**Objectives:**
- Build regression models to predict `Aggregate rating`.
- Evaluate and compare model performance.

**Features Used:**
- `Average Cost for two`
- `Votes`
- `Price range`
- `Has Table booking` (encoded)
- `Has Online delivery` (encoded)

**Train-Test Split:** 80% Training / 20% Testing (`random_state=42`)

**Model Performance Comparison:**

| Model | MSE | R² Score |
|:---|:---:|:---:|
| **Linear Regression** | 1.6765 | 0.2634 |
| **Decision Tree** | 0.2074 | 0.9089 |
| **Random Forest** | **0.1337** | **0.9413** |

**Interpretation:**
- **Linear Regression** performed poorly (R² ≈ 0.26), confirming that the relationship between features and rating is non-linear.
- **Decision Tree** improved significantly (R² ≈ 0.91), capturing non-linear patterns but potentially overfitting.
- **Random Forest** delivered the best results (R² ≈ **0.94**), with the lowest MSE of **0.1337**, making it the recommended model for rating prediction.

---

### Task 2: Customer Preference Analysis

**Objectives:**
- Analyze the relationship between cuisine type and ratings.
- Identify the most popular cuisines by customer votes.
- Determine cuisines that tend to receive higher ratings.

**Most Popular Cuisines by Total Votes:**

| Rank | Cuisine | Total Votes |
|:---:|:---|:---:|
| 1 | North Indian, Mughlai | 53,747 |
| 2 | North Indian | 46,241 |
| 3 | North Indian, Chinese | 42,012 |
| 4 | Cafe | 30,657 |
| 5 | Chinese | 21,925 |

**Cuisines with Highest Average Ratings:**
- **Italian, Hawaiian, Seafood, Tea, Sandwich, Continental, Indian**
- These niche cuisines attract fewer but more satisfied customers, resulting in higher average ratings.

**Rating Variability by Cuisine:**
- **Cafe and Fast Food:** Consistent and predictable ratings.
- **Mughlai, North Indian, Chinese:** Higher variance in ratings — both high and low performers exist within these categories.

---

### Task 3: Data Visualization

**Objectives:**
- Visualize the distribution of restaurant ratings.
- Compare average ratings across cuisines and cities.
- Explore feature-target relationships.

**Key Visualizations Produced:**

1. **Rating Distribution Histogram:** The distribution is negatively skewed, with a large cluster of 0.0 ratings (unrated restaurants) and the bulk of rated restaurants concentrated in the 3.0–4.0 range.

2. **Average Rating by Cuisine (Bar Chart):** Italian, Hawaiian, and Seafood cuisine restaurants consistently receive the highest average ratings.

3. **Average Rating by City (Bar Chart):** Cities such as **Inner City, Quezon City, and Makati City** have the highest average restaurant ratings.

4. **Feature Correlation (Pair Plot):**
   - `Votes` and `Aggregate rating` are **positively correlated** — restaurants with more votes tend to have higher ratings.
   - `Average Cost for two` shows a weak positive relationship with rating.

---

## 7. Key Findings and Business Recommendations

### Summary of Key Findings

| Area | Key Insight |
|:---|:---|
| **Geography** | New Delhi dominates with 57% of all restaurants; Gurgaon and Noida follow. |
| **Services** | Table booking drives significantly higher ratings (+0.88 average). |
| **Delivery** | Online delivery is most common and effective in mid-range restaurants. |
| **Pricing** | Most restaurants are budget-tier (Price Range 1), but luxury restaurants earn the highest ratings. |
| **Cuisine** | North Indian and Chinese are most common; Italian and Hawaiian earn the best ratings. |
| **Modeling** | Random Forest (R² = 0.94) is the best model for predicting restaurant ratings. |

### Business Recommendations

1. **Introduce Table Booking:** Restaurants not currently offering table booking should consider implementing it, as it correlates with an average rating increase of ~0.88 points.

2. **Target Mid-Range for Delivery Expansion:** Mid-priced restaurants see the highest online delivery adoption (~43%). New entrants in this segment should invest in online delivery infrastructure.

3. **Niche Cuisine Opportunity:** While North Indian and Chinese cuisines dominate by volume, Italian, Hawaiian, Seafood, and Continental cuisines earn the highest ratings. There is an opportunity for new restaurants to differentiate in these high-rated, underserved niches.

4. **Focus on Votes/Engagement:** Since votes are positively correlated with ratings, encouraging customer reviews and feedback can help improve a restaurant's visibility and perceived quality.

5. **Geographic Expansion:** The current dataset is heavily skewed towards NCR (National Capital Region of India). Expansion to other cities could present new market opportunities with less competition.

---

## 8. Technologies Used

| Category | Library/Tool |
|:---|:---|
| **Language** | Python 3 |
| **Data Manipulation** | Pandas, NumPy |
| **Visualization** | Matplotlib, Seaborn |
| **Geospatial Analysis** | GeoPandas, Shapely |
| **Machine Learning** | Scikit-learn (LinearRegression, DecisionTreeRegressor, RandomForestRegressor) |
| **Notebook Environment** | Jupyter Notebook / Google Colab |

---

## 9. Conclusion

This internship project provided a comprehensive, hands-on experience in data science applied to the restaurant industry. Working through three progressive levels — data exploration, insight enhancement, and predictive modeling — demonstrated the full pipeline of a data science project.

**Level 1** established a strong foundation by cleaning the data, understanding its structure, and uncovering geographic and categorical distributions.

**Level 2** deepened the analysis by quantifying the impact of service offerings (table booking, online delivery) and pricing on customer ratings, while also engineering new features for modeling.

**Level 3** brought it all together with machine learning. The **Random Forest Regressor** proved to be the most effective model with an R² score of **0.94**, accurately predicting restaurant ratings based on cost, votes, price range, and service availability. Customer preference analysis further revealed that engagement (votes) and cuisine type are meaningful differentiators in restaurant performance.

Overall, the project successfully demonstrated that data science techniques can deliver meaningful, actionable insights for the restaurant industry — from understanding customer preferences to building reliable predictive models.

---

*Report prepared by **Karthik Kuru** as part of the Cognifyz Technologies Data Science Internship.*
*[LinkedIn Profile](https://www.linkedin.com/in/karthikkuru/) | [GitHub Repository](https://github.com/karthik-824/Cognifyz---Data-Science-Internship)*
