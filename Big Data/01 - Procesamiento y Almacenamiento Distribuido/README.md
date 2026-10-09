# Módulo 01: Procesamiento y Almacenamiento Distribuido 🏗️⚙️

<p align="center">
  <img src="https://img.shields.io/badge/Discipline-Big%20Data-ea580c?style=for-the-badge&logo=apachespark&logoColor=white" alt="Big Data"/>
  <img src="https://img.shields.io/badge/Topics-Procesamiento%20y%20Almacenamiento%20Distribuido-0ea5e9?style=for-the-badge" alt="Topics"/>
  <img src="https://img.shields.io/badge/Course-Big%20Data-6366f1?style=for-the-badge" alt="Course"/>
  <img src="https://img.shields.io/badge/Institution-USTA%20Tunja-1e3a8a?style=for-the-badge" alt="USTA"/>
</p>

Bienvenido al **Módulo 01**, el **segundo** de la asignatura **Big Data** de la *Especialización en Ciencia de Datos* de la **Universidad Santo Tomás — Seccional Tunja**.

---

## 🧭 ¿De qué trata este módulo?

Este módulo continúa el **Capítulo 1** del libro de la asignatura y corresponde a la sección **1.4 (*Procesamiento y almacenamiento distribuido*)**: **1.4.1** opciones de procesamiento (Hadoop, Spark, NoSQL y SQL); **1.4.2** MapReduce y sus limitaciones; y **1.4.3** *frameworks* distribuidos (HDFS, Spark y HBase). Tras el [Módulo 00](../00%20-%20Fundamentos%20de%20Big%20Data/README.md) (qué es el Big Data y cómo se ven y viven los datos), la pregunta es **¿con qué herramientas se guardan y se procesan los datos cuando ya no caben en una máquina, y qué se sacrifica en cada elección?**

El módulo **no** repite lo que ya existe en el repositorio: la arquitectura de **Apache Spark / PySpark**, el ETL, MLlib y el *streaming* están en [Data Mining, Módulo 07](../../Data%20Mining/07%20-%20Mineria%20de%20Datos%20con%20Big%20Data/README.md). Aquí el enfoque es el del libro: **entender por dentro cada pieza** con implementaciones **desde cero en Python** (cuatro almacenes NoSQL, una simulación del teorema CAP, un motor MapReduce con `multiprocessing`, un mini-HDFS, un mini-RDD y un mini-HBase) y **PySpark real en modo local** para contrastar. Como en el resto del repositorio, se **verifica con `assert`** dentro de cada cuaderno, con **semillas fijas** y **resultados reportados con honestidad**, incluidos los casos en que lo «más sofisticado» **no** gana (DuckDB y *pandas* le ganan a Spark local con datos que caben en memoria; NumPy en un solo proceso le gana por mucho a PageRank en MapReduce y en Spark; `cache()` ayuda poco con datos pequeños).

> 🗺️ **Mapa del curso (seis módulos):** **00** Fundamentos → **01** Procesamiento y Almacenamiento Distribuido *(este módulo)* → **02** *Data Warehousing* y *Data Lake* → **03** Analítica y Visualización → **04** Seguridad y Gobernanza → **05** Avances y Tendencias. El [README del curso](../README.md) se actualizará con el índice completo.

> 🔗 **Conexión con otros cursos:** la **velocidad** y los eventos en flujo (ventanas, latencia) vienen del [Módulo 00, cuaderno 00](../00%20-%20Fundamentos%20de%20Big%20Data/00_Introduccion_y_Las_V_del_Big_Data.ipynb); `sqlite3`, JSON y Parquet, del [Módulo 00, cuaderno 02](../00%20-%20Fundamentos%20de%20Big%20Data/02_Tipos_de_Datos_Estructurados_No_Estructurados_Semiestructurados.ipynb). Para **más Spark** (arquitectura, DataFrames, ETL distribuido, MLlib y *streaming*): [Data Mining, Módulo 07](../../Data%20Mining/07%20-%20Mineria%20de%20Datos%20con%20Big%20Data/README.md). El procesamiento de **flujos y grafos** a escala (PageRank con *Pregel*) se retoma en el Módulo 05.

