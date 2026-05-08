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

## 📊 Estrategia de Visualización & BI
El producto final es un centro de mando en **MicroStrategy** que permite la gestión por excepción:
* **Dashboards de Impacto:** Seguimiento de métricas clave como *Churn*, *ARPU* y cumplimiento de *SLAs* de instalación.
* **Matching de Datos:** Cruce automático entre los registros de logística (decodificadores/antenas) y las activaciones comerciales.
* **Reportabilidad de Grano Fino:** Capacidad de navegar desde una vista gerencial hasta el detalle técnico de cada suscriptor.

---

## 💡 Impacto y Beneficios Obtenidos
* **Estabilidad del Sistema:** Se liberó la carga de los servidores de operación en un **80%**, al desplazar el consumo de datos hacia el DWH.
* **Mantenimiento Eficiente:** Gracias a los paquetes **SSIS segmentados**, es posible realizar ajustes en el flujo de Logística sin afectar los reportes de Ventas o Contabilidad.
* **Única Fuente de Verdad:** Eliminación de discrepancias entre departamentos; los números financieros ahora coinciden con la operación técnica.
* **Calidad de Datos:** La zona de **Staging** redujo la tasa de errores y duplicados en los reportes finales al mínimo.

---

## 🛠️ Tecnologías Utilizadas
* **Motores de BD:** Oracle (Raw), SQL Server (Transactional & DWH).
* **ETL:** SQL Server Integration Services (SSIS).
* **BI Platform:** MicroStrategy Desktop / Web.
* **Lenguajes:** T-SQL (Stored Procedures, Views, Optimization).

