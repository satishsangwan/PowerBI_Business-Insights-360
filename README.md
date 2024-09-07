<h1 align="center">Business Insights 360</h1> 

# Project: Business Insights 360 Dashboard for Finance, Sales, Marketing, Supply Chain and Executive

## Project Description


**Domain:** FMCG  
**Function:** Executive, Finance, Sales, Marketing, Supply Chain  
**Company:** AtliQ Hardwares 

AtliQ Hardwares is a consumer electronics company expanding rapidly but is not able to compete with other companies using data as most of their report still exists in Excel. My goal is to implement an advanced analytics solution using Power BI that will enable the company to get insights and make informed decisions. In this project, the goal is to be one report which could be used by stakeholders from sales, marketing, finance and executive team. The focus is made on the following :

1. Robust Data Modeling
2. User-empathetic Report design
3. Drillable Insights

## **Table of Contents**
- [Introduction](#introduction)
- [Project Overview](#project-overview)
- [Data Sources](#data-sources)
- [ETL Process (Data Cleaning)](#etl-process-data-cleaning)
- [Data Modeling](#data-modeling)
- [DAX Measures](#dax-measures)
- [Dashboards](#dashboards)
  - [Finance Dashboard](#finance-dashboard)
  - [Sales Dashboard](#sales-dashboard)
  - [Marketing Dashboard](#marketing-dashboard)
  - [Supply Chain Dashboard](#supply-chain-dashboard)
  - [Executive Overview Dashboard](#executive-overview-dashboard)
  - [Home Page](#home-page-navigation)
- [Technology Stack](#technology-stack)
- [Media & Visualizations](#media--visualizations)
- [Conclusion](#conclusion)

## **Introduction**
In this project, I analyzed comprehensive datasets from the FMCG domain, covering multiple functional areas such as finance, sales, marketing, supply chain, and executive operations. The project includes individual dashboards for each function, along with a home page for easy navigation.

The project showcases end-to-end data analysis using Power BI, starting from importing data from SQL databases and CSV files, cleaning and transforming it in Power Query, performing data modeling, and finally creating insightful visualizations.

## **Project Overview**
This project follows a systematic approach:
- **Data Import**: Data was sourced from two different locations: SQL database and CSV files.
- **Data Cleaning**: Implemented using Power Query for transformation, dealing with missing values, duplicates, and other irregularities.
- **Data Modeling**: Created relationships between tables, optimized the model for analysis.
- **DAX Measures**: Developed multiple DAX measures to provide KPIs, metrics, and insights for different business functions.
- **Visualizations**: Designed interactive and user-friendly dashboards for each function with a navigation home page.

## **Data Sources**
1. **SQL Database**: The data for this project comes from two distinct MySQL databases: **gdb041** and **gdb056**. Understanding the structure and content of these databases is essential for conducting effective analysis.

### **gdb041 Database**
This database contains information related to customers, markets, products, and sales forecasts. It includes the following key tables:

- **dim_customer**:
  - 27 distinct markets (e.g., India, USA, Spain).
  - 75 distinct customers across these markets.
  - Two platform types: 
    - Brick & Mortar (Physical/offline stores).
    - E-commerce (Online platforms like Amazon, Flipkart).
  - Three sales channels: Retailer, Direct, and Distributors.
    ![dim_customer](https://github.com/satishsangwan/PowerBI_Business-Insights-360/blob/main/images/dim_customer.png)

- **dim_market**:
  - 27 distinct markets.
  - 7 sub-zones and 4 regions: APAC, EU, LATAM, and others (nan).
    
  <img align="centre" alt="dim_market" src= "https://github.com/satishsangwan/PowerBI_Business-Insights-360/blob/main/images/dim_market.png"/>  
 
- **dim_product**:
  - Divisions: 
    - P & A (Peripherals & Accessories), PC (Notebook, Desktop), N & S (Networking & Storage).
  - 14 different product categories (e.g., Internal HDD, Keyboard) and multiple variants for each product.
   ![dim_product](https://github.com/satishsangwan/PowerBI_Business-Insights-360/blob/main/images/dim_product.png)
- **fact_forecast_monthly**:
  - Used for forecasting customer needs, leading to higher customer satisfaction and reduced warehousing costs.
  - The table is denormalized to streamline analytical work.
  - Dates are represented by the start of the month.
  - Contains a forecast quantity column, representing predicted demand for each customer.
   ![fact_forecast](https://github.com/satishsangwan/PowerBI_Business-Insights-360/blob/main/images/fact_forecast.png)
- **fact_sales_monthly**:
  - Similar to the fact_forecast_monthly table, but the final column represents actual sales (sold quantity) instead of forecasted values.
    ![fact_sales](https://github.com/satishsangwan/PowerBI_Business-Insights-360/blob/main/images/fact_sales_monthly.png)

### **gdb056 Database**
This database contains details related to pricing, manufacturing costs, and deductions. It includes the following key tables:

- **freight_cost**:
  - Contains details of travel costs and other logistics-related costs for each market, broken down by fiscal year.

    ![freight_cost](https://github.com/satishsangwan/PowerBI_Business-Insights-360/blob/main/images/freight_cost.png)

- **gross_price**:
  - Provides gross pricing information for products, based on product codes.

    ![gross_price](https://github.com/satishsangwan/PowerBI_Business-Insights-360/blob/main/images/gross_price.png)
    
- **manufacturing_cost**:
  - Contains manufacturing costs associated with each product, linked to the product code and year.

    ![manufacturing_cost](https://github.com/satishsangwan/PowerBI_Business-Insights-360/blob/main/images/manufacturing_cost.png)
    
- **pre_invoice_deductions**:
  - Provides details of pre-invoice deduction percentages for each customer by year.

    ![pre_invoice_deductions](https://github.com/satishsangwan/PowerBI_Business-Insights-360/blob/main/images/pre_invoice_deductions.png)
    
- **post_invoice_deductions**:
  - Contains post-invoice deduction details and other relevant deductions.
 
    ![post_invoice_deductions](https://github.com/satishsangwan/PowerBI_Business-Insights-360/blob/main/images/post_invoice_deductions.png)

These tables are essential for conducting a thorough analysis, ranging from customer forecasting to understanding the impact of costs and pricing on profitability.

2. **CSV Files**: In addition to the MySQL databases, data from three CSV files was also used in this analysis. Each CSV file provides key information regarding sales targets, market share, and operating expenses. The following CSV files were incorporated:

- **1. Targets**:
  - Columns: Market, Month, Net Sales Target, Gross Margin Target, Net Profit Target.
  - This file contains the sales and financial performance targets set for each market, including goals for net sales, gross margins, and net profits.
 
    ![targets](https://github.com/satishsangwan/PowerBI_Business-Insights-360/blob/main/images/target.png)

- **2. Market Share**:
  - Columns: Subzone, Category, Financial Year, Total Market Sales, Atliq Sales, Dale Sales, Innovo Sales, Pacer Sales, BP Sales, Other Sales.
  - This file details the market share across various subzones and product categories, broken down by financial year. It includes sales data from Atliq and its competitors (Dale, Innovo, Pacer, BP, and others).
 
    ![marketshare](https://github.com/satishsangwan/PowerBI_Business-Insights-360/blob/main/images/marketshare.png)

- **3. Operating Expenses**:
  - Columns: Market, Fiscal Year, Ads & Promotions (%), Other Operational Expenses (%).
  - This file provides operational expense data, showing the percentage of expenses spent on ads, promotions, and other operational activities for each market and fiscal year.
 
    ![operatingexpense](https://github.com/satishsangwan/PowerBI_Business-Insights-360/blob/main/images/operational_expenses.png)

These CSV files complement the database data by providing granular insights into the targets, competition, and operational costs in each market.

## **ETL Process (Data Cleaning)**
The data was cleaned using Power Query. Key steps included:
- Removing duplicates and errors.
- Filling in missing data.
- Standardizing data types and formats.
- Merging multiple tables.

**Media**:  
Include screenshots of:
- Power Query transformation steps.
- Before and after cleaning process comparison.

## **Data Modeling**
The data modeling process involved creating relationships between multiple tables for efficient analysis. Key features:
- Snowflake schema design.
- Fact tables for sales, finance, and supply chain.
- Dimension tables for time, customers, products, and market.

![Data_Model](https://github.com/satishsangwan/PowerBI_Business-Insights-360/blob/main/images/Data%20Model%20Screenshot.png)

## **DAX Measures**
A wide range of DAX measures were created to generate key business insights:
- **Finance**: Revenue, cost analysis, profit margins.
- **Sales**: Sales volume, average order value, growth percentages.
- **Marketing**: Campaign performance, conversion rates.
- **Supply Chain**: Inventory turnover, delivery time analysis.

**Media**:  
Include snippets of key DAX code along with a brief explanation of their purpose.

## **Dashboards**

### **Finance Dashboard**
- Overview of revenue, expenses, and profitability.
- Key KPIs: Gross Margin, Operating Income, Net Profit.

**Media**:  
Provide screenshots of the finance dashboard, highlighting KPIs and visuals like line charts and bar graphs.

### **Sales Dashboard**
- Sales performance by region, product category, and sales channel.
- KPIs: Total Sales, Year-over-Year Growth, Sales by Channel.

**Media**:  
Add screenshots of sales dashboard visuals, such as pie charts for regional distribution and line graphs for sales trends.

### **Marketing Dashboard**
- Campaign analysis and customer engagement metrics.
- KPIs: Conversion Rate, Cost per Lead, Return on Marketing Investment (ROMI).

**Media**:  
Include visuals like funnel charts and bar graphs showcasing campaign performance.

### **Supply Chain Dashboard**
- Key metrics for supply chain operations: stock levels, delivery times, and order fulfillment.
- KPIs: Inventory Turnover, Lead Time, Stock-out Rate.

**Media**:  
Add charts such as stacked columns for stock levels, maps for delivery regions, etc.

### **Executive Overview Dashboard**
- High-level insights combining financial, sales, and operational data.
- KPIs: Total Revenue, Profit Margins, Business Growth, and overall performance.

**Media**:  
Provide a screenshot of a holistic executive dashboard summarizing key metrics from all functional areas.

### **Home Page (Navigation)**
- A user-friendly homepage providing navigation to all functional dashboards.

**Media**:  
Include an image of the navigation page, showing clickable buttons or links to each dashboard.

## **Technology Stack**
- **Power BI**: For data modeling and dashboard creation.
- **SQL**: For querying the database and extracting data.
- **Power Query**: For data transformation and cleaning.
- **DAX**: For measures and calculated columns.

## **Media & Visualizations**
Including visuals is crucial for engaging visitors and showcasing your work. Suggested media:
- **Screenshots**: Include clear, high-quality images of each dashboard and process step.
- **Animated GIFs**: For showcasing the interactive nature of the dashboards (e.g., filter interactions).
- **Video**: Consider adding a short video demo walking through the dashboards and functionality.
- **Power BI Report Link**: If possible, provide a live link to your Power BI report hosted on a platform like Power BI service.

## **Conclusion**
This project demonstrates an in-depth approach to data analysis, covering multiple functional domains within the FMCG sector. By utilizing Power BI's powerful data visualization and modeling capabilities, the project provides actionable insights to improve decision-making in finance, sales, marketing, and supply chain.
