# Módulo 04: Clustering No Supervisado 🧩🔍

<p align="center">
  <img src="https://img.shields.io/badge/Discipline-Machine%20Learning-059669?style=for-the-badge&logo=scikitlearn&logoColor=white" alt="Machine Learning"/>
  <img src="https://img.shields.io/badge/Topics-Clustering%20No%20Supervisado-0ea5e9?style=for-the-badge" alt="Topics"/>
  <img src="https://img.shields.io/badge/Course-Machine%20Learning-6366f1?style=for-the-badge" alt="Course"/>
  <img src="https://img.shields.io/badge/Institution-USTA%20Tunja-1e3a8a?style=for-the-badge" alt="USTA"/>
</p>

Bienvenido al **Módulo 04** de la asignatura **Machine Learning** de la *Especialización en Ciencia de Datos* de la **Universidad Santo Tomás — Seccional Tunja**.

---

## 🧭 ¿De qué trata este módulo?

Este módulo **abre el Capítulo 2** del syllabus y corresponde a las **secciones 2.1 a 2.5**: *Introducción*, *Resumen*, *Unsupervised Learning*, los tres algoritmos de agrupamiento (**2.4.1 *K-Means***, **2.4.2 *Hierarchical Clustering***, **2.4.3 *DBSCAN***) y las métricas de validación (**2.5.1 *Silhouette Score***, **2.5.2 *Calinski–Harabasz Index***, **2.5.3 *DBCV***). Tras el Capítulo 1 (aprendizaje supervisado y evaluación, [Módulos 00 a 03](../03%20-%20Metricas%20y%20Ajuste%20de%20Hiperparametros/README.md)), la pregunta cambia: ya no hay una respuesta correcta que predecir, sino **estructura que descubrir**, y por eso **validar es el gran problema**.

> 📌 **Una nota sobre el índice del libro:** el título oficial del Capítulo 2 en el índice original es *Outline of the Scientific Research Process*, pero su contenido real es **aprendizaje no supervisado, reducción de dimensionalidad, aprendizaje por refuerzo y selección de modelos**. El curso sigue el contenido real: el Módulo 04 cubre el agrupamiento y su validación, y los Módulos 05 a 07 (cuyos nombres definitivos pueden ajustarse) desarrollan el resto del capítulo.

El enfoque es **más profundo** que el de los cursos previos: cada algoritmo se **formula matemáticamente**, se **implementa desde cero** y se **verifica contra `scikit-learn`, `SciPy` o `hdbscan`** con `assert` dentro del propio cuaderno (algoritmo de Lloyd y *k-means++*, el aglomerativo con enlaces *single/complete/average/Ward* y la correlación cofenética, DBSCAN con la misma partición que `sklearn.cluster.DBSCAN`, silueta, Calinski–Harabasz, ARI, NMI y **DBCV**). Además se estudian las **trampas**: la inicialización en mínimos locales, los supuestos geométricos de *K-Means*, el encadenamiento del enlace *single*, la ambigüedad de los puntos borde, la maldición de la dimensionalidad y, sobre todo, el **sesgo de silueta y Calinski–Harabasz hacia grupos convexos**, que penalizan injustamente a DBSCAN.

> 🔗 **Conexión con otros cursos:** este módulo **no repite** el manejo práctico del *clustering* con `scikit-learn` ya visto en [Data Science Programming — Módulo 10 (Clustering)](../../Data%20Science%20programming/10%20-%20Clustering/README.md) ni en [Data Mining — Módulo 03 (Clustering y Minería de Reglas de Asociación)](../../Data%20Mining/03%20-%20Clustering%20y%20Mineria%20Reglas%20de%20Asociacion/README.md); los enlaza y profundiza en lo que allá no se aborda: formulación matemática, implementación propia verificada, propiedades de convergencia, comparaciones controladas y la validación basada en densidad (DBCV). También retoma ideas anteriores del curso: el [Módulo 00](../00%20-%20Introduccion%20al%20Machine%20Learning/01_Paradigmas_de_Aprendizaje.ipynb) presentó el paradigma no supervisado, y el [Módulo 03](../03%20-%20Metricas%20y%20Ajuste%20de%20Hiperparametros/00_Metricas_de_Clasificacion.ipynb) las nociones de precisión, recall y evaluación.

