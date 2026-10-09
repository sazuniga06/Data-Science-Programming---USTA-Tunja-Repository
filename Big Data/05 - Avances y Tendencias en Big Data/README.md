# Módulo 05: Avances y Tendencias en Big Data 🌊🤖

<p align="center">
  <img src="https://img.shields.io/badge/Discipline-Big%20Data-ea580c?style=for-the-badge&logo=apachespark&logoColor=white" alt="Big Data"/>
  <img src="https://img.shields.io/badge/Topics-Avances%20y%20Tendencias-0ea5e9?style=for-the-badge" alt="Topics"/>
  <img src="https://img.shields.io/badge/Course-Big%20Data-6366f1?style=for-the-badge" alt="Course"/>
  <img src="https://img.shields.io/badge/Institution-USTA%20Tunja-1e3a8a?style=for-the-badge" alt="USTA"/>
</p>

Bienvenido al **Módulo 05**, el **sexto y último** de la asignatura **Big Data** de la *Especialización en Ciencia de Datos* de la **Universidad Santo Tomás — Seccional Tunja**. Este módulo **cierra el Capítulo 2 y todo el curso**.

---

## 🧭 ¿De qué trata este módulo?

Corresponde a la sección **2.5 (*Avances y tendencias*)** del libro de la asignatura: **2.5.1** procesamiento de flujos y de grafos, y **2.5.2** tendencias emergentes (analíticas empoderadas con IA y *blockchain*). Tras el [Módulo 04](../04%20-%20Seguridad%20y%20Gobernanza%20de%20Big%20Data/README.md) (cómo se protege y se gobierna el dato), la pregunta final es **¿hacia dónde se mueve el Big Data y qué hay de real detrás de cada promesa?**

Como en el resto del curso, **no se explica nada sin construirlo**: cada concepto se implementa **desde cero en Python**, se **verifica con `assert`** contra una referencia independiente (`pandas`, `networkx`, `scikit-learn`, Spark) y se **reporta con honestidad**, incluidos los casos en que **lo novedoso no gana** (la regla estadística simple y *Isolation Forest* se **complementan** y ninguna gana en todo; AutoML a veces **no supera** la línea base; el PSI **no ve** la deriva de concepto; con TF-IDF una pregunta con sinónimos no recupera nada; el aprendizaje federado con datos no IID **solo se resiente** con muchas épocas locales; un *hash* sin sal de un dato adivinable **se revierte en milisegundos**; y en un grafo que cabe en memoria, `networkx` le gana a cualquier motor distribuido).

> 🔗 **Para no repetir:** el *streaming* con PySpark (micro-lotes, detección de anomalías en ventanas, marcas de agua) ya existe en [Data Mining, Módulo 07, cuaderno 04](../../Data%20Mining/07%20-%20Mineria%20de%20Datos%20con%20Big%20Data/04_Streaming_y_Mineria_en_Tiempo_Real.ipynb); aquí **se enlaza** y se hace lo que allí no está: ventanas y marcas de agua **desde cero**, un **log tipo Kafka**, PageRank, **Pregel** y las tendencias de IA y *blockchain*.

> 🗺️ **Mapa del curso (seis módulos):** [00 Fundamentos](../00%20-%20Fundamentos%20de%20Big%20Data/README.md) → [01 Procesamiento y Almacenamiento Distribuido](../01%20-%20Procesamiento%20y%20Almacenamiento%20Distribuido/README.md) → [02 *Data Warehousing* y *Data Lake*](../02%20-%20Data%20Warehousing%20y%20Data%20Lake/README.md) → [03 Analítica y Visualización](../03%20-%20Analitica%20y%20Visualizacion%20en%20Big%20Data/README.md) → [04 Seguridad y Gobernanza](../04%20-%20Seguridad%20y%20Gobernanza%20de%20Big%20Data/README.md) → **05 Avances y Tendencias** *(este módulo)*.

> 🛠️ **Ponlo en práctica:** todos los cuadernos (estándar y *Para Dummies*) incluyen secciones **«🛠️ Práctica»**: una celda de código para que escribas tu solución y, justo debajo, la **solución guiada desplegable** (`💡 Haz clic aquí para ver la solución guiada...`). Inténtalo primero y abre la solución solo para comparar.

---

## 📚 Estructura Curricular del Módulo

