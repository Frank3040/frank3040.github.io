+++
title = "Desarrollo de un Pipeline y visualizaciónes para datos de ventas de un comercio de productos deportivos"
date = 2025-10-15
description = "Este proyecto implementa un pipeline robusto de ETL (Extract, Load, Transform) para que se enfoca en la ingesta, carga y transformación de datos de ventas de un comercio de productos deportivos, además de la visualización de los datos en Power BI y Looker."
tags = ["python", "data", "airflow", "docker", "postgresql", "dashboard"]
# externalLink = "https://github.com/..." # User can use this to link directly out
+++

## Contenido

- [Resumen del Proyecto](#resumen-del-proyecto)
- [Contexto del Dataset](#contexto-del-dataset)
- [Arquitectura del Proyecto](#arquitectura-del-proyecto)
- [Dashboards](#dashboards)
- [Tecnologías Utilizadas](#tecnologías-utilizadas)

## Resumen del Proyecto

Este proyecto implementa un pipeline robusto de **ELT (Extract, Load, Transform)** para analizar datos de ventas de un comercio de productos deportivos. El pipeline ingresa datos brutos en formato Excel a un almacen de datos en **PostgreSQL**, transforma los datos para análisis y visualiza los resultados utilizando **Power BI** y **Looker**. Sin embargo, como el análisis no es el enfoque principal de este proyecto, los dashboards son simples y sirven para demostrar la funcionalidad end-to-end del pipeline.

##### **El codigo de este proyecto se puede encontrar en Github, da click en el siguiente enlace: [GitHub](https://github.com/Frank3040/Sports-Store-Pipeline.git)**

## Fuente de Datos
El dataset utilizado es el **Sport Products Sales Analysis Challenge** de FP20 Analytics Challenges Group, una comunidad de LinkedIn enfocada en proyectos de análisis de datos. Puedes encontrar más sobre ellos [aquí](https://fp20analytics.com/).

Después de examinar todos los datasets que han compartido, seleccioné este porque ofrece un conjunto rico de dimensiones, incluyendo Tiempo (Fecha de Factura), Geografía (Región, Estado, Ciudad), Jerarquía de Productos (Producto), y Entidades de Negocio (Retailer, Sales Method), lo que lo hace perfecto para el análisis. Además, el dataset presenta desafíos reales de calidad de datos, como manejar errores tipográficos y estandarizar nombres de columnas, lo que lo hace excelente para practicar la lógica de transformación.

## Arquitectura del Sistema

![Arquitectura del proyecto](/project_images/p5/p5-1.jpg)

El proyecto utiliza una arquitectura moderna basada en contenedores:

1. Orquestación (Airflow): Gestiona el flujo de trabajo ELT.
2. Extracción: Recupera datos de fuentes externas.
3. Carga: Ingesta datos crudos a PostgreSQL (schema: raw).
    - Almacenamiento (PostgreSQL): Base de datos relacional con esquema en capas (Raw -> Processed -> Trusted).
4. Transformación: Limpieza y normalización de datos mediante SQL (schema: processed).
    - Modelado: Creación de vistas analíticas (schema: trusted).
5. Visualización (Looker/Power BI): Herramientas de visualización de datos que consumen las vistas confiables para mostrar KPIs y gráficos.
6. Infraestructura (Docker): Todo el entorno se despliega mediante docker-compose.


## Dashboards
Este Dashboard fue creado usando Looker:

![Dashboard](/project_images/p5/p5-2.png)

Este Dashboard fue creado usando Power BI:

![Dashboard](/project_images/p5/p5-3.png)

## Tecnologías Utilizadas

-   **Python**: Utilizado para la extracción, transformación y carga de datos.
-   **Airflow**: Utilizado para la orquestación del pipeline.
-   **Docker**: Utilizado para la orquestación del pipeline.
-   **PostgreSQL**: Utilizado como almacenamiento de datos.
-   **Power BI**: Utilizado para la visualización de datos.
-   **Looker**: Utilizado para la visualización de datos.
