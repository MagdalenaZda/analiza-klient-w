# Technical and Business Documentation: Customer Personality Analysis 

## I. Business Documentation

### 1. Project Objectives
The primary goal is to provide a deep dive into customer demographics and behavior. By analyzing these patterns, the project identifies key drivers of revenue and evaluates the effectiveness of promotional activities.

### 2. Key Insights
* **Customer Profile:** The highest purchasing activity is shown by **Seniors** and **Middle-aged** individuals. These groups dominate all sales channels.
* **Sales Structure:** Sales are dominated by **Wine (35.8%)** and **Meat products (25.8%)**. Other categories serve as supplementary offerings.
* **Channel Preferences:** Despite the availability of online and catalog shopping, physical stores remain the primary contact point for every age segment.
* **Marketing:** Campaigns 3 and 4 recorded the highest response rates, suggesting superior effectiveness compared to other initiatives.

### 3. Recommendations
* Maintain a wide assortment of wines in physical stores to satisfy the preferences of the key demographic (Seniors).
* Analyze the reasons behind the low activity of the "Young Adults" group to better tailor future marketing campaigns.



## II. Technical Documentation

### 1. Data Architecture

#### Phase I: Relational Modeling
The project is based on an optimized relational model subjected to a normalization process. The database defines keys, eliminates data redundancy, and ensures full referential integrity between customer profiles and transactional event history.

#### Phase II: Analytical Layer
Raw data was transformed into a logic-view layer ready for analysis:
* `v_customer_golden_record`
* `v_customer_engagement`

### 2. Data Flow (ETL)
**Goal:** Transform raw, unstructured CSV data into an optimized relational model.

1.  **Temporary Table Creation:** Fast data import without type validation. All columns are set to `TEXT` to prevent errors during the initial loading of source files (`tmp_marketing`).
2.  **Transformation and Loading:**
    * Conversion from `TEXT` to `INT`, `VARCHAR`, and `DATE`.
    * **Date Standardization:** Used the `TO_DATE(dt_customer, 'DD-MM-YYYY')` function to unify the time format.
    * **Segmentation:** Added customer segmentation using `CASE` statements for age and income.

### 3. Power BI and Data Visualization

#### Data Transformation
* **Locale:** Set to Polish for the interface and date formatting.
* **Translations:** Applied custom mapping for age group names and income levels from English to Polish.

#### DAX Implementation
* **Time Hierarchy:** Month names were mapped to Polish and sorted by month number (1-12) to avoid alphabetical sorting.
* **SWITCH:** Used for dynamic label changes in specific slicers.

#### Visualizations and Interactions
* **Slicers:** Utilized "List" slicers for age and income groups and "Tiles" for month selection.
* **Data Consistency:** All visual objects have cross-filtering enabled.
* **KPI Cards:** Display the total number of customers and promotional transactions.

---

**Data Source:** [Kaggle - Customer Personality Analysis](https://www.kaggle.com/datasets/imakash3011/customer-personality-analysis)
