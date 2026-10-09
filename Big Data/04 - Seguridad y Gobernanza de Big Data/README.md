# Módulo 04: Seguridad y Gobernanza de Big Data 🛡️🏛️

<p align="center">
  <img src="https://img.shields.io/badge/Discipline-Big%20Data-ea580c?style=for-the-badge&logo=apachespark&logoColor=white" alt="Big Data"/>
  <img src="https://img.shields.io/badge/Topics-Seguridad%20y%20Gobernanza-0ea5e9?style=for-the-badge" alt="Topics"/>
  <img src="https://img.shields.io/badge/Course-Big%20Data-6366f1?style=for-the-badge" alt="Course"/>
  <img src="https://img.shields.io/badge/Institution-USTA%20Tunja-1e3a8a?style=for-the-badge" alt="USTA"/>
</p>

Bienvenido al **Módulo 04** de la asignatura **Big Data** de la *Especialización en Ciencia de Datos* de la **Universidad Santo Tomás — Seccional Tunja**.

---

## 🧭 ¿De qué trata este módulo?

Este módulo corresponde a la **Sección 2.4** del libro de la asignatura (Capítulo 2): **2.4.1** amenazas de seguridad (brechas de datos, accesos no autorizados y *data leakage*), **2.4.2** técnicas de seguridad (encriptación, control de acceso y auditoría) y **2.4.3** gobernanza de datos (propiedad, responsabilidad y transparencia). Cuando los datos crecen, también crece la **superficie de ataque** y la necesidad de **saber de quién son, quién responde y qué reglas aplican**. El módulo responde tres preguntas: **¿qué puede salir mal?** (cuaderno 00), **¿cómo me defiendo?** (cuaderno 01) y **¿quién responde y cómo lo demuestro?** (cuaderno 02).

Como en el resto del curso, todo se **implementa y se prueba con `assert`** sobre **datos sintéticos con semilla fija**, con **resultados reportados con honestidad** (por ejemplo: en la detección de anomalías el modelo «sofisticado» **no** gana al $z$-score en precisión@$k$ y lo que funciona es **combinarlos**; la sal **no** frena un ataque de diccionario contra un *hash* rápido; la cadena de *hashes* **no** detecta que se recalculen todos los enlaces sin un ancla externa). **Este módulo no usa Spark.**

> 🛑 **Principio de seguridad:** nunca se implementa criptografía propia para uso real. El cifrado, las firmas y la derivación de claves usan **`cryptography`, `hashlib`, `hmac` y `secrets`**; las piezas «desde cero» (un servicio de claves de juguete, RBAC/ABAC, una bitácora encadenada, el cifrado César de los *Dummies*) son **didácticas** y están rotuladas así. Los «ataques» son **simulaciones defensivas** sobre datos del propio cuaderno; no hay código ofensivo contra sistemas reales.

> 🗺️ **Mapa del curso (seis módulos):** 00 Fundamentos → 01 Procesamiento y Almacenamiento Distribuido → 02 *Data Warehousing* y *Data Lake* → 03 Analítica y Visualización → **04 Seguridad y Gobernanza** *(este módulo)* → 05 Avances y Tendencias. Módulo anterior: [03](../03%20-%20Analitica%20y%20Visualizacion%20en%20Big%20Data/README.md).

