# Módulo 09: Casos de Estudio y Aplicaciones 🧩🎬

<p align="center">
  <img src="https://img.shields.io/badge/Discipline-Machine%20Learning-059669?style=for-the-badge&logo=scikitlearn&logoColor=white" alt="Machine Learning"/>
  <img src="https://img.shields.io/badge/Topics-Casos%20de%20Estudio%20y%20Aplicaciones-0ea5e9?style=for-the-badge" alt="Topics"/>
  <img src="https://img.shields.io/badge/Course-Machine%20Learning-6366f1?style=for-the-badge" alt="Course"/>
  <img src="https://img.shields.io/badge/Institution-USTA%20Tunja-1e3a8a?style=for-the-badge" alt="USTA"/>
</p>

Bienvenido al **Módulo 09**, el **último** de la asignatura **Machine Learning** de la *Especialización en Ciencia de Datos* de la **Universidad Santo Tomás — Seccional Tunja**.

---

## 🧭 ¿De qué trata este módulo?

Este módulo **cierra el Capítulo 3** del syllabus, ***Advanced Topics and Practical Applications***, y con él **todo el libro**. Corresponde a las secciones **3.8 (*Case Studies and Applications*)**, **3.9 (*Computer Vision applications: image classification, object detection*)**, **3.10 (*Natural Language Processing applications: text classification, sentiment analysis*)** y **3.11 (*Recommender systems: Collaborative Filtering, Matrix Factorization*)**. Tras el [Módulo 08](../08%20-%20Temas%20Avanzados%20de%20ML/README.md) (qué hay que añadir a un algoritmo para que sea útil y confiable en un problema real), la pregunta final es: **¿cómo se ve todo eso en proyectos y en datos que no son una tabla?**

El primer cuaderno es el **integrador (*capstone*) del curso**: encadena en tres proyectos completos (fuga de clientes, precio de vivienda y segmentación) las técnicas de los Módulos 00 a 08 **enlazando** a cada una en vez de repetirla. Los otros tres llevan el mismo rigor a **imágenes**, **texto** e **interacciones usuario–ítem**. Como en el resto del curso, se **implementa desde cero y se verifica con `assert`** dentro del propio cuaderno (contra `SciPy`, `scikit-learn`, `PyTorch` y `torchvision`), con **semillas fijas**, **varias repeticiones** y **resultados reportados con honestidad**, incluidos los casos en que el modelo «más sofisticado» **no** gana.

> 🔗 **Conexión con otros cursos y módulos:** este módulo **usa** casi todo lo anterior: el `Pipeline` y la fuga de datos ([Módulo 00](../00%20-%20Introduccion%20al%20Machine%20Learning/03_Importancia_del_Preprocesamiento.ipynb)), los modelos lineales y la regularización ([Módulo 01](../01%20-%20Modelos%20Lineales%20Supervisados/README.md)), las redes neuronales con PyTorch ([Módulo 02](../02%20-%20Arboles%20Bosques%20y%20Redes%20Neuronales/02_Redes_Neuronales.ipynb)), las métricas y la validación ([Módulo 03](../03%20-%20Metricas%20y%20Ajuste%20de%20Hiperparametros/README.md)), K-Means y la silueta ([Módulo 04](../04%20-%20Clustering%20No%20Supervisado/README.md)), PCA y la SVD ([Módulo 05](../05%20-%20Reduccion%20de%20Dimensionalidad/README.md)), la exploración (bandidos, [Módulo 06](../06%20-%20Aprendizaje%20por%20Refuerzo/README.md)), la selección de modelos y el *Random Search* ([Módulo 07](../07%20-%20Seleccion%20de%20Modelos%20y%20Optimizacion/README.md)) y el *transfer learning*, la explicabilidad, el desbalance y los faltantes ([Módulo 08](../08%20-%20Temas%20Avanzados%20de%20ML/README.md)). La **ética de la IA** y el pensamiento crítico sobre datos, en [IA — Módulo 03](../../Introduccion%20a%20la%20Inteligencia%20Artificial/03%20-%20Etica%20y%20el%20Nuevo%20Paradigma%20de%20la%20IA/README.md) y [Visual Analytics — Módulo 03](../../Visual%20Analytics%20and%20Critical%20Thinking/03%20-%20Pensamiento%20Critico%20en%20Datos/README.md).

> 🛠️ **Ponlo en práctica:** todos los cuadernos (estándar y *Para Dummies*) incluyen secciones **«🛠️ Práctica»**: una celda de código para que escribas tu solución y, justo debajo, la **solución guiada desplegable** (`💡 Haz clic aquí para ver la solución guiada...`). Inténtalo primero y abre la solución solo para comparar.

---

## 📚 Estructura Curricular del Módulo

### 🎓 1. Cuadernos Académicos Estándar:
1. [**00_Casos_de_Estudio_y_Aplicaciones.ipynb**](00_Casos_de_Estudio_y_Aplicaciones.ipynb): *Sección 3.8.* **Cuaderno integrador (*capstone*).** El flujo de un proyecto con un **mapa de enlaces** a los Módulos 00–08. **Caso A, fuga de clientes** (8 000 clientes sintéticos, ≈ 8 % de fugas, faltantes MAR/MNAR y variables de ruido): **métrica de negocio con costos** (umbral teórico $50/500=0.10$), políticas triviales y **techo realista** (conocido solo en sintético), `Pipeline` + `ColumnTransformer` con imputación e indicador, **CV repetida y prueba t corregida** (Nadeau–Bengio: p ≈ 0.03 frente a ≈ 0.001 de la ingenua), *Random Search*, **calibración**, **umbral por costo** (casi **duplica el ahorro** frente al 0.5), permutación y PDP (control negativo con variables de ruido) y análisis de errores por segmentos; resultado honesto: **la regresión logística gana** a bosque y *boosting*. **Caso B, precio de vivienda:** transformación logarítmica, métricas en unidades reales, diagnóstico de residuos e **intervalos cuantílicos que sub-cubren** (≈ 66 % frente al 80 % nominal). **Caso C, segmentación:** PCA + K-Means con silueta y estabilidad. **Ficha del modelo** (*model card*) generada automáticamente con IC *bootstrap* y una **lista de verificación de 16 puntos** enlazada a los módulos. Bandera `RAPIDO`.
2. [**01_Vision_por_Computador.ipynb**](01_Vision_por_Computador.ipynb): *Sección 3.9.* La imagen como tensor; **convolución 2D desde cero** (*padding*, *stride*, multicanal) **verificada contra `scipy.signal.correlate2d` y `torch.nn.functional.conv2d`**, con el tamaño de salida y la **equivarianza** comprobados; filtros de Sobel/gaussiano/laplaciano y ***pooling*** (el *max-pooling* sube la correlación ante un desplazamiento de 1 píxel de ≈ 0.77 a ≈ 0.98). **Clasificación de dígitos** con píxeles, rasgos clásicos (HOG-lite) y una **CNN en PyTorch**: con imágenes limpias la CNN **no es mejor** que la regresión logística (≈ 0.97 todas), la CNN sin aumento **no es invariante** (≈ 0.45 con 1 píxel de desplazamiento) y con aumento llega a ≈ 0.92; con 100 imágenes el aumento **perjudica**. **Detección:** **IoU, NMS (idéntico a `torchvision.ops.nms`), anclas, precisión/recobrado, AP y mAP desde cero**, y un **detector de juguete** (ventana deslizante + clasificador + NMS) sobre escenas sintéticas (mAP@0.5 ≈ 0.98 con NMS y ≈ 0.58 sin él; **falla con otra escala**). Sección **opcional protegida** (`USAR_DETECTOR_PRETRAINED = False`) con un detector preentrenado de `torchvision`; enlaza con el [*transfer learning* del Módulo 08](../08%20-%20Temas%20Avanzados%20de%20ML/01_Transfer_Learning_y_Fine_Tuning.ipynb). Bandera `RAPIDO`.
3. [**02_Procesamiento_de_Lenguaje_Natural.ipynb**](02_Procesamiento_de_Lenguaje_Natural.ipynb): *Sección 3.10.* **Corpus sintético de reseñas en español** (plantillas con negación, doble negación, «pero», sarcasmo, erratas, tildes y ruido de etiquetas; **documentado como sintético: las métricas son optimistas**); tokenización y trampas del español (las *stopwords* incluyen **«no»**); **bolsa de palabras y TF-IDF desde cero** verificados contra `CountVectorizer`/`TfidfVectorizer`; **Naive Bayes multinomial desde cero** (Laplace, log-espacio) verificado contra `MultinomialNB`; regresión logística con 1-2-gramas (≈ 0.93 frente a ≈ 0.80 de Naive Bayes); **léxico frente a supervisado** (la exactitud baja ≈ 10 puntos al cambiar de dominio; quitar «no» baja la exactitud con negación de 0.955 a 0.784); desbalance; 16 frases escritas a mano; **LSA y vectores de palabras (co-ocurrencia → PPMI → SVD) desde cero** verificados contra `TruncatedSVD` (y por qué LSA **no** es supervisado). Dos bloques **opcionales protegidos** (`USAR_TRANSFORMERS`, `USAR_20NG`, ambos `False`): un modelo BERT multilingüe con `transformers.pipeline` y 20 Newsgroups.
4. [**03_Sistemas_de_Recomendacion.ipynb**](03_Sistemas_de_Recomendacion.ipynb): *Sección 3.11.* Matriz usuario–ítem **sintética** (600 × 400, ≈ 6 % observada, MNAR, 5 factores latentes); retroalimentación explícita frente a implícita; evaluación por usuario y tiempo con **RMSE, Precision@k, Recall@k y NDCG@k desde cero** (NDCG verificado contra `sklearn`); líneas base (azar, sesgos, popularidad); **kNN por usuarios y por ítems desde cero**; **factorización de matrices con SGD** (**gradiente verificado con diferencias finitas**) **y con ALS** (**objetivo monótono verificado**); **teorema de Eckart–Young verificado** (con la matriz completa, ALS sin regularizar **==** SVD truncada); resultado honesto: **MF gana en RMSE (≈ 0.78 frente a ≈ 1.18) pero la popularidad la supera en NDCG@10 sobre lo observado** (≈ 0.19 frente a ≈ 0.09), y **contra la verdad completa** MF acierta ≈ 94 % del *top-10* frente a ≈ 42 %; arranque en frío y **híbrido con contenido**, cobertura y burbuja de filtro. Bloque **opcional protegido** (`USAR_MOVIELENS = False`) con MovieLens: con calificaciones **reales**, MF casi no mejora el RMSE (≈ 0.853 frente a ≈ 0.867 de los sesgos) y la popularidad gana con claridad en NDCG@10 (≈ 0.080 frente a ≈ 0.031). Bandera `RAPIDO`.

