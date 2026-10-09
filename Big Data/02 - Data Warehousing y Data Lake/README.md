# Módulo 02: Data Warehousing y Data Lake 🏬🌊

<p align="center">
  <img src="https://img.shields.io/badge/Discipline-Big%20Data-ea580c?style=for-the-badge&logo=apachespark&logoColor=white" alt="Big Data"/>
  <img src="https://img.shields.io/badge/Topics-Data%20Warehousing%20y%20Data%20Lake-0ea5e9?style=for-the-badge" alt="Topics"/>
  <img src="https://img.shields.io/badge/Course-Big%20Data-6366f1?style=for-the-badge" alt="Course"/>
  <img src="https://img.shields.io/badge/Institution-USTA%20Tunja-1e3a8a?style=for-the-badge" alt="USTA"/>
</p>

Bienvenido al **Módulo 02**, el **tercero** de la asignatura **Big Data** de la *Especialización en Ciencia de Datos* de la **Universidad Santo Tomás — Seccional Tunja**, y el que **cierra el Capítulo 1** del libro de la asignatura.

---

## 🧭 ¿De qué trata este módulo?

Este módulo corresponde a la **Sección 1.5** del libro: **1.5.1** *Data Warehousing* (OLAP, ETL y esquema estrella), **1.5.2** *Data Lake* (con Hive y Pig) y **1.5.3** *Comparación entre Data Warehouse y Data Lake*. Los módulos anteriores respondieron *qué es* el Big Data y *cómo se procesa y se almacena* en muchas máquinas; este responde **¿dónde y cómo se organiza el dato para analizarlo?**: en un **almacén** (esquema al escribir, modelo dimensional, calidad por construcción) o en un **lago** (dato crudo, esquema al leer, capas y catálogo), y **cuándo conviene cada uno**.

