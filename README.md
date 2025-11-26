# Cognifyz-Data-Science-Internship
# 🍽️ Restaurant Data Analysis & Predictive Modeling

## 📌 Project Overview
This repository contains the work completed during the Data Science Internship at **Cognifyz Technologies**. The project focuses on analyzing a restaurant dataset to extract meaningful insights, perform geospatial analysis, and build predictive models to estimate restaurant ratings.

The project is divided into three distinct levels, progressing from basic data exploration to advanced machine learning techniques.

## 📂 Project Structure
The analysis is split into three levels, each contained in its own Jupyter Notebook:

### Level 1: Data Exploration and Visualization
* **File:** `Restaurant_Data_Analysis_Level_1.ipynb`
* **Focus:** Data Preprocessing, Descriptive Statistics, and Geospatial Analysis.
* **Key Tasks:**
    * Handling missing values (specifically in the 'Cuisines' column).
    * Analyzing class imbalances in the target variable ('Aggregate rating').
    * Visualizing restaurant distribution on a map using Latitude and Longitude.
    * Identifying top cities and cuisines by frequency.

### Level 2: Insights Enhancement
* **File:** `Restaurant_Insights_Enhancement_Level_2.ipynb`
* **Focus:** Service Analysis, Price Range correlation, and Feature Engineering.
* **Key Tasks:**
    * Analyzing the impact of Table Booking and Online Delivery on ratings.
    * Determining the most common price ranges and their average ratings.
    * **Feature Engineering:** Creating new columns for 'Restaurant Name Length', 'Address Length', and encoding categorical variables.

### Level 3: Predictive Modeling & Advanced Analysis
* **File:** `Restaurant_Data_Analysis_&_Predictive_Modeling_Level_3.ipynb`
* **Focus:** Machine Learning, Customer Preference Analysis, and Advanced Visualization.
* **Key Tasks:**
    * **Predictive Modeling:** Building regression models to predict Aggregate rating.
    * **Algorithm Selection:** Comparing Linear Regression, Decision Tree, and Random Forest.
    * **Customer Preference:** Analyzing the relationship between votes, cuisines, and ratings.

## 📊 Key Findings & Insights

### 1. Geographical Insights
* **Top Hubs:** New Delhi, Gurgaon, and Noida have the highest concentration of restaurants.
* **Correlation:** There is a negative correlation between Longitude and Ratings, while Latitude shows no significant correlation.

### 2. Service & Rating Dynamics
* **Table Booking:** Only ~12% of restaurants offer table booking, but those that do have a significantly higher average rating (**3.44**) compared to those that don't (**2.56**).
* **Online Delivery:** Available in ~25% of restaurants. It is most prevalent in medium-priced restaurants rather than low or high-end ones.

### 3. Cuisine Preferences
* **Most Popular (by count/votes):** North Indian, Mughlai, and Chinese.
* **Highest Rated:** Italian, Hawaiian, Seafood, Tea, and Continental cuisines tend to have the highest average ratings.

### 4. Model Performance
To predict restaurant ratings, three regression models were evaluated. **Random Forest Regressor** performed the best:

| Model | MSE | R² Score |
| :--- | :--- | :--- |
| **Linear Regression** | ~1.67 | 0.26 |
| **Decision Tree** | ~0.20 | 0.90 |
| **Random Forest** | **~0.13** | **0.94 (Best Fit)** |

## 🛠️ Technologies Used
* **Language:** Python
* **Data Manipulation:** Pandas, NumPy
* **Visualization:** Matplotlib, Seaborn
* **Geospatial Analysis:** GeoPandas, Shapely
* **Machine Learning:** Scikit-learn (Linear Regression, Decision Tree, Random Forest)

##📢 Acknowledgments
* **[Cognifyz Technologies](https://cognifyz.com/)**

    
    
## 👤 Author
 **[Karthik Kuru](https://www.linkedin.com/in/karthikkuru/)**


   