> 🛠️ **Ponlo en práctica:** todos los cuadernos (estándar y *Para Dummies*) incluyen secciones **«🛠️ Práctica»**: una celda de código para que escribas tu solución y, justo debajo, la **solución guiada desplegable** (`💡 Haz clic aquí para ver la solución guiada...`). Inténtalo primero y abre la solución solo para comparar.

---

## 📚 Estructura Curricular del Módulo

### 🎓 1. Cuadernos Académicos Estándar:
1. [**00_Introduccion_Cap2_y_No_Supervisado.ipynb**](00_Introduccion_Cap2_y_No_Supervisado.ipynb): *Secciones 2.1, 2.2 y 2.3.* El Capítulo 2 en contexto y el **mapa de los Módulos 04 a 07**; **formalización** del aprendizaje no supervisado y sus cuatro tareas (*clustering*, reducción de dimensionalidad, estimación de densidad y detección de anomalías); por qué es **difícil validar** (un algoritmo siempre «encuentra» grupos, incluso en ruido uniforme, y la inercia siempre decrece con $K$); **escalado** (*Wine* con ARI antes y después de estandarizar) y **métrica de distancia** (Euclídea, Manhattan, coseno; la identidad $\|\mathbf{u}-\mathbf{v}\|^2=2(1-\cos\theta)$); **maldición de la dimensionalidad** (concentración de distancias, volumen de la bola inscrita y degradación del agrupamiento al añadir variables de ruido); y la **taxonomía** de familias (particional, jerárquica, densidad y mezclas) con tabla comparativa y diagramas.
2. [**01_KMeans.ipynb**](01_KMeans.ipynb): *Sección 2.4.1.* Función objetivo (**inercia/WCSS**) y por qué la media es el centroide óptimo; **algoritmo de Lloyd desde cero** verificado contra `KMeans` (mismas etiquetas, centroides e inercia con centros iniciales dados); **monotonía de la inercia** y convergencia a un mínimo local; **sensibilidad a la inicialización** y ***k-means++* desde cero** (con verificación estadística de su regla de muestreo); **método del codo**; limitaciones (lunas, grupos alargados, varianzas distintas, *outliers*) con la mezcla gaussiana como alternativa y *K-Means* como su límite duro; ***Mini-Batch K-Means*** (regla de Sculley) y mención de *K-Medoids*.
3. [**02_Clustering_Jerarquico.ipynb**](02_Clustering_Jerarquico.ipynb): *Sección 2.4.2.* Aglomerativo frente a divisivo; **criterios de enlace** (*single*, *complete*, *average*, *Ward*) con la **fórmula de Lance–Williams**; **aglomerativo ingenuo $O(n^3)$ desde cero** idéntico a `scipy.cluster.hierarchy.linkage` (pares, alturas y tamaños); **dendrograma**, corte por altura o por $K$ (`fcluster`) y heurística de la mayor brecha; **correlación cofenética desde cero**; **encadenamiento** (*chaining*) del enlace *single* y su equivalencia con el **árbol generador mínimo**; complejidad, memoria cuadrática e inversiones de *centroid* y *median*.
4. [**03_DBSCAN.ipynb**](03_DBSCAN.ipynb): *Sección 2.4.3.* Definiciones formales (vecindad $\varepsilon$, núcleo, borde, ruido, alcanzabilidad y conectividad por densidad); **DBSCAN desde cero idéntico a `sklearn.cluster.DBSCAN`** y **documentación del único caso ambiguo** (punto borde alcanzable desde dos grupos); elección de $\varepsilon$ con el **gráfico de $k$-distancias** (equivalencia núcleo $\iff$ $k$-distancia $\le\varepsilon$); sensibilidad a $(\varepsilon,\texttt{min\_samples})$; formas arbitrarias frente a *K-Means* y *Ward*; detección de *outliers*; limitaciones (**densidades variables** y **alta dimensión**) y las extensiones **OPTICS** y **HDBSCAN**.
5. [**04_Metricas_de_Clustering.ipynb**](04_Metricas_de_Clustering.ipynb): *Sección 2.5.* Validación interna, externa y relativa; **silueta** (por muestra y global) y **Calinski–Harabasz** (con $T=B+W$) **desde cero**, verificadas contra `sklearn.metrics`; elección de $k$ con inercia, silueta, CH y Davies–Bouldin (el caso de *Iris*); el **sesgo hacia grupos convexos** (silueta y CH prefieren la partición equivocada de *K-Means* en lunas y círculos) y la **trampa de la etiqueta `-1`**; **DBCV desde cero** (distancia de alcanzabilidad mutua, MST, dispersión y separación de densidad) **verificado contra `hdbscan.validity.validity_index`** y usado para elegir $\varepsilon$; y las métricas **externas ARI y NMI desde cero**, con la corrección por azar.

