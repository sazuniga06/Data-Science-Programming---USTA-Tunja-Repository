# Módulo 03: Métricas y Ajuste de Hiperparámetros 🎯🔄

<p align="center">
  <img src="https://img.shields.io/badge/Discipline-Machine%20Learning-059669?style=for-the-badge&logo=scikitlearn&logoColor=white" alt="Machine Learning"/>
  <img src="https://img.shields.io/badge/Topics-M%C3%A9tricas%20%26%20Ajuste%20de%20Hiperpar%C3%A1metros-0ea5e9?style=for-the-badge" alt="Topics"/>
  <img src="https://img.shields.io/badge/Course-Machine%20Learning-6366f1?style=for-the-badge" alt="Course"/>
  <img src="https://img.shields.io/badge/Institution-USTA%20Tunja-1e3a8a?style=for-the-badge" alt="USTA"/>
</p>

Bienvenido al **Módulo 03** de la asignatura **Machine Learning** de la *Especialización en Ciencia de Datos* de la **Universidad Santo Tomás — Seccional Tunja**.

---

## 🧭 ¿De qué trata este módulo?

Este módulo corresponde a las **secciones 1.9 y 1.10 del Capítulo 1** del syllabus y **cierra el capítulo**. Tras estudiar los modelos lineales ([Módulo 01](../01%20-%20Modelos%20Lineales%20Supervisados/README.md)) y los modelos no lineales —árboles, bosques y redes ([Módulo 02](../02%20-%20Arboles%20Bosques%20y%20Redes%20Neuronales/README.md))—, toca responder dos preguntas que determinan si un modelo sirve de verdad: **¿cómo medimos qué tan bueno es?** (sección 1.9: *Accuracy*, *Precision*, *Recall*, *F1-Score* y la familia del *Mean Squared Error*) y **¿cómo lo ajustamos sin hacer trampa?** (sección 1.10: *Hyperparameter Tuning*, *Cross-Validation* y *GridSearch*).

El enfoque es **más profundo** que el de los cursos previos: cada métrica se **define formalmente**, se **implementa desde cero en NumPy** y se **verifica contra `scikit-learn`** con `assert` dentro del propio cuaderno (matriz de confusión, *precision/recall/F-β*, promedios *macro/micro/weighted*, ROC-AUC por rangos, precisión promedio, MSE/RMSE/MAE/R²/MAPE, `KFold`, `StratifiedKFold`, *leave-one-out* y un *GridSearch* completo que reproduce `GridSearchCV`). Además se estudian las **trampas de interpretación**: la paradoja de la exactitud con clases desbalanceadas, el umbral de decisión y el costo de cada error, el R² negativo en prueba, el sesgo de MAPE hacia subestimar, la sensibilidad a *outliers*, el sesgo de selección al ajustar sobre la prueba y la **fuga de datos** dentro de la validación cruzada.

> 🔗 **Conexión con otros cursos:** este módulo **no repite** el manejo práctico de métricas con `scikit-learn` ya visto en [Data Science Programming — Módulo 08 (Classification)](../../Data%20Science%20programming/08%20-%20Classification/README.md), [Data Science Programming — Módulo 07 (Regression)](../../Data%20Science%20programming/07%20-%20Regression/README.md) ni [Data Mining — Módulo 02 (Clasificación y Regresión)](../../Data%20Mining/02%20-%20Clasificacion%20y%20Regresion/README.md); los enlaza y profundiza en lo que allá no se aborda: definiciones formales, implementación propia, propiedades matemáticas, simulaciones del sesgo y la varianza de la validación cruzada y análisis de `cv_results_`. La búsqueda aleatoria, la validación cruzada anidada y la optimización bayesiana se **mencionan** aquí y se desarrollan en el Módulo 07.


> 🛠️ **Ponlo en práctica:** todos los cuadernos (estándar y *Para Dummies*) incluyen secciones **«🛠️ Práctica»**: una celda de código para que escribas tu solución y, justo debajo, la **solución guiada desplegable** (`💡 Haz clic aquí para ver la solución guiada...`). Inténtalo primero y abre la solución solo para comparar.
---