---

### 📝 2. Taller Práctico Evaluativo (*Hands-On*):
* [**../homeworks/09_Casos_Estudio_Aplicaciones_Hands_On.ipynb**](../homeworks/09_Casos_Estudio_Aplicaciones_Hands_On.ipynb): Taller evaluativo que integra el flujo de proyecto y las aplicaciones a imágenes, texto y recomendación en ejercicios prácticos *(el cuaderno se publica aparte)*.

---

### 🧸 3. Ruta Didáctica: Para Dummies:
Ubicada en la subcarpeta [`Para Dummies/`](Para%20Dummies/):
1. [**00_Casos_Estudio_Dummies.ipynb**](Para%20Dummies/00_Casos_Estudio_Dummies.ipynb): **El triage de urgencias**: el guardia que dice «nadie se va» (90 % de aciertos sin detectar a nadie), la cuenta de costos que fija **a partir de qué probabilidad llamar** (50/500 = 0.10) y el **examen sellado** frente al aprendiz que memoriza (100 % estudiando, ≈ 82 % en el examen); la receta de siete pasos.
2. [**01_Vision_Computador_Dummies.ipynb**](Para%20Dummies/01_Vision_Computador_Dummies.ipynb): **La lupa que se desliza**: una imagen de 6×6 y una plantilla que «se enciende» en un borde, el **IoU** como «dos manteles que se pisan», **quedarse con la caja más segura** (NMS) y el modelo de dígitos que cae de ≈ 97 % a ≈ 39 % al correr la imagen un píxel. Sin PyTorch.
3. [**02_NLP_Dummies.ipynb**](Para%20Dummies/02_NLP_Dummies.ipynb): **Contar palabras como cartas de una baraja**: frases como filas de conteos, las palabras raras que pesan más, Naive Bayes como **votación de palabras** y la **trampa del «no»** (con palabras sueltas, «es bueno» y «no es bueno» dan el azar).
4. [**03_Recomendacion_Dummies.ipynb**](Para%20Dummies/03_Recomendacion_Dummies.ipynb): **Amigos con gustos parecidos**: la tabla de gustos casi vacía, **preguntar al amigo más parecido**, los **gustos ocultos** (acción y romance, descubiertos solos) y la **persona nueva** (arranque en frío).

---

## 💾 Datos Utilizados

Todos los datos son de `scikit-learn` o **sintéticos con semilla fija, generados por código dentro de cada cuaderno**; **no hay descargas** en el flujo principal y **no se necesita ninguna carpeta `data/`** (no se crearon archivos CSV: los generadores son funciones de unas pocas líneas, y así cada cuaderno es autocontenido en Google Colab).

| Conjunto | Origen | Dónde se usa |
|---|---|---|
| **Clientes con fuga** (8 000 × 13, ≈ 8 % de fugas, faltantes MAR/MNAR, 2 variables de ruido) | Generador `generar_clientes(semilla=7)` | Cuaderno 00, Caso A |
| **Viviendas** (3 000 × 6, precio multiplicativo) | Generador `generar_viviendas(semilla=11)` | Cuaderno 00, Caso B |
| **Segmentos de clientes** (3 000 × 6, 4 segmentos ocultos) | Generador `generar_segmentos(semilla=5)` | Cuaderno 00, Caso C |
| **Foto de ejemplo** (`china.jpg`, 427 × 640 × 3) | `sklearn.datasets.load_sample_image` (incluida en `scikit-learn`) | Cuaderno 01 (la imagen como tensor, filtros) |
| ***Digits*** (1 797 imágenes 8×8) | `sklearn.datasets.load_digits` | Cuaderno 01 (CNN, aumento) y Dummies 01 |
| **Escenas sintéticas** (lienzos 64×64 con cuadrados, círculos y cruces; cajas exactas) | Generador `generar_escena` | Cuaderno 01 (detector de juguete) |
| **Reseñas en español** (4 000 de restaurantes + 1 000 de electrónica) y **16 frases escritas a mano** | Generador `generar_corpus(semilla=1 y 2)` | Cuaderno 02 |
| **Calificaciones usuario–ítem** (600 × 400, ≈ 6 % observada, 5 factores latentes) | Generador `generar_ratings(semilla=0..)` | Cuaderno 03 |
| **Mini-ejemplos de juguete** (clientes, tabla de gustos, reseñas) | `numpy.random.default_rng(semilla)` y tablas escritas a mano | Los cuatro *Dummies* |

> 🌐 **Excepciones (opcionales y protegidas, desactivadas por defecto):** cuaderno 01, sección 8 (un detector de `torchvision`, con descarga de pesos); cuaderno 02, sección 8 (un modelo de `transformers` y `20 Newsgroups`); cuaderno 03, sección 8 (MovieLens por URL). Cada una exige poner su bandera en `True` **y** tener red; todas están en `try/except` y, si algo falta, imprimen un aviso y el cuaderno **sigue**.

## ⚙️ Requisitos

`numpy`, `pandas`, `matplotlib`, `seaborn`, `scipy` y `scikit-learn` (preinstalados en Google Colab). **`torch` es requerido** para el cuaderno **01** (preinstalado en Colab). **Opcionales:** `torchvision` (la verificación de NMS/IoU contra `torchvision.ops` y la sección 8 del cuaderno 01), `scikit-image` (la verificación del filtro de Sobel), `transformers` (la sección 8 del cuaderno 02) y `imbalanced-learn`/`shap` (no se usan aquí); cada una se importa con `try/except` y, si falta, imprime un aviso y el cuaderno **sigue** sin errores. Los cuatro **Dummies** usan solo `NumPy`, `matplotlib` y `scikit-learn` (sin PyTorch).

Se ejecutó de verdad, de arriba abajo y sin errores, con las **versiones más recientes** (NumPy 2.5, SciPy 1.18, scikit-learn 1.9, PyTorch 2.14 CPU, con `torchvision` instalado) y con versiones **tipo Colab** (NumPy 2.0, SciPy 1.14, scikit-learn 1.6, sin `torchvision`: la rama «no instalado»). Tiempos aproximados en un equipo de escritorio con CPU de 8 núcleos (varían con la carga y el número de núcleos; en Colab pueden ser mayores): cuaderno 00 ≈ 40 s, 01 ≈ 50–70 s, 02 ≈ 10 s y 03 ≈ 35–45 s con `RAPIDO = True`; los *Dummies* tardan 3–15 s. Con `RAPIDO = False` (más semillas, épocas, repeticiones de validación cruzada y conjuntos de datos): 00 ≈ 2 min, 01 ≈ 4 min y 03 ≈ 1 min. Se comprobaron además las **ramas opcionales**: con `scikit-image` instalado (correlación de 1.00000 con `skimage.filters.sobel`) y sin él; con `torchvision` instalado y sin él; y, **con red**, las tres secciones protegidas (detector de COCO, BERT multilingüe y *20 Newsgroups*, MovieLens real).

---

## 📚 Lecturas Complementarias

*Todas están citadas de memoria salvo las marcadas como verificadas contra el índice del PDF en `Machine Learning/Libros/`: comprueba los datos bibliográficos antes de citarlas formalmente.*

