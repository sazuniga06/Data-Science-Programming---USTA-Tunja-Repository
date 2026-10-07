# Módulo 05: Reducción de Dimensionalidad 🧭🌀

<p align="center">
  <img src="https://img.shields.io/badge/Discipline-Machine%20Learning-059669?style=for-the-badge&logo=scikitlearn&logoColor=white" alt="Machine Learning"/>
  <img src="https://img.shields.io/badge/Topics-Reducci%C3%B3n%20de%20Dimensionalidad-0ea5e9?style=for-the-badge" alt="Topics"/>
  <img src="https://img.shields.io/badge/Course-Machine%20Learning-6366f1?style=for-the-badge" alt="Course"/>
  <img src="https://img.shields.io/badge/Institution-USTA%20Tunja-1e3a8a?style=for-the-badge" alt="USTA"/>
</p>

Bienvenido al **Módulo 05** de la asignatura **Machine Learning** de la *Especialización en Ciencia de Datos* de la **Universidad Santo Tomás — Seccional Tunja**.

---

## 🧭 ¿De qué trata este módulo?

Este módulo continúa el **Capítulo 2** del syllabus y corresponde a la **sección 2.6 (*Dimensionality reduction*)**: las tres técnicas **PCA**, **t-SNE** e **Isomap**. Tras el [Módulo 04](../04%20-%20Clustering%20No%20Supervisado/README.md) (agrupar sin etiquetas), la pregunta es ahora **cómo representar con pocas dimensiones datos que tienen muchas** sin perder lo esencial: para **visualizar**, **comprimir**, **acelerar** modelos o **combatir la maldición de la dimensionalidad** (concentración de distancias, volumen en las esquinas), que ya se presentó en la [Introducción al Capítulo 2](../04%20-%20Clustering%20No%20Supervisado/00_Introduccion_Cap2_y_No_Supervisado.ipynb) y **no se repite** aquí.

> 📌 **Una nota sobre el índice del libro:** el título oficial del Capítulo 2 en el índice original es *Outline of the Scientific Research Process*, pero su contenido real es **aprendizaje no supervisado, reducción de dimensionalidad, aprendizaje por refuerzo y selección de modelos**. El curso sigue el contenido real: el Módulo 05 cubre la reducción de dimensionalidad y los Módulos 06 y 07 (cuyos nombres definitivos pueden ajustarse) desarrollan el resto del capítulo.

El enfoque es **más profundo** que el de los cursos previos: cada técnica se **formula matemáticamente**, se **implementa desde cero** y se **verifica contra `scikit-learn` y `SciPy`** con `assert` dentro del propio cuaderno (PCA por autodescomposición y por SVD con los componentes, la varianza explicada, la transformada y la reconstrucción de `sklearn.decomposition.PCA`; las afinidades $P$ y el gradiente de t-SNE; el Isomap completo contra `sklearn.manifold.Isomap`; *trustworthiness* contra `sklearn.manifold.trustworthiness`). Además se estudian las **trampas**: el efecto de la escala y de «varianza $\neq$ relevancia» en PCA, los **límites de la comparación** con una técnica no determinista (t-SNE: se compara la KL y la *trustworthiness*, no las coordenadas), la **interpretación errónea** de tamaños y distancias en un mapa t-SNE, y el **cortocircuito** de Isomap cuando $k$ es demasiado grande.

> 🔗 **Conexión con otros cursos:** el uso práctico de `PCA` con `scikit-learn` ya se vio en [Data Mining — Módulo 01 (Reducción de Dimensionalidad con PCA)](../../Data%20Mining/01%20-%20Preprocesamiento%20de%20los%20Datos/04_Reduccion_de_Dimensionalidad_con_PCA.ipynb) y en [Data Science Programming — Módulo 06 (PCA en Feature Engineering)](../../Data%20Science%20programming/06%20-%20Feature%20Engineering/04_PCA_Feature_Engineering.ipynb); este módulo los enlaza y profundiza en lo que allá no se aborda: derivación, equivalencia con la SVD, implementación propia verificada, criterios para elegir el número de componentes, blanqueamiento y límites. También retoma ideas anteriores del curso: el [Módulo 00](../00%20-%20Introduccion%20al%20Machine%20Learning/03_Importancia_del_Preprocesamiento.ipynb) (escalado y fuga de datos), el [Módulo 03](../03%20-%20Metricas%20y%20Ajuste%20de%20Hiperparametros/02_Validacion_Cruzada_y_GridSearch.ipynb) (validación cruzada y `Pipeline`) y el [Módulo 04](../04%20-%20Clustering%20No%20Supervisado/01_KMeans.ipynb) (distancias y agrupamiento sobre datos reducidos).

> 🛠️ **Práctica:** **todos** los cuadernos (los tres estándar y los tres *Para Dummies*) incluyen secciones «🛠️ Práctica» con una celda para escribir tu código y una **solución guiada desplegable**.

---

## 📚 Estructura Curricular del Módulo