### 🎓 1. Cuadernos Académicos Estándar:
1. [**00_Stream_Processing_y_Graph_Processing.ipynb**](00_Stream_Processing_y_Graph_Processing.ipynb): *Sección 2.5.1.* **Flujos:** tiempo de evento frente a tiempo de procesamiento (con un flujo sintético donde el 45 % de los eventos llega desordenado); ventanas ***tumbling***, ***sliding*** y **de sesión** desde cero (verificadas a mano y contra `pandas`); **marcas de agua** y datos tardíos con un motor propio que mide el compromiso **completitud frente a latencia** (con $L$ igual al retraso máximo el resultado es **exacto**); **semánticas de entrega** simuladas (*a lo sumo una vez* pierde, *al menos una vez* duplica, *al menos una vez + efecto idempotente* es exacta); un **log particionado tipo Kafka** desde cero (particiones, *offsets*, clave → partición, grupos de consumidores, reequilibrio al caer un miembro, repetición y *lag*); y **Spark Structured Streaming real** (fuente `rate` con sumidero en memoria y `query.stop()`; fuente de archivos con `availableNow`, **idéntica** a la implementación propia; marca de agua en modo `append`, que **no coincide fila a fila**). **Grafos:** **PageRank por iteración de potencias** desde cero (verificado contra `networkx.pagerank` a $10^{-9}$, con contracción de factor $\alpha$ y efecto de $\alpha$ en las iteraciones), el **modelo vertex-céntrico BSP de Pregel** desde cero (componentes conexas, caminos más cortos y PageRank, todos verificados contra `networkx`, con y sin combinador y con diagrama BSP) y **GraphX/GraphFrames** solo de forma conceptual. 2 prácticas (¿cuánto esperar para ser casi exactos?; propagar el mayor puntaje por componente con Pregel).
2. [**01_Tendencias_Emergentes_IA_y_Blockchain.ipynb**](01_Tendencias_Emergentes_IA_y_Blockchain.ipynb): *Sección 2.5.2.* **Analítica con IA:** *pipeline* de detección de anomalías (`StandardScaler` + `IsolationForest`) frente a una **z robusta** desde cero (cada una ve un tipo distinto de anomalía; su unión cubre ambos); **AutoML como búsqueda aleatoria** de *pipelines* de `scikit-learn` con validación cruzada **dentro** del *pipeline*, línea base, conjunto de prueba intocado y curva «mejor hasta ahora»; **monitoreo de deriva con el PSI** desde cero (simetría con la divergencia de Kullback-Leibler, deriva de covariables detectada antes del daño y **punto ciego ante la deriva de concepto**); **RAG** conceptual con un **recuperador TF-IDF desde cero idéntico a `TfidfVectorizer`** (sin llamar a ningún LLM ni a la red, y con su límite léxico); y **aprendizaje federado (FedAvg)** desde cero, **equivalente exacto** del gradiente centralizado con una época por ronda y comparado con IID, no IID y clientes aislados. ***Blockchain:*** cadena de *hashes*, **prueba de trabajo** (≈ $16^d$ intentos medidos), **árbol de Merkle** con pruebas de inclusión, **detección de manipulación** y costo de rehacer la cadena, su uso en **auditoría y gobernanza** y sus **límites** (rendimiento, energía, derecho al olvido, incluida la reversión por fuerza bruta de un *hash* sin sal). 2 prácticas (¿cuándo salta la alarma del PSI y cuándo se nota el daño?; manipular, detectar y rehacer una cadena).

---

### 📝 2. Taller Práctico Evaluativo (*Hands-On*):
* [**../homeworks/05_Streaming_Grafos_Tendencias_Hands_On.ipynb**](../homeworks/05_Streaming_Grafos_Tendencias_Hands_On.ipynb): Taller evaluativo que integra flujos, grafos y tendencias en ejercicios prácticos *(el cuaderno se publica aparte)*.

---

### 🧸 3. Ruta Didáctica: Para Dummies:
Ubicada en la subcarpeta [`Para Dummies/`](Para%20Dummies/). Sin jerga ni fórmulas, con analogías cotidianas; **no requieren *Spark* ni Java**:
1. [**00_Stream_y_Grafos_Dummies.ipynb**](Para%20Dummies/00_Stream_y_Grafos_Dummies.ipynb): **El buzón del pueblo y el chisme que se riega**: 12 cartas con sello que llegan desordenadas (cuánto esperar antes de cerrar cada hora: 8 de 12 pedidos sin esperar, 11 con media hora y los 12 solo con la espera completa), **quién es la persona más importante del pueblo** (la importancia se hereda: el Padre Luis, con solo 2 admiradores, supera con mucho a Beto porque uno de ellos es Rosa) y **el chisme por tandas** (3 tandas para llegar a las 6 personas, hablando solo con los vecinos).
2. [**01_Tendencias_IA_Blockchain_Dummies.ipynb**](Para%20Dummies/01_Tendencias_IA_Blockchain_Dummies.ipynb): **La báscula que se descalibra, tres colegios y un cuaderno con sellos**: dos alarmas distintas (bulto raro frente a promedio corrido), el promedio general de tres colegios **sin mover las notas** (el promedio pesado coincide con el real y el simple de promedios se equivoca) y un **cuaderno de actas con sellos encadenados** que delata la hoja alterada y obliga a rehacer las siguientes.

---

## 💾 Datos Utilizados

Todos los datos son **sintéticos con semilla fija, generados por código dentro de cada cuaderno**; **no hay descargas** y **no se necesita ninguna carpeta `data/`** (los archivos JSON del *streaming* con Spark se escriben en un **directorio temporal** que se borra al terminar; Spark guarda su almacén y sus *checkpoints* también ahí, así que el repositorio **no acumula** `spark-warehouse/`, `metastore_db/`, `derby.log` ni carpetas de *checkpoint*).

