Amazon Marketplace Intelligence Dashboard
Table of Contents

Case Study

Dataset Description

Data Model

Data Cleaning & Transformations

Calculated Measures

Performance Insights

Pricing & Competitive Insights

Competitive Intelligence Analysis

Dashboard Overview

Tools Used

Case Study

This project analyzes Amazon marketplace product performance to uncover insights related to revenue, pricing strategy, customer satisfaction, and competitive positioning.

The objective of this analysis is to:

Identify top-performing sellers

Understand pricing impact on ratings and revenue

Benchmark category performance

Detect high-opportunity market segments

Support data-driven pricing and competitive strategy decisions

This dashboard is designed for business stakeholders, sellers, and analysts to evaluate marketplace performance and strategic positioning.

Dataset Description

The dataset consists of transactional and dimensional data structured in a star schema format.

Fact Table
Fact_Sales

Product_id – Unique product identifier

SellerID – Unique seller identifier

Revenue – Total revenue generated

UnitSold – Total units sold

price – Selling price

listPrice – Original list price

Rating – Customer rating

ReviewCount – Number of reviews

isBestSeller – Bestseller indicator

Dimension Tables
Dim_Product

Product_id

category_name

Product hierarchy

Dim_Seller

SellerID

Seller attributes

Dim_Date

Date

Year

Month

Dim_Category

CategoryID

category_name

Data Model

The dataset follows a Star Schema Model:

Fact_Sales connected to:

Dim_Product

Dim_Seller

Dim_Date

Dim_Category

This structure ensures optimized aggregation and performance in Power BI.

Data Cleaning & Transformations

The following transformations were applied:

Removed null values and duplicates

Standardized column names

Created calculated columns for:

Discount %

Price Index

Revenue Rank

Rating Band

Created price bins for distribution analysis

Built measures for dynamic aggregation

Calculated Measures
Discount %
Discount % = 
DIVIDE(
    SUM(Fact_Sales[listPrice]) - SUM(Fact_Sales[price]),
    SUM(Fact_Sales[listPrice])
)

Price Index

Measures seller pricing position relative to market average.

Price Index =
DIVIDE(
    [Avg Price],
    CALCULATE([Avg Price], ALL(Dim_Seller))
)

Revenue Rank

Ranks sellers based on total revenue.

Revenue Rank =
RANKX(
    ALL(Dim_Seller[SellerID]),
    [Total Revenue],
    ,
    DESC
)

Rating Band

Classifies ratings into performance categories:

High (4.2+)

Medium (3.5 – 4.2)

Low (Below 3.5)

Performance Insights
Revenue & Sales Analysis

Identified top-performing seller by revenue

Analyzed revenue distribution by category

Monthly revenue trend analysis

Bestseller percentage comparison across sellers

Pricing & Competitive Insights
Price vs Rating Analysis

Correlation between price and customer rating

Bubble size represents total revenue

Identified premium and budget segments

Price Distribution

Most products fall within low-to-mid price range

High-priced products contribute lower volume but higher margins

Seller Price Positioning

Seller 1 positioned below market average (Price Index < 1)

Seller 2 positioned at market level (Price Index ≈ 1)

Competitive Intelligence Analysis
Seller Comparison Table

Compares sellers across:

Total Revenue

Units Sold

Average Price

Rating

Bestseller %

Price Index

Category Performance Benchmarking

Categories analyzed across:

Revenue

Units Sold

Rating Distribution

Pricing Position

Top performing categories identified based on:

High revenue + high rating

Strong bestseller presence

Revenue vs Rating Heatmap

Visual representation of:

Price (X-axis)

Rating (Y-axis)

Revenue (Bubble size)

Quadrants created using average price and average rating:

High Rating + Low Price → High Opportunity

High Rating + High Price → Premium Segment

Low Rating + Low Price → Improvement Needed

Low Rating + High Price → Risk Zone

Dashboard Overview

The dashboard consists of 4 pages:

Page 1 – Executive Performance Overview

KPI Cards

Revenue by Category

Monthly Revenue Trend

Seller Revenue Split

Page 2 – Pricing & Performance Analysis

Price vs Rating Scatter

Price Distribution Histogram

Seller Price Index

Page 3 – Competitive Intelligence

Seller Comparison Table

Category Benchmarking

Revenue Heatmap

Page 4 – Market Positioning Analysis

Opportunity Quadrant

Pricing vs Rating Benchmarking

Tools Used

Power BI

DAX

Data Modeling (Star Schema)

Git & GitHub

Excel (Data preparation)