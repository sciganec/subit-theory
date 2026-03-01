# subit-cli-spec.md  
Version 1.0.0  
Status: Canonical Specification   

---

## 1. Purpose

This document defines the canonical specification for the SUBIT Command-Line Interface (CLI).  
The CLI is a thin, deterministic shell over the SUBIT Engine and Simulation Protocol.  
Its purpose is to provide structural access to:

- single-event encoding  
- stream processing  
- trajectory analysis  
- state inspection  
- domain mapping  
- export for visualization  

The CLI exposes **structure**, not content.

---

## 2. Canonical Identity

Command name:

```
subit
```

The CLI operates entirely within the SUBIT crystal:

- WHO axis: ME (10), WE (11), YOU (01), THEY (00)  
- WHERE axis: EAST (10), SOUTH (11), WEST (01), NORTH (00)  
- WHEN axis: SPRING (10), SUMMER (11), AUTUMN (01), WINTER (00)

Total states:

```
4 × 4 × 4 = 64 = 2⁶
```

---

## 3. Command Structure

General pattern:

```
subit <mode> [options] [arguments]
```

Where:

- `<mode>` selects the operational domain  
- `[options]` configure behavior  
- `[arguments]` specify input sources  

Modes are deterministic and mutually exclusive.

---

## 4. Modes

---

### 4.1 encode  
Encode a single input into one SUBIT state.

Usage:

```
subit encode --text "I feel calm."
subit encode --file input.txt
subit encode --json event.json
```

Output (conceptual):

```
STATE: 011100
WHO:   YOU
WHERE: SOUTH
WHEN:  WINTER
LAYER: Experiential (28)
```

---

### 4.2 stream  
Process a continuous input stream into a SUBIT trajectory.

Usage:

```
subit stream --file chat.txt
subit stream --stdin
subit stream --json events.json
```

Output (conceptual):

```
t=0  011000  YOU × EAST × WINTER
t=1  011010  YOU × EAST × SPRING
t=2  101010  ME  × EAST × SPRING
t=3  101011  ME  × EAST × SUMMER
```

Optional flags:

```
--show-layer
--show-delta
--limit <n>
```

---

### 4.3 analyze  
Analyze an existing SUBIT trajectory.

Usage:

```
subit analyze trajectory.subit
```

Output (conceptual):

```
LENGTH: 512 steps
LAYERS:
  Material:      12%
  Experiential:  48%
  Human:         30%
  Archetypal:    10%

COHERENCE:
  Temporal:   0.78
  Horizontal: 0.64
  Vertical:   0.71

PRIMARY ATTRACTOR:
  Center: 011010 (YOU × EAST × SPRING)
  Occupancy: 22%
```

---

### 4.4 inspect  
Inspect a single SUBIT state.

Usage:

```
subit inspect --state 42
subit inspect --bits 101010
```

Output:

```
INDEX: 42
BITS:  101010

WHO:   ME
WHERE: EAST
WHEN:  SPRING

LAYER: Human (32–47)
ROLE:  Structural emergence, prediction, generative intelligence
```

---

### 4.5 map  
Map a domain-specific label to a SUBIT region.

Usage:

```
subit map --label "panic attack"
subit map --label "flow state"
```

Output (conceptual):

```
LABEL: panic attack

PRIMARY REGION:
  011111  YOU × SOUTH × SUMMER
  011011  YOU × EAST  × SUMMER
```

---

### 4.6 export  
Export a trajectory into an external format.

Usage:

```
subit export trajectory.subit --format csv
subit export trajectory.subit --format json
```

CSV example:

```
t,index,bits,who,where,when,layer
0,24,011000,YOU,EAST,WINTER,Experiential
1,26,011010,YOU,EAST,SPRING,Experiential
2,42,101010,ME,EAST,SPRING,Human
```

---

## 5. Global Options

```
--lang <code>       # interface language
--layers <set>      # restrict to specific layers
--seed <n>          # seed for deterministic components
--config <file>     # custom config
--out <file>        # write output to file
--quiet             # minimal output
--verbose           # detailed logs
```

---

## 6. Structural Guarantees

The CLI guarantees:

- canonical mapping of bits to WHO/WHERE/WHEN  
- deterministic encoding  
- deterministic transitions  
- stable output formats  
- strict separation of structure and content  
- no semantic interpretation beyond structural extraction  

All states are 6-bit values in the space:

```
{0,1}⁶
```

All trajectories are sequences of such states.

---

## 7. Error Conditions

### Invalid mode

```
ERROR: Unknown mode 'analyse'. Did you mean 'analyze'?
```

### Invalid bits

```
ERROR: Expected 6 bits. Received: 10101
```

### Missing input

```
ERROR: No input provided. Use --text, --file, or --stdin.
```

### Invalid trajectory file

```
ERROR: File is not a valid SUBIT trajectory.
```

---

## 8. Example Session

```
subit encode --text "I feel grounded."
```

Output:

```
STATE: 011100
YOU × SOUTH × WINTER
```

```
subit stream --file chat.txt --out chat.subit
subit analyze chat.subit
```

Output:

```
PRIMARY ATTRACTOR:
  011010 (YOU × EAST × SPRING)
```

---

## 9. Summary

The SUBIT CLI is a deterministic structural interface to the SUBIT Engine.  
It provides canonical access to encoding, streaming, analyzing, inspecting, mapping, and exporting SUBIT states and trajectories.  
All operations are grounded in the invariant structure:

```
Chaos → SUBIT → Bit
```

and the canonical identity:

```
4 × 4 × 4 = 64 = 2⁶
```

---

## 10. Reference Architecture

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

## 11. Conclusion

The SUBIT CLI Specification defines a complete, minimal, and universal interface for interacting with the SUBIT‑64 framework. It ensures deterministic behavior, structural transparency, and coherence‑aligned operations across all layers of the field.

---
