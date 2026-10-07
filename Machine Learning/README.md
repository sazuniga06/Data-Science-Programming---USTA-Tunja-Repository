# Machine Learning (Aprendizaje Automático) 🤖

> **Especialización en Ciencia de Datos**
> **Universidad Santo Tomás — Seccional Tunja**
> **Nivel Académico:** Semestre II
> **Docente / Gestor Virtual:** Santiago A. Zúñiga M.
> **Contacto:** [gestorvirtualcienciadatos@ustatunja.edu.co](mailto:gestorvirtualcienciadatos@ustatunja.edu.co)

<p align="center">
  <img src="https://img.shields.io/badge/Discipline-Machine%20Learning-8b5cf6?style=for-the-badge&logo=scikitlearn&logoColor=white" alt="Machine Learning"/>
  <img src="https://img.shields.io/badge/Topics-Supervisado%20%7C%20No%20Supervisado%20%7C%20Refuerzo-0ea5e9?style=for-the-badge" alt="Temas"/>
  <img src="https://img.shields.io/badge/Course-Machine%20Learning-6366f1?style=for-the-badge" alt="Course"/>
  <img src="https://img.shields.io/badge/Institution-USTA%20Tunja-1e3a8a?style=for-the-badge" alt="USTA"/>
</p>

---

## 📌 Descripción de la Asignatura

Fundamentos y práctica del aprendizaje automático: los tres paradigmas (supervisado, no supervisado y por refuerzo), los tipos de problema (clasificación, regresión, *clustering* y reglas de asociación), la importancia del preprocesamiento, los algoritmos clásicos (regresión lineal y logística, árboles de decisión, *Random Forests* y redes neuronales), las métricas de evaluación y el ajuste de hiperparámetros, el aprendizaje no supervisado (K-Means, jerárquico y DBSCAN, con sus métricas de validación), la reducción de dimensionalidad (PCA, t-SNE e Isomap), el aprendizaje por refuerzo (MDPs, funciones de valor, gradientes de política y DQN), la selección rigurosa de modelos (validación cruzada avanzada, Random Search y optimización bayesiana) y los temas avanzados con sus aplicaciones: transfer learning, explicabilidad, datasets desbalanceados, datos faltantes, visión por computador, NLP y sistemas de recomendación.

Cada módulo sigue la misma filosofía: **teoría rigurosa, implementaciones desde cero verificadas contra scikit-learn, resultados honestos** (lo que no funciona también se muestra) y **secciones «🛠️ Práctica»** con solución desplegable.

---

## 📚 Estructura Curricular Oficial de la Asignatura

El curso sigue el índice del libro de la asignatura en tres capítulos y se desarrolla en **10 módulos** (00 a 09), cada uno con su ruta estándar, su ruta **Para Dummies** y un taller práctico evaluativo:

| # | Módulo | Secciones del libro | Temas Principales | Ruta Estándar | Ruta Para Dummies | Taller Práctico |
|:---:|:---|:---:|:---|:---:|:---:|:---:|
| **00** | **Introducción al Machine Learning** | 1.1 – 1.6 | Definición de Mitchell, paradigmas, tipos de problema, ciclo de vida del proyecto, importancia del preprocesamiento y la fuga de datos | [Ver Cuadernos](00%20-%20Introduccion%20al%20Machine%20Learning/) | [Para Dummies](00%20-%20Introduccion%20al%20Machine%20Learning/Para%20Dummies/) | [Hands-On](homeworks/00_Introduccion_ML_Hands_On.ipynb) |
| **01** | **Modelos Lineales Supervisados** | 1.7, 1.8.1 – 1.8.2 | Riesgo empírico, sesgo-varianza, regresión lineal (ecuación normal y gradiente), regresión logística (entropía cruzada, softmax) | [Ver Cuadernos](01%20-%20Modelos%20Lineales%20Supervisados/) | [Para Dummies](01%20-%20Modelos%20Lineales%20Supervisados/Para%20Dummies/) | [Hands-On](homeworks/01_Modelos_Lineales_Hands_On.ipynb) |
| **02** | **Árboles, Bosques y Redes Neuronales** | 1.8.3 – 1.8.5 | CART desde cero, poda, *bagging* y *Random Forests*, retropropagación, MLP en NumPy y PyTorch | [Ver Cuadernos](02%20-%20Arboles%20Bosques%20y%20Redes%20Neuronales/) | [Para Dummies](02%20-%20Arboles%20Bosques%20y%20Redes%20Neuronales/Para%20Dummies/) | [Hands-On](homeworks/02_Arboles_Bosques_Redes_Hands_On.ipynb) |
| **03** | **Métricas y Ajuste de Hiperparámetros** | 1.9, 1.10 | Matriz de confusión, precision/recall/F1, ROC-AUC, MSE y familia, validación cruzada, GridSearch — cierra el Capítulo 1 | [Ver Cuadernos](03%20-%20Metricas%20y%20Ajuste%20de%20Hiperparametros/) | [Para Dummies](03%20-%20Metricas%20y%20Ajuste%20de%20Hiperparametros/Para%20Dummies/) | [Hands-On](homeworks/03_Metricas_y_Ajuste_Hands_On.ipynb) |
| **04** | **Clustering No Supervisado** | 2.1 – 2.5 | K-Means (Lloyd y k-means++), jerárquico, DBSCAN, Silhouette, Calinski-Harabasz y DBCV | [Ver Cuadernos](04%20-%20Clustering%20No%20Supervisado/) | [Para Dummies](04%20-%20Clustering%20No%20Supervisado/Para%20Dummies/) | [Hands-On](homeworks/04_Clustering_Hands_On.ipynb) |
| **05** | **Reducción de Dimensionalidad** | 2.6 | PCA (autovalores y SVD), t-SNE exacto, Isomap y variedades, *trustworthiness* | [Ver Cuadernos](05%20-%20Reduccion%20de%20Dimensionalidad/) | [Para Dummies](05%20-%20Reduccion%20de%20Dimensionalidad/Para%20Dummies/) | [Hands-On](homeworks/05_Reduccion_Dimensionalidad_Hands_On.ipynb) |
| **06** | **Aprendizaje por Refuerzo** | 2.7 – 2.9 | MDPs, ecuaciones de Bellman, Q-learning y SARSA, gradientes de política, DQN y REINFORCE | [Ver Cuadernos](06%20-%20Aprendizaje%20por%20Refuerzo/) | [Para Dummies](06%20-%20Aprendizaje%20por%20Refuerzo/Para%20Dummies/) | [Hands-On](homeworks/06_Aprendizaje_por_Refuerzo_Hands_On.ipynb) |
| **07** | **Selección de Modelos y Optimización** | 2.10 – 2.13 | Comparación estadística de modelos, calibración, validación cruzada anidada, Random Search y optimización bayesiana — cierra el Capítulo 2 | [Ver Cuadernos](07%20-%20Seleccion%20de%20Modelos%20y%20Optimizacion/) | [Para Dummies](07%20-%20Seleccion%20de%20Modelos%20y%20Optimizacion/Para%20Dummies/) | [Hands-On](homeworks/07_Seleccion_Modelos_Optimizacion_Hands_On.ipynb) |
| **08** | **Temas Avanzados de ML** | 3.1 – 3.7 | *Dataset shift*, transfer learning, explicabilidad (Shapley, LIME, gradientes integrados), desbalance (SMOTE), datos faltantes | [Ver Cuadernos](08%20-%20Temas%20Avanzados%20de%20ML/) | [Para Dummies](08%20-%20Temas%20Avanzados%20de%20ML/Para%20Dummies/) | [Hands-On](homeworks/08_Temas_Avanzados_Hands_On.ipynb) |
| **09** | **Casos de Estudio y Aplicaciones** | 3.8 – 3.11 | Proyecto integrador, visión por computador, NLP, sistemas de recomendación; incluye Glosario y Referencias Bibliográficas | [Ver Cuadernos](09%20-%20Casos%20de%20Estudio%20y%20Aplicaciones/) | [Para Dummies](09%20-%20Casos%20de%20Estudio%20y%20Aplicaciones/Para%20Dummies/) | [Hands-On](homeworks/09_Casos_Estudio_Aplicaciones_Hands_On.ipynb) |

> **Nota sobre el índice:** el Capítulo 2 del libro se titula *«Outline of the Scientific Research Process»*, pero su contenido real es aprendizaje no supervisado, refuerzo y selección de modelos; los módulos 04 a 07 se nombran por su contenido.

---

## 📝 Talleres Prácticos Evaluativos (Hands-On)

Los talleres de los 10 módulos, con su versión guiada **Para Dummies**, están centralizados en [`homeworks/`](homeworks/). A diferencia de los cuadernos de clase, **no incluyen soluciones**: traen retos con autoverificación (`assert`), rúbrica de evaluación y checklist de entrega. Consulta [`homeworks/README.md`](homeworks/README.md) para el mapa completo.

---

## 💡 Edición «Para Dummies» y Prácticas

- **Para Dummies:** cada cuaderno estándar tiene su espejo en la subcarpeta `Para Dummies/` de su módulo, con analogías cotidianas, sin jerga ni fórmulas y un solo bloque de práctica muy guiado.
- **Prácticas:** los cuadernos incluyen secciones «🛠️ Práctica» (enunciado, celda `# Escribe tu código aquí` y solución guiada desplegable) tomando como modelo el curso *Data Science programming*.

---

## 🛠️ Tecnologías y Librerías Utilizadas

* **Python 3.10+** (Entorno base de ejecución)
* **NumPy, Pandas, SciPy** (Cálculo numérico y manejo de datos)
* **Scikit-Learn** (Algoritmos, métricas, validación y *pipelines*)
* **Matplotlib, Seaborn** (Visualización)
* **PyTorch** (Redes neuronales, DQN y transfer learning; solo donde se indica)
* **Gymnasium** (Entornos de aprendizaje por refuerzo; opcional)
* **Opcionales:** `mlxtend`, `hdbscan`, `shap`, `imbalanced-learn`, `optuna`, `torchvision`, `transformers` (siempre con alternativa o aviso si no están instalados)

---

## 📖 Bibliografía de Apoyo

La carpeta [`Libros/`](Libros/) reúne la bibliografía de referencia del curso (por ejemplo *Hands-On Machine Learning with Scikit-Learn and PyTorch*, de A. Géron, y *Python Machine Learning*, de S. Raschka). Las referencias citadas a lo largo de los módulos están consolidadas, junto con el glosario, en el [README del módulo 09](09%20-%20Casos%20de%20Estudio%20y%20Aplicaciones/README.md).

---

<div align="center">
  <p style="font-size: 0.9em; color: #64748b;">
    © 2026 <b>Universidad Santo Tomás — Seccional Tunja</b><br>
    <i>Especialización en Ciencia de Datos | Plataforma de Laboratorios Virtuales</i>
  </p>
</div>
