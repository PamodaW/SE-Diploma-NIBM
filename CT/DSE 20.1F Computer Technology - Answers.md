# DSE 20.1F Computer Technology (24 Feb 2021) – Model Answers

Full theory with diagrams: `CT Common Theory - Answers.md` (Tx). X' means NOT X.

---

## Question 1

### (a)(i) Z = NOT[ NOT(P + NOT(Q + R)) + NOT(P'·Q' + NOT(P·Q)) ]
(Overbars as printed: one bar over everything, one bar over each bracket, a bar over (Q + R), bars on P and Q, and a bar over P·Q. The extra ")" in the paper is a typo.)

Let X = P + (Q + R)' and Y = P'Q' + (PQ)'. Then Z = (X' + Y')' = **X·Y** (De Morgan: (X' + Y')' = X''·Y'').

- X = P + (Q + R)' = **P + Q'R'** (De Morgan: (Q + R)' = Q'R')
- (PQ)' = P' + Q' (De Morgan), so Y = P'Q' + P' + Q' = **P' + Q'** (P'Q' is absorbed)

Z = (P + Q'R')(P' + Q')
 = PP' + PQ' + P'Q'R' + Q'Q'R'
 = 0 + PQ' + P'Q'R' + Q'R'
 = PQ' + Q'R'(P' + 1)
 = PQ' + Q'R'

**Z = Q'(P + R')**

### (a)(ii) A = NOT[ NOT(X + Y) + NOT(X'·NOT(Y + Z)) ]
Using (M' + N')' = M·N:
A = (X + Y)·(X'·(Y + Z)')
 = (X + Y)·X'·Y'·Z' (De Morgan: (Y + Z)' = Y'Z')
 = XX'Y'Z' + X'YY'Z'
 = 0 + 0

**A = 0**

### (b) Z = Σm(1, 2, 3, 8, 9, 11, 12, 14, 15) + d(4, 7, 10)

#### (i) K-map
|AB \ CD| 00 | 01 | 11 | 10 |
|---|---|---|---|---|
| **00** | 0 | 1 | 1 | 1 |
| **01** | X | 0 | X | 0 |
| **11** | 1 | 0 | 1 | 1 |
| **10** | 1 | 1 | 1 | X |

Groups:
- m1, m3, m9, m11 → **B'D**
- m2, m3, m10, m11 → **B'C**
- m8, m10, m12, m14 (corners of rows 11/10, columns 00/10) → **AD'**
- m3, m7, m11, m15 (column CD = 11) → **CD**

**Z = B'D + B'C + AD' + CD** (CD may be replaced by AC; both cover m15.)

#### (ii) Tabular method
**Column 1** (✓ = combined later)
| Group | Minterms (ABCD) |
|---|---|
| 1 | 1 (0001) ✓, 2 (0010) ✓, 4d (0100) ✓, 8 (1000) ✓ |
| 2 | 3 (0011) ✓, 9 (1001) ✓, 10d (1010) ✓, 12 (1100) ✓ |
| 3 | 7d (0111) ✓, 11 (1011) ✓, 14 (1110) ✓ |
| 4 | 15 (1111) ✓ |

**Column 2** (pairs)
| Group | Pairs |
|---|---|
| 1 | 1,3 (00-1) ✓; 1,9 (-001) ✓; 2,3 (001-) ✓; 2,10 (-010) ✓; **4,12 (-100) PI**; 8,9 (100-) ✓; 8,10 (10-0) ✓; 8,12 (1-00) ✓ |
| 2 | 3,7 (0-11) ✓; 3,11 (-011) ✓; 9,11 (10-1) ✓; 10,11 (101-) ✓; 10,14 (1-10) ✓; 12,14 (11-0) ✓ |
| 3 | 7,15 (-111) ✓; 11,15 (1-11) ✓; 14,15 (111-) ✓ |

**Column 3** (quads) – all prime implicants
| Quad | Term |
|---|---|
| 1,3,9,11 (-0-1) | B'D |
| 2,3,10,11 (-01-) | B'C |
| 8,9,10,11 (10--) | AB' |
| 8,10,12,14 (1--0) | AD' |
| 3,7,11,15 (--11) | CD |
| 10,11,14,15 (1-1-) | AC |

