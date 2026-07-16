Northwind ETL & Analytics Pipeline

Este proyecto implementa un flujo de datos de extremo a extremo (End-to-End) utilizando KNIME para los procesos de extracción, transformación y limpieza de datos (ETL), y Power BI para el modelado de datos relacional y el diseño de un tablero analítico de negocio (Business Intelligence).

📊 Arquitectura del Proyecto

Origen de Datos: Base de datos relacional transaccional (Northwind).

Proceso ETL (KNIME): Limpieza de strings, tratamiento de valores nulos, estandarización de registros, cálculo de variables analíticas y normalización de esquemas.

Modelado y Visualización (Power BI): Diseño de modelo estrella (Star Schema) e implementación de medidas avanzadas en DAX para la toma de decisiones estratégicas.

🛠️ Fase 1: ETL y Calidad de Datos (KNIME)

El flujo de KNIME automatiza la limpieza y estructuración de las 8 tablas de la base de datos original.

Procesos clave implementados:

Limpieza de Texto: Uso de String Manipulation para eliminar espacios excedentes (strip) y normalizar nombres de países, ciudades y compañías a mayúsculas.

Tratamiento de Nulos: Reemplazo de valores nulos utilizando el nodo Missing Value (ej. sustitución de teléfonos ausentes por "No disponible" y faxes por "Sin Fax").

Transformación de Fechas: Conversión de cadenas de texto a formatos temporales estándar con String to Date&Time. Cálculo exacto de la edad y antigüedad de los empleados mediante diferencias de tiempo.

Integridad Referencial: Validación de claves foráneas entre productos y proveedores usando el nodo Reference Row Filter.

Ingeniería de Características: Generación del campo calculado de ventas analíticas total_linea utilizando fórmulas matemáticas personalizadas.

Pega aquí una captura de pantalla de tu flujo de KNIME para que el reclutador vea tu estructura visual de nodos.

📐 Fase 2: Modelado Relacional (Power BI)

Una vez exportados los datos procesados en KNIME, se importaron a Power BI construyendo un Modelo Estrella eficiente para optimizar las consultas y el rendimiento del reporte.

Relaciones del Modelo:

Clientes (1) ─── * → Órdenes

Empleados (1) ─── * → Órdenes

Transportistas (1) ─── * → Órdenes

Categorías (1) ─── * → Productos ─── (1) ─── * → Detalles de Orden

Proveedores (1) ─── * → Productos

📈 Fase 3: Métricas de Negocio (DAX)

Se desarrolló un set de medidas analíticas en DAX para proveer de KPIs interactivos al negocio:

Métrica

Fórmula DAX

Descripción

Total Ventas

SUM(Fact_DetalleOrden[total_linea])

Facturación total libre de inconsistencias.

Número de Pedidos

DISTINCTCOUNT(Fact_Ordenes[orden_id])

Volumen de transacciones únicas.

Venta Promedio por Pedido

[Total Ventas] / [Número de Pedidos]

Ticket promedio por orden de compra.

Antigüedad del Empleado

DATEDIFF(Dim_Empleados[fecha_contratacion], TODAY(), YEAR)

Antigüedad del personal de ventas.

🖥️ Dashboard Analítico Interactiva

El reporte interactivo final incluye:

KPIs Principales: Ventas totales, pedidos generados y ticket promedio de compra.

Gráficos de Barras y Matrices: Análisis de rendimiento de empleados y categorías de producto más rentables.

Segmentadores Dinámicos: Filtros por zona geográfica, cliente estratégico y rangos temporales.

Pega aquí una o dos capturas de pantalla de tu dashboard final en Power BI. El diseño visual es lo que vende tu trabajo.

🚀 Cómo replicar este proyecto

Descarga el flujo de KNIME (.knwf) ubicado en la carpeta /knime de este repositorio e impórtalo en tu espacio de trabajo.

Ejecuta el flujo para generar los archivos limpios en formato CSV.

Abre el archivo .pbix de Power BI ubicado en la carpeta /powerbi y actualiza la ruta del origen de datos hacia tus CSVs locales.