> 🛠️ **Ponlo en práctica:** todos los cuadernos (estándar y *Para Dummies*) incluyen secciones **«🛠️ Práctica»**: una celda de código para que escribas tu solución y, justo debajo, la **solución guiada desplegable** (`💡 Haz clic aquí para ver la solución guiada...`). Inténtalo primero y abre la solución solo para comparar.

---

## 📚 Estructura Curricular del Módulo

### 🎓 1. Cuadernos Académicos Estándar:
1. [**00_Opciones_de_Procesamiento_Hadoop_Spark_NoSQL_SQL.ipynb**](00_Opciones_de_Procesamiento_Hadoop_Spark_NoSQL_SQL.ipynb): *Sección 1.4.1.* **Lotes frente a flujo** (el retraso medio de un lote de $W$ segundos es $W/2$, medido con 12 000 eventos). **Modelo relacional:** una transferencia **ACID** que viola un `CHECK` se revierte completa, y la misma consulta en **SQLite, DuckDB y *pandas*** da el mismo resultado. **Los cuatro tipos de almacén NoSQL desde cero:** **clave-valor** con expiración *TTL*, **documentos** con consultas por campo e índice secundario (menos documentos revisados), **familia de columnas** (tabla ancha y dispersa) y **grafo** con lista de adyacencia (el «amigo de amigo» verificado contra un autoJOIN en SQL y `networkx`). **ACID frente a BASE y el teorema CAP** con una **simulación de partición de red** que aísla una de tres réplicas: la política **CP** rechaza peticiones y no sirve datos viejos; la **AP** responde siempre, lee datos obsoletos y pierde escrituras al reconciliar; el quórum $R+W>N$ verificado por fuerza bruta. **Panorama de Hadoop y Spark** y **el mismo conteo/agregación en *pandas*, DuckDB, SQLite y Spark local** con tiempos medidos (solo conclusiones cualitativas) y una **matriz de decisión** («qué opción usar según el caso»). 2 prácticas (recomendar amistades con amigos en común; partición donde ninguna réplica tiene mayoría).
2. [**01_MapReduce_y_sus_Limitaciones.ipynb**](01_MapReduce_y_sus_Limitaciones.ipynb): *Sección 1.4.2.* **MapReduce desde cero** con `multiprocessing` (partición de la entrada, `map`, *combiner*, partición por hash estable, *shuffle*, `reduce`) y un **diagrama dibujado con `matplotlib` sobre una ejecución real**. Cuatro trabajos **verificados** contra `Counter`/*pandas*/fuerza bruta: **conteo de palabras** (el *combiner* reduce los pares barajados más de 10 veces), **promedio por clave** (el promedio de promedios es un error; el par (suma, cuenta) lo corrige), ***reduce-side join*** e **índice invertido**. **Sesgo de claves** con demostración cuantitativa (desbalance entre reductores, que **crece con el número de reductores**) y mitigación con **sal de claves**. **Limitaciones medidas:** el costo de **escribir a disco entre rondas** (PageRank encadenado en MapReduce, con `fsync`), los **algoritmos iterativos** (NumPy frente a MapReduce propio frente a **Spark con y sin `cache()`**, todos con el mismo resultado y verificados contra `networkx`), los **archivos pequeños** y la **latencia mínima** de un trabajo; y **cuándo MapReduce sigue siendo razonable**. 2 prácticas (temperatura máxima por estación con *combiner*; ¿cuántos reductores sirven?).
3. [**02_Frameworks_Distribuidos_HDFS_Spark_HBase.ipynb**](02_Frameworks_Distribuidos_HDFS_Spark_HBase.ipynb): *Sección 1.4.3.* **Mini-HDFS desde cero:** NameNode (mapa archivo → bloques → DataNodes), DataNodes en dos *racks*, tamaño de bloque, **factor de replicación 3** con conciencia de *racks*, **falla de un DataNode y de un *rack* completo con re-replicación** (con `assert` de que **ningún bloque queda con menos réplicas** que el factor), qué fracción de **fallas simultáneas** pierde datos según el factor, y el costo en metadatos del NameNode (bloques pequeños, archivos pequeños). **Spark:** arquitectura *driver*/ejecutores y DAG dibujados con `matplotlib`; un **mini-RDD perezoso** con linaje, etapas, *shuffle* reutilizado y `cache()` (contando cuántas veces corre cada función); y **PySpark local** con evaluación perezosa medida, **`explain()`** (un `Exchange` = un *shuffle*; *pushdown* del filtro a Parquet), particiones (`repartition` frente a `coalesce`) y `cache()` medido. **HBase desde cero:** filas **ordenadas** por clave, familias de columnas, **versiones por *timestamp*** con marcas de borrado, **escaneo por rango y prefijo**, **división de regiones** (sin huecos ni solapes) y los **puntos calientes**: claves monótonas frente a claves con sal (y el costo de salar). **Tabla comparativa** HDFS/Spark/HBase y cuándo se usa cada uno. 3 prácticas (dos DataNodes caen a la vez; etapas y caché con el mini-RDD; versiones en un rango de HBase).

