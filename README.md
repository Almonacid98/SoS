# 🌌 Orbital Simulator 2D

<div align="center">

### 🛰️ Simulador Orbital Interactivo 2D

**Modelado numérico del movimiento de un satélite bajo la acción de la gravedad**

![Python](https://img.shields.io/badge/Python-3.x-3776AB?style=for-the-badge&logo=python&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-Cálculo_Numérico-013243?style=for-the-badge&logo=numpy&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-Visualización-11557C?style=for-the-badge)
![Status](https://img.shields.io/badge/Estado-En_Desarrollo-orange?style=for-the-badge)

**Trabajo Final Integrador — Física**  
Ingeniería en Informática

</div>

---

## 🚀 Sobre el proyecto

**Orbital Simulator 2D** es un simulador de física desarrollado en Python cuyo objetivo es modelar el movimiento de un satélite alrededor de un planeta utilizando principios de **mecánica clásica y gravitación newtoniana**.

A diferencia de una animación con una trayectoria previamente definida, la posición del satélite es calculada durante cada instante de la simulación a partir de las fuerzas que actúan sobre él.

El proyecto permite estudiar cómo diferentes condiciones iniciales, como la **altura**, la **velocidad** y la **dirección del movimiento**, pueden producir distintos comportamientos orbitales.

```text
                         🛰️
                        ↗
                   · · · · · ·
                ·               ·
              ·                   ·
             ·         🌍          ·
              ·                   ·
                ·               ·
                   · · · · · ·
```

Dependiendo de las condiciones iniciales, el satélite podrá:

- 💥 Impactar contra el planeta.
- 🟢 Mantener una órbita aproximadamente circular.
- 🟡 Describir una órbita elíptica.
- 🔵 Alcanzar una trayectoria de escape.

---

## 🎯 Objetivo

El objetivo principal es desarrollar una simulación computacional que permita aplicar y relacionar conceptos fundamentales de Física con herramientas propias de la Ingeniería en Informática.

El proyecto integra:

- 📏 Magnitudes y unidades.
- 📍 Posición y desplazamiento.
- 🏃 Velocidad y aceleración.
- 🧭 Vectores y movimiento bidimensional.
- 🍎 Leyes de Newton.
- 🌍 Gravitación universal.
- ⚙️ Trabajo y energía.
- 🔢 Métodos numéricos.
- 📊 Análisis y visualización de resultados.

---

## 🌍 Modelo físico

El sistema inicial está compuesto por:

```text
                 velocidad tangencial
                         ↑
                         │
                         🛰️ Satélite
                         │
                         │ r
                         │
                         │
                         🌍
                       Tierra
```

El planeta se encuentra inicialmente fijo en el origen:

```text
Tierra → (0, 0)
```

Mientras que el satélite posee:

```text
Posición     → (x, y)
Velocidad    → (vx, vy)
Aceleración  → (ax, ay)
```

La trayectoria resultante no se encuentra programada previamente.

Es consecuencia de resolver numéricamente las ecuaciones físicas del sistema.

---

## 🧲 Gravitación Universal

La interacción principal del modelo está determinada por la **Ley de Gravitación Universal de Newton**:

$$
F = G\frac{Mm}{r^2}
$$

donde:

| Símbolo | Magnitud |
|---|---|
| $F$ | Fuerza gravitatoria |
| $G$ | Constante de gravitación universal |
| $M$ | Masa del planeta |
| $m$ | Masa del satélite |
| $r$ | Distancia entre los centros de ambos cuerpos |

Utilizando la segunda ley de Newton:

$$
\vec{F}=m\vec{a}
$$

se obtiene la aceleración gravitatoria:

$$
\vec{a}=-\frac{GM}{r^3}\vec{r}
$$

El signo negativo indica que la aceleración está dirigida hacia el centro del planeta.

---

## 🛰️ Mecánica orbital

La combinación entre la velocidad tangencial del satélite y la aceleración gravitatoria produce el movimiento orbital.

```text
                         velocidad
                            ↑
                            │
                        🛰️ ●
                          ↙
                       gravedad
                        ↙

                     🌍
```

Si la velocidad inicial es adecuada, el satélite cae continuamente hacia el planeta mientras avanza lateralmente, generando una órbita.

Para una órbita circular ideal:

$$
v_{orbital}=\sqrt{\frac{GM}{r}}
$$

Mientras que la velocidad de escape está dada por:

$$
v_{escape}=\sqrt{\frac{2GM}{r}}
$$

---

## ⚡ Energía del sistema

Durante la simulación también se analiza la energía del satélite.

### Energía cinética

$$
E_c=\frac{1}{2}mv^2
$$

### Energía potencial gravitatoria

$$
E_p=-\frac{GMm}{r}
$$

### Energía mecánica

$$
E_m=E_c+E_p
$$

En un sistema ideal:

$$
E_m \approx constante
$$

Esto permite estudiar la **conservación de la energía mecánica** y analizar los errores producidos por los métodos numéricos.

---

## 🔢 Simulación numérica

Las ecuaciones de movimiento se resuelven mediante métodos numéricos.

La simulación divide el tiempo en pequeños intervalos:

$$
\Delta t
$$

y calcula repetidamente:

```text
┌─────────────────────────────┐
│     Posición actual         │
└─────────────┬───────────────┘
              ↓
┌─────────────────────────────┐
│ Distancia Tierra-Satélite   │
└─────────────┬───────────────┘
              ↓
┌─────────────────────────────┐
│   Fuerza gravitatoria       │
└─────────────┬───────────────┘
              ↓
┌─────────────────────────────┐
│       Aceleración           │
└─────────────┬───────────────┘
              ↓
┌─────────────────────────────┐
│     Nueva velocidad         │
└─────────────┬───────────────┘
              ↓
┌─────────────────────────────┐
│      Nueva posición         │
└─────────────┬───────────────┘
              │
              └──────────→ REPETIR
```

---

## 🧮 Métodos numéricos

El proyecto contempla la implementación y comparación de diferentes métodos.

### Método de Euler

$$
\vec{v}_{n+1}
=
\vec{v}_{n}+\vec{a}_{n}\Delta t
$$

$$
\vec{r}_{n+1}
=
\vec{r}_{n}+\vec{v}_{n}\Delta t
$$

### Runge-Kutta de cuarto orden — RK4

Posteriormente se implementará **RK4** para comparar su precisión con Euler.

Uno de los objetivos experimentales será analizar cómo el método numérico y el tamaño de $\Delta t$ afectan la conservación de la energía y la estabilidad de las órbitas.

---

## 🧪 Experimentos

El simulador permitirá realizar diferentes experimentos modificando las condiciones iniciales.

### 💥 1. Impacto

Velocidad orbital insuficiente.

```text
       🛰️
          ↘
             ↘
                🌍
```

### 🟢 2. Órbita circular

Velocidad cercana a la velocidad orbital teórica.

```text
             🛰️
        · · · · · ·
      ·             ·
     ·      🌍       ·
      ·             ·
        · · · · · ·
```

### 🟡 3. Órbita elíptica

El satélite cambia su distancia y velocidad durante la trayectoria.

```text
          · · · · · · · · 🛰️
       ·                   ·
     ·                      ·
    ·     🌍                 ·
     ·                      ·
       ·                   ·
          · · · · · · · ·
```

### 🔵 4. Escape gravitacional

Si la velocidad inicial es suficientemente grande:

```text
                         🛰️
                       ↗
                     ↗
                   ↗

                🌍
```

el objeto puede abandonar una órbita cerrada.

---

## 📊 Resultados y visualizaciones

La simulación permitirá analizar gráficamente:

- Trayectoria orbital $x-y$.
- Posición en función del tiempo.
- Distancia al planeta.
- Velocidad.
- Aceleración.
- Energía cinética.
- Energía potencial gravitatoria.
- Energía mecánica total.
- Error numérico.
- Comparación Euler vs. Runge-Kutta.

---

## 🛠️ Tecnologías

El proyecto está desarrollado utilizando **Python 3** y herramientas científicas para cálculo, simulación y visualización.

| Tecnología | Utilización |
|---|---|
| 🐍 Python | Lenguaje principal |
| 🔢 NumPy | Vectores y cálculo numérico |
| 📊 Matplotlib | Gráficos y visualización |
| 🧪 SciPy | Herramientas científicas y comparación numérica |
| 📐 Math | Operaciones matemáticas |
| 🎮 Pygame | Interfaz y animación 2D *(planificado)* |

---

## 🧱 Programación orientada a objetos

El proyecto utilizará clases para representar los componentes físicos.

```text
                  SistemaOrbital
                        │
             ┌──────────┴──────────┐
             │                     │
          Planeta               Satelite
             │                     │
             ├─ masa               ├─ masa
             ├─ radio              ├─ posición
             └─ posición           ├─ velocidad
                                   └─ aceleración
```

Esto permitirá ampliar posteriormente el simulador incorporando nuevos cuerpos celestes.

---

## 📁 Estructura del proyecto

La estructura evolucionará durante el desarrollo:

```text
orbital-simulator-2d/
│
├── main.py
│
├── src/
│   ├── cuerpos.py
│   ├── fisica.py
│   ├── metodos_numericos.py
│   └── simulacion.py
│
├── graficos/
│
├── requirements.txt
│
└── README.md
```

---

## 🚧 Estado del proyecto

```text
[████░░░░░░░░░░░░░░░░] En desarrollo
```

### Etapas

- [x] Definición del fenómeno físico.
- [x] Selección del modelo gravitacional.
- [x] Definición de magnitudes y unidades.
- [ ] Implementación de clases.
- [ ] Implementación de gravitación 2D.
- [ ] Método de Euler.
- [ ] Visualización de la primera órbita.
- [ ] Cálculo de energía.
- [ ] Runge-Kutta RK4.
- [ ] Comparación de métodos numéricos.
- [ ] Animación 2D.
- [ ] Interfaz interactiva.
- [ ] Análisis de resultados.
- [ ] Documentación final.

---

## ❓ Preguntas de investigación

La simulación buscará responder preguntas como:

> **¿Qué velocidad necesita un satélite para permanecer en órbita a una determinada altura?**

> **¿Cómo cambia la trayectoria al modificar la velocidad inicial?**

> **¿Qué condiciones producen una órbita circular, una órbita elíptica, un impacto o una trayectoria de escape?**

> **¿Se conserva la energía mecánica durante una simulación numérica?**

> **¿Qué diferencias existen entre los métodos de Euler y Runge-Kutta al simular una órbita durante largos períodos?**

---

## 🔭 Posibles extensiones

Una vez construido el modelo principal, el simulador podría ampliarse para incorporar:

- 🌙 Sistema Tierra-Luna.
- ☀️ Órbitas planetarias.
- 🚀 Transferencias orbitales.
- ☄️ Trayectorias de asteroides.
- 🪐 Sistemas de múltiples cuerpos.
- 🌌 Problema de los tres cuerpos.
- 🛰️ Diferentes satélites simultáneamente.

---

## 🎓 Contexto académico

Proyecto desarrollado como **Trabajo Final Integrador de Física** de la carrera de **Ingeniería en Informática**.

El objetivo es integrar conceptos físicos con programación científica, métodos numéricos, modelado computacional y visualización de datos.

---

<div align="center">

### 🌍 + 🐍 = 🛰️

**Física · Programación · Simulación**

*“Modelar para comprender.”*

</div>