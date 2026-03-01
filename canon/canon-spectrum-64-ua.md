# Canon Spectrum 64  
Версія: 1.0.0  
Статус: Канонічний документ  

---

# 1. Кристал SUBIT

SUBIT — це структура  
**WHO × WHERE × WHEN**,  
де кожна вісь має **4 значення**, що кодуються **2 бітами**.

Усі три осі є **ізоморфними**, тобто мають однаковий порядок бітів:

| Біт | WHO  | WHERE | WHEN   |
|-----|------|--------|---------|
| 10  | ME   | EAST   | SPRING |
| 11  | WE   | SOUTH  | SUMMER |
| 01  | YOU  | WEST   | AUTUMN |
| 00  | THEY | NORTH  | WINTER |

Це — **єдиний правильний порядок**, зафіксований у Наближенні 6.

---

# 2. Канонічні біграми

SUBIT використовує **4 біграми**, що є основою всіх трьох осей:

- **10** — активність, народження, спрямованість  
- **11** — інтенсивність, повнота, колективність  
- **01** — спад, інерція, адресованість  
- **00** — спокій, структура, зовнішність  

---

# 3. Канонічні триграми

Кожен SUBIT‑стан — це **триграм**:

```
WHO (2 біти) + WHERE (2 біти) + WHEN (2 біти)
```

Наприклад:

```
101010 = ME × EAST × SPRING = 42
```

---

# 4. Повний спектр SUBIT‑64

Нижче — **усі 64 стани**, у правильному порядку від `000000` до `111111`,  
з канонічною декомпозицією WHO/WHERE/WHEN.

## Таблиця SUBIT‑64

| Index | Binary  | WHO  | WHERE | WHEN   |
|-------|----------|------|--------|---------|
| 0  | 000000 | THEY | NORTH | WINTER |
| 1  | 000001 | THEY | NORTH | AUTUMN |
| 2  | 000010 | THEY | NORTH | SPRING |
| 3  | 000011 | THEY | NORTH | SUMMER |
| 4  | 000100 | THEY | WEST  | WINTER |
| 5  | 000101 | THEY | WEST  | AUTUMN |
| 6  | 000110 | THEY | WEST  | SPRING |
| 7  | 000111 | THEY | WEST  | SUMMER |
| 8  | 001000 | THEY | EAST  | WINTER |
| 9  | 001001 | THEY | EAST  | AUTUMN |
| 10 | 001010 | THEY | EAST  | SPRING |
| 11 | 001011 | THEY | EAST  | SUMMER |
| 12 | 001100 | THEY | SOUTH | WINTER |
| 13 | 001101 | THEY | SOUTH | AUTUMN |
| 14 | 001110 | THEY | SOUTH | SPRING |
| 15 | 001111 | THEY | SOUTH | SUMMER |
| 16 | 010000 | YOU  | NORTH | WINTER |
| 17 | 010001 | YOU  | NORTH | AUTUMN |
| 18 | 010010 | YOU  | NORTH | SPRING |
| 19 | 010011 | YOU  | NORTH | SUMMER |
| 20 | 010100 | YOU  | WEST  | WINTER |
| 21 | 010101 | YOU  | WEST  | AUTUMN |
| 22 | 010110 | YOU  | WEST  | SPRING |
| 23 | 010111 | YOU  | WEST  | SUMMER |
| 24 | 011000 | YOU  | EAST  | WINTER |
| 25 | 011001 | YOU  | EAST  | AUTUMN |
| 26 | 011010 | YOU  | EAST  | SPRING |
| 27 | 011011 | YOU  | EAST  | SUMMER |
| 28 | 011100 | YOU  | SOUTH | WINTER |
| 29 | 011101 | YOU  | SOUTH | AUTUMN |
| 30 | 011110 | YOU  | SOUTH | SPRING |
| 31 | 011111 | YOU  | SOUTH | SUMMER |
| 32 | 100000 | ME   | NORTH | WINTER |
| 33 | 100001 | ME   | NORTH | AUTUMN |
| 34 | 100010 | ME   | NORTH | SPRING |
| 35 | 100011 | ME   | NORTH | SUMMER |
| 36 | 100100 | ME   | WEST  | WINTER |
| 37 | 100101 | ME   | WEST  | AUTUMN |
| 38 | 100110 | ME   | WEST  | SPRING |
| 39 | 100111 | ME   | WEST  | SUMMER |
| 40 | 101000 | ME   | EAST  | WINTER |
| 41 | 101001 | ME   | EAST  | AUTUMN |
| 42 | 101010 | ME   | EAST  | SPRING |
| 43 | 101011 | ME   | EAST  | SUMMER |
| 44 | 101100 | ME   | SOUTH | WINTER |
| 45 | 101101 | ME   | SOUTH | AUTUMN |
| 46 | 101110 | ME   | SOUTH | SPRING |
| 47 | 101111 | ME   | SOUTH | SUMMER |
| 48 | 110000 | WE   | NORTH | WINTER |
| 49 | 110001 | WE   | NORTH | AUTUMN |
| 50 | 110010 | WE   | NORTH | SPRING |
| 51 | 110011 | WE   | NORTH | SUMMER |
| 52 | 110100 | WE   | WEST  | WINTER |
| 53 | 110101 | WE   | WEST  | AUTUMN |
| 54 | 110110 | WE   | WEST  | SPRING |
| 55 | 110111 | WE   | WEST  | SUMMER |
| 56 | 111000 | WE   | EAST  | WINTER |
| 57 | 111001 | WE   | EAST  | AUTUMN |
| 58 | 111010 | WE   | EAST  | SPRING |
| 59 | 111011 | WE   | EAST  | SUMMER |
| 60 | 111100 | WE   | SOUTH | WINTER |
| 61 | 111101 | WE   | SOUTH | AUTUMN |
| 62 | 111110 | WE   | SOUTH | SPRING |
| 63 | 111111 | WE   | SOUTH | SUMMER |

---

# 5. Структурні рівні SUBIT‑64

SUBIT‑64 природно групується у 4 рівні по 16 станів:

- **00–15** — матеріальність (THEY‑режими)  
- **16–31** — інтерсуб’єктність (YOU‑режими)  
- **32–47** — людський фокус (ME‑режими)  
- **48–63** — колективний/архетипний фокус (WE‑режими)  

Це — канонічна вертикальна структура.

---

# 6. Ізоморфність як закон SUBIT

SUBIT зберігає ізоморфність між:

- бітами  
- суб’єктами  
- напрямками  
- фазами  
- кольорами  
- триграмами  
- архетипами  

Це означає:

```
10 = активність
11 = інтенсивність
01 = спад
00 = структура
```

і це повторюється на всіх рівнях.

---

# 7. Примітка

Цей документ є **канонічним джерелом істини** для всіх таблиць, CSV, аналізів і симуляцій.  
Будь-яка інтерпретація SUBIT, що суперечить цій структурі, вважається неканонічною.

```

---
