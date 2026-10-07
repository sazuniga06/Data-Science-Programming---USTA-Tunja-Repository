# Módulo 02: Árboles, Bosques y Redes Neuronales 🌳🌲🧠

<p align="center">
  <img src="https://img.shields.io/badge/Discipline-Machine%20Learning-059669?style=for-the-badge&logo=scikitlearn&logoColor=white" alt="Machine Learning"/>
  <img src="https://img.shields.io/badge/Topics-%C3%81rboles%2C%20Bosques%20%26%20Redes%20Neuronales-0ea5e9?style=for-the-badge" alt="Topics"/>
  <img src="https://img.shields.io/badge/Course-Machine%20Learning-6366f1?style=for-the-badge" alt="Course"/>
  <img src="https://img.shields.io/badge/Institution-USTA%20Tunja-1e3a8a?style=for-the-badge" alt="USTA"/>
</p>

Bienvenido al **Módulo 02** de la asignatura **Machine Learning** de la *Especialización en Ciencia de Datos* de la **Universidad Santo Tomás — Seccional Tunja**.

---

## 🧭 ¿De qué trata este módulo?

Este módulo corresponde a las **secciones 1.8.3, 1.8.4 y 1.8.5 del Capítulo 1** del syllabus: tres familias de modelos supervisados **no lineales**: los **árboles de decisión**, los **bosques aleatorios** (*random forests*) y las **redes neuronales**. Si el [Módulo 01](../01%20-%20Modelos%20Lineales%20Supervisados/README.md) trazaba **una frontera recta**, aquí las fronteras se vuelven **escalonadas** (árboles), **promediadas y estables** (bosques) o **suaves y arbitrariamente flexibles** (redes).

El enfoque es **más profundo** que el de los cursos previos: cada modelo se **formula matemáticamente**, se **implementa desde cero en NumPy** (un árbol CART recursivo, un bosque con *bootstrap* y error *out-of-bag*, y un perceptrón multicapa con retropropagación) y se **verifica contra `scikit-learn`** con `assert` dentro del propio cuaderno (estructura y predicciones idénticas, gradientes comprobados con diferencias finitas y comparados con un paso de `MLPClassifier`). Además se estudia el **diagnóstico**: curvas de validación, poda por complejidad de costo, varianza de un promedio de árboles correlacionados, importancia por impureza vs. por permutación, inicialización, tasa de aprendizaje y regularización. El cuaderno de redes culmina con la **misma red en PyTorch** (`nn.Module`, `autograd`, optimizador), el framework de *deep learning* del curso.

> 🔗 **Conexión con otros cursos:** este módulo **no repite** el manejo práctico de `scikit-learn` ya visto en [Data Science Programming — Módulo 09 (Decision Trees)](../../Data%20Science%20programming/09%20-%20Decision%20Trees/README.md), [Data Mining — Módulo 04 (Árboles y Bosques)](../../Data%20Mining/04%20-%20Arboles%20de%20Decision%20y%20Bosques%20Aleatorios/README.md) ni [Data Mining — Módulo 06 (SVM y Redes Neuronales)](../../Data%20Mining/06%20-%20Maquinas%20de%20Soporte%20Vectorial%20y%20Redes%20Neuronales/README.md); los enlaza y profundiza en lo que allá no se aborda: derivaciones, implementación propia, verificación numérica y diagnóstico. El *boosting* (GBM/XGBoost) se aborda allá y aquí solo se contrasta.

---

## 📚 Estructura Curricular del Módulo

