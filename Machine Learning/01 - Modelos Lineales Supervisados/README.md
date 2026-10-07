# Módulo 01: Modelos Lineales Supervisados 📈🎯

<p align="center">
  <img src="https://img.shields.io/badge/Discipline-Machine%20Learning-059669?style=for-the-badge&logo=scikitlearn&logoColor=white" alt="Machine Learning"/>
  <img src="https://img.shields.io/badge/Topics-Regresi%C3%B3n%20Lineal%20%26%20Regresi%C3%B3n%20Log%C3%ADstica-0ea5e9?style=for-the-badge" alt="Topics"/>
  <img src="https://img.shields.io/badge/Course-Machine%20Learning-6366f1?style=for-the-badge" alt="Course"/>
  <img src="https://img.shields.io/badge/Institution-USTA%20Tunja-1e3a8a?style=for-the-badge" alt="USTA"/>
</p>

Bienvenido al **Módulo 01** de la asignatura **Machine Learning** de la *Especialización en Ciencia de Datos* de la **Universidad Santo Tomás — Seccional Tunja**.

---

## 🧭 ¿De qué trata este módulo?

Este módulo corresponde a las **secciones 1.7 y 1.8 del Capítulo 1** del syllabus: el **aprendizaje supervisado** y sus dos modelos lineales fundamentales, la **regresión lineal** (predecir un número) y la **regresión logística** (predecir una clase y su probabilidad). Si el [Módulo 00](../00%20-%20Introduccion%20al%20Machine%20Learning/README.md) respondió *¿qué es aprender?*, este responde *¿cómo se formula, se optimiza y se diagnostica un modelo supervisado?*

El enfoque es **más profundo** que el de los cursos previos: cada modelo se **formula matemáticamente**, se **deriva** su criterio de estimación, se **implementa desde cero en NumPy** (ecuación normal, descenso del gradiente, softmax) y se **verifica numéricamente contra `scikit-learn`** con `np.allclose` dentro del propio cuaderno. Además se estudia el **diagnóstico**: sesgo–varianza estimado por Monte Carlo, curvas de aprendizaje y de validación, análisis de residuos, VIF y regularización. Todo con código ejecutable, semilla fija y gráficos.

> 🔗 **Conexión con otros cursos:** este módulo **no repite** el manejo práctico de `scikit-learn` ya visto en [Data Science Programming — Módulo 07 (Regresión)](../../Data%20Science%20programming/07%20-%20Regression/README.md) y [Módulo 08 (Clasificación)](../../Data%20Science%20programming/08%20-%20Classification/README.md), ni en [Data Mining — Módulo 02](../../Data%20Mining/02%20-%20Clasificacion%20y%20Regresion/README.md); los enlaza y profundiza en lo que allá no se aborda: derivaciones, implementación propia y diagnóstico.

---

## 📚 Estructura Curricular del Módulo

### 🎓 1. Cuadernos Académicos Estándar:
1. [**00_Fundamentos_del_Aprendizaje_Supervisado.ipynb**](00_Fundamentos_del_Aprendizaje_Supervisado.ipynb): *Sección 1.7.* Formulación $(X, y, f, \mathcal{H}, L)$, riesgo verdadero vs. empírico, regresión y clasificación como casos del mismo marco, partición entrenamiento/validación/prueba, sobreajuste y subajuste, **descomposición sesgo–varianza derivada y estimada con una simulación Monte Carlo**, regularización como control de complejidad, curvas de aprendizaje y de validación, y el teorema *No Free Lunch*.
2. [**01_Regresion_Lineal.ipynb**](01_Regresion_Lineal.ipynb): *Sección 1.8.1.* Modelo y MCO, **derivación de la ecuación normal**, implementación desde cero con la ecuación normal y con **descenso del gradiente** (curva de convergencia, tasa de aprendizaje y número de condición), regresión múltiple con errores estándar, valores $p$ e intervalos calculados a mano, $R^2$ y $R^2$ ajustado, supuestos con diagnóstico gráfico de residuos, multicolinealidad con **VIF a mano**, y extensión polinomial con Ridge/Lasso.
3. [**02_Regresion_Logistica.ipynb**](02_Regresion_Logistica.ipynb): *Sección 1.8.2.* De la regresión lineal a la sigmoide, *log-odds* y *odds ratio*, **máxima verosimilitud, entropía cruzada y derivación del gradiente** (con verificación por diferencias finitas), implementación desde cero, frontera de decisión y umbral, regularización L1/L2 (parámetro $C$), extensión multiclase (*one-vs-rest* y *softmax* desde cero) e interpretación como *odds ratios* con intervalos *bootstrap*. Evaluación solo a nivel básico (*accuracy* y matriz de confusión): las métricas se estudian a fondo en el Módulo 03.

