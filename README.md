# merchant_transction_dashboard
Analysis of customer transaction data to identify key merchant partners. This project covers the full workflow from raw data ETL in Power Query to a final dashboard with actionable insights in Power BI.
This repository contains the files and summary for a comprehensive data analysis project. The project simulates a real-world task for a fictional bank, involving data cleaning, transformation, analysis, and visualization to derive actionable business insights.

1. Business Problem
The Head of Merchant Partnerships at FinSecure Bank needed to analyze two years of customer debit card transactions (2022-2023) to understand spending patterns. The primary goal was to identify the most valuable merchant partners to help inform and prioritize the strategic partnership efforts for the upcoming year.

The data was provided in a raw state across multiple files, requiring significant preparation before any analysis could be performed.

2. Data Source
The dataset for this project was provided as part of a structured data analysis course. In accordance with the course's policy on proprietary materials, the raw data files are not included in this repository.

3. Tools Used
Power BI / Power Query: For data cleaning, transformation (ETL), data modeling, and visualization.

DAX (Data Analysis Expressions): For creating custom measures to enable dynamic and flexible analysis.

4. Data Processing & Transformation (ETL)
The initial raw data required the following cleaning and transformation steps in Power Query:

Merchant Dimension (dim_merchants):

Split the merchant name from the industry segment description.

Cleaned the new 'Industry Segment' column by trimming whitespace and removing parentheses.

Identified and removed duplicate merchant records that had different merchant IDs.

Date Dimension (dim_date):

Enriched the table by extracting Year, Month Name, and Day Name from the primary date column to enable time-based analysis.

Category Dimension (dim_category):

Transformed the table from a wide (pivoted) format to a long (unpivoted) format to make it suitable for relationships and analysis.

Fact Tables (fact_transactions_2022, fact_transactions_2023):

Filtered both tables to remove insignificant transactions (debit amount < ₹100).

Appended the two yearly tables into a single, unified fact table named fact_transactions.

Data Modeling:

Merged the unified fact_transactions table with the cleaned dim_merchants and dim_category tables to create a single, denormalized table ready for analysis.

Feature Engineering:

Added a conditional column named Transaction Category to classify transactions as 'High' (> ₹1000) or 'Low'.

5. Data Analysis & Visualization
After preparing the data, the analysis focused on answering the key business questions using DAX measures and visualizations in Power BI.

Key DAX Measure Created:
A dynamic measure for Average Transaction Value was created to overcome the limitations of pre-calculated data from Power Query.

Code snippet

Average_Transaction = AVERAGE(fact_transactions[Debit_Amount])
Key Visualizations:
Top Merchants by Total Value (Horizontal Bar Chart): This chart clearly ranked all merchants by their total revenue contribution, identifying the most valuable partners.

Total Transaction Value by Category (Horizontal Bar Chart): This visual broke down the total spending by category, highlighting the most dominant sectors.

Average Transaction Value by Category (Horizontal Bar Chart): Using the new DAX measure, this chart revealed a crucial insight: the categories with the highest total spending were not the ones with the highest average transaction value.

6. Key Findings & Recommendations
Findings:
Value vs. Volume: The analysis revealed a clear distinction between high-volume and high-value merchants. The top merchants by total sales (Reliance Trends, Grofers) were different from the top merchants by number of transactions (Ajio).

Dominant Categories: Apparel and Groceries are the most critical categories, leading in both total transaction value and total transaction count.

The High-Value Niche: Healthcare was identified as a key insight. Despite having a lower number of transactions, it has the highest average transaction value, indicating that customers make larger purchases when they shop in this category.

Recommendations:
Strengthen Core Partnerships: The Partnerships team should prioritize and strengthen relationships with top-tier merchants in the high-performing Apparel and Groceries categories. These are the bank's core transaction drivers.

Develop Niche Strategies: A dedicated strategy should be developed for the Healthcare sector. Given its high average transaction value, the bank could explore premium partnerships or co-branded offers with major pharmacy chains or hospitals to capitalize on this valuable segment.
