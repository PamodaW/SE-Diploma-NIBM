# DSE 19.1P Computer Technology (19 Oct 2019) – Model Answers

Answer all questions. Full theory: `CT Common Theory - Answers.md` (Tx).

---

## Question 01 – MCQ (16 × 2 marks)

| No. | Answer | Reason |
|---|---|---|
| 1 | **A** fixed resistors | Resistance cannot be changed |
| 2 | **B** same | Series circuit has only one path |
| 3 | **D** 10 Ω | 1/R = 1/20 + 1/30 + 1/60 = (3 + 2 + 1)/60 = 6/60 → R = 10 Ω |
| 4 | **C** 15 Ω | Series (combined): 5 + 10 = 15 Ω |
| 5 | **A** 5 Ω | Equal resistors in parallel: R/n = 10/2 |
| 6 | **B** low resistance | Ammeter is in series; must not reduce the current |
| 7 | **D** 1.25 mA | I = V/R = 15 / (5k + 7k) = 15/12 000 |
| 8 | **C** 5 V, 7 V (see note) | V5k = 1.25 mA × 5k = 6.25 V, V7k = 8.75 V |
| 9 | **A** capacitor | Stores charge (Q = CV) |
| 10 | **c** 100 Hz | Half-wave ripple = input frequency |
| 11 | **a** 100 Hz | Full-wave ripple = 2 × input frequency |
| 12 | **d** All of the mentioned | Adders compute addresses, indices, ++/−− |
| 13 | **a** 2 | Half adder inputs A and B |
| 14 | **b** Addition | Carry comes from addition (subtraction gives borrow) |
| 15 | **c** A XOR B | Sum = A ⊕ B |
| 16 | **a** A AND B | Carry = A·B |

Note on Q8: the correct voltages are 6.25 V and 8.75 V (they must add to 15 V). None of the options is exactly right; **C (5 V, 7 V)** is the only one in the correct 5 : 7 ratio, so it is the intended answer. It is worth writing the working in the exam.

---

## Question 02 – Half adder (25 marks)

### a.1) Truth table (8 marks)
| A | B | Carry | Sum |
|---|---|---|---|
| 0 | 0 | 0 | 0 |
| 0 | 1 | 0 | 1 |
| 1 | 0 | 0 | 1 |
| 1 | 1 | 1 | 0 |

### a.2) K-maps (10 marks)
**Carry**
| A \ B | 0 | 1 |
|---|---|---|
| 0 | 0 | 0 |
| 1 | 0 | **1** |

Single 1 at A=1, B=1 → no grouping possible → Carry = A·B

**Sum**
| A \ B | 0 | 1 |
|---|---|---|
| 0 | 0 | **1** |
| 1 | **1** | 0 |

The two 1s are diagonal (not adjacent) → cannot be grouped → Sum = A'B + AB'

### a.3) Boolean expressions (4 marks)
- **SUM = A'B + AB' = A ⊕ B**
- **CARRY = A·B**

### a.4) Logic circuit (3 marks)
```
 A ──┬──────────\\‾‾\
     │           ))XOR >──── SUM
 B ──┼──┬───────//__/
     │  │
     │  └──────┐‾‾‾\
     └─────────┤AND )──── CARRY
               └___/
```
One **XOR** gate (inputs A, B → Sum) and one **AND** gate (inputs A, B → Carry). If drawn from the SOP form: two NOT gates, two AND gates (A'B, AB') and an OR gate for Sum, plus an AND gate for Carry.

---

## Question 03 (16 marks)

### Circuit 1: 6 V with 15 Ω, 20 Ω, 25 Ω in series
**b.1)** R_T = 15 + 20 + 25 = **60 Ω**
**b.2)** I = V / R_T = 6 / 60 = **0.1 A (100 mA)**

### Circuit 2: 12 V with three 24 Ω resistors in parallel
**b.1)** 1/R_T = 1/24 + 1/24 + 1/24 = 3/24 → R_T = **8 Ω**
**b.2)** Point A carries the total current: I = 12 / 8 = **1.5 A** (0.5 A through each 24 Ω resistor).

---

## Question 04 (5 marks) – 6 V, R = 1.5 kΩ, two Si diodes in series

**c.1)** Both diodes point in the direction of conventional current from the battery's positive terminal, through R, down through the diodes and back to the negative terminal, so **both diodes are forward biased**.

**c.2)** Each Si diode drops 0.7 V:
- V_R = 6 − (0.7 + 0.7) = **4.6 V**
- I = V_R / R = 4.6 / 1500 = **3.07 mA**

(If the battery were the other way round, both diodes would be reverse biased and I ≈ 0.)

---

## Question 05 (12 marks) – VCC = 12 V, RC = 4.7 kΩ, RB = 565 kΩ
Collector loop: VCE = VCC − IC·RC

**I. IC = 2.5 mA**
VCE = 12 − (2.5 mA × 4.7 kΩ) = 12 − 11.75 = **0.25 V** (almost saturated)

**II. VCE = 2.6 V**
IC = (VCC − VCE) / RC = (12 − 2.6) / 4.7 kΩ = 9.4 / 4700 = **2.0 mA**

**III. IC = 0**
VCE = 12 − 0 = **12 V** (cut-off, VCE = VCC)

(These are points on the DC load line: saturation end IC(sat) ≈ 12/4.7k = 2.55 mA, cut-off end VCE = 12 V. For reference, IB = (12 − 0.7)/565 kΩ = 20 µA.)

---

## Question 06 (10 marks)

### E.1) Half-wave rectifier (single diode D1 and R_L)
- 0–180° (positive half cycle): D1 forward biased → Vout follows Vin (peak ≈ +Amax − 0.7 V).
- 180–360° (negative half cycle): D1 reverse biased → **Vout = 0**.

Output: positive half-sine humps separated by flat zero sections, same period T as the input.
```
Vout  /\        /\
     /  \      /  \
 ___/    \____/    \____   time
    0   T/2   T   3T/2  2T
```

### E.2) Bridge full-wave rectifier (D1–D4, transformer, R_L)
- Positive half cycle: two diodes (D1 and D2) conduct → current through R_L top to bottom.
- Negative half cycle: the other two diodes (D3 and D4) conduct → current through R_L **in the same direction**.

Output: every half cycle appears positive – continuous positive humps, **two humps per input period** (ripple frequency = 2 × input frequency). Peak ≈ Vm − 1.4 V.
```
Vout  /\  /\  /\  /\
     /  \/  \/  \/  \
 ___/                \__  time
    0  T/2  T  3T/2  2T
```
