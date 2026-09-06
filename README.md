# andes-real-estate-strategy
# Análisis Comercial Inmobiliario — Andes Capital Real Estate

## 📌 Contexto

Grupo Andes buscaba evaluar el desempeño de sus operaciones inmobiliarias para identificar oportunidades de crecimiento, optimizar sus canales comerciales y comprender mejor el comportamiento de sus clientes.

## 🎯 Objetivo

Desarrollar un dashboard ejecutivo en Power BI que permitiera monitorear los indicadores clave del negocio y apoyar la toma de decisiones estratégicas a partir del análisis de ventas, clientes y propiedades.

## 🗂️ Fuentes de datos

| Tabla | Descripción |
|---|---|
| `hecho_ventas_propiedades` | Tabla de hechos con las transacciones de venta (precio, cliente, propiedad, canal, fecha) |
| `dim_clientes` | Información y segmentación de clientes |
| `dim_propiedades` | Características de las propiedades (tipo, tamaño, ubicación) |
| `dim_fecha` | Tabla calendario construida para habilitar inteligencia de tiempo |

## 🧹 Preparación y calidad de datos

- Se validó que `fecha_venta` estuviera en formato *Date* y que `porcentaje_comision` estuviera en formato porcentaje.
- Se revisaron valores nulos en las tablas, justificando en cada caso si debían eliminarse o mantenerse.
- Se validó la ausencia de duplicados en las claves primarias de `dim_clientes` y `dim_propiedades`.
- Se construyó una dimensión de fechas (`dim_fecha`) para habilitar comparaciones interanuales y métricas acumuladas (YTD, MTD).

## 📐 Modelo de datos

Modelo en estrella con `hecho_ventas_propiedades` como tabla de hechos, relacionada con `dim_clientes`, `dim_propiedades` y `dim_fecha`.

## 📏 KPIs y medidas construidas

**Medidas base**
- Ingreso Total
- Total de Ventas
- Ticket Promedio
- Comisión Total

**Medidas con contexto de filtro** (usadas como tooltip/etiqueta en gráficos)
- % Participación de ingresos por tipo de propiedad
- % Participación de ingresos por canal de venta
- % Participación de ingresos por segmento de cliente

**Inteligencia de tiempo**
- Ventas Year to Date (YTD)
- Ventas Month to Date (MTD)
- Ventas del año anterior
- Crecimiento Year over Year (YoY)

**Cohortes de clientes**
- Mes Cohorte (mes de primera compra del cliente)
- Mes Venta (mes de cada transacción posterior)
- Matriz de cohortes: Mes Cohorte × Mes Venta, con Ingreso Total

## 📊 Estructura del dashboard

### 1. Overview ejecutivo
Tarjetas de Ingreso Total, Total de Ventas, Ticket Promedio, Comisión Total y Crecimiento YoY; evolución de ingresos en el tiempo (gráfica de línea); ingresos por ciudad; filtros por año-mes, ciudad y canal de venta.

### 2. Análisis comercial
Tabla comparativa por tipo de propiedad (ventas, ingreso, ticket promedio, comisión, crecimiento YoY); participación de ingresos por tipo de propiedad, canal de venta y segmento de cliente.

### 3. Análisis de Cohortes
Matriz de cohortes (Mes Cohorte vs. Mes Venta) para evaluar si los clientes vuelven a comprar después de su primera transacción y qué cohortes generan más ingresos con el tiempo.

## 🔑 Hallazgos clave

- El ingreso total del periodo fue de **$6.01 mil millones**, generado por **8,500 ventas**.
- El tipo de propiedad que genera mayor ingreso es **Casa**, superando los **$2.2 mil millones**.
- La ciudad con mayor volumen de ventas es **Bogotá**, con **4,377 ventas**.
- El canal **Corredor** concentra aproximadamente el **73%** del volumen comercial, siendo el canal dominante en la generación de ingresos.

### Métricas principales
| Métrica | Valor |
|---|---|
| Ingreso Total | $6.01 mil millones |
| Cantidad de Ventas | 8,500 |
| Ticket Promedio | $707 mil |
| Comisión Total | $200.6 millones |

### Insights accionables
- El segmento de clientes **"Primera vez"** concentra la mayor parte del ingreso, lo que representa una oportunidad para fortalecer estrategias de adquisición y fidelización.
- Los clientes adquiridos en las cohortes de **2023-03 / 2023-04** muestran mayor recurrencia e ingresos acumulados en comparación con cohortes más recientes.
- Las ventas muestran un crecimiento interanual (YoY) positivo, evidenciando una tendencia favorable en la evolución del negocio inmobiliario.

## 💡 Recomendaciones estratégicas

- Priorizar la comercialización de propiedades tipo **Casa**, dada su mayor contribución al ingreso total.
- Fortalecer el canal de ventas **Directo** para diversificar la captación comercial y reducir la dependencia del canal Corredor (73% del volumen).
- Implementar estrategias de retención para mejorar la tasa de recompra en las cohortes más recientes, replicando lo que funcionó en las cohortes de 2023-03/04.
- Diseñar campañas específicas para clientes de primera compra, aprovechando su alta participación dentro del negocio.

## 🖼️ Dashboard

<!-- Agrega aquí tus capturas, por ejemplo: -->
<!-- ![Overview ejecutivo](images/overview_ejecutivo.png) -->
<!-- ![Análisis comercial](images/analisis_comercial.png) -->
<!-- ![Análisis de cohortes](images/analisis_cohortes.png) -->

## 🛠️ Herramientas utilizadas
- Power BI (modelado de datos, DAX, dashboard)
- Python / Jupyter Notebook (documentación y planeación del análisis)