---

### 📝 2. Taller Práctico Evaluativo (*Hands-On*):
* [**../homeworks/01_Procesamiento_Almacenamiento_Hands_On.ipynb**](../homeworks/01_Procesamiento_Almacenamiento_Hands_On.ipynb): Taller evaluativo que integra las opciones de procesamiento, MapReduce y los *frameworks* distribuidos en ejercicios prácticos *(el cuaderno se publica aparte)*.

---

### 🧸 3. Ruta Didáctica: Para Dummies:
Ubicada en la subcarpeta [`Para Dummies/`](Para%20Dummies/). Sin jerga ni fórmulas, con analogías cotidianas; **no requieren *Spark* ni Java**:
1. [**00_Opciones_Procesamiento_Dummies.ipynb**](Para%20Dummies/00_Opciones_Procesamiento_Dummies.ipynb): **El cuaderno, el casillero y el mapa de amigos**: el **cierre de caja** frente a la **caja registradora** (lote frente a flujo), un casillero con ticket que vence, carpetas con hojas distintas, el mapa de «amigos de amigos» y **dos sucursales con la línea cortada** (prudente frente a rápida: 0 ventas y 0 errores frente a 6 ventas y 1 sobreventa).
2. [**01_MapReduce_Dummies.ipynb**](Para%20Dummies/01_MapReduce_Dummies.ipynb): **Contar los votos en varias mesas**: cada mesa cuenta lo suyo, manda un acta y el centro suma (20 renglones en vez de 5 000 papeletas), **la ventanilla saturada** cuando un candidato tiene el 70 % de los votos y cómo se arregla, y **el costo del papel entre rondas** (modelo de juguete con supuestos explícitos).
3. [**02_Frameworks_Distribuidos_Dummies.ipynb**](Para%20Dummies/02_Frameworks_Distribuidos_Dummies.ipynb): **La biblioteca con copias en varias sedes**: tomos con tres copias y un catálogo que manda sacar fotocopias cuando cierra una sede (HDFS), una **receta perezosa** que no se ejecuta hasta que alguien pide el resultado y un **cuaderno de apuntes** (Spark y `cache`) y un **archivo de fichas ordenadas** donde un rango se lee saltando directo al inicio (HBase).

---

## 💾 Datos Utilizados

Todos los datos son **sintéticos con semilla fija, generados por código dentro de cada cuaderno**; **no hay descargas** y **no se necesita ninguna carpeta `data/`** (los archivos que se escriben —Parquet para Spark y DuckDB, archivos pequeños, resultados intermedios de MapReduce— se crean en un **directorio temporal** que se borra al terminar; las sesiones de Spark guardan su almacén también en ese directorio, así que el repositorio **no acumula** `spark-warehouse/`, `metastore_db/` ni `derby.log`).

