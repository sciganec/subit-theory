# SUBIT CLI Specification (v1.0.0)
Formal Specification for the SUBIT Command‑Line Interface

---

## 1. Overview

The SUBIT CLI is a universal command‑line interface for interacting with the SUBIT‑64 framework. It provides a minimal, structural, and deterministic set of commands for:

- encoding inputs into SUBIT states  
- running SUBIT simulations  
- analyzing coherence and transitions  
- inspecting internal engine structures  
- managing configurations and runtime state  

This specification defines the canonical behavior, flags, output formats, and error conditions for all commands.

---

## 2. Design Goals

The SUBIT CLI adheres to the following principles:

- **Minimality** — each command performs one structural operation.  
- **Determinism** — identical inputs produce identical outputs.  
- **Transparency** — internal vectors and states are always inspectable.  
- **Universality** — works across all SUBIT layers (material → archetypal).  
- **Coherence‑first** — all operations preserve SUBIT structural integrity.  
- **Human‑readable** — outputs are clear, aligned with SUBIT terminology.  

---

## 3. Command Groups

The CLI is organized into five groups:

```
subit encode      # input → SUBIT state
subit simulate    # run SUBIT simulation cycles
subit analyze     # compute coherence, transitions, amplitudes
subit inspect     # view internal engine structures
subit util        # helper tools (reset, export, config)
```

Each group contains subcommands defined below.

---

## 4. Encode Commands

### 4.1. Encode raw input

```
subit encode input "<string>"
```

Maps arbitrary input into a SUBIT state using structural encoding.

**Output format:**

```
STATE: <id> (<binary>)
WHO: <label>
WHERE: <label>
WHEN: <label>
```

### 4.2. Encode structured fields

```
subit encode fields --who <ME|YOU|THEY|IT> --where <NORTH|EAST|SOUTH|WEST> --when <WINTER|SPRING|SUMMER|AUTUMN>
```

Produces a deterministic 6‑bit state.

### 4.3. Encode numeric state

```
subit encode state <0–63>
```

Decodes the 6‑bit structure into WHO/WHERE/WHEN.

---

## 5. Simulation Commands

### 5.1. Single simulation step

```
subit simulate step --input "<string>"
```

Runs one full SUBIT Engine cycle.

**Output format:**

```
INPUT → STATE: <id>
NEXT  → STATE: <id>
COHERENCE: <float>
```

### 5.2. Multi‑step simulation

```
subit simulate run --steps <N> --input-stream <file>
```

Processes a sequence of inputs.

### 5.3. Continuous simulation loop

```
subit simulate loop
```

Runs indefinitely until interrupted.

### 5.4. Simulation flags

- `--decay <float>` — amplitude decay factor  
- `--mode <deterministic|stochastic|hybrid>`  
- `--seed <int>` — random seed for stochastic mode  

---

## 6. Analysis Commands

### 6.1. Coherence of a state

```
subit analyze coherence <state>
```

Computes:

```
V(i) = SUM_{j=0..63} C[i,j] * A(j)
```

### 6.2. Transition probabilities

```
subit analyze transitions <state>
```

Outputs:

```
P(i) = V(i) / SUM(V)
```

### 6.3. Coherence matrix row

```
subit analyze row <state>
```

### 6.4. Full amplitude ranking

```
subit analyze amplitudes
```

Sorted descending by A(i).

---

## 7. Inspect Commands

### 7.1. Current state

```
subit inspect state
```

### 7.2. Amplitude vector

```
subit inspect amplitudes
```

### 7.3. Coherence vector

```
subit inspect coherence
```

### 7.4. Trajectory history

```
subit inspect history --last <N>
```

### 7.5. Engine metadata

```
subit inspect meta
```

Outputs:
- engine version  
- decay factor  
- simulation mode  
- seed  
- timestamp  

---

## 8. Utility Commands

### 8.1. Reset engine

```
subit util reset
```

Clears amplitude vector and history.

### 8.2. Export engine state

```
subit util export --format <json|yaml|txt>
```

### 8.3. Load configuration

```
subit util load <file>
```

### 8.4. Validate configuration

```
subit util validate <file>
```

---

## 9. Output Specification

### 9.1. State Format

```
<id> (<binary>)  # e.g., 32 (100000)
```

### 9.2. Coherence Format

```
V(<state>) = <float>
```

### 9.3. Transition Format

```
<state>: <probability>
```

### 9.4. Amplitude Format

```
A[<state>] = <float>
```

### 9.5. Error Format

```
ERROR: <message>
HINT: <suggestion>
```

---

## 10. Error Conditions

### 10.1. Invalid state

```
ERROR: Invalid state index.
HINT: Use a value between 0 and 63.
```

### 10.2. Invalid field

```
ERROR: Unknown WHO/WHERE/WHEN value.
HINT: Valid WHO values: ME, YOU, THEY, IT.
```

### 10.3. Missing input

```
ERROR: No input provided.
HINT: Use --input "<string>".
```

### 10.4. Invalid configuration

```
ERROR: Configuration file malformed.
HINT: Run 'subit util validate <file>'.
```

---

## 11. Example Session

```
$ subit encode input "pressure rising"
STATE: 27 (00011011)

$ subit simulate step --input "pressure rising"
NEXT: 32 (100000)
COHERENCE: 0.934

$ subit analyze transitions 32
32: 0.41
31: 0.22
42: 0.18
...

$ subit inspect amplitudes
A[32] = 0.91
A[27] = 0.44
A[42] = 0.22
```

---

## 12. Reference Architecture

```
+-------------------+
|  SUBIT CLI        |
+-------------------+
          |
          v
+-------------------+
|  Command Parser   |
+-------------------+
          |
          v
+-------------------+
|  SUBIT Engine     |
+-------------------+
          |
          v
+-------------------+
|  Simulation Core  |
+-------------------+
          |
          v
+-------------------+
|  Analyzer / Inspector |
+-------------------+
          |
          v
+-------------------+
|  Output Formatter |
+-------------------+
```

---

## 13. Conclusion

The SUBIT CLI Specification defines a complete, minimal, and universal interface for interacting with the SUBIT‑64 framework. It ensures deterministic behavior, structural transparency, and coherence‑aligned operations across all layers of the field.

---
