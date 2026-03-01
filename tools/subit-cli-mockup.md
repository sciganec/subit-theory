# SUBIT CLI Mockup (v1.0.0)
Conceptual Command‑Line Interface for SUBIT Engines, Simulations, and Analysis

---

## 1. Introduction

This document defines a conceptual command‑line interface (CLI) for interacting with the SUBIT‑64 framework. The SUBIT CLI is not tied to any specific programming language or runtime. Instead, it provides a **universal interaction model** for:

- running SUBIT simulations  
- inspecting SUBIT states  
- analyzing coherence  
- encoding inputs  
- generating trajectories  
- debugging SUBIT‑based agents  

The CLI is designed to be minimal, structural, and fully aligned with the SUBIT ontology.

---

## 2. Design Principles

The SUBIT CLI follows these principles:

- **Minimalism** — every command corresponds to a single structural operation.  
- **Transparency** — no hidden state; all internal vectors can be inspected.  
- **Universality** — works for material, experiential, reflective, and archetypal layers.  
- **Determinism** — commands produce predictable, reproducible outputs.  
- **Coherence‑first** — all operations preserve SUBIT structural integrity.

---

## 3. CLI Structure Overview

The CLI is organized into five functional groups:

```
subit encode      # map input → SUBIT state
subit simulate    # run SUBIT simulation cycles
subit analyze     # compute coherence, amplitudes, transitions
subit inspect     # view internal structures
subit util        # helper tools (reset, export, etc.)
```

Each group contains subcommands described below.

---

## 4. Encode Commands

### 4.1. Encode raw input into a SUBIT state

```
subit encode input "some text or signal"
```

Output example:

```
STATE: 32 (100000)
WHO: ME
WHERE: NORTH
WHEN: WINTER
```

### 4.2. Encode structured fields

```
subit encode fields --who ME --where EAST --when SPRING
```

Output:

```
STATE: 42 (101010)
```

### 4.3. Encode from numeric state

```
subit encode state 56
```

Output:

```
STATE: 56 (111000)
WHO: YOU
WHERE: NORTH
WHEN: WINTER
```

---

## 5. Simulation Commands

### 5.1. Run a single simulation step

```
subit simulate step --input "signal"
```

Output:

```
INPUT → STATE: 18 (00010010)
NEXT  → STATE: 32 (100000)
COHERENCE: 0.812
```

### 5.2. Run N simulation steps

```
subit simulate run --steps 50 --input-stream file.txt
```

### 5.3. Run continuous simulation

```
subit simulate loop
```

(Stops with Ctrl+C.)

---

## 6. Analysis Commands

### 6.1. Compute coherence for a state

```
subit analyze coherence 32
```

Output:

```
V(32) = 0.921
Top Coupled States:
  31  (00011111)
  42  (101010)
  00  (000000)
```

### 6.2. Show transition probabilities

```
subit analyze transitions 42
```

Output:

```
P(32) = 0.41
P(56) = 0.27
P(43) = 0.12
...
```

### 6.3. Show full coherence matrix row

```
subit analyze row 18
```

---

## 7. Inspect Commands

### 7.1. Inspect amplitude vector

```
subit inspect amplitudes
```

Output:

```
A[00] = 0.12
A[01] = 0.03
A[32] = 0.88
A[42] = 0.44
...
```

### 7.2. Inspect current state

```
subit inspect state
```

### 7.3. Inspect trajectory history

```
subit inspect history --last 20
```

---

## 8. Utility Commands

### 8.1. Reset the engine

```
subit util reset
```

### 8.2. Export current state

```
subit util export --format json
```

### 8.3. Load configuration

```
subit util load config.yaml
```

---

## 9. Example Session

```
$ subit encode input "I feel pressure rising"
STATE: 27 (00011011)

$ subit simulate step --input "I feel pressure rising"
NEXT: 32 (100000)

$ subit analyze coherence 32
V(32) = 0.934

$ subit inspect amplitudes
A[32] = 0.91
A[27] = 0.44
A[42] = 0.22
```

This demonstrates a typical SUBIT workflow: encode → simulate → analyze → inspect.

---

## 10. Conceptual Architecture

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

## 11. Conclusion

The SUBIT CLI mockup defines a minimal, universal, and structurally coherent interface for interacting with the SUBIT‑64 framework. It provides a complete conceptual toolkit for encoding, simulating, analyzing, and inspecting SUBIT dynamics across all layers of the field.

---
