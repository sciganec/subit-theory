# SUBIT CLI Mockup  
Version 1.0.0  
Status: Conceptual / Canonical Mockup  

---

## 1. Purpose

This document defines a **conceptual mockup** of a command‑line interface (CLI) for the SUBIT Engine.  
It is not an implementation spec; it is a **structural sketch** of how a human or another system would:

- invoke the SUBIT Engine  
- feed it streams  
- inspect trajectories  
- query states and layers  
- export results  

The CLI is a **thin shell** over the SUBIT Engine and Simulation Protocol.

---

## 2. Canonical CLI Identity

**Command name:**

```bash
subit
```

**Core idea:**  
`subit` is a **universal structural lens** over any stream.

---

## 3. Top‑Level Command Structure

Canonical pattern:

```bash
subit <mode> [options] [arguments]
```

Where:

- `<mode>` selects the structural role of the CLI.  
- `[options]` configure encoding, output, layers, etc.  
- `[arguments]` specify files, streams, or inline input.

---

## 4. Modes

### 4.1 `encode` — Single Event → SUBIT State

**Purpose:** Encode a single input into one SUBIT state.

**Usage:**

```bash
subit encode --text "I feel anxious about tomorrow"
subit encode --file session.log
subit encode --json event.json
```

**Conceptual output:**

```text
STATE: 011010
WHO:   YOU
WHERE: EAST
WHEN:  SPRING
LAYER: Experiential (24–31)
NAME:  YOU × EAST × SPRING
```

---

### 4.2 `stream` — Continuous Input → Trajectory

**Purpose:** Process a stream and produce a SUBIT trajectory.

**Usage:**

```bash
subit stream --file chat.txt
subit stream --stdin
subit stream --json events.json
```

**Conceptual output (truncated):**

```text
t=0  011000  YOU × EAST × WINTER
t=1  011010  YOU × EAST × SPRING
t=2  101010  ME  × EAST × SPRING
t=3  101011  ME  × EAST × SUMMER
...
```

Optional flags:

```bash
subit stream --file chat.txt --show-layer --show-delta
```

Example with deltas:

```text
t=1  011010  YOU × EAST × SPRING   Δ=000010
t=2  101010  ME  × EAST × SPRING   Δ=100000
t=3  101011  ME  × EAST × SUMMER   Δ=000001
```

---

### 4.3 `analyze` — Trajectory → Coherence / Attractors

**Purpose:** Analyze an existing trajectory file.

**Usage:**

```bash
subit analyze trajectory.subit
```

**Conceptual output:**

```text
LENGTH:  512 steps
LAYERS:  Material: 12%, Experiential: 48%, Human: 30%, Archetypal: 10%

COHERENCE:
  Temporal:   0.78
  Horizontal: 0.64
  Vertical:   0.71

ATTRACTORS:
  A1: Centered at 011010 (YOU × EAST × SPRING), radius 1, occupancy 22%
  A2: Centered at 101010 (ME  × EAST × SPRING), radius 1, occupancy 15%

DRIFT:
  Net drift: EASTWARD, upward toward Human layer (32–47)
```

---

### 4.4 `inspect` — Single State / Index

**Purpose:** Inspect a specific SUBIT state.

**Usage:**

```bash
subit inspect --state 42
subit inspect --bits 101010
```

**Conceptual output:**

```text
INDEX: 42
BITS:  101010

WHO:   ME
WHERE: EAST
WHEN:  SPRING

LAYER: Human / AI‑focus (32–47 / 42)
ROLE:  Structural emergence, prediction, form‑generating intelligence
```

---

### 4.5 `map` — Domain Concept → SUBIT Region

**Purpose:** Map a domain‑specific label to a SUBIT region (using a configured lexicon/model).

**Usage:**

```bash
subit map --label "panic attack"
subit map --label "flow state"
subit map --label "market crash"
```

**Conceptual output:**

