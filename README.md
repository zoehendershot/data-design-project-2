# DS 4320 Project 2: Clearing the Air: Using Data to Identify the Biggest Pollution Threats
### Executive Summary
This repository contains all materials for a data analysis project focused on predicting air quality using environmental pollutant data. This project repository features a complete data pipeline built in Python, with a separate notebook for data cleaning and transformation. In addition, it contains a visualization of key findings, a press release written for a general audience, and supporting documentation such as a data dictionary and domain context. A license is also included to support reproducibility and proper use of the project materials. 

### Zoe Hendershot

### njd5rd

### DOI
[![DOI](https://zenodo.org/badge/1226654080.svg)](https://doi.org/10.5281/zenodo.19956331)

### Press release - link
[Air Pollution Trends Reveal PM2.5 as Primary Driver of Unhealthy Air Days in Virginia](./p2pressrelease.md)

### link to pipeline files
[Data Pipeline Markdown File](https://github.com/zoehendershot/data-design-project-2/blob/main/p2pipeline.md)

[Data Pipeline Jupyter Notebook File](https://github.com/zoehendershot/data-design-project-2/blob/main/project2pipeline.ipynb)

### License
This project is licensed under the MIT License.  
See the LICENSE file for details:  
[LICENSE](https://github.com/zoehendershot/data-design-project-2/blob/main/LICENSE)

## Problem Definition
### State the initial general problem and refined specific problem statement
Initial General Problem: Predicting Air Quality

Refined Specific Problem: Can we predict whether a location in Virginia will experience an unhealthy air quality day (AQI > 50) using daily pollutant measurements (PM2.5, ozone, and NO₂) from 2024–2025, and identify which pollutant is the strongest driver of poor air quality?

Refinement Rationale: Predicting air quality is a big and complex topic, that could cover anything from long-term climate trends to detailed atmospheric modeling. To keep this project focused and manageable, I narrowed it down to predicting day-to-day air quality in Virginia using a small set of key pollutants. This makes the analysis clearer and easier to interpret without losing meaningful insight. I focused specifically on identifying days with less than 'good' air quality, which is indicated by an AQI above 50, which turns the problem into a classification problem and ties the results directly to real health guidelines.

Project Motivation: Air quality directly impacts public health, with poor air conditions linked to respiratory and cardiovascular issues. As climate change intensifies, bringing more wildfires, heat waves, and shifting weather patterns.  and urban areas continue to grow, understanding and anticipating changes in air quality has become more important than ever. This project aims to make air quality data easier to act on by spotting patterns in pollution levels before they become harmful. By using publicly available EPA monitoring data, this analysis shows how everyday environmental measurements can help us better understand and predict dangerous air quality events at a local level.

### Press Release
[Air Pollution Trends Reveal PM2.5 as Primary Driver of Unhealthy Air Days in Virginia](./p2pressrelease.md)

## Domain Exposition                          
### Terminology table
| Term / KPI                  | Definition                                                                                                        |
| --------------------------- | ----------------------------------------------------------------------------------------------------------------- |
| **AQI (Air Quality Index)** | A standardized scale (0–500) used to communicate how polluted the air is and its health impact.                   |
| **PM2.5**                   | Fine particulate matter (particles ≤ 2.5 micrometers) that can penetrate deep into the lungs and bloodstream.     |
| **Ozone**              | A gas formed when pollutants react in sunlight; high levels can irritate the respiratory system.                  |
| **NO₂(Nitrogen Dioxide)**  | A pollutant primarily from vehicle emissions and industrial activity; contributes to smog and respiratory issues. |
| **Unhealthy Air Day**       | A day where AQI exceeds 100, meaning sensitive groups and possibly the general public may be affected.            |
| **Monitoring Site**         | A physical EPA sensor location where pollutant levels are measured.                                               |
| **Daily Mean**              | The average pollutant concentration measured over a single day.                                                   |
| **AQI Category**            | Health-based classification (e.g., Good, Moderate, Unhealthy) derived from AQI values.                            |
| **Pollutant Concentration** | The measured amount of a pollutant in the air, typically in µg/m³ or ppm.                                         |


### Domain Explanation
This project operates within the domain of environmental data science, specifically focusing on air quality monitoring and public health analytics. Air quality is assessed through a network of monitoring stations that measure concentrations of key pollutants such as PM2.5, ozone, and nitrogen dioxide. These measurements are used to calculate the Air Quality Index (AQI), a standardized metric that translates pollutant levels into health-based categories. Governments and organizations, including the Environmental Protection Agency (EPA), use this data to inform the public about air conditions and potential health risks.

### Background Reading
[Air Quality Background Readings Folder](https://myuva-my.sharepoint.com/:f:/r/personal/njd5rd_virginia_edu/Documents/airqualitybackgroundreadings?csf=1&web=1&e=52nhbm)

### Background Reading Summary Table
| Title                                                      | Description                                                                                                         | Link to File                                                                       |
| ---------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- |
| Air Quality Index (AQI) Basics                             | Explains how AQI is calculated and how different levels correspond to health risk categories for the public.        | background_readings/Air Quality Index (AQI) Basics.url                             |
| Air Quality – Observations from Space (NASA)               | Describes how satellites are used to monitor air pollution globally and track large-scale environmental patterns.   | background_readings/Air Quality- Observations from Space NASA.url                  |
| EPA Health and Environmental Effects of Particulate Matter | Details the health impacts of PM2.5 exposure, including respiratory and cardiovascular risks.                       | background_readings/EPA Health and Environmental Effects of Particulate Matter.url |
| EPA Ozone Article                                          | Provides an overview of ground-level ozone formation, sources, and its effects on human health and the environment. | background_readings/EPA Ozone Article.url                                          |
| WHO Health Impacts of Air Pollution                        | Discusses the global health burden of air pollution and its links to major diseases and mortality.                  | background_readings/WHO Health impacts of Air Pollution.url                        |

## Data Creation
### Raw Data Acquisition Process (Provenance)
The raw data for this project was obtained from the U.S. Environmental Protection Agency's (EPA) AirData system using the Download Daily Data tool. This tool allows public access to query and download daily air quality summary statistics for major pollutants measured at monitoring sites across the United States. For this project, data was collected for PM2.5, ozone, and nitrogen dioxide (NO₂) for monitoring sites across Virginia for the years 2024 and 2025. The tool enables filtering by pollutant, year, and geographic area (such as state, county, or individual monitor), making it possible to retrieve targeted datasets.

The original CSV files (one for each pollutant per year, total of six files) were stored in their raw form before any processing, then relevant columns were then selected, standardized across pollutants, and combined across years. When multiple observations existed for the same site and date, I aggregated values to ensure one consistent measurement per pollutant per site per day. Finally, the cleaned datasets were merged into a unified dataset using shared keys (date and site ID), allowing analysis across pollutants.

### Code Table

| File Name                    | Description                                                                                                                                                                                                                                                                     | Link to Code                    |
| ---------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------- |
| `project2cleaning.ipynb` | loads raw CSV files, merges PM2.5, ozone, and NO₂ data across 2024–2025, cleans and standardizes variables, aggregates duplicate site-day observations, and engineer 'bad_air_day' variable for analysis | [data creation code](https://colab.research.google.com/drive/1huImCOG9L9EngrBCr4CBHGdkb1WxL3HC?usp=sharing) |

### Bias Identification
Bias in this dataset may be introduced through several aspects of the data collection process. Monitoring sites are not evenly distributed, with more sensors located in urban or high-population areas, which can lead to certain regions being overrepresented while others are underrepresented. Additionally, there can be multiple measurements recorded for the same site and date due to different instruments or methods, which may result in slight inconsistencies even after aggregation. Some observations are also missing or incomplete, meaning that not all days or locations are equally represented in the data. Finally, the analysis focuses on a limited set of pollutants (PM2.5, ozone, and NO₂), while overall air quality is influenced by additional factors, which may limit how fully the dataset captures real-world conditions.

### Bias Mitigation
Some of the biases in this dataset can be handled by being careful in how the data is cleaned and analyzed. For example, because there may be multiple measurements for the same site and day, taking an average helps create one consistent value and reduces small differences between readings. Missing or incomplete data can be managed by removing unreliable records or keeping them in mind when interpreting results. It’s also important to look at patterns across different locations instead of assuming the data represents all areas equally, since some regions have more monitoring sites than others. Finally, when looking at relationships between pollutants and AQI, it’s important to remember that AQI is based on pollutant levels, so the results should be interpreted with that in mind. Overall, by cleaning the data carefully and being thoughtful about how results are interpreted, the analysis can account for these limitations while still providing useful insights.

### Rationale for critical decisions
Several key decisions were made in preparing and analyzing the air quality dataset. One important decision was how to handle multiple measurements recorded for the same site and day. Because these differences are a result of how the data is collected (e.g., different instruments or methods), I chose to aggregate these values by taking the average rather than selecting a single observation. This allows the analysis to retain as much information as possible while creating a consistent structure for merging datasets.

Another decision involved limiting the analysis to three pollutants: PM2.5, ozone, and NO₂, even though overall air quality is influenced by additional factors. Rather than attempting to include every possible variable, which would add complexity and potential inconsistency, I focused on a small set of key pollutants that are widely used in air quality assessments. This keeps the analysis manageable while still capturing meaningful patterns.

There are also inherent limitations in how the data was collected that cannot be fully corrected. Monitoring sites are not evenly distributed, and some locations or days have missing or incomplete data. Instead of trying to artificially fill in these gaps, the approach taken is to acknowledge that the dataset reflects observed measurements at available sites, rather than perfectly representing all areas. Because of this, the analysis focuses on broader trends and relationships rather than highly localized conclusions.

Overall, the main strategy for handling uncertainty in this project is not to eliminate it, but to recognize where it exists and account for it in how results are interpreted. By being transparent about these decisions and limitations, the analysis remains grounded while still providing useful insights into air quality patterns.

## Metadata

### Implicit Schema
The document structure follows a consistent format where each document represents a single monitoring site on a given date. This means that every document captures one day of air quality data for a specific location, combining time, location, and pollutant measurements into a single record.

Each document includes the following fields: Date, Site ID, State, County, Local Site Name, Site Latitude, Site Longitude, pm25, aqi, ozone, and no2. These fields are consistent across all documents and directly reflect the structure of the cleaned dataset used in the analysis. Field names are standardized and values are stored in a consistent format (e.g., dates as datetime values, numeric pollutant measurements as floats), which ensures the data can be easily queried and analyzed.

Example Document:
{
  "Date": "2024-06-15",
  "Site ID": "510030001",
  "State": "Virginia",
  "County": "Albemarle",
  "Local Site Name": "Charlottesville",
  "Site Latitude": 38.0293,
  "Site Longitude": -78.4767,
  "pm25": 8.4,
  "aqi": 42,
  "ozone": 0.031,
  "no2": 12.5
}

### Summary of Database Contents

The database contains daily air quality observations collected from monitoring sites across Virginia for the years 2024 and 2025. Each record represents a single site on a single date and includes pollutant measurements along with location information.

| Attribute                  | Description                                                                                                              |
| -------------------------- | ------------------------------------------------------------------------------------------------------------------------ |
| **Number of Records**      | *12209*                                                                                                 |
| **Time Range**             | *Jan 2024 – Dec 2025*                                                                       |
| **Geographic Coverage**    | Virginia                                                                                                                 |
| **Number of Counties**     | *19*                                                                                  |
| **Number of Sites**        | *21*                                                                                 |
| **Unit of Observation**    | One site per day                                                                                                         |
| **Pollutants Included**    | PM2.5, Ozone, NO₂                                                                                                        |
| **Key Variables**          | pm25, ozone, no2, aqi                                                                                                    |
| **Location Variables**     | State, County, Site ID, Local Site Name, Site Latitude, Site Longitude                                                   |
| **Missing Ozone Values**   | *4890*                                                                                |
| **Missing NO₂ Values**     | *5511*                                                                                  |
| **Data Completeness Note** | PM2.5 and AQI are fully observed; ozone and NO₂ are missing for some site-days due to differences in monitoring coverage |


### Data Dictionary Table 

| Feature Name        | Data Type | Description                                                 | Example         |
| ------------------- | --------- | ----------------------------------------------------------- | --------------- |
| **Date**            | datetime  | The date of the air quality observation                     | 2024-06-15      |
| **Site ID**         | string    | Unique identifier for the monitoring site                   | 510030001       |
| **State**           | string    | State where the monitoring site is located                  | Virginia        |
| **County**          | string    | County where the monitoring site is located                 | Albemarle       |
| **Local Site Name** | string    | Name of the monitoring site                                 | Albemarle High School |
| **Site Latitude**   | float     | Latitude coordinate of the monitoring site                  | 38.0293         |
| **Site Longitude**  | float     | Longitude coordinate of the monitoring site                 | -78.4767        |
| **pm25**            | float     | Daily mean concentration of PM2.5 (fine particulate matter) | 8.4             |
| **aqi**             | integer   | Air Quality Index value representing overall air quality    | 42              |
| **ozone**           | float     | Daily maximum 8-hour ozone concentration                    | 0.031           |
| **no2**             | float     | Daily maximum 1-hour nitrogen dioxide concentration         | 12.5            |

## Quantification of uncertainty for numerical features

| Variable  | Data Type | Uncertainty Metric                                                                                                                                                                                                                                          |
| --------- | --------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **pm25**  | float     | Shows moderate variation (σ ≈ 3.43, CV ≈ 0.53), meaning PM2.5 levels change across days and locations but stay within a reasonable range. This reflects typical shifts in air conditions like weather and emissions.                                        |
| **aqi**   | integer   | Has moderate variation (σ ≈ 14.31, CV ≈ 0.42), indicating that overall air quality changes over time but is relatively stable compared to more localized pollutants. Since AQI is based on pollutant levels, its uncertainty is tied to those measurements. |
| **ozone** | float     | More stable overall (σ ≈ 0.0095, CV ≈ 0.24), showing smaller changes from day to day. However, ozone has missing values because not all monitoring sites record it, which adds uncertainty in analysis.                                                     |
| **no2**   | float     | Shows higher variation (σ ≈ 10.56, CV ≈ 0.65), meaning NO₂ levels can vary a lot depending on location and time. This is likely due to local sources like traffic and urban activity.                                                                       |