Plus BC'D' (4,12) from column 2.

**Prime implicant chart** (real minterms only)
| PI | 1 | 2 | 3 | 8 | 9 | 11 | 12 | 14 | 15 |
|---|---|---|---|---|---|---|---|---|---|
| BC'D' | | | | | | | X | | |
| B'D | ⊗ | | X | | X | X | | | |
| B'C | | ⊗ | X | | | X | | | |
| CD | | | X | | | X | | | X |
| AB' | | | | X | X | X | | | |
| AD' | | | | X | | | X | X | |
| AC | | | | | | X | | X | X |

- **B'D** essential (only cover of 1); **B'C** essential (only cover of 2).
- They cover 1, 2, 3, 9, 11. Remaining: 8, 12, 14, 15.
- **AD'** covers 8, 12, 14 in one term. 15 needs **CD** (or AC).

**Z = B'D + B'C + AD' + CD** – same as the K-map.

---

## Question 2

### (a) Full adder from 2 half adders and an OR gate (see T8)
- HA1: A, B → S1 = A ⊕ B, C1 = AB
- HA2: S1, Cin → **Sum = A ⊕ B ⊕ Cin**, C2 = (A ⊕ B)Cin
- OR: **Cout = C1 + C2 = AB + (A ⊕ B)Cin**

Draw two half-adder boxes in cascade, and an OR gate taking the two carries.

### (b) Train brake (inputs ES1, ES2, S1, S2; output BR)
BR = ES1 + ES2 + S1·S2

**i. Truth table**
| m | ES1 | ES2 | S1 | S2 | BR |
|---|---|---|---|---|---|
| 0 | 0 | 0 | 0 | 0 | 0 |
| 1 | 0 | 0 | 0 | 1 | 0 |
| 2 | 0 | 0 | 1 | 0 | 0 |
| 3 | 0 | 0 | 1 | 1 | 1 |
| 4–7 | 0 | 1 | x | x | 1 |
| 8–15 | 1 | x | x | x | 1 |

(Write all 16 rows in the exam: rows 4–15 are all 1.)

**ii. Simplified POS**
Zeros at m0, m1, m2 only. K-map of zeros:
- m0, m1 → ES1'ES2'S1' → maxterm (ES1 + ES2 + S1)
- m0, m2 → ES1'ES2'S2' → maxterm (ES1 + ES2 + S2)

**BR = (ES1 + ES2 + S1)(ES1 + ES2 + S2)**

**iii(a). NOR only**
- G1 = NOR(ES1, ES2, S1)
- G2 = NOR(ES1, ES2, S2)
- **BR = NOR(G1, G2)**
(3 NOR gates. Check: NOR(G1, G2) = G1'·G2' = (ES1+ES2+S1)(ES1+ES2+S2).)

**iii(b). Multiplexer** – 8:1 MUX, selects S2 S1 S0 = ES1 ES2 S1, data from S2:
| ES1 ES2 S1 | BR (S2=0) | BR (S2=1) | Input |
|---|---|---|---|
| 000 → I0 | 0 | 0 | 0 |
| 001 → I1 | 0 | 1 | S2 |
| 010–111 → I2–I7 | 1 | 1 | 1 |

I0 = 0, I1 = S2, I2 … I7 = 1.

### (c) Counter 1 → 2 → 6 → 7 → 1 with JK flip-flops
3 flip-flops Q2 Q1 Q0; unused 0, 3, 4, 5 = don't care. Use the JK excitation table (0→0: 0X, 0→1: 1X, 1→0: X1, 1→1: X0).

| Present Q2Q1Q0 | Next | J2 K2 | J1 K1 | J0 K0 |
|---|---|---|---|---|
| 001 (1) | 010 (2) | 0 X | 1 X | X 1 |
| 010 (2) | 110 (6) | 1 X | X 0 | 0 X |
| 110 (6) | 111 (7) | X 0 | X 0 | 1 X |
| 111 (7) | 001 (1) | X 1 | X 1 | X 0 |