## 📚 Estructura Curricular del Módulo

### 🎓 1. Cuadernos Académicos Estándar:
1. [**00_Metricas_de_Clasificacion.ipynb**](00_Metricas_de_Clasificacion.ipynb): *Sección 1.9 (1.9.1 a 1.9.4).* Matriz de confusión (VP, FP, FN, VN) y definiciones formales, ***accuracy* y la paradoja de la exactitud** (demostración con 1 % de fraude, accuracy balanceada y MCC), *precision* y *recall* como compromiso según el **umbral de decisión** (curva precision–recall construida desde cero), **F1 como media armónica** (por qué no aritmética) y $F_\beta$, promedios ***macro/micro/weighted*** y multiclase, **costo de los errores y umbral óptimo** $t^{\ast}=c_{FP}/(c_{FP}+c_{FN})$, introducción a **ROC-AUC y PR-AUC** (cálculo por rangos y por suma escalonada, efecto de la prevalencia) y `classification_report` reproducido a mano. Todo verificado contra `sklearn.metrics`.
2. [**01_Metricas_de_Regresion.ipynb**](01_Metricas_de_Regresion.ipynb): *Sección 1.9 (familia del Mean Squared Error).* MSE, RMSE, MAE, MedAE y R² desde cero, **media vs. mediana** como minimizadores de MSE y MAE, **R² negativo en prueba** (identidad exacta con el modelo base y `DummyRegressor`), **MAPE y sMAPE y sus trampas** (división por cero, asimetría, sesgo hacia subestimar con óptimo teórico $e^{\mu-\sigma^2}$), **sensibilidad a *outliers*** (MSE vs. MAE vs. Huber, con demostración numérica), la **lectura probabilística** (MSE ↔ máxima verosimilitud gaussiana, MAE ↔ Laplace) y cómo **elegir y reportar** el error (unidades del problema, baseline, intervalos *bootstrap*).
3. [**02_Validacion_Cruzada_y_GridSearch.ipynb**](02_Validacion_Cruzada_y_GridSearch.ipynb): *Sección 1.10.* Parámetros vs. hiperparámetros, por qué **no** se ajusta con el *test* (simulación del sesgo de selección), *hold-out* vs. *k-fold*, **`KFold` y `StratifiedKFold` desde cero** (pliegues idénticos a los de `scikit-learn`), *leave-one-out* con su atajo cerrado (PRESS), **sesgo y varianza del estimador de CV según $k$** (simulación), **fuga de datos** y su solución con `Pipeline`, **GridSearch desde cero** verificado contra `GridSearchCV`, `cv_results_` con `pandas` y mapa de calor de dos hiperparámetros, `scoring` personalizado y `refit`, y la **explosión combinatoria** de la rejilla.

---

### 📝 2. Taller Práctico Evaluativo (*Hands-On*):
* [**../homeworks/03_Metricas_y_Ajuste_Hands_On.ipynb**](../homeworks/03_Metricas_y_Ajuste_Hands_On.ipynb): Taller evaluativo que integra métricas de clasificación y regresión, validación cruzada y búsqueda de hiperparámetros en ejercicios prácticos.

---

### 🧸 3. Ruta Didáctica: Para Dummies:
Ubicada en la subcarpeta [`Para Dummies/`](Para%20Dummies/):
1. [**00_Metricas_Clasificacion_Dummies.ipynb**](Para%20Dummies/00_Metricas_Clasificacion_Dummies.ipynb): La alarma de humo y sus cuatro resultados posibles, la trampa del 99 % de aciertos, la **red de pesca** (precisión vs. cobertura según qué tan exigente sea el modelo), el F1 como «promedio exigente» y cuál nota priorizar en cada problema.
2. [**01_Metricas_Regresion_Dummies.ipynb**](Para%20Dummies/01_Metricas_Regresion_Dummies.ipynb): Un agente inmobiliario en Tunja: el error promedio en pesos, el «profesor exigente» que castiga los fallos graves, el R² como comparación con el **amigo que adivina el promedio** (y por qué puede ser negativo), las trampas de los porcentajes y cómo contar bien el error.
3. [**02_Validacion_Cruzada_GridSearch_Dummies.ipynb**](Para%20Dummies/02_Validacion_Cruzada_GridSearch_Dummies.ipynb): Simulacros y examen final: por qué no se vale mirar el examen, la validación cruzada como simulacros rotativos, la **fuga de datos** («ver las respuestas antes»), el cocinero que prueba todas las recetas (GridSearch) y por qué demasiadas combinaciones se vuelven carísimas.

