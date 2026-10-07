# Módulo 06: Aprendizaje por Refuerzo 🎮🤖

<p align="center">
  <img src="https://img.shields.io/badge/Discipline-Machine%20Learning-059669?style=for-the-badge&logo=scikitlearn&logoColor=white" alt="Machine Learning"/>
  <img src="https://img.shields.io/badge/Topics-Aprendizaje%20por%20Refuerzo-0ea5e9?style=for-the-badge" alt="Topics"/>
  <img src="https://img.shields.io/badge/Course-Machine%20Learning-6366f1?style=for-the-badge" alt="Course"/>
  <img src="https://img.shields.io/badge/Institution-USTA%20Tunja-1e3a8a?style=for-the-badge" alt="USTA"/>
</p>

Bienvenido al **Módulo 06** de la asignatura **Machine Learning** de la *Especialización en Ciencia de Datos* de la **Universidad Santo Tomás — Seccional Tunja**.

---

## 🧭 ¿De qué trata este módulo?

Este módulo continúa el **Capítulo 2** del syllabus y corresponde a las secciones **2.7 (*Reinforcement Learning*)**, **2.8 (*Core concepts: MDPs, value functions, policy gradients*)** y **2.9 (*Deep Reinforcement Learning: DQN, Policy Gradient Methods*)**. Tras el [Módulo 05](../05%20-%20Reduccion%20de%20Dimensionalidad/README.md) (representar los datos con pocas dimensiones), entramos al tercer paradigma de aprendizaje: **un agente que decide en secuencia, interactúa con un entorno y aprende de una recompensa escalar y retrasada**, sin ejemplos con la respuesta correcta. En el [Módulo 00](../00%20-%20Introduccion%20al%20Machine%20Learning/01_Paradigmas_de_Aprendizaje.ipynb) el refuerzo se vio solo como un **bandido multibrazo** $\varepsilon$-*greedy* (un único estado); aquí damos el salto al **problema completo** y **no se repite** el bandido ni la fórmula de Q-learning: se **generalizan, se derivan y se verifican**.

> 📌 **Una nota sobre el índice del libro:** el título oficial del Capítulo 2 en el índice original es *Outline of the Scientific Research Process*, pero su contenido real es **aprendizaje no supervisado, reducción de dimensionalidad, aprendizaje por refuerzo y selección de modelos**. El curso sigue el contenido real: el Módulo 06 cubre el aprendizaje por refuerzo y el Módulo 07 (cuyo nombre definitivo puede ajustarse) cierra el capítulo con la **selección de modelos**.

El enfoque es **más profundo** que el de los cursos previos: todo se **formula, se implementa desde cero y se verifica con `assert`** dentro del propio cuaderno. Se construye un **MDP finito con matrices $P$ y $R$ explícitas** y se comprueba que reproduce **exactamente** la dinámica de `FrozenLake-v1` de Gymnasium (`env.unwrapped.P`); la evaluación **Monte Carlo** se contrasta con la solución **exacta** del sistema $(I-\gamma P_\pi)V=r_\pi$; la **programación dinámica** (evaluación iterativa, iteración de política y de valor) se verifica entre sí y contra la solución exacta, incluida la **cota de contracción** $\gamma^k$; **Q-learning converge a $Q_*$** dentro de una tolerancia, y el *Cliff Walking* muestra con números la diferencia entre **SARSA (camino seguro)** y **Q-learning (camino óptimo)**; el **teorema del gradiente de la política** se verifica con tres métodos que coinciden (fórmula cerrada, diferencias finitas y estimador REINFORCE) y la reducción de varianza de una *baseline* se **mide**; y en el cuaderno de RL profundo se programan **DQN** y **REINFORCE** en PyTorch con **varias semillas** y una discusión **honesta** de su inestabilidad y su sensibilidad a los hiperparámetros (sin esconder semillas malas ni asegurar que se alcance el máximo).

> 🔗 **Conexión con otros cursos:** la idea de **agente, estado y acción** viene de [Introducción a la IA — Módulo 04 (Algoritmos de Búsqueda)](../../Introduccion%20a%20la%20Inteligencia%20Artificial/04%20-%20Algoritmos%20de%20Busqueda/README.md): allá el modelo es conocido y determinista y la solución es un camino; aquí el resultado de actuar es **incierto** y la solución es una **política**. Las **redes neuronales y PyTorch** que se usan en el último cuaderno se desarrollaron en el [Módulo 02, cuaderno 02](../02%20-%20Arboles%20Bosques%20y%20Redes%20Neuronales/02_Redes_Neuronales.ipynb); el mapa del Capítulo 2 está en la [Introducción al Capítulo 2](../04%20-%20Clustering%20No%20Supervisado/00_Introduccion_Cap2_y_No_Supervisado.ipynb).

