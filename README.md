![photo_5769571513547210539_x](https://github.com/ammu993/Customer-Demographics-Analysis/assets/74145869/7e19eb16-7ca0-47da-84f1-84230135a2d9)

# Customer Demographics Analysis

## Overview
An in-depth customer demographics analysis that utilized <b>Tableau</b> and <b> BigQuery </b>  to create two interactive dashboards: one tailored for executive decision-making and the other providing actionable insights for Marketing and Sales teams. 

## Project Structure
Employing the 6 steps of the Data Analysis Process - **ASK**, **PREPARE**, **PROCESS**, **ANALYZE**, **SHARE**, **ACT**- in this project two dashboards and presentations were created for two different audiences, Executive Leadership and Sales & Marketing Team. Taking into account the time availability, decision-making power, and data literacy of each group of target audience, the presentations and dashboard were structured in the following manner:  
-To Executive Leadership - short, high-level, and strategic content that communicates the problem, its importance, and how the solution could help to achieve the goals of the organization. Focus on  the big picture, performance metrics, and cost-benefit analysis.  
-To Sales & Marketing Team - specific and tactical that provides more details on how the outcome of the analysis will impact their specific area of the organization and how they can contribute to the success of the problem-solving.  

## Tools Used  
BigQuery, Excel, Tableau, Google Slides 

## Data Source
AdventureWorks Sample Database 2001-2004  

## Problem (ASK)
Based on the initial exploration of the AdventureWorks Sample Database in previous projects, I identified the following problems and questions, which are of relevance to the Executives and S&M teams respectively: 
 1. Online sales are underperforming in comparison to offline sales channels --> How to improve Online sales?
 2. The number of monthly new customer acquisitions has been declining in the recent fiscal year -->How to improve the number of new customer acquisitions?   
*Using the insights on behaviors, preferences, and traits through customer demographics analysis, I address these problems.*

## Data Cleaning and Preprocessing (PREPARE & PROCESS)
Code snippet to extract Age and Gender of online customers
```sql
 SELECT
    CustomerID,
    PARSE_DATE('%Y-%m-%d', REPLACE(REGEXP_EXTRACT(Demographics, r'<BirthDate>(.*?)<\/BirthDate>'),'Z',' ')) AS birthdate,
    REGEXP_EXTRACT(Demographics, r'<Gender>(.*?)<\/Gender>') AS gender,
    2004 - EXTRACT(YEAR
    FROM
      PARSE_DATE('%Y-%m-%d', REPLACE(REGEXP_EXTRACT(Demographics, r'<BirthDate>(.*?)<\/BirthDate>'),'Z',' '))) AS age_ind_customer
  FROM
    `adwentureworks_db.individual`
```
3 Data sources queried using BigQuery were added to Tableau Public for creating the Dashboards

## Analysis and Visualizations (SHARE)
### **[EXECUTIVE DASHBOARD](https://public.tableau.com/views/AdWorksExecutiveSummarybasedonOnlineCustomerDemographics/ExecutiveSummaryDashboard2?:language=en-US&:display_count=n&:origin=viz_share_link)**   
(Filters: Year of order, Country, Type of Sale)   
* Measured KPIs: Total Online Revenue(USD), Count of Orders Count of Customers, Sales type by Country  
* Online Customer Demographics :   
Age Groups (20-29, 30-39 etc) - Average age of Customer, Highest revenue-generating age group
Gender - Count (%) of Customers by Gender
Frequency of purchase by Country

![Executive Summary Dashboard (2) (2)](https://github.com/ammu993/Customer-Demographics-Analysis/assets/74145869/de307184-2d8d-4265-8ff0-6dba9799b6cb)

*The dashboards are linked. By clicking the arrow next to Online Customer Demographics Insights one can view the SALES & MARKETING DASHBOARD*  

### **[SALES & MARKETING DASHBOARD](https://public.tableau.com/views/AdWorksSalesMarketingbasedonOnlineCustomerDemographics/OnlineSalesOverviewforSalesMarketingTeam?:language=en-US&:display_count=n&:origin=viz_share_link)**   
(Filters: Country, Gender, Fiscal Year; <kbd> Choose Age Group </kbd> filter dynamically adjusts all charts and KPIs on the dashboard to reflect proportional changes)
* Measured KPIs: Total Online Revenue, Count of Online Customers, Top 3 products by Sales, Top 3 products by volume
* Charts: Monthly New Customer Acquisitions by country, Total revenue by Fiscal year
* Drill downs: Count of Reason Type in %, Popularity of products by volume

![Online Sales Overview for Sales   Marketing Team (3)](https://github.com/ammu993/Customer-Demographics-Analysis/assets/74145869/f9a1e1b9-c8d0-4e08-91bf-1e5f55b94bc9)

## Recommendations (ACT)

Based on the analyses conducted to address the questions of "How to improve Online sales?" and "How to improve the number of new customer acquisitions?", which involved gaining insights into customer demographics, purchasing behavior, and preferences, the following general recommendations for further actions were proposed:  
* Gain insights on gender and revenue distribution across age groups to understand customer behavior and preferences.
* Analyze popular products among different age groups to tailor offerings and improve sales.
* Implement data-driven targeted marketing strategies based on online customer demographics to enhance customer loyalty and engagement, and improve both online and offline sales.

Presentations :  
[exec][Executive Ppt.pdf](https://github.com/ammu993/Customer-Demographics-Analysis/files/14234560/Executive.Ppt.pdf)   
[Sales & Marketing][Sales & Marketing.pdf](https://github.com/ammu993/Customer-Demographics-Analysis/files/14234562/Sales.Marketing.pdf)

## Challenges and Limitations
Given the dataset's age of nearly 20 years, the recommendations presented were crafted by considering online customer behavior and technological advancements prevalent during the early 2000s.