El módulo **no** repite lo que ya existe en el repositorio: *Apache Spark / PySpark* (arquitectura, ETL, MLlib, *streaming*) está en [Data Mining, Módulo 07](../../Data%20Mining/07%20-%20Mineria%20de%20Datos%20con%20Big%20Data/README.md); aquí **implementamos los conceptos desde cero en Python** (un ETL con reglas de calidad y cuarentena, una dimensión de variación lenta tipo 2, un catálogo/*metastore* con SQLite, un mini-Pig, una guía de decisión con modelo de costo) y usamos **Spark local solo para contrastar**. Como en el resto del repositorio, **todo se verifica con `assert`** dentro de cada cuaderno, con **semillas fijas** y **resultados reportados con honestidad**, incluidos los casos en que lo «más sofisticado» **no** gana (por ejemplo, en nuestra medición el Parquet de un lago le ganó en rapidez a la tabla del almacén, y con 36 mil filas el Python puro le gana a Spark).

> 🗺️ **Mapa del curso (seis módulos):** **00** Fundamentos → **01** Procesamiento y Almacenamiento Distribuido → **02** *Data Warehousing* y *Data Lake* *(este módulo, cierra el Capítulo 1)* → **03** Analítica y Visualización → **04** Seguridad y Gobernanza → **05** Avances y Tendencias. El [README del curso](../README.md) se actualizará con el índice completo.

> 🔗 **Conexión con otros cursos:** el almacenamiento columnar y el formato **Parquet** se midieron en [Módulo 00, cuaderno 02](../00%20-%20Fundamentos%20de%20Big%20Data/02_Tipos_de_Datos_Estructurados_No_Estructurados_Semiestructurados.ipynb); el **ciclo de vida** (zonas, cuarentena, retención) en [Módulo 00, cuaderno 03](../00%20-%20Fundamentos%20de%20Big%20Data/03_Ciclo_de_Vida_de_los_Datos.ipynb); el procesamiento distribuido (MapReduce, HDFS, Spark) en el [Módulo 01](../01%20-%20Procesamiento%20y%20Almacenamiento%20Distribuido/README.md); y la **gobernanza** de los datos se desarrolla en el Módulo 04 de este curso.

> 🛠️ **Ponlo en práctica:** todos los cuadernos (estándar y *Para Dummies*) incluyen secciones **«🛠️ Práctica»**: una celda de código para que escribas tu solución y, justo debajo, la **solución guiada desplegable** (`💡 Haz clic aquí para ver la solución guiada...`). Inténtalo primero y abre la solución solo para comparar.

---

## 📚 Estructura Curricular del Módulo

### 🎓 1. Cuadernos Académicos Estándar:
1. [**00_Data_Warehousing_OLAP_ETL_y_Esquema_Estrella.ipynb**](00_Data_Warehousing_OLAP_ETL_y_Esquema_Estrella.ipynb): *Sección 1.5.1.* **OLTP frente a OLAP** y las cuatro características de un DW; **modelado dimensional** (proceso, granularidad, dimensiones, hechos, claves sustitutas, dimensión degenerada) con un **diagrama dibujado con `matplotlib`** (estrella frente a copo de nieve). **Cuatro «sistemas fuente» simulados** (POS en CSV, catálogo y tiendas del ERP, clientes y novedades del CRM en JSON) con **defectos sembrados a propósito**; un **ETL completo** (*extract*, *transform*, *load*) que **corrige** lo inequívoco (formatos de fecha, espacios, precio vacío), **rechaza a cuarentena con su motivo** lo demás y verifica la **conservación de filas** (4 060 = 3 928 + 132) y que **cada regla encuentra exactamente lo sembrado**. Esquema estrella en **DuckDB** (llaves, `CHECK`, miembro «No identificado») y una **dimensión de variación lenta tipo 2 (SCD2)** implementada y verificada con `assert` (una versión actual por cliente, vigencias contiguas, novedades sin cambio que no crean versión, hechos que apuntan a la **versión vigente en la fecha de la venta**) y contrastada con el **tipo 1**, que reescribe el pasado (mismo total, distinto reparto por ciudad). **Estrella frente a copo de nieve** con el mismo resultado y las uniones, el texto repetido y el tiempo medidos. **Operaciones OLAP** (*roll-up*, *drill-down*, *slice*, *dice*, *pivot*, `ROLLUP` y `CUBE` con `GROUPING()`) en SQL y en pandas, **verificadas entre sí**, más una conciliación independiente contra los datos limpios. 2 prácticas (un cliente pasa a «Premium»: SCD2; dados y pivote del segundo semestre).
2. [**01_Data_Lake_Hive_y_Pig.ipynb**](01_Data_Lake_Hive_y_Pig.ipynb): *Sección 1.5.2.* **Qué es un lago** y sus **tres capas** (cruda/bronce, curada/plata, de negocio/oro) dibujadas con `matplotlib`. Un lago **real** sobre un directorio temporal: ≈ 36 500 líneas JSON de pedidos (ficticios) en 53 lotes semanales con defectos sembrados (líneas malformadas, duplicados, valores no positivos, tipos que cambian, un **campo nuevo desde abril**) → **Parquet particionado estilo Hive** (`anio=2025/mes=03/`, 62 archivos en 12 particiones, el JSON pesa ≈ 6 veces más) → tablas de **oro**; conservación de filas y oro que cuadra con plata. **Esquema en lectura:** el mismo crudo leído con esquemas distintos, un lector antiguo que no se rompe con la columna nueva y la inferencia de **DuckDB** (que trata de otra manera las líneas malformadas y deduce `cantidad` como texto). **Catálogo/*metastore* desde cero con SQLite** (`crear_tabla`, `reparar` ≈ `MSCK REPAIR TABLE`, `particiones`, `archivos`, `plan`) y **poda de particiones medida** (6 de 62 archivos para `mes = 3`, mismo resultado) más el **problema de los archivos pequeños** (compactación). **Spark SQL** (local, con `spark.stop()`): descubre **las mismas 12 particiones** y la misma consulta con función de ventana da el **mismo resultado en Spark SQL, DuckDB y pandas**; el plan de ejecución muestra `PartitionFilters` solo si el filtro es por una columna de partición. **Flujo estilo Pig Latin** (`LOAD`, `FILTER`, `GROUP`, `FOREACH ... GENERATE`, `ORDER`, `STORE`) como mini-Pig en Python y su **equivalente en Spark**, con resultados idénticos, y una nota honesta sobre por qué Pig y Hive sobre MapReduce son **herramientas heredadas** frente a Spark SQL (el estado actual de cada proyecto se marca «verificar»). 2 prácticas (un lector «geo» con esquema en lectura; un flujo Pig de los 3 productos con más unidades).
3. [**02_Comparacion_Data_Warehouse_vs_Data_Lake.ipynb**](02_Comparacion_Data_Warehouse_vs_Data_Lake.ipynb): *Sección 1.5.3 (cierra el Capítulo 1).* **Tabla comparativa rigurosa** (esquema al escribir/leer, tipos de datos, ETL frente a ELT, calidad, usuarios, costo, gobernanza, rendimiento, agilidad, casos típicos) con cuatro advertencias de rigor. **Experimento con el mismo conjunto de datos servido de tres formas** (tabla con esquema estricto en DuckDB, lago crudo en JSON y lago curado en Parquet): **una consulta analítica fija** con respuesta idéntica y tiempos medidos (el JSON crudo es varias veces más lento; el Parquet curado fue tan rápido o más que la tabla: **el factor es el formato y el motor, no la etiqueta**), la **rigidez** (el almacén no puede responder por un campo no modelado y rechaza un dato inválido; el lago responde y lo acepta) y el **costo de cambio** al llegar **columnas inesperadas** y un **conflicto de tipos** (bitácora paso a paso: el `INSERT` «que funciona» **pierde 3 columnas en silencio**; en el lago el costo se traslada al lector con `union_by_name` y `TRY_CAST`). **Lakehouse** (Delta Lake, Iceberg y Hudi, **solo conceptual**) con un diagrama de las tres arquitecturas. **Guía de decisión** (reglas heurísticas) y **modelo de costo** con **supuestos explícitos y ficticios**, **punto de equilibrio** analítico verificado numéricamente. **Pantano de datos:** un lago desordenado sintético se **mide** (catálogo, metadatos, duplicados por *hash*, archivos viejos) y se **remedia** con controles en código (`NOT NULL`, `CHECK`, deduplicación, archivado). 2 prácticas (un lote con columna sorpresa; cómo mueven el equilibrio el volumen y los cambios de esquema).

---

### 📝 2. Taller Práctico Evaluativo (*Hands-On*):
* [**../homeworks/02_Data_Warehouse_Data_Lake_Hands_On.ipynb**](../homeworks/02_Data_Warehouse_Data_Lake_Hands_On.ipynb): Taller evaluativo que integra el esquema estrella, el ETL, el lago y la comparación en ejercicios prácticos *(el cuaderno se publica aparte)*.

---

### 🧸 3. Ruta Didáctica: Para Dummies:
Ubicada en la subcarpeta [`Para Dummies/`](Para%20Dummies/). Sin jerga ni fórmulas, con analogías cotidianas; **no requieren *Spark* ni Java**:
1. [**00_Data_Warehousing_Dummies.ipynb**](Para%20Dummies/00_Data_Warehousing_Dummies.ipynb): **El libro de cuentas de doña Rosa**: del cuaderno de la caja al libro limpio (un ETL con **recibo** 11 = 8 + 3), las **fichas** y los renglones de ventas con códigos (la estrella) y el **cubo** (resumir, detallar, rebanar y pivotar sin que el total cambie).
2. [**01_Data_Lake_Dummies.ipynb**](Para%20Dummies/01_Data_Lake_Dummies.ipynb): **El centro de acopio de papa**: las tres zonas (recibo, lavado y empaque; 124 = 122 + 2), los **estantes rotulados por mes** con «el cuaderno del bodeguero» (misma respuesta abriendo 10 de 30 archivos) y una **receta estilo Pig**.
3. [**02_DW_vs_Lake_Dummies.ipynb**](Para%20Dummies/02_DW_vs_Lake_Dummies.ipynb): **Tienda ordenada o plaza de mercado**: qué hace cada una con un dato inesperado y uno malo, por qué **dos lectores obtienen dos cifras** de los mismos datos, el **pantano** sin etiquetas y **tres preguntas** para decidir.

---

## 💾 Datos Utilizados

Todos los datos son **sintéticos con semilla fija, generados por código dentro de cada cuaderno**; **no hay descargas** y **no se necesita ninguna carpeta `data/`** (los archivos que se escriben —CSV y JSON de las fuentes, Parquet particionado, catálogo SQLite, salidas de Pig— se crean en un **directorio temporal** que se borra al cerrar el núcleo; así cada cuaderno es autocontenido en Google Colab y el repositorio no acumula archivos).

| Conjunto | Origen | Dónde se usa |
|---|---|---|
| **Sistemas fuente** (4 060 líneas POS con 10 tipos de defectos, 60 productos, 8 tiendas, 150 clientes + 8 repetidos, 22 novedades del CRM) | `generar_fuentes(semilla=2025)` | Cuaderno 00 |
| **Pedidos de «Mercado Boyacá»** (≈ 36 500 líneas JSON en 53 lotes semanales, 10 productos, 8 municipios) | `generar_bronce(semilla=2025)` (ficticio) | Cuaderno 01 |
| **Ventas** (300 000 con `RAPIDO = True`, 1 500 000 con `False`; 60 productos, 8 tiendas, campo extra `canal`) y **lotes nuevos** con columnas inesperadas | `generar_ventas(semilla=7)` | Cuaderno 02 |
| **Lago desordenado** (36 archivos: 30 distintos + 6 copias exactas, 14 «viejos») | `generar_pantano(semilla=11)` | Cuaderno 02 |
| **Mini-ejemplos de juguete** (cuaderno de caja de doña Rosa, 30 archivos de acopio de papa, pedidos de la tienda y la plaza, 10 puestos) | Tablas y listas escritas a mano o con `default_rng(5)` | Los tres *Dummies* |

> ⚠️ **Los datos son inventados** (nombres, documentos, precios, productos y municipios): los resultados describen el **mecanismo**, **no** el rendimiento esperable en un caso real. Los **costos del modelo** del cuaderno 02 son **ficticios** (unidades monetarias): lo que importa es su **estructura**, no su valor. Los nombres de municipios de Boyacá solo ambientan los ejemplos.

## ⚙️ Requisitos

`numpy`, `pandas`, `matplotlib`, `pyarrow` y `duckdb` en los cuadernos 00 y 02; el cuaderno 01 añade **`pyspark`** (modo local, `local[2]`) y requiere **Java** (en Google Colab ya está disponible: `# !pip install -q pyspark` y `# !pip install -q duckdb` van comentados al inicio por si faltan). `sqlite3`, `json`, `csv`, `hashlib`, `tempfile`, `shutil` y `datetime` son de la **biblioteca estándar**. **No se necesita red** salvo para instalar paquetes. Los tres **Dummies** usan solo `NumPy`, `pandas` y `matplotlib` (sin Spark ni Java).

Se ejecutó de verdad, de arriba abajo y sin errores, con **Python 3.12**, **NumPy 2.5**, **pandas 2.3**, **Matplotlib 3.11**, **PyArrow 25**, **DuckDB 1.5**, **PySpark 4.2** y **OpenJDK 25** en Linux (de verdad: con los *starters* de las prácticas tal cual —solo comentarios— y con una copia donde cada *starter* se reemplazó por su solución). *No se probó en Google Colab ni en Windows/macOS.* **PySpark 4.2 avisa que no soporta bien pandas ≥ 3**; los cuadernos usan `collect()` (no `toPandas`) y se verificaron con pandas 2.3. Tiempos aproximados en un equipo de escritorio **compartido y con carga alta** (varían; en un equipo libre serán menores): cuaderno 00 ≈ 7–10 s, 01 ≈ 55–65 s (de los cuales ≈ 40 s son de *Spark*: arranque de la JVM, descubrimiento de particiones y la consulta con ventana; la sesión se detiene al final de cada sección), 02 ≈ 14–33 s con `RAPIDO = True` (≈ 32 s con `RAPIDO = False`, 1 500 000 ventas) y los *Dummies* 3–5 s. Notas de portabilidad: DuckDB y Spark **tratan distinto** los nombres de carpeta como `mes=03` (DuckDB conserva `'03'` como texto, Spark lo infiere entero) y las líneas JSON malformadas; **el cuaderno lo convierte o lo mide explícitamente**. Los mensajes de error que se imprimen (`Binder Error`, etc.) pueden variar de redacción entre versiones de DuckDB.

---

## 📚 Lecturas Complementarias

Cierre del **Capítulo 1** (*Big Data, almacenamiento y procesamiento distribuido, data warehousing y data lakes*). Para profundizar en lo visto desde los módulos 00 a 02. **Todas están citadas de memoria: verifica los datos de publicación (año, congreso o editorial, edición) antes de citarlas en un trabajo.**

1. Dean, J. & Ghemawat, S. (2004). *MapReduce: Simplified Data Processing on Large Clusters*. OSDI '04 (versión resumida en *Communications of the ACM*, 2008). **El modelo de programación que dio origen a Hadoop** y a los lenguajes de alto nivel como Pig y Hive *(citado de memoria, verificar)*.
2. Ghemawat, S., Gobioff, H. & Leung, S.-T. (2003). *The Google File System*. SOSP '03. **Diseño del sistema de archivos distribuido** que inspiró a HDFS (Módulo 01) *(citado de memoria, verificar)*.
3. Chang, F. et al. (2006). *Bigtable: A Distributed Storage System for Structured Data*. OSDI '06. **Almacenamiento distribuido de columnas anchas**, antecedente de HBase *(citado de memoria, verificar)*.
4. Kimball, R. & Ross, M. (2013). *The Data Warehouse Toolkit: The Definitive Guide to Dimensional Modeling* (3.ª ed.). Wiley. **La referencia del esquema estrella, las dimensiones de variación lenta y el ETL** (cuaderno 00) *(citado de memoria, verificar)*.
5. Inmon, W. H. (2005). *Building the Data Warehouse* (4.ª ed.). Wiley. **La definición clásica de almacén de datos** y la arquitectura corporativa normalizada *(citado de memoria, verificar)*.
6. Kleppmann, M. (2017). *Designing Data-Intensive Applications*. O'Reilly. **OLTP frente a OLAP, formatos de codificación y evolución de esquemas, procesamiento por lotes y en flujo**: lectura transversal a todo el capítulo *(citado de memoria, verificar)*.
7. Thusoo, A. et al. (2009). *Hive — A Warehousing Solution Over a Map-Reduce Framework*. Proceedings of the VLDB Endowment, 2(2). **El origen de Hive y de su metastore** (cuaderno 01) *(citado de memoria, verificar)*.
8. Armbrust, M., Ghodsi, A., Xin, R. & Zaharia, M. (2021). *Lakehouse: A New Generation of Open Platforms that Unify Data Warehousing and Advanced Analytics*. CIDR 2021. **La propuesta del *lakehouse*** discutida en el cuaderno 02 *(citado de memoria, verificar)*.

> 📖 **En el repositorio:** *E-Commerce Big Data Mining and Analytics* (Cao, 2023; `Data Mining/Libros/`, Cap. 3 y 4) y *Data Science Solutions on Azure* (Soh y Singh, 2020; `Machine Learning/Libros/`, Cap. 3) se verificaron contra el índice del PDF y se citan en los *Recursos Recomendados* de los cuadernos.

---

<div align="center">
  <p style="font-size: 0.9em; color: #64748b;">
    © 2026 <b>Universidad Santo Tomás — Seccional Tunja</b><br>
    <i>Especialización en Ciencia de Datos | Asignatura: Big Data</i>
  </p>
</div>