---

## 📚 Estructura Curricular del Módulo

### 🎓 1. Cuadernos Académicos Estándar:
1. [**00_Fundamentos_RL_y_MDPs.ipynb**](00_Fundamentos_RL_y_MDPs.ipynb): *Secciones 2.7 y 2.8.1.* El **bucle agente–entorno**, la **hipótesis de la recompensa**, el **retorno** y el **factor de descuento** (recursión $G_t=r_{t+1}+\gamma G_{t+1}$, verificada), **política**, **propiedad de Markov**, tareas **episódicas y continuas**, la tupla $(\mathcal S,\mathcal A,P,R,\gamma)$ y el dilema **exploración–explotación**; un ***FrozenLake* resbaladizo construido desde cero** con tensores $P$ y $R$, **simulación de episodios**, la **estimación Monte Carlo** de una política aleatoria verificada contra el **cálculo exacto** (radio espectral y serie de Neumann incluidos), la **API de Gymnasium** (`reset`/`step`, `terminated` frente a `truncated`) y la **verificación con `assert` contra `env.unwrapped.P`** (4×4 resbaladizo, 4×4 determinista y 8×8).
2. [**01_Funciones_de_Valor_y_Q_Learning.ipynb**](01_Funciones_de_Valor_y_Q_Learning.ipynb): *Sección 2.8.2.* $v_\pi$ y $q_\pi$; las ecuaciones de **Bellman de expectativa y de optimalidad** (derivación) y la **contracción** del operador (5 000 pares verificados); **programación dinámica desde cero** (evaluación iterativa, **iteración de política**, **iteración de valor**) coincidentes entre sí y con la solución exacta, con la cota $\gamma^k$ y el caso 8×8; **Monte Carlo y TD(0)** (sesgo, varianza y el «piso de ruido» de $\alpha$ constante); **SARSA y Q-learning** tabulares desde cero con $\varepsilon$-*greedy* decreciente: Q-learning converge a $Q_*$ en *FrozenLake* (100 000 episodios) y su política voraz es óptima; **Cliff Walking** propio (*on-policy* frente a *off-policy*: camino seguro de SARSA frente al óptimo de Q-learning, con el retorno esperado **exacto** de la política $\varepsilon$-*greedy*); y un barrido honesto de $\alpha$ y del decaimiento de $\varepsilon$.
3. [**02_Gradientes_de_Politica.ipynb**](02_Gradientes_de_Politica.ipynb): *Sección 2.8.3.* Por qué optimizar la política directamente (acciones continuas, **políticas estocásticas óptimas**: el *pasillo corto*, suavidad); política **softmax**; el **truco de la log-derivada**, el **teorema del gradiente de la política** y el estimador **REINFORCE** (derivación); **verificación triple** del gradiente en el *mundo 4×3* de Russell & Norvig (fórmula cerrada $=$ diferencias finitas $=$ Monte Carlo, error $\propto1/\sqrt N$); **varianza del estimador** y ***baselines*** medidas cuantitativamente sin sesgo; **REINFORCE desde cero** en NumPy con tres *baselines* y 8 semillas (objetivo $J(\theta)$ exacto en cada iteración); la **ventaja** $A=q-v$, el **actor-crítico** (propiedades verificadas, sin implementarlo) y la **tabla comparativa** *value-based* / *policy-based* / actor-crítico.
4. [**03_Deep_RL_DQN_y_Policy_Gradient.ipynb**](03_Deep_RL_DQN_y_Policy_Gradient.ipynb): *Sección 2.9.* La **explosión de estados**, la **aproximación de funciones** y la **«tríada letal»** (aproximación + *bootstrapping* + *off-policy*) con el **contraejemplo de Baird** implementado desde cero; **DQN** (Mnih et al., 2015) en **PyTorch**: red $Q$, **memoria de repetición**, **red objetivo**, $\varepsilon$-*greedy* con decaimiento, **pérdida de Huber** y el manejo correcto de `terminated`/`truncated`; **REINFORCE** (con y sin *baseline*) en PyTorch con el gradiente verificado contra la teoría; **curvas de aprendizaje con varias semillas** (curvas individuales y media ± desviación), tablas por semilla y discusión **honesta** de la inestabilidad y la sensibilidad a los hiperparámetros; **Double DQN**, A2C y PPO como siguiente paso. Incluye la bandera `RAPIDO` (por defecto `True`, ~1–2 min en CPU) para controlar el presupuesto de cómputo.