### 🎓 1. Cuadernos Académicos Estándar:
1. [**00_PCA.ipynb**](00_PCA.ipynb): *Principal Component Analysis.* Las **dos formulaciones equivalentes** (varianza máxima y error de reconstrucción mínimo, con el barrido de direcciones que lo comprueba), el **centrado** y el **escalado**; la derivación con la **matriz de covarianza** y con la **SVD** ($\lambda_j=\sigma_j^2/(n-1)$), la **ambigüedad de signo** y la **estabilidad numérica** (la covarianza pierde los componentes pequeños); **PCA desde cero** (solvers `eigen` y `svd`) idéntico a `sklearn.decomposition.PCA` (componentes salvo signo, varianza explicada, transformada, reconstrucción) en tres escenarios, y el error de reconstrucción $=(n-1)\sum_{j>m}\lambda_j$; **cuántos componentes** conservar (umbral, codo por la cuerda, Kaiser, Minka y la **verosimilitud PPCA validada**, frente a la trampa de la reconstrucción en validación); **cargas** como correlaciones y *biplot* (*Wine*); PCA dentro de un **`Pipeline`** con validación cruzada (*Dígitos*); **compresión y reconstrucción de imágenes** con *eigen-dígitos*; **blanqueamiento** (PCA y ZCA) y su riesgo; límites (**escala**, **estructura no lineal**, **varianza $\neq$ relevancia**) y las variantes **Kernel PCA**, **Incremental PCA** y PCA aleatorizado.
2. [**01_tSNE.ipynb**](01_tSNE.ipynb): *t-SNE (van der Maaten & Hinton, 2008).* La idea (preservar **vecindades**); las **afinidades gaussianas** con **búsqueda binaria de $\sigma_i$** para una **perplejidad** objetivo, desde cero y verificadas (perplejidad de cada fila, simetría y contra la $P$ interna de `scikit-learn`); la $t$ de Student y el **problema de aglomeración**; el costo $\mathrm{KL}(P\Vert Q)$ y su **gradiente** (derivado y **verificado con diferencias finitas**); **t-SNE exacto $O(n^2)$ desde cero** (exageración temprana, *momentum*, ganancias) comparado con `TSNE(method="exact")` por **KL final** y ***trustworthiness*** dentro de una tolerancia (documentando por qué no hay igualdad exacta); efecto de la **perplejidad**, las **iteraciones** y la **inicialización**; advertencias de interpretación (tamaños, distancias, estructura falsa en ruido, semillas, sin `transform`); costo computacional, **Barnes–Hut** y **UMAP** como alternativa.
3. [**02_Isomap_y_Variedades.ipynb**](02_Isomap_y_Variedades.ipynb): *Isomap (Tenenbaum, de Silva & Langford, 2000).* **Hipótesis de la variedad** y **distancia geodésica frente a la Euclídea** en el *Swiss roll* con **verdad terreno analítica** (longitud de arco de la espiral); grafo de $k$ vecinos, **Floyd–Warshall desde cero** (verificado contra `scipy.sparse.csgraph`, Dijkstra de SciPy para $n=1000$) y **MDS clásico desde cero** (doble centrado), con la equivalencia **PCA = MDS con distancias Euclídeas**; **Isomap propio idéntico a `sklearn.manifold.Isomap`** y recuperación del desenrollado medida con **Procrustes**; elección de $k$ con **grafos desconectados** y **cortocircuitos** (contados con la verdad terreno); ***trustworthiness*** y ***continuity*** desde cero; **comparación PCA, Isomap, t-SNE (y LLE)** en el *Swiss roll* y la curva S con métricas locales y globales; **tabla comparativa final** y menciones de **LLE** y **UMAP**.

---

### 📝 2. Taller Práctico Evaluativo (*Hands-On*):
* [**../homeworks/05_Reduccion_Dimensionalidad_Hands_On.ipynb**](../homeworks/05_Reduccion_Dimensionalidad_Hands_On.ipynb): Taller evaluativo que integra PCA, t-SNE e Isomap en ejercicios prácticos *(el cuaderno se publica aparte)*.

---

### 🧸 3. Ruta Didáctica: Para Dummies:
Ubicada en la subcarpeta [`Para Dummies/`](Para%20Dummies/):
1. [**00_PCA_Dummies.ipynb**](Para%20Dummies/00_PCA_Dummies.ipynb): **La mejor sombra de tus datos**: el ángulo de luz cuya sombra se estira más, cuántas «sombras» guardar, comprimir una foto, y las dos trampas (la regla y la báscula, y que solo entiende rectas).
2. [**01_tSNE_Dummies.ipynb**](Para%20Dummies/01_tSNE_Dummies.ipynb): **El mapa de amigos de una fiesta**: sentar a 500 invitados para que cada quien quede junto a sus amigos, la perplejidad («¿cuántos amigos cuenta cada uno?») y por qué no es un mapa de carreteras (tamaños, distancias, semilla y datos nuevos).
3. [**02_Isomap_Variedades_Dummies.ipynb**](Para%20Dummies/02_Isomap_Variedades_Dummies.ipynb): **La hormiga y la alfombra enrollada**: distancia del pájaro frente a la de la hormiga, la red de vecinos, el peligro del atajo y una tabla simple para elegir entre PCA, Isomap y t-SNE.

