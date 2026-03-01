# SUBIT CLI — Help (v1.0.0)
Universal Command‑Line Interface for SUBIT‑64 Engines, Simulations, and Analysis

Usage:
  subit <command> [subcommand] [options]

SUBIT is a structural interface for encoding inputs, running simulations, analyzing coherence, and inspecting the internal state of a SUBIT Engine. All commands are deterministic, minimal, and coherence‑aligned.

---

## Commands

  encode       Encode input into a SUBIT state
  simulate     Run SUBIT simulation cycles
  analyze      Compute coherence, transitions, amplitudes
  inspect      View internal engine structures
  util         Utility commands (reset, export, config)
  help         Show help for any command or subcommand

Run `subit help <command>` for details.

---

## encode — Input → SUBIT State

Usage:
  subit encode input "<string>"
  subit encode fields --who <WHO> --where <WHERE> --when <WHEN>
  subit encode state <0–63>

Options:
  --who        ME | YOU | THEY | IT
  --where      NORTH | EAST | SOUTH | WEST
  --when       WINTER | SPRING | SUMMER | AUTUMN

Examples:
  subit encode input "pressure rising"
  subit encode fields --who ME --where EAST --when SPRING
  subit encode state 42

---

## simulate — Run SUBIT Simulation

Usage:
  subit simulate step --input "<string>"
  subit simulate run --steps <N> --input-stream <file>
  subit simulate loop

Options:
  --decay <float>        Amplitude decay factor (0.95–0.999)
  --mode <mode>          deterministic | stochastic | hybrid
  --seed <int>           Random seed for stochastic mode

Examples:
  subit simulate step --input "signal"
  subit simulate run --steps 100 --input-stream data.txt
  subit simulate loop

---

## analyze — Coherence, Transitions, Amplitudes

Usage:
  subit analyze coherence <state>
  subit analyze transitions <state>
  subit analyze row <state>
  subit analyze amplitudes

Descriptions:
  coherence     Compute V(i) for a given state
  transitions   Show transition probabilities from a state
  row           Display coherence matrix row C[state,*]
  amplitudes    Show amplitude vector sorted by magnitude

Examples:
  subit analyze coherence 32
  subit analyze transitions 42
  subit analyze amplitudes

---

## inspect — Internal Engine Structures

Usage:
  subit inspect state
  subit inspect amplitudes
  subit inspect coherence
  subit inspect history --last <N>
  subit inspect meta

Descriptions:
  state         Show current SUBIT state
  amplitudes    Show amplitude vector A[i]
  coherence     Show coherence vector V[i]
  history       Show recent state transitions
  meta          Show engine metadata

Examples:
  subit inspect state
  subit inspect history --last 20

---

## util — Utility Tools

Usage:
  subit util reset
  subit util export --format <json|yaml|txt>
  subit util load <file>
  subit util validate <file>

Descriptions:
  reset         Clear amplitude vector and history
  export        Export engine state
  load          Load configuration file
  validate      Validate configuration file

Examples:
  subit util reset
  subit util export --format json

---

## help — Display Help

Usage:
  subit help
  subit help <command>
  subit help <command> <subcommand>

Examples:
  subit help encode
  subit help simulate run

---

## WHO / WHERE / WHEN Reference

WHO:
  ME, YOU, THEY, IT

WHERE:
  NORTH, EAST, SOUTH, WEST

WHEN:
  WINTER, SPRING, SUMMER, AUTUMN

---

## Exit Codes

  0   Success
  1   Invalid arguments
  2   Invalid state or field
  3   Configuration error
  4   Runtime error

---

## Example Session

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

---
