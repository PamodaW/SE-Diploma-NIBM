# DSE 20.1P Computer Technology (24 Apr 2021) – Model Answers

This paper is the same as 20.1F except for **Q1(b)**, **Q3(c)** numbers and **Q4(c)** values. Shared questions are answered briefly here; full working is in `DSE 20.1F Computer Technology - Answers.md` and theory in `CT Common Theory - Answers.md` (Tx). X' means NOT X.

---

## Question 1

### (a)(i) Z = NOT[ NOT(P + NOT(Q + R)) + NOT(P'Q' + NOT(PQ)) ]
Z = (P + Q'R')·(P'Q' + P' + Q') = (P + Q'R')(P' + Q') = PQ' + P'Q'R' + Q'R' = PQ' + Q'R'

**Z = Q'(P + R')**

### (a)(ii) A = NOT[ NOT(X + Y) + NOT(X'·NOT(Y + Z)) ]
A = (X + Y)·X'·Y'·Z' = XX'Y'Z' + X'YY'Z' = **0**

### (b) Z = Σm(1, 3, 7, 9, 11, 12, 13, 15) + d(4, 8, 10)

#### (i) K-map
|AB \ CD| 00 | 01 | 11 | 10 |
|---|---|---|---|---|
| **00** | 0 | 1 | 1 | 0 |
| **01** | X | 0 | 1 | 0 |
| **11** | 1 | 1 | 1 | 0 |
| **10** | X | 1 | 1 | X |

Groups:
- m1, m3, m9, m11 → **B'D**
- m3, m7, m11, m15 (column CD = 11) → **CD**
- m8, m9, m12, m13 (rows 11/10, columns 00/01) → **AC'**

**Z = B'D + CD + AC'**

#### (ii) Tabular method
**Column 1**
| Group | Minterms (ABCD) |
|---|---|
| 1 | 1 (0001) ✓, 4d (0100) ✓, 8d (1000) ✓ |
| 2 | 3 (0011) ✓, 9 (1001) ✓, 10d (1010) ✓, 12 (1100) ✓ |
| 3 | 7 (0111) ✓, 11 (1011) ✓, 13 (1101) ✓ |
| 4 | 15 (1111) ✓ |

**Column 2** (pairs)
| Group | Pairs |
|---|---|
| 1 | 1,3 (00-1) ✓; 1,9 (-001) ✓; **4,12 (-100) PI**; 8,9 (100-) ✓; 8,10 (10-0) ✓; 8,12 (1-00) ✓ |
| 2 | 3,7 (0-11) ✓; 3,11 (-011) ✓; 9,11 (10-1) ✓; 9,13 (1-01) ✓; 10,11 (101-) ✓; 12,13 (110-) ✓ |
| 3 | 7,15 (-111) ✓; 11,15 (1-11) ✓; 13,15 (11-1) ✓ |

**Column 3** (quads) – prime implicants
| Quad | Term |
|---|---|
| 1,3,9,11 (-0-1) | B'D |
| 8,9,10,11 (10--) | AB' |
| 8,9,12,13 (1-0-) | AC' |
| 3,7,11,15 (--11) | CD |
| 9,11,13,15 (1--1) | AD |

Plus BC'D' (4,12).

**Prime implicant chart**
| PI | 1 | 3 | 7 | 9 | 11 | 12 | 13 | 15 |
|---|---|---|---|---|---|---|---|---|
| BC'D' | | | | | | X | | |
| B'D | ⊗ | X | | X | X | | | |
| CD | | X | ⊗ | | X | | | X |
| AB' | | | | X | X | | | |
| AC' | | | | X | | X | X | |
| AD | | | | X | X | | X | X |

- **B'D** essential (only cover of 1); **CD** essential (only cover of 7).
- Covered so far: 1, 3, 7, 9, 11, 15. Remaining: 12, 13.
- **AC'** covers both 12 and 13.

**Z = B'D + CD + AC'**

---

## Question 2 (same as 20.1F)

**(a)** Full adder: HA1(A, B) → S1 = A ⊕ B, C1 = AB; HA2(S1, Cin) → Sum = A ⊕ B ⊕ Cin, C2 = (A ⊕ B)Cin; Cout = C1 + C2 (OR gate). (T8)

**(b)** BR = ES1 + ES2 + S1·S2
- i. Truth table: BR = 0 only for (ES1 ES2 S1 S2) = 0000, 0001, 0010; all other 13 rows are 1.
- ii. **BR = (ES1 + ES2 + S1)(ES1 + ES2 + S2)**
- iii(a). G1 = NOR(ES1, ES2, S1), G2 = NOR(ES1, ES2, S2), **BR = NOR(G1, G2)**
- iii(b). 8:1 MUX, selects ES1 ES2 S1: I0 = 0, I1 = S2, I2–I7 = 1.

**(c)** Counter 1 → 2 → 6 → 7 with JK flip-flops (Q2 Q1 Q0):

| Present | Next | J2 K2 | J1 K1 | J0 K0 |
|---|---|---|---|---|
| 001 | 010 | 0 X | 1 X | X 1 |
| 010 | 110 | 1 X | X 0 | 0 X |
| 110 | 111 | X 0 | X 0 | 1 X |
| 111 | 001 | X 1 | X 1 | X 0 |

**J2 = Q0', K2 = Q0; J1 = 1, K1 = Q0; J0 = Q2, K0 = Q2'**

---

## Question 3

**(a)** Extrinsic semiconductors: n-type (pentavalent donor, electrons majority) and p-type (trivalent acceptor, holes majority). (T1)

**(b)** Full-wave rectifier with capacitor smoothing – see T3 (circuit, operation, three waveforms).

**(c)** LED circuit
- **i.** An **ammeter** (multimeter on DC mA).
- **ii.** Connect the ammeter **in series** with R1 and the LED, observing polarity, and read the current (T9).
- **iii.** I_LED = 10 mA, R1 = 4 kΩ, no LED drop: V = 10 mA × 4 kΩ = **40 V**
- **iv.** R2 = 5 kΩ across the battery: I_R2 = 40 / 5 kΩ = 8 mA → I_total = 10 + 8 = **18 mA**

---

## Question 4

**(a)** BJT characteristic: label cut-off (IC ≈ 0 along the VCE axis), active (flat curves, IC = βIB), saturation (steep region at VCE ≈ 0.2 V). (T4)

**(b)** JFET with VGS < 0, VDS > 0: reverse-biased gate widens the depletion regions, narrowing the channel; ID controlled by VGS; pinch-off gives constant ID; VGS(off) gives ID = 0. (T5)

**(c)** Si, active mode, β = 15, RB = 120 kΩ, RC = 3 kΩ, VCC = 10 V, VBB = 5 V
- IB = (5 − 0.7) / 120 kΩ = 4.3 / 120 000 = **35.83 µA**
- IC = β·IB = 15 × 35.83 µA = **0.5375 mA**
- VCE = VCC − IC·RC = 10 − 0.5375 mA × 3 kΩ = 10 − 1.6125 = **8.39 V**

VCE > 0.2 V → active mode confirmed.
