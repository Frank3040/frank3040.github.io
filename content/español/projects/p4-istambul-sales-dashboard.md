+++
weight = 1
title = "Dashboard para análisis de ventas en tiendas de Estambul (Turquía)"
date = 2025-10-14
description = "Este proyecto implementa un análisis descriptivo de un dataset que contiene información sobre transacciones de compras de 10 tiendas diferentes en Estambul, Turquía."
tags = ["python", "power bi", "data", "visualization", "dashboard"]
# externalLink = "https://github.com/..." # User can use this to link directly out
+++

## Resumen del Proyecto

Este fue el proyecto final para el curso de Modelado de Visualización. El objetivo era realizar un análisis descriptivo de un dataset basado en preguntas de negocio y crear un dashboard que muestre los insights de manera clara y concisa. Se decidió usar Python para la limpieza de datos y Power BI para la visualización. El dataset contiene información sobre transacciones de compras de 10 tiendas diferentes en Estambul, Turquía, cubriendo un período de tres años desde 2021 hasta 2023. Es importante mencionar que ambos años, 2021 y 2022, están completos, en el caso del año 2023 solo los primeros dos meses están disponibles.

### Dashboard

Sección 1: Resumen de métricas

![alt text](/project_images/p4-istambul-sales/p4-1.png)

Sección 2: Detalles de ventas

![alt text](/project_images/p4-istambul-sales/p4-2.png)

Sección 3: Detalles de Ordenes

![alt text](/project_images/p4-istambul-sales/p4-3.png)

### Fuentes de Datos

El dataset fue obtenido de Kaggle y contiene información sobre transacciones de compras de **10 tiendas diferentes en Estambul**, cubriendo un período de tres años desde **2021 hasta 2023**. El dataset consta de **99,457 filas** y **10 columnas**, todas las cuales son utilizadas para el análisis. Proporciona una visión general de las hábitos de compra en Estambul, incluyendo detalles sobre la demografía de los clientes, los productos comprados, los métodos de pago y las ubicaciones de las tiendas.

Si desea descargar el dataset, puede encontrarlo [aquí](https://www.kaggle.com/datasets/mehmettahiraslan/customer-shopping-dataset).

### Propósito y Usuario Principal

El **Dashboard de Análisis de Ventas** fue específicamente creado para proporcionar insights prácticos a los **stakeholders ejecutivos**. Actuando como un centro de control para comprender el rendimiento de las ventas y el comportamiento del cliente.

## Componentes del Dashboard

### Menú de Navegación

![alt text](/project_images/p4-istambul-sales/p4-4-nv.png)

El **menú de navegación** en el lado izquierdo del dashboard permite a los usuarios cambiar de manera fluida entre diferentes secciones, proporcionando una organización y una forma intuitiva de explorar los aspectos variados de los datos de ventas.

### Panel de Filtros

![alt text](/project_images/p4-istambul-sales/p4-5-filters.png)

El **panel de filtros** proporciona filtros robustos, permitiendo a los usuarios refinar los datos mostrados basándose en diversos criterios. Puedes segmentar los datos por **categoría**, **año**, **mes**, **tienda**, y **método de pago**, lo que permite un análisis altamente específico.

### Métricas Principales

![alt text](/project_images/p4-istambul-sales/p4-6-metrics.png)

Esta sección muestra los key performance indicators (KPIs) at a glance. These include the **total sales amount**, **total sales revenue**, **average sales revenue per transaction**, and **average quantity sold**, providing an immediate overview of overall sales performance.

## Resultados de la Análisis
El análisis de las transacciones de compras de diez tiendas diferentes en Estambul (2021–2023) revela varios patrones relevantes de clientes y ventas.

La mayoría de los clientes pertenecen al grupo de edad 55–69, que también representa el mayor gasto total, lo que indica que este segmento tiene fuerte poder de compra y alta participación.

En términos de distribución por género, las mujeres representan el 59.72% de las transacciones totales, lo que las hace el segmento dominante en el dataset.

Las cinco categorías de productos con mayor volumen de ventas son ropa, calzado, tecnología, cosméticos y juguetes, con ropa liderando el consumo general. Esto destaca una fuerte demanda de productos relacionados con la moda en todas las tiendas.

En cuanto a los métodos de pago, el efectivo es el tipo de pago más frecuentemente utilizado, seguido por tarjetas de crédito y débito, lo que sugiere una preferencia continua por los métodos tradicionales de pago, a pesar de la disponibilidad de opciones electrónicas.

En términos temporales, los lunes registran el mayor número de transacciones, lo que indica una actividad aumentada del consumidor al inicio de la semana.

Finalmente, el ingreso de ventas mantiene un nivel relativamente estable a lo largo de los tres años, sin un crecimiento o declive significativo año por año. Esto sugiere un rendimiento constante pero un crecimiento orgánico limitado durante el período analizado.


### Tecnologías Utilizadas
*   Python
*   Power BI