> 🔗 **Para no duplicar:** la ética del uso de datos y de los algoritmos (sesgo, equidad, un laboratorio de seudonimización con sal y de $k$-anonimato) está en [Data Mining, Módulo 00 · Ética, privacidad y gobernanza](../../Data%20Mining/00%20-%20Introduccion%20al%20Data%20Mining/04_Etica_Privacidad_y_Gobernanza_en_Mineria_de_Datos.ipynb) y en [Introducción a la IA, Módulo 03 · Consideraciones éticas](../../Introduccion%20a%20la%20Inteligencia%20Artificial/03%20-%20Etica%20y%20el%20Nuevo%20Paradigma%20de%20la%20IA/00_Consideraciones_Eticas_de_la_IA.ipynb); la fuga de datos **de Machine Learning** (contaminación entre entrenamiento y prueba) está en [Machine Learning, Módulo 00](../../Machine%20Learning/00%20-%20Introduccion%20al%20Machine%20Learning/03_Importancia_del_Preprocesamiento.ipynb). Aquí el enfoque es **la seguridad y la gobernanza de los datos a escala Big Data**. El curso completo de gobernanza vive en [Adquisición, gestión y gobernanza de datos](../../Adquision%20gestion%20y%20gobernanza%20de%20datos/README.md) y el de seguridad en [Privacidad, seguridad e integridad de los datos](../../Privacidad,%20Seguridad%20e%20Integridad%20de%20los%20datos/README.md) *(hoy ambos solo con su README)*.

> 🛠️ **Ponlo en práctica:** todos los cuadernos incluyen secciones **«🛠️ Práctica»**: una celda de código para que escribas tu solución y, justo debajo, la **solución guiada desplegable**. Inténtalo primero.

---

## 📚 Estructura Curricular del Módulo

### 🎓 1. Cuadernos Académicos Estándar:
1. [**00_Amenazas_de_Seguridad.ipynb**](00_Amenazas_de_Seguridad.ipynb): *Sección 2.4.1.* **Tríada CIA y modelo de amenazas STRIDE** (con un diagrama de flujo de datos y fronteras de confianza dibujado con `matplotlib`). **Brechas de datos:** una bitácora sintética de ≈ 50 800 eventos con amenazas sembradas; **fuerza bruta** con umbrales por ventana de tiempo (`rolling('5min')`): con la clave «IP» no hay umbral perfecto (la ráfaga legítima de una oficina da falsa alarma o se escapa el ataque lento) y con la clave `(IP, usuario)` los umbrales de 5 a 30 dan precisión y recobrado de 1.0; **accesos anómalos** con `IsolationForest` frente a un $z$-score sobre 12 anomalías de cuatro tipos (se complementan: la unión de ambas listas recupera ≈ 92 %). **Accesos no autorizados:** matriz de control de acceso por rol y detección exacta de las 32 violaciones sembradas. ***Data leakage*:** detección de **PII** (cédulas, correos, teléfonos) con expresiones regulares (patrón ingenuo con precisión ≈ 0.33 frente a uno contextual), **redacción** idempotente; **ataque de reidentificación por enlace** entre una publicación «anónima» y un padrón público (≈ 92 % reidentificado con fecha exacta, sexo y municipio), **$k$-anonimato desde cero** con escalera de generalización y supresión, y el **ataque de homogeneidad** ($l$-diversidad). Aviso sobre la fuga de datos de ML y lista de verificación. 2 prácticas (revocar un permiso y medir el impacto; clases homogéneas).
2. [**01_Tecnicas_de_Seguridad_Encriptacion_Acceso_Auditoria.ipynb**](01_Tecnicas_de_Seguridad_Encriptacion_Acceso_Auditoria.ipynb): *Sección 2.4.2.* **Cifrado simétrico (Fernet) y asimétrico (RSA-OAEP, firma RSA-PSS)** con `cryptography` (detección de un bit alterado; RSA ≈ cientos de veces más lento), **cifrado en reposo y en tránsito** (conceptual) y una **demo de cifrado por sobre** (DEK por registro, KMS de juguete, **rotación de KEK** que reescribe solo las DEK y ***crypto-shredding***). ***Hashing* con sal y derivación de claves** (`hashlib.pbkdf2_hmac`, `secrets`, `hmac.compare_digest`): tasas medidas de MD5/SHA-1/SHA-256 frente a PBKDF2 y un experimento sobre una tabla de contraseñas filtrada **sintética** (SHA-1 sin sal cae con 49 cálculos; la sal sola **no** frena el diccionario con un *hash* rápido). **Enmascaramiento, seudonimización con HMAC y tokenización con bóveda** (un SHA-256 a secas de una cédula se invierte por enumeración; el HMAC con clave no). **RBAC (con herencia) y ABAC (denegar por defecto, la denegación gana)** desde cero con *asserts* y la «explosión de roles». **Bitácora inviolable con cadena de *hashes*:** detecta alterar y borrar; recalcular o truncar solo lo detecta un **ancla** externa; alertas de monitoreo. **Privacidad diferencial** (mecanismo de Laplace: error $\approx 1/\varepsilon$, razón de densidades acotada por $e^{\varepsilon}$, costo de repetir consultas). 2 prácticas (regla ABAC de horario; detectar alteración y truncamiento).
3. [**02_Gobernanza_de_Datos.ipynb**](02_Gobernanza_de_Datos.ipynb): *Sección 2.4.3.* **Propiedad, custodia, responsabilidad y transparencia**; **matriz RACI** validada por código (una sola A, al menos una R); **catálogo de datos** mínimo desde cero (18 fichas, metadatos, validación al registrar, `perfilar`); **linaje como grafo dirigido** con `networkx` (dibujado con `matplotlib`, análisis de impacto aguas abajo y de origen aguas arriba, detección de ciclos); un **motor de reglas de calidad** (completitud, unicidad, validez, consistencia, oportunidad) que encuentra **exactamente** los defectos sembrados y envía filas a cuarentena conservando el total; **políticas como código** (propiedad, retención, clasificación, accesos; con un efecto cruzado al corregir) y **contratos de datos** con detección de cambios incompatibles; **cumplimiento a nivel conceptual** (Habeas Data / Ley 1581 de 2012 y GDPR, sin citar artículos, marcado «verificar»; **no es asesoría jurídica**), y **modelo de madurez** con indicadores calculados antes y después. 2 prácticas (herencia de sensibilidad por el linaje; versionado semántico de un contrato).

