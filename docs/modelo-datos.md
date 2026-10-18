# Modelo de datos

El proyecto **Industrial Operations Intelligence** utiliza un modelo dimensional tipo estrella para separar los eventos operativos de las dimensiones de análisis.

## Dimensiones

### DimFecha
Calendario central del modelo. Incluye fecha, año, número de mes, mes, año-mes, trimestre, semana, día, número de día de la semana, nombre del día y bandera de fin de semana.

### DimLinea
Catálogo de líneas de producción:
- L1 — Envasado A
- L2 — Envasado B
- L3 — Empaque
- L4 — Etiquetado

### DimProducto
Catálogo de productos:
- P001 — Producto Alfa
- P002 — Producto Beta
- P003 — Producto Gamma

### DimProveedor
Catálogo de proveedores utilizados en el análisis logístico.

### DimMaterial
Catálogo de materiales utilizados para el análisis de inventario y punto de reorden.

## Tablas de hechos

- **T_Produccion**: volumen producido, unidades buenas, objetivos, tiempos de operación y variables de producción.
- **T_Calidad**: eventos y defectos de calidad.
- **T_Mantenimiento**: órdenes de mantenimiento, tipo, estatus, técnico y costo.
- **T_Paros**: causas y duración de paros.
- **T_Energia**: consumo y costo de energía por línea y periodo.
- **T_Inventario**: existencia, punto de reorden y situación de materiales.
- **T_Logistica**: entregas, cumplimiento OTIF, Fill Rate y tiempos de descarga.

## Relaciones principales

Las dimensiones filtran a las tablas de hechos mediante relaciones uno-a-muchos y dirección de filtro simple desde la dimensión hacia el hecho.

`DimFecha[Fecha]` se relaciona con las fechas activas de las tablas de hechos. En logística, `fecha_real` funciona como relación activa y `fecha_promesa` como relación alternativa/inactiva.

`DimLinea` se conecta con las tablas operativas que contienen línea de producción. `DimProducto` filtra producción, `DimProveedor` filtra logística y `DimMaterial` filtra inventario.

## Medidas y KPIs

Las medidas están centralizadas en la tabla **Medidas**. Entre los indicadores principales se encuentran:

- OEE
- Disponibilidad
- Rendimiento
- Calidad
- Cumplimiento de producción
- Scrap % y Scrap Unidades
- MTTR
- MTBF aproximado
- Cumplimiento preventivo
- Costo de mantenimiento
- OTIF %
- Fill Rate %
- Tiempo promedio de descarga
- Consumo y costo de energía
- kWh por 1000 unidades
- Materiales bajo reorden
- Existencia actual y punto de reorden
- Minutos de paro y porcentaje acumulado para Pareto

## Nota

Los datos del proyecto son simulados y se utilizan exclusivamente con fines académicos y de portafolio.