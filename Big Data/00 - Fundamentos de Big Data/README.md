# Módulo 00: Fundamentos de Big Data 🌊📊

<p align="center">
  <img src="https://img.shields.io/badge/Discipline-Big%20Data-ea580c?style=for-the-badge&logo=apachespark&logoColor=white" alt="Big Data"/>
  <img src="https://img.shields.io/badge/Topics-Fundamentos%20de%20Big%20Data-0ea5e9?style=for-the-badge" alt="Topics"/>
  <img src="https://img.shields.io/badge/Course-Big%20Data-6366f1?style=for-the-badge" alt="Course"/>
  <img src="https://img.shields.io/badge/Institution-USTA%20Tunja-1e3a8a?style=for-the-badge" alt="USTA"/>
</p>

Bienvenido al **Módulo 00**, el **primero** de la asignatura **Big Data** de la *Especialización en Ciencia de Datos* de la **Universidad Santo Tomás — Seccional Tunja**.

---

## 🧭 ¿De qué trata este módulo?

Este módulo abre el **Capítulo 1** del libro de la asignatura y corresponde a las secciones **1.1 (*Introducción*)**, **1.2 (*Resumen*)** y **1.3 (*Conceptos fundamentales*)**: **1.3.1** volumen, variedad y velocidad; **1.3.2** importancia del Big Data en el mundo actual; **1.3.3** tipos de datos (estructurados, no estructurados y semiestructurados); y **1.3.4** ciclo de vida de los datos. La pregunta que responde es **¿qué es el Big Data, por qué importa y cómo se ven y viven los datos?**, antes de pasar a *cómo se procesan y almacenan* en muchas máquinas (el módulo siguiente).

El módulo **no** repite lo que ya existe en el repositorio: el contenido de **Apache Spark / PySpark** (arquitectura, ETL, MLlib y *streaming*) está en [Data Mining, Módulo 07](../../Data%20Mining/07%20-%20Mineria%20de%20Datos%20con%20Big%20Data/README.md); aquí el enfoque es el del libro: **conceptos de Big Data con implementaciones desde cero en Python** (un reparto de trabajo con `multiprocessing` y la ley de Amdahl, una simulación de flujo de eventos, un *pipeline* con bitácora de linaje, una política de retención, comparación medida de formatos de archivo). Como en el resto del repositorio, se **verifica con `assert`** dentro de cada cuaderno, con **semillas fijas** y **resultados reportados con honestidad**, incluidos los casos en que lo «más sofisticado» **no** gana.

> 🗺️ **Mapa del curso (seis módulos):** **00** Fundamentos *(este módulo)* → **01** Procesamiento y Almacenamiento Distribuido → **02** *Data Warehousing* y *Data Lake* → **03** Analítica y Visualización → **04** Seguridad y Gobernanza → **05** Avances y Tendencias. El [README del curso](../README.md) se actualizará con el índice completo.

> 🔗 **Conexión con otros cursos:** la segmentación, la detección de anomalías y el pronóstico del cuaderno 01 usan técnicas de [Machine Learning, Módulo 04 (clustering)](../../Machine%20Learning/04%20-%20Clustering%20No%20Supervisado/README.md) y de [Data Mining, Módulo 01 (valores atípicos)](../../Data%20Mining/01%20-%20Preprocesamiento%20de%20los%20Datos/README.md); la calidad y la ética de datos se profundizan en [Data Mining, Módulo 00](../../Data%20Mining/00%20-%20Introduccion%20al%20Data%20Mining/README.md) y en [Introducción a la IA, Módulo 03 (ética)](../../Introduccion%20a%20la%20Inteligencia%20Artificial/03%20-%20Etica%20y%20el%20Nuevo%20Paradigma%20de%20la%20IA/README.md).

> 🛠️ **Ponlo en práctica:** todos los cuadernos (estándar y *Para Dummies*) incluyen secciones **«🛠️ Práctica»**: una celda de código para que escribas tu solución y, justo debajo, la **solución guiada desplegable** (`💡 Haz clic aquí para ver la solución guiada...`). Inténtalo primero y abre la solución solo para comparar.

---

## 📚 Estructura Curricular del Módulo

