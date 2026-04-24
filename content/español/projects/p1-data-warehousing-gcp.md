+++
title = "Data Warehouse (DW) para el dataset de NY Yellow Taxi Trips"
date = 2025-10-21
description = "Este proyecto presenta el diseño e implementación de un Almacén de Datos (DW) en Google Cloud Platform (GCP) utilizando BigQuery y un Dashboard usando Looker Studio. Esto con el objetivo de analizar patrones de movilidad urbana utilizando datos de viajes en taxi de la ciudad de Nueva York."
tags = ["Data", "Pipeline", "GCP", "BigQuery", "Data Warehousing", "Looker Studio"]
# externalLink = "https://github.com/..." # User can use this to link directly out
+++


# Contenido
 - [Objetivo del Proyecto](#objetivo-del-proyecto)
 - [Descripción del Conjunto de Datos](#descripción-del-conjunto-de-datos)
 - [Modelado Dimensional](#modelado-dimensional) 
 - [Proceso ELT](#proceso-elt)
 - [Tablas de dimensiones y hechos en BigQuery](#tablas-de-dimensiones-y-hechos-en-bigquery)
 - [Dashboard](#dashboard)
 - [Tecnologías Utilizadas](#tecnologías-utilizadas)


## Objetivo del Proyecto

El objetivo principal es respaldar la toma de decisiones eficiente y basada en datos, integrando, transformando y organizando datos transaccionales sin procesar en un modelo dimensional bien estructurado, optimizado para consultas analíticas y creación de dashboards.

## Descripción del Conjunto de Datos
El conjunto de datos utilizado es el de New York Yellow Taxi Trips de 2018, disponible en BigQuery, que contiene información sobre viajes en taxi, incluyendo ubicaciones de recogida y entrega, distancia del viaje, monto del pasaje, monto total, cantidad de pasajeros, etc. Para más información, por favor visita el [sitio web de la NYC](https://www.nyc.gov/site/tlc/about/tlc-trip-record-data.page).

## Modelado Dimensional

El Data Warehouse fue diseñado siguiendo el enfoque de **esquema en estrella** para garantizar simplicidad, alto rendimiento de consultas y flexibilidad analítica.

### Componentes del Modelo

- **Tabla de Hechos**
  - **fact_trips**: Almacena métricas clave de rendimiento, como distancia del viaje, monto del pasaje, monto total y cantidad de pasajeros

- **Tablas de Dimensión**
  - **dim_time**: Captura jerarquías temporales como día, mes, año y día de la semana.
  - **dim_location**: Describe zonas de recogida y entrega.
  - **dim_payment**: Contiene métodos de pago y sus descripciones.
  - **dim_vendor**: Identifica proveedores de servicios de taxi.

Este modelo permite análisis multidimensional por tiempo, ubicación, tipo de pago y proveedor, proporcionando valiosos conocimientos sobre el comportamiento del transporte urbano.

![Star schema representation showing fact and dimension relationships.](/project_images/p1-gcp-bigquery/p1-1.png)

*Figura 1. Representación del esquema estrella que muestra las relaciones entre hechos y dimensiones.*

## Proceso ELT

Para este proyecto se utilizó el patrón Extraer, Cargar y Transformar, ELT por sus siglas en inglés (Extract, Load, and Transform). Consiste en las siguientes etapas:

1. **Extracción**  
   Los datos se recuperan directamente del conjunto de datos públicos de viajes en taxi de NYC en BigQuery.

2. **Carga**  
   Los datos se cargan en tablas de BigQuery que se utilizan primero como tablas de preparación bajo un esquema **raw** para realizar limpieza y transformación de datos.

3. **Transformación**  
   Los datos se mueven a un esquema **processed** donde se limpian, se normalizan los tipos de datos y se crean atributos derivados. Luego, los datos se cargan en un esquema **trusted** en las tablas de hechos y dimensiones. Finalmente, se crean vistas materializadas para proporcionar acceso rápido a los datos.


### Tablas de dimensiones y hechos en BigQuery

![Bigquery data warehouse schema](/project_images/p1-gcp-bigquery/p1-3.png)

*Figura 2. Se muestra las tablas de BigQuery que componen el data warehouse.*


## Dashboard

Usando **Looker Studio** conectado a **BigQuery**, se desarrolló un dashboard interactivo para analizar los patrones operativos y de movilidad de los servicios de taxi de NYC. Las visualizaciones que contiene respaldan información sobre volúmenes de viajes, distribución de ingresos, tendencias temporales y demanda geográfica, demostrando el valor analítico del diseño del Data Warehouse. Puedes acceder al dashboard [aquí](https://lookerstudio.google.com/reporting/ac9e3cf1-d247-479a-a1a0-eee83c33d6b9). 

Debajo hay una captura de pantalla del dashboard, para que te puedas dar una idea de las gráficas que contiene.

![Dashboard screenshot](/project_images/p1-gcp-bigquery/p1-2.png)
*Figura 3. Dashboard interactivo para analizar los patrones operativos y de movilidad de los servicios de taxi de NYC.*

### Análisis y Resultados


### Tecnologías Utilizadas
*   SQL
*   Google Cloud Platform (GCP)
*   BigQuery
*   Data Warehousing
*   Looker
