# 🏛️ Enterprise Data Warehouse: Arquitectura ETL con SSIS y MicroStrategy

## 📝 Resumen del Proyecto
Diseño y construcción de un ecosistema de **Business Intelligence** integral para centralizar la operación de una compañía multiarea. La solución utiliza un flujo robusto de extracción, transformación y carga (ETL) para consolidar datos dispersos en un **Data Warehouse (DWH)** unificado, sirviendo como base para el análisis estratégico en **MicroStrategy**.

---

## 🚨 El Reto
La compañía enfrentaba silos de información y cuellos de botella críticos:
* **Fragmentación:** Los datos residían en un motor Oracle de alta transaccionalidad.
* **Rendimiento:** La generación de reportes directamente sobre las bases operativas degradaba el performance del servicio.
* **Inconsistencia:** No existía una "Única Fuente de Verdad", lo que generaba discrepancias en los indicadores entre áreas.

---

## ✅ Solución Implementada: Arquitectura de Datos Profesional (Oracle - SQL - DWH)

Se implementó una arquitectura de tres capas para desacoplar la operación del análisis:

1. **Capa de Ingesta (Oracle):** Extracción de la data *raw* (cruda) desde el motor principal. Se gestionó la extracción de volúmenes masivos de registros sin impactar la operación del core de negocio.
2. **Capa Transaccional (SQL Server):** Centralización de la información crítica en un entorno SQL Server intermedio, consolidando la data de toda la empresa en un repositorio operativo unificado.
3. **Capa Analítica (DWH Especializado):** * Se construyó un **Data Warehouse exclusivo para reportería**, eliminando la competencia por recursos con los sistemas de producción.
    * **Modularización con SSIS:** Desarrollo de un pipeline en *SQL Server Integration Services* segmentado por unidades de negocio (**Ventas, Atención al Cliente, Logística, Contabilidad y Gerencial**).
    * **Capa Semántica en MicroStrategy:** Implementación de reglas de negocio centralizadas para asegurar la consistencia de los KPIs en todos los niveles.

Esta arquitectura permitió separar el procesamiento pesado de la visualización, logrando una gobernanza total sobre las reglas de negocio de cada departamento.

---

## ⚙️ Estrategia de Carga Incremental (Stored Procedures)
Para optimizar el rendimiento y reducir la ventana de tiempo del ETL, se implementó una estrategia de **Carga Incremental** mediante Stored Procedures que gestionan la lógica de "Delta" (solo cambios nuevos o modificados).

### 🛠️ Lógica de Actualización (Upsert)
Se utilizó el patrón **Merge/Upsert** para insertar registros nuevos y actualizar los existentes, evitando cargas totales diarias:

-- Ejemplo de lógica incremental para el área de Ventas


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

