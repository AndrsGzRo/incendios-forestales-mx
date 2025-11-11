# Análisis y Visualización de Incendios Forestales en México (2015-2024)
Este proyecto presenta un análisis exploratorio y de visualización de los **incendios forestales** registrados en **México** entre **2015 y 2024**, con el **objetivo** de **identificar patrones espaciales, temporales y de severidad** a partir de datos públicos. 
El propósito es generar una comprensión visual del fenómeno y establecer una base para un futuro modelo predictivo de riesgo de incendios. 

## Descripción General
Los incendios forestales representan uno de los principales problemas ambientales en México, afectando miles de hectáreas en varios puntos del territorio mexicano.
A través del análisis de datos abiertos de la **Comisión Nacional Forestal (CONAFOR)**, se examinan las causas, duración, superficie afectada y distribución geográfica de los incendios a lo largo del país.
El análisis cubre lo siguiente:
- **Periodo**: 2015-2024:
- **Fuente** ["Datos.gob.mx - Incendios Forestales"](https://datos.gob.mx/dataset/incendios_forestales/resource/ddf38874-6243-4437-8f76-19f797cafa5c)

## Contenido del proyecto
| Archivo| Descripción|
|---|---|
|```visualizations```| Carpeta con las visualizaciones exportadas (PNG)|
|```Incendios_Forestales_EDA.ipynb```| Notebook de análisis y visualización |
|```README.md```| Descripción del proyecto|
|```data-2025-11-05.csv```| Datos originales sin limpiar|
|```estados_mexico.zip```| Shapefile de estados (CONABIO) |
|```table_2025-11-05-16-51-38.csv```| Descripción de las variables |

## Limpieza y Preparación de Datos
- Se eliminaron columnas duplicadas y campos ```fn_``` sin valor.
- Las fechas se transformaron desde formato **timestamp** a fechas reales.
- Con la información de las fechas, se obtuvo la estación del incendio, esta será una variable.
- A partir de las fechas, se generaron variables como:
    - ```anio_inicio```
    - ```mes_inicio```
    - ```duracion_dias_num```
- Se corrigieron inconsistencias en nombre de estados, municipios y causas.
- Los puntos fuera del territorio nacional fueron **excluidos** con un filtro de GeoPandas.
- Se asignó la **región geográfica** (Noroesta, Noreste, Centro, Occidente, Sur-Sureste).

## 🔎Análisis Exploratorio 

El análisis abordó tres dimensiones principales:

1. **Temporal**:
   - Evolución anual de incendios y superficie afectada
2. **Geográfica**:
   - Distribución de incendios por estado, municipio y región.
   - Mapas de calor con concentración espacial. 
3. **Causal y de Severidad**:
   - Principales causas.
   - Promedio y total de hectáreas afectadas por año y región.

## Visualizaciones Principales
- **Incendios por causa**
  ![Incendios por causa](visualizations/incendios_por_causa.png)
-  **Mapas de concentración por estado y región (GeoPandas)**
![Incendios por Estado](visualizations/incendios_por_estado_mapa.png)
![Incendios por Región](visualizations/concentracion_incendios_region.png)
![Incendios en México](visualizations/distribucion_incendios.png)

-  **Tendencia Anual y Estsacional de hectáreas afectadas**

![Incendios por año](visualizations/incendios_por_anio.png)
![Incendios por mes y año](visualizations/incendios_por_mes_anio.png)
![Incendios por Estación](visualizations/incendios_por_estacion.png)

-  **Mapa de calor año vs mes**

![Año vs Mes](visualizations/heatmap_mes_anio.png)

- **Estados con más incendios**
![Estados con más incendios](visualizations/estados_incendios.png)

- **Radar chart de superficie afectada por región**
![Superficie afectada por región](visualizations/superficie_afectada_region.png)

-  **Municipios con mayor área afectada**
  
![Municipios con mayor área afectada](visualizations/municipios_hectareas_Afectadas.png)

-  **Evolución de Incendios Forestales por Estado**
![Evolución de Incendios por Estado](visualizations/heatmap_incendios_anio_estado.png)

-  **Severidad Promedio por Región**
  ![Severidad promedio](visualizations/severidad_promedio_por_Region.png)

-**Hectáreas afectadas por año**
![Hectáreas afectadas por año](visualizations/hectareas_anio.png)

- **Hectáreas promedio afectadas por año**
  ![Hectáreas promedio afectadas por año](visualizations/hectareas_promedio.png)

- **Frecuencia y Severidad**
- ![Frecuencia y Severidad](visualizations/frecuencia_severidad_estado.png)

- **Top 10 Causas con Mayor Severidad Promedio (Más hectáreas afectadas promedio)**
  ![Causas](visualizations/causas_mayor_severidad.png)

- **Municipios con más incendios severos**
![Incendios severos por municipio](visualizations/incendios_severos_municipio.png)
  
## Hallazgos Clave
- 13,023 incendios fueron causados de manera intencional, mientras que 10,843 fueron por actividades agrícolas
- La mayoría de los incendios se concentran en la primavera, en los meses de marzo a abril, lo que corresponde a la época de estiaje.
- El estado con más incendios es el **Estado México**, seguido por **Jalisco** y **Michoacán**.
- La región del Noroeste, es en donde se encuentran los incendios más severos. Así mismo, de los 5 municipios con más hectáreas afectadas, 3 son del norte.
- En las regiones de **Centro** y **Occidente** es donde se concentran la mayor cantidad de incendios.
- El año de 2024 es en donde más hectáreas afectadas hubo, en este año hubo un poco más de 1.6 millones de hectáreas afectadas. 
- El promedio de hectáreas afectadas ha aumentado desde el 2021, en donde se promedió aproxidamenete 100 hectáreas por incendio, mientras que en 2025, son cerca de 200 hectáreas por incendio.
- El estado de Guerrero es un estado que cuenta con pocos incendios, pero estos son muy severos. Por otra parte, el Estado de México cuenta con muchos incendios pero son menos destructivas.
- Los incendios naturales y los cazadores son dos de las cinco principales causas con mayor severidad, la primera afecta 300 hectáreas, mientras que los cazadores afectan aproximadamente 150 hectárea.
- 10 de los 12 municipios con incendios más severos se encuentran en el norte del país. 
## Tecnologías Utilizadas
- **Python**:
    -```pandas```
    -```matplotlib```
    -```seaborn```
    -```geopandas```
    -```squarify```
    -```calendar```
- **Jupyter Notebooks** para desarrollo y análisis interactivo.
- **Datos geoespaciales**:
  - [Portal de Geoinformación 2025](http://www.conabio.gob.mx/informacion/gis/)
  - ["Datos.gob.mx - Incendios Forestales"](https://datos.gob.mx/dataset/incendios_forestales/resource/ddf38874-6243-4437-8f76-19f797cafa5c)

## Próximos Pasos
- Integrar variables climáticas (temperatura, precipitación, humedad).
- Desarrollar un modelo predictivo de riesgo para incendios.
- Crear un dashboard interactivo con Streamlit o Plotly.

## Créditos
- **Autor**: [Andrés Guzmán Rodríguez](https://github.com/AndrsGzRo).
- **Fuente de datos**: CONAFOR/ Datos.gob.mx/ CONABIO
## Fuente de datos 
Este proyecto utiliza la base de datos [“Incendios forestales”](https://datos.gob.mx/dataset/incendios_forestales/resource/ddf38874-6243-4437-8f76-19f797cafa5c) publicada por la Comisión Nacional Forestal (CONAFOR). Última actualización 16 abril 2025. Licencia CC BY 4.0. 
