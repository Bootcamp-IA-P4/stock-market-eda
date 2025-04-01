# Exploratory Data Analysis (EDA) on Synthetic Stock Data

## Descripción del Proyecto

Este repositorio contiene el código y los hallazgos de un Análisis Exploratorio de Datos (EDA) realizado sobre el conjunto de datos `synthetic_stock_data.csv`. El objetivo principal es comprender la estructura, calidad, características y relaciones dentro de los datos, sirviendo como base para análisis más profundos o modelado predictivo. El análisis se realizó principalmente utilizando Python con las librerías Pandas, NumPy, Matplotlib, Seaborn y SciPy.

## Conjunto de Datos

*   **Archivo:** `synthetic_stock_data.csv`
*   **Fuente:** Datos sintéticos (generados, no reales del mercado).
*   **Tamaño:** 1000 filas, 14 columnas iniciales (+ 9 generadas).
*   **Rango Temporal Aprox.:** Enero 2022 - Septiembre 2024.
*   **Contenido:** Información bursátil diaria simulada para 63 compañías en 7 sectores.
*   **Columnas Clave:**
    *   `Date`: Fecha de la observación.
    *   `Company`: Nombre de la compañía.
    *   `Sector`: Sector industrial.
    *   `Open`, `High`, `Low`, `Close`: Precios OHLC.
    *   `Volume`: Volumen de transacciones.
    *   `Market_Cap`: Capitalización de mercado.
    *   `PE_Ratio`: Ratio Precio/Beneficio.
    *   `Dividend_Yield`: Rentabilidad por dividendo.
    *   `Volatility`: Medida de volatilidad diaria.
    *   `Sentiment_Score`: Puntuación de sentimiento (rango -1 a 1).
    *   `Trend`: Etiqueta de tendencia (Stable, Bullish, Bearish).

## Proceso del EDA

El análisis siguió los siguientes pasos estándar:

1.  **Carga e Inspección Inicial:** Carga de datos, revisión de primeras/últimas filas, dimensiones (`shape`), tipos de datos e información general (`info()`).
2.  **Limpieza de Datos:**
    *   Verificación y manejo de valores nulos (No se encontraron).
    *   Verificación y manejo de filas duplicadas (No se encontraron).
    *   Corrección de tipos de datos (Conversión de `Date` a `datetime`).
3.  **Análisis Univariado:**
    *   **Numéricas:** Cálculo de estadísticas descriptivas (media, mediana, std, cuartiles, IQR, skewness, kurtosis) y visualización de distribuciones (histogramas, boxplots).
    *   **Categóricas:** Conteo de frecuencias, cálculo de proporciones y visualización (gráficos de barras para baja cardinalidad).
4.  **Análisis Bivariado:**
    *   **Numérica-Numérica:** Matriz de correlación, mapa de calor (heatmap) y diagramas de dispersión (scatter plots) para pares seleccionados.
    *   **Categórica-Categórica:** Tabla de contingencia (crosstab), gráfico de barras agrupadas y prueba Chi-cuadrado (ej: Sector vs Trend).
    *   **Numérica-Categórica:** Boxplots/Violin plots para comparar distribuciones numéricas entre categorías (ej: Close vs Sector, Sentiment_Score vs Trend), y estadísticas descriptivas agrupadas.
5.  **Identificación de Outliers:** Uso del método del Rango Intercuartílico (IQR) para identificar valores atípicos en variables numéricas clave.
6.  **Ingeniería de Características (Inicial):** Creación de nuevas variables a partir de las existentes:
    *   Componentes de Fecha: `Year`, `Month`, `Day`, `DayOfWeek`, `WeekOfYear`.
    *   Características de Precio: `PriceRange` (High-Low), `PriceChange` (Close-Open), `DailyReturn` ((Close-Open)/Open).
    *   Interacción: `Volume_x_Volatility`.

## Hallazgos Clave Resumidos

*   **Calidad de Datos:** El dataset sintético es de alta calidad, sin valores faltantes ni duplicados.
*   **Outliers:** No se detectaron outliers significativos usando el método 1.5*IQR, lo que puede deberse a la naturaleza controlada de los datos sintéticos.
*   **Distribuciones:** Las variables numéricas mostraron distribuciones mayormente simétricas y relativamente contenidas (curtosis negativa), a diferencia de lo que a menudo se ve en datos financieros reales.
*   **Variables Categóricas:** `Company` tiene alta cardinalidad y representación desbalanceada. `Sector` y `Trend` están razonablemente equilibrados.
*   **Relaciones:** Se confirmó la fuerte correlación esperada entre precios OHLC. Sin embargo, se encontraron correlaciones lineales débiles entre la mayoría de los otros pares numéricos. No se halló una asociación estadística significativa entre `Sector` y `Trend`. Variables como `Sentiment_Score` no mostraron una diferencia clara entre las etiquetas de `Trend`.
*   **Ingeniería de Características:** Se generaron con éxito 9 nuevas características que pueden ser útiles para análisis posteriores.

## Cómo Usar / Reproducir

1.  **Entorno:** El análisis fue realizado en un entorno tipo Jupyter Notebook / Google Colab.
2.  **Librerías Requeridas:**
    *   `pandas`
    *   `numpy`
    *   `matplotlib`
    *   `seaborn`
    *   `scipy` (para la prueba Chi-cuadrado)
3.  **Datos:** Asegúrate de que el archivo `synthetic_stock_data.csv` esté accesible (en el mismo directorio o ajustar la ruta en el código).
4.  **Ejecución:** Ejecuta las celdas del notebook (ej: `EDA_Stock_Data.ipynb` - *renombrar según tu archivo*) en orden secuencial.

---

**Nota:** Siéntete libre de modificar el nombre del notebook (`EDA_Stock_Data.ipynb`), añadir tu nombre o información de contacto, y ajustar cualquier detalle que consideres necesario para tu repositorio específico.