| Conjunto | Origen | Dónde se usa |
|---|---|---|
| **Eventos con monto** (12 000 en 1 hora) | `default_rng(42)` uniforme + gamma | Cuaderno 00 (lotes frente a flujo) |
| **Cuentas bancarias** (3) y **pedidos** (60 000 / 400 000 con `RAPIDO = False`) | Tablas escritas a mano y `lognormal` | Cuaderno 00 (ACID y la misma consulta en tres motores) |
| **Catálogo de productos** (5 000 documentos de esquema variable), **lecturas de estaciones** (3 estaciones × 7 días) y **grafo de amistades** (60 personas) | `default_rng(42)` | Cuaderno 00 (almacenes NoSQL) |
| **Réplicas de un dato** (3, 300 operaciones) | `default_rng` con semilla fija | Cuaderno 00 (teorema CAP) |
| **Pedidos para el benchmark** (400 000 / 3 000 000 filas, 30 municipios) | `default_rng(42)`, escrito a Parquet temporal | Cuaderno 00 (pandas, DuckDB, SQLite, Spark) |
| **Texto con frecuencias tipo Zipf** (12 000 líneas), **lecturas de estaciones** (20 000), **clientes y pedidos**, **300 documentos** | `default_rng(42)` | Cuaderno 01 (cuatro trabajos MapReduce) |
| **Visitas** (80 000, 400 páginas con ley de potencias) y **grafo de 1 500 nodos** (≈ 10 000 aristas) | `default_rng(42)` / `default_rng(7)` | Cuaderno 01 (sesgo, PageRank) |
| **Archivos pequeños** (100 000 registros en 1 archivo o 2 000 archivos) | `default_rng(42)`, directorio temporal | Cuaderno 01 |
| **Archivos de «1 MB» y «200 KB»** (bytes aleatorios) en un clúster de 6 DataNodes y 2 *racks* | `default_rng(42).bytes` | Cuaderno 02 (mini-HDFS) |
| **Ventas** (300 000 filas, 8 regiones) para PySpark y **450 usuarios / 6 000 filas** para el mini-HBase | `default_rng(42)` | Cuaderno 02 |
| **Mini-ejemplos de juguete** (ventas del día, casilleros, carpetas, votos, sedes y tomos, fichas) | Tablas y listas escritas a mano o `random` con semilla | Los tres *Dummies* |

> ⚠️ **Los datos son inventados**: los resultados describen el **mecanismo**, **no** el rendimiento esperable en un caso real ni en un clúster. Los tiempos dependen de la máquina y de la carga; los cuadernos solo extraen **conclusiones cualitativas** de ellos. Los nombres de municipios de Boyacá solo ambientan los ejemplos.

## ⚙️ Requisitos

`numpy`, `pandas`, `matplotlib`, `networkx`, `duckdb`, `pyarrow` y **`pyspark`** (4.x, en modo local `local[2]`, con la interfaz web desactivada y 4 particiones de *shuffle*). **Spark necesita Java** (Spark 4 requiere JDK 17 o superior *(verificar)*); en Google Colab se instala con `!pip install -q pyspark duckdb` (los cuadernos traen esa línea comentada y deberás verificar que el JDK de Colab sea compatible). `sqlite3`, `multiprocessing`, `hashlib`, `bisect`, `pickle` y `itertools` son de la **biblioteca estándar**. Los tres **Dummies** usan solo `NumPy`/`pandas`/`matplotlib` y la biblioteca estándar: **no necesitan Spark ni Java**.

Se ejecutó de verdad, de arriba abajo y sin errores, con **Python 3.12**, **NumPy 2.5**, **pandas 2.3** (PySpark 4.2 avisa que no soporta bien *pandas* ≥ 3), **Matplotlib 3.11**, **networkx 3.7**, **DuckDB 1.5**, **PyArrow 25**, **PySpark 4.2.0** y **Java 25** en Linux (de verdad: con los *starters* de las prácticas tal cual —solo comentarios— y con una copia donde cada *starter* se reemplazó por su solución). *No se probó en Google Colab ni en Windows/macOS.* Tiempos aproximados en un equipo de escritorio con 8 núcleos (varían con la carga; el arranque de cada sesión de Spark local tarda unos 6–12 s): cuaderno 00 ≈ 30–55 s, 01 ≈ 45–90 s y 02 ≈ 35–65 s con `RAPIDO = True` (el extremo alto corresponde a una máquina muy cargada); los *Dummies* tardan 3–7 s. Notas de portabilidad: el motor MapReduce usa `multiprocessing` con el método **`fork`** (Linux y Colab); en Windows (donde no existe `fork`) el motor **ejecuta secuencialmente** con el mismo resultado; las funciones de usuario de los trabajos MapReduce deben ser funciones de nivel superior (`def`), no `lambda`.

---

<div align="center">
  <p style="font-size: 0.9em; color: #64748b;">
    © 2026 <b>Universidad Santo Tomás — Seccional Tunja</b><br>
    <i>Especialización en Ciencia de Datos | Asignatura: Big Data</i>
  </p>
</div>
