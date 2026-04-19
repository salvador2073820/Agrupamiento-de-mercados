# 🌐 Clustering de Mercados Financieros Globales

> Análisis no supervisado de 12 índices bursátiles internacionales mediante K-Means, PCA y Clustering Jerárquico, utilizando datos reales descargados con `yfinance`.

---

## 📋 Tabla de Contenidos

- [Descripción del Proyecto](#descripción-del-proyecto)
- [Mercados Analizados](#mercados-analizados)
- [Tecnologías Utilizadas](#tecnologías-utilizadas)
- [Estructura del Proyecto](#estructura-del-proyecto)
- [Feature Engineering](#feature-engineering)
- [Metodología](#metodología)
- [Resultados](#resultados)
- [Cómo Ejecutar el Proyecto](#cómo-ejecutar-el-proyecto)
- [Autor](#autor)

---

## 📌 Descripción del Proyecto

Los mercados financieros globales no se comportan de forma aislada: algunos se mueven en sincronía, otros presentan dinámicas completamente distintas. Este proyecto aplica técnicas de **Machine Learning no supervisado** para descubrir agrupaciones naturales entre 12 índices bursátiles de diferentes regiones del mundo.

A partir de datos históricos desde **enero 2019**, se construye un perfil cuantitativo de cada mercado (retorno, volatilidad, riesgo, momentum) y se aplican tres enfoques de clustering para encontrar patrones estructurales entre ellos.

---

## 📈 Mercados Analizados

| Índice | Ticker | Región |
|---|---|---|
| S&P 500 | `^GSPC` | América del Norte |
| NASDAQ | `^IXIC` | América del Norte |
| IPC México | `^MXX` | América Latina |
| Bovespa Brasil | `^BVSP` | América Latina |
| DAX | `^GDAXI` | Europa |
| CAC 40 | `^FCHI` | Europa |
| FTSE 100 | `^FTSE` | Europa |
| Nikkei 225 | `^N225` | Asia-Pacífico |
| Shanghai | `000001.SS` | Asia |
| NIFTY 50 | `^NSEI` | Asia |
| KOSPI | `^KS11` | Asia |
| ASX 200 | `^AXJO` | Asia-Pacífico |

---

## 🛠 Tecnologías Utilizadas

![Python](https://img.shields.io/badge/Python-3.13-blue?logo=python)
![yfinance](https://img.shields.io/badge/yfinance-Data-0d6efd)
![Scikit-learn](https://img.shields.io/badge/Scikit--learn-ML-F7931E?logo=scikit-learn)
![Seaborn](https://img.shields.io/badge/Seaborn-Viz-4c72b0)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange?logo=jupyter)

```
yfinance      → Descarga de datos históricos de precios
pandas/numpy  → Procesamiento y cálculo de métricas financieras
scikit-learn  → KMeans, PCA, StandardScaler
scipy         → Clustering jerárquico y dendrogramas
matplotlib    → Visualizaciones
seaborn       → Matriz de correlación
```

---

## 📁 Estructura del Proyecto

```
Analisis-Mercados-Financieros/
│
├── Mercados.ipynb       # Notebook principal con todo el análisis
└── README.md            # Este archivo
```

> No se requiere ningún archivo CSV: los datos se descargan automáticamente con `yfinance` al ejecutar el notebook.

---

## 🔬 Feature Engineering

Para cada mercado se construyen **8 métricas financieras** a partir de los retornos diarios:

| Feature | Descripción | Fórmula |
|---|---|---|
| `mean_return` | Retorno anual promedio | `mean(r) × 252` |
| `volatility` | Volatilidad anual | `std(r) × √252` |
| `skewness` | Asimetría de los retornos | — |
| `kurtosis` | Curtosis (colas de la distribución) | — |
| `sharpe_ratio` | Rentabilidad ajustada al riesgo | `mean_return / volatility` |
| `max_drawdown` | Caída máxima desde el pico | `min((cum - peak) / peak)` |
| `VaR_95` | Value at Risk al 95% | `quantile(r, 0.05)` |
| `momentum` | Tendencia anual promedio | `pct_change(252).mean()` |

---

## 🔄 Metodología

```
1. Descarga de precios de cierre (yfinance, desde 2019)
         ↓
2. Cálculo de retornos diarios (pct_change)
         ↓
3. Feature Engineering (8 métricas por mercado)
         ↓
4. Escalado de datos (StandardScaler)
         ↓
5. Método Elbow → selección de k=3 clusters
         ↓
6. K-Means Clustering
         ↓
7. Visualización PCA (2 componentes)
         ↓
8. Matriz de correlación entre mercados
         ↓
9. Clustering Jerárquico (Ward, dendrograma)
         ↓
10. Clustering basado en distancia de correlación
```

---

## 📊 Resultados

### Clusters obtenidos (K-Means, k=3)

| Cluster | Mercados | Perfil |
|---|---|---|
| **0** | SP500, BRAZIL, DAX, CAC40, NIKKEI, NIFTY, KOSPI | Mercados de alto rendimiento / alta exposición global |
| **1** | MEXICO, FTSE, SHANGHAI, ASX | Mercados de menor volatilidad relativa / más defensivos |
| **2** | NASDAQ | Perfil único: mayor retorno y mayor volatilidad tecnológica |

### Métricas destacadas

| Mercado | Retorno Anual | Volatilidad | Sharpe Ratio | Max Drawdown |
|---|---|---|---|---|
| NASDAQ | 25.5% | 25.7% | 0.99 | -36.1% |
| SP500 | 20.4% | 21.2% | 0.96 | -33.9% |
| NIKKEI | 22.2% | 23.8% | 0.93 | -31.2% |
| KOSPI | 21.9% | 24.2% | 0.90 | -35.7% |
| FTSE | 9.2% | 17.9% | 0.51 | -35.0% |
| MEXICO | 10.3% | 18.9% | 0.55 | -28.1% |
| SHANGHAI | 11.0% | 19.0% | 0.58 | -27.2% |

> **NASDAQ** se agrupa solo en su propio cluster por su perfil tecnológico distintivo: el mayor Sharpe Ratio pero también la mayor volatilidad.

> **Shanghai y ASX** agrupan con mercados defensivos (México, FTSE) por su menor drawdown y volatilidad controlada.

### ⚠️ Nota técnica

La celda 13 genera un `ClusterWarning` de scipy al aplicar `linkage` sobre una matriz de distancias ya condensada. Para corregirlo:

```python
from scipy.spatial.distance import squareform

# Convertir la matriz cuadrada a forma condensada antes del linkage
Z_corr = linkage(squareform(distance), method="ward")
```

---

## ▶️ Cómo Ejecutar el Proyecto

### 1. Clonar el repositorio

```bash
git clone https://github.com/SalvadorHernandezJuarez/Prediccion-abandono-de-clientes.git
cd Prediccion-abandono-de-clientes
```

### 2. Instalar dependencias

```bash
pip install pandas numpy matplotlib seaborn yfinance scikit-learn scipy jupyter
```

### 3. Ejecutar el notebook

```bash
jupyter notebook Mercados.ipynb
```

> Se requiere conexión a internet para descargar los datos históricos con `yfinance`.

---

## 👤 Autor

**Salvador Hernández Juárez**

[![GitHub](https://img.shields.io/badge/GitHub-SalvadorHernandezJuarez-181717?logo=github)](https://github.com/SalvadorHernandezJuarez)

---

*Proyecto de Machine Learning No Supervisado — Clustering de Mercados Financieros Globales*
