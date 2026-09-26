# 🚀 Hello Stages — Node.js, Git & Docker Compose

![Node.js](https://img.shields.io/badge/Node.js-24_LTS-339933?style=for-the-badge&logo=nodedotjs&logoColor=white)
![Docker](https://img.shields.io/badge/Docker_Compose-v2-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![Git](https://img.shields.io/badge/Git-Workflow-F05032?style=for-the-badge&logo=git&logoColor=white)
![Tests](https://img.shields.io/badge/Tests-node%3Atest-informational?style=for-the-badge)
![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)

> **Trabajo Práctico**  
> **Asignatura:** Gestión de Desarrollo de Software  
> **Carrera:** Tecnicatura Superior en Desarrollo de Software — **UTN FRTDF**  

---

## 📌 Tabla de Contenidos

- [Descripción del Proyecto](#-descripción-del-proyecto)
- [Arquitectura y Estructura](#-arquitectura-y-estructura)
- [Requisitos Previos](#-requisitos-previos)
- [Puesta en Marcha Local](#-puesta-en-marcha-local)
- [Ejecución con Docker Compose (Stages)](#-ejecución-con-docker-compose-stages)
- [Endpoints de la API](#-endpoints-de-la-api)
- [Gestión de Git y Resolución del Conflicto](#-gestión-de-git-y-resolución-del-conflicto)
- [Preguntas de Reflexión](#-preguntas-de-reflexión)
- [Checklist de Entregables](#-checklist-de-entregables)

---

## 📖 Descripción del Proyecto

**Hello Stages** es un proyecto basado en **Node.js 24 LTS** construido exclusivamente con **módulos nativos** (`node:http`, `node:url`, `node:test`), sin dependencias externas. 

El objetivo principal es implementar un flujo de trabajo profesional que comprende:
1. **Flujo de ramas en Git (`feature-branching`)** con integración de dos funcionalidades y resolución manual de un conflicto deliberado.
2. **Suite de pruebas automatizadas** nativas.
3. **Contenerización multi-stage con Docker** dividida en 3 entornos (*stages*) controlados mediante perfiles de Docker Compose:
   * **Development (`dev`):** Con hot-reload (`node --watch`) y volumen montado.
   * **Test (`test`):** Contenedor efímero para validación de pruebas automatizadas.
   * **Production (`prod`):** Imagen optimizada y mínima, sin suite de pruebas y bajo usuario sin privilegios (`USER node`).

---

## 📂 Arquitectura y Estructura

```plaintext
hello-stages/
├── .dockerignore            # Exclusiones del build context de Docker
├── .gitignore               # Exclusiones del versionado Git
├── compose.yaml             # Configuración de servicios y perfiles Docker
├── Dockerfile               # Construcción multi-stage (base, dev, test, prod)
├── package.json             # Manifiesto y scripts de ejecución
├── README.md                # Documentación del proyecto
├── env/
│   ├── dev.env              # Variables para entorno de desarrollo (PORT=3000)
│   ├── test.env             # Variables para entorno de testing (PORT=3000)
│   └── prod.env             # Variables para entorno de producción (PORT=3000 -> 8080)
├── src/
│   └── server.js            # Servidor HTTP modularizado y rutas
└── test/
    └── server.test.js       # Suite de pruebas automatizadas con node:test
