# 🏛️ Enterprise Data Warehouse: Arquitectura ETL con SSIS y MicroStrategy

## 📝 Resumen del Proyecto
Diseño y construcción de un ecosistema de **Business Intelligence** integral para centralizar la operación de una compañía multiarea. La solución utiliza un flujo robusto de extracción, transformación y carga (ETL) para consolidar datos dispersos en un **Data Warehouse (DWH)** unificado, sirviendo como base para el análisis estratégico en **MicroStrategy**.

---

## 🚨 El Reto
La información se encontraba fragmentada en diferentes bases de datos operativas. Esto generaba inconsistencias en los reportes (ej. Ventas no coincidía con Contabilidad) y una alta carga sobre los servidores de producción al intentar generar reportes en tiempo real.

---

## 🛠️ Solución Implementada: Flujo de Datos Profesional

### 1. Extracción y Limpieza (SQL Server + SSIS)
Se implementó una arquitectura de carga por etapas para garantizar que solo los datos limpios lleguen a los ejecutivos:

* **Paquetes SSIS Modulares:** Se desarrolló un paquete de **Integration Services** independiente por cada unidad de negocio:
    * 💰 **Ventas** | 📞 **Atención al Cliente** | 📦 **Logística** | 🧾 **Contabilidad** | 📈 **Gerencial**
* **Capa de Staging (Validación):** Los datos no pasan directo al reporte. Primero llegan a una zona de "Staging" donde se validan formatos, se eliminan duplicados y se limpian nulos. Si un dato no cumple la regla, no avanza.
* **Carga al Data Warehouse:** Una vez validados, los datos se integran en el **DWH final** bajo un modelo de **Esquema en Estrella** (Tablas de Hechos y Dimensiones), optimizado para consultas rápidas.

### 2. Capa de Inteligencia (MicroStrategy)
Uso de MicroStrategy para la democratización de la información:
* **Objeto de Negocio Único:** Creación de una capa semántica donde las métricas (como el "Margen de Utilidad") se definen una sola vez y se reutilizan en todos los reportes, evitando discrepancias.
* **Dashboards de Alto Impacto:** Creación de tableros visuales para la gerencia y reportes de "grano fino" para los supervisores operativos.
* **Gobernanza:** Configuración de permisos de seguridad para que cada área acceda exclusivamente a su información correspondiente.

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
