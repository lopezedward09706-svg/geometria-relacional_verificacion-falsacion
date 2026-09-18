Verificación y falsación sistemática del corpus Geometría Relacional (RG): 108 ecuaciones clasificadas como postulados. Método por ecuación: enunciado, abstract técnico, verificación matemática, contraste con CODATA/PDG/Planck, visualización y veredicto. Registro público de cada paso.

---

## Autor

**Edward P. López** (El Arquitecto)
ORCID: [0009-0009-0717-5536](https://orcid.org/0009-0009-0717-5536)
GitHub: [@lopezedward09706-svg](https://github.com/lopezedward09706-svg)

Asistencia técnica: BRO (compañero de investigación en física teórica).

---

## Naturaleza del proyecto

Este repositorio **no es el corpus RG**. Es el registro independiente del proceso de verificación y falsación del corpus.

- El corpus (postulados, derivaciones previas, formulaciones históricas) vive en los repositorios fuente listados abajo.
- Este repositorio **empieza la verificación desde cero**: cada ecuación se re-deriva, se contrasta y se dictamina sin asumir validez previa.
- Los repositorios fuente se usan como **punto de partida documental**, no como autoridad epistémica.

Regla operativa: *"No validamos por simpatía. No descartamos por escepticismo. Verificamos. Falsamos. Volvemos a verificar. Solo entonces decidimos."*

---

## Fuentes y repositorios de referencia

Material de partida del corpus. Se citan como origen, no como respaldo.

### Corpus RG
- [geometria-relacional-rg](https://github.com/lopezedward09706-svg/geometria-relacional-rg)
- [geometria-relacional-rg-](https://github.com/lopezedward09706-svg/geometria-relacional-rg-)
- [Geometr-a-Relacional-RG-libro-maestro-](https://github.com/lopezedward09706-svg/Geometr-a-Relacional-RG-libro-maestro-)
- [Geometr-a-Relacional-RG-RQNT-Y-ABC-](https://github.com/lopezedward09706-svg/Geometr-a-Relacional-RG-RQNT-Y-ABC-)
- [CENTRO-DE-INFORMACION-TODO-EL-PROCESO-SIN-ESTRUCTURA-](https://github.com/lopezedward09706-svg/CENTRO-DE-INFORMACION-TODO-EL-PROCESO-SIN-ESTRUCTURA-)

### R-QNT (Relational Quantum Network Theory)
- [R-QNT-Emergent-Gravity-o-Relational-Quantum-Network-Theory](https://github.com/lopezedward09706-svg/R-QNT-Emergent-Gravity-o-Relational-Quantum-Network-Theory)
- [RQNTV1.0](https://github.com/lopezedward09706-svg/RQNTV1.0)
- [RQNT-THEORY-EXPLARE-](https://github.com/lopezedward09706-svg/RQNT-THEORY-EXPLARE-)
- [LAB-RQNT](https://github.com/lopezedward09706-svg/LAB-RQNT)
- [Laboratorio-Digital-R-QNT](https://github.com/lopezedward09706-svg/Laboratorio-Digital-R-QNT)

### Proyecto ABC
- [ABC2](https://github.com/lopezedward09706-svg/ABC2)
- [ABC-QUANTUM-](https://github.com/lopezedward09706-svg/ABC-QUANTUM-)
- [PROYECTO-ABC](https://github.com/lopezedward09706-svg/PROYECTO-ABC)
- [Proyecto-ABC-v2.0---Reality-Dashboard](https://github.com/lopezedward09706-svg/Proyecto-ABC-v2.0---Reality-Dashboard)
- [ABC-Theory-Quantum-Gravity-Simulator](https://github.com/lopezedward09706-svg/ABC-Theory-Quantum-Gravity-Simulator)
- [NODOS-ABC](https://github.com/lopezedward09706-svg/NODOS-ABC)
- [communityABC](https://github.com/lopezedward09706-svg/communityABC)

### Perfil y otros
- [Perfil GitHub](https://github.com/lopezedward09706-svg/Edward-P.-L-pez-0009-0009-0717-5536)
- [Academia.edu](https://independent.academia.edu/EdwardLopez143)
- [ANALISIS-DE-DATOS-](https://github.com/lopezedward09706-svg/ANALISIS-DE-DATOS-)
- [Geometr-a-Termogravitacional-cuantica](https://github.com/lopezedward09706-svg/Geometr-a-Termogravitacional-cuantica)
- [PEEREYE-3RE3-](https://github.com/lopezedward09706-svg/PEEREYE-3RE3-)

---

## Método

Cada ecuación se procesa en siete pasos, en orden. No se avanza al siguiente hasta cerrar el veredicto.

1. **Enunciado** — fórmula explícita, notación, dominio de validez.
2. **Abstract físico-técnico** — 3–5 líneas. Qué mide, de dónde surge en RG, cómo se conecta con física establecida.
3. **Verificación matemática** — derivación paso a paso, consistencia dimensional, verificación numérica, casos límite.
4. **Verificación experimental** — contraste con CODATA, PDG, Planck, LIGO. Error relativo si hay dato. Predicción declarada si no lo hay.
5. **Visualización** — script Python ejecutable en Google Colab, 1–3 figuras, interpretación.
6. **Veredicto** — estado asignado con justificación explícita.
7. **Registro** — un `.md` por ecuación, commit por cierre, tag por sesión.

### Semántica de veredictos

| Estado | Significado |
|---|---|
| `[POSTULADO]` | Se acepta como axioma del marco. No se deriva de primeros principios. |
| `[VERIFICADO]` | Coincidencia numérica con dato externo, error relativo declarado, sin parámetros ajustados ad hoc. |
| `[FALSADO]` | Contradicción persistente tras agotar los 5 pasos de terquedad científica. |
| `[PENDIENTE]` | Falta dato, derivación, o enunciado completo. |
| `[INDETERMINADO]` | No falsable con tecnología o datos actuales. |

### Regla de terquedad científica

Un solo dato no mata una teoría. Antes de marcar `[FALSADO]`:

1. Verificar el dato (fuente, precisión, citación).
2. Verificar la interpretación (régimen, conversiones, dimensionalidad).
3. Falsar la falsación (¿falla la teoría o falla el modelo comparativo?).
4. Buscar salida lógica (reformular manteniendo el espíritu, postular y seguir).
5. Decisión final con justificación completa.

Una acumulación de contradicciones no explicadas sí mata. Un solo resultado aislado, no.

---

## Estructura del repositorio

```

RG-108/
├── README.md                    ← este archivo
├── bitacora.md                  ← cronología de sesiones
├── checklist.md                 ← estado de las 108 ecuaciones
├── equations/
│   ├── E001_silencio_armonico.md
│   ├── E002_norma_unidad.md
│   └── ...
├── code/
│   ├── E001_visualization.py
│   └── ...
├── figures/
│   ├── E001_silencio_armonico.png
│   └── ...
└── data/
├── E001_output.txt
└── ...

```

---

## Índice de ecuaciones

Cinco volúmenes, 30 fases, 108 ecuaciones. Estado actualizado en [`checklist.md`](./checklist.md).

| Volumen | Fases | Ecuaciones | Rango |
|---|---|---|---|
| I — Ontología del Silencio | 1–6 | 34 | E1–E34 |
| II — Estructura de la Materia | 7–12 | 24 | E35–E58 |
| III — Constantes Fundamentales | 13–18 | 11 | E59–E69 |
| IV — Cosmología y Gravedad | 19–24 | 18 | E70–E87 |
| V — Observador y Predicciones | 25–30 | 21 | E88–E108 |

Consulta [`checklist.md`](./checklist.md) para el estado individual de cada ecuación.

---

## Reproducir resultados

Todos los scripts son ejecutables en Google Colab. Dependencias mínimas:

```bash
pip install numpy matplotlib scipy sympy networkx plotly
```

Para reproducir una ecuación específica:

```bash
python code/Exxx_visualization.py
```

Los outputs numéricos se guardan en data/, las figuras en figures/.

---

Convenciones

· Commits: [EXXX] Veredicto: <ESTADO>
· Tags: sesion-001, sesion-002, ...
· Archivos de ecuación: Exxx_nombre_descriptivo.md
· Archivos de código: Exxx_visualization.py

---

Licencia
MIT
