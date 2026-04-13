# 📊 Clustering de Mercados Financieros mediante Minería de Datos

Este proyecto aplica técnicas de **aprendizaje no supervisado** para identificar similitudes estructurales entre mercados financieros globales. A partir de datos históricos de índices bursátiles, se construyen variables financieras clave y se utilizan algoritmos de clustering para agrupar mercados con comportamientos similares.

El objetivo es descubrir **patrones ocultos en los mercados**, permitiendo entender mejor su estructura, niveles de riesgo y relaciones globales.

---

## Mercados Analizados

Se analizaron los siguientes índices bursátiles:

* S&P 500 (EE.UU.)
* NASDAQ (EE.UU.)
* IPC (México)
* Bovespa (Brasil)
* DAX (Alemania)
* CAC40 (Francia)
* FTSE100 (Reino Unido)
* Nikkei 225 (Japón)
* Shanghai Composite (China)
* Nifty 50 (India)
* KOSPI (Corea del Sur)
* ASX 200 (Australia)

---
### 1. Recolección de datos

* Fuente: Yahoo Finance (`yfinance`)
* Periodo: 2019 - Actualidad

### 2. Se calcularon los siguientes indicadores financieros:

* Retorno promedio anual
* Volatilidad anual
* Asimetría (Skewness)
* Curtosis (Kurtosis)
* Ratio de Sharpe
* Máximo Drawdown
* Value at Risk (VaR 95%)
* Momentum

## 📊 Visualizaciones

El proyecto incluye:

* Método Elbow (selección de clusters)
* Gráfico PCA (visualización de clusters)
* Mapa de correlaciones (heatmap)
* Dendrograma jerárquico
* Dendrograma basado en correlaciones

---

## 📂 Estructura del Proyecto

```id="k3f8aa"
financial-market-clustering/

│── data/
│── notebooks/
│── src/
│── market_clustering.py
│── requirements.txt
│── README.md
```

---

## Cómo ejecutar el proyecto

1. Clonar el repositorio:

```id="m2l0od"
git clone https://github.com/tu-usuario/financial-market-clustering.git
```

2. Instalar dependencias:

```id="9i3tbn"
pip install -r requirements.txt
```

3. Ejecutar el script:

```id="2f7kxl"
python market_clustering.py
```

---

## Autor

Salvador Hernandez
Estudiante de Ingeniería en Software | Enfoque en Mineria de Datos

Este proyecto demuestra la aplicación de técnicas de **machine learning en mercados financieros**, combinando análisis estadístico y modelos de clustering para extraer conocimiento a partir de datos complejos.