| Conjunto | Origen | Dónde se usa |
|---|---|---|
| **Flujo de lecturas** (3 000 eventos en 10 min, 6 estaciones; 12 000 con `RAPIDO = False`; 6 % con retraso de 20 a 90 s) | `default_rng(42)` | Cuaderno 00 (ventanas, marca de agua, entrega, Kafka, Spark) |
| **Grafo tipo web** (300 nodos, ≈ 870 aristas, 9 colgantes), **grafo de componentes** (aleatorio + camino + clique + aislados, pesos 1 a 9) y **grafo de 150 nodos sin colgantes** | enlace preferencial con `default_rng(7)`; `networkx` con semilla 3; `default_rng(11)` | Cuaderno 00 (PageRank, Pregel) |
| **5 000 pagos** con 75 anomalías de dos tipos | `default_rng(42)` | Cuaderno 01 (anomalías) |
| **Problema de clasificación** (1 500 filas, 20 variables) | `make_classification(random_state=42)` | Cuaderno 01 (AutoML) |
| **Semanas en producción** (4 000 + 8 × 2 000 filas) | `default_rng` con semillas fijas | Cuaderno 01 (PSI y deriva) |
| **14 documentos y 10 preguntas** (frases cortas escritas para el cuaderno) | texto escrito a mano | Cuaderno 01 (RAG con TF-IDF) |
| **4 000 + 2 000 filas** repartidas en 5 clientes (IID y no IID) | `default_rng(42)` | Cuaderno 01 (FedAvg) |
| **Transacciones de auditoría** (8, y 6 bloques de 4) y un **código de 5 dígitos** inventado | texto generado por código | Cuaderno 01 (Merkle, cadena, fuerza bruta) |
| **Mini-ejemplos de juguete** (12 cartas, 6 vecinos, pesadas de papa, 3 colegios, actas) | listas escritas a mano o `random` con semilla | Los dos *Dummies* |

> ⚠️ **Los datos son inventados**: los resultados describen el **mecanismo**, **no** el rendimiento esperable en un caso real. Los tiempos dependen de la máquina; los cuadernos solo extraen **conclusiones cualitativas** de ellos. Los nombres de personas y colegios solo ambientan los ejemplos.

## ⚙️ Requisitos

`numpy`, `pandas`, `matplotlib`, `networkx`, `scipy`, `scikit-learn` y, **solo en el cuaderno 00**, **`pyspark`** (4.x, en modo local `local[2]`, con la interfaz web desactivada). **Spark necesita Java** (Spark 4 requiere JDK 17 o superior *(verificar)*); en Google Colab se instala con `!pip install -q pyspark` (los cuadernos traen esa línea comentada y deberás verificar que el JDK de Colab sea compatible). `hashlib`, `random`, `statistics`, `math`, `collections` y `unicodedata` son de la **biblioteca estándar**. Los **dos *Dummies*** usan solo `matplotlib`, `pandas` y la biblioteca estándar: **no necesitan Spark ni Java**.

Se ejecutó de verdad, de arriba abajo y sin errores, con **Python 3.12**, **NumPy 2.5**, **pandas 2.3** (PySpark 4.2 avisa que no soporta bien *pandas* ≥ 3), **Matplotlib 3.11**, **networkx 3.7**, **SciPy 1.18**, **scikit-learn 1.9**, **PySpark 4.2.0** y **Java 25** en Linux (de verdad: con los *starters* de las prácticas tal cual —solo comentarios— y con una copia donde cada *starter* se reemplazó por su solución). *No se probó en Google Colab ni en Windows/macOS.* Tiempos aproximados en un equipo de escritorio con 8 núcleos (varían con la carga): cuaderno 00 ≈ 40–60 s con `RAPIDO = True` (el arranque de Spark local tarda unos 6–14 s y las consultas de flujo unos 20 s; la primera consulta espera hasta ver 4 ventanas), cuaderno 01 ≈ 17–20 s y los *Dummies* ≈ 3 s. Al detener la consulta con `query.stop()` Spark imprime mensajes de error del micro-lote que se cancela a propósito; no son una falla.

---

## 📚 Lecturas Complementarias

Cierre del **Capítulo 2** y de **todo el curso** (analítica, visualización, seguridad y gobernanza, *streaming*, grafos y tendencias). **Todas están citadas de memoria: verifica los datos de publicación (año, congreso o editorial, edición) antes de citarlas en un trabajo.**

1. Hutter, F., Kotthoff, L. & Vanschoren, J. (Eds.). (2019). *Automated Machine Learning: Methods, Systems, Challenges*. Springer. **Analítica:** fundamentos de AutoML y búsqueda de hiperparámetros (cuaderno 01) *(citado de memoria, verificar)*.
2. Knaflic, C. N. (2015). *Storytelling with Data: A Data Visualization Guide for Business Professionals*. Wiley. **Visualización:** contexto, elección del gráfico y narración (Módulo 03) *(citado de memoria, verificar)*.
3. Sweeney, L. (2002). *k-anonymity: a model for protecting privacy*. International Journal of Uncertainty, Fuzziness and Knowledge-Based Systems, 10(5). **Seguridad y gobernanza:** el modelo de anonimización que se estudia en el Módulo 04 *(citado de memoria, verificar)*.
4. Kleppmann, M. (2017). *Designing Data-Intensive Applications*. O'Reilly. **Flujos:** el capítulo sobre *stream processing* (tiempo de evento, ventanas, *logs* particionados, semánticas de entrega) es la lectura natural del cuaderno 00 *(citado de memoria, verificar)*.
5. Akidau, T. et al. (2015). *The Dataflow Model*. Proceedings of the VLDB Endowment. **Flujos:** formaliza tiempo de evento, ventanas y marcas de agua *(citado de memoria, verificar)*.
6. Malewicz, G. et al. (2010). *Pregel: A System for Large-Scale Graph Processing*. SIGMOD. **Grafos:** el modelo vertex-céntrico que se implementa en el cuaderno 00 *(citado de memoria, verificar)*.
7. McMahan, H. B. et al. (2017). *Communication-Efficient Learning of Deep Networks from Decentralized Data*. AISTATS. **Tendencias:** el artículo que introduce FedAvg (cuaderno 01) *(citado de memoria, verificar)*.
8. Nakamoto, S. (2008). *Bitcoin: A Peer-to-Peer Electronic Cash System*. **Tendencias:** el documento original de la cadena de bloques con prueba de trabajo *(citado de memoria, verificar)*.

