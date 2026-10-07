# Módulo 07: Selección de Modelos y Optimización de Hiperparámetros 🧪🎯

<p align="center">
  <img src="https://img.shields.io/badge/Discipline-Machine%20Learning-059669?style=for-the-badge&logo=scikitlearn&logoColor=white" alt="Machine Learning"/>
  <img src="https://img.shields.io/badge/Topics-Selecci%C3%B3n%20de%20Modelos%20%26%20Optimizaci%C3%B3n-0ea5e9?style=for-the-badge" alt="Topics"/>
  <img src="https://img.shields.io/badge/Course-Machine%20Learning-6366f1?style=for-the-badge" alt="Course"/>
  <img src="https://img.shields.io/badge/Institution-USTA%20Tunja-1e3a8a?style=for-the-badge" alt="USTA"/>
</p>

Bienvenido al **Módulo 07** de la asignatura **Machine Learning** de la *Especialización en Ciencia de Datos* de la **Universidad Santo Tomás — Seccional Tunja**.

---

## 🧭 ¿De qué trata este módulo?

Este módulo **cierra el Capítulo 2** del syllabus y corresponde a las secciones **2.10 (*Model Evaluation and Selection*)**, **2.11 (*Metrics for model evaluation*)**, **2.12 (*Model selection techniques: Cross-Validation, GridSearch, Bayesian Optimization*, con 2.12.1–2.12.3)** y **2.13 (*Hyperparameter Tuning Strategies: Random Search, GridSearch, Bayesian Optimization*, con 2.13.1–2.13.3)**. Tras el [Módulo 06](../06%20-%20Aprendizaje%20por%20Refuerzo/README.md) (el agente que aprende de recompensas), volvemos a la pregunta que atraviesa todo el curso: **¿cuánto podemos creerle a un número y cómo elegimos con rigor entre modelos y configuraciones?**

> 📌 **Una nota sobre el índice del libro:** el título oficial del Capítulo 2 en el índice original es *Outline of the Scientific Research Process*, pero su contenido real es **aprendizaje no supervisado, reducción de dimensionalidad, aprendizaje por refuerzo y selección de modelos**. El curso sigue el contenido real: los Módulos [04](../04%20-%20Clustering%20No%20Supervisado/README.md), [05](../05%20-%20Reduccion%20de%20Dimensionalidad/README.md) y [06](../06%20-%20Aprendizaje%20por%20Refuerzo/README.md) cubren lo no supervisado y el refuerzo, y este Módulo 07 cierra el capítulo con la **evaluación y selección de modelos**.

Este módulo **no repite** lo del [Módulo 03](../03%20-%20Metricas%20y%20Ajuste%20de%20Hiperparametros/README.md) (matriz de confusión, ROC-AUC y PR-AUC, métricas de regresión, *k*-fold, *stratified*, *leave-one-out*, fuga de datos, sesgo de selección, `GridSearchCV` desde cero y `cv_results_`): lo **profundiza y enlaza**. El enfoque sigue siendo **formular, implementar desde cero y verificar con `assert`** dentro del propio cuaderno: los **intervalos *bootstrap*** y de **Wilson** (verificado contra `scipy.stats.binomtest`); la ***t* pareada**, la **corrección de Nadeau y Bengio**, **McNemar** (asintótico y exacto) y la **5×2cv** (*t* de Dietterich y *F* combinada de Alpaydin), con una **simulación del error tipo I** que demuestra que la *t* ingenua es demasiado optimista; el **log loss, el Brier y el ECE** (contra `scikit-learn`) y la **calibración** (Platt e isotónica); `RepeatedKFold`, `ShuffleSplit` y `TimeSeriesSplit` (con `gap` y ventana deslizante) **idénticos** a los de `scikit-learn`; la **validación cruzada anidada** idéntica a `cross_val_score(GridSearchCV(...))` y su **sesgo optimista medido** contra un error verdadero conocido; **Random Search** idéntico a `RandomizedSearchCV` (mismas configuraciones y puntajes); y un **proceso gaussiano** (Cholesky) idéntico a `GaussianProcessRegressor` con la **mejora esperada** verificada contra Monte Carlo e integración numérica. Los experimentos **reportan con honestidad** los casos en que la ventaja de un método es **pequeña** (Random Search frente a rejilla en 2 dimensiones; optimización bayesiana frente a Random Search en un SVM).