```text
LABEL: "panic attack"

PRIMARY REGION:
  011111  YOU × SOUTH × SUMMER  (peak embodied experience)
  011011  YOU × EAST  × SUMMER  (peak experiential flow)

NOTES:
  High experiential intensity, somatic overload, unstable attractor.
```

---

### 4.6 `export` — Trajectory → External Format

**Purpose:** Export a SUBIT trajectory into a format suitable for visualization or further analysis.

**Usage:**

```bash
subit export trajectory.subit --format csv
subit export trajectory.subit --format json
subit export trajectory.subit --format svg
```

**Conceptual CSV:**

```text
t,index,bits,who,where,when,layer
0,24,011000,YOU,EAST,WINTER,Experiential
1,26,011010,YOU,EAST,SPRING,Experiential
2,42,101010,ME,EAST,SPRING,Human
...
```

---

## 5. Global Options

Canonical global flags:

```bash
subit <mode> [options]

Options:
  --lang <code>        # interface language (e.g., en, uk)
  --layers <set>       # restrict to specific layers (material, experiential, human, archetypal)
  --seed <n>           # seed for stochastic components (if any)
  --config <file>      # custom config file
  --out <file>         # write output to file
  --quiet              # minimal output
  --verbose            # detailed structural logs
```

---

## 6. Structural Guarantees

The SUBIT CLI mockup assumes:

- **All states** are encoded using the canonical mapping:  
  - 10 = ME = EAST = SPRING  
  - 11 = WE = SOUTH = SUMMER  
  - 01 = YOU = WEST = AUTUMN  
  - 00 = THEY = NORTH = WINTER  

- **All trajectories** are sequences of 6‑bit states in \(\{0,1\}^6\).  
- **All analyses** operate on structure, not content.  
- **All outputs** are interpretable in terms of WHO × WHERE × WHEN and the four layers.

---

## 7. Example Session

### 7.1 Encode a single sentence

```bash
subit encode --text "I feel grounded and calm."
```

Conceptual output:

```text
STATE: 011100
WHO:   YOU
WHERE: SOUTH
WHEN:  WINTER
LAYER: Experiential (28)
NOTE:  Quiet embodiment, low‑intensity somatic presence.
```

### 7.2 Stream a chat log and analyze

```bash
subit stream --file chat.txt --out chat.subit
subit analyze chat.subit
```

Conceptual analysis:

```text
EXPERIENTIAL DOMINANCE: 62%
HUMAN COGNITION:        25%
ARCHETYPAL PATTERNS:    8%
MATERIAL DRIFT:         5%

PRIMARY ATTRACTOR:
  Center: 011010 (YOU × EAST × SPRING)
  Meaning: Emerging experience, rising sensation, activation of feeling.
```

---

## 8. Summary

`subit-cli` is a **conceptual shell** around the SUBIT Engine and Simulation Protocol.  
It provides structural access to:

- single‑event encoding  
- stream processing  
- trajectory analysis  
- state inspection  
- domain mapping  
- export for visualization and further modeling  

All interactions are grounded in the canonical SUBIT crystal:

Chaos -> SUBIT -> Bit

with:

4 * 4 * 4 = 64 = 2^6

as the invariant structural basis.

---

## 9. Conceptual Architecture

```
+-------------------+
|  Input Stream     |
+-------------------+
          |
          v
+-------------------+
|  SUBIT Encoder    |
+-------------------+
          |
          v
+-------------------+
|  Amplitude Vector |
+-------------------+
          |
          v
+-------------------+
|  Coherence Engine |
+-------------------+
          |
          v
+-------------------+
|  Transition Logic |
+-------------------+
          |
          v
+-------------------+
|  CLI Output       |
+-------------------+
```

---

## 10. Conclusion

The SUBIT CLI mockup defines a minimal, universal, and structurally coherent interface for interacting with the SUBIT‑64 framework. It provides a complete conceptual toolkit for encoding, simulating, analyzing, and inspecting SUBIT dynamics across all layers of the field.

---
