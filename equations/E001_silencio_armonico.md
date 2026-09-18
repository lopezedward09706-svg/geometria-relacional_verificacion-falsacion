---


```markdown
# E001 — Silencio Armónico

## Enunciado

**Ĥ|0⟩ = 0**

Notación:
- `Ĥ`: operador Hamiltoniano autoadjunto sobre el espacio de Hilbert 𝓗.
- `|0⟩`: vector de estado en 𝓗, llamado "estado de silencio" o "vacío primordial".
- `0`: vector nulo de 𝓗.

Dominio de validez: todo 𝓗. Sin restricción sobre Ĥ más allá de autoadjunción.

## Abstract físico-técnico

La ecuación postula la existencia de un estado `|0⟩` aniquilado por el Hamiltoniano. En QFT estándar, el vacío se define por `a_k|0⟩ = 0` (aniquilación modal), y típicamente `Ĥ|0⟩ = E₀|0⟩` con `E₀ ≠ 0` (energía de punto cero, formalmente divergente). Fijar `E₀ = 0` es una elección de origen de energía (normal ordering). En RG, E1 se presenta como axioma fundacional: el "silencio armónico" es el estado sin excitación ni oscilación neta. Funciona como **definición** del vacío en el marco, no como derivación.

## Verificación matemática

### Consistencia algebraica

Ĥ autoadjunto ⇒ espectro real, autovectores ortogonales completos. La ecuación dice: `0 ∈ σ(Ĥ)` y `|0⟩` es autovector asociado.

Toda matriz hermitiana tiene al menos un autovalor real `E_min`. Para que `E_min = 0`, se requiere una condición adicional sobre Ĥ: que el mínimo del espectro esté exactamente en cero.

**Sin embargo:** dado cualquier `Ĥ` con `E_min ≠ 0`, se define `Ĥ' = Ĥ − E_min·𝕀`, y entonces `Ĥ'|0⟩ = 0`. Por lo tanto E1 **es siempre alcanzable** por redefinición del origen de energía. No impone restricción sobre el espectro salvo la elección de origen.

### Consistencia dimensional

- `[Ĥ] = energía = M L² T⁻²`
- `[|0⟩] = adimensional` (vector normalizado)
- `[Ĥ|0⟩] = energía`
- `[0] = energía` (el vector nulo hereda las unidades del espacio vectorial)

Consistente. No hay desbalance.

### Casos límite

| Caso | Comportamiento |
|---|---|
| `Ĥ = 0` | Cualquier `|0⟩` satisface. Trivial. |
| Oscilador armónico `Ĥ = ħω(a†a + ½)` | `E_min = ħω/2 ≠ 0`. E1 falla sin normal ordering. Con `:Ĥ: = ħω a†a`, E1 se satisface. |
| Espectro con gap positivo | E1 no se satisface sin shift. |
| Espectro continuo desde 0 | E1 se satisface si 0 está en el espectro y `|0⟩` es estado base. |

### Verificación numérica

Oscilador armónico con `ħω = 1`, base de Fock truncada a `N = 10`:

- Sin shift: `E = {0.5, 1.5, 2.5, ...}`, `E_min = 0.5`.
- Con shift (normal ordering): `E = {0, 1, 2, ...}`, `E_min = 0`.

Ver salida en `data/E001_output.txt`.

### Conclusión matemática

E1 es **matemáticamente admisible** y **siempre alcanzable por convención**. No es derivación; es elección de origen de energía.

## Verificación experimental

**No hay test experimental directo.** La energía absoluta del vacío no es medible en aislamiento; solo diferencias (efecto Casimir, Lamb shift) son medibles. La elección `E₀ = 0` no resuelve el problema de la constante cosmológica (que es de gravedad, no de QFT en espacio plano; ver E76–E77).

**Predicción falsable asociada:** ninguna desde E1 aislada.

## Visualización

Ver `code/E001_visualization.py`. Genera `figures/E001_oscilador_shift.png`.

Interpretación: se muestra el espectro del oscilador armónico con y sin shift del origen. El panel izquierdo ilustra que sin normal ordering, `E₀ = ħω/2 ≠ 0` y E1 falla. El panel derecho muestra que con `:Ĥ:`, E1 se satisface por construcción. La figura es pedagógica: **E1 no es un resultado físico, es una elección de marco**.

## Veredicto

**Estado: `[POSTULADO]`**

Justificación:
- Matemáticamente consistente y admisible.
- No derivable de primeros principios: es elección de origen de energía.
- No falsable aislada: sin test experimental directo.
- Función en RG: definir el vacío como estado de energía cero. Es ancla ontológica del sistema, no resultado empírico.

Clasificación: **postulado definicional** (axioma de origen).

## Notas

- **Conexión con E2:** E1 no dice nada sobre la norma de `|0⟩`. E2 la fija en 1.
- **Conexión con E3:** `[Ĥ, P̂(0)]|0⟩ = 0` **no se sigue** solo de E1. De `Ĥ|0⟩ = 0` se obtiene `[Ĥ, P̂]|0⟩ = Ĥ P̂|0⟩ − P̂·0 = Ĥ P̂|0⟩`, que es cero solo si además `P̂|0⟩ ∈ ker(Ĥ)`. E3 requiere postulado adicional.
- **Conexión con E4:** el Hamiltoniano de red `Ĥ = Σ J[1−cos(Δψ)]` tiene mínimo en `Δψ = 0` con valor 0. E1 se satisface automáticamente si `|0⟩` es el estado de fases uniformes.
- **Equivalencia conocida:** la elección `E₀ = 0` es exactamente el normal ordering de QFT de campos libres. No es nueva; es convención estándar.
```

