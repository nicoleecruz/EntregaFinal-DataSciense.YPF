# 🌳 Análisis de la Deforestación en Argentina (2001–2020)

📊 Proyecto de Ciencia de Datos y Machine Learning  
👥 **Grupo 12 — Integrantes:**  
- Cruz Nicole  
- Ulloa Soto Melina Gimena  

---

## 📘 Introducción

La **deforestación** es uno de los desafíos ambientales más importantes en Argentina y el mundo.  
Este proyecto busca **analizar, visualizar y predecir** el comportamiento de la deforestación entre 2001 y 2020 utilizando técnicas de **ciencia de datos** y **machine learning**.

Aplicamos modelos:
- **Supervisados**: `Random Forest` para predicción.  
- **No supervisados**: `KMeans` para detección de patrones y agrupamiento de provincias según impacto ambiental.

📌 El objetivo es generar conocimiento útil para el diseño de **políticas públicas** y estrategias de conservación.

---

## 🎯 Objetivos

- Analizar la evolución de la deforestación en Argentina entre 2001 y 2020.  
- Detectar **patrones temporales y espaciales** de pérdida de cobertura vegetal.  
- Predecir la deforestación futura mediante modelos supervisados.  
- Agrupar provincias por comportamiento con modelos no supervisados.  
- Proveer herramientas analíticas para el diseño de políticas ambientales.

---

## 📂 Estructura del Repositorio

```
📦 deforestacion-argentina/
├── 📁 datasets/
│   ├── Argentina_Deforestacion.csv
│   └── Dataset_Forest_ConservationAreas_Funding_inSouthAmerica_PAN2024.csv
├── 📁 notebooks/
│   ├── analisis_supervisado.ipynb
│   └── clustering_no_supervisado.ipynb
├── 📁 visualizaciones/
│   └── mapas, heatmaps, gráficos por región
└── 📄 README.md
```

---

## 📊 Datasets Utilizados

### 📌 Dataset 1 — *Argentina_Deforestacion.csv*  
**Fuente:** Plataforma Trase  
- Filas: 2.381  
- Variables: Año, región, provincia (`parent_region`), hectáreas deforestadas  

### 📌 Dataset 2 — *Conservación de Bosques y Fondos PAN*  
- Filas: 10.328  
- Complementa información faltante del primer dataset  
- Se unificaron: **11.417 observaciones**

---

## 🔄 Metodología General

1. **Carga y limpieza de datos**  
   - Eliminación de columnas irrelevantes  
   - Revisión de nulos y duplicados (no se encontraron)  
   - Renombrado de columnas  
   - Conversión de tipos de datos  
   - Codificación de variables categóricas (`LabelEncoder`)  

2. **Análisis exploratorio**  
   - Boxplots, histogramas, líneas de tendencia  
   - Análisis por provincia y región  
   - Heatmap de correlaciones  

---

## 🤖 Modelos Aplicados

### 🧩 Aprendizaje Supervisado — `Random Forest Regressor`
- Variables de entrada: `year`, `parent_region_encoded`  
- Variable objetivo: `deforestation_hectares`  
- División: 80% entrenamiento / 20% prueba  

**Métricas obtenidas:**  
- MAE: `684.51`  
- MSE: `8.568.047`  
- R²: `0.29`  

📌 *El modelo capturó correctamente los picos de deforestación, aunque con margen de mejora.*

---

### 🧠 Aprendizaje No Supervisado — `KMeans`

- Variables utilizadas:  
  - `total_deforestation`  
  - `mean_deforestation`  
  - `years_count`  
- Normalización con `StandardScaler`  
- Número de clusters: `3` (según el método del codo)

| Cluster | Prom. Anual | Total Ha | Descripción                 |
|---------|-------------|----------|-----------------------------|
| 0       | ~899 ha     | ~108k    | Bajo impacto                |
| 1       | ~4.435 ha   | ~2.3M    | Alto impacto sostenido      |
| 2       | ~4.710 ha   | ~1.15M   | Impacto reciente, menor historial |

---

## 📍 Principales Hallazgos

- **Chaco** y **Santiago del Estero** concentran gran parte de la deforestación acumulada.  
- El período **2008–2012** mostró picos históricos de pérdida de bosque.  
- Los clusters distinguen regiones con impacto **sostenido** vs. **reciente**.  
- Las predicciones podrían mejorar incluyendo más variables explicativas.

---

## 🛠️ Herramientas Utilizadas

- 🧮 Python: `Pandas`, `NumPy`, `Matplotlib`, `Seaborn`  
- 🤖 `Scikit-learn` para modelado  
- 📓 Google Colab (ejecución de notebooks)  
- 💾 GitHub (gestión del proyecto)

---

## 🚀 Cómo Ejecutar el Proyecto

1. Clonar el repositorio:

```bash
git clone https://github.com/tu_usuario/deforestacion-argentina.git
cd deforestacion-argentina
```

2. Abrir los notebooks en **Google Colab** o **Jupyter Notebook**

3. Si lo ejecutás localmente, instalá las dependencias:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn
```

---

## 🌱 Futuro del Proyecto

Este trabajo sienta una base sólida para seguir profundizando en el análisis ambiental.

🔮 **Posibles mejoras:**
- Incluir variables climáticas, económicas o de uso del suelo  
- Incorporar imágenes satelitales (NDVI) y datos geoespaciales  
- Analizar la relación con reservas naturales  
- Aplicar modelos más complejos: `XGBoost`, `LightGBM`, redes neuronales  
- Probar técnicas como PCA, `DBSCAN`, `Agglomerative Clustering`

---

## 📌 Conclusión

Este proyecto demuestra cómo la ciencia de datos puede ayudar a entender procesos ambientales complejos.

> 🌎 **La deforestación es un problema urgente. Entenderla es el primer paso para detenerla.**
