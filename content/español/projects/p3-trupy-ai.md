+++
weight = 2
title = "Trupy AI: Chatbot para el departamento de psicología de la UPY"
date = 2026-01-01
description = "Este proyecto presenta el diseño e implementación de un chatbot para el Departamento de Psicología de la Universidad Politécnica de Yucatán (UPY)."
tags = ["python", "data", "docker", "chatbot", "vue", "ai", "openai", "fastapi"]
+++

## Contenido
- [Descripción del Proyecto](#descripción-del-proyecto)
- [Arquitectura del Sistema](#arquitectura-del-sistema)
- [Demo](#demo)
- [Próximos Pasos](#próximos-pasos)
- [Tecnologías Utilizadas](#tecnologías-utilizadas)

## Descripción del Proyecto

Trupy AI es un chatbot impulsado por IA desarrollado para el Departamento de Psicología de la Universidad Politécnica de Yucatán (UPY). Este proyecto sirvió como proyecto final del curso de Ingeniería de Software. Trupy AI actúa como un compañero virtual para los estudiantes, proporcionando un espacio seguro y de apoyo para discutir temas de psicología y bienestar mental.

## Arquitectura del Sistema

![Project Architecture Diagram](/project_images/p3-trupy-ai/p3-1.png)

*Figura 1. Arquitectura del sistema Trupy AI.*

### *Puedes encontrar el código de este proyecto en [GitHub](https://github.com/Frank3040/Trupy-AI.git).*

## Características Principales

- **Interfaz de Chat Intuitiva**: Una interfaz de usuario limpia y moderna permite a los usuarios interactuar fácilmente con Trupy AI.
- **Integración con DeepSeek**: Aprovecha el poder de los LLM para generar respuestas coherentes y contextualmente relevantes.
- **Persistencia de Datos**: Utiliza una base de datos para almacenar información de usuarios y conversaciones, permitiendo una experiencia personalizada.
- **Despliegue Contenerizado**: Utilizar Docker para un despliegue fácil y consistente.

## Demo

![Demo](/project_images/p3-trupy-ai/p3-2.png)
![Demo](/project_images/p3-trupy-ai/p3-3.png)

*Figura 2. Demo del sistema Trupy AI.*

## Próximos Pasos

- Autenticación y autorización de usuarios
- Integración con recursos universitarios (por ejemplo, reserva de citas, enlaces de recursos)
- Panel de análisis de estadísticas de uso
- Mejora de la interfaz de usuario y la accesibilidad

## Tecnologías Utilizadas

- **Lenguaje de Programación**: Python
- **LLM**: DeepSeek
- **Framework de Backend**: FastAPI
- **Framework de Frontend**: Vue.js
- **Base de Datos**: SQLite
- **Contenerización**: Docker
- **Cache**: Redis