> 🔗 **Conexión con otros cursos:** el uso básico de `GridSearchCV` con árboles y *k*-NN está en [Data Science Programming — Módulo 09 (Decision Trees)](../../Data%20Science%20programming/09%20-%20Decision%20Trees/README.md) y [Módulo 08 (Classification)](../../Data%20Science%20programming/08%20-%20Classification/README.md); las métricas de *clustering* en el [Módulo 04, cuaderno 04](../04%20-%20Clustering%20No%20Supervisado/04_Metricas_de_Clustering.ipynb); y el mapa de todo el capítulo en la [Introducción al Capítulo 2](../04%20-%20Clustering%20No%20Supervisado/00_Introduccion_Cap2_y_No_Supervisado.ipynb).

> 🛠️ **Ponlo en práctica:** todos los cuadernos (estándar y *Para Dummies*) incluyen secciones **«🛠️ Práctica»**: una celda de código para que escribas tu solución y, justo debajo, la **solución guiada desplegable** (`💡 Haz clic aquí para ver la solución guiada...`). Inténtalo primero y abre la solución solo para comparar.

---

## 📚 Estructura Curricular del Módulo

### 🎓 1. Cuadernos Académicos Estándar:
1. [**00_Evaluacion_y_Seleccion_de_Modelos.ipynb**](00_Evaluacion_y_Seleccion_de_Modelos.ipynb): *Secciones 2.10 y 2.11.* El **protocolo completo** (desarrollo / **prueba sellada** que solo se evalúa una vez, con **líneas base**); **intervalos de confianza por *bootstrap*** desde cero frente a **Wilson** y **Wald** (con la **cobertura real** simulada y la regla $1/\sqrt n$); **comparación de modelos con rigor**: *t* pareada, **corrección de Nadeau y Bengio (2003)**, **McNemar** y **5×2cv (Dietterich, 1998; variante *F* de Alpaydin, 1999)**, todas desde cero y **verificadas**, y una **simulación bajo $H_0$** del error tipo I (la *t* ingenua con 30 remuestras declara una diferencia inexistente ≈ 1 de cada 3 veces); **métricas probabilísticas** (log loss, Brier, ECE, diagrama de confiabilidad) y **calibración** con Platt e isotónica (`CalibratedClassifierCV`); **curvas de aprendizaje** como diagnóstico de sesgo y varianza (desde cero == `learning_curve`); una **tabla guía de métricas por tipo de problema** (clasificación, regresión, *clustering*, *ranking* con NDCG@k desde cero, refuerzo) y un **árbol de decisión para elegir la métrica según el costo del negocio**.
2. [**01_Validacion_Cruzada_Avanzada.ipynb**](01_Validacion_Cruzada_Avanzada.ipynb): *Sección 2.12.1.* ***k*-fold repetido** (desde cero == `RepeatedKFold`) y la varianza de la estimación por CV; **validación por grupos** (`GroupKFold`; demostración de la fuga con varias filas por paciente: ≈ 88 % frente a ≈ 58 %); **series de tiempo** (*walk-forward* desde cero == `TimeSeriesSplit` con `gap` y ventana deslizante; por qué barajar es trampa; purga y embargo); **validación cruzada anidada desde cero** == `cross_val_score(GridSearchCV(...))` con las mismas particiones y la **demostración cuantitativa del sesgo optimista** del mejor puntaje de CV frente al anidado y a un error verdadero conocido; ***bootstrap* .632 / .632+** (implementado, con el caso de falla del .632); **CV Monte Carlo** (`ShuffleSplit` desde cero); **regla de una desviación estándar**; y **CV con datos desbalanceados** (estratificar y por qué remuestrear *antes* de dividir produce una AP falsa de ≈ 1.0).
3. [**02_Random_Search_y_GridSearch.ipynb**](02_Random_Search_y_GridSearch.ipynb): *Secciones 2.12.2, 2.13.1 y 2.13.2.* Recapitulación de la rejilla (tabla, enlazada al módulo 03) y **la comparación**: **dimensión efectiva** y el argumento de **Bergstra y Bengio (2012)** con una **demostración numérica propia**; la cuenta $1-(1-p)^N$ (59 muestras para el mejor 5 % con 95 % de confianza); **distribuciones de muestreo** (`uniform`, `loguniform`, `randint`); **Random Search desde cero == `RandomizedSearchCV`** (mismas configuraciones y puntajes; qué parte no puede ser exacta); **curvas «mejor puntaje vs. presupuesto»** promediadas sobre miles de repeticiones (SVM en 2 dimensiones y árbol en 4) con la conclusión **honesta** de cuándo gana cada uno; ***coarse-to-fine***; **reducción sucesiva** (*successive halving* desde cero y `HalvingRandomSearchCV`, experimental, dentro de `try/except`); `n_jobs`, costos y **reproducibilidad** (semillas de búsqueda, estimador y divisor).
4. [**03_Optimizacion_Bayesiana.ipynb**](03_Optimizacion_Bayesiana.ipynb): *Secciones 2.12.3 y 2.13.3.* El problema de la **caja negra costosa**; **proceso gaussiano desde cero** (núcleo RBF, posterior con **Cholesky**, verosimilitud marginal) **verificado contra `GaussianProcessRegressor`** con el núcleo fijo (`optimizer=None`: media, desviación, covarianza y log-verosimilitud); **funciones de adquisición** PI, **EI** (fórmula cerrada derivada y verificada contra Monte Carlo y `scipy.integrate.quad`) y UCB/LCB; el compromiso exploración–explotación ($\xi$, $\kappa$); **demo 1D paso a paso** (media, banda de incertidumbre, adquisición, siguiente punto); un **bucle de BO propio** aplicado a `C` y `gamma` de un SVM y su **comparación honesta con Random Search** sobre varias semillas; **TPE y Optuna** (celda **opcional**: se ejecuta solo si `optuna` está instalado); **limitaciones** medidas (costo cúbico, ventaja que se encoge con la dimensión, ruido) y una guía de **cuándo elegir rejilla, aleatoria o bayesiana**.

