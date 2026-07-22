# Data Science Salary Dashboard

An interactive Excel dashboard designed to analyze salaries for data science and tech roles (Data Analyst, Data Scientist, Data Engineer, Machine Learning Engineer, Software Engineer, etc.) globally.

## Overview

This project allows users to filter data based on:
- **Job Title**
- **Country**
- **Job Type** (Full-time, Contractor, Part-time, etc.)

Based on the selected filters, the dashboard dynamically displays:
- The **Median Annual Salary** for the selected criteria.
- A **Bar Chart** comparing salaries across different job titles.

## File Structure (Worksheets)

| Sheet Name | Description |
|---|---|
| `job` | Main Dashboard containing filters, key metrics, and the bar chart |
| `Data` | Raw data for all job postings (Title, Country, Schedule Type, Salary, Company, Skills, etc.) |
| `job_title` | List of job titles used for data validation/filtering |
| `country` | List of countries used for data validation/filtering |
| `type` | List of job types/schedules used for data validation/filtering |
| `platform` | Additional data regarding job posting platforms |

## Key Formulas & Logic

- **MEDIAN + IF (Array Formula):** Used to calculate the median salary dynamically based on multiple condition matches (Title, Country, Job Type):
  ```excel
  =MEDIAN(IF(
      (jobs[job_title_short]=title)*
      (jobs[job_country]=country)*
      (ISNUMBER(SEARCH(type,jobs[job_schedule_type])))*
      (jobs[salary_year_avg]<>0),
      jobs[salary_year_avg]
  ))
Named Ranges: Used named ranges (title, country, type) pointing to the filter selection cells (Dropdowns) on the dashboard sheet.

Data Validation: Configured drop-down lists for seamless user filtering.

How to Use
Open the job sheet.

Select your desired Job Title, Country, and Job Type from the drop-down menus.

The median salary and the bar chart will update automatically based on your selection.

