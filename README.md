# Cyclistic Bike-Share Customer Behavior Analysis
### Google Data Analytics Specialization - Capstone Project

![Excel](https://img.shields.io/badge/Excel-217346?logo=microsoft-excel&logoColor=white)
![SQL](https://img.shields.io/badge/SQL-005C84?logo=database&logoColor=white)
![R](https://img.shields.io/badge/R-276DC3?logo=r&logoColor=white)

---

## Table of Contents

- [Overview](#overview)
- [Business Task](#business-task)
- [Objectives](#objectives)
- [Dataset](#dataset)
- [Tools & Technologies](#tools--technologies)
- [Methodology](#methodology)
- [SQL Analysis Results](#sql-analysis-results)
- [Visualizations](#visualizations)
- [Key Performance Indicators](#key-performance-indicators)
- [Key Findings](#key-findings)
- [Business Recommendations](#business-recommendations)
- [Repository Contents](#repository-contents)

---

## Overview

This capstone project analyzes the Cyclistic (Divvy) Q1 2020 bike-share dataset to understand how casual riders and annual members use the service differently, and to translate that difference into marketing recommendations that increase membership conversions. The analysis follows the Google Data Analytics case study framework (Ask → Prepare → Process → Analyze → Share → Act) and was built across Excel, MySQL, and RStudio (tidyverse, lubridate, ggplot2).

---

## Business Task

**Key question:** How do annual members and casual riders use Cyclistic bikes differently?

Cyclistic's business goal is to convert casual riders into annual members through targeted, data-driven marketing campaigns rather than broad, undifferentiated outreach.

---

## Objectives

- Quantify ride-behavior differences between casual riders and annual members
- Identify day-of-week and hourly usage patterns for each rider type
- Locate geographic hotspots specific to casual rider activity
- Build cross-tool (Excel/SQL/R) analysis to validate findings consistently
- Convert findings into concrete, actionable membership-conversion strategies

---

## Dataset

| Attribute | Detail |
|---|---|
| Source | Divvy Q1 2020 public dataset (Motivate International Inc.) |
| Original Size | 300,000+ rows |
| Working Sample | 8,036 rows (sampled to preserve distribution and patterns while enabling smooth cross-tool analysis) |
| Data Standard | Reliable, Original, Comprehensive, Current, Cited (ROCCC) |
| PII | None included |

**Raw attributes:** `ride_id`, `rideable_type`, `started_at`, `ended_at`, `start_station_name`, `start_station_id`, `end_station_name`, `end_station_id`, `start_lat`, `start_lng`, `end_lat`, `end_lng`, `member_casual`

**Engineered attributes:**

| Tool | New Fields |
|---|---|
| Excel | `ride_length`, `day_of_week`, `start_hour`, `start_month` |
| SQL | `started_at_dt`, `ended_at_dt`, `ride_length_secs`, `ride_length_mins` |
| R | `weekday`, `started_hour_new`, `started_month_new`, `started_date`, `is_weekend` |

---

## Tools & Technologies

| Category | Tools |
|---|---|
| Data Cleaning & Dashboards | Microsoft Excel |
| Database & Query | MySQL Workbench 8.0 |
| Analysis & Visualization | RStudio |
| R Libraries | tidyverse, dplyr, lubridate, ggplot2 |

---

## Methodology

**1. Ask - Define the Business Task**
Framed the core question (member vs. casual usage difference) around Cyclistic's stated goal of increasing membership conversion.

**2. Prepare - Data Source & Credibility**
Sourced the Divvy Q1 2020 public dataset, verified it against the ROCCC data-quality standard, and confirmed no PII was present before working across Excel, MySQL, and RStudio.

**3. Process - Cleaning & Feature Engineering**
In Excel: converted timestamps, calculated ride length, added weekday/hour/month columns, and removed invalid or zero-duration rides. In SQL and R, mirrored this feature engineering to support cross-validation between tools (see engineered attributes table above).

**4. Analyze - SQL & R**
Ran SQL aggregations to validate data integrity (row counts, missing values, date ranges) and compute ride-duration and usage-volume metrics by rider type. Extended this analysis in R with grouped summaries and statistical comparisons.

**5. Share - Visualization**
Built an Excel KPI dashboard and 6 ggplot2 visualizations in R to communicate member vs. casual usage patterns clearly.

**6. Act - Recommendations**
Converted the analysis into 3 specific marketing strategies aimed at converting casual riders into annual members.

---

## SQL Analysis Results

All queries in [`cyclistic_analysis.sql`](./cyclistic_analysis.sql); all screenshots in [`Cylistic_analysis_results`](./Cylistic_analysis_results).

| # | Result | Screenshot |
|---|--------|------------|
| 1 | Total rows loaded — confirms successful import into MySQL | ![Total Rows](Cylistic_analysis_results/total_rows_sql.png) |
| 2 | Missing values check — count of missing/NULL values per column | ![Missing Values](Cylistic_analysis_results/missing_values_sql.png) |
| 3 | First 10 rows preview — verifies formatting and integrity | ![Preview 10 Rows](Cylistic_analysis_results/10_rows_sql.png) |
| 4 | Average ride duration — mean ride duration via SQL aggregates | ![Average Ride Duration](Cylistic_analysis_results/avg_ride_minutes_sql.png) |
| 5 | Maximum ride duration — longest recorded ride | ![Max Ride Duration](Cylistic_analysis_results/max_ride_minutes.png) |
| 6 | Ride length (seconds & minutes) — computed duration fields | ![Ride Length](Cylistic_analysis_results/ride_length_and_secs_sql.png) |
| 7 | Most active day of week — weekday with highest total rides | ![Most Active Day](Cylistic_analysis_results/hightest_day_of_week_sql.png) |
| 8 | Avg ride duration, member vs. casual — direct comparison | ![Avg Ride Duration User Type](Cylistic_analysis_results/member_casual_avg_ride_mints_Sql.png) |
| 9 | Total rides, member vs. casual — trip counts per rider category | ![Total Rides User Type](Cylistic_analysis_results/member_casual_total_rides_sql.png) |
| 10 | Hourly ride distribution — peak riding hours | ![Hourly Ride Distribution](Cylistic_analysis_results/hightest_rides_by_hour_sql.png) |
| 11 | Monthly ride distribution — seasonal ride trends | ![Monthly Ride Distribution](Cylistic_analysis_results/hightest_rides_by_month_sql.png) |

---

## Visualizations

**Excel Dashboard**

| Dashboard | Description |
|---|---|
| ![excel_dashboard](Cylistic_analysis_results/excel_dashboard.png) | Overview of key KPIs, ride distribution trends, and user-type comparisons |

**R Visualizations**

| # | Chart | Description |
|---|-------|-------------|
| 1 | ![ride_length_summary_R](Cylistic_analysis_results/ride_length_summary_R.png) | Ride Length Summary — overall spread and distribution of ride durations |
| 2 | ![avg_ride_length_R](Cylistic_analysis_results/avg_ride_length_R.png) | Average Ride Length by User Type — casual riders take notably longer rides |
| 3 | ![avg_ride_length_by_week_of_day_R](Cylistic_analysis_results/avg_ride_length_by_week_of_day.png) | Average Ride Length by Day of Week — variation across weekdays/weekends by user type |
| 4 | ![number_of_rides_by_day_R](Cylistic_analysis_results/number_of_rides_by_day_R.png) | Number of Rides by Day — total ride volume per weekday |
| 5 | ![hourly_usage_pattern_by_user_type_R](Cylistic_analysis_results/hourly_usage_pattern_by_user_type_R.png) | Hourly Usage Pattern by User Type — differing peak hours (commuting vs. leisure) |
| 6 | ![top_start_stations_by_user_type_R](Cylistic_analysis_results/top_start_stations_by_user_type_R.png) | Top Start Stations by User Type — most-used stations per rider category |

---

## Key Performance Indicators

| KPI | Result |
|---|---|
| Sample Size Analyzed | 8,036 rides |
| Avg. Ride Duration — Casual | ~388 minutes |
| Avg. Ride Duration — Member | ~279 minutes |
| Member Share of Total Rides | 90%+ |
| Member Peak Hours | 7–9 AM, 4–6 PM |
| Casual Peak Period | Mid-day & afternoon |

---

## Key Findings

- **Ride duration:** Casual riders average ~388 minutes per ride vs. ~279 minutes for members — casual usage skews toward longer, leisure-style trips.
- **Usage volume:** Members account for over 90% of total rides, making them the dominant user base by volume despite shorter average trips.
- **Day patterns:** Casual riders peak mid-week and on weekends; members show stable weekday usage consistent with commuting.
- **Hourly patterns:** Members peak at classic commute windows (7–9 AM, 4–6 PM); casual riders peak mid-day and in the afternoon.
- **Geographic hotspots:** Casual rider activity concentrates around Michigan Ave & Washington St, Millennium Park, and Lake Shore Dr & Monroe St — all leisure/tourist-adjacent locations.

---

## Business Recommendations

1. **Target casual riders at leisure-heavy stations** — focus campaigns at Millennium Park, the Lakefront, and Michigan Ave using QR codes, in-app offers, and tourist-focused promotions.
2. **Introduce weekend/tourist-friendly membership tiers** — e.g., a Weekend Unlimited Pass or a Tourist-to-Monthly upgrade discount, matching how casual riders actually use the service.
3. **Lead digital marketing with cost and convenience messaging** — emphasize savings, unlimited rides, and rewards, since these levers align directly with observed casual-rider behavior.

---

## Repository Contents

| File | Description |
|---|---|
| `cyclistic_analysis.xlsx` | Excel cleaning, pivot tables, dashboard, KPI metrics |
| `cyclistic_analysis.sql` | SQL cleaning and analysis queries |
| `cyclistic_analysis.R` | R data cleaning, analysis, and ggplot2 visualizations |
| `cyclistic_workspace.RData` | Saved R environment |
| `Cylistic_analysis_results/` | All SQL and R output screenshots |

---