---

### 📝 2. Taller Práctico Evaluativo (*Hands-On*):
* [**../homeworks/06_Aprendizaje_por_Refuerzo_Hands_On.ipynb**](../homeworks/06_Aprendizaje_por_Refuerzo_Hands_On.ipynb): Taller evaluativo que integra MDP, programación dinámica, Q-learning, gradiente de política y RL profundo en ejercicios prácticos *(el cuaderno se publica aparte)*.

---

### 🧸 3. Ruta Didáctica: Para Dummies:
Ubicada en la subcarpeta [`Para Dummies/`](Para%20Dummies/):
1. [**00_RL_y_MDPs_Dummies.ipynb**](Para%20Dummies/00_RL_y_MDPs_Dummies.ipynb): **El perro, el premio y el lago resbaloso**: los personajes del refuerzo (agente, entorno, acciones, recompensa, política), la **paciencia** (por qué un premio tardío vale menos), un plan perfecto que casi nunca gana en piso resbaloso y el dilema de probar o repetir.
2. [**01_Valor_y_QLearning_Dummies.ipynb**](Para%20Dummies/01_Valor_y_QLearning_Dummies.ipynb): **La libreta de notas y el precipicio**: las notas de valor que se «contagian» desde el tesoro, y el viajero **optimista** (Q-learning) frente al **cauteloso** (SARSA) con una mini simulación real.
3. [**02_Gradientes_de_Politica_Dummies.ipynb**](Para%20Dummies/02_Gradientes_de_Politica_Dummies.ipynb): **La perilla de las probabilidades**: una máquina de tres botones, la regla «sube lo que salió mejor de lo esperado» y por qué compararse con una **referencia** evita enamorarse de un botón malo (40 agentes simulados).
4. [**03_Deep_RL_Dummies.ipynb**](Para%20Dummies/03_Deep_RL_Dummies.ipynb): **El cerebro, las fichas de estudio y el profesor paciente**: por qué la libreta no cabe, la **memoria de repetición** (experimento: error ~0 frente a ~0.3) y la **red objetivo**, y la inestabilidad entre intentos. Sin PyTorch ni Gymnasium.

> 🛠️ **Ponlo en práctica:** todos los cuadernos (estándar y *Para Dummies*) incluyen secciones **«🛠️ Práctica»**: una celda de código para que escribas tu solución y, justo debajo, la **solución guiada desplegable** (`💡 Haz clic aquí para ver la solución guiada...`). Inténtalo primero y abre la solución solo para comparar.

---

## 💾 Datos Utilizados

Este módulo **no usa conjuntos de datos**: en aprendizaje por refuerzo los datos **los genera el propio agente al interactuar** con un entorno. Los entornos son:

| Entorno | Origen | Dónde se usa |
|---|---|---|
| ***FrozenLake* 4×4 y 8×8** (resbaladizo y determinista) | MDP **propio** en NumPy (matrices $P$ y $R$), verificado contra `FrozenLake-v1` de **Gymnasium** | Cuadernos 00 y 01 |
| ***Cliff Walking* 4×12** | MDP **propio** en NumPy (equivalente a `CliffWalking` de Gymnasium) | Cuaderno 01 |
| ***Mundo 4×3*** de Russell & Norvig y el ***pasillo corto*** de Sutton & Barto | MDP **propio** en NumPy | Cuaderno 02 |
| ***CartPole-v1*** | **Gymnasium** (`gym.make("CartPole-v1")`) | Cuaderno 03 |
| *Contraejemplo de Baird* | Implementación propia en NumPy | Cuaderno 03 |

Todo se ejecuta con **semillas fijas** (`SEED = 42`, semillas por corrida) y **sin ninguna descarga** de datos, por lo que los cuadernos son reproducibles sin conexión a internet (Gymnasium trae sus entornos *classic control* y *toy text*). Con NumPy las salidas son idénticas entre ejecuciones; con **PyTorch** los resultados de entrenamiento pueden variar ligeramente entre versiones y plataformas, por lo que los `assert` del cuaderno 03 solo cubren lo **robusto** (superar a la política aleatoria por un margen amplio; coherencia de dimensiones, objetivo TD y gradientes), **nunca** que se alcance el retorno máximo.