### 🎓 1. Cuadernos Académicos Estándar:
1. [**00_Introduccion_y_Las_V_del_Big_Data.ipynb**](00_Introduccion_y_Las_V_del_Big_Data.ipynb): *Secciones 1.1, 1.2 y 1.3.1.* **Por qué existe el Big Data** (los límites de memoria, disco, CPU y red de una máquina), el **resumen del Capítulo 1 y el mapa de los seis módulos**. **Volumen:** calculadora de unidades (SI frente a binarias, con asserts: un «1 TB» son ≈ 931 GiB) y de crecimiento compuesto con replicación (empresa **ficticia**: tiempo de duplicación y mes en que un servidor deja de alcanzar); **por qué *pandas* deja de alcanzar** (perfil de memoria con `tracemalloc`: el `DataFrame` ocupa ≈ 4.7 veces el archivo CSV y los tipos compactos lo reducen ≈ 92 %; el pico de memoria al cargar todo crece linealmente y por trozos con `chunksize` queda plano, con resultado idéntico verificado, aunque **más lento**). **Velocidad:** simulación de **flujo de eventos** (proceso de Poisson no homogéneo con ráfaga), ventanas *tumbling* y *sliding*, **latencia** por estrategia (lote de 60 s ≈ 33 s frente a evento a evento ≈ 0.9 s), **tiempo de evento frente a llegada** y marca de agua, y la **cola** (*backlog*) según la capacidad. **Variedad:** cinco fuentes heterogéneas (CSV, JSON, XML, *log*, texto) armonizadas en un esquema común; **veracidad** y **valor** a nivel conceptual. ***Scale-up* frente a *scale-out*:** **ley de Amdahl** verificada, probabilidad de fallos en un clúster ($1-(1-q)^N$, comprobada por simulación) y un **experimento real de reparto con `multiprocessing`** (pasos de Collatz): resultado idéntico, aceleración **sublineal** y fracción paralelizable efectiva ajustada. 2 prácticas (la media de las medias es una trampa; ¿cuántos procesadores para llegar al 90 % del techo?).
2. [**01_Importancia_del_Big_Data_en_el_Mundo_Actual.ipynb**](01_Importancia_del_Big_Data_en_el_Mundo_Actual.ipynb): *Sección 1.3.2.* **Del dato al valor:** la **pirámide DIKW ejecutada** sobre una estación meteorológica sintética (336 lecturas → 14 resúmenes → una alerta de 3 días; la regla es ilustrativa, **no agronómica**); **sectores y casos de uso** (salud, **agro de Boyacá**, transporte, finanzas, gobierno, comercio) **sin cifras de mercado**; **economía del dato** y cadena de valor. **Tres mini-demostraciones sobre datos sintéticos:** (A) **segmentación de clientes** con K-Means (≈ 11 % de los clientes aportan ≈ 56 % del ingreso; la silueta prefiere $k=2$ aunque la estructura real es de 3), (B) **detección de anomalías en transacciones** (umbral global frente a $z$ robusto por cliente frente a *Isolation Forest*: el contexto del cliente y la hora sube la precisión en el 1 % superior de ≈ 34 % a ≈ 52 %), (C) **pronóstico de demanda** (líneas base frente a regresión con tendencia y estacionalidad, traducido a **costo de inventario**; el promedio móvil **no** mejora al ingenuo). **Riesgos y ética** con una medición de **k-anonimato** («sin nombre» no es «anónimo»: ≈ 56 % de registros únicos con cuatro atributos) y enlaces a la Ley 1581 de 2012 (conceptual). 2 prácticas (pronóstico estacional con promedio; ¿qué ancho de banda de edad basta?).
3. [**02_Tipos_de_Datos_Estructurados_No_Estructurados_Semiestructurados.ipynb**](02_Tipos_de_Datos_Estructurados_No_Estructurados_Semiestructurados.ipynb): *Sección 1.3.3.* Los tres tipos como **espectro**. **Estructurados:** `sqlite3` con claves, restricciones (`CHECK`, `FOREIGN KEY`), `JOIN` + `GROUP BY` **igual a** `merge` + `groupby`, un **índice** que cambia el plan de ejecución y una **transacción atómica**. **Semiestructurados:** eventos **JSON de esquema variable**, `json_normalize` (nulos que **no son faltantes**), `record_path` para listas y el mismo sensor en **XML** (`ElementTree`). **No estructurados:** texto (expresiones regulares y conteos), **imágenes como arreglos** y ***logs*** con **cuarentena** de líneas mal formadas. ***Schema-on-write* frente a *schema-on-read*** con los mismos 2 000 pagos «sucios» (el esquema al escribir acepta el 72.6 %; el lector tolerante recupera el 94.4 % del crudo). **Formatos de archivo medidos:** CSV, JSON por líneas y **Parquet** (≈ 2.9 veces menos espacio que el CSV, lectura de una columna 10–16 veces más rápida, tipos conservados) y una **tabla guía** de qué almacenar dónde. 2 prácticas (esquema variable y nulos; compresión de Parquet).
4. [**03_Ciclo_de_Vida_de_los_Datos.ipynb**](03_Ciclo_de_Vida_de_los_Datos.ipynb): *Sección 1.3.4.* Las **seis etapas** (generación, ingesta, almacenamiento, procesamiento, análisis/visualización, archivado/eliminación) con un **diagrama dibujado con `matplotlib`**; un **pipeline mínimo funcional** (una función por etapa, zonas origen → cruda → curada → archivo, **cuarentena con motivo** y **conservación de filas** verificada: 1 038 = 949 + 59 + 30) con **bitácora de linaje** y huellas; **métricas de calidad** (completitud, unicidad, validez) y un **sensor «pegado»** que pasa todas las reglas de rango; **política de retención y borrado** (eliminar, anonimizar, seudonimizar; por qué un *hash* sin sal se revierte por fuerza bruta) con la **Ley 1581 de 2012 / *Habeas Data*** a nivel conceptual (sin citar artículos; **no es asesoría jurídica**); y **buenas prácticas** por etapa. 2 prácticas (regla de veracidad para el sensor pegado; derecho de supresión).

