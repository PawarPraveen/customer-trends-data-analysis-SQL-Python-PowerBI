# Customer Trends Data Analysis Project Summary

## Project purpose
The project analyzes customer shopping behavior using a CSV dataset and applies Python, SQL, and visualization to answer business questions.

## Problem statement
- Understand customer spending patterns and revenue drivers.
- Determine how discounts, subscriptions, age groups, shipping, and purchase frequency affect behavior.
- Produce insights that support dashboard reporting and business decision making.

## Data source
- File: `customer_shopping_behavior.csv`
- Shape: 3900 rows, 18 columns
- Key fields:
  - Customer ID
  - Age
  - Gender
  - Item Purchased
  - Category
  - Purchase Amount (USD)
  - Review Rating
  - Subscription Status
  - Shipping Type
  - Discount Applied
  - Previous Purchases
  - Frequency of Purchases

## Notebook workflow
The notebook loads and inspects the dataset with pandas, performs cleaning and transformation, and creates visualizations.

### Data inspection
- `df.head()`
- `df.info()`
- `df.describe(include='all')`
- `df.isnull().sum()`

### Data cleaning and transformation
- Filled missing `Review Rating` values using category median.
- Normalized column names to `snake_case`.
- Renamed `purchase_amount_(usd)` to `purchase_amount`.
- Added derived fields:
  - `age_group` using age quartiles
  - `purchase_frequency_days` from `frequency_of_purchases`
- Dropped `promo_code_used` after verifying it matched `discount_applied`.

### Why cleaning matters
- Ensures accurate aggregation and analysis
- Prevents incorrect patterns caused by missing or inconsistent data
- Makes queries and visualizations easier to build and maintain
- Allows derived categories to answer business questions directly

## Visualization
The notebook includes:
- KPI dashboard metrics
- Subscription status pie chart
- Revenue by age group bar chart

### Why visualization is important
- Makes insights easier to understand quickly
- Highlights comparisons and trends
- Supports storytelling for stakeholders
- Reveals patterns not obvious from raw tables

## SQL analysis file
File: `customer_behavior_sql_queries.sql`

### Purpose of SQL in this project
- Provides structured analytics for the relational customer table
- Supports business questions with repeatable queries
- Enables dashboard and reporting integration
- Makes it easy to compare segments and compute aggregates

### Example SQL questions
- Revenue by gender
- High-spending customers using discounts
- Top products by average rating
- Compare spend across shipping types
- Subscription vs non-subscription revenue
- Discount usage by product
- Customer segmentation based on repeat purchases
- Top products per category
- Revenue by age group
- Discount impact on satisfaction and spending
- Purchase frequency effects on spending and discount usage

## Why SQL instead of MongoDB / Mongoose
- The dataset is tabular and fits naturally into a relational model
- SQL is ideal for aggregation, grouping, and analytics
- PostgreSQL also uses SQL, so the approach is compatible with relational databases
- Mongoose is for MongoDB, a NoSQL document database, which is not needed here

## Power BI follow-up questions
- What business story should the dashboard emphasize?
- What filters or slicers are most important?
- Which KPIs should be highlighted?
- Should the dashboard compare segments cross-sectionally or over time?

## Summary
This project combines data cleaning, transformation, SQL analysis, and visualization to turn raw customer records into actionable insights. The notebook and SQL file form a strong base for a Power BI report that can communicate customer behavior across subscriptions, discounts, age groups, and product categories.