---

## ⚙️ Requisitos

`numpy`, `pandas`, `matplotlib`, `seaborn` (preinstalados en Google Colab) y, **solo para los cuadernos que lo usan**, `gymnasium` (cuadernos 00 y 03; puede no venir preinstalado en Colab: la primera celda de esos cuadernos trae la línea `# !pip install -q gymnasium` para quitarle el comentario) y `torch` (cuaderno 03; preinstalado en Colab). Los cuadernos 01 y 02 y los cuatro **Dummies** **no** necesitan PyTorch ni Gymnasium. El código usa la **API moderna de Gymnasium** (`reset()` → `(obs, info)`; `step()` → 5 valores con `terminated` y `truncated`), probada con **Gymnasium 1.x**, y evita las APIs frágiles entre versiones (p. ej. no usa `np.bool8`, eliminado en NumPy 2). Tiempos aproximados en un equipo de escritorio con CPU: cuadernos 00 y 02 ≈ 20–30 s, cuaderno 01 ≈ 40–50 s y cuaderno 03 ≈ 1–1.5 min con `RAPIDO = True` (con `RAPIDO = False` se usan 5 semillas y 30 000 pasos de DQN —≈ 10–11 min— y se activa un barrido de hiperparámetros); los Dummies tardan entre 5 y 15 s.

---

## 📚 Lecturas Complementarias

*Todas están citadas de memoria salvo las marcadas como verificadas: comprueba los datos bibliográficos antes de citarlas formalmente.*

1. Géron, A. (2025). *Hands-On Machine Learning with Scikit-Learn and PyTorch*, O'Reilly. **Cap. 19** (*Reinforcement Learning*): *Policy Gradients*, *Value-Based Methods* (MDP, TD, Q-learning, DQN y sus mejoras), *Actor-Critic Algorithms* y *Overview of Some Popular RL Algorithms*. Disponible en `Machine Learning/Libros/` (capítulo verificado contra el PDF).
2. Sutton, R. S. & Barto, A. G. (2018). *Reinforcement Learning: An Introduction*, 2.ª ed., MIT Press. Referencia estándar; disponible en línea de forma gratuita. *(citado de memoria, verificar)*
3. Bellman, R. (1957). *A Markovian decision process*. **Journal of Mathematics and Mechanics** 6(5): 679–684 (verificada en el capítulo de Géron); y Bellman, R. (1957). *Dynamic Programming*, Princeton University Press. *(citado de memoria, verificar)*
4. Watkins, C. J. C. H. & Dayan, P. (1992). *Q-learning*. **Machine Learning** 8: 279–292; y Sutton, R. S. (1988). *Learning to predict by the methods of temporal differences*. **Machine Learning** 3: 9–44. *(citados de memoria, verificar)*
5. Williams, R. J. (1992). *Simple statistical gradient-following algorithms for connectionist reinforcement learning*. **Machine Learning** 8: 229–256 (verificada en el capítulo de Géron); y Sutton, R. S., McAllester, D., Singh, S. & Mansour, Y. (2000). *Policy gradient methods for reinforcement learning with function approximation*. **NIPS 12**. *(citado de memoria, verificar)*
6. Mnih, V. et al. (2013). *Playing Atari with Deep Reinforcement Learning*. **arXiv:1312.5602**; y Mnih, V. et al. (2015). *Human-level control through deep reinforcement learning*. **Nature** 518: 529–533 (ambas verificadas en el capítulo de Géron).
7. van Hasselt, H., Guez, A. & Silver, D. (2016). *Deep reinforcement learning with double Q-learning*. **AAAI**; Schulman, J. et al. (2017). *Proximal policy optimization algorithms*. **arXiv:1707.06347**. *(citados de memoria, verificar)*
8. Henderson, P. et al. (2018). *Deep reinforcement learning that matters*. **AAAI**: sobre la reproducibilidad y la sensibilidad a las semillas. *(citado de memoria, verificar)*
9. Russell, S. & Norvig, P. (2020). *Artificial Intelligence: A Modern Approach*, 4.ª ed., Cap. 17: el mundo 4×3. *(citado de memoria, verificar)*

---

<div align="center">
  <p style="font-size: 0.9em; color: #64748b;">
    © 2026 <b>Universidad Santo Tomás — Seccional Tunja</b><br>
    <i>Especialización en Ciencia de Datos | Asignatura: Machine Learning</i>
  </p>
</div>