---

### 📝 2. Taller Práctico Evaluativo (*Hands-On*):
* [**../homeworks/04_Clustering_Hands_On.ipynb**](../homeworks/04_Clustering_Hands_On.ipynb): Taller evaluativo que integra *K-Means*, jerárquico, DBSCAN y las métricas de validación en ejercicios prácticos.

---

### 🧸 3. Ruta Didáctica: Para Dummies:
Ubicada en la subcarpeta [`Para Dummies/`](Para%20Dummies/):
1. [**00_Introduccion_No_Supervisado_Dummies.ipynb**](Para%20Dummies/00_Introduccion_No_Supervisado_Dummies.ipynb): Aprender **sin profesor** (la bolsa de frutas sin etiquetas), las cuatro cosas que se pueden hacer, por qué un programa **siempre encuentra grupos** (incluso en el azar), la regla y la báscula (**escala**), tres formas de medir «cerca» (pájaro, taxi y brújula) y el edificio enorme (**muchas columnas**).
2. [**01_KMeans_Dummies.ipynb**](Para%20Dummies/01_KMeans_Dummies.ipynb): **Abrir tiendas de arepas en un pueblo**: asignar cada casa a la tienda más cercana y mover la tienda al centro de sus clientes; la suerte del inicio, el **codo** («¿cuántas tiendas valen la pena?») y cuándo falla (formas raras, tamaños distintos y clientes muy lejanos).
3. [**02_Jerarquico_Dummies.ipynb**](Para%20Dummies/02_Jerarquico_Dummies.ipynb): El **árbol de los parecidos** con ciudades de Colombia: juntar amigos en grupos cada vez más grandes, leer y cortar el dendrograma, cuatro formas de medir la distancia entre grupos y la **cadena de amigos de amigos**.
4. [**03_DBSCAN_Dummies.ipynb**](Para%20Dummies/03_DBSCAN_Dummies.ipynb): La **plaza llena de gente**: radio y mínimo de vecinos, centros de la multitud, orillas y solitarios; formas raras, los botones mal girados, los solitarios como detector de rarezas y por qué un solo radio no sirve para multitudes de densidades distintas.
5. [**04_Metricas_Clustering_Dummies.ipynb**](Para%20Dummies/04_Metricas_Clustering_Dummies.ipynb): **Calificar un agrupamiento sin hoja de respuestas**: la silueta («¿te sientes en casa en tu grupo?»), la nota de grupos compactos y lejanos, la trampa de las formas raras y la nota de acuerdo cuando sí hay respuestas.

---

## 💾 Datos Utilizados