> 📖 **En el repositorio:** *E-Commerce Big Data Mining and Analytics* (Cao, 2023; `Data Mining/Libros/`, Cap. 4, sección 4.3 *Graph Store*, y Cap. 5, sección 5.4 *Blockchain Technology*) y *Artificial Intelligence, Big Data, and Internet of Things for Sustainable Industry and Infrastructure Development* (Singh et al., 2026; `Introduccion a la Inteligencia Artificial/Libros/`, Cap. 2) se verificaron contra el índice del PDF y se citan en los *Recursos Recomendados* de los cuadernos.

---

## 📖 Glosario

Términos clave de **todo el curso**, con la definición breve y el módulo donde se estudia (el enlace lleva a la carpeta del módulo).

| Término | Definición breve | Módulo |
|---|---|---|
| **Las V del Big Data** | Características que hacen «grande» a un conjunto de datos: **volumen** (cantidad), **variedad** (formatos) y **velocidad** (ritmo de llegada); suele añadirse la **veracidad** (calidad y confianza) | [00](../00%20-%20Fundamentos%20de%20Big%20Data/) |
| **Datos estructurados, semiestructurados y no estructurados** | Con esquema fijo (tablas); con etiquetas pero sin esquema rígido (JSON, XML); y sin estructura predefinida (texto, imágenes, audio) | [00](../00%20-%20Fundamentos%20de%20Big%20Data/) |
| **Ciclo de vida de los datos** | Etapas por las que pasa un dato: generación, ingesta, almacenamiento, procesamiento, uso y archivo o eliminación | [00](../00%20-%20Fundamentos%20de%20Big%20Data/) |
| **Ley de Amdahl** | Límite de la aceleración al paralelizar: la parte **secuencial** del trabajo acota la mejora máxima, por muchos procesadores que se usen | [00](../00%20-%20Fundamentos%20de%20Big%20Data/) |
| **Formato columnar (Parquet)** | Formato de archivo que guarda los datos **por columnas**, con compresión y estadísticas: acelera las consultas analíticas que leen pocas columnas | [02](../02%20-%20Data%20Warehousing%20y%20Data%20Lake/) |
| **HDFS** | Sistema de archivos distribuido de Hadoop: parte los archivos en **bloques** y los **replica** en varios nodos; un *NameNode* guarda los metadatos y los *DataNodes* los bloques | [01](../01%20-%20Procesamiento%20y%20Almacenamiento%20Distribuido/) |
| **Factor de replicación** | Número de copias de cada bloque (típicamente 3), para tolerar la caída de nodos o de *racks* completos | [01](../01%20-%20Procesamiento%20y%20Almacenamiento%20Distribuido/) |
| **MapReduce** | Modelo de programación con dos funciones: `map` transforma registros en pares clave-valor y `reduce` agrega los valores de cada clave, con un *shuffle* entre ambas | [01](../01%20-%20Procesamiento%20y%20Almacenamiento%20Distribuido/) |
| ***Combiner*** | Un «mini-`reduce`» local que reduce la salida del `map` **antes** de moverla por la red; exige una operación asociativa y conmutativa | [01](../01%20-%20Procesamiento%20y%20Almacenamiento%20Distribuido/) |
| ***Shuffle*** | Reparto de los pares intermedios **por clave** entre los *reducers*; es el paso caro porque mueve datos por la red | [01](../01%20-%20Procesamiento%20y%20Almacenamiento%20Distribuido/) |
| **Evaluación perezosa (RDD)** | Spark solo construye un plan (con su **linaje**) y lo ejecuta cuando una acción pide un resultado; permite reutilizar y recomputar | [01](../01%20-%20Procesamiento%20y%20Almacenamiento%20Distribuido/) |
| **NoSQL** | Familia de almacenes no relacionales: clave-valor, documentos, familia de columnas y grafos; sacrifican garantías de SQL para escalar | [01](../01%20-%20Procesamiento%20y%20Almacenamiento%20Distribuido/) |
| **HBase** | Almacén de familia de columnas sobre HDFS: filas **ordenadas por clave**, versiones por *timestamp* y escaneos por rango | [01](../01%20-%20Procesamiento%20y%20Almacenamiento%20Distribuido/) |
| **Teorema CAP** | Ante una **partición de red**, un sistema distribuido debe elegir entre **consistencia** y **disponibilidad** | [01](../01%20-%20Procesamiento%20y%20Almacenamiento%20Distribuido/) |
| **ACID / BASE** | ACID: transacciones atómicas, consistentes, aisladas y durables. BASE: disponibilidad básica, estado «blando» y consistencia eventual | [01](../01%20-%20Procesamiento%20y%20Almacenamiento%20Distribuido/) |
| ***Data warehouse*** | Almacén de datos integrado, histórico y orientado a temas, con **esquema definido antes** de cargar y pensado para consultas analíticas | [02](../02%20-%20Data%20Warehousing%20y%20Data%20Lake/) |
| **Esquema estrella** | Modelo dimensional con una tabla de **hechos** central (medidas) rodeada de tablas de **dimensiones** (contexto) | [02](../02%20-%20Data%20Warehousing%20y%20Data%20Lake/) |
| **OLAP** | Procesamiento analítico en línea: consultas multidimensionales (cubo, *roll-up*, *drill-down*, *slice*) sobre datos históricos | [02](../02%20-%20Data%20Warehousing%20y%20Data%20Lake/) |
| **ETL** | Extraer, transformar y cargar: el proceso que lleva los datos de las fuentes al almacén, limpiándolos y conformándolos en el camino | [02](../02%20-%20Data%20Warehousing%20y%20Data%20Lake/) |
| ***Data lake*** | Repositorio de datos **crudos** en su formato original, de bajo costo, para múltiples usos futuros | [02](../02%20-%20Data%20Warehousing%20y%20Data%20Lake/) |
| ***Schema-on-read*** | El esquema se **aplica al leer** (típico del *data lake*), frente a *schema-on-write*, donde se impone al cargar (típico del *data warehouse*) | [02](../02%20-%20Data%20Warehousing%20y%20Data%20Lake/) |
| **Particionado** | Dividir una tabla o conjunto de archivos por el valor de una columna (p. ej. fecha) para que las consultas lean solo las particiones necesarias | [02](../02%20-%20Data%20Warehousing%20y%20Data%20Lake/) |
| **Metastore (Hive)** | Catálogo que guarda el esquema, las particiones y las rutas de las tablas sobre archivos de un *data lake* | [02](../02%20-%20Data%20Warehousing%20y%20Data%20Lake/) |
| ***Sketch*** | Estructura de datos probabilística de memoria pequeña que resume un flujo (conteo de frecuencias con *Count-Min*, elementos distintos con *HyperLogLog*) con error acotado | [03](../03%20-%20Analitica%20y%20Visualizacion%20en%20Big%20Data/) |
| **Storytelling con datos** | Comunicar un hallazgo con contexto, el gráfico adecuado, sin desorden y con una narración que lleva a una decisión | [03](../03%20-%20Analitica%20y%20Visualizacion%20en%20Big%20Data/) |
| ***Data leakage*** (fuga de datos) | Dos acepciones: **seguridad**, salida no autorizada de información; y **aprendizaje automático**, filtración de información del futuro o del objetivo al entrenamiento, que produce métricas optimistas | [04](../04%20-%20Seguridad%20y%20Gobernanza%20de%20Big%20Data/) |
| **k-anonimato** | Garantía de que cada registro es indistinguible de al menos otros $k-1$ respecto a sus cuasi-identificadores | [04](../04%20-%20Seguridad%20y%20Gobernanza%20de%20Big%20Data/) |
| **Privacidad diferencial** | Garantía formal de que el resultado de un análisis cambia muy poco si se incluye o no a una persona, típicamente añadiendo ruido calibrado | [04](../04%20-%20Seguridad%20y%20Gobernanza%20de%20Big%20Data/) |
| **RBAC** | Control de acceso basado en roles: los permisos se asignan a **roles** y los roles a **usuarios** | [04](../04%20-%20Seguridad%20y%20Gobernanza%20de%20Big%20Data/) |
| **Linaje de datos** | Registro del **origen** de un dato y de las transformaciones por las que pasó (trazabilidad) | [04](../04%20-%20Seguridad%20y%20Gobernanza%20de%20Big%20Data/) |
| **Gobernanza de datos** | Conjunto de políticas, roles y procesos (propiedad, responsabilidad, transparencia) que definen quién decide qué sobre los datos y cómo se controla su uso | [04](../04%20-%20Seguridad%20y%20Gobernanza%20de%20Big%20Data/) |
| **Ventana** (*tumbling*, *sliding*, de sesión) | Intervalo de tiempo en el que se agrupan los eventos de un flujo: fijo sin solape, fijo con solape, o delimitado por silencios | [05](./) |
| **Tiempo de evento / de procesamiento** | Cuándo **ocurrió** un dato frente a cuándo el sistema **lo procesa**; su diferencia (el retraso) hace que los flujos lleguen desordenados | [05](./) |
| ***Watermark*** (marca de agua) | Regla $\max t_e - L$ que decide cuándo cerrar una ventana; los eventos que llegan después se consideran **tardíos** (aquí, descartados) | [05](./) |
| **Log particionado (Kafka)** | Registro de solo anexar dividido en particiones con *offsets*; el orden es total solo dentro de cada partición y los grupos de consumidores se reparten las particiones | [05](./) |
| **PageRank** | Medida de importancia de un nodo en un grafo dirigido: se hereda de los nodos importantes que lo apuntan; se calcula por iteración de potencias | [05](./) |
| **Pregel (BSP)** | Modelo de procesamiento de grafos «piensa como un vértice»: superpasos separados por barreras, con mensajes entre vecinos y votación para detenerse | [05](./) |
| **Deriva de datos y PSI** | Cambio en la distribución de los datos de producción; el índice de estabilidad poblacional lo mide como una divergencia simetrizada entre cajones | [05](./) |
| **AutoML** | Automatización de la elección de *pipeline*, modelo e hiperparámetros, aquí como búsqueda aleatoria evaluada por validación cruzada | [05](./) |
| **RAG** | Recuperación aumentada por generación: recuperar fragmentos relevantes de una base de conocimiento y dárselos como contexto a un modelo de lenguaje | [05](./) |
| **Aprendizaje federado (FedAvg)** | Entrenar un modelo en varios clientes sin juntar sus datos: viajan los parámetros, que el servidor promedia ponderando por tamaño | [05](./) |
| ***Blockchain*** | Registro de solo anexar formado por bloques encadenados por *hashes* (con prueba de trabajo y árbol de Merkle en el caso clásico): la manipulación **se detecta** | [05](./) |

