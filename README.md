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

The project showcases end-to-end data analysis using Power BI, starting from importing data from SQL databases and CSV files, cleaning and transforming it in Power Query, performing data modeling, and finally creating insightful visualizations. Explore the interactive Power BI dashboard live by clicking [here](https://app.powerbi.com/view?r=eyJrIjoiOWE5M2UwYzItOWM3MC00NDQxLWEzMDUtZjgxYTkwMzgyMzJlIiwidCI6ImM2ZTU0OWIzLTVmNDUtNDAzMi1hYWU5LWQ0MjQ0ZGM1YjJjNCJ9) to gain insights from the data visualizations.

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
 
  <p align="center"> 
  <img src= "https://github.com/satishsangwan/PowerBI_Business-Insights-360/blob/main/images/dim_customer.png" alt="dim_customer"/>  
  </p>
    

- **dim_market**:
  - 27 distinct markets.
  - 7 sub-zones and 4 regions: APAC, EU, LATAM, and NA.
    
  <p align="center"> 
  <img src= "https://github.com/satishsangwan/PowerBI_Business-Insights-360/blob/main/images/dim_market.png" alt="dim_market"/>  
  </p>
  
- **dim_product**:
  - Divisions: 
    - P & A (Peripherals & Accessories), PC (Notebook, Desktop), N & S (Networking & Storage).
  - 14 different product categories (e.g., Internal HDD, Keyboard) and multiple variants for each product.

  <p align="center"> 
  <img src= "https://github.com/satishsangwan/PowerBI_Business-Insights-360/blob/main/images/dim_product.png" alt="dim_product"/>  
  </p>
  
- **fact_forecast_monthly**:
  - Used for forecasting customer needs, leading to higher customer satisfaction and reduced warehousing costs.
  - The table is denormalized to streamline analytical work.
  - Dates are represented by the start of the month.
  - Contains a forecast quantity column, representing predicted demand for each customer.

  <p align="center"> 
  <img src= "https://github.com/satishsangwan/PowerBI_Business-Insights-360/blob/main/images/fact_forecast.png" alt="fact_forecast"/>  
  </p>
  
- **fact_sales_monthly**:
  - Similar to the fact_forecast_monthly table, but the final column represents actual sales (sold quantity) instead of forecasted values.

  <p align="center"> 
  <img src= "https://github.com/satishsangwan/PowerBI_Business-Insights-360/blob/main/images/fact_sales_monthly.png"alt="fact_sales_monthly"/>  
  </p>
    
### **gdb056 Database**
This database contains details related to pricing, manufacturing costs, and deductions. It includes the following key tables:

- **freight_cost**:
  - Contains details of travel costs and other logistics-related costs for each market, broken down by fiscal year.
    
<p align="center"> 
  <img src= "https://github.com/satishsangwan/PowerBI_Business-Insights-360/blob/main/images/freight_cost.png"alt="freight_cost"/> 
</p>
    
- **gross_price**:
  - Provides gross pricing information for products, based on product codes.

<p align="center"> 
  <img src= "https://github.com/satishsangwan/PowerBI_Business-Insights-360/blob/main/images/gross_price.png"alt="gross_price"/> 
</p>
      
- **manufacturing_cost**:
  - Contains manufacturing costs associated with each product, linked to the product code and year.

<p align="center"> 
<img src= "https://github.com/satishsangwan/PowerBI_Business-Insights-360/blob/main/images/manufacturing_cost.png"alt="manufacturing_cost"/> 
</p>
   
- **pre_invoice_deductions**:
  - Provides details of pre-invoice deduction percentages for each customer by year.

<p align="center"> 
<img src= "https://github.com/satishsangwan/PowerBI_Business-Insights-360/blob/main/images/pre_invoice_deductions.png" alt="pre_invoice_deductions"/> 
</p>
      
- **post_invoice_deductions**:
  - Contains post-invoice deduction details and other relevant deductions.

<p align="center"> 
<img src= "https://github.com/satishsangwan/PowerBI_Business-Insights-360/blob/main/images/post_invoice_deductions.png" alt="post_invoice_deductions"/> 
</p>

These tables are essential for conducting a thorough analysis, ranging from customer forecasting to understanding the impact of costs and pricing on profitability.

2. **CSV Files**: In addition to the MySQL databases, data from three CSV files was also used in this analysis. Each CSV file provides key information regarding sales targets, market share, and operating expenses. The following CSV files were incorporated:

- **1. Targets**:
  - Columns: Market, Month, Net Sales Target, Gross Margin Target, Net Profit Target.
  - This file contains the sales and financial performance targets set for each market, including goals for net sales, gross margins, and net profits.

<p align="center"> 
<img src= "https://github.com/satishsangwan/PowerBI_Business-Insights-360/blob/main/images/target.png" alt="targets"/> 
</p>
   

- **2. Market Share**:
  - Columns: Subzone, Category, Financial Year, Total Market Sales, Atliq Sales, Dale Sales, Innovo Sales, Pacer Sales, BP Sales, Other Sales.
  - This file details the market share across various subzones and product categories, broken down by financial year. It includes sales data from Atliq and its competitors (Dale, Innovo, Pacer, BP, and others).

<p align="center"> 
<img src= "https://github.com/satishsangwan/PowerBI_Business-Insights-360/blob/main/images/marketshare.png" alt="market_share"/> 
</p>    

- **3. Operating Expenses**:
  - Columns: Market, Fiscal Year, Ads & Promotions (%), Other Operational Expenses (%).
  - This file provides operational expense data, showing the percentage of expenses spent on ads, promotions, and other operational activities for each market and fiscal year.

<p align="center"> 
<img src= "https://github.com/satishsangwan/PowerBI_Business-Insights-360/blob/main/images/operational_expenses.png" alt="operating expenses"/> 
</p>   

These CSV files complement the database data by providing granular insights into the targets, competition, and operational costs in each market.

## **ETL Process (Data Cleaning)**
The data was cleaned using Power Query. Key steps included:
- Removing duplicates and errors.
- Filling in missing data.
- Standardizing data types and formats.
- Merging multiple tables.

## **Data Modeling**
The data modeling process involved creating relationships between multiple tables for efficient analysis. Key features:
- Snowflake schema design.
- Fact tables for sales, finance, and supply chain.
- Dimension tables for time, customers, products, and market.
  
<p align = "center">
  <img src="https://github.com/satishsangwan/PowerBI_Business-Insights-360/blob/main/images/Data%20Model%20Screenshot.png" alt = "Data Model" width = "800"/>
</p>

## **DAX Measures**
A wide range of DAX measures were created to generate key business insights, Here are few snippets of DAX Measures:
<p align="center">
  <img src="https://github.com/satishsangwan/PowerBI_Business-Insights-360/blob/main/images/Forecast%20QTY.png" alt="forecast" width="400"/>
  <img src="https://github.com/satishsangwan/PowerBI_Business-Insights-360/blob/main/images/P%20%26%20L%20Final%20Value.png" alt="P & L Final Value" width="400"/>
</p>
<p align="center">
  <img src="https://github.com/satishsangwan/PowerBI_Business-Insights-360/blob/main/images/P%20%26%20L%20BM.png" alt="P & L BM" width="400"/>
  <img src="https://github.com/satishsangwan/PowerBI_Business-Insights-360/blob/main/images/P%20%26%20L%20Chg%20%25.png" alt="P & L chg %" width="400"/>
</p>
<p align="center">
  <img src="https://github.com/satishsangwan/PowerBI_Business-Insights-360/blob/main/images/Net%20Error%20LY.png" alt="Net Error LY" width="400"/>
  <img src="https://github.com/satishsangwan/PowerBI_Business-Insights-360/blob/main/images/Reference%20Label.png" alt="Reference Label" width="400"/>
</p>
<p align = "center">
  <img src="https://github.com/satishsangwan/PowerBI_Business-Insights-360/blob/main/images/P%20%26%20L%20Values.png" alt = "P & L Values" width = "600"/>
</p>

## **Dashboards**
### **Home Page (Navigation)**
- A user-friendly homepage providing navigation to all functional dashboards.
<p align = "center">
  <img src="https://github.com/satishsangwan/PowerBI_Business-Insights-360/blob/main/images/dashboards/HomePage.gif" alt = "Home" />
</p>

### **Finance Dashboard**
- Overview of revenue, expenses, and profitability.
- Key KPIs: Gross Margin, Operating Income, Net Profit.

<p align = "center">
<img src="https://github.com/satishsangwan/PowerBI_Business-Insights-360/blob/main/images/dashboards/Finance_Mockup.png" alt = "Financemockup" width="650"/>
<img src="https://github.com/satishsangwan/PowerBI_Business-Insights-360/blob/main/images/dashboards/Finance.gif" alt = "Finance" width="650"/>
</p>

### **Sales Dashboard**
- Sales performance by region, product category, and sales channel.
- KPIs: Total Sales, Year-over-Year Growth, Sales by Channel.

<p align = "center">
<img src="https://github.com/satishsangwan/PowerBI_Business-Insights-360/blob/main/images/dashboards/Sales_Mockup.png" alt = "salesmockup" width="650"/>
<img src="https://github.com/satishsangwan/PowerBI_Business-Insights-360/blob/main/images/dashboards/Sales.gif" alt = "sales" width="650"/>
</p>


### **Marketing Dashboard**
- Campaign analysis and customer engagement metrics.
- KPIs: Conversion Rate, Cost per Lead, Return on Marketing Investment (ROMI).

<p align = "center">
<img src="https://github.com/satishsangwan/PowerBI_Business-Insights-360/blob/main/images/dashboards/Marketing%20Mockup.png
" alt = "marketingmockup" width="650"/>
<img src="https://github.com/satishsangwan/PowerBI_Business-Insights-360/blob/main/images/dashboards/Marketing.gif" alt = "marketing" width="650"/>
</p>

### **Supply Chain Dashboard**
- Key metrics for supply chain operations: stock levels, delivery times, and order fulfillment.
- KPIs: Inventory Turnover, Lead Time, Stock-out Rate.

<p align = "center">
<img src="https://github.com/satishsangwan/PowerBI_Business-Insights-360/blob/main/images/dashboards/Supply%20Chain%20Mockup.png" alt = "supplychainmockup" width="650"/>
<img src="https://github.com/satishsangwan/PowerBI_Business-Insights-360/blob/main/images/dashboards/SupplyChain.gif" alt = "supplychain" width="650"/>
</p>

### **Executive Overview Dashboard**
- High-level insights combining financial, sales, and operational data.
- KPIs: Total Revenue, Profit Margins, Business Growth, and overall performance.

<p align = "center">
<img src="https://github.com/satishsangwan/PowerBI_Business-Insights-360/blob/main/images/dashboards/Executive.gif" alt = "supplychain" width="650"/>
</p>


## **Technology Stack**
- **Power BI Desktop**: For data modeling and dashboard creation.
- **SQL**: For querying the database and extracting data.
- **Power Query**: For data transformation and cleaning.
- **DAX**: For measures and calculated columns.
- **DAX Studio**: For opimizing the report performance
- **Power BI Service**: For sharing the report with stakeholders
- **Project Charter File**
- **Excel**

## **Conclusion**
This project demonstrates an in-depth approach to data analysis, covering multiple functional domains within the FMCG sector. By utilizing Power BI's powerful data visualization and modeling capabilities, the project provides actionable insights to improve decision-making in finance, sales, marketing, and supply chain.