Este módulo **no requiere archivos externos**: usa datasets incluidos en `scikit-learn` (*Wine*, *Iris* y *Dígitos*) y **datos sintéticos generados en el propio código con semilla fija** (`make_blobs`, `make_moons`, `make_circles`, ruido uniforme y gaussiano, semirrectas para contrastar distancias, y puntos «puente» para el encadenamiento). El único «dato real» escrito a mano es una pequeña tabla de coordenadas aproximadas de ciudades colombianas (latitud y longitud) en el cuaderno Dummies del jerárquico. No se usa ningún `fetch_*` ni descarga de conjuntos de datos, por lo que los cuadernos se ejecutan sin conexión a internet y de forma reproducible, tanto en local como en Google Colab.

---

## ⚙️ Requisitos

`numpy`, `pandas`, `matplotlib`, `seaborn`, `scikit-learn` y `scipy` (preinstalados en Google Colab). **Opcional:** [`hdbscan`](https://hdbscan.readthedocs.io/) (`pip install hdbscan`), usado **únicamente** en el cuaderno `04_Metricas_de_Clustering` para comparar en vivo nuestra implementación de DBCV con la de referencia; si no está instalado (o no compila en tu entorno), el cuaderno lo detecta con un `try/except`, lo avisa explícitamente y verifica el DBCV propio contra valores de referencia fijos. Los cinco cuadernos estándar se ejecutan en **menos de un minuto** cada uno en un equipo de escritorio.

---

## 📚 Lecturas Complementarias

*Todas están citadas de memoria: verifica los datos bibliográficos antes de citarlas formalmente.*

1. Arthur, D. & Vassilvitskii, S. (2007). *k-means++: The advantages of careful seeding*. **SODA 2007**, pp. 1027–1035. Inicialización con garantía $O(\log K)$-competitiva. *(citado de memoria, verificar)*
2. Ester, M., Kriegel, H.-P., Sander, J. & Xu, X. (1996). *A density-based algorithm for discovering clusters in large spatial databases with noise*. **KDD-96**, pp. 226–231. Artículo original de DBSCAN. *(citado de memoria, verificar)*
3. Schubert, E., Sander, J., Ester, M., Kriegel, H.-P. & Xu, X. (2017). *DBSCAN revisited, revisited: why and how you should (still) use DBSCAN*. **ACM Transactions on Database Systems** 42(3), art. 19. Guía actual para elegir parámetros y aclaraciones sobre los puntos borde. *(citado de memoria, verificar)*
4. Rousseeuw, P. J. (1987). *Silhouettes: a graphical aid to the interpretation and validation of cluster analysis*. **Journal of Computational and Applied Mathematics** 20: 53–65. *(citado de memoria, verificar)*
5. Moulavi, D., Jaskowiak, P. A., Campello, R. J. G. B., Zimek, A. & Sander, J. (2014). *Density-based clustering validation*. **Proceedings of the 2014 SIAM International Conference on Data Mining (SDM)**, pp. 839–847. El artículo de DBCV. *(citado de memoria, verificar)*
6. Müllner, D. (2011). *Modern hierarchical, agglomerative clustering algorithms*. **arXiv:1109.2378**. Algoritmos que usan `SciPy` y `fastcluster`. *(citado de memoria, verificar)*
7. Hubert, L. & Arabie, P. (1985). *Comparing partitions*. **Journal of Classification** 2: 193–218; y Vinh, N. X., Epps, J. & Bailey, J. (2010). *Information theoretic measures for clusterings comparison*. **JMLR** 11: 2837–2854. ARI, NMI y la corrección por azar (AMI). *(citados de memoria, verificar)*
8. Hastie, T., Tibshirani, R. & Friedman, J. (2009). *The Elements of Statistical Learning*, 2.ª ed., Springer. **Cap. 14** (*Unsupervised Learning*). *(citado de memoria, verificar el número de capítulo en tu edición)*

---

<div align="center">
  <p style="font-size: 0.9em; color: #64748b;">
    © 2026 <b>Universidad Santo Tomás — Seccional Tunja</b><br>
    <i>Especialización en Ciencia de Datos | Asignatura: Machine Learning</i>
  </p>
</div>