---

### 📝 2. Taller Práctico Evaluativo (*Hands-On*):
* [**../homeworks/07_Seleccion_Modelos_Optimizacion_Hands_On.ipynb**](../homeworks/07_Seleccion_Modelos_Optimizacion_Hands_On.ipynb): Taller evaluativo que integra el protocolo de evaluación, la comparación estadística de modelos, la validación anidada y la búsqueda de hiperparámetros en ejercicios prácticos *(el cuaderno se publica aparte)*.

---

### 🧸 3. Ruta Didáctica: Para Dummies:
Ubicada en la subcarpeta [`Para Dummies/`](Para%20Dummies/):
1. [**00_Evaluacion_Seleccion_Dummies.ipynb**](Para%20Dummies/00_Evaluacion_Seleccion_Dummies.ipynb): **El examen sorpresa, la moneda y el pronosticador honesto**: el estudiante **memorión** (100 % en la práctica, ≈ 50 % en el examen nuevo), por qué 91 % frente a 90 % en 100 preguntas es **suerte** (el «re-sorteo» como intervalo de confianza), el pronosticador **sabio** frente al **exagerado** (calibración) y la **alarma de incendios** (la medida depende de qué error duele más).
2. [**01_Validacion_Cruzada_Avanzada_Dummies.ipynb**](Para%20Dummies/01_Validacion_Cruzada_Avanzada_Dummies.ipynb): **Los exámenes de práctica justos**: simulacros repetidos, las **fotos del mismo paciente** (mezclar da > 90 %, separar por paciente ≈ 50 %), el calendario (**no se predice el pasado con el futuro**) y el **concurso de talentos** donde el ganador de 50 iguales sale inflado (validación anidada).
3. [**02_Random_Grid_Search_Dummies.ipynb**](Para%20Dummies/02_Random_Grid_Search_Dummies.ipynb): **Buscar las llaves**: el radio con dos perillas (cuadrícula 3×3 frente a 9 intentos al azar), la **escala mágica** (logarítmica), el **mapa del tesoro** con zoom (que ayuda solo si el barrido amplio da pistas) y el **casting de talentos** (reducción sucesiva).
4. [**03_Optimizacion_Bayesiana_Dummies.ipynb**](Para%20Dummies/03_Optimizacion_Bayesiana_Dummies.ipynb): **El cazador de cumbres en la niebla**: el **mapa mental** (estimación + duda) paso a paso, 300 cordilleras contra el azar, el dilema del **restaurante** (explorar o explotar) y **cuándo vale la pena** (cuando cada excursión es cara).

