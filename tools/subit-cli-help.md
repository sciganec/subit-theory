# subit-cli-help.md  
Version 1.0.0  
Status: Canonical Help Output  

---

## NAME
subit — command‑line interface for the SUBIT Engine

---

## SYNOPSIS
```
subit <mode> [options] [arguments]
```

Modes are deterministic and mutually exclusive.  
All outputs follow the canonical SUBIT mapping:

- WHO: 10 = ME, 11 = WE, 01 = YOU, 00 = THEY  
- WHERE: 10 = EAST, 11 = SOUTH, 01 = WEST, 00 = NORTH  
- WHEN: 10 = SPRING, 11 = SUMMER, 01 = AUTUMN, 00 = WINTER  

Total state space:

```
4 × 4 × 4 = 64 = 2⁶
```

---

## DESCRIPTION
`subit` provides structural access to the SUBIT Engine.  
It encodes events, processes streams, analyzes trajectories, inspects states, maps domain concepts, and exports results.  
The CLI exposes **structure**, not content.

---

## MODES

### encode
Encode a single input into one SUBIT state.

Usage:
```
subit encode --text "<string>"
subit encode --file <path>
subit encode --json <path>
```

Example output:
```
STATE: 011100
YOU × SOUTH × WINTER
LAYER: Experiential (28)
```

---

### stream
Process a continuous input stream into a SUBIT trajectory.

Usage:
```
subit stream --file <path>
subit stream --stdin
subit stream --json <path>
```

Example:
```
t=0  011000  YOU × EAST × WINTER
t=1  011010  YOU × EAST × SPRING
t=2  101010  ME  × EAST × SPRING
```

Options:
```
--show-layer
--show-delta
--limit <n>
```

---

### analyze
Analyze a SUBIT trajectory file.

Usage:
```
subit analyze <trajectory.subit>
```

Example:
```
LENGTH: 512 steps
TEMPORAL COHERENCE:   0.78
HORIZONTAL COHERENCE: 0.64
VERTICAL COHERENCE:   0.71

PRIMARY ATTRACTOR:
  011010 (YOU × EAST × SPRING)
```

---

### inspect
Inspect a single SUBIT state.

Usage:
```
subit inspect --state <index>
subit inspect --bits <6-bit>
```

Example:
```
INDEX: 42
BITS:  101010
ME × EAST × SPRING
LAYER: Human (32–47)
```

---

### map
Map a domain-specific label to a SUBIT region.

Usage:
```
subit map --label "<string>"
```

Example:
```
LABEL: panic attack
PRIMARY REGION:
  011111  YOU × SOUTH × SUMMER
  011011  YOU × EAST  × SUMMER
```

---

### export
Export a trajectory into an external format.

Usage:
```
subit export <trajectory.subit> --format csv
subit export <trajectory.subit> --format json
```

CSV example:
```
t,index,bits,who,where,when,layer
0,24,011000,YOU,EAST,WINTER,Experiential
1,26,011010,YOU,EAST,SPRING,Experiential
2,42,101010,ME,EAST,SPRING,Human
```

---

## GLOBAL OPTIONS
```
--lang <code>       interface language
--layers <set>      restrict to specific layers
--seed <n>          deterministic seed
--config <file>     custom config file
--out <file>        write output to file
--quiet             minimal output
--verbose           detailed logs
```

---

## EXIT STATUS
```
0   success
1   general error
2   invalid arguments
3   invalid input format
4   invalid trajectory file
```

---

## ERRORS

### Unknown mode
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

### Invalid trajectory
```
ERROR: File is not a valid SUBIT trajectory.
```

---

## EXAMPLES

Encode:
```
subit encode --text "I feel grounded."
```

Stream + analyze:
```
subit stream --file chat.txt --out chat.subit
subit analyze chat.subit
```

Inspect:
```
subit inspect --state 42
```

---
