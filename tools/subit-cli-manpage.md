# SUBIT(1) SUBIT CLI Manual | Version 1.0.0

# NAME
subit — command‑line interface for SUBIT‑64 engines, simulations, and coherence analysis

# SYNOPSIS
**subit** <command> [subcommand] [options]

# DESCRIPTION
The **subit** command provides a universal structural interface for interacting with the SUBIT‑64 framework. It supports encoding inputs into SUBIT states, running simulation cycles, analyzing coherence, inspecting internal engine structures, and managing runtime configuration.

All operations are deterministic, minimal, and aligned with the SUBIT ontology.

# COMMANDS

## ENCODE
Encode input into a SUBIT state.

**subit encode input "<string>"**  
 Encode raw input into a 6‑bit SUBIT state.

**subit encode fields --who <WHO> --where <WHERE> --when <WHEN>**  
 Encode structured WHO/WHERE/WHEN fields.

**subit encode state <0–63>**  
 Decode numeric state into WHO/WHERE/WHEN.

Valid WHO: ME, YOU, THEY, IT  
Valid WHERE: NORTH, EAST, SOUTH, WEST  
Valid WHEN: WINTER, SPRING, SUMMER, AUTUMN

---

## SIMULATE
Run SUBIT simulation cycles.

**subit simulate step --input "<string>"**  
 Run a single simulation step.

**subit simulate run --steps <N> --input-stream <file>**  
 Run N steps using a stream of inputs.

**subit simulate loop**  
 Run continuous simulation until interrupted.

Options:  
 **--decay <float>** Amplitude decay factor (0.95–0.999)  
 **--mode <mode>** deterministic | stochastic | hybrid  
 **--seed <int>** Random seed for stochastic mode

---

## ANALYZE
Compute coherence, transitions, and amplitude structure.

**subit analyze coherence <state>**  
 Compute vertical coherence V(i).

**subit analyze transitions <state>**  
 Show transition probabilities from a state.

**subit analyze row <state>**  
 Display coherence matrix row C[state,*].

**subit analyze amplitudes**  
 Show amplitude vector sorted by magnitude.

---

## INSPECT
View internal engine structures.

**subit inspect state**  
 Show current SUBIT state.

**subit inspect amplitudes**  
 Show amplitude vector A[i].

**subit inspect coherence**  
 Show coherence vector V[i].

**subit inspect history --last <N>**  
 Show last N state transitions.

**subit inspect meta**  
 Show engine metadata (version, mode, decay, seed).

---

## UTIL
Utility commands.

**subit util reset**  
 Reset amplitude vector and history.

**subit util export --format <json|yaml|txt>**  
 Export engine state.

**subit util load <file>**  
 Load configuration file.

**subit util validate <file>**  
 Validate configuration file.

---

# OPTIONS
Global options:

**--help**  
 Show help for any command or subcommand.

**--version**  
 Show SUBIT CLI version.

---

# EXIT STATUS
**0** Success  
**1** Invalid arguments  
**2** Invalid state or field  
**3** Configuration error  
**4** Runtime error  

---

# FILES
**~/.subit/config.yaml**  
 Default configuration file.

**~/.subit/history.log**  
 Simulation history (if enabled).

---

# EXAMPLES

Encode input:

```
$ subit encode input "pressure rising"
STATE: 27 (00011011)
```

Run a simulation step:

```
$ subit simulate step --input "pressure rising"
NEXT: 32 (100000)
COHERENCE: 0.934
```

Analyze transitions:

```
$ subit analyze transitions 32
32: 0.41
31: 0.22
42: 0.18
...
```

Inspect amplitudes:

```
$ subit inspect amplitudes
A[32] = 0.91
A[27] = 0.44
A[42] = 0.22
```

---

# SEE ALSO
**subit-cli-spec(1)** — formal CLI specification  
**subit-cli-help(1)** — help output  
**subit-engine(7)** — SUBIT Engine architecture  
**subit-simulation-protocol(7)** — simulation workflow  
**subit-analysis(7)** — coherence and transition analysis

---

SUBIT CLI Manual — minimal, deterministic, coherence‑aligned.
```

---
