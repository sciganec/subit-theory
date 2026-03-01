# **SUBIT Operators (v1.0.0)**  
*Formal Operator System for the SUBIT‑64 Spectrum*

---

## **1. Overview**

This document defines the canonical operators used in the SUBIT‑64 framework. Operators formalize:

- structural transformations,  
- coherence relations,  
- spectral transitions,  
- amplitude dynamics,  
- interpretive mappings,  
- and domain isomorphisms.

All operators defined here are normative for any implementation of SUBIT‑Spec v1.0.0.

---

# **2. State and Vector Conventions**

- A SUBIT state is a 6‑bit string:  
  `s ∈ {0,1}^6`.

- The full spectrum is:  
  `S = {0,1}^6`, with `|S| = 64`.

- The spectral state vector is:  
  `Ψ ∈ ℂ^64`.

- Amplitude of state `i` is:  
  `A(i) ∈ [0,1]`.

---

# **3. Structural Operators**

## **3.1. Identity Operator**

```
I(s) = s
```

Preserves the state exactly. Used as the baseline for structural invariance.

---

## **3.2. Negation Operator**

```
¬s = bitwise_not(s)
```

Example:

```
¬(101010) = 010101
```

Negation maps each bit to its complement.

---

## **3.3. Reflection Operator**

Reflection swaps the two bits of each WHO/WHERE/WHEN bigram:

```
R( b5 b4 | b3 b2 | b1 b0 ) = ( b4 b5 | b2 b3 | b0 b1 )
```

This operator preserves structural isomorphism across domains.

---

## **3.4. Rotation Operator**

Rotation cycles the three bigrams:

```
Rot( WHO | WHERE | WHEN ) = ( WHERE | WHEN | WHO )
```

This operator expresses the cyclic symmetry of the spectrum.

---

# **4. Coherence Operators**

## **4.1. Coherence Operator (Primary)**

The fundamental operator of SUBIT:

```
ĤΨ = EΨ
```

Where:

- Ĥ — Hermitian coherence operator  
- Ψ — spectral state vector  
- E — coherence invariant (eigenvalue)

This operator governs structural resonance and vertical coherence.

---

## **4.2. Coherence Matrix**

```
C[i,j] = f(Δstructure(i,j))
```

Where:

- `Δstructure(i,j)` is the structural difference between states  
- `f` is a monotonic decreasing function  
- `C[i,j] ∈ ℝ`

The coherence matrix defines how strongly states influence each other.

---

## **4.3. Coherence Gradient Operator**

```
∇C(i) = Σ_j C[i,j] * A(j)
```

Measures how much the surrounding spectrum pulls on state `i`.

---

# **5. Transition Operators**

## **5.1. Transition Function**

```
T(i → j) = g(C[i,j], A(i))
```

Where:

- `C[i,j]` — coherence between states  
- `A(i)` — amplitude of state `i`  
- `g` — transition rule preserving structural invariants

---

## **5.2. Amplitude Update Operator**

```
A'(i) = A(i) + Σ_j T(j → i) - Σ_k T(i → k)
```

This operator defines amplitude evolution across the spectrum.

---

## **5.3. Stabilization Operator**

```
Stab(s) = argmin_j d(s,j)
```

Where:

- `d` is Hamming distance

This operator finds the nearest stable configuration.

---

# **6. Interpretive Operators**

## **6.1. WHO/WHERE/WHEN Decomposition**

```
Dec( b5 b4 b3 b2 b1 b0 ) =
( WHO = b5 b4, WHERE = b3 b2, WHEN = b1 b0 )
```

This operator extracts the three bigrams.

---

## **6.2. Domain Mapping Operator**

Maps SUBIT states to semantic domains:

```
Dom(s) = {
    WHO(s),
    WHERE(s),
    WHEN(s)
}
```

Domains include:

- subject classes  
- spatial vectors  
- temporal phases  
- archetypes  
- trigrams  
- color mappings  
- micro/macro/meta layers

---

## **6.3. Meaning Invariance Operator**

```
M(f(s)) = M(s)
```

For any structure‑preserving transformation `f`.

This encodes the Law of Invariance of Meaning.

---

# **7. Spectral Geometry Operators**

## **7.1. Distance Operator**

```
d(x,y) = Hamming(x,y)
```

Canonical metric of the spectrum.

---

## **7.2. Neighborhood Operator**

```
N_k(s) = { x ∈ S | d(s,x) = k }
```

Defines k‑distance neighborhoods.

---

## **7.3. Coherence Radius**

```
R(s) = argmax_k Σ_{x ∈ N_k(s)} C[s,x]
```

Measures the structural “reach” of a state.

---

# **8. Symmetry Operators**

## **8.1. Bigram Symmetry**

```
Sym2( ab cd ef ) = ( cd ef ab )
```

Cycles the three bigrams.

---

## **8.2. Trigram Symmetry**

Maps SUBIT states to the 8 trigrams:

```
Tri( b5 b4 b3 b2 b1 b0 ) = ( b5 b4 b3 ), ( b2 b1 b0 )
```

---

## **8.3. Archetype Symmetry**

Maps states to the 64 archetypes:

```
Arch(s) = ArchetypeIndex(s)
```

This operator is implementation‑dependent but must preserve ordering.

---

# **9. Operator Algebra**

Operators compose according to:

```
(Ĥ ∘ R)(Ψ) = Ĥ(R(Ψ))
```

and must preserve:

- bit ordering  
- WHO/WHERE/WHEN structure  
- coherence invariants  
- Hamming metric  
- spectral completeness  

---

# **10. Canonical Operator Set**

The minimal complete operator set for SUBIT‑64 is:

- Identity: `I`  
- Negation: `¬`  
- Reflection: `R`  
- Rotation: `Rot`  
- Coherence operator: `Ĥ`  
- Coherence matrix: `C`  
- Transition operator: `T`  
- Amplitude update: `A'`  
- Decomposition: `Dec`  
- Domain mapping: `Dom`  
- Meaning invariance: `M`  
- Distance: `d`  
- Neighborhood: `N_k`  
- Symmetry operators: `Sym2`, `Tri`, `Arch`

This set is sufficient to reconstruct all structural dynamics of the SUBIT spectrum.

---