---

2. code/E001_visualization.py

```python
"""
E001 — Silencio Armónico: Ĥ|0⟩ = 0

Compara el espectro de un oscilador armónico con energía de punto cero
no nula versus uno normal-ordenado (E₀ = 0).

Salidas:
  figures/E001_oscilador_shift.png
  data/E001_output.txt
"""

import os
import numpy as np
import matplotlib.pyplot as plt

# Asegurar carpetas
os.makedirs("figures", exist_ok=True)
os.makedirs("data", exist_ok=True)

# ---------- Parámetros ----------
hbar_omega = 1.0     # cuanto de energía
N          = 10      # truncamiento de la base de Fock
x          = np.linspace(-4, 4, 400)

# ---------- Espectros ----------
n = np.arange(N)
E_sin_shift = hbar_omega * (n + 0.5)   # E_n = ħω(n + 1/2)
E_con_shift = hbar_omega * n           # normal ordering

# ---------- Potencial y estado base ----------
m, omega = 1.0, 1.0  # ħ = 1
V    = 0.5 * m * omega**2 * x**2
psi0 = (m*omega/np.pi)**0.25 * np.exp(-m*omega*x**2/2)

# ---------- Figura ----------
fig, axes = plt.subplots(1, 2, figsize=(12, 5), sharey=True)

for ax, E, title in zip(
    axes,
    [E_sin_shift, E_con_shift],
    ["Sin shift:  E₀ = ħω/2 ≠ 0", "Normal ordering:  E₀ = 0"]
):
    ax.plot(x, V, color="#2C3E50", lw=2, label="V(x) = ½mω²x²")
    for i, Ei in enumerate(E):
        ax.hlines(Ei, -3.5, 3.5, color="#E74C3C", alpha=0.6, lw=1)
        ax.text(3.6, Ei, f"n={i}", va="center", fontsize=9, color="#E74C3C")
    ax.plot(x, V + 0.5*V.max()*psi0**2 * 4,
            color="#3498DB", lw=2, label="|ψ₀|² (escalada)")
    ax.set_xlabel("x")
    ax.set_title(title)
    ax.set_ylim(-0.5, 6)
    ax.grid(alpha=0.3)
    ax.legend(loc="upper left", fontsize=9)

axes[0].set_ylabel("E / ħω")
fig.suptitle("E001 — Silencio Armónico: Ĥ|0⟩ = 0", fontsize=14, y=1.02)
fig.tight_layout()
fig.savefig("figures/E001_oscilador_shift.png", dpi=140, bbox_inches="tight")
print("Figura guardada: figures/E001_oscilador_shift.png")

# ---------- Output numérico ----------
with open("data/E001_output.txt", "w") as f:
    f.write("E001 — Silencio Armónico: Ĥ|0⟩ = 0\n")
    f.write("=" * 45 + "\n\n")
    f.write(f"Base de Fock truncada a N = {N}\n")
    f.write(f"ħω = {hbar_omega}\n\n")
    f.write("Espectro sin shift (E_n = ħω(n + 1/2)):\n")
    for i, Ei in enumerate(E_sin_shift):
        f.write(f"  n={i:2d}   E = {Ei:.6f}\n")
    f.write("\nEspectro con shift (E_n = ħω·n):\n")
    for i, Ei in enumerate(E_con_shift):
        f.write(f"  n={i:2d}   E = {Ei:.6f}\n")
    f.write(f"\nE_min sin shift: {E_sin_shift[0]:.6f}\n")
    f.write(f"E_min con shift: {E_con_shift[0]:.6f}\n")
    f.write("\nConclusion:\n")
    f.write("  Sin shift, Ĥ|0> = (ħω/2)|0> != 0. E1 falla.\n")
    f.write("  Con shift, Ĥ|0> = 0. E1 se satisface por convencion.\n")
    f.write("  E1 es eleccion de origen de energia, no resultado fisico.\n")

print("Datos guardados:  data/E001_output.txt")
```