---

## 💾 Datos Utilizados

Todos los datos son de `scikit-learn` o **sintéticos con semilla fija**; **no hay descargas** y no se necesita ninguna carpeta `data/`.

| Conjunto | Origen | Dónde se usa |
|---|---|---|
| ***Breast Cancer Wisconsin*** (569 × 30) | `sklearn.datasets.load_breast_cancer` | Cuadernos 00 (protocolo, pruebas de comparación), 01 (*k*-fold repetido, anidada, .632, 1-SE), 02 (SVM y bosque) y 03 (SVM) |
| **Problemas sintéticos de clasificación** | `make_classification` con `random_state` fijo | Cuaderno 00 (calibración, curvas de aprendizaje, costo), 01 (desbalanceo, .632+) y 02 (reducción sucesiva, árbol de 4 hiperparámetros) |
| **Simulaciones propias** (pacientes con varias filas, serie de tiempo con tendencia y ruido AR(1), «dos sensores» con el mismo error, funciones de respuesta) | `numpy.random.default_rng(semilla)` | Cuadernos 00, 01, 02 y 03; los cuatro *Dummies* |
| ***Iris*** | `sklearn.datasets.load_iris` | Cuaderno 02 (solo la comparación del paralelismo) |

## ⚙️ Requisitos

`numpy`, `pandas`, `matplotlib`, `seaborn`, `scipy` y `scikit-learn` (todos preinstalados en Google Colab). **Opcional:** `optuna` (solo la sección 6 del cuaderno 03: la celda comprueba con `try/except` si está instalada, ejecuta un estudio corto si lo está y, si no, imprime un aviso; la primera celda trae la línea `# !pip install -q optuna` para quitarle el comentario). Los cuatro **Dummies** usan solo `NumPy` y `matplotlib` (el 03 usa además el `GaussianProcessRegressor` de `scikit-learn` como «caja»). El código evita las APIs frágiles entre versiones y las experimentales sin `try/except` (`HalvingRandomSearchCV` se importa dentro de un `try/except`); se ejecutó de verdad, de arriba abajo y sin errores, con las **versiones más recientes** (NumPy 2.5, SciPy 1.18, scikit-learn 1.9) y con versiones **tipo Colab** (NumPy 2.0, SciPy 1.14, scikit-learn 1.6), y la rama de `optuna` instalada y no instalada. Tiempos aproximados en un equipo de escritorio con CPU (varían con el número de núcleos): cuaderno 00 ≈ 25–30 s, 01 ≈ 40–50 s, 02 ≈ 40 s y 03 ≈ 30 s (≈ 40 s con `optuna` instalado; en un equipo de 8 núcleos); los Dummies tardan 3–5 s, salvo el 03 (≈ 18 s).

---

## 📚 Lecturas Complementarias

*Esta sección cierra el Capítulo 2: reúne lecturas sobre evaluación y selección de modelos, optimización de hiperparámetros, aprendizaje no supervisado y refuerzo. Todas están citadas de memoria salvo las marcadas como verificadas: comprueba los datos bibliográficos antes de citarlas formalmente.*

