# Módulo 00: Introducción al Machine Learning 🤖📈

<p align="center">
  <img src="https://img.shields.io/badge/Discipline-Machine%20Learning-059669?style=for-the-badge&logo=scikitlearn&logoColor=white" alt="Machine Learning"/>
  <img src="https://img.shields.io/badge/Topics-Paradigmas%2C%20Tipos%20de%20Problema%20%26%20Preprocesamiento-0ea5e9?style=for-the-badge" alt="Topics"/>
  <img src="https://img.shields.io/badge/Course-Machine%20Learning-6366f1?style=for-the-badge" alt="Course"/>
  <img src="https://img.shields.io/badge/Institution-USTA%20Tunja-1e3a8a?style=for-the-badge" alt="USTA"/>
</p>

Bienvenido al módulo inaugural de **Introducción al Machine Learning** de la asignatura **Machine Learning** de la *Especialización en Ciencia de Datos* de la **Universidad Santo Tomás — Seccional Tunja**.

---

## 🧭 ¿De qué trata este módulo?

El **Machine Learning** (aprendizaje automático) es la disciplina que construye programas capaces de **mejorar su desempeño en una tarea a partir de la experiencia** (datos), en lugar de depender de reglas escritas a mano. Este módulo corresponde al **Capítulo 1** del syllabus y responde cuatro preguntas fundacionales antes de entrenar el primer modelo del curso: **¿qué significa que una máquina aprende?** (definición de Mitchell, 1997), **¿de qué maneras puede aprender?** (paradigmas), **¿qué problemas resuelve?** (tipos de problema) y **¿por qué los datos deben prepararse con rigor?** (preprocesamiento y fuga de datos).

Cada cuaderno incluye teoría con formalización matemática, diagramas y **código ejecutable** con `numpy`, `pandas`, `matplotlib`, `seaborn` y `scikit-learn`, con semilla fija para reproducibilidad.

> 🛠️ **Ponlo en práctica:** todos los cuadernos (estándar y *Para Dummies*) incluyen secciones **«🛠️ Práctica»**: una celda de código para que escribas tu solución y, justo debajo, la **solución guiada desplegable** (`💡 Haz clic aquí para ver la solución guiada...`). Inténtalo primero y abre la solución solo para comparar.

> 🔗 **Conexión con otros cursos:** este módulo **no repite** [Introducción a la IA](../../Introduccion%20a%20la%20Inteligencia%20Artificial/00%20-%20Fundamentos%20y%20Origenes%20de%20la%20IA/README.md) ni [Data Mining — Módulo 00](../../Data%20Mining/00%20-%20Introduccion%20al%20Data%20Mining/README.md), sino que los enlaza y retoma sus ideas desde la perspectiva del aprendizaje.

---

## 📚 Estructura Curricular del Módulo

### 🎓 1. Cuadernos Académicos Estándar:
1. [**00_Introduccion_y_Panorama_del_ML.ipynb**](00_Introduccion_y_Panorama_del_ML.ipynb): *Secciones 1.1 a 1.3.* Resumen del capítulo y mapa del curso, definición de Mitchell $(T, P, E)$, ML vs. programación tradicional, ML vs. Data Mining vs. IA, historia breve, ciclo de vida de un proyecto y un primer ejemplo *end-to-end* (cargar → entrenar → evaluar).
2. [**01_Paradigmas_de_Aprendizaje.ipynb**](01_Paradigmas_de_Aprendizaje.ipynb): *Sección 1.4.* Aprendizaje supervisado (*k*-NN sobre Iris), no supervisado (K-Means sobre *blobs*) y por refuerzo (bandido multibrazo $\varepsilon$-greedy en NumPy puro), con mención del aprendizaje semi-supervisado y auto-supervisado y una tabla comparativa final.
3. [**02_Tipos_de_Problemas_en_ML.ipynb**](02_Tipos_de_Problemas_en_ML.ipynb): *Sección 1.5.* Clasificación (binaria y multiclase), regresión, clustering y reglas de asociación (soporte, confianza y *lift* calculados a mano con `pandas`), más un árbol de decisión para identificar el tipo de problema.
4. [**03_Importancia_del_Preprocesamiento.ipynb**](03_Importancia_del_Preprocesamiento.ipynb): *Sección 1.6.* Principio GIGO, demostración cuantitativa (mismo modelo con datos crudos vs. preparados), fuga de datos (*data leakage*), `Pipeline` + `ColumnTransformer` y checklist de preprocesamiento.

---

### 📝 2. Taller Práctico Evaluativo (*Hands-On*):
* [**../homeworks/00_Introduccion_ML_Hands_On.ipynb**](../homeworks/00_Introduccion_ML_Hands_On.ipynb): Taller evaluativo que integra la definición de aprendizaje, los paradigmas, los tipos de problema y el preprocesamiento en ejercicios prácticos.

---

### 🧸 3. Ruta Didáctica: Para Dummies:
Ubicada en la subcarpeta [`Para Dummies/`](Para%20Dummies/):
1. [**00_Introduccion_ML_Dummies.ipynb**](Para%20Dummies/00_Introduccion_ML_Dummies.ipynb): ¿Qué es el Machine Learning? La receta de cocina vs. aprender probando, la definición de Mitchell explicada con el tejo y tu primer modelo (¿papa criolla o pastusa?).
2. [**01_Paradigmas_Dummies.ipynb**](Para%20Dummies/01_Paradigmas_Dummies.ipynb): Las 3 formas de aprender de una máquina: con profesor, sin profesor y por premios (¡con puestos de empanadas en Tunja!).
3. [**02_Tipos_de_Problemas_Dummies.ipynb**](Para%20Dummies/02_Tipos_de_Problemas_Dummies.ipynb): Los 4 oficios de la plaza de mercado: clasificar, predecir un número, agrupar y encontrar parejas de productos.
4. [**03_Preprocesamiento_Dummies.ipynb**](Para%20Dummies/03_Preprocesamiento_Dummies.ipynb): Lavar las papas antes de cocinar: datos vacíos, escalas distintas, palabras a números y la trampa de ver el examen antes de presentarlo.

---

## 💾 Datos Utilizados

Este módulo **no requiere archivos externos**: todos los ejemplos usan datasets incluidos en `scikit-learn` (*Breast Cancer Wisconsin*, *Iris*, *Wine*, *Diabetes*) o **datos sintéticos generados en el propio código con semilla fija** (clientes de crédito, canastas de supermercado, segmentación RFM, ruido puro para el experimento de fuga de datos). Por eso los cuadernos se ejecutan sin conexión a internet y de forma reproducible, tanto en local como en Google Colab.

---

## ⚙️ Requisitos

`numpy`, `pandas`, `matplotlib`, `seaborn` y `scikit-learn` (preinstalados en Google Colab). La librería `mlxtend` es **opcional** y solo se usa para una verificación en el cuaderno 02; si no está instalada, el cuaderno continúa sin ella.

---

<div align="center">
  <p style="font-size: 0.9em; color: #64748b;">
    © 2026 <b>Universidad Santo Tomás — Seccional Tunja</b><br>
    <i>Especialización en Ciencia de Datos | Asignatura: Machine Learning</i>
  </p>
</div>