---

## 📑 Referencias Bibliográficas

Lista **consolidada y deduplicada** en formato APA de las obras **citadas de verdad** en los README y los cuadernos de los módulos 00 a 05 de `Big Data/` (se obtuvo con `grep` sobre las secciones *Recursos Recomendados* y *Lecturas Complementarias*; **no se añadió ninguna referencia nueva**). Las obras marcadas **«(citado de memoria, verificar)»** se citaron sin comprobarlas contra una fuente; las demás son libros disponibles en el repositorio cuyos capítulos se verificaron contra el índice del PDF. Donde el cuaderno original citó «et al.» o sin editorial, se conserva así: **completa los datos al verificar**.

Ackoff, R. L. (1989). From data to wisdom. *Journal of Applied Systems Analysis, 16*. *(citado de memoria, verificar)*

Akidau, T., Chernyak, S. & Lax, R. (2018). *Streaming systems*. O'Reilly. *(citado de memoria, verificar)*

Akidau, T. et al. (2015). The dataflow model. *Proceedings of the VLDB Endowment*. *(citado de memoria, verificar)*

Amdahl, G. M. (1967). Validity of the single processor approach to achieving large scale computing capabilities. *AFIPS Spring Joint Computer Conference*. *(citado de memoria, verificar)*

Anderson, R. (2020). *Security engineering* (3.ª ed.). Wiley. *(citado de memoria, verificar)*