1. Géron, A. (2025). *Hands-On Machine Learning with Scikit-Learn and PyTorch*, O'Reilly. **Cap. 1** (*Testing and Validating*, *Hyperparameter Tuning and Model Selection*, *Data Mismatch*), **Cap. 2** (*Better Evaluation Using Cross-Validation*, *Fine-Tune Your Model*: *Grid Search* y *Randomized Search*), **Cap. 9** (*Hyperparameter Tuning Guidelines*) y **Cap. 10** (*Fine-Tuning Neural Network Hyperparameters with Optuna*). Disponible en `Machine Learning/Libros/` (títulos de capítulo y sección verificados contra el índice del PDF).
2. Raschka, S. (2015). *Python Machine Learning*, Packt. **Cap. 6** (*Learning Best Practices for Model Evaluation and Hyperparameter Tuning*): curvas de aprendizaje, *grid search*, **validación cruzada anidada** y métricas; cita a Varma & Simon (2006), *Bias in error estimation when using cross-validation for model selection*, **BMC Bioinformatics** 7:91. Disponible en `Machine Learning/Libros/` (verificado contra el PDF). Además, Raschka, S. (2018), *Model evaluation, model selection, and algorithm selection in machine learning*, arXiv:1811.12808 *(citado de memoria, verificar)*.
3. Bergstra, J. & Bengio, Y. (2012). *Random search for hyper-parameter optimization*. **Journal of Machine Learning Research** 13: 281–305. *(citado de memoria, verificar)*
4. Snoek, J., Larochelle, H. & Adams, R. P. (2012). *Practical Bayesian optimization of machine learning algorithms*. **NeurIPS 25**; y Shahriari, B., Swersky, K., Wang, Z., Adams, R. P. & de Freitas, N. (2016). *Taking the human out of the loop: a review of Bayesian optimization*. **Proceedings of the IEEE** 104(1): 148–175. *(citados de memoria, verificar)*
5. Dietterich, T. G. (1998). *Approximate statistical tests for comparing supervised classification learning algorithms*. **Neural Computation** 10(7): 1895–1923; Alpaydin, E. (1999). *Combined 5×2 cv F test for comparing supervised classification learning algorithms*. **Neural Computation** 11(8): 1885–1892; y Nadeau, C. & Bengio, Y. (2003). *Inference for the generalization error*. **Machine Learning** 52: 239–281. *(citados de memoria, verificar)*
6. Cawley, G. C. & Talbot, N. L. C. (2010). *On over-fitting in model selection and subsequent selection bias in performance evaluation*. **JMLR** 11: 2079–2107; y Bates, S., Hastie, T. & Tibshirani, R. (2023). *Cross-validation: what does it estimate and how well does it do it?* **Journal of the American Statistical Association**. *(citados de memoria, verificar)*
7. Akiba, T., Sano, S., Yanase, T., Ohta, T. & Koyama, M. (2019). *Optuna: a next-generation hyperparameter optimization framework*. **KDD '19**; y Bergstra, J., Bardenet, R., Bengio, Y. & Kégl, B. (2011). *Algorithms for hyper-parameter optimization*. **NeurIPS 24** (TPE). *(citados de memoria, verificar)*
8. Hastie, T., Tibshirani, R. & Friedman, J. (2009). *The Elements of Statistical Learning*, 2.ª ed., Springer: **Cap. 7** (*Model Assessment and Selection*) y **Cap. 14** (*Unsupervised Learning*); y Sutton, R. S. & Barto, A. G. (2018). *Reinforcement Learning: An Introduction*, 2.ª ed., MIT Press (disponible en línea de forma gratuita), que cierra el capítulo con el aprendizaje por refuerzo del [Módulo 06](../06%20-%20Aprendizaje%20por%20Refuerzo/README.md). *(citados de memoria, verificar)*

---

<div align="center">
  <p style="font-size: 0.9em; color: #64748b;">
    © 2026 <b>Universidad Santo Tomás — Seccional Tunja</b><br>
    <i>Especialización en Ciencia de Datos | Asignatura: Machine Learning</i>
  </p>
</div>
