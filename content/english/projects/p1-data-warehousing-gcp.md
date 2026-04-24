+++
title = "Urban Mobility Data Warehouse for NYC Taxi Trips"
date = 2025-10-21
description = "This project presents the design and implementation of a Data Warehouse (DW) in Google Cloud Platform (GCP) using BigQuery aimed at analyzing urban mobility patterns using New York City taxi trip data."
tags = ["Data", "Pipeline", "GCP", "BigQuery", "Data Warehousing"]
# externalLink = "https://github.com/..." # User can use this to link directly out
+++


# Table of Contents
 - [Project Overview](#project-overview)
 - [Dataset Description](#dataset-description)
 - [Dimensional Modeling](#dimensional-modeling)
 - [ELT Process](#elt-process)
 - [Dimension and Fact Tables in BigQuery](#dimension-and-fact-tables-in-bigquery)
 - [Final Dashboard](#final-dashboard)
 - [Technologies Used](#technologies-used)


## Project Overview

This project presents the design and implementation of a Data Warehouse (DW) in Google Cloud Platform (GCP) using BigQuery aimed at analyzing urban mobility patterns using New York City taxi trip data. The primary objective is to support efficient, data-driven decision-making by integrating, transforming, and organizing raw transactional data into a well-structured dimensional model optimized for analytical queries and dashboarding.

## Dataset Description
The dataset used in this project is the **New York City Taxi Trips** dataset available in BigQuery. The dataset contains information about taxi trips in New York City, including pickup and drop-off locations, trip distance, fare amount, total amount, passenger count, etc. For more information, please visit the [NYC website](https://www.nyc.gov/site/tlc/about/tlc-trip-record-data.page).

## Dimensional Modeling

The Data Warehouse was designed following the **star schema** approach to ensure simplicity, high query performance, and analytical flexibility.

### Model Components

- **Fact Table**
  - **fact_trips**: Stores key performance metrics, including trip distance, fare amount, total amount, and passenger count.

- **Dimension Tables**
  - **dim_time**: Captures temporal hierarchies such as day, month, year, and weekday.
  - **dim_location**: Describes pickup and drop-off zones.
  - **dim_payment**: Contains payment methods and their descriptions.
  - **dim_vendor**: Identifies taxi service providers.

This model enables multi-dimensional analysis by time, location, payment type, and vendor, providing valuable insights into urban transportation behavior.

![Star schema representation showing fact and dimension relationships.](/project_images/p1-gcp-bigquery/p1-1.png)

*Figure 1. Star schema representation showing fact and dimension relationships.*

## ELT Process

For this project the Extract, Load, and Transform (ELT) pattern was used. It consists of the following stages:

1. **Extraction**  
   Data is retrieved directly from BigQuery’s public NYC taxi trips dataset.

2. **Loading**  
   Data is loaded into BigQuery tables that are first used as staging tables under a **raw** schema to perform data cleaning and transformation.

3. **Transformation**  
   Data is then moved to a **processed** schema where it is cleaned, data types are normalized, and derived attributes are created. Subsequently, data is loaded into a **trusted** schema in the fact and dimension tables. Finally, materialized views are created to provide fast access to the data as it contains millions of records.


### Dimension and Fact Tables in BigQuery

![Bigquery data warehouse schema](/project_images/p1-gcp-bigquery/p1-3.png)

*Figure 2. Shows the BigQuery tables that make up the data warehouse.*


## Final Dashboard

Using **Looker Studio** connected to **BigQuery**, an interactive dashboard was developed to analyze operational and mobility patterns of NYC taxi services. The visualizations that it contains support insights into trip volumes, revenue distribution, temporal trends, and geographic demand, demonstrating the analytical value of the Data Warehouse design. You can access the dashboard [here](https://lookerstudio.google.com/reporting/ac9e3cf1-d247-479a-a1a0-eee83c33d6b9). 

Below is a screenshot of the dashboard, so you can get an idea of the data and visualizations that it contains.

![Dashboard screenshot](/project_images/p1-gcp-bigquery/p1-2.png)
*Figure 3. Dashboard screenshot.*


### Technologies Used
*   SQL
*   Google Cloud Platform (GCP)
*   BigQuery
*   Data Warehousing
*   Looker