---

### 📝 2. Taller Práctico Evaluativo (*Hands-On*):
* [**../homeworks/01_Modelos_Lineales_Hands_On.ipynb**](../homeworks/01_Modelos_Lineales_Hands_On.ipynb): Taller evaluativo que integra la formulación supervisada, la regresión lineal y la regresión logística en ejercicios prácticos.

---

### 🧸 3. Ruta Didáctica: Para Dummies:
Ubicada en la subcarpeta [`Para Dummies/`](Para%20Dummies/):
1. [**00_Fundamentos_Supervisado_Dummies.ipynb**](Para%20Dummies/00_Fundamentos_Supervisado_Dummies.ipynb): Estudiar para el examen: aprender con respuestas, los tres paquetes de datos (ejercicios, simulacro y examen final) y la diferencia entre estudiar poco, entender y memorizar (¡con una panadería!).
2. [**01_Regresion_Lineal_Dummies.ipynb**](Para%20Dummies/01_Regresion_Lineal_Dummies.ipynb): Dibujar la mejor línea: predecir el precio de un apartamento en Tunja, leer el valor base y el aumento por metro cuadrado, y por qué no confiar en la línea lejos de los datos.
3. [**02_Regresion_Logistica_Dummies.ipynb**](Para%20Dummies/02_Regresion_Logistica_Dummies.ipynb): ¿Sí o no?: la curva en S, el punto de corte como nota mínima para aprobar, los «momios» (3 a 1) y qué hacer cuando hay más de dos opciones.

> 🛠️ **Práctica:** todos los cuadernos (estándar y Para Dummies) incluyen secciones «🛠️ Práctica» con una celda para escribir tu código y una solución desplegable.
> Resuélvelas antes de abrir la solución.

---

## 💾 Datos Utilizados

Este módulo **no requiere archivos externos**: usa datasets incluidos en `scikit-learn` (*Diabetes* con `scaled=False` para conservar las unidades originales, *Breast Cancer Wisconsin* e *Iris*) y **datos sintéticos generados en el propio código con semilla fija** (`make_classification`, `make_moons`, `make_circles` y procesos generadores propios como $y = \sin(2\pi x) + \varepsilon$). Por eso los cuadernos se ejecutan sin conexión a internet y de forma reproducible, tanto en local como en Google Colab.

---

## ⚙️ Requisitos

`numpy`, `pandas`, `matplotlib`, `seaborn`, `scikit-learn` y `scipy` (preinstalados en Google Colab). La librería `statsmodels` es **opcional** y solo se usa en el cuaderno 01 para verificar con una implementación independiente la tabla de coeficientes y el VIF; si no está instalada, el cuaderno lo informa y continúa sin ella.

---

<div align="center">
  <p style="font-size: 0.9em; color: #64748b;">
    © 2026 <b>Universidad Santo Tomás — Seccional Tunja</b><br>
    <i>Especialización en Ciencia de Datos | Asignatura: Machine Learning</i>
  </p>
</div>
