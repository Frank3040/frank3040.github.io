+++
title = "End-to-End ELT Pipeline for a Video Streaming Platform"
date = 2025-10-10
description = "This project implements an end-to-end ELT pipeline designed to analyze the performance of a video streaming platform using synthetic data."
tags = ["python", "data", "pipeline", "dbt", "airflow", "docker", "postgresql", "mongodb", "powerbi"]
# externalLink = "https://github.com/..." # User can use this to link directly out
+++

## Table of Contents
- [System Architecture](#system-architecture)
- [Project Overview](#project-overview)
- [Data Sources](#data-sources)
- [Data Modeling and Storage Strategy](#data-modeling-and-storage-strategy)
- [ELT Pipeline and Orchestration](#elt-pipeline-and-orchestration)
- [Analytics Dashboard](#analytics-dashboard)
- [How to Replicate this Project](#how-to-replicate-this-project)
- [Tools and Technologies](#tools-and-technologies)

## System Architecture

![Project Architecture Diagram](/project_images/p2-streaming/etl-pipeline-diagram.jpg)

### *You can find the code for this project in [GitHub](https://github.com/Frank3040/Video-Streaming-Pipeline.git).*

## Project Overview

This project implements an **end-to-end ELT pipeline** designed to analyze the performance of a **video streaming platform** using synthetic data. The pipeline simulates real-world platform behavior through datasets representing **users, content, and viewing sessions**.

The primary objective is to demonstrate the design and implementation of a modern data engineering workflow, including:
- Data ingestion from heterogeneous sources  
- Integration of relational and NoSQL data models  
- Centralized storage in a data warehouse  
- Transformations and dimensional modeling for analytics  

The final output enables analytical reporting and dashboarding to support data-driven insights into user behavior and content performance.

### Data Sources

Three synthetic datasets were created to emulate a video streaming platform:

- **users.csv**  
  Contains user demographics and subscription details.
- **viewing_sessions.csv**  
  Captures detailed viewing session information, including device type, session duration, and streaming quality.
- **content.json**  
  Stores structured metadata for movies and TV series.

### Data Modeling and Storage Strategy

To reflect a realistic multi-source environment:

- **MongoDB (NoSQL source)**   
  - `content.json`  

- **PostgreSQL (Relational source)**  
  - `viewing_sessions.csv`  
  - `users.csv` 

The ELT pipeline extracts data from both MongoDB and PostgreSQL and loads it into **PostgreSQL as a Data Warehouse**. The warehouse is structured using multiple schemas:

- **`raw` schema**  
  Stores ingested data in a normalized, source-aligned format.

- **`trusted` schema**  
  Contains transformed, analytics-ready data modeled using dimensional design principles and created with **dbt**.

### ELT Pipeline and Orchestration

The pipeline follows an **ELT approach**:

1. **Extract**  
   Data is extracted from MongoDB and PostgreSQL source systems.

2. **Load**  
   Raw data is loaded into the PostgreSQL Data Warehouse under the `raw` schema.

3. **Transform**  
   dbt is used to apply transformations, enforce data quality rules, and create a dimensional model in the `trusted` schema.

The entire workflow is orchestrated using **Apache Airflow**, ensuring:
- Task dependency management  
- Logging and observability  
- Error handling and retries  
- Idempotent executions  

All components run in a **Dockerized environment** to ensure consistency and reproducibility.

#### DAG Overview

![Dag Diagram](/project_images/p2-streaming/dag-streaming-pipeline.png)

The Airflow DAG `video_streaming_elt_pipeline` consists of the following key tasks:
- **Create MongoDB Collections**: Initializes the MongoDB source database.
- **Create PostgreSQL Tables**: Initializes the PostgreSQL source database.
- **Load JSON to MongoDB**: Loads `content.json` into MongoDB.
- **Load CSVs to PostgreSQL**: Loads `users.csv` and `viewing_sessions.csv` into PostgreSQL.
- **Extract to Data Warehouse**: Extracts data from source systems and loads it into the `raw` schema of the PostgreSQL Data Warehouse.
- **Transform with dbt**: Executes dbt models to transform raw data into a dimensional model in the `trusted` schema.

## Analytics Dashboard
First section:

![Power BI Dashboard Screenshot](/project_images/p2-streaming/p2-3.png)

Second section:

![Power BI Dashboard Screenshot](/project_images/p2-streaming/p2-4.png)

A **Power BI dashboard** was built on top of the dimensional model to visualize key performance indicators (KPIs), including:
- User demographics and subscription distribution  
- Content popularity and engagement  
- Viewing session metrics and usage patterns  

The dashboard enables interactive exploration of platform performance and supports data-driven decision-making.

### Tools and Technologies
- **Database:** PostgreSQL, MongoDB  
- **Programming Language:** Python 
- **Orchestration:** Apache Airflow  
- **Data Transformation:** dbt 
- **Visualization:** Power BI  