### 🎓 1. Cuadernos Académicos Estándar:
1. [**00_Arboles_de_Decision.ipynb**](00_Arboles_de_Decision.ipynb): *Sección 1.8.3.* Partición recursiva, impureza (Gini, entropía, MSE) y ganancia de información, **algoritmo CART implementado desde cero** y verificado contra `DecisionTreeClassifier` (con análisis documentado de los **desempates**), fronteras ortogonales y sensibilidad a la rotación, **sobreajuste vs. profundidad** (curvas de validación), **poda por complejidad de costo** (`ccp_alpha`, alfa efectivo calculado a mano), árboles de regresión, **importancia MDI a mano y sus sesgos**, interpretabilidad (`export_text`, `plot_tree`) e **inestabilidad** de los árboles.
2. [**01_Random_Forests.ipynb**](01_Random_Forests.ipynb): *Sección 1.8.4.* *Bootstrap* (≈ 63.2 % de ejemplos únicos, **verificado numéricamente**), por qué promediar reduce la varianza ($\rho\sigma^2 + \frac{1-\rho}{B}\sigma^2$, con simulación y con árboles reales), submuestreo de variables como decorrelación, **bosque desde cero** con error *out-of-bag* comparado con `RandomForestClassifier`, **importancia MDI vs. permutación** (con el sesgo de MDI y el efecto de variables correlacionadas), curvas de hiperparámetros (`n_estimators`, `max_depth`, `max_features`, `min_samples_leaf`), comparación árbol / *bagging* / bosque y un vistazo al *boosting*.
3. [**02_Redes_Neuronales.ipynb**](02_Redes_Neuronales.ipynb): *Sección 1.8.5.* Neurona artificial y perceptrón (teorema de convergencia verificado y fallo en el XOR), activaciones y derivadas, perceptrón multicapa y **teorema de aproximación universal**, pérdidas, **retropropagación derivada paso a paso**, **MLP desde cero en NumPy** con verificación del gradiente por diferencias finitas, entrenamiento por mini-lotes sobre `make_moons` (contraste con la regresión logística del Módulo 01), verificación contra `MLPClassifier` (un paso de gradiente idéntico), **la misma red en PyTorch** (`nn.Module`, `autograd`, SGD/Adam), inicialización, tasa de aprendizaje, regularización (L2, *early stopping*, *dropout*) y cuándo usar **redes vs. árboles vs. modelos lineales** en datos tabulares.

---

### 📝 2. Taller Práctico Evaluativo (*Hands-On*):
* [**../homeworks/02_Arboles_Bosques_Redes_Hands_On.ipynb**](../homeworks/02_Arboles_Bosques_Redes_Hands_On.ipynb): Taller evaluativo que integra árboles, bosques aleatorios y redes neuronales en ejercicios prácticos.

---

### 🧸 3. Ruta Didáctica: Para Dummies:
Ubicada en la subcarpeta [`Para Dummies/`](Para%20Dummies/):
1. [**00_Arboles_Dummies.ipynb**](Para%20Dummies/00_Arboles_Dummies.ipynb): El juego de las 20 preguntas: un árbol que decide si llevar paraguas, cómo elige la pregunta que más «ordena» (los frijoles blancos y negros), por qué memorizar es peor que aprender y por qué un solo árbol es inestable.
2. [**01_Random_Forests_Dummies.ipynb**](Para%20Dummies/01_Random_Forests_Dummies.ipynb): Preguntarle a cien amigos: la sabiduría de la multitud (frijoles en un frasco), por qué cada árbol ve datos distintos, cómo el bosque se autoevalúa con lo que no vio y qué significa una variable «importante».
3. [**02_Redes_Neuronales_Dummies.ipynb**](Para%20Dummies/02_Redes_Neuronales_Dummies.ipynb): Un equipo de jurados que aprende: la neurona como suma ponderada de opiniones, los ayudantes en capas (el problema de la fiesta o XOR), aprender como afinar perillas según el error y una mini-red en NumPy que dibuja curvas donde la recta falla.

> 🛠️ **Práctica incluida:** todos los cuadernos (estándar y *Para Dummies*) incluyen secciones «🛠️ Práctica» con una celda para que escribas tu código y una **solución guiada desplegable**.
> Intenta resolver cada práctica antes de abrir la solución.

---

## 💾 Datos Utilizados

Este módulo **no requiere archivos externos**: usa datasets incluidos en `scikit-learn` (*Breast Cancer Wisconsin*, *Iris*, *Wine* y *Dígitos*) y **datos sintéticos generados en el propio código con semilla fija** (`make_moons`, `make_classification`, `make_friedman1` y procesos generadores propios como $y = \sin(2\pi x) + \varepsilon$). No se usa ningún `fetch_*` ni descarga de conjuntos de datos. Por eso los cuadernos se ejecutan sin conexión a internet y de forma reproducible, tanto en local como en Google Colab.

---

## ⚙️ Requisitos

`numpy`, `pandas`, `matplotlib`, `seaborn`, `scikit-learn` y `scipy` (preinstalados en Google Colab). El cuaderno [02_Redes_Neuronales.ipynb](02_Redes_Neuronales.ipynb) usa además **PyTorch** (`torch`), que **ya viene en Google Colab**; en un entorno local instálalo con `pip install torch` (la versión solo-CPU basta, p. ej. `pip install torch --index-url https://download.pytorch.org/whl/cpu`). La primera celda de ese cuaderno incluye la línea `# !pip install -q torch` comentada. Los demás cuadernos, incluidos los *Para Dummies*, **no** requieren PyTorch.

---

<div align="center">
  <p style="font-size: 0.9em; color: #64748b;">
    © 2026 <b>Universidad Santo Tomás — Seccional Tunja</b><br>
    <i>Especialización en Ciencia de Datos | Asignatura: Machine Learning</i>
  </p>
</div>
