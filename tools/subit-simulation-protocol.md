# SUBIT Simulation Protocol  
Version 1.0.0  
Status: Canonical  

---

## 1. Purpose of the Simulation Protocol

The SUBIT Simulation Protocol defines how a system processes continuous input over time by converting it into a trajectory through the 64‑state SUBIT space. It specifies the rules for encoding, transitioning, updating, and evaluating SUBIT states in a dynamic environment. The protocol is substrate‑independent and applies equally to physical, cognitive, computational, ecological, symbolic, and agent‑based systems.

---

## 2. SUBIT as the Simulation Substrate

SUBIT is defined as:

\[
\text{SUBIT} = \text{WHO} \times \text{WHERE} \times \text{WHEN}
\]

Each axis has four canonical values encoded by two bits:

| Bits | WHO  | WHERE | WHEN   |
|------|------|--------|---------|
| 10   | ME   | EAST   | SPRING |
| 11   | WE   | SOUTH  | SUMMER |
| 01   | YOU  | WEST   | AUTUMN |
| 00   | THEY | NORTH  | WINTER |

This yields:

\[
4 \times 4 \times 4 = 64 = 2^6
\]

Each SUBIT state is a 6‑bit trigram:

```
WHO (2 bits) + WHERE (2 bits) + WHEN (2 bits)
```

The simulation operates entirely within this 64‑state structural space.

---

## 3. Simulation Loop Overview

A SUBIT simulation consists of a repeating loop with four canonical stages:

1. Perception — receive input from the environment.  
2. Encoding — convert input into a SUBIT state.  
3. Transition — update the system’s internal state.  
4. Evaluation — compute coherence, drift, and attractors.

This loop runs continuously, producing a structural trajectory.

---

## 4. Stage 1: Perception

The simulation receives an input event. This may be:

- a sensory signal  
- a text fragment  
- a system log  
- a behavioral action  
- an environmental change  
- an internal cognitive shift  

The protocol does not constrain the input format. Everything is treated as a structural event.

---

## 5. Stage 2: SUBIT Encoding

The engine extracts three structural components:

- WHO — subject position  
- WHERE — directional vector  
- WHEN — temporal phase  

The encoding step produces a single SUBIT state:

\[
S_t = (WHO_t, WHERE_t, WHEN_t)
\]

Example (canonical):

```
101010 = ME × EAST × SPRING
```

This is the system’s structural interpretation of the input at time t.

---

## 6. Stage 3: State Transition

Given the previous state \(S_{t-1}\) and the new state \(S_t\), the simulation computes:

### Transition Vector  
A 6‑bit difference:

\[
\Delta_t = S_t \oplus S_{t-1}
\]

Example (canonical):

```
Previous: 000000 = THEY × NORTH × WINTER
Current:  000010 = THEY × NORTH × SPRING
Δ = 000010
```

### Coherence  
A measure of structural alignment:

- vertical coherence (layer alignment)  
- horizontal coherence (Hamming proximity)  
- temporal coherence (trajectory smoothness)  

### Drift  
A measure of directional change across time.

### Attractor Detection  
If the system repeatedly returns to a region of the crystal, an attractor is formed.

The transition step updates the system’s internal memory and structural momentum.

---

## 7. Stage 4: Evaluation

The simulation evaluates:

- state quality — how stable or unstable the current state is  
- trajectory quality — how coherent the recent sequence is  
- layer transitions — whether the system is moving between material, experiential, human, or archetypal layers  
- emergent patterns — cycles, oscillations, attractors, bifurcations  

Evaluation does not modify the state; it informs the next iteration.

---

## 8. Multi‑Agent Simulation

The protocol supports multi‑agent environments. Each agent:

- maintains its own SUBIT state  
- processes its own input  
- generates its own trajectory  

Agents interact structurally:

- one agent’s output becomes another agent’s input  
- coherence between agents is measured  
- shared attractors may form  
- divergence indicates structural conflict  

Multi‑agent SUBIT simulations model communication, coordination, conflict, and collective intelligence.

---

## 9. Environmental Dynamics

The environment itself may be represented as a SUBIT state or trajectory. This allows:

- environmental drift  
- environmental attractors  
- environmental coherence  
- agent–environment coupling  

The environment becomes a structural participant in the simulation.

---

## 10. Simulation Termination Conditions

A simulation may terminate when:

- a fixed point is reached  
- an attractor stabilizes  
- coherence exceeds a threshold  
- drift exceeds a threshold  
- a predefined number of steps is completed  
- an external event interrupts the loop  

Termination is not required; SUBIT simulations may run indefinitely.

---

## 11. SUBIT Simulation as a Universal Framework

The protocol applies to:

- cognitive simulations  
- behavioral simulations  
- ecological simulations  
- symbolic simulations  
- narrative simulations  
- agent‑based simulations  
- system‑level simulations  

SUBIT provides a universal structural language for all of them.

---

## 12. Summary

The SUBIT Simulation Protocol defines how a system:

- perceives input  
- encodes it structurally  
- transitions through the 64‑state crystal  
- evaluates coherence and drift  
- forms attractors  
- interacts with other agents  
- interacts with its environment  

It is a substrate‑independent framework for modeling structure, meaning, behavior, and systems across all domains.

---
