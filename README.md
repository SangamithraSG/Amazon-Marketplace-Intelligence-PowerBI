Amazon Marketplace Intelligence – Pricing, Performance & Seller Analytics
#Table of Contents

Case Study

Dataset Description

Data Modeling

Data Cleaning & Transformation

DAX Calculations

Business Analysis & Insights

Dashboard Overview

Key Takeaways

About the Project

#Case Study

This project analyzes Amazon marketplace data to uncover insights into:

Product pricing strategies

Discount effectiveness

Seller performance

Revenue contribution

Customer behavior patterns

The goal is to understand how pricing, discounts, ratings, and seller types impact revenue and sales performance.

This dashboard is designed to simulate a real-world business intelligence scenario where stakeholders need actionable insights for strategic decision-making.

#Dataset Description

The dataset consists of marketplace product-level data including:

-Product Information

Product_ID – Unique identifier

Category

Price

List Price

Discount %

Rating

Review Count

-Sales Information

Units Sold

Total Revenue

Estimated Monthly Revenue

Bestseller Flag

-Seller Information

Seller_ID

Seller Type (Regular / Bestseller)

-Date Information

Generated Date

Month

Year

#Data Modeling

A star schema model was implemented:

Fact Table: Fact_Sales

Dimension Tables:

Dim_Product

Dim_Seller

Dim_Date

Relationships were established using primary and foreign keys to ensure clean filtering and accurate aggregations.

#Data Cleaning & Transformation

Key steps performed in Power Query:

Removed null and duplicate values

Standardized column naming

Created calculated Discount % column

Validated pricing logic (List Price > Price)

Created date hierarchy for time analysis

#DAX Calculations
- Discount %
Discount % =
DIVIDE(
    Fact_Sales[listPrice] - Fact_Sales[price],
    Fact_Sales[listPrice]
)

- Bestseller %
Bestseller % =
DIVIDE(
    CALCULATE(COUNTROWS(Fact_Sales), Fact_Sales[isBestSeller] = TRUE()),
    COUNTROWS(Fact_Sales)
)

#Seller Price Positioning Index

Measures how aggressively a seller prices relative to overall market average.

#Business Analysis & Insights
-Revenue Insights

Total Revenue generated: 4.7B+

A small percentage of products contribute disproportionately to total revenue.

Bestseller products show stronger revenue concentration.

#Pricing & Discount Analysis

Most products fall within the low-to-mid price range.

Higher discounts do not always guarantee higher unit sales.

Extreme discounts show diminishing returns in revenue.

#Ratings vs Price

Majority of products cluster around 4+ ratings.

No strong linear relationship between high price and high rating.

Mid-priced products dominate high-rating segments.

#Seller Insights

Regular sellers dominate total revenue (~90%+ share).

Bestsellers show stronger unit efficiency.

Seller pricing index reveals aggressive vs conservative pricing strategies.

#Category Insights

Certain categories dominate in revenue generation.

Discount dependency varies significantly across categories.

Revenue distribution is highly skewed across product segments.

#Dashboard Overview
- Page 1 – Executive Performance Dashboard

KPI Cards (Revenue, Units Sold, Reviews, Bestseller %, Avg Rating)

Revenue by Category

Monthly Revenue Trend

Revenue by Seller Type

Clean executive layout for stakeholders

- Page 2 – Pricing & Performance Analysis

Price vs Rating Scatter Plot

Discount vs Units Sold Bubble Analysis

Price Distribution Histogram

Seller Price Positioning Index

Interactive slicers for dynamic filtering

#Key Takeaways

Pricing alone does not define performance — rating and positioning matter.

Discount strategy must be optimized per category.

Bestseller flag strongly correlates with sales velocity.

Revenue is highly concentrated among specific product segments.

#Tools Used

Power BI

Power Query

DAX

Data Modeling (Star Schema)

Git & GitHub