---

### 📝 2. Taller Práctico Evaluativo (*Hands-On*):
* [**../homeworks/04_Seguridad_Gobernanza_Hands_On.ipynb**](../homeworks/04_Seguridad_Gobernanza_Hands_On.ipynb): Taller evaluativo que integra amenazas, técnicas de seguridad y gobernanza en ejercicios prácticos *(el cuaderno se publica aparte)*.

---

### 🧸 3. Ruta Didáctica: Para Dummies:
Ubicada en la subcarpeta [`Para Dummies/`](Para%20Dummies/). Sin jerga ni fórmulas, con analogías cotidianas; **no requieren *Spark*, Java ni `cryptography`**:
1. [**00_Amenazas_Seguridad_Dummies.ipynb**](Para%20Dummies/00_Amenazas_Seguridad_Dummies.ipynb): **La tienda de Doña Rosa**: el cuaderno de la portería y la alarma de «más de 5 fallos en 5 minutos» por persona, la tabla de **quién tiene qué llave** y cómo se descubre quién abrió lo que no debía, y «le quité el nombre»: con la edad exacta las 12 personas se reconocen, en rangos quedan 3.
2. [**01_Tecnicas_Seguridad_Dummies.ipynb**](Para%20Dummies/01_Tecnicas_Seguridad_Dummies.ipynb): **Candados, huellas y un libro a prueba de borrones**: el cifrado César **de juguete** (se rompe probando 25 claves), la **huella digital** y las contraseñas guardadas con sal, y un **libro de portería encadenado** donde arrancar una hoja se nota (y por qué se guarda la última huella afuera).
3. [**02_Gobernanza_Datos_Dummies.ipynb**](Para%20Dummies/02_Gobernanza_Datos_Dummies.ipynb): **La biblioteca del pueblo**: la ficha de cada libro (dueño, cuidador, sensible) y los datos sensibles sin responsable, **de la vaca a la arepa** (qué se afecta si falla un ingrediente y de dónde viene un producto) y la revisión de una lista de asistencia con reglas y cuarentena (4 buenas + 4 dudosas = 8).

