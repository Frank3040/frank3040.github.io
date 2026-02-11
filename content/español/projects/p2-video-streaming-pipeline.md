+++
title = "Desarrollo de un End-to-End ELT Pipeline para una Plataforma de Video Streaming"
date = 2025-10-10
description = "Este proyecto es la implementación de un end-to-end ELT pipeline diseñado para analizar el rendimiento de una plataforma de video streaming utilizando datos sintéticos."
tags = ["python", "data", "pipeline", "dbt", "airflow", "docker", "postgresql", "mongodb", "powerbi"]
# externalLink = "https://github.com/..." # User can use this to link directly out
+++

## Table of Contents
- [Arquitectura del Sistema](#system-architecture)
- [Descripción del Proyecto](#project-overview)
- [Fuentes de Datos](#data-sources)
- [Estrategia de Modelado y Almacenamiento de Datos](#data-modeling-and-storage-strategy)
- [ELT Pipeline y Orquestación](#elt-pipeline-and-orchestration)
- [Dashboard Analítico](#analytics-dashboard)
- [Herramientas y Tecnologías](#tools-and-technologies)

## Arquitectura del Sistema

![Project Architecture Diagram](/project_images/p2-streaming/etl-pipeline-diagram.jpg)

### *Puedes encontrar el código de este proyecto en [GitHub](https://github.com/Frank3040/Video-Streaming-Pipeline.git).*

## Descripción del Proyecto

Este proyecto implementa un **end-to-end ELT pipeline** diseñado para analizar el rendimiento de una **plataforma de video streaming** utilizando datos sintéticos. El pipeline simula el comportamiento real de la plataforma a través de conjuntos de datos que representan **usuarios, contenido y sesiones de visualización**.

El objetivo principal fue diseñar e implementar un flujo de trabajo moderno de ingeniería de datos, que incluye:
- Ingesta de datos desde fuentes heterogéneas  
- Integración de modelos de datos relacionales y NoSQL  
- Almacenamiento centralizado en un data warehouse  
- Transformaciones y modelado dimensional para análisis  

El resultado final permite la generación de reportes analíticos y dashboards para obtener insights basados en datos sobre el comportamiento del usuario y el rendimiento del contenido.

### Fuentes de Datos

Se crearon tres conjuntos de datos sintéticos para simular una plataforma de video streaming:

- **users.csv**  
  Contiene información demográfica y de suscripción de los usuarios.
- **viewing_sessions.csv**  
  Registra información detallada de las sesiones de visualización, incluyendo tipo de dispositivo, duración de la sesión y calidad de transmisión.
- **content.json**  
  Contiene metadatos estructurados de películas y series de televisión.

### Estrategia de Modelado y Almacenamiento de Datos

Para reflejar un entorno realista multi-fuente:

- **MongoDB (NoSQL)**   
  - `content.json`  

- **PostgreSQL (Relacional)**  
  - `viewing_sessions.csv`  
  - `users.csv` 

El pipeline ELT extrae datos de MongoDB y PostgreSQL y los carga en **PostgreSQL como un Data Warehouse**. El data warehouse está estructurado utilizando múltiples esquemas:

- **Esquema `raw`**  
  Almacena los datos ingeridos en un formato normalizado y alineado con la fuente.

- **Esquema `trusted`**  
  Contiene datos transformados y listos para análisis, modelados utilizando principios de diseño dimensional y creados con **dbt**.

### ELT Pipeline y Orquestación

El pipeline sigue un **enfoque ELT** (Extract, Load, Transform):

1. **Extract**  
   Los datos se extraen de los sistemas fuente MongoDB y PostgreSQL.

2. **Load**  
   Los datos crudos se cargan en el Data Warehouse de PostgreSQL bajo el esquema `raw`.

3. **Transform**  
   Se utiliza dbt para aplicar transformaciones, aplicar reglas de calidad de datos y crear un modelo dimensional en el esquema `trusted`.

El flujo de trabajo completo es orquestado por **Apache Airflow**, asegurando:
- Gestión de dependencias entre tareas  
- Logging y observabilidad  
- Manejo de errores y reintentos  
- Ejecuciones idempotentes  

Todos los componentes se ejecutan en un **entorno Dockerizado** para garantizar la consistencia y reproducibilidad.

#### DAG Overview

![Dag Diagram](/project_images/p2-streaming/dag-streaming-pipeline.png)

El DAG de Airflow `video_streaming_elt_pipeline` consta de las siguientes tareas principales:
- **Create MongoDB Collections**: Inicializa la base de datos fuente MongoDB.
- **Create PostgreSQL Tables**: Inicializa la base de datos fuente PostgreSQL.
- **Load JSON to MongoDB**: Carga `content.json` en MongoDB.
- **Load CSVs to PostgreSQL**: Carga `users.csv` y `viewing_sessions.csv` en PostgreSQL.
- **Extract to Data Warehouse**: Extrae datos de los sistemas fuente y los carga en el esquema `raw` del Data Warehouse de PostgreSQL.
- **Transform with dbt**: Ejecuta los modelos de dbt para transformar los datos crudos en un modelo dimensional en el esquema `trusted`.

## Dashboard Analítico

Primera sección: 

![Power BI Dashboard Screenshot](/project_images/p2-streaming/p2-3.png)

Segunda sección:

![Power BI Dashboard Screenshot](/project_images/p2-streaming/p2-4.png)

Un **Power BI dashboard** fue desarrollado sobre el modelo dimensional para visualizar indicadores clave de rendimiento (KPIs), incluyendo:
- Distribución de datos demográficos y de suscripción de usuarios  
- Popularidad y engagement del contenido  
- Métricas de sesiones de visualización y patrones de uso 

El dashboard permite la exploración interactiva del rendimiento de la plataforma y apoya la toma de decisiones basada en datos.

### Herramientas y Tecnologías
- **Base de Datos:** PostgreSQL, MongoDB  
- **Lenguaje de Programación:** Python 
- **Orquestación:** Apache Airflow  
- **Transformación de Datos:** dbt 
- **Visualización:** Power BI  