K-maps (with don't cares 0, 3, 4, 5) give:
- **J2 = Q0'**, **K2 = Q0**
- **J1 = 1**, **K1 = Q0**
- **J0 = Q2**, **K0 = Q2'**

Check: 1(001): Q2 reset→0, Q1 toggle→1, Q0 reset→0 → 010 ✓; 2(010): Q2 set→1, Q1 hold, Q0 reset→0 → 110 ✓; 6(110): hold 1, hold 1, set→1 → 111 ✓; 7(111): reset, toggle→0, hold 1 → 001 ✓.

Circuit: three positive-edge JK flip-flops, common clock; J2 from Q0', K2 from Q0; J1 tied to logic 1, K1 from Q0; J0 from Q2, K0 from Q2'. No extra gates needed.

---

## Question 3

### (a) Two types of extrinsic semiconductor (see T1)
- **n-type:** Si + pentavalent donor (P, As, Sb). The 5th electron is free. Majority carriers electrons, minority holes; donor becomes + ion.
- **p-type:** Si + trivalent acceptor (B, Al, Ga). A missing bond forms a hole. Majority carriers holes, minority electrons; acceptor becomes − ion.
Both have much higher conductivity than intrinsic Si and remain electrically neutral overall.

### (b) Full-wave rectifier with capacitor smoothing (see T3)
Bridge rectifier + C across R_L. D1/D2 conduct on the positive half, D3/D4 on the negative half, current through R_L always in the same direction. C charges to the peak and discharges slowly through R_L between peaks → nearly smooth DC with small ripple at twice the supply frequency. Draw input sine, rectified humps, and smoothed output.

### (c) LED circuit (R1 in series with the LED, R2 in parallel with that branch, across V)
**i.** An **ammeter** (or multimeter on the DC mA range).

**ii.** Break the LED branch and connect the ammeter **in series** with R1 and the LED (+ terminal towards the battery's positive side), choose a suitable range, switch on and read the current. An ammeter has very low resistance, so it doesn't disturb the circuit. (Redraw Figure 1.1 with an "A" circle in series in the R1–LED branch.) (See T9.)

**iii.** I_LED = 12 mA, R1 = 3 kΩ, no LED drop:
V = I × R1 = 12 mA × 3 kΩ = **36 V**

**iv.** R2 = 5 kΩ is directly across the battery:
- I_R2 = V / R2 = 36 / 5 kΩ = 7.2 mA
- I_total = I_LED + I_R2 = 12 + 7.2 = **19.2 mA**

---

## Question 4

### (a) BJT characteristic with regions (see T4)
Draw IC vs VCE curves for several IB values (or the transfer curve VCE vs Vin). Label: **Saturation** – the steep region near VCE ≈ 0.2 V on the left; **Active** – the flat, evenly spaced curves (IC = βIB); **Cut-off** – the region along the VCE axis where IB = 0 and IC ≈ 0.

### (b) JFET operation with VGS < 0, VDS > 0 (see T5)
n-channel JFET. VDS > 0 makes electrons flow source → drain (ID). VGS < 0 reverse-biases the gate-channel junctions, so IG ≈ 0 and depletion layers grow into the channel, narrowing it and reducing ID. The depletion region is wider at the drain end (reverse bias = |VGS| + VDS there). As VDS increases the channel pinches off and ID levels off (saturation). At VGS = VGS(off) the channel closes fully and ID = 0. Draw the bar with p-gate regions and wedge-shaped depletion regions.

### (c) Si, active mode, β = 20, RB = 80 kΩ, RC = 2 kΩ, VCC = 10 V, VBB = 5 V
- IB = (VBB − 0.7) / RB = (5 − 0.7) / 80 kΩ = 4.3 / 80 000 = **53.75 µA**
- IC = β·IB = 20 × 53.75 µA = **1.075 mA**
- VCE = VCC − IC·RC = 10 − 1.075 mA × 2 kΩ = 10 − 2.15 = **7.85 V**

VCE > 0.2 V → active mode assumption is correct.