---

## 💾 Datos Utilizados

Todos los datos son **sintéticos con semilla fija, generados por código dentro de cada cuaderno**; **no hay descargas, ni datos personales reales, y no se necesita ninguna carpeta `data/`**.

| Conjunto | Origen | Dónde se usa |
|---|---|---|
| **Bitácora de acceso** (300 usuarios × 14 días, ≈ 50 800 eventos) con 4 ataques de fuerza bruta, una ráfaga legítima, 12 usuario-día anómalos y 32 violaciones sembradas | `generar_bitacora(semilla=42)` | Cuaderno 00 |
| **600 mensajes de soporte** con cédulas, correos (`@example.com/.org`) y teléfonos **fabricados** y distractores numéricos | `generar_mensajes` | Cuaderno 00 |
| **Población de 20 000 personas** (padrón) y publicación «anónima» de 10 000 registros con diagnóstico | `generar_poblacion` | Cuaderno 00 |
| **Registros de clientes** (200), **tabla de contraseñas filtrada** (300 usuarios), **cédulas** (3 000) y tablas de compras, **bitácora de 20 entradas**, **base con 5 000 personas** para el conteo con ruido | `numpy.random.default_rng(42)` | Cuaderno 01 |
| **Catálogo de 18 conjuntos** de una organización ficticia, su **linaje** (17 aristas), **5 060 clientes** con defectos sembrados, **contratos** | Tablas escritas a mano y `generar_clientes` | Cuaderno 02 |
| **Mini-ejemplos de juguete** (cuaderno de la portería, tabla de llaves, lista del centro de salud, inventario, recetas, lista de asistencia) | Tablas y listas escritas a mano | Los tres *Dummies* |

> ⚠️ **Los datos son inventados** (nombres, documentos, cifras, áreas y diagnósticos): los resultados describen el **mecanismo**, **no** el rendimiento esperable en un caso real. Los valores de retención por clasificación del cuaderno 02 son **ilustrativos**, no requisitos legales. Los nombres de municipios de Boyacá solo ambientan los ejemplos.

## ⚙️ Requisitos

`numpy`, `pandas`, `matplotlib`, `scikit-learn` y `networkx` (preinstalados en Google Colab) y, **solo para el cuaderno 01**, **`cryptography`** (suele venir preinstalada en Colab; si no, `pip install cryptography`). `hashlib`, `hmac`, `secrets`, `re`, `json` y `datetime` son de la **biblioteca estándar**. **No se necesita *Spark*, Java ni red.** Los tres **Dummies** usan solo biblioteca estándar y `pandas`.

Se ejecutó de verdad, de arriba abajo y sin errores, con **Python 3.12**, **NumPy 2.5**, **pandas 2.3**, **scikit-learn 1.9**, **Matplotlib 3.11**, **NetworkX 3.7** y **cryptography 50.0** en Linux (con los *starters* de las prácticas tal cual —solo comentarios— y con una copia donde cada *starter* se reemplazó por su solución). *No se probó en Google Colab ni en Windows/macOS.* Tiempos aproximados en un equipo de escritorio (varían con la carga): cuaderno 00 ≈ 10 s, 01 ≈ 8 s y 02 ≈ 5 s; los *Dummies* tardan 2–3 s. El cuaderno 00 ofrece `RAPIDO = True` por defecto (con `False`: 600 usuarios y 100 000 personas). Las tasas de *hashing* y el rendimiento de Fernet frente a RSA **dependen de la máquina**; el texto describe órdenes de magnitud.

---

<div align="center">
  <p style="font-size: 0.9em; color: #64748b;">
    © 2026 <b>Universidad Santo Tomás — Seccional Tunja</b><br>
    <i>Especialización en Ciencia de Datos | Asignatura: Big Data</i>
  </p>
</div>