---

### 📝 2. Taller Práctico Evaluativo (*Hands-On*):
* [**../homeworks/00_Fundamentos_Big_Data_Hands_On.ipynb**](../homeworks/00_Fundamentos_Big_Data_Hands_On.ipynb): Taller evaluativo que integra las «V», los tipos de datos y el ciclo de vida en ejercicios prácticos *(el cuaderno se publica aparte)*.

---

### 🧸 3. Ruta Didáctica: Para Dummies:
Ubicada en la subcarpeta [`Para Dummies/`](Para%20Dummies/). Sin jerga ni fórmulas, con analogías cotidianas; **no requieren *Spark* ni Java**:
1. [**00_Introduccion_Las_V_Dummies.ipynb**](Para%20Dummies/00_Introduccion_Las_V_Dummies.ipynb): **La plaza de mercado gigante**: cuántas fotos caben en un disco y por qué **duplicar cada mes** llena 1 TB en 10 meses, **la fila de la caja** que se acumula (una caja frente a dos) y **las cocineras y el único horno** (más manos ayudan, pero el horno pone el techo).
2. [**01_Importancia_Big_Data_Dummies.ipynb**](Para%20Dummies/01_Importancia_Big_Data_Dummies.ipynb): **De los tomates a la salsa**: la tendera que agrupa a sus clientes (3 fieles dejan ≈ 66 % del dinero), la **alarma de la tarjeta** con su falsa alarma de Navidad y **cuánta papa pedir** copiando el mismo día de la semana pasada.
3. [**02_Tipos_de_Datos_Dummies.ipynb**](Para%20Dummies/02_Tipos_de_Datos_Dummies.ipynb): **Cuaderno, formulario y álbum de fotos**: una tabla que se consulta en una línea, formularios que cambian y dejan huecos que **no son errores**, y cómo una computadora «ve» un texto y una foto de 5×5.
4. [**03_Ciclo_de_Vida_Dummies.ipynb**](Para%20Dummies/03_Ciclo_de_Vida_Dummies.ipynb): **De la vaca a tu mesa**: las seis estaciones del viaje de un dato, el **recibo** que cierra (12 = 8 + 4) y la **fecha de vencimiento** con el «borren mis datos» (y por qué hay que buscar en todos los lugares).

---

## 💾 Datos Utilizados

