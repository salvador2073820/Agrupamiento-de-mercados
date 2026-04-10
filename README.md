# 📊 Clustering de Mercados Financieros mediante Minería de Datos

## 📌 Descripción del Proyecto

Este proyecto aplica técnicas de **aprendizaje no supervisado** para identificar similitudes estructurales entre mercados financieros globales. A partir de datos históricos de índices bursátiles, se construyen variables financieras clave y se utilizan algoritmos de clustering para agrupar mercados con comportamientos similares.

El objetivo es descubrir **patrones ocultos en los mercados**, permitiendo entender mejor su estructura, niveles de riesgo y relaciones globales.

---

## 🎯 Objetivos

* Obtener datos históricos de mercados financieros globales
* Construir variables financieras relevantes
* Aplicar algoritmos de clustering
* Visualizar relaciones entre mercados
* Interpretar resultados desde un enfoque financiero

---

## 🌍 Mercados Analizados

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

## 🧠 Metodología

### 1. Recolección de datos

* Fuente: Yahoo Finance (`yfinance`)
* Periodo: 2019 - Actualidad

### 2. Ingeniería de características

Se calcularon los siguientes indicadores financieros:

* Retorno promedio anual
* Volatilidad anual
* Asimetría (Skewness)
* Curtosis (Kurtosis)
* Ratio de Sharpe
* Máximo Drawdown
* Value at Risk (VaR 95%)
* Momentum

### 3. Preprocesamiento

* Eliminación de valores faltantes
* Escalado de variables con `StandardScaler`

### 4. Técnicas de Clustering

#### 🔹 K-Means

* Agrupamiento de mercados en clusters
* Selección del número óptimo con método Elbow

#### 🔹 Clustering Jerárquico

* Método de Ward
* Representación mediante dendrogramas

#### 🔹 Clustering basado en correlaciones

* Distancia definida como:

  distance = √(2(1 - correlación))

* Permite identificar mercados que se mueven de forma similar

### 5. Reducción de dimensionalidad

* PCA (Análisis de Componentes Principales) para visualización

---

## 📈 Resultados e Interpretación

El análisis permitió identificar distintos grupos de mercados financieros:

### 🔹 Mercados desarrollados

* Menor volatilidad
* Retornos más estables
* Mejor relación riesgo-retorno
* Ejemplo: S&P 500, NASDAQ, DAX

### 🔹 Mercados emergentes

* Mayor volatilidad
* Caídas más pronunciadas (drawdowns)
* Mayor incertidumbre
* Ejemplo: México, Brasil

### 🔹 Mercados asiáticos

* Alta correlación regional
* Comportamientos propios del mercado asiático
* Ejemplo: China, Japón, Corea

### 💡 Insights clave

* Los mercados se agrupan según su **perfil de riesgo y comportamiento histórico**
* Existen patrones **regionales y estructurales**
* El clustering basado en correlaciones revela relaciones importantes para **diversificación de portafolios**

---

## 📊 Visualizaciones

El proyecto incluye:

* Método Elbow (selección de clusters)
* Gráfico PCA (visualización de clusters)
* Mapa de correlaciones (heatmap)
* Dendrograma jerárquico
* Dendrograma basado en correlaciones

---

## 🛠️ Tecnologías utilizadas

* Python
* Pandas
* NumPy
* Scikit-learn
* Matplotlib
* Seaborn
* SciPy
* yfinance

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

## 🚀 Cómo ejecutar el proyecto

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

## 📌 Mejoras futuras

* Incluir más mercados (30+ índices)
* Agregar indicadores técnicos (RSI, MACD)
* Construir grafos de correlación entre mercados
* Analizar clustering dinámico en el tiempo
* Crear dashboard interactivo (Streamlit)

---

## 💼 Autor

Salvador Hernandez
Estudiante de Ingeniería en Software | Enfoque en Ciencia de Datos

---

## ⭐ Nota final

Este proyecto demuestra la aplicación de técnicas de **machine learning en mercados financieros**, combinando análisis estadístico y modelos de clustering para extraer conocimiento a partir de datos complejos.

---
