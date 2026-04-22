# Práctica 2 — Técnicas de Análisis

Trabajo de la asignatura **Minería de Datos** en el que se aplican técnicas de aprendizaje supervisado y no supervisado sobre el dataset **Obesity Levels** (UCI Machine Learning Repository).

## Objetivo

Aplicar y comparar las principales técnicas de minería de datos vistas en clase:

- **Parte 1:** Regresión y clasificación (con árboles de decisión como modelo obligatorio).
- **Parte 2:** Ensembles y clustering.

A partir de hábitos alimenticios, actividad física y condición física de 2.111 individuos, se busca:

1. **Predecir el peso corporal** (`Weight`) a partir del resto de variables — *regresión*.
2. **Predecir el nivel de obesidad** (`NObeyesdad`, 7 clases) — *clasificación multiclase*.
3. **Mejorar la clasificación anterior** mediante ensembles (Random Forest, Gradient Boosting, etc.).
4. **Descubrir perfiles de estilo de vida** mediante clustering no supervisado y compararlos con las etiquetas reales.

## Dataset

**Nombre:** *Estimation of Obesity Levels Based on Eating Habits and Physical Condition*
**Fuente:** UCI Machine Learning Repository
**URL:** https://archive.ics.uci.edu/dataset/544/estimation+of+obesity+levels+based+on+eating+habits+and+physical+condition
**Archivo usado:** `.vscode/ObesityDataSet_raw_and_data_sinthetic.csv`
**Tamaño:** 2.111 filas × 17 columnas
**Origen de los datos:** 23% observaciones reales (México, Perú, Colombia) + 77% generados sintéticamente mediante SMOTE para equilibrar las clases.

### Variables

| Tipo                             | Columnas                                                                                      |
| -------------------------------- | --------------------------------------------------------------------------------------------- |
| Demográficas / antropométricas | `Gender`, `Age`, `Height`, `Weight`                                                   |
| Hábitos alimenticios            | `family_history_with_overweight`, `FAVC`, `FCVC`, `NCP`, `CAEC`, `CH2O`, `CALC` |
| Estilo de vida                   | `SMOKE`, `SCC`, `FAF`, `TUE`, `MTRANS`                                              |
| **Target**                 | `NObeyesdad` (7 clases)                                                                     |

### Clases de `NObeyesdad`

`Insufficient_Weight`, `Normal_Weight`, `Overweight_Level_I`, `Overweight_Level_II`, `Obesity_Type_I`, `Obesity_Type_II`, `Obesity_Type_III`

## Cumplimiento de requisitos

| Requisito                              | Cumplimiento                                 |
| -------------------------------------- | -------------------------------------------- |
| ≥4 dimensiones + variable objetivo    | ✅ 16 features + target                      |
| Clasificación multiclase (≥3 clases) | ✅ 7 clases                                  |
| Árboles de decisión obligatorios     | ✅ Parte 1                                   |
| Ensembles multiclase                   | ✅ Parte 2 (mismo target que clasificación) |
| Clustering con ≥3 dimensiones         | ✅ Parte 2                                   |

## Estructura del repositorio

```
PRACTICA_2/
├── README.md                                       ← este archivo
└── .vscode/
    ├── practica_2.ipynb                            ← notebook principal
    └── ObesityDataSet_raw_and_data_sinthetic.csv   ← dataset
```

## Estructura del notebook

1. **Introducción y requisitos de la práctica.**
2. **Parte 1 — Regresión y clasificación**
   - Carga del dataset.
   - Descripción de variables.
   - Análisis exploratorio (distribución de clases, countplot, pairplot, heatmap de correlaciones).
   - Preprocesado (codificación binaria, ordinal para `CAEC`/`CALC`, one-hot para `MTRANS`).
   - Regresión con árbol de decisión sobre `Weight`.
   - Clasificación con árbol de decisión sobre `NObeyesdad`.
   - Métricas, visualización del árbol e importancias de variables.
3. **Parte 2 — Ensembles y clustering**
   - Ensembles (Random Forest / Gradient Boosting) para comparar con el árbol base.
   - Clustering (KMeans / jerárquico) sobre variables de hábitos.
   - Comparación de clusters con las etiquetas reales (ARI, matriz de confusión).
   - Conclusiones.

## Preprocesado aplicado

| Variable                                                                       | Transformación                                                            |
| ------------------------------------------------------------------------------ | -------------------------------------------------------------------------- |
| `Gender`, `family_history_with_overweight`, `FAVC`, `SMOKE`, `SCC`   | Mapeo binario 0/1                                                          |
| `CAEC`, `CALC`                                                             | Escala ordinal 0–3 (`no` < `Sometimes` < `Frequently` < `Always`) |
| `MTRANS`                                                                     | One-hot encoding                                                           |
| `Age`, `Height`, `Weight`, `FCVC`, `NCP`, `CH2O`, `FAF`, `TUE` | Sin transformación (ya numéricas)                                        |

## Requisitos técnicos

- Python ≥ 3.9
- Librerías:
  ```
  pandas
  numpy
  matplotlib
  seaborn
  scikit-learn
  ```

Instalación rápida:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn
```

## Ejecución

1. Abrir `.vscode/practica_2.ipynb` en Jupyter, VS Code o cualquier entorno compatible.
2. Asegurarse de que el CSV está en el mismo directorio que el notebook (o ajustar la ruta de `pd.read_csv`).
3. Ejecutar las celdas en orden.

## Autoras

* Itsaso Ariztimuño Cenoz
* Jimena Mill Moreno

— Minería de Datos, Máster en Ciencia de Datos, curso 2025/2026.