---

## 💾 Datos Utilizados

Este módulo **no requiere archivos externos**: usa datasets incluidos en `scikit-learn` (*Breast Cancer Wisconsin*, *Diabetes* con su respuesta en unidades originales y *Dígitos*) y **datos sintéticos generados en el propio código con semilla fija** (`make_classification` con `weights` para el desbalance de clases, distribuciones gaussianas, de Laplace y log-normales, y ruido puro para las demostraciones de sesgo de selección y fuga de datos). No se usa ningún `fetch_*` ni descarga de conjuntos de datos. Por eso los cuadernos se ejecutan sin conexión a internet y de forma reproducible, tanto en local como en Google Colab.

---

## ⚙️ Requisitos

`numpy`, `pandas`, `matplotlib`, `seaborn`, `scikit-learn` y `scipy` (preinstalados en Google Colab). Ningún cuaderno de este módulo requiere PyTorch ni librerías adicionales. Los tres cuadernos estándar se ejecutan en **menos de un minuto** cada uno en un equipo de escritorio (el de validación cruzada es el más lento por sus simulaciones y búsquedas en rejilla).

---

## 📚 Lecturas Complementarias

Como este módulo **cierra el Capítulo 1**, estas lecturas profundizan en la evaluación y la selección de modelos. *Todas están citadas de memoria: verifica los datos bibliográficos antes de citarlas formalmente.*

1. Davis, J. & Goadrich, M. (2006). *The relationship between Precision-Recall and ROC curves*. **Proceedings of the 23rd International Conference on Machine Learning (ICML 2006)**, pp. 233–240. Muestra la correspondencia entre ambas curvas y por qué la interpolación lineal en el espacio PR es engañosa. *(citado de memoria, verificar)*
2. Saito, T. & Rehmsmeier, M. (2015). *The Precision-Recall Plot Is More Informative than the ROC Plot When Evaluating Binary Classifiers on Imbalanced Datasets*. **PLoS ONE** 10(3): e0118432. *(citado de memoria, verificar)*
3. Powers, D. M. W. (2011). *Evaluation: from precision, recall and F-measure to ROC, informedness, markedness and correlation*. **Journal of Machine Learning Technologies** 2(1): 37–63. Crítica del F1 y alternativas (informedness, markedness, correlación de Matthews). *(citado de memoria, verificar)*
4. Varma, S. & Simon, R. (2006). *Bias in error estimation when using cross-validation for model selection*. **BMC Bioinformatics** 7: 91. Fundamento de la validación cruzada **anidada**, que veremos en el Módulo 07. *(citado de memoria, verificar)*
5. Arlot, S. & Celisse, A. (2010). *A survey of cross-validation procedures for model selection*. **Statistics Surveys** 4: 40–79. Revisión rigurosa del sesgo y la varianza de la validación cruzada según el esquema y $k$. *(citado de memoria, verificar)*
6. Hastie, T., Tibshirani, R. & Friedman, J. (2009). *The Elements of Statistical Learning*, 2.ª ed., Springer. **Cap. 7** (*Model Assessment and Selection*): error de generalización, validación cruzada y la forma correcta e incorrecta de aplicarla. *(citado de memoria, verificar el número de capítulo en tu edición)*

---

<div align="center">
  <p style="font-size: 0.9em; color: #64748b;">
    © 2026 <b>Universidad Santo Tomás — Seccional Tunja</b><br>
    <i>Especialización en Ciencia de Datos | Asignatura: Machine Learning</i>
  </p>
</div>