Armbrust, M. et al. (2018). Structured streaming: A declarative API for real-time applications in Apache Spark. *SIGMOD*. *(citado de memoria, verificar)*

Armbrust, M., Ghodsi, A., Xin, R. & Zaharia, M. (2021). Lakehouse: A new generation of open platforms that unify data warehousing and advanced analytics. *CIDR 2021*. *(citado de memoria, verificar)*

Aumasson, J.-P. (2017). *Serious cryptography*. No Starch Press. *(citado de memoria, verificar)*

Bergstra, J. & Bengio, Y. (2012). Random search for hyper-parameter optimization. *Journal of Machine Learning Research*. *(citado de memoria, verificar)*

Brewer, E. (2000). *Towards robust distributed systems*. *(citado de memoria, verificar)*

Cairo, A. (2016). *The truthful art*. New Riders. *(citado de memoria, verificar)*

Cairo, A. (2019). *How charts lie*. W. W. Norton. *(citado de memoria, verificar)*

Cao, J. (2023). *E-commerce big data mining and analytics*. Springer.

Carr, D. B. et al. (1987). Scatterplot matrix techniques for large N. *Journal of the American Statistical Association, 82*(398). *(citado de memoria, verificar)*

Chambers, B. & Zaharia, M. (2018). *Spark: The definitive guide*. O'Reilly. *(citado de memoria, verificar)*

Chandola, V., Banerjee, A. & Kumar, V. (2009). Anomaly detection: A survey. *ACM Computing Surveys*. *(citado de memoria, verificar)*

Chang, F. et al. (2006). Bigtable: A distributed storage system for structured data. *OSDI*. *(citado de memoria, verificar)*

Codd, E. F. (1970). A relational model of data for large shared data banks. *Communications of the ACM, 13*(6). *(citado de memoria, verificar)*

Cormode, G. & Muthukrishnan, S. (2005). An improved data stream summary: The count-min sketch and its applications. *Journal of Algorithms, 55*(1). *(citado de memoria, verificar)*

DAMA International. (2017). *DAMA-DMBOK: Data management body of knowledge* (2.ª ed.). *(citado de memoria, verificar)*

Damji, J., Wenig, B., Das, T. & Lee, D. (2020). *Learning Spark* (2.ª ed.). O'Reilly. *(citado de memoria, verificar)*

Dave, A. et al. (2016). GraphFrames: An integrated API for mixing graph and relational queries. *GRADES*. *(citado de memoria, verificar)*

Dean, J. et al. (2012). Large scale distributed deep networks. *NeurIPS*. *(citado de memoria, verificar)*

