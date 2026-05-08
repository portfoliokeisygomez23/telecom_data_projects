# 🏛️ Enterprise Data Warehouse: Arquitectura ETL con SSIS y MicroStrategy

## 📝 Resumen del Proyecto
Diseño y construcción de un ecosistema de **Business Intelligence** integral para centralizar la operación de una compañía multiarea. La solución utiliza un flujo robusto de extracción, transformación y carga (ETL) para consolidar datos dispersos en un **Data Warehouse (DWH)** unificado, sirviendo como base para el análisis estratégico en **MicroStrategy**.

---

## 🚨 El Reto
La información se encontraba fragmentada en diferentes bases de datos operativas. Esto generaba inconsistencias en los reportes (ej. Ventas no coincidía con Contabilidad) y una alta carga sobre los servidores de producción al intentar generar reportes en tiempo real.

---

## ✅ Solución Implementada: Arquitectura de 3 Capas (Oracle - SQL - DWH)

Se diseñó e implementó un flujo de datos estructurado para desacoplar la operación del análisis, garantizando que el consumo de reportes no afectara el rendimiento de los sistemas críticos:

* **Capa 1: Ingesta desde Oracle (Raw Data):** Extracción de grandes volúmenes de datos crudos desde el core transaccional de la compañía (Oracle).
* **Capa 2: Repositorio Transaccional (SQL Server):** Centralización de la información necesaria en SQL Server, actuando como un centro de datos operativo para la empresa.
* **Capa 3: Data Warehouse Especializado (DWH):** * Se decidió crear un repositorio exclusivo en SQL Server optimizado para **Reportería Estratégica**.
    * **Automatización con SSIS:** Desarrollo de paquetes modulares en *SQL Server Integration Services* por área de negocio (**Ventas, Atención al Cliente, Logística, Contabilidad y Gerencial**).
    * **Consumo en MicroStrategy:** Los reportes finales se alimentan directamente desde este DWH, asegurando tiempos de respuesta rápidos y consistencia en los KPIs.

Esta arquitectura permitió separar el procesamiento pesado de la visualización, logrando una gobernanza total sobre las reglas de negocio de cada departamento.

---

## ✅ Arquitectura Técnica
* **Motor de Base de Datos:** SQL Server.
* **Herramienta ETL:** SQL Server Integration Services (SSIS).
* **Almacenamiento:** Arquitectura de dos capas (Staging Area + Data Warehouse).
* **Plataforma de BI:** MicroStrategy.

---

## 💡 Impacto y Beneficios Obtenidos
* **Única Fuente de Verdad:** Se eliminaron las discusiones sobre "qué número es el correcto" entre departamentos.
* **Mantenimiento Eficiente:** Al tener paquetes separados por área, es posible hacer ajustes en Logística sin afectar o detener los reportes de Contabilidad.
* **Rendimiento del Sistema:** Se liberó la carga de los servidores de operación en un **80%**, ya que los reportes ahora consultan el DWH y no las bases de datos de trabajo diario.
* **Confiabilidad:** Gracias a la etapa de Staging, la tasa de error en los reportes finales se redujo al mínimo.

---

## 🛠️ Tecnologías Utilizadas
* SQL Server (T-SQL, Stored Procedures)
* SQL Server Integration Services (SSIS)
* MicroStrategy Desktop / Web
