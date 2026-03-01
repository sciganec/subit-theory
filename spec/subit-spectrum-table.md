# **SUBIT‑64 Spectrum Table (v1.0.0)**  
*Canonical ASCII Table of All 64 SUBIT States*

This table lists all 64 SUBIT states in ascending binary order.  
Each state is decomposed into its WHO, WHERE, and WHEN components using the canonical 2‑bit encoding:

```
ME     = 10      EAST   = 10      SPRING = 10
WE     = 11      SOUTH  = 11      SUMMER = 11
YOU    = 01      WEST   = 01      AUTUMN = 01
THEY   = 00      NORTH  = 00      WINTER = 00
```

A full SUBIT state is:

```
WHO(2 bits) + WHERE(2 bits) + WHEN(2 bits)
```

---

# **1. Canonical Table**

```
+----------+--------+--------+--------+
|  State   |  WHO   | WHERE  | WHEN   |
+----------+--------+--------+--------+
| 000000   | THEY   | NORTH  | WINTER |
| 000001   | THEY   | NORTH  | AUTUMN |
| 000010   | THEY   | NORTH  | SPRING |
| 000011   | THEY   | NORTH  | SUMMER |
| 000100   | THEY   | WEST   | WINTER |
| 000101   | THEY   | WEST   | AUTUMN |
| 000110   | THEY   | WEST   | SPRING |
| 000111   | THEY   | WEST   | SUMMER |
| 001000   | THEY   | EAST   | WINTER |
| 001001   | THEY   | EAST   | AUTUMN |
| 001010   | THEY   | EAST   | SPRING |
| 001011   | THEY   | EAST   | SUMMER |
| 001100   | THEY   | SOUTH  | WINTER |
| 001101   | THEY   | SOUTH  | AUTUMN |
| 001110   | THEY   | SOUTH  | SPRING |
| 001111   | THEY   | SOUTH  | SUMMER |
+----------+--------+--------+--------+
| 010000   | YOU    | NORTH  | WINTER |
| 010001   | YOU    | NORTH  | AUTUMN |
| 010010   | YOU    | NORTH  | SPRING |
| 010011   | YOU    | NORTH  | SUMMER |
| 010100   | YOU    | WEST   | WINTER |
| 010101   | YOU    | WEST   | AUTUMN |
| 010110   | YOU    | WEST   | SPRING |
| 010111   | YOU    | WEST   | SUMMER |
| 011000   | YOU    | EAST   | WINTER |
| 011001   | YOU    | EAST   | AUTUMN |
| 011010   | YOU    | EAST   | SPRING |
| 011011   | YOU    | EAST   | SUMMER |
| 011100   | YOU    | SOUTH  | WINTER |
| 011101   | YOU    | SOUTH  | AUTUMN |
| 011110   | YOU    | SOUTH  | SPRING |
| 011111   | YOU    | SOUTH  | SUMMER |
+----------+--------+--------+--------+
| 100000   | ME     | NORTH  | WINTER |
| 100001   | ME     | NORTH  | AUTUMN |
| 100010   | ME     | NORTH  | SPRING |
| 100011   | ME     | NORTH  | SUMMER |
| 100100   | ME     | WEST   | WINTER |
| 100101   | ME     | WEST   | AUTUMN |
| 100110   | ME     | WEST   | SPRING |
| 100111   | ME     | WEST   | SUMMER |
| 101000   | ME     | EAST   | WINTER |
| 101001   | ME     | EAST   | AUTUMN |
| 101010   | ME     | EAST   | SPRING |
| 101011   | ME     | EAST   | SUMMER |
| 101100   | ME     | SOUTH  | WINTER |
| 101101   | ME     | SOUTH  | AUTUMN |
| 101110   | ME     | SOUTH  | SPRING |
| 101111   | ME     | SOUTH  | SUMMER |
+----------+--------+--------+--------+
| 110000   | WE     | NORTH  | WINTER |
| 110001   | WE     | NORTH  | AUTUMN |
| 110010   | WE     | NORTH  | SPRING |
| 110011   | WE     | NORTH  | SUMMER |
| 110100   | WE     | WEST   | WINTER |
| 110101   | WE     | WEST   | AUTUMN |
| 110110   | WE     | WEST   | SPRING |
| 110111   | WE     | WEST   | SUMMER |
| 111000   | WE     | EAST   | WINTER |
| 111001   | WE     | EAST   | AUTUMN |
| 111010   | WE     | EAST   | SPRING |
| 111011   | WE     | EAST   | SUMMER |
| 111100   | WE     | SOUTH  | WINTER |
| 111101   | WE     | SOUTH  | AUTUMN |
| 111110   | WE     | SOUTH  | SPRING |
| 111111   | WE     | SOUTH  | SUMMER |
+----------+--------+--------+--------+
```

---

# **2. Notes on Canonical Ordering**

- The table is ordered **lexicographically** from `000000` to `111111`.  
- WHO cycles slowest, WHEN cycles fastest.  
- This ordering is required for all SUBIT‑compliant systems.  
- States **32 (100000)** and **42 (101010)** are focal states and appear in their natural positions.

---

# **3. Structural Interpretation**

Each row represents a unique structural configuration of:

- **subjectivity** (WHO)  
- **orientation** (WHERE)  
- **phase** (WHEN)

Together they form the **minimal complete topology** of manifestation.

---