1. **Visión (libros del curso).** Géron, A. (2025), *Hands-On Machine Learning with Scikit-Learn and PyTorch*, O'Reilly: **Cap. 12** (*Deep Computer Vision Using Convolutional Neural Networks*: *Convolutional Layers*, *Pooling Layers*, *Object Detection*, *You Only Look Once*), **Cap. 16** (*Vision and Multimodal Transformers*); Barua, T. et al. (2024), *Machine Learning with Python*, De Gruyter: **Cap. 8**, secciones 8.4 y 8.4.1; Mueller, J. P. & Massaron, L. (2021), *Machine Learning For Dummies*: **Cap. 17**. Disponibles en `Machine Learning/Libros/` (títulos verificados contra el índice de cada PDF).
2. **Visión (artículos).** LeCun, Y., Bottou, L., Bengio, Y. & Haffner, P. (1998), *Gradient-based learning applied to document recognition*, **Proceedings of the IEEE** 86(11); Krizhevsky, A., Sutskever, I. & Hinton, G. E. (2012), *ImageNet classification with deep convolutional neural networks*, **NeurIPS 25**; Redmon, J., Divvala, S., Girshick, R. & Farhadi, A. (2016), *You only look once*, **CVPR**; Ren, S., He, K., Girshick, R. & Sun, J. (2015), *Faster R-CNN*, **NeurIPS 28**. *(citados de memoria, verificar)*
3. **Lenguaje natural (libros del curso).** Raschka, S. (2015), *Python Machine Learning*, Packt: **Cap. 8** (*Applying Machine Learning to Sentiment Analysis*); Géron (2025): **Cap. 14** (*Natural Language Processing with RNNs and Attention*) y **Cap. 15** (*Transformers for Natural Language Processing and Chatbots*); Ramsay, A. & Ahmad, T. (2023), *Machine Learning for Emotion Analysis in Python*, Packt: **Caps. 5 y 6**; Mueller & Massaron (2021): **Cap. 18**. Disponibles en `Machine Learning/Libros/` (verificados contra el índice o el prólogo de cada PDF).
4. **Lenguaje natural (artículos y libro de referencia).** Jurafsky, D. & Martin, J. H., *Speech and Language Processing* (3.ª ed., borrador en línea); Mikolov, T., Chen, K., Corrado, G. & Dean, J. (2013), *Efficient estimation of word representations in vector space*, **arXiv:1301.3781**; Vaswani, A. et al. (2017), *Attention is all you need*, **NeurIPS 30**; Devlin, J., Chang, M.-W., Lee, K. & Toutanova, K. (2019), *BERT*, **NAACL**. *(citados de memoria, verificar)*
5. **Recomendación (libros del curso).** Harrington, P. (2012), *Machine Learning in Action*, Manning: **Cap. 14** (*Simplifying data with the singular value decomposition*: sistemas de recomendación y filtrado colaborativo); Winn, J. et al., *Model-Based Machine Learning*, CRC Press: **Cap. 5** (*Making Recommendations*); Barua et al. (2024): **sección 8.3**; Mueller & Massaron (2021): **Cap. 19**. Disponibles en `Machine Learning/Libros/` (verificados contra el índice de cada PDF).
6. **Recomendación (artículos).** Koren, Y., Bell, R. & Volinsky, C. (2009), *Matrix factorization techniques for recommender systems*, **IEEE Computer** 42(8): 30–37; Sarwar, B., Karypis, G., Konstan, J. & Riedl, J. (2001), *Item-based collaborative filtering recommendation algorithms*, **WWW**; Hu, Y., Koren, Y. & Volinsky, C. (2008), *Collaborative filtering for implicit feedback datasets*, **ICDM**. *(citados de memoria, verificar)*
7. **Aplicaciones y práctica de ML.** Géron (2025): **Cap. 2** (*End-to-End Machine Learning Project*); McMahon, A. P. (2023), *Machine Learning Engineering with Python* (2.ª ed.), Packt: **Cap. 3**; Mitchell, M. et al. (2019), *Model cards for model reporting*, **FAT\* 2019**; Sculley, D. et al. (2015), *Hidden technical debt in machine learning systems*, **NeurIPS 28**. Los libros, disponibles en `Machine Learning/Libros/` (verificados); los artículos, *(citados de memoria, verificar)*.
8. **Visión del libro completo.** Hastie, T., Tibshirani, R. & Friedman, J. (2009), *The Elements of Statistical Learning*, 2.ª ed., Springer; Sutton, R. S. & Barto, A. G. (2018), *Reinforcement Learning: An Introduction*, 2.ª ed., MIT Press: las dos referencias teóricas a las que remiten las lecturas de los Módulos 03 a 07. *(citados de memoria, verificar)*

---

## 📖 Glosario

Los **40 términos clave de todo el curso** (con el módulo donde se estudian), en orden alfabético:

| Término | Definición breve | Dónde se estudia |
|---|---|---|
| **Aprendizaje no supervisado** | Descubrir estructura (grupos, representaciones de baja dimensión, densidad) en datos **sin etiquetas**; no hay verdad de terreno contra la cual validar. | [M04 · No supervisado](../04%20-%20Clustering%20No%20Supervisado/00_Introduccion_Cap2_y_No_Supervisado.ipynb) |
| **Aprendizaje por refuerzo** | Un **agente** aprende a actuar interactuando con un entorno para **maximizar la recompensa acumulada**; no recibe respuestas correctas sino señales de recompensa. | [M06 · Fundamentos de RL](../06%20-%20Aprendizaje%20por%20Refuerzo/00_Fundamentos_RL_y_MDPs.ipynb) |
| **Aprendizaje supervisado** | Aprender una función $f$ a partir de ejemplos etiquetados $(\mathbf x, y)$ para predecir $y$ en datos nuevos: **clasificación** si $y$ es discreta, **regresión** si es continua. | [M01 · Fundamentos](../01%20-%20Modelos%20Lineales%20Supervisados/00_Fundamentos_del_Aprendizaje_Supervisado.ipynb) |
| **Calibración** | Propiedad de que las probabilidades predichas coinciden con las frecuencias observadas; se mide con la curva de calibración y la puntuación de Brier. | [M07 · Evaluación y selección](../07%20-%20Seleccion%20de%20Modelos%20y%20Optimizacion/00_Evaluacion_y_Seleccion_de_Modelos.ipynb) |
| **Coeficiente de silueta** | Para cada punto, $(b-a)/\max(a,b)\in[-1,1]$, con $a$ la distancia media a su grupo y $b$ a la del grupo más cercano; mide cohesión y separación sin etiquetas. | [M04 · Métricas de clustering](../04%20-%20Clustering%20No%20Supervisado/04_Metricas_de_Clustering.ipynb) |
| **Convolución y CNN** | Operación que desliza un *kernel* sobre una imagen sumando productos (en rigor, correlación cruzada); con **pesos compartidos** y equivarianza a la traslación. Una CNN apila convoluciones, no linealidades y *pooling*. | [M09 · Visión](01_Vision_por_Computador.ipynb) |
| **DBSCAN** | *Clustering* basado en densidad con $\varepsilon$ y `min_samples`: distingue puntos núcleo, borde y **ruido**; encuentra formas arbitrarias sin fijar el número de grupos. | [M04 · DBSCAN](../04%20-%20Clustering%20No%20Supervisado/03_DBSCAN.ipynb) |
| **Descenso del gradiente** | Minimiza una función de pérdida actualizando los parámetros en dirección opuesta al gradiente, $\theta\leftarrow\theta-\eta\nabla L$; variantes por lotes, estocástica y de mini-lotes. | [M01 · Regresión lineal](../01%20-%20Modelos%20Lineales%20Supervisados/01_Regresion_Lineal.ipynb) |
| **Desplazamiento de distribución (*dataset shift*)** | Cambio de $P(\mathbf x,y)$ entre entrenamiento y producción: de covariables, de etiquetas o de concepto; degrada el modelo aunque el código no cambie. | [M08 · Introducción al Cap. 3](../08%20-%20Temas%20Avanzados%20de%20ML/00_Introduccion_Cap3_y_Conceptos_Avanzados.ipynb) |
| **DQN (*Deep Q-Network*)** | *Q-learning* con una red neuronal como aproximador, estabilizado con **repetición de experiencia** y una **red objetivo**. | [M06 · Deep RL](../06%20-%20Aprendizaje%20por%20Refuerzo/03_Deep_RL_DQN_y_Policy_Gradient.ipynb) |
| ***Embeddings* y LSA** | Representaciones densas de palabras o documentos obtenidas factorizando una matriz (SVD de TF-IDF en LSA; de PPMI en vectores de palabras), de modo que la cercanía refleja contextos parecidos. | [M09 · PLN](02_Procesamiento_de_Lenguaje_Natural.ipynb) |
| **Explicabilidad (permutación, PDP, SHAP)** | Técnicas para describir qué usa un modelo: importancia por **permutación**, **dependencia parcial** y **valores de Shapley** (atribución aditiva con eficiencia, simetría, jugador nulo y aditividad). Describen al modelo, no la causalidad. | [M08 · Explicabilidad](../08%20-%20Temas%20Avanzados%20de%20ML/02_Explicabilidad_de_Modelos.ipynb) |
| **Ficha del modelo (*model card*)** | Documento breve que resume qué decide un modelo, con qué datos, qué tan bien funciona (con incertidumbre y por subgrupos), sus límites, usos excluidos y plan de monitoreo. | [M09 · Casos de estudio](00_Casos_de_Estudio_y_Aplicaciones.ipynb) |
| **Filtrado colaborativo y factorización de matrices** | Recomendar a partir de la matriz usuario–ítem: por **vecindarios** (usuarios o ítems parecidos) o con factores latentes $\hat r_{ui}=\mu+b_u+b_i+\mathbf p_u^\top\mathbf q_i$ ajustados con SGD o ALS. Se evalúa con RMSE y P@k, R@k y NDCG@k. | [M09 · Recomendación](03_Sistemas_de_Recomendacion.ipynb) |
| **Fuga de datos y *Pipeline*** | **Fuga:** información del conjunto de prueba, del futuro o de la etiqueta que se filtra al entrenamiento y da resultados optimistas. El ***Pipeline*** encadena preprocesamiento y modelo para ajustar todo **solo** con el entrenamiento. | [M00 · Preprocesamiento](../00%20-%20Introduccion%20al%20Machine%20Learning/03_Importancia_del_Preprocesamiento.ipynb) |
| **Función de valor** | Retorno esperado desde un estado, $v_\pi(s)$, o desde un par estado–acción, $q_\pi(s,a)$, siguiendo una política; satisface las **ecuaciones de Bellman**. | [M06 · Funciones de valor](../06%20-%20Aprendizaje%20por%20Refuerzo/01_Funciones_de_Valor_y_Q_Learning.ipynb) |
| **Gradiente de política (REINFORCE)** | Optimiza directamente los parámetros de la política ascendiendo $\nabla J=\mathbb E[G_t\,\nabla\log\pi_\theta(a_t\mid s_t)]$; alta varianza, mitigada con *baselines* y actor-crítico. | [M06 · Gradientes de política](../06%20-%20Aprendizaje%20por%20Refuerzo/02_Gradientes_de_Politica.ipynb) |
| **Hiperparámetro** | Valor que se fija **antes** de entrenar y no se aprende de los datos (profundidad, $k$, $C$, tasa de aprendizaje); se elige con validación, nunca con el conjunto de prueba. | [M03 · Validación cruzada y GridSearch](../03%20-%20Metricas%20y%20Ajuste%20de%20Hiperparametros/02_Validacion_Cruzada_y_GridSearch.ipynb) |
| **IoU, NMS y mAP** | **IoU:** intersección sobre unión de dos cajas. **NMS:** conserva la caja de mayor puntaje y elimina las que la solapan (IoU $>\tau$). **mAP:** media sobre clases del área bajo la curva precisión–recobrado a un umbral de IoU. | [M09 · Visión](01_Vision_por_Computador.ipynb) |
| ***K-Means*** | Particiona los datos en $k$ grupos minimizando la **inercia** (suma de distancias cuadradas a los centroides) mediante el algoritmo de Lloyd; sensible a la inicialización y a la escala. | [M04 · K-Means](../04%20-%20Clustering%20No%20Supervisado/01_KMeans.ipynb) |
| **Matriz de confusión** | Tabla de aciertos y errores por clase (verdaderos/falsos positivos y negativos) de la que se derivan casi todas las métricas de clasificación. | [M03 · Métricas de clasificación](../03%20-%20Metricas%20y%20Ajuste%20de%20Hiperparametros/00_Metricas_de_Clasificacion.ipynb) |
| **Mecanismos de ausencia (MCAR, MAR, MNAR) e imputación** | Los datos faltan completamente al azar, al azar condicionado a lo observado o **no** al azar; de ello depende el sesgo de eliminar casos o imputar (media, *k* vecinos, MICE). | [M08 · Datos faltantes](../08%20-%20Temas%20Avanzados%20de%20ML/04_Datos_Faltantes.ipynb) |
| **MSE, RMSE y $R^2$** | Error cuadrático medio, su raíz (en las unidades de $y$) y fracción de la varianza explicada respecto a predecir la media (puede ser **negativo**). | [M03 · Métricas de regresión](../03%20-%20Metricas%20y%20Ajuste%20de%20Hiperparametros/01_Metricas_de_Regresion.ipynb) |
| **Optimización bayesiana** | Optimiza una función costosa (caja negra) con un **modelo sustituto** (proceso gaussiano) y una **función de adquisición** que equilibra explorar y explotar. | [M07 · Optimización bayesiana](../07%20-%20Seleccion%20de%20Modelos%20y%20Optimizacion/03_Optimizacion_Bayesiana.ipynb) |
| **PCA (análisis de componentes principales)** | Proyección lineal ortogonal que **maximiza la varianza** (o, equivalentemente, minimiza el error de reconstrucción); se calcula con la SVD de los datos centrados. | [M05 · PCA](../05%20-%20Reduccion%20de%20Dimensionalidad/00_PCA.ipynb) |
| **Política** | Regla de decisión del agente, $\pi(a\mid s)$: qué acción tomar (o con qué probabilidad) en cada estado. | [M06 · MDP](../06%20-%20Aprendizaje%20por%20Refuerzo/00_Fundamentos_RL_y_MDPs.ipynb) |
| ***Precision*, *recall* y F1** | *Precision* $=VP/(VP+FP)$; *recall* $=VP/(VP+FN)$; F1 es su **media armónica**. Con clases desbalanceadas la exactitud engaña y se prefieren estas. | [M03 · Métricas de clasificación](../03%20-%20Metricas%20y%20Ajuste%20de%20Hiperparametros/00_Metricas_de_Clasificacion.ipynb) |
| **Proceso de decisión de Markov (MDP)** | Modelo $(\mathcal S,\mathcal A,P,R,\gamma)$ de decisión secuencial con la propiedad de Markov: el futuro depende solo del estado y la acción actuales. | [M06 · MDP](../06%20-%20Aprendizaje%20por%20Refuerzo/00_Fundamentos_RL_y_MDPs.ipynb) |
| ***Q-learning*** | Algoritmo de diferencia temporal ***off-policy*** que actualiza $Q(s,a)\leftarrow Q+\alpha\,[\,r+\gamma\max_{a'}Q(s',a')-Q\,]$ y converge, en el caso tabular, a $q^*$. | [M06 · Q-learning](../06%20-%20Aprendizaje%20por%20Refuerzo/01_Funciones_de_Valor_y_Q_Learning.ipynb) |
| ***Random Search*** | Busca hiperparámetros muestreándolos de distribuciones; supera a la rejilla cuando solo unos pocos hiperparámetros importan (dimensión efectiva baja). | [M07 · Random Search](../07%20-%20Seleccion%20de%20Modelos%20y%20Optimizacion/02_Random_Search_y_GridSearch.ipynb) |
| **Red neuronal y retropropagación** | Composición de capas de neuronas con activaciones no lineales; se entrena calculando el gradiente de la pérdida con la **regla de la cadena** (retropropagación) y un optimizador. | [M02 · Redes neuronales](../02%20-%20Arboles%20Bosques%20y%20Redes%20Neuronales/02_Redes_Neuronales.ipynb) |
| **Regularización** | Penalizar la complejidad del modelo para reducir su varianza: $L_2$ (*Ridge*), $L_1$ (*Lasso*, produce ceros), poda de árboles, *dropout* o parada temprana. | [M01 · Regresión lineal](../01%20-%20Modelos%20Lineales%20Supervisados/01_Regresion_Lineal.ipynb) |
| **ROC-AUC y PR-AUC** | Áreas bajo la curva ROC y bajo la curva precisión–recobrado: resumen **independiente del umbral**. La línea base de la PR-AUC es la prevalencia de la clase positiva. | [M03 · Métricas de clasificación](../03%20-%20Metricas%20y%20Ajuste%20de%20Hiperparametros/00_Metricas_de_Clasificacion.ipynb) |
| **SMOTE** | Sobremuestreo sintético de la clase minoritaria: cada ejemplo nuevo se interpola sobre el segmento entre un minoritario y uno de sus vecinos minoritarios; debe aplicarse **solo** al entrenamiento. | [M08 · Desbalanceados](../08%20-%20Temas%20Avanzados%20de%20ML/03_Datasets_Desbalanceados.ipynb) |
| **Sobreajuste y sesgo–varianza** | El modelo memoriza el ruido del entrenamiento: error de entrenamiento bajo y de generalización alto. Se explica por la descomposición del error esperado en **sesgo², varianza y ruido irreducible**: más complejidad baja el sesgo y sube la varianza. | [M01 · Fundamentos](../01%20-%20Modelos%20Lineales%20Supervisados/00_Fundamentos_del_Aprendizaje_Supervisado.ipynb) |
| **TF-IDF y Naive Bayes** | **TF-IDF:** conteo de la palabra por documento ponderado por $\ln\frac{1+n}{1+\mathrm{df}}+1$ y normalizado. **Naive Bayes multinomial:** clasifica sumando $\log\theta_{c,t}$ de las palabras, suponiendo independencia entre ellas dada la clase. | [M09 · PLN](02_Procesamiento_de_Lenguaje_Natural.ipynb) |
| ***Transfer learning* y *fine-tuning*** | Reutilizar un modelo preentrenado en otra tarea: extraer sus rasgos con el *backbone* congelado o ajustarlo con una tasa de aprendizaje pequeña; ayuda sobre todo con pocos datos. | [M08 · Transfer learning](../08%20-%20Temas%20Avanzados%20de%20ML/01_Transfer_Learning_y_Fine_Tuning.ipynb) |
| **t-SNE** | Reducción no lineal para **visualización** que conserva las vecindades locales (minimiza la divergencia KL entre afinidades); distancias entre grupos y tamaños **no** son interpretables. | [M05 · t-SNE](../05%20-%20Reduccion%20de%20Dimensionalidad/01_tSNE.ipynb) |
| **Validación cruzada** | Dividir los datos en $k$ pliegues y rotar el de validación para estimar la generalización; el preprocesamiento debe reajustarse **dentro** de cada pliegue. | [M03 · Validación cruzada y GridSearch](../03%20-%20Metricas%20y%20Ajuste%20de%20Hiperparametros/02_Validacion_Cruzada_y_GridSearch.ipynb) |
| **Árbol de decisión y *Random Forest*** | Un **árbol** divide el espacio de forma recursiva reduciendo una impureza (Gini, entropía; CART). Un **bosque** promedia muchos árboles entrenados con remuestras *bootstrap* y submuestreo de variables, lo que **reduce la varianza**. | [M02 · Random Forests](../02%20-%20Arboles%20Bosques%20y%20Redes%20Neuronales/01_Random_Forests.ipynb) |

---

## 📑 Referencias Bibliográficas

Lista **consolidada y deduplicada** de las referencias citadas en los Módulos 00 a 09 (formato APA). Los **libros de `Machine Learning/Libros/`** se citan con los datos de editorial y año de su portada; **los demás se marcan *(citado de memoria, verificar)*** salvo los que se verificaron contra el capítulo de un libro del curso (Mnih et al., Williams, Bellman 1957a, Schaul et al., Varma y Simon, Efron y Tibshirani 1997, Irpan). **No se ha inventado ninguna referencia nueva**: todas aparecen en los módulos.

### 📕 Libros del curso (en `Machine Learning/Libros/`)

- Barua, T., Hiran, K. K., Jain, R. K. & Doshi, R. (2024). *Machine Learning with Python*. De Gruyter.
- Géron, A. (2025). *Hands-On Machine Learning with Scikit-Learn and PyTorch*. O'Reilly Media.
- Harrington, P. (2012). *Machine Learning in Action*. Manning.
- Hsieh, W. W. (2009). *Machine Learning Methods in the Environmental Sciences*. Cambridge University Press.
- Kunapuli, G. (2023). *Ensemble Methods for Machine Learning*. Manning.
- McMahon, A. P. (2023). *Machine Learning Engineering with Python* (2.ª ed.). Packt.
- Mueller, J. P. & Massaron, L. (2021). *Machine Learning For Dummies* (2.ª ed.). Wiley.
- Pote, S. (2023). *Machine Learning in Production*. BPB Online.
- Ramsay, A. & Ahmad, T. (2023). *Machine Learning for Emotion Analysis in Python*. Packt.
- Raschka, S. (2015). *Python Machine Learning*. Packt.
- Saleh, R. (2025). *Fundamentals of Robust Machine Learning*. Wiley.
- Simeone, O. (2023). *Machine Learning for Engineers*. Cambridge University Press.
- Vasques, X. (2024). *Machine Learning Theory and Applications*. Wiley.
- Weiß, S. (s. f.). *Machine Learning with Python* [archivo `Intro_To_Machine_Learning_with_PyTorch` en `Machine Learning/Libros/`]. (Año y editorial no figuran en el PDF).
- Winn, J. et al. (s. f.). *Model-Based Machine Learning*. Chapman & Hall/CRC. (Año y coautores citados de memoria, verificar; el PDF indica CRC Press).

### 📄 Libros y artículos citados en los módulos 00–09

- Agrawal, R., Imieliński, T. & Swami, A. (1993). Mining association rules between sets of items in large databases. *SIGMOD*. *(citado de memoria, verificar)*
- Agrawal, R. & Srikant, R. (1994). Fast algorithms for mining association rules. *VLDB*. *(citado de memoria, verificar)*
- Akiba, T., Sano, S., Yanase, T., Ohta, T. & Koyama, M. (2019). Optuna: a next-generation hyperparameter optimization framework. *KDD '19*. *(citado de memoria, verificar)*
- Alpaydin, E. (1999). Combined 5×2 cv F test for comparing supervised classification learning algorithms. *Neural Computation, 11*(8), 1885–1892. *(citado de memoria, verificar)*
- Ankerst, M., Breunig, M. M., Kriegel, H.-P. & Sander, J. (1999). OPTICS: ordering points to identify the clustering structure. *SIGMOD 1999*. *(citado de memoria, verificar)*
- Apley, D. W. & Zhu, J. (2020). Visualizing the effects of predictor variables in black box supervised learning models. *Journal of the Royal Statistical Society B, 82*(4). *(citado de memoria, verificar)*
- Arbelaitz, O. et al. (2013). An extensive comparative study of cluster validity indices. *Pattern Recognition, 46*(1), 243–256. *(citado de memoria, verificar)*
- Arlot, S. & Celisse, A. (2010). A survey of cross-validation procedures for model selection. *Statistics Surveys, 4*, 40–79. *(citado de memoria, verificar)*
- Arthur, D. & Vassilvitskii, S. (2007). k-means++: the advantages of careful seeding. *SODA 2007*, 1027–1035. *(citado de memoria, verificar)*
- Balasubramanian, M. & Schwartz, E. L. (2002). The Isomap algorithm and topological stability. *Science, 295*, 7. *(citado de memoria, verificar)*
- Bates, S., Hastie, T. & Tibshirani, R. (2023). Cross-validation: what does it estimate and how well does it do it? *Journal of the American Statistical Association*. *(citado de memoria, verificar)*
- Batista, G., Prati, R. & Monard, M. (2004). A study of the behavior of several methods for balancing machine learning training data. *SIGKDD Explorations, 6*(1). *(citado de memoria, verificar)*
- Bellman, R. (1957a). A Markovian decision process. *Journal of Mathematics and Mechanics, 6*(5), 679–684.
- Bellman, R. (1957b). *Dynamic Programming*. Princeton University Press. *(citado de memoria, verificar)*
- Bergstra, J., Bardenet, R., Bengio, Y. & Kégl, B. (2011). Algorithms for hyper-parameter optimization. *NeurIPS 24*. *(citado de memoria, verificar)*
- Bergstra, J. & Bengio, Y. (2012). Random search for hyper-parameter optimization. *Journal of Machine Learning Research, 13*, 281–305. *(citado de memoria, verificar)*
- Bernstein, M., de Silva, V., Langford, J. C. & Tenenbaum, J. B. (2000). *Graph approximations to geodesics on embedded manifolds* [informe técnico]. Stanford. *(citado de memoria, verificar)*
- Beyer, K., Goldstein, J., Ramakrishnan, R. & Shaft, U. (1999). When is "nearest neighbor" meaningful? *ICDT 1999*. *(citado de memoria, verificar)*
- Breck, E. et al. (2017). The ML test score: a rubric for ML production readiness and technical debt reduction. *IEEE Big Data*. *(citado de memoria, verificar)*
- Breiman, L. (1996a). Bagging predictors. *Machine Learning, 24*(2), 123–140. *(citado de memoria, verificar)*
- Breiman, L. (1996b). Stacked regressions. *Machine Learning, 24*, 49–64. *(citado de memoria, verificar)*
- Breiman, L., Friedman, J. H., Olshen, R. A. & Stone, C. J. (1984). *Classification and Regression Trees*. Wadsworth. *(citado de memoria, verificar)*
- Breiman, L. (2001). Random forests. *Machine Learning, 45*(1), 5–32. *(citado de memoria, verificar)*
- Caliński, T. & Harabasz, J. (1974). A dendrite method for cluster analysis. *Communications in Statistics, 3*(1), 1–27. *(citado de memoria, verificar)*
- Campello, R. J. G. B., Moulavi, D. & Sander, J. (2013). Density-based clustering based on hierarchical density estimates. *PAKDD 2013*. *(citado de memoria, verificar)*
- Carion, N. et al. (2020). End-to-end object detection with transformers (DETR). *ECCV*. *(citado de memoria, verificar)*
- Cawley, G. C. & Talbot, N. L. C. (2010). On over-fitting in model selection and subsequent selection bias in performance evaluation. *Journal of Machine Learning Research, 11*, 2079–2107. *(citado de memoria, verificar)*
- Chawla, N. V., Bowyer, K. W., Hall, L. O. & Kegelmeyer, W. P. (2002). SMOTE: synthetic minority over-sampling technique. *Journal of Artificial Intelligence Research, 16*, 321–357. *(citado de memoria, verificar)*
- Cox, D. R. (1958). The regression analysis of binary sequences. *Journal of the Royal Statistical Society B, 20*(2). *(citado de memoria, verificar)*
- Cybenko, G. (1989). Approximation by superpositions of a sigmoidal function. *Mathematics of Control, Signals and Systems, 2*. *(citado de memoria, verificar)*
- Dalal, N. & Triggs, B. (2005). Histograms of oriented gradients for human detection. *CVPR*. *(citado de memoria, verificar)*
- Davis, J. & Goadrich, M. (2006). The relationship between Precision-Recall and ROC curves. *Proceedings of the 23rd International Conference on Machine Learning (ICML 2006)*, 233–240. *(citado de memoria, verificar)*
- Deerwester, S. et al. (1990). Indexing by latent semantic analysis. *Journal of the American Society for Information Science, 41*(6), 391–407. *(citado de memoria, verificar)*
- Deng, J. et al. (2009). ImageNet: a large-scale hierarchical image database. *CVPR*. *(citado de memoria, verificar)*
- Devlin, J., Chang, M.-W., Lee, K. & Toutanova, K. (2019). BERT: pre-training of deep bidirectional transformers for language understanding. *NAACL*. *(citado de memoria, verificar)*
- Dietterich, T. G. (1998). Approximate statistical tests for comparing supervised classification learning algorithms. *Neural Computation, 10*(7), 1895–1923. *(citado de memoria, verificar)*
- Dijkstra, E. W. (1959). A note on two problems in connexion with graphs. *Numerische Mathematik, 1*, 269–271. *(citado de memoria, verificar)*
- Eckart, C. & Young, G. (1936). The approximation of one matrix by another of lower rank. *Psychometrika, 1*(3), 211–218. *(citado de memoria, verificar)*
- Efron, B., Hastie, T., Johnstone, I. & Tibshirani, R. (2004). Least angle regression. *Annals of Statistics, 32*(2). *(citado de memoria, verificar)*
- Efron, B. & Tibshirani, R. (1993). *An Introduction to the Bootstrap*. Chapman & Hall. *(citado de memoria, verificar)*
- Efron, B. & Tibshirani, R. (1997). Improvements on cross-validation: the .632+ bootstrap method. *Journal of the American Statistical Association, 92*, 548–560.
- Ester, M., Kriegel, H.-P., Sander, J. & Xu, X. (1996). A density-based algorithm for discovering clusters in large spatial databases with noise. *KDD-96*, 226–231. *(citado de memoria, verificar)*
- Everingham, M. et al. (2010). The PASCAL Visual Object Classes (VOC) challenge. *International Journal of Computer Vision, 88*(2), 303–338. *(citado de memoria, verificar)*
- Floyd, R. W. (1962). Algorithm 97: shortest path. *Communications of the ACM, 5*(6), 345. *(citado de memoria, verificar)*
- Friedman, J. H. (2001). Greedy function approximation: a gradient boosting machine. *Annals of Statistics, 29*(5). *(citado de memoria, verificar)*
- Frénay, B. & Verleysen, M. (2014). Classification in the presence of label noise: a survey. *IEEE Transactions on Neural Networks and Learning Systems, 25*(5). *(citado de memoria, verificar)*
- Funk, S. (2006). *Netflix update: try this at home* [entrada de blog]. *(citado de memoria, verificar)*
- Gebru, T. et al. (2021). Datasheets for datasets. *Communications of the ACM, 64*(12), 86–92. *(citado de memoria, verificar)*
- Girshick, R. et al. (2014). Rich feature hierarchies for accurate object detection and semantic segmentation (R-CNN). *CVPR*. *(citado de memoria, verificar)*
- Goldstein, A., Kapelner, A., Bleich, J. & Pitkin, E. (2015). Peeking inside the black box: visualizing statistical learning with plots of individual conditional expectation. *Journal of Computational and Graphical Statistics, 24*(1). *(citado de memoria, verificar)*
- Goodfellow, I., Bengio, Y. & Courville, A. (2016). *Deep Learning*. MIT Press. *(citado de memoria, verificar)*
- Gower, J. C. (1966). Some distance properties of latent root and vector methods used in multivariate analysis. *Biometrika, 53*, 325–338. *(citado de memoria, verificar)*
- Guo, C. et al. (2017). On calibration of modern neural networks. *ICML*. *(citado de memoria, verificar)*
- Halko, N., Martinsson, P.-G. & Tropp, J. A. (2011). Finding structure with randomness: probabilistic algorithms for constructing approximate matrix decompositions. *SIAM Review, 53*(2), 217–288. *(citado de memoria, verificar)*
- Han, H., Wang, W.-Y. & Mao, B.-H. (2005). Borderline-SMOTE. *ICIC*. *(citado de memoria, verificar)*
- Harper, F. M. & Konstan, J. A. (2015). The MovieLens datasets: history and context. *ACM Transactions on Interactive Intelligent Systems, 5*(4). *(citado de memoria, verificar)*
- Hastie, T., Tibshirani, R. & Friedman, J. (2009). *The Elements of Statistical Learning* (2.ª ed.). Springer. *(citado de memoria, verificar)*
- He, H., Bai, Y., Garcia, E. A. & Li, S. (2008). ADASYN: adaptive synthetic sampling approach for imbalanced learning. *IJCNN*. *(citado de memoria, verificar)*
- He, H. & Garcia, E. A. (2009). Learning from imbalanced data. *IEEE Transactions on Knowledge and Data Engineering, 21*(9). *(citado de memoria, verificar)*
- He, K., Zhang, X., Ren, S. & Sun, J. (2016). Deep residual learning for image recognition. *CVPR*. *(citado de memoria, verificar)*
- Henderson, P. et al. (2018). Deep reinforcement learning that matters. *AAAI*. *(citado de memoria, verificar)*
- Herlocker, J. L., Konstan, J. A., Terveen, L. G. & Riedl, J. T. (2004). Evaluating collaborative filtering recommender systems. *ACM Transactions on Information Systems, 22*(1), 5–53. *(citado de memoria, verificar)*
- Hinton, G. & Roweis, S. (2002). Stochastic neighbor embedding. *NIPS 15*. *(citado de memoria, verificar)*
- Hornik, K., Stinchcombe, M. & White, H. (1989). Multilayer feedforward networks are universal approximators. *Neural Networks, 2*(5). *(citado de memoria, verificar)*
- Howard, J. & Ruder, S. (2018). Universal language model fine-tuning for text classification. *ACL*. *(citado de memoria, verificar)*
- Huber, P. J. (1964). Robust estimation of a location parameter. *The Annals of Mathematical Statistics, 35*(1), 73–101. *(citado de memoria, verificar)*
- Hubert, L. & Arabie, P. (1985). Comparing partitions. *Journal of Classification, 2*, 193–218. *(citado de memoria, verificar)*
- Hu, E. et al. (2022). LoRA: low-rank adaptation of large language models. *ICLR*. *(citado de memoria, verificar)*
- Hu, Y., Koren, Y. & Volinsky, C. (2008). Collaborative filtering for implicit feedback datasets. *ICDM*. *(citado de memoria, verificar)*
- Hyndman, R. J. & Koehler, A. B. (2006). Another look at measures of forecast accuracy. *International Journal of Forecasting, 22*(4), 679–688. *(citado de memoria, verificar)*
- Irpan, A. (2018). *Deep Reinforcement Learning Doesn't Work Yet* [entrada de blog].
- Jain, A. K. (2010). Data clustering: 50 years beyond K-means. *Pattern Recognition Letters, 31*(8), 651–666. *(citado de memoria, verificar)*
- James, G., Witten, D., Hastie, T. & Tibshirani, R. *An Introduction to Statistical Learning*. Springer. (Año no indicado en los módulos; verificar la edición). *(citado de memoria, verificar)*
- Jamieson, K. & Talwalkar, A. (2016). Non-stochastic best arm identification and hyperparameter optimization. *AISTATS*. *(citado de memoria, verificar)*
- Jolliffe, I. T. (2002). *Principal Component Analysis* (2.ª ed.). Springer. *(citado de memoria, verificar)*
- Jones, D. R., Schonlau, M. & Welch, W. J. (1998). Efficient global optimization of expensive black-box functions. *Journal of Global Optimization, 13*, 455–492. *(citado de memoria, verificar)*
- Josse, J., Prost, N., Scornet, E. & Varoquaux, G. (2019). On the consistency of supervised learning with missing values. *arXiv:1902.06931*. *(citado de memoria, verificar)*
- Järvelin, K. & Kekäläinen, J. (2002). Cumulated gain-based evaluation of IR techniques. *ACM Transactions on Information Systems, 20*(4), 422–446. *(citado de memoria, verificar)*
- Jurafsky, D. & Martin, J. H. *Speech and Language Processing* (3.ª ed., borrador en línea). (Año de la versión consultada no indicado; capítulos citados de memoria, verificar). *(citado de memoria, verificar)*
- Kleinberg, J. (2002). An impossibility theorem for clustering. *NIPS 2002*. *(citado de memoria, verificar)*
- Kobak, D. & Berens, P. (2019). The art of using t-SNE for single-cell transcriptomics. *Nature Communications, 10*, 5416. *(citado de memoria, verificar)*
- Kobak, D. & Linderman, G. C. (2021). Initialization is critical for preserving global data structure in both t-SNE and UMAP. *Nature Biotechnology, 39*, 156–157. *(citado de memoria, verificar)*
- Kohavi, R. (1995). A study of cross-validation and bootstrap for accuracy estimation and model selection. *IJCAI-95*. *(citado de memoria, verificar)*
- Koren, Y., Bell, R. & Volinsky, C. (2009). Matrix factorization techniques for recommender systems. *IEEE Computer, 42*(8), 30–37. *(citado de memoria, verificar)*
- Krizhevsky, A., Sutskever, I. & Hinton, G. E. (2012). ImageNet classification with deep convolutional neural networks. *NeurIPS 25*. *(citado de memoria, verificar)*
- Kumar, A. et al. (2022). Fine-tuning can distort pretrained features and underperform out-of-distribution. *ICLR*. *(citado de memoria, verificar)*
- Kumar, I. E., Venkatasubramanian, S., Scheidegger, C. & Friedler, S. (2020). Problems with Shapley-value-based explanations as feature importance measures. *ICML*. *(citado de memoria, verificar)*
- Lance, G. N. & Williams, W. T. (1967). A general theory of classificatory sorting strategies: 1. Hierarchical systems. *The Computer Journal, 9*(4), 373–380. *(citado de memoria, verificar)*
- LeCun, Y., Bottou, L., Bengio, Y. & Haffner, P. (1998). Gradient-based learning applied to document recognition. *Proceedings of the IEEE, 86*(11), 2278–2324. *(citado de memoria, verificar)*
- Lemaître, G., Nogueira, F. & Aridas, C. K. (2017). Imbalanced-learn: a Python toolbox to tackle the curse of imbalanced datasets in machine learning. *Journal of Machine Learning Research, 18*(17). *(citado de memoria, verificar)*
- Levy, O. & Goldberg, Y. (2014). Neural word embedding as implicit matrix factorization. *NeurIPS 27*. *(citado de memoria, verificar)*
- Li, L., Jamieson, K., DeSalvo, G., Rostamizadeh, A. & Talwalkar, A. (2017). Hyperband: a novel bandit-based approach to hyperparameter optimization. *Journal of Machine Learning Research, 18*. *(citado de memoria, verificar)*
- Lin, T.-Y. et al. (2014). Microsoft COCO: common objects in context. *ECCV*. *(citado de memoria, verificar)*
- Lipton, Z. C. (2018). The mythos of model interpretability. *Queue, 16*(3). *(citado de memoria, verificar)*
- Lipton, Z., Wang, Y.-X. & Smola, A. (2018). Detecting and correcting for label shift with black box predictors. *ICML*. *(citado de memoria, verificar)*
- Little, R. J. A. & Rubin, D. B. (2019). *Statistical Analysis with Missing Data* (3.ª ed.). Wiley. *(citado de memoria, verificar)*
- Liu, W. et al. (2016). SSD: single shot multibox detector. *ECCV*. *(citado de memoria, verificar)*
- Lloyd, S. P. (1982). Least squares quantization in PCM. *IEEE Transactions on Information Theory, 28*(2), 129–137. *(citado de memoria, verificar)*
- Lundberg, S. M. & Lee, S.-I. (2017). A unified approach to interpreting model predictions. *NeurIPS 30*. *(citado de memoria, verificar)*
- López de Prado, M. (2018). *Advances in Financial Machine Learning*. Wiley. *(citado de memoria, verificar)*
- MacQueen, J. (1967). Some methods for classification and analysis of multivariate observations. *Proceedings of the 5th Berkeley Symposium*, vol. 1, 281–297. *(citado de memoria, verificar)*
- McCallum, A. & Nigam, K. (1998). A comparison of event models for Naive Bayes text classification. *AAAI Workshop*. *(citado de memoria, verificar)*
- McInnes, L., Healy, J. & Melville, J. (2018). UMAP: uniform manifold approximation and projection for dimension reduction. *arXiv:1802.03426*. *(citado de memoria, verificar)*
- Mikolov, T., Chen, K., Corrado, G. & Dean, J. (2013). Efficient estimation of word representations in vector space. *arXiv:1301.3781*. *(citado de memoria, verificar)*
- Minka, T. P. (2000). Automatic choice of dimensionality for PCA. *NIPS 2000*. *(citado de memoria, verificar)*
- Mitchell, M. et al. (2019). Model cards for model reporting. *FAT\* 2019 (Conference on Fairness, Accountability, and Transparency)*. *(citado de memoria, verificar)*
- Mitchell, T. M. (1997). *Machine Learning*. McGraw-Hill. *(citado de memoria, verificar)*
- Mnih, V. et al. (2016). Asynchronous methods for deep reinforcement learning. *(citado de memoria, verificar)*
- Mnih, V. et al. (2015). Human-level control through deep reinforcement learning. *Nature, 518*, 529–533.
- Mnih, V. et al. (2013). Playing Atari with deep reinforcement learning. *arXiv:1312.5602*.
- Molnar, C. *Interpretable Machine Learning* [libro en línea de acceso libre]. (Año de la edición consultada no indicado). *(citado de memoria, verificar)*
- Moreno-Torres, J. G. et al. (2012). A unifying view on dataset shift in classification. *Pattern Recognition, 45*(1). *(citado de memoria, verificar)*
- Moulavi, D., Jaskowiak, P. A., Campello, R. J. G. B., Zimek, A. & Sander, J. (2014). Density-based clustering validation. *Proceedings of the 2014 SIAM International Conference on Data Mining (SDM)*, 839–847. *(citado de memoria, verificar)*
- Müllner, D. (2011). Modern hierarchical, agglomerative clustering algorithms. *arXiv:1109.2378*. *(citado de memoria, verificar)*
- Nadeau, C. & Bengio, Y. (2003). Inference for the generalization error. *Machine Learning, 52*, 239–281. *(citado de memoria, verificar)*
- Niculescu-Mizil, A. & Caruana, R. (2005). Predicting good probabilities with supervised learning. *ICML*. *(citado de memoria, verificar)*
- Northcutt, C., Jiang, L. & Chuang, I. (2021). Confident learning: estimating uncertainty in dataset labels. *Journal of Artificial Intelligence Research, 70*. *(citado de memoria, verificar)*
- Pang, B. & Lee, L. (2008). Opinion mining and sentiment analysis. *Foundations and Trends in Information Retrieval, 2*(1–2), 1–135. *(citado de memoria, verificar)*
- Pan, S. J. & Yang, Q. (2010). A survey on transfer learning. *IEEE Transactions on Knowledge and Data Engineering, 22*(10), 1345–1359. *(citado de memoria, verificar)*
- Pariser, E. (2011). *The Filter Bubble*. Penguin. *(citado de memoria, verificar)*
- Platt, J. (1999). Probabilistic outputs for support vector machines and comparisons to regularized likelihood methods. *(citado de memoria, verificar)*
- Powers, D. M. W. (2011). Evaluation: from precision, recall and F-measure to ROC, informedness, markedness and correlation. *Journal of Machine Learning Technologies, 2*(1), 37–63. *(citado de memoria, verificar)*
- Quiñonero-Candela, J., Sugiyama, M., Schwaighofer, A. & Lawrence, N. D. (Eds.). (2009). *Dataset Shift in Machine Learning*. MIT Press. *(citado de memoria, verificar)*
- Raschka, S. (2018). Model evaluation, model selection, and algorithm selection in machine learning. *arXiv:1811.12808*. *(citado de memoria, verificar)*
- Rasmussen, C. E. & Williams, C. K. I. (2006). *Gaussian Processes for Machine Learning*. MIT Press. *(citado de memoria, verificar)*
- Redmon, J., Divvala, S., Girshick, R. & Farhadi, A. (2016). You only look once: unified, real-time object detection. *CVPR*. *(citado de memoria, verificar)*
- Ren, S., He, K., Girshick, R. & Sun, J. (2015). Faster R-CNN: towards real-time object detection with region proposal networks. *NeurIPS 28*. *(citado de memoria, verificar)*
- Resnick, P. et al. (1994). GroupLens: an open architecture for collaborative filtering of netnews. *CSCW*. *(citado de memoria, verificar)*
- Ribeiro, M. T., Singh, S. & Guestrin, C. (2016). "Why should I trust you?": explaining the predictions of any classifier. *KDD*. *(citado de memoria, verificar)*
- Rousseeuw, P. J. (1987). Silhouettes: a graphical aid to the interpretation and validation of cluster analysis. *Journal of Computational and Applied Mathematics, 20*, 53–65. *(citado de memoria, verificar)*
- Roweis, S. T. & Saul, L. K. (2000). Nonlinear dimensionality reduction by locally linear embedding. *Science, 290*(5500), 2323–2326. *(citado de memoria, verificar)*
- Rubin, D. B. (1976). Inference and missing data. *Biometrika, 63*(3), 581–592. *(citado de memoria, verificar)*
- Rubin, D. B. (1987). *Multiple Imputation for Nonresponse in Surveys*. Wiley. *(citado de memoria, verificar)*
- Rudin, C. (2019). Stop explaining black box models for high stakes decisions and use interpretable models instead. *Nature Machine Intelligence, 1*, 206–215. *(citado de memoria, verificar)*
- Rumelhart, D. E., Hinton, G. E. & Williams, R. J. (1986). Learning representations by back-propagating errors. *Nature, 323*, 533–536. *(citado de memoria, verificar)*
- Rummery, G. A. & Niranjan, M. (1994). *On-line Q-learning using connectionist systems* [informe técnico]. Universidad de Cambridge. *(citado de memoria, verificar)*
- Russell, S. & Norvig, P. (2020). *Artificial Intelligence: A Modern Approach* (4.ª ed.). Pearson. *(citado de memoria, verificar)*
- Saito, T. & Rehmsmeier, M. (2015). The precision-recall plot is more informative than the ROC plot when evaluating binary classifiers on imbalanced datasets. *PLoS ONE, 10*(3), e0118432. *(citado de memoria, verificar)*
- Salton, G. & Buckley, C. (1988). Term-weighting approaches in automatic text retrieval. *Information Processing & Management, 24*(5), 513–523. *(citado de memoria, verificar)*
- Sarwar, B., Karypis, G., Konstan, J. & Riedl, J. (2001). Item-based collaborative filtering recommendation algorithms. *WWW*. *(citado de memoria, verificar)*
- Schaul, T. et al. (2015). Prioritized experience replay. *arXiv:1511.05952*.
- Schölkopf, B., Smola, A. & Müller, K.-R. (1998). Nonlinear component analysis as a kernel eigenvalue problem. *Neural Computation, 10*(5), 1299–1319. *(citado de memoria, verificar)*
- Schubert, E., Sander, J., Ester, M., Kriegel, H.-P. & Xu, X. (2017). DBSCAN revisited, revisited: why and how you should (still) use DBSCAN. *ACM Transactions on Database Systems, 42*(3), art. 19. *(citado de memoria, verificar)*
- Schulman, J. et al. (2017). Proximal policy optimization algorithms. *arXiv:1707.06347*. *(citado de memoria, verificar)*
- Sculley, D. et al. (2015). Hidden technical debt in machine learning systems. *NeurIPS 28*. *(citado de memoria, verificar)*
- Sculley, D. (2010). Web-scale k-means clustering. *WWW 2010*, 1177–1178. *(citado de memoria, verificar)*
- Shahriari, B., Swersky, K., Wang, Z., Adams, R. P. & de Freitas, N. (2016). Taking the human out of the loop: a review of Bayesian optimization. *Proceedings of the IEEE, 104*(1), 148–175. *(citado de memoria, verificar)*
- Shapley, L. S. (1953). A value for n-person games. En *Contributions to the Theory of Games II*. *(citado de memoria, verificar)*
- Shimodaira, H. (2000). Improving predictive inference under covariate shift by weighting the log-likelihood function. *Journal of Statistical Planning and Inference, 90*(2), 227–244. *(citado de memoria, verificar)*
- Snoek, J., Larochelle, H. & Adams, R. P. (2012). Practical Bayesian optimization of machine learning algorithms. *NeurIPS 25*. *(citado de memoria, verificar)*
- Sokal, R. R. & Rohlf, F. J. (1962). The comparison of dendrograms by objective methods. *Taxon, 11*(2), 33–40. *(citado de memoria, verificar)*
- Srinivas, N. et al. (2010). Gaussian process optimization in the bandit setting. *ICML*. *(citado de memoria, verificar)*
- Steck, H. (2011). Item popularity and recommendation accuracy. *RecSys*. *(citado de memoria, verificar)*
- Strobl, C., Boulesteix, A.-L., Zeileis, A. & Hothorn, T. (2007). Bias in random forest variable importance measures. *BMC Bioinformatics, 8*, 25. *(citado de memoria, verificar)*
- Sundararajan, M., Taly, A. & Yan, Q. (2017). Axiomatic attribution for deep networks. *ICML*. *(citado de memoria, verificar)*
- Sutton, R. S. & Barto, A. G. (2018). *Reinforcement Learning: An Introduction* (2.ª ed.). MIT Press. *(citado de memoria, verificar)*
- Sutton, R. S. (1988). Learning to predict by the methods of temporal differences. *Machine Learning, 3*, 9–44. *(citado de memoria, verificar)*
- Sutton, R. S., McAllester, D., Singh, S. & Mansour, Y. (2000). Policy gradient methods for reinforcement learning with function approximation. *NIPS 12*. *(citado de memoria, verificar)*
- Tan, P.-N., Steinbach, M., Karpatne, A. & Kumar, V. (2018). *Introduction to Data Mining* (2.ª ed.). Pearson. *(citado de memoria, verificar)*
- Tenenbaum, J. B., de Silva, V. & Langford, J. C. (2000). A global geometric framework for nonlinear dimensionality reduction. *Science, 290*(5500), 2319–2323. *(citado de memoria, verificar)*
- Tipping, M. E. & Bishop, C. M. (1999). Probabilistic principal component analysis. *Journal of the Royal Statistical Society B, 61*(3), 611–622. *(citado de memoria, verificar)*
- Tomek, I. (1976). Two modifications of CNN. *IEEE Transactions on Systems, Man and Cybernetics*. *(citado de memoria, verificar)*
- Torgerson, W. S. (1952). Multidimensional scaling: I. Theory and method. *Psychometrika, 17*(4), 401–419. *(citado de memoria, verificar)*
- Troyanskaya, O. et al. (2001). Missing value estimation methods for DNA microarrays. *Bioinformatics, 17*(6), 520–525. *(citado de memoria, verificar)*
- Štrumbelj, E. & Kononenko, I. (2014). Explaining prediction models and individual predictions with feature contributions. *Knowledge and Information Systems, 41*. *(citado de memoria, verificar)*
- van Buuren, S. & Groothuis-Oudshoorn, K. (2011). mice: multivariate imputation by chained equations in R. *Journal of Statistical Software, 45*(3). *(citado de memoria, verificar)*
- van der Maaten, L. (2014). Accelerating t-SNE using tree-based algorithms. *Journal of Machine Learning Research, 15*, 3221–3245. *(citado de memoria, verificar)*
- van der Maaten, L. & Hinton, G. (2008). Visualizing data using t-SNE. *Journal of Machine Learning Research, 9*, 2579–2605. *(citado de memoria, verificar)*
- van Hasselt, H., Guez, A. & Silver, D. (2016). Deep reinforcement learning with double Q-learning. *AAAI-30*, 2094–2100. (Géron lo fecha en 2015; el año de las actas es 2016).
- van Rijsbergen, C. J. (1979). *Information Retrieval* (2.ª ed.). Butterworths. *(citado de memoria, verificar)*
- Vapnik, V. N. (1998). *Statistical Learning Theory*. Wiley. *(citado de memoria, verificar)*
- Varma, S. & Simon, R. (2006). Bias in error estimation when using cross-validation for model selection. *BMC Bioinformatics, 7*, 91.
- Vaswani, A. et al. (2017). Attention is all you need. *NeurIPS 30*. *(citado de memoria, verificar)*
- Venna, J. & Kaski, S. (2006). Local multidimensional scaling. *Neural Networks, 19*(6–7), 889–899. *(citado de memoria, verificar)*
- Vinh, N. X., Epps, J. & Bailey, J. (2010). Information theoretic measures for clusterings comparison: variants, properties, normalization and correction for chance. *Journal of Machine Learning Research, 11*, 2837–2854. *(citado de memoria, verificar)*
- Wang, Z. et al. (2016). Dueling network architectures for deep reinforcement learning.
- Ward, J. H. (1963). Hierarchical grouping to optimize an objective function. *Journal of the American Statistical Association, 58*(301), 236–244. *(citado de memoria, verificar)*
- Watkins, C. J. C. H. & Dayan, P. (1992). Q-learning. *Machine Learning, 8*, 279–292. *(citado de memoria, verificar)*
- Wattenberg, M., Viégas, F. & Johnson, I. (2016). How to use t-SNE effectively. *Distill*. *(citado de memoria, verificar)*
- Williams, R. J. (1992). Simple statistical gradient-following algorithms for connectionist reinforcement learning. *Machine Learning, 8*, 229–256.
- Wilson, D. L. (1972). Asymptotic properties of nearest neighbor rules using edited data. *IEEE Transactions on Systems, Man and Cybernetics*. *(citado de memoria, verificar)*
- Wolpert, D. H. (1992). Stacked generalization. *Neural Networks, 5*(2), 241–259. *(citado de memoria, verificar)*
- Yosinski, J., Clune, J., Bengio, Y. & Lipson, H. (2014). How transferable are features in deep neural networks? *NeurIPS 27*. *(citado de memoria, verificar)*
- Zhou, Y., Wilkinson, D., Schreiber, R. & Pan, R. (2008). Large-scale parallel collaborative filtering for the Netflix Prize. *AAIM*. *(citado de memoria, verificar)*

### 🔎 Obras mencionadas en el texto sin datos completos en los módulos

*Aparecen solo con autor y año en los cuadernos; **verifica** título y fuente antes de citarlas formalmente.*

- Aloise, D. et al. (2009) y Mahajan, M. et al. (2009): NP-dificultad de K-Means (Módulo 04). *(citado de memoria, verificar)*
- Amit, Y. & Geman, D. (1997) y Ho, T. K. (1995): raíces de los bosques aleatorios (Módulo 02). *(citado de memoria, verificar)*
- Chen, T. et al. (2020): SimCLR; y Devlin, J. et al. (2018): versión inicial de BERT (Módulo 00). *(citado de memoria, verificar)*
- Cortes, C. & Vapnik, V. (1995); Cover, T. & Hart, P. (1967); Freund, Y. & Schapire, R. (1997); Pedregosa, F. et al. (2011); Chen, T. & Guestrin, C. (2016): hitos de la historia del ML (Módulo 00). *(citado de memoria, verificar)*
- Efron, B. (1979) y Efron, B. (1983): el *bootstrap* y su uso en la estimación del error (Módulo 07). *(citado de memoria, verificar)*
- Fayyad, U., Piatetsky-Shapiro, G. & Smyth, P. (1996): proceso KDD (Módulo 00). *(citado de memoria, verificar)*
- Firth, J. R. (1957): hipótesis distribucional (Módulo 09, cuaderno 02). *(citado de memoria, verificar)*
- Glorot, X. & Bengio, Y. (2010) y He, K. et al. (2015): inicializaciones de pesos Glorot y He (Módulo 02). *(citado de memoria, verificar)*
- Grinsztajn, L. et al. (2022) y Shwartz-Ziv, R. & Armon, A. (2022): árboles frente a redes en datos tabulares (Módulo 02). *(citado de memoria, verificar)*
- Hornik, K. (1991): aproximación universal con redes (Módulo 02). *(citado de memoria, verificar)*
- Hyafil, L. & Rivest, R. L. (1976): hallar el árbol de decisión óptimo es NP-completo (Módulo 02). *(citado de memoria, verificar)*
- Jacobs, R. A. (1988): ganancias adaptativas, usadas en t-SNE (Módulo 05). *(citado de memoria, verificar)*
- Kaufman, L. & Rousseeuw, P. J. (1990): K-Medoids, DIANA y la lectura de la silueta (Módulo 04). *(citado de memoria, verificar)*
- Kingma, D. P. & Ba, J. (2015): Adam (Módulo 02). *(citado de memoria, verificar)*
- McCulloch, W. S. & Pitts, W. (1943); Rosenblatt, F. (1958); Minsky, M. & Papert, S. (1969); Novikoff, A. B. J. (1962): neurona artificial, perceptrón, XOR y teorema de convergencia (Módulos 00 y 02). *(citado de memoria, verificar)*
- Pearson, K. (1901) y Hotelling, H. (1933): orígenes del PCA (Módulo 05). *(citado de memoria, verificar)*
- Quinlan, J. R. (1986) y Quinlan, J. R. (1993): ID3 y C4.5 (Módulo 02). *(citado de memoria, verificar)*
- Samuel, A. L. (1959) y Silver, D. et al. (2016): damas con aprendizaje y AlphaGo; Watkins, C. J. C. H. (1989): Q-learning (Módulo 00). *(citado de memoria, verificar)*
- Srivastava, N. et al. (2014): *dropout* (Módulo 02). *(citado de memoria, verificar)*
- Strehl, A. & Ghosh, J. (2002): información mutua normalizada (Módulo 04). *(citado de memoria, verificar)*
- Turing, A. (1950): *Computing Machinery and Intelligence* (Módulo 00). *(citado de memoria, verificar)*
- Wolpert, D. H. (1996) y Wolpert, D. H. & Macready, W. G. (1997): teoremas *No Free Lunch* (Módulo 01). *(citado de memoria, verificar)*

---

<div align="center">
  <p style="font-size: 0.9em; color: #64748b;">
    © 2026 <b>Universidad Santo Tomás — Seccional Tunja</b><br>
    <i>Especialización en Ciencia de Datos | Asignatura: Machine Learning</i>
  </p>
</div>