Todos los datos son **sintéticos con semilla fija, generados por código dentro de cada cuaderno**; **no hay descargas** y **no se necesita ninguna carpeta `data/`** (los archivos que se escriben —un CSV de 300 000 filas, archivos Parquet, zonas del *pipeline*— se crean en un **directorio temporal** que se borra al cerrar el núcleo; así cada cuaderno es autocontenido en Google Colab y el repositorio no acumula archivos).

| Conjunto | Origen | Dónde se usa |
|---|---|---|
| **Transacciones CSV** (300 000 filas, `monto` lognormal con tendencia) | Generador `generar_transacciones(semilla=42)` | Cuaderno 00 (perfil de memoria, `chunksize`, Práctica 1) |
| **Flujo de eventos** (≈ 131 000 eventos en 10 min, con ráfaga y 5 % de tardíos) | Proceso de Poisson no homogéneo, `default_rng(42)` | Cuaderno 00 (velocidad) |
| **Números para repartir** (100 000 enteros, pasos de Collatz) | `default_rng(42)` | Cuaderno 00 (`multiprocessing`, Amdahl) |
| **Estación meteorológica** (14 días × 24 h) | `generar_estacion` | Cuaderno 01 (DIKW) |
| **Clientes** (3 000, 3 segmentos ocultos), **transacciones con fraude** (40 000, ≈ 1 %), **demanda diaria** (≈ 3 años) y **beneficiarios** (5 000) | `generar_clientes`, `generar_transacciones_fraude`, `generar_demanda`, `generar_beneficiarios` | Cuaderno 01 |
| **Clientes y pedidos** (200 y 2 000), **eventos JSON** (300), **reseñas**, ***logs*** (600 líneas), **pagos sucios** (2 000) y **lecturas de sensores** (200 000 filas) | `numpy.random.default_rng(42)` | Cuaderno 02 |
| **Lecturas de 6 estaciones** (7 días, con defectos) y **titulares** (400, ficticios) | `generar`, `generar_titulares` | Cuaderno 03 |
| **Mini-ejemplos de juguete** (clientes, compras de Ana, ventas de papa, pedidos, litros por vaca) | Tablas y listas escritas a mano | Los cuatro *Dummies* |

> ⚠️ **Los datos son inventados** (nombres, documentos, cifras y estaciones): los resultados describen el **mecanismo**, **no** el rendimiento esperable en un caso real. Los nombres de municipios de Boyacá solo ambientan los ejemplos.

## ⚙️ Requisitos

`numpy`, `pandas`, `matplotlib`, `scikit-learn` y `pyarrow` (todos preinstalados en Google Colab). `sqlite3`, `json`, `xml`, `re`, `multiprocessing`, `tracemalloc` y `hashlib` son de la **biblioteca estándar**. **No se necesita *Spark*, Java ni red.** Los cuatro **Dummies** usan solo `NumPy`, `pandas` y `matplotlib`.

Se ejecutó de verdad, de arriba abajo y sin errores, con **Python 3.12**, **NumPy 2.5**, **pandas 2.3**, **scikit-learn 1.9**, **Matplotlib 3.11** y **PyArrow 25** en Linux (de verdad: con los *starters* de las prácticas tal cual —solo comentarios— y con una copia donde cada *starter* se reemplazó por su solución). *No se probó en Google Colab ni en Windows/macOS.* Tiempos aproximados en un equipo de escritorio con 8 núcleos (varían con la carga): cuaderno 00 ≈ 11 s, 01 ≈ 8 s, 02 ≈ 8–11 s y 03 ≈ 4 s con `RAPIDO = True`; los *Dummies* tardan 3–6 s. Con `RAPIDO = False` (más filas): 00 ≈ 45 s y 02 ≈ 65 s. Notas de portabilidad: el experimento de `multiprocessing` del cuaderno 00 usa el método **`fork`** (Linux y Colab); en Windows y macOS (método `spawn`) se **omite** con un aviso y el resto del cuaderno sigue; `pd.to_datetime(..., format="ISO8601")` requiere *pandas* ≥ 2.0.

---

<div align="center">
  <p style="font-size: 0.9em; color: #64748b;">
    © 2026 <b>Universidad Santo Tomás — Seccional Tunja</b><br>
    <i>Especialización en Ciencia de Datos | Asignatura: Big Data</i>
  </p>
</div>
