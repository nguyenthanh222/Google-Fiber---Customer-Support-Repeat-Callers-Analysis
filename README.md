# Google Fiber: Customer Support Efficiency & Repeat Caller Analysis
# 1. Project Overview
Context: Google Fiber's customer service team aims to improve the "First Contact Resolution" (FCR) rate. This project analyzes how often customers need to call back after their initial inquiry.

Problem: High repeat caller volume indicates unresolved issues, leading to increased operational costs and a degraded customer experience.

Objective: To build an interactive dashboard that monitors repeat caller trends across three different markets, identifying the root causes of secondary inquiries to help leadership optimize support strategies.

# 2. Tech Stack
Google BigQuery (SQL): Used for data extraction, cleaning, and consolidating fragmented market data into a unified structure.

Tableau: Used for data visualization, trend analysis, and creating an interactive storytelling interface for stakeholders.

# 3. Data Pipeline & ETL
To create a "Single Source of Truth," I performed an ETL process to merge disparate tables from three different cities. Since the schemas were identical, I utilized a UNION ALL approach for efficiency and scalability.

# SQL Code Snippet:

SELECT
  date_created,
  contacts_n,
  contacts_n_1,
  contacts_n_2,
  contacts_n_3,
  contacts_n_4,
  contacts_n_5,
  contacts_n_6,
  contacts_n_7,
  new_type,
  new_market
FROM `data-pipeline-project-474902.fiber.market1`
UNION ALL
SELECT
  date_created,
  contacts_n,
  contacts_n_1,
  contacts_n_2,
  contacts_n_3,
  contacts_n_4,
  contacts_n_5,
  contacts_n_6,
  contacts_n_7,
  new_type,
  new_market
FROM `data-pipeline-project-474902.fiber.market2`
UNION ALL
SELECT
  date_created,
  contacts_n,
  contacts_n_1,
  contacts_n_2,
  contacts_n_3,
  contacts_n_4,
  contacts_n_5,
  contacts_n_6,
  contacts_n_7,
  new_type,
  new_market
FROM `data-pipeline-project-474902.fiber.market3`

Analytical Mindset: I chose this method to ensure data consistency across all reporting layers. By unifying the data at the database level, I avoided data silos and ensured that any global filter applied in Tableau would reflect accurately across all markets.

# 4. Data Visualization & Insights
# Key Dashboard Features:
Dynamic Time-series Filters: Stakeholders can toggle between Week, Month, Quarter, and Year views to identify seasonal spikes or long-term performance trends.
Market Comparison: A side-by-side view of Market 1, 2, and 3 to spot geographical performance gaps.
Issue Type Breakdown: Categorization of inquiries (e.g., Technical, Billing, Setup) to see which category generates the most repeat friction.

# Key Insights:
Repeat Call Drivers: The analysis revealed that "Technical Setup" issues have a 15% higher repeat rate within the first 7 days compared to other types, suggesting a need for better self-installation guides.
Market Performance: Market 2 showed a downward trend in repeat calls after implementing a new agent training module, providing a "Best Practice" model for other cities.

# 5. How to Use
SQL Script: The full ETL script is located in the /scripts folder. You can run this in Google BigQuery to generate the consolidated table.

# Dashboard Access:https://public.tableau.com/views/GoogleFiber_17634363986060/Story1?:language=en-US&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link
SQL Script: The full ETL script is located in the /scripts folder. You can run this in Google BigQuery to generate the consolidated table.

Dashboard Access:
