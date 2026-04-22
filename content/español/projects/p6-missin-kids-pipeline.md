+++
weight = 3
title = "End-to-End Pipeline para registros de niños desaparecidos"
date = 2026-04-21
description = "Pipeline de datos serverless en AWS y Snowflake que valida, transforma, modela y cataloga datos de desapariciones en Chiapas para analítica y BI."
tags = ["AWS", "Snowflake", "dbt", "Terraform", "Serverless", "Data Pipeline", "Python", "Athena", "Step Functions", "S3", "Lambda", "Glue"]
+++

## Contenido
- [Objetivo del Proyecto](#objetivo-del-proyecto)
- [Descripción del Conjunto de Datos](#descripción-del-conjunto-de-datos)
- [Metodología/Procesos](#metodologíaprocesos)
- [Resultados](#resultados)
- [Tecnologías Utilizadas](#tecnologías-utilizadas)

## Objetivo del Proyecto
Desarrollo de un Pipeline serverless y orientado a eventos en AWS y Snowflake que ingesta archivos CSV sobre personas desaparecidas en Chiapas, México, valida la calidad de los datos, transforma los registros a Parquet particionado, carga los conjuntos curados en Snowflake y usa dbt para construir la capa analítica para su visualización en Power BI o QuickSight. Además, se usa Terraform para el aprovisionamiento y gestión de todos los recursos de AWS.

![Diagrama de arquitectura](/project_images/p6-missing-kids/p6-1.png)
*Figura 1. Arquitectura serverless y flujo de datos.*

### *Puedes encontrar el código de este proyecto en [GitHub](https://github.com/Frank3040/aws-missing-kids-pipeline).*

## Descripción del Conjunto de Datos
El conjunto de datos fuente es un CSV (por ejemplo, `base-desapariciones-dataton-2025.csv`) con registros de niñas y niños desaparecidos en Chiapas entre 2019 y 2025. Incluye campos como sexo, edad, grupo etario, municipio, región, colonia/localidad, condición migrante, fecha de desaparición, día de la semana, horario, estatus del caso y días sin localizar.

## Flujo del Pipeline
1. Los CSV se cargan a `raw/` en un bucket de S3.
2. EventBridge activa un tópico SNS que publica hacia SQS.
3. Un Lambda inicial dispara un flujo en AWS Step Functions.
4. El Lambda validador revisa columnas requeridas y un umbral de calidad (>70% filas válidas).
5. El Lambda transformador limpia campos (fechas, edades, horarios, división de ubicación) y escribe Parquet particionado (`year=YYYY`) en el bucket procesado.
6. Un cargador de Snowflake ingesta los archivos parquet procesados en Snowflake para analítica posterior.
7. dbt modela y prueba la capa analítica sobre Snowflake para generar marts listos para BI.
8. Glue Crawler actualiza el catálogo para consultas en Athena, y los fallos se envían a un DLQ y generan alertas con CloudWatch/SNS.

## Resultados
Los datos procesados se consultan en Athena y Snowflake, y se conectan a Power BI o QuickSight para construir tableros que muestran tendencias por municipio, grupo etario, periodo y estatus del caso. dbt aporta el modelado dimensional y la consistencia de la capa analítica.

![Mockup de dashboard](/project_images/p6-missing-kids/p6-2.png)
*Figura 2. Ejemplo de Dashboard en Power BI.*

## Tecnologías Utilizadas
- AWS S3, EventBridge, SNS, SQS
- AWS Lambda, Step Functions
- AWS Glue, Athena
- Snowflake, dbt
- Terraform
- Python, pandas, awswrangler
- Power BI
