# DSE 20.2F Computer Technology (27 Oct 2021) – Model Answers

Answer all questions. Full theory with diagrams: `CT Common Theory - Answers.md` (Tx). X' means NOT X.

---

## Question 1

### (a)(i) Z = NOT[ (A' + B + C) · NOT(A' + C') ]
- Inner bar: (A' + C')' = A''·C'' = **AC** (De Morgan)
- (A' + B + C)·AC = AA'C + ABC + ACC = 0 + ABC + AC = **AC** (absorption: AC + ABC = AC)
- Outer bar: Z = (AC)' = **A' + C'**

**Z = A' + C'**

### (a)(ii) Z = NOT[ NOT(B'·(A + NOT(B + C))) + NOT(A'·B·C' + NOT(A·C)) ]
Using (M' + N')' = M·N, Z = M·N where:
- M = B'(A + (B + C)') = B'(A + B'C') = AB' + B'C'
- N = A'BC' + (AC)' = A'BC' + A' + C' = **A' + C'** (A'BC' is absorbed by A')

Z = (AB' + B'C')(A' + C')
 = AA'B' + AB'C' + A'B'C' + B'C'C'
 = 0 + AB'C' + A'B'C' + B'C'
 = B'C'(A + A' + 1)

**Z = B'C'**

### (b) Z = Σm(1, 2, 3, 4, 7, 8, 12, 14) + d(0, 9, 13) – Tabular method

**Column 1** (✓ = combined)
| Group | Minterms (ABCD) |
|---|---|
| 0 | 0d (0000) ✓ |
| 1 | 1 (0001) ✓, 2 (0010) ✓, 4 (0100) ✓, 8 (1000) ✓ |
| 2 | 3 (0011) ✓, 9d (1001) ✓, 12 (1100) ✓ |
| 3 | 7 (0111) ✓, 13d (1101) ✓, 14 (1110) ✓ |

**Column 2** (pairs)
| Group | Pairs |
|---|---|
| 0 | 0,1 (000-) ✓; 0,2 (00-0) ✓; 0,4 (0-00) ✓; 0,8 (-000) ✓ |
| 1 | 1,3 (00-1) ✓; 1,9 (-001) ✓; 2,3 (001-) ✓; 4,12 (-100) ✓; 8,9 (100-) ✓; 8,12 (1-00) ✓ |
| 2 | **3,7 (0-11) PI**; 9,13 (1-01) ✓; 12,13 (110-) ✓; **12,14 (11-0) PI** |

**Column 3** (quads)
| Quad | Term |
|---|---|
| 0,1,2,3 (00--) | A'B' **PI** |
| 0,1,8,9 (-00-) | B'C' **PI** |
| 0,4,8,12 (--00) | C'D' **PI** |
| 8,9,12,13 (1-0-) | AC' **PI** |

Prime implicants: A'B', B'C', C'D', AC', A'CD (3,7), ABD' (12,14).

**Prime implicant chart** (real minterms only)
| PI | 1 | 2 | 3 | 4 | 7 | 8 | 12 | 14 |
|---|---|---|---|---|---|---|---|---|
| A'CD | | | X | | ⊗ | | | |
| ABD' | | | | | | | X | ⊗ |
| A'B' | X | ⊗ | X | | | | | |
| B'C' | X | | | | | X | | |
| C'D' | | | | ⊗ | | X | X | |
| AC' | | | | | | X | X | |

Essential PIs:
- **A'B'** (only cover of 2) → covers 1, 2, 3
- **C'D'** (only cover of 4) → covers 4, 8, 12
- **A'CD** (only cover of 7)
- **ABD'** (only cover of 14)

All minterms are now covered.

**Z = A'B' + C'D' + A'CD + ABD'**

---

## Question 2

### (a) Full adder from 2 half adders + OR (see T8)
HA1(A, B): S1 = A ⊕ B, C1 = AB. HA2(S1, Cin): **Sum = A ⊕ B ⊕ Cin**, C2 = (A ⊕ B)Cin. **Cout = C1 + C2 = AB + (A ⊕ B)Cin.**

### (b) Warehouse alarm Y (sensors S1 S2 S3 S4)
Y = 1 if S2S3, or S2S4, or at least three sensors are active.

**i. Truth table**
| m | S1 | S2 | S3 | S4 | Y | reason |
|---|---|---|---|---|---|---|
| 0 | 0 | 0 | 0 | 0 | 0 | |
| 1 | 0 | 0 | 0 | 1 | 0 | |
| 2 | 0 | 0 | 1 | 0 | 0 | |
| 3 | 0 | 0 | 1 | 1 | 0 | only 2 active, not S2 |
| 4 | 0 | 1 | 0 | 0 | 0 | |
| 5 | 0 | 1 | 0 | 1 | 1 | S2S4 |
| 6 | 0 | 1 | 1 | 0 | 1 | S2S3 |
| 7 | 0 | 1 | 1 | 1 | 1 | S2S3 / 3 active |
| 8 | 1 | 0 | 0 | 0 | 0 | |
| 9 | 1 | 0 | 0 | 1 | 0 | |
| 10 | 1 | 0 | 1 | 0 | 0 | |
| 11 | 1 | 0 | 1 | 1 | 1 | 3 active |
| 12 | 1 | 1 | 0 | 0 | 0 | |
| 13 | 1 | 1 | 0 | 1 | 1 | S2S4 |
| 14 | 1 | 1 | 1 | 0 | 1 | S2S3 |
| 15 | 1 | 1 | 1 | 1 | 1 | all |

Y = Σm(5, 6, 7, 11, 13, 14, 15)

**ii. Simplified SOP**
|S1S2 \ S3S4| 00 | 01 | 11 | 10 |
|---|---|---|---|---|
| **00** | 0 | 0 | 0 | 0 |
| **01** | 0 | 1 | 1 | 1 |
| **11** | 0 | 1 | 1 | 1 |
| **10** | 0 | 0 | 1 | 0 |

- m5, m7, m13, m15 → **S2S4**
- m6, m7, m14, m15 → **S2S3**
- m11, m15 → **S1S3S4**

**Y = S2S3 + S2S4 + S1S3S4**

**iii(a). NAND only** (SOP → NAND-NAND)
- G1 = NAND(S2, S3)
- G2 = NAND(S2, S4)
- G3 = NAND(S1, S3, S4)
- **Y = NAND(G1, G2, G3)**

Check: NAND(G1, G2, G3) = G1' + G2' + G3' = S2S3 + S2S4 + S1S3S4. (4 NAND gates.)

**iii(b). Multiplexer** – 8:1 MUX, selects = S1 S2 S3, data from S4:
| S1 S2 S3 | Y (S4=0) | Y (S4=1) | Input |
|---|---|---|---|
| 000 → I0 | 0 | 0 | 0 |
| 001 → I1 | 0 | 0 | 0 |
| 010 → I2 | 0 | 1 | S4 |
| 011 → I3 | 1 | 1 | 1 |
| 100 → I4 | 0 | 0 | 0 |
| 101 → I5 | 0 | 1 | S4 |
| 110 → I6 | 0 | 1 | S4 |
| 111 → I7 | 1 | 1 | 1 |

I0 = I1 = I4 = 0; I2 = I5 = I6 = S4; I3 = I7 = 1.

### (c) Demultiplexer (1:4) (see T8)
A DEMUX sends a single data input D to **one of 4 outputs**, chosen by 2 select lines S1 S0. Y0 = S1'S0'D, Y1 = S1'S0D, Y2 = S1S0'D, Y3 = S1S0D. E.g. S1S0 = 10 → D appears on Y2, the others are 0. Built from 4 AND gates and 2 inverters. Draw the block (D in; S1, S0 below; Y0–Y3 out) and the truth table.

---

## Question 3

### (a) Sequential vs combinational (see T6)
Combinational: output depends only on current inputs, no memory, no feedback, no clock (adders, MUX). Sequential: output depends on current inputs and past state, has memory (flip-flops), feedback and usually a clock (counters, registers).

### (b) JK flip-flop reduced truth table and excitation table (see T7)
| J | K | Q(n+1) |
|---|---|---|
| 0 | 0 | Qn (hold) |
| 0 | 1 | 0 (reset) |
| 1 | 0 | 1 (set) |
| 1 | 1 | Qn' (toggle) |

| Qn → Q(n+1) | J | K |
|---|---|---|
| 0 → 0 | 0 | X |
| 0 → 1 | 1 | X |
| 1 → 0 | X | 1 |
| 1 → 1 | X | 0 |

### (c) Timing diagram (positive edge, Q starts at 0)
Reading J and K at each rising clock edge:

| Rising edge | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 |
|---|---|---|---|---|---|---|---|---|
| J | 0 | 1 | 0 | 1 | 1 | 0 | 0 | 0 |
| K | 0 | 0 | 1 | 1 | 1 | 1 | 0 | 0 |
| Action | hold | set | reset | toggle | toggle | reset | hold | hold |
| Q after edge | 0 | **1** | 0 | **1** | 0 | 0 | 0 | 0 |

Q waveform: LOW until the 2nd rising edge, HIGH from edge 2 to edge 3, LOW from edge 3 to edge 4, HIGH from edge 4 to edge 5, then LOW for the rest.
```
Clock  _|‾|_|‾|_|‾|_|‾|_|‾|_|‾|_|‾|_|‾
        1   2   3   4   5   6   7   8
Q      _____|‾‾‾|___|‾‾‾|_______________
```

### (d) Counter 1 → 2 → 3 → 4 → 1 using JK flip-flops
Q2 Q1 Q0; unused 0, 5, 6, 7 = don't care.

| Present | Next | J2 K2 | J1 K1 | J0 K0 |
|---|---|---|---|---|
| 001 (1) | 010 (2) | 0 X | 1 X | X 1 |
| 010 (2) | 011 (3) | 0 X | X 0 | 1 X |
| 011 (3) | 100 (4) | 1 X | X 1 | X 1 |
| 100 (4) | 001 (1) | X 1 | 0 X | 1 X |

K-map results:
- **J2 = Q1·Q0**, **K2 = 1**
- **J1 = Q2'**, **K1 = Q0**
- **J0 = 1**, **K0 = 1** (Q0 toggles on every clock)

Check: 001 → Q2: J=0 K=1 → 0; Q1: J=1 K=1 → toggle → 1; Q0 toggle → 0 → 010 ✓. 010 → 0; J1=1,K1=0 → 1; Q0 → 1 → 011 ✓. 011 → J2=1,K2=1 → 1; Q1 toggle → 0; Q0 → 0 → 100 ✓. 100 → K2=1 → 0; J1=0,K1=0 → hold 0; Q0 → 1 → 001 ✓.

Circuit: three positive-edge JK flip-flops on a common clock; one AND gate (Q1·Q0) to J2; K2, J0, K0 tied to logic 1; J1 from Q2', K1 from Q0.

### (e) Count sequence: JA = QB, KA = 1; JB = 1, KB = QA; JC = QB, KC = 1; start QA QB QC = 111
| Clock | QA QB QC | JA KA | JB KB | JC KC | Next QA QB QC |
|---|---|---|---|---|---|
| 0 | 1 1 1 | 1 1 toggle | 1 1 toggle | 1 1 toggle | 0 0 0 |
| 1 | 0 0 0 | 0 1 reset | 1 0 set | 0 1 reset | 0 1 0 |
| 2 | 0 1 0 | 1 1 toggle | 1 0 set | 1 1 toggle | 1 1 1 |
| 3 | 1 1 1 | repeats | | | |

**Sequence: 111 → 000 → 010 → 111 → …** (7 → 0 → 2 → 7 with QA as MSB). A mod-3 sequence.

---

## Question 4

### (a) Two extrinsic semiconductors (see T1)
n-type: Si + pentavalent donor (P, As, Sb); extra free electron; electrons majority carriers. p-type: Si + trivalent acceptor (B, Al, Ga); a hole per acceptor; holes majority carriers. Both far more conductive than pure Si; both electrically neutral.

### (b) Full-wave rectifier with capacitor smoothing (see T3)
Bridge rectifier with C across R_L; alternate diode pairs conduct on each half cycle; C charges to Vpeak and discharges slowly between peaks → smooth DC with small ripple at 2f. Draw the three waveforms.

### (c) LED circuit (R in series with LED across V), using Figure 1.2
**i.** An **ammeter** (multimeter on the DC mA range).

**ii.** Connect the ammeter **in series** between R and the LED (observe polarity), choose a range above the expected current, switch on, read. Redraw Figure 1.1 with the ammeter added. (T9)

**iii.** At I = 10 mA, from the forward-current vs forward-voltage graph: **VLED ≈ 1.9 V**.
From the luminous-intensity graph (straight line through (0, 0) and (30 mA, 1.5)): relative intensity = 10 × (1.5/30) = **0.5**.

**iv.** R = 2.2 kΩ:
- VR = I × R = 10 mA × 2.2 kΩ = 22 V
- V = VR + VLED = 22 + 1.9 = **23.9 V**

---

## Question 5

### (a) Diode I-V curve with regions (see T2)
Draw forward region (current rises sharply after the knee voltage ≈0.7 V Si), reverse region (tiny constant Is below the axis), and breakdown region (sharp drop at the breakdown voltage / PIV).

### (b) Three 7 Ω resistors
- Series: R = 7 + 7 + 7 = **21 Ω**
- Parallel: 1/R = 3/7 → R = 7/3 = **2.33 Ω**

### (c) Si, active mode, β = 30, RB = 90 kΩ, RC = 3 kΩ, VCC = 12 V, VBB = 6 V
- IB = (6 − 0.7) / 90 kΩ = 5.3 / 90 000 = **58.9 µA**
- IC = β·IB = 30 × 58.9 µA = **1.767 mA**
- VCE = VCC − IC·RC = 12 − 1.767 mA × 3 kΩ = 12 − 5.3 = **6.7 V**

VCE > 0.2 V → active mode confirmed.

### (d) AND gate using transistor-resistor logic (see T10)
Two NPN transistors in **series** between VCC and an output resistor to ground; inputs A and B drive the bases through base resistors; output taken across the emitter resistor.
- If A or B is LOW, that transistor is cut off → no current path → Y = 0.
- Only when A and B are both HIGH do both transistors saturate → current flows through the output resistor → Y = HIGH.
- So **Y = A·B**. Include the 4-row truth table.