Dean, J. & Ghemawat, S. (2004). MapReduce: Simplified data processing on large clusters. *OSDI*. *(citado de memoria, verificar)*

DeCandia, G. et al. (2007). Dynamo: Amazon's highly available key-value store. *(citado de memoria, verificar)*

Dehghani, Z. (2022). *Data mesh*. O'Reilly. *(citado de memoria, verificar)*

Dwork, C. & Roth, A. (2014). The algorithmic foundations of differential privacy. *Foundations and Trends in Theoretical Computer Science*. *(citado de memoria, verificar)*

Eryurek, E. et al. (2021). *Data governance: The definitive guide*. O'Reilly. *(citado de memoria, verificar)*

Fernandez Climent, E. (2024). *Securing the AI enterprise: DevOps, MLOps, and MLSecOps explained*.

Ferguson, N., Schneier, B. & Kohno, T. (2010). *Cryptography engineering*. Wiley. *(citado de memoria, verificar)*

Flajolet, P., Fusy, É., Gandouet, O. & Meunier, F. (2007). HyperLogLog: The analysis of a near-optimal cardinality estimation algorithm. *AofA*. *(citado de memoria, verificar)*

Fortino, A. (2022). *Data mining and predictive analytics for business decisions*. Mercury Learning.

Gama, J. et al. (2014). A survey on concept drift adaptation. *ACM Computing Surveys*. *(citado de memoria, verificar)*

George, L. (2011). *HBase: The definitive guide*. O'Reilly. *(citado de memoria, verificar)*

Géron, A. (2025). *Hands-on machine learning with Scikit-Learn and PyTorch*. O'Reilly.

Ghemawat, S., Gobioff, H. & Leung, S.-T. (2003). The Google file system. *SOSP*. *(citado de memoria, verificar)*

Gilbert, S. & Lynch, N. (2002). Brewer's conjecture and the feasibility of consistent, available, partition-tolerant web services. *(citado de memoria, verificar)*

Gonzalez, J. E. et al. (2014). GraphX: Graph processing in a distributed dataflow framework. *OSDI*. *(citado de memoria, verificar)*

Gorelick, M. & Ozsvald, I. (2025). *High performance Python* (3.ª ed.). O'Reilly.

Goyal, P. et al. (2017). Accurate, large minibatch SGD: Training ImageNet in 1 hour. *(citado de memoria, verificar)*

Gustafson, J. L. (1988). Reevaluating Amdahl's law. *Communications of the ACM*. *(citado de memoria, verificar)*

Han, J., Kamber, M. & Pei, J. (2011). *Data mining: Concepts and techniques* (3.ª ed.). Morgan Kaufmann. *(citado de memoria, verificar)*

Heule, M., Nunkesser, M. & Hall, A. (2013). HyperLogLog in practice (HLL++). *EDBT*. *(citado de memoria, verificar)*

Hutter, F., Kotthoff, L. & Vanschoren, J. (Eds.). (2019). *Automated machine learning: Methods, systems, challenges*. Springer. *(citado de memoria, verificar)*

Hyndman, R. J. & Athanasopoulos, G. (2021). *Forecasting: Principles and practice* (3.ª ed.). OTexts. *(citado de memoria, verificar)*

Inmon, W. H. (2005). *Building the data warehouse* (4.ª ed.). Wiley. *(citado de memoria, verificar)*

Jugel, U. et al. (2014). M4: A visualization-oriented time series data aggregation. *PVLDB, 7*(10). *(citado de memoria, verificar)*

Kairouz, P. et al. (2021). Advances and open problems in federated learning. *Foundations and Trends in Machine Learning*. *(citado de memoria, verificar)*

Kimball, R. & Ross, M. (2013). *The data warehouse toolkit: The definitive guide to dimensional modeling* (3.ª ed.). Wiley. *(citado de memoria, verificar)*

Kleppmann, M. (2017). *Designing data-intensive applications*. O'Reilly. *(citado de memoria, verificar)*

Knaflic, C. N. (2015). *Storytelling with data*. Wiley. *(citado de memoria, verificar)*

Kreps, J., Narkhede, N. & Rao, J. (2011). Kafka: A distributed messaging system for log processing. *NetDB*. *(citado de memoria, verificar)*

Laney, D. (2001). *3D data management: Controlling data volume, velocity, and variety*. META Group. *(citado de memoria, verificar)*

Leskovec, J., Rajaraman, A. & Ullman, J. D. (2020). *Mining of massive datasets* (3.ª ed.). Cambridge University Press. *(citado de memoria, verificar)*

Lewis, P. et al. (2020). Retrieval-augmented generation for knowledge-intensive NLP tasks. *NeurIPS*. *(citado de memoria, verificar)*

Lin, J. & Dyer, C. (2010). *Data-intensive text processing with MapReduce*. Morgan & Claypool. *(citado de memoria, verificar)*

Liu, F. T., Ting, K. M. & Zhou, Z.-H. (2008). Isolation forest. *ICDM*. *(citado de memoria, verificar)*

Malewicz, G. et al. (2010). Pregel: A system for large-scale graph processing. *SIGMOD*. *(citado de memoria, verificar)*

Manning, C. D., Raghavan, P. & Schütze, H. (2008). *Introduction to information retrieval*. Cambridge University Press. *(citado de memoria, verificar)*