Ejecutable en Colab con pip install numpy matplotlib (ya vienen por defecto).

---

3. Actualizaciones a archivos existentes

checklist.md — línea E1:

```diff
- - [ ] **E1** — Silencio Armónico: `Ĥ|0⟩ = 0` — `[POSTULADO]`
+ - [x] **E1** — Silencio Armónico: `Ĥ|0⟩ = 0` — `[POSTULADO]`
```

Y contador:

```diff
- **Estado global:** Cerradas: 0 / 108
+ **Estado global:** Cerradas: 1 / 108
```

bitacora.md — añadir al final, antes de *Fin de sesiones registradas.*:

```markdown
## Sesión 001 — 17 sep 2026 — E1 (Silencio Armónico)

**Duración:** ~40 min
**Ecuación trabajada:** E1
**Resultado:** `[POSTULADO]`
**Archivos generados:**
- `equations/E001_silencio_armonico.md`
- `code/E001_visualization.py`
- `figures/E001_oscilador_shift.png`
- `data/E001_output.txt`

**Notas:**
- E1 es admisible matemáticamente y siempre alcanzable por convención (shift del origen de energía).
- Se verifica que E1 **no implica E3**: `[Ĥ, P̂(0)]|0⟩ = 0` requiere postulado adicional (`P̂|0⟩ ∈ ker(Ĥ)`).
- Se verifica que E1 es **equivalente al normal ordering** de QFT de campos libres. No es novedad técnica, sí es declaración ontológica en RG.
- Sin predicción falsable asociada desde E1 aislada.

**Siguiente paso propuesto:** Sesión 002 — E2 (Norma Unidad).
```

Y actualizar el marcador inferior:

```diff
- *Fin de sesiones registradas.*
+ *Fin de sesiones registradas: Sesión 001.*
```

README.md — dos líneas:

```diff
- **Estado:** 0 / 108 ecuaciones cerradas · Última actualización: 17 sep 2026
+ **Estado:** 1 / 108 ecuaciones cerradas · Última actualización: 17 sep 2026
```

```diff
- | I — Ontología del Silencio | 1–6 | 34 | E1–E34 | 0 / 34 |
+ | I — Ontología del Silencio | 1–6 | 34 | E1–E34 | 1 / 34 |
```

---

4. Commit y tag

```
Commit: [E001] Veredicto: POSTULADO
Tag:    sesion-001
```

---

