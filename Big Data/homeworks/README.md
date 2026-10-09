# Talleres Prácticos Evaluativos (Hands-On Homeworks) 📝

> **Especialización en Ciencia de Datos**
> **Universidad Santo Tomás — Seccional Tunja**
> **Docente:** Santiago A. Zúñiga M.
> **Contacto:** [gestorvirtualcienciadatos@ustatunja.edu.co](mailto:gestorvirtualcienciadatos@ustatunja.edu.co)

---

## 📌 Descripción General

Esta carpeta contiene los **Talleres Prácticos Evaluativos (*Hands-On Homeworks*)** del curso **Big Data**, uno por cada módulo teórico, en dos ediciones:

* **Edición estándar** (esta carpeta): 4 retos integradores con código más un reto final de conclusiones, con problemas **nuevos** (no repiten los datos ni los ejemplos del módulo), rúbrica de evaluación y checklist de entrega.
* **Edición Para Dummies** ([`Para Dummies/`](Para%20Dummies/)): los mismos objetivos con 3 retos muy guiados, en lenguaje cotidiano y con pistas.

A diferencia de los cuadernos de clase, **los talleres no traen soluciones**: el estudiante los resuelve de forma autónoma. Cada reto incluye una celda de **autoverificación** con `assert` que falla con un mensaje claro mientras el reto no esté resuelto y pasa con una solución correcta. Todos los datos son sintéticos, con semilla fija y sin descargas, y los talleres **no requieren Spark ni Java**: los conceptos se implementan con Python, pandas, DuckDB/SQLite, NumPy, networkx y scikit-learn.

---

## 🗺️ Mapa de Talleres del Curso

| # | Taller Práctico | Módulo Asociado | Retos |
|---|---|---|---|
| **00** | [**00_Fundamentos_Big_Data_Hands_On.ipynb**](00_Fundamentos_Big_Data_Hands_On.ipynb) · [Dummies](Para%20Dummies/00_Fundamentos_Big_Data_Hands_On_Dummies.ipynb) | **Módulo 00: Fundamentos de Big Data** | Crecimiento y almacenamiento de una flota de datos, ventanas y el precio de esperar, tres fuentes en un solo esquema y el ciclo de vida con derecho al olvido. |
| **01** | [**01_Procesamiento_Almacenamiento_Hands_On.ipynb**](01_Procesamiento_Almacenamiento_Hands_On.ipynb) · [Dummies](Para%20Dummies/01_Procesamiento_Almacenamiento_Hands_On_Dummies.ipynb) | **Módulo 01: Procesamiento y Almacenamiento Distribuido** | Réplicas, quórums y red partida, MapReduce desde cero, un mini-HDFS que sobrevive a la caída de un nodo y un mini-HBase con su punto caliente. |
| **02** | [**02_Data_Warehouse_Data_Lake_Hands_On.ipynb**](02_Data_Warehouse_Data_Lake_Hands_On.ipynb) · [Dummies](Para%20Dummies/02_Data_Warehouse_Data_Lake_Hands_On_Dummies.ipynb) | **Módulo 02: Data Warehousing y Data Lake** | ETL que corrige, rechaza y cuadra, esquema estrella, preguntas OLAP en SQL y pandas, y del almacén al lago con particiones, poda y compactación. |
| **03** | [**03_Analitica_Visualizacion_Hands_On.ipynb**](03_Analitica_Visualizacion_Hands_On.ipynb) · [Dummies](Para%20Dummies/03_Analitica_Visualizacion_Hands_On_Dummies.ipynb) | **Módulo 03: Analítica y Visualización** | Muestreo de reservorio y Count-Min con cotas, aprendizaje fuera de memoria con `partial_fit`, SGD con paralelismo de datos y agregar antes de graficar contando la historia en una sola figura. |
| **04** | [**04_Seguridad_Gobernanza_Hands_On.ipynb**](04_Seguridad_Gobernanza_Hands_On.ipynb) · [Dummies](Para%20Dummies/04_Seguridad_Gobernanza_Hands_On_Dummies.ipynb) | **Módulo 04: Seguridad y Gobernanza** | Detección de fuerza bruta y fugas de lectura, identificadores y k-anonimato, cifrado con biblioteca seria y auditoría encadenada, y gobernanza con un grafo de linaje y control de acceso. |
| **05** | [**05_Streaming_Grafos_Tendencias_Hands_On.ipynb**](05_Streaming_Grafos_Tendencias_Hands_On.ipynb) · [Dummies](Para%20Dummies/05_Streaming_Grafos_Tendencias_Hands_On_Dummies.ipynb) | **Módulo 05: Avances y Tendencias** | Ventanas, sesiones y marca de agua con datos tardíos, PageRank y componentes conexas con Pregel, deriva y aprendizaje federado, y un libro de entregas a prueba de alteraciones. |

---

## 📋 Instrucciones y Criterios de Entrega

1. **Entorno de Ejecución:** Python 3.10+ con NumPy, Pandas, SciPy, Scikit-Learn, Matplotlib, NetworkX y DuckDB; el taller 04 usa además `cryptography` en la edición estándar. No hace falta Spark, PyTorch ni conexión a internet.
2. **Ejecución Completa:** antes de la entrega, reinicia el kernel y ejecuta todas las celdas (*Restart Kernel and Run All Cells*). No deben quedar `# TODO` ni `...` pendientes y todas las celdas de autoverificación deben pasar.
3. **Autonomía:** los talleres no incluyen soluciones; consulta los cuadernos del módulo correspondiente como material de apoyo.
4. **Seguridad:** en el taller 04, los «ataques» son simulaciones defensivas sobre datos sintéticos propios del taller, y nunca se implementa criptografía propia para uso real.
5. **Conclusiones:** el último reto de cada taller estándar es una reflexión escrita (5 a 8 líneas) que interpreta tus resultados.
6. **Evaluación:** cada taller suma 100 puntos; la rúbrica por criterio está al final de cada cuaderno.
7. **Tiempos:** todos corren en menos de 10 segundos.

---

<div align="center">
  <p style="font-size: 0.9em; color: #64748b;">
    © 2026 <b>Universidad Santo Tomás — Seccional Tunja</b><br>
    <i>Especialización en Ciencia de Datos | Big Data</i>
  </p>
</div>