Marwala, T. (2026). *The governance of artificial intelligence*. Morgan Kaufmann (Elsevier).

Mayer-Schönberger, V. & Cukier, K. (2013). *Big data: A revolution that will transform how we live, work, and think*. *(citado de memoria, verificar)*

McMahan, H. B. et al. (2017). Communication-efficient learning of deep networks from decentralized data. *AISTATS*. *(citado de memoria, verificar)*

McMahon, A. P. (2023). *Machine learning engineering with Python* (2.ª ed.). Packt.

McSherry, F., Isard, M. & Murray, D. (2015). Scalability! But at what COST? *HotOS*. *(citado de memoria, verificar)*

Meier, M. (2026). *Mastering Tableau 2026* (5.ª ed.). Packt.

Melnik, S. et al. (2010). Dremel: Interactive analysis of web-scale datasets. *VLDB*. *(citado de memoria, verificar)*

Milligan, J. N. (2025). *Learning Tableau 2025* (6.ª ed.). Packt.

Murray, S. (2017). *Interactive data visualization for the web* (2.ª ed.). O'Reilly. *(citado de memoria, verificar)*

Nakamoto, S. (2008). *Bitcoin: A peer-to-peer electronic cash system*. *(citado de memoria, verificar)*

Narayanan, A. et al. (2016). *Bitcoin and cryptocurrency technologies*. Princeton University Press. *(citado de memoria, verificar)*

O'Neil, C. (2016). *Weapons of math destruction*. Crown. *(citado de memoria, verificar)*

Page, L., Brin, S., Motwani, R. & Winograd, T. (1999). *The PageRank citation ranking: Bringing order to the web*. Stanford InfoLab. *(citado de memoria, verificar)*

Provost, F. & Fawcett, T. (2013). *Data science for business*. O'Reilly. *(citado de memoria, verificar)*

Rajput, N. S. & Bhatt, S. (2025). *Visual analytics using Tableau* (1.ª ed.). BPB.

Reis, J. & Housley, M. (2022). *Fundamentals of data engineering*. O'Reilly. *(citado de memoria, verificar)*

Sadalage, P. & Fowler, M. (2012). *NoSQL distilled*. Addison-Wesley. *(citado de memoria, verificar)*

Shostack, A. (2014). *Threat modeling: Designing for security*. Wiley. *(citado de memoria, verificar)*

Shvachko, K. et al. (2010). The Hadoop distributed file system. *MSST*. *(citado de memoria, verificar)*

Singh, R., Kumar, R. & Malhotra, R. K. (Eds.). (2026). *Artificial intelligence, big data, and Internet of Things for sustainable industry and infrastructure development*. Bentham Books.

Soh, J. & Singh, P. (2020). *Data science solutions on Azure*. Apress.

Superintendencia de Industria y Comercio. (s. f.). *Autoridad de protección de datos personales (Colombia)*. *(citado de memoria; consulta el texto oficial vigente)*

Sweeney, L. (2002). k-anonymity: A model for protecting privacy. *International Journal of Uncertainty, Fuzziness and Knowledge-Based Systems, 10*(5). *(citado de memoria, verificar)*

Thusoo, A. et al. (2009). Hive: A warehousing solution over a map-reduce framework. *Proceedings of the VLDB Endowment, 2*(2). *(citado de memoria, verificar)*

Tufte, E. R. (2001). *The visual display of quantitative information* (2.ª ed.). Graphics Press. *(citado de memoria, verificar)*

Valiant, L. G. (1990). A bridging model for parallel computation. *Communications of the ACM*. *(citado de memoria, verificar)*

VanderPlas, J. (2017). *Python data science handbook*. O'Reilly.

Venkatesan, N. (2025). *Architecting Power BI solutions in Microsoft Fabric*. Packt.

Vitter, J. S. (1985). Random sampling with a reservoir. *ACM Transactions on Mathematical Software, 11*(1). *(citado de memoria, verificar)*

Weinberger, K. et al. (2009). Feature hashing for large scale multitask learning. *ICML*. *(citado de memoria, verificar)*

White, T. (2015). *Hadoop: The definitive guide* (4.ª ed.). O'Reilly. *(citado de memoria, verificar)*

Wickham, H. (2010). A layered grammar of graphics. *Journal of Computational and Graphical Statistics, 19*(1). *(citado de memoria, verificar)*

Wilkinson, L. (2005). *The grammar of graphics* (2.ª ed.). Springer. *(citado de memoria, verificar)*

Wilkinson, M. D. et al. (2016). The FAIR guiding principles for scientific data management and stewardship. *Scientific Data, 3*. *(citado de memoria, verificar)*

Zaharia, M. et al. (2012). Resilient distributed datasets. *NSDI*. *(citado de memoria, verificar)*

*Normativa citada (consulta siempre el texto oficial vigente):* Ley 1581 de 2012 (Colombia), régimen general de protección de datos personales (*Habeas Data*), y sus decretos reglamentarios *(citado de memoria, verificar)*.

---

<div align="center">
  <p style="font-size: 0.9em; color: #64748b;">
    © 2026 <b>Universidad Santo Tomás — Seccional Tunja</b><br>
    <i>Especialización en Ciencia de Datos | Asignatura: Big Data</i>
  </p>
</div>
