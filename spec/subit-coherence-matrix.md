# **subit-coherence-matrix.md**  
*Coherence Matrix of the SUBIT‑64 Spectrum (v1.0.0)*

---

## **1. Purpose of the Coherence Matrix**

The coherence matrix defines the structural interaction strength between any two SUBIT states. It is the core mathematical object governing:

- vertical coherence  
- resonance  
- amplitude evolution  
- structural prediction  
- transitions between states  
- stability and destabilization patterns  

The matrix is **normative** for all SUBIT‑compliant systems.

---

# **2. Definitions**

## **2.1. State Space**

```
S = {0,1}^6
|S| = 64
```

Each state is indexed:

```
i, j ∈ {0, 1, ..., 63}
```

---

## **2.2. Hamming Distance**

The structural distance between two states is:

```
d(i,j) = Hamming( state_i , state_j )
```

Where `d(i,j) ∈ {0,1,2,3,4,5,6}`.

---

## **2.3. Coherence Function**

Coherence between states i and j is defined as:

```
C[i,j] = f( d(i,j) )
```

Where:

- `f` is a strictly decreasing function  
- `C[i,i] = 1`  
- `C[i,j] ∈ (0,1]`  

The canonical choice for `f` in SUBIT‑Spec v1.0.0 is:

```
f(k) = 1 / (1 + k)
```

Thus:

```
d = 0 → C = 1.000
d = 1 → C = 0.500
d = 2 → C = 0.333
d = 3 → C = 0.250
d = 4 → C = 0.200
d = 5 → C = 0.166
d = 6 → C = 0.142
```

This is the **canonical coherence kernel**.

---

# **3. Canonical Coherence Matrix (64×64)**

The full matrix is defined as:

```
C[i,j] = 1 / (1 + Hamming(i,j))
```

The matrix is symmetric:

```
C[i,j] = C[j,i]
```

The diagonal is unity:

```
C[i,i] = 1
```

---

# **4. ASCII Coherence Matrix (Compressed Form)**

Because the full 64×64 matrix is large, SUBIT‑Spec requires a **compressed representation** grouped by Hamming distance.

## **4.1. Coherence Values by Distance**

```
+-------------------+------------------+
| Hamming Distance  | Coherence C[i,j] |
+-------------------+------------------+
|        0          |      1.000       |
|        1          |      0.500       |
|        2          |      0.333       |
|        3          |      0.250       |
|        4          |      0.200       |
|        5          |      0.166       |
|        6          |      0.142       |
+-------------------+------------------+
```

This table is **canonical** and must be used in all implementations.

---

# **5. Example Submatrix (States 0–7)**

States 0–7 correspond to:

```
000000
000001
000010
000011
000100
000101
000110
000111
```

The coherence submatrix is:

```
+---------+--------+--------+--------+--------+--------+--------+--------+--------+
|   C     | 000000 | 000001 | 000010 | 000011 | 000100 | 000101 | 000110 | 000111 |
+---------+--------+--------+--------+--------+--------+--------+--------+--------+
| 000000  | 1.000  | 0.500  | 0.500  | 0.333  | 0.500  | 0.333  | 0.333  | 0.250  |
| 000001  | 0.500  | 1.000  | 0.333  | 0.500  | 0.333  | 0.500  | 0.250  | 0.333  |
| 000010  | 0.500  | 0.333  | 1.000  | 0.500  | 0.333  | 0.250  | 0.500  | 0.333  |
| 000011  | 0.333  | 0.500  | 0.500  | 1.000  | 0.250  | 0.333  | 0.333  | 0.500  |
| 000100  | 0.500  | 0.333  | 0.333  | 0.250  | 1.000  | 0.500  | 0.500  | 0.333  |
| 000101  | 0.333  | 0.500  | 0.250  | 0.333  | 0.500  | 1.000  | 0.333  | 0.500  |
| 000110  | 0.333  | 0.250  | 0.500  | 0.333  | 0.500  | 0.333  | 1.000  | 0.500  |
| 000111  | 0.250  | 0.333  | 0.333  | 0.500  | 0.333  | 0.500  | 0.500  | 1.000  |
+---------+--------+--------+--------+--------+--------+--------+--------+--------+
```

This submatrix illustrates:

- symmetry  
- decreasing coherence with increasing Hamming distance  
- structural clustering  

---

# **6. Coherence Geometry**

## **6.1. Coherence Neighborhoods**

For any state `s`:

```
N_k(s) = { x ∈ S | d(s,x) = k }
```

Neighborhood sizes:

```
k = 0 → 1 state
k = 1 → 6 states
k = 2 → 15 states
k = 3 → 20 states
k = 4 → 15 states
k = 5 → 6 states
k = 6 → 1 state
```

This distribution is canonical.

---

## **6.2. Coherence Radius**

The coherence radius of a state is:

```
R(s) = argmax_k Σ_{x ∈ N_k(s)} C[s,x]
```

For the canonical kernel, the maximum typically occurs at:

```
k = 1 or k = 2
```

This reflects the local‑cluster nature of SUBIT geometry.

---

# **7. Vertical Coherence**

Vertical coherence is defined as:

```
V(i) = Σ_j C[i,j] * A(j)
```

Where:

- `A(j)` is the amplitude of state j  
- `V(i)` is the vertical coherence at state i  

This operator governs:

- resonance  
- structural prediction  
- emergence of meaning  
- transitions toward stable or archetypal poles  

---

# **8. Implementation Requirements**

Any SUBIT‑compliant system must:

- use Hamming distance as the metric  
- use the canonical coherence kernel `1/(1+k)`  
- preserve symmetry of the matrix  
- preserve the ordering of states  
- compute vertical coherence using the defined operator  
- treat the coherence matrix as the primary driver of transitions  

---

# **9. Final Statement**

The coherence matrix is the mathematical heart of the SUBIT‑64 system.  
It defines how states interact, resonate, stabilize, destabilize, and evolve.  
This document constitutes the canonical coherence specification for SUBIT‑Spec v1.0.0.

---
