# Talleres Prácticos Evaluativos (Hands-On Homeworks) 📝

> **Especialización en Ciencia de Datos**
> **Universidad Santo Tomás — Seccional Tunja**
> **Docente:** Santiago A. Zúñiga M.
> **Contacto:** [gestorvirtualcienciadatos@ustatunja.edu.co](mailto:gestorvirtualcienciadatos@ustatunja.edu.co)

---

## 📌 Descripción General

Esta carpeta contiene los **Talleres Prácticos Evaluativos (*Hands-On Homeworks*)** del curso **Machine Learning**, uno por cada módulo teórico, en dos ediciones:

* **Edición estándar** (esta carpeta): 4 a 5 retos integradores por taller, con problemas **nuevos** (no repiten los datos ni los ejemplos del módulo), rúbrica de evaluación y checklist de entrega.
* **Edición Para Dummies** ([`Para Dummies/`](Para%20Dummies/)): los mismos objetivos con 2 o 3 retos muy guiados, en lenguaje cotidiano y con pistas.

A diferencia de los cuadernos de clase, **los talleres no traen soluciones**: el estudiante los resuelve de forma autónoma. Cada reto incluye una celda de **autoverificación** con `assert` que falla con un mensaje claro mientras el reto no esté resuelto y pasa con una solución correcta. Todos los datos son sintéticos o de scikit-learn, con semilla fija y sin descargas.

---

## 🗺️ Mapa de Talleres del Curso

| # | Taller Práctico | Módulo Asociado | Retos |
|---|---|---|---|
| **00** | [**00_Introduccion_ML_Hands_On.ipynb**](00_Introduccion_ML_Hands_On.ipynb) · [Dummies](Para%20Dummies/00_Introduccion_ML_Hands_On_Dummies.ipynb) | **Módulo 00: Introducción al ML** | Formular el problema, cazar una fuga de datos, preprocesar sin trampa dentro de un `Pipeline`, medir el valor del preprocesamiento y evaluar con honestidad. |
| **01** | [**01_Modelos_Lineales_Hands_On.ipynb**](01_Modelos_Lineales_Hands_On.ipynb) · [Dummies](Para%20Dummies/01_Modelos_Lineales_Hands_On_Dummies.ipynb) | **Módulo 01: Modelos Lineales** | Regresión lineal por dentro y por fuera, variables gemelas y Ridge, de la regresión a la clasificación logística y Lasso como selección de variables. |
| **02** | [**02_Arboles_Bosques_Redes_Hands_On.ipynb**](02_Arboles_Bosques_Redes_Hands_On.ipynb) · [Dummies](Para%20Dummies/02_Arboles_Bosques_Redes_Hands_On_Dummies.ipynb) | **Módulo 02: Árboles, Bosques y Redes** | Profundidad de un árbol y sobreajuste, importancia de variables en un bosque, *forward pass* de una red a mano y duelo final entre modelos. |
| **03** | [**03_Metricas_y_Ajuste_Hands_On.ipynb**](03_Metricas_y_Ajuste_Hands_On.ipynb) · [Dummies](Para%20Dummies/03_Metricas_y_Ajuste_Hands_On_Dummies.ipynb) | **Módulo 03: Métricas y Ajuste** | Matriz de confusión a mano y paradoja de la exactitud, umbral por costo sin mirar la prueba, métricas de regresión y línea base, GridSearch sin fuga. |
| **04** | [**04_Clustering_Hands_On.ipynb**](04_Clustering_Hands_On.ipynb) · [Dummies](Para%20Dummies/04_Clustering_Hands_On_Dummies.ipynb) | **Módulo 04: Clustering** | Escala, elección de *k* e inercia en K-Means, jerarquía y enlaces, DBSCAN y la trampa de la silueta, ARI desde cero y estabilidad entre semillas. |
| **05** | [**05_Reduccion_Dimensionalidad_Hands_On.ipynb**](05_Reduccion_Dimensionalidad_Hands_On.ipynb) · [Dummies](Para%20Dummies/05_Reduccion_Dimensionalidad_Hands_On_Dummies.ipynb) | **Módulo 05: Reducción de Dimensionalidad** | PCA con criterio (escala, varianza y reconstrucción), PCA desde cero con la SVD, t-SNE y perplejidad, Isomap frente a PCA en una variedad enrollada. |
| **06** | [**06_Aprendizaje_por_Refuerzo_Hands_On.ipynb**](06_Aprendizaje_por_Refuerzo_Hands_On.ipynb) · [Dummies](Para%20Dummies/06_Aprendizaje_por_Refuerzo_Hands_On_Dummies.ipynb) | **Módulo 06: Refuerzo** | Retornos y Monte Carlo, evaluación exacta e iteración de valor, Q-learning tabular y REINFORCE en un bandido de tres brazos (NumPy puro). |
| **07** | [**07_Seleccion_Modelos_Optimizacion_Hands_On.ipynb**](07_Seleccion_Modelos_Optimizacion_Hands_On.ipynb) · [Dummies](Para%20Dummies/07_Seleccion_Modelos_Optimizacion_Hands_On_Dummies.ipynb) | **Módulo 07: Selección y Optimización** | Protocolo, línea base e intervalo de confianza, fuga por grupos en la validación cruzada, comparación estadística de modelos, búsqueda aleatoria y calibración. |
| **08** | [**08_Temas_Avanzados_Hands_On.ipynb**](08_Temas_Avanzados_Hands_On.ipynb) · [Dummies](Para%20Dummies/08_Temas_Avanzados_Hands_On_Dummies.ipynb) | **Módulo 08: Temas Avanzados** | *Dataset shift* entre entrenamiento y producción, fraude raro (desbalance), encuesta con huecos (datos faltantes) y abrir la caja negra (explicabilidad). |
| **09** | [**09_Casos_Estudio_Aplicaciones_Hands_On.ipynb**](09_Casos_Estudio_Aplicaciones_Hands_On.ipynb) · [Dummies](Para%20Dummies/09_Casos_Estudio_Aplicaciones_Hands_On_Dummies.ipynb) | **Módulo 09: Casos y Aplicaciones** | Proyecto integrador: preparación sin fuga, línea base y comparación de modelos, decisión por costo, y explicar, auditar y documentar el modelo. |

---

## 📋 Instrucciones y Criterios de Entrega

1. **Entorno de Ejecución:** Python 3.10+ con NumPy, Pandas, SciPy, Scikit-Learn y Matplotlib. Los talleres no requieren PyTorch, Gymnasium ni librerías opcionales.
2. **Ejecución Completa:** antes de la entrega, reinicia el kernel y ejecuta todas las celdas (*Restart Kernel and Run All Cells*). No deben quedar `# TODO` ni `...` pendientes y todas las celdas de autoverificación deben pasar.
3. **Autonomía:** los talleres no incluyen soluciones; consulta los cuadernos del módulo correspondiente como material de apoyo.
4. **Conclusiones:** el último reto de cada taller estándar es una reflexión escrita (5 a 8 líneas) que interpreta tus resultados.
5. **Evaluación:** cada taller suma 100 puntos; la rúbrica por criterio está al final de cada cuaderno.
6. **Tiempos:** la mayoría corre en menos de 60 segundos. El taller 02 estándar puede tardar entre uno y dos minutos, y el reto 3 del taller 05 (t-SNE) unos 20 segundos.

---

<div align="center">
  <p style="font-size: 0.9em; color: #64748b;">
    © 2026 <b>Universidad Santo Tomás — Seccional Tunja</b><br>
    <i>Especialización en Ciencia de Datos | Machine Learning</i>
  </p>
</div>