---

## 💾 Datos Utilizados

Este módulo **no requiere archivos externos**: usa datasets incluidos en `scikit-learn` (*Dígitos*, *Wine*) y **datos sintéticos generados en el propio código con semilla fija** (`make_swiss_roll`, `make_s_curve`, `make_circles`, `make_blobs`, ruido gaussiano, datos de rango bajo más ruido y notas sintéticas de estudiantes en el cuaderno Dummies de PCA). El *Swiss roll* y la curva S se usan con su **verdad terreno** (longitud de arco) para juzgar cualquier desenrollado. No se usa ningún `fetch_*` ni descarga de conjuntos de datos, por lo que los cuadernos se ejecutan sin conexión a internet y de forma reproducible, tanto en local como en Google Colab.

---

## ⚙️ Requisitos

`numpy`, `pandas`, `matplotlib`, `seaborn`, `scikit-learn` y `scipy` (preinstalados en Google Colab). No se necesita ningún paquete adicional: **UMAP** y **LLE** solo se mencionan (LLE se usa a través de `sklearn.manifold.LocallyLinearEmbedding` como referencia en la comparación final). El código es compatible con las diferencias entre versiones de `scikit-learn` (p. ej. `TSNE` usa `max_iter` desde la 1.5 y su antiguo `n_iter` se deprecó y luego se eliminó: el cuaderno de t-SNE lo detecta con un `try/except`). Los seis cuadernos se ejecutan en **menos de un minuto** cada uno en un equipo de escritorio (el t-SNE exacto desde cero usa $n=500$ para que $O(n^2)$ siga siendo rápido).

---

## 📚 Lecturas Complementarias

*Todas están citadas de memoria: verifica los datos bibliográficos antes de citarlas formalmente.*

1. Jolliffe, I. T. (2002). *Principal Component Analysis*, 2.ª ed., Springer. Referencia clásica de PCA. *(citado de memoria, verificar)*
2. Eckart, C. & Young, G. (1936). *The approximation of one matrix by another of lower rank*. **Psychometrika** 1(3): 211–218. La mejor aproximación de rango bajo (SVD truncada). *(citado de memoria, verificar)*
3. Tipping, M. E. & Bishop, C. M. (1999). *Probabilistic principal component analysis*. **Journal of the Royal Statistical Society B** 61(3): 611–622; y Minka, T. P. (2000). *Automatic choice of dimensionality for PCA*, **NIPS 2000**. PPCA y estimación de la dimensión. *(citados de memoria, verificar)*
4. Halko, N., Martinsson, P.-G. & Tropp, J. A. (2011). *Finding structure with randomness: probabilistic algorithms for constructing approximate matrix decompositions*. **SIAM Review** 53(2): 217–288. SVD aleatorizada. *(citado de memoria, verificar)*
5. Schölkopf, B., Smola, A. & Müller, K.-R. (1998). *Nonlinear component analysis as a kernel eigenvalue problem*. **Neural Computation** 10(5): 1299–1319. Kernel PCA. *(citado de memoria, verificar)*
6. van der Maaten, L. & Hinton, G. (2008). *Visualizing data using t-SNE*. **Journal of Machine Learning Research** 9: 2579–2605; y van der Maaten, L. (2014). *Accelerating t-SNE using tree-based algorithms*. **JMLR** 15: 3221–3245. t-SNE y Barnes–Hut. *(citados de memoria, verificar)*
7. Wattenberg, M., Viégas, F. & Johnson, I. (2016). *How to use t-SNE effectively*. **Distill**. Guía interactiva de las trampas de interpretación. *(citado de memoria, verificar)*
8. Tenenbaum, J. B., de Silva, V. & Langford, J. C. (2000). *A global geometric framework for nonlinear dimensionality reduction*. **Science** 290(5500): 2319–2323; y Roweis, S. T. & Saul, L. K. (2000), **Science** 290(5500): 2323–2326 (LLE). *(citados de memoria, verificar)*
9. McInnes, L., Healy, J. & Melville, J. (2018). *UMAP: Uniform Manifold Approximation and Projection for dimension reduction*. **arXiv:1802.03426**. *(citado de memoria, verificar)*
10. Venna, J. & Kaski, S. (2006). *Local multidimensional scaling*. **Neural Networks** 19(6–7): 889–899. *Trustworthiness* y *continuity*. *(citado de memoria, verificar)*
11. Géron, A. (2025). *Hands-On Machine Learning with Scikit-Learn and PyTorch*, O'Reilly. **Cap. 7** (*Dimensionality Reduction*); y Raschka, S. (2015). *Python Machine Learning*, Packt, **Cap. 5** (*Compressing Data via Dimensionality Reduction*). Ambos disponibles en `Machine Learning/Libros/` (capítulos verificados contra los PDF).

---

<div align="center">
  <p style="font-size: 0.9em; color: #64748b;">
    © 2026 <b>Universidad Santo Tomás — Seccional Tunja</b><br>
    <i>Especialización en Ciencia de Datos | Asignatura: Machine Learning</i>
  </p>
</div>
