# DSE 18.1F Computer Technology (1 Oct 2018) – Model Answers

Answer five of six questions. Theory marked **(see Common Theory Tx)** is covered in full, with diagrams, in `CT Common Theory - Answers.md`.

Notation: X' means NOT X (X with a bar).

---

## Question 1

### (a)(i) Z = NOT[ ( NOT(A' + A'B') + ABC ) · NOT(ABC + AC) ]
(Reading of the overbars: a bar over the whole expression; a bar over "A' + A'B'" (with A, A and B each individually barred); a bar over "(ABC + AC)".)

Step 1 – inner terms
- A' + A'B' = A'(1 + B') = A' → NOT(A') = **A**
- First bracket: A + ABC = A(1 + BC) = **A**
- ABC + AC = AC(B + 1) = AC → NOT(AC) = **A' + C'** (De Morgan)

Step 2 – product: A·(A' + C') = AA' + AC' = **AC'**

Step 3 – outer bar: Z = (AC')' = A' + C'' (De Morgan)

**Z = A' + C**

### (a)(ii) Z = NOT[ (A'·B'·C' + C) + (A + B) + (A' + (BC)') ]
Inside the outer bar we have A + A' (from the 2nd and 3rd brackets), and A + A' = 1.
So the whole OR expression = 1 (anything + 1 = 1).

**Z = NOT(1) = 0**

(If asked to show De Morgan explicitly: Z = (A'B'C' + C)' · (A + B)' · (A' + (BC)')' = (…)·(A'B')·(A·BC) = A'·A·(…) = 0.)

### (b) Z = Σm(2, 3, 8, 9, 12, 14) + d(6, 7, 13)

#### I. K-map method
|AB \ CD| 00 | 01 | 11 | 10 |
|---|---|---|---|---|
| **00** | 0 | 0 | 1 (m3) | 1 (m2) |
| **01** | 0 | 0 | X (m7) | X (m6) |
| **11** | 1 (m12) | X (m13) | 0 | 1 (m14) |
| **10** | 1 (m8) | 1 (m9) | 0 | 0 |

Groups:
- Quad m2, m3, m6, m7 (top two rows, CD = 11,10) → **A'C**
- Quad m8, m9, m12, m13 (bottom two rows, CD = 00,01) → **AC'**
- Pair m6, m14 (column CD = 10, rows 01 and 11) → **BCD'** (to cover m14)

**Z = A'C + AC' + BCD'**
(Equally minimal: Z = A'C + AC' + ABD', using the pair m12, m14.)

#### II. Tabular (Quine–McCluskey) method
Include minterms and don't cares, grouped by number of 1s.

**Column 1**
| Group | Minterm | ABCD |
|---|---|---|
| 1 | 2 | 0010 ✓ |
| | 8 | 1000 ✓ |
| 2 | 3 | 0011 ✓ |
| | 6 (d) | 0110 ✓ |
| | 9 | 1001 ✓ |
| | 12 | 1100 ✓ |
| 3 | 7 (d) | 0111 ✓ |
| | 13 (d) | 1101 ✓ |
| | 14 | 1110 ✓ |

**Column 2 (pairs)**
| Pair | ABCD |
|---|---|
| 2,3 | 001- ✓ |
| 2,6 | 0-10 ✓ |
| 8,9 | 100- ✓ |
| 8,12 | 1-00 ✓ |
| 3,7 | 0-11 ✓ |
| 6,7 | 011- ✓ |
| 6,14 | -110 **PI** |
| 9,13 | 1-01 ✓ |
| 12,13 | 110- ✓ |
| 12,14 | 11-0 **PI** |

**Column 3 (quads)**
| Quad | ABCD |
|---|---|
| 2,3,6,7 | 0-1- **PI** → A'C |
| 8,9,12,13 | 1-0- **PI** → AC' |

Prime implicants: A'C, AC', BCD' (6,14), ABD' (12,14).

**Prime implicant chart** (only the real minterms 2,3,8,9,12,14)
| PI | 2 | 3 | 8 | 9 | 12 | 14 |
|---|---|---|---|---|---|---|
| A'C | ⊗ | ⊗ | | | | |
| AC' | | | ⊗ | ⊗ | X | |
| BCD' | | | | | | X |
| ABD' | | | | | X | X |

- A'C is essential (only one covering 2 and 3).
- AC' is essential (only one covering 8 and 9).
- Remaining minterm 14: covered by either BCD' or ABD'.

**Z = A'C + AC' + BCD'** (or A'C + AC' + ABD') – same as the K-map.

---

## Question 2

### (a)(i) Truth table
Let 1 = door open / ignition ON / headlights ON.
X = 1 if (A·B) or (D·C') or (B·D).

| m | A | B | C | D | X |
|---|---|---|---|---|---|
| 0 | 0 | 0 | 0 | 0 | 0 |
| 1 | 0 | 0 | 0 | 1 | 1 |
| 2 | 0 | 0 | 1 | 0 | 0 |
| 3 | 0 | 0 | 1 | 1 | 0 |
| 4 | 0 | 1 | 0 | 0 | 0 |
| 5 | 0 | 1 | 0 | 1 | 1 |
| 6 | 0 | 1 | 1 | 0 | 0 |
| 7 | 0 | 1 | 1 | 1 | 1 |
| 8 | 1 | 0 | 0 | 0 | 0 |
| 9 | 1 | 0 | 0 | 1 | 1 |
| 10 | 1 | 0 | 1 | 0 | 0 |
| 11 | 1 | 0 | 1 | 1 | 0 |
| 12 | 1 | 1 | 0 | 0 | 1 |
| 13 | 1 | 1 | 0 | 1 | 1 |
| 14 | 1 | 1 | 1 | 0 | 1 |
| 15 | 1 | 1 | 1 | 1 | 1 |

X = Σm(1, 5, 7, 9, 12, 13, 14, 15)

### (a)(ii)(a) Simplified SOP
|AB \ CD| 00 | 01 | 11 | 10 |
|---|---|---|---|---|
| **00** | 0 | 1 | 0 | 0 |
| **01** | 0 | 1 | 1 | 0 |
| **11** | 1 | 1 | 1 | 1 |
| **10** | 0 | 1 | 0 | 0 |

- Row AB = 11 (m12–15) → **AB**
- Column CD = 01 (m1, 5, 13, 9) → **C'D**
- Quad m5, m7, m13, m15 → **BD**

**X = AB + BD + C'D**

### (a)(ii)(b) Simplified POS
Group the 0s: X' = Σm(0, 2, 3, 4, 6, 8, 10, 11)
- m0, m4, m2, m6 (A = 0, D = 0) → A'D'
- m0, m2, m8, m10 (B = 0, D = 0) → B'D'
- m2, m3, m10, m11 (B = 0, C = 1) → B'C

X' = A'D' + B'D' + B'C → apply De Morgan:

**X = (A + D)(B + D)(B + C')**

### (a)(iii)(a) NOR gates only
A POS expression maps directly onto NOR-NOR:
1. C' = NOR(C, C)
2. G1 = NOR(A, D) = (A + D)'
3. G2 = NOR(B, D) = (B + D)'
4. G3 = NOR(B, C') = (B + C')'
5. X = NOR(G1, G2, G3) = (A + D)(B + D)(B + C')

```
 C ─┬─[NOR]── C'
    └─┘
 A ──[NOR]─ G1 ─┐
 D ──┘          │
 B ──[NOR]─ G2 ─┼─[3-input NOR]── X
 D ──┘          │
 B ──[NOR]─ G3 ─┘
 C'──┘
```
(5 NOR gates.)

### (a)(iii)(b) Multiplexer
Use an **8:1 MUX**, select lines S2 S1 S0 = A B C, and use D (or 0/1) on the data inputs. For each ABC look at the two rows D = 0 and D = 1:

| A B C | X at D=0 | X at D=1 | Input |
|---|---|---|---|
| 000 (I0) | 0 | 1 | **D** |
| 001 (I1) | 0 | 0 | **0** |
| 010 (I2) | 0 | 1 | **D** |
| 011 (I3) | 0 | 1 | **D** |
| 100 (I4) | 0 | 1 | **D** |
| 101 (I5) | 0 | 0 | **0** |
| 110 (I6) | 1 | 1 | **1** |
| 111 (I7) | 1 | 1 | **1** |

Connect I0, I2, I3, I4 = D; I1, I5 = 0 (ground); I6, I7 = 1 (VCC); output Y = X.
(A 16:1 MUX with ABCD on the selects and the truth-table column on I0–I15 is also acceptable.)

### (b) Combinational vs Sequential (see Common Theory T6)
- Combinational: output depends only on present inputs, no memory, no feedback, no clock. E.g. adder, MUX, decoder.
- Sequential: output depends on present inputs **and** previous state, has memory (flip-flops), uses feedback, usually clocked. E.g. counters, registers.

---

## Question 3

### (i) Positive-edge-triggered D flip-flop output
Q copies D at each **rising** clock edge (edges at 0, 2, 4, 6, 8, 10, 12). Reading the input at each rising edge:

| Rising edge | 0 | 2 | 4 | 6 | 8 | 10 | 12 |
|---|---|---|---|---|---|---|---|
| Input (D) | 0* | 1 | 0 | 1 | 0 | 0 | 1 |
| Q after edge | 0 | 1 | 0 | 1 | 0 | 0 | 1 |

\*The input rises just **after** edge 0, so D is still 0 at that edge.

Output waveform: Q = 0 from start until edge 2; **HIGH from edge 2 to edge 4**; LOW 4–6; **HIGH 6–8**; LOW from 8 to 12; **HIGH from edge 12** onwards. The short input pulse between 7 and 8 is ignored because it is not present at a rising edge.
```
Q:  ________|‾‾‾‾‾|_____|‾‾‾‾‾|___________|‾‾‾‾
    0       2     4     6     8     10    12
```

### (ii) T flip-flop (see Common Theory T7)
| T | Qn | Q(n+1) |
|---|---|---|
| 0 | 0 | 0 |
| 0 | 1 | 1 |
| 1 | 0 | 1 |
| 1 | 1 | 0 |

Excitation table: T = Qn ⊕ Q(n+1)
| Qn | Q(n+1) | T |
|---|---|---|
| 0 | 0 | 0 |
| 0 | 1 | 1 |
| 1 | 0 | 1 |
| 1 | 1 | 0 |

### (iii) Counter 2 → 3 → 5 → 7 → 2 using T flip-flops
3 flip-flops Q2 Q1 Q0. Unused states 0, 1, 4, 6 = don't care.

| Present Q2Q1Q0 | Next Q2Q1Q0 | T2 | T1 | T0 |
|---|---|---|---|---|
| 010 (2) | 011 (3) | 0 | 0 | 1 |
| 011 (3) | 101 (5) | 1 | 1 | 0 |
| 101 (5) | 111 (7) | 0 | 1 | 0 |
| 111 (7) | 010 (2) | 1 | 0 | 1 |

K-maps (Q2 = rows, Q1Q0 = columns 00 01 11 10; X for 0,1,4,6):

T2: 1s at 3, 7; 0s at 2, 5 → **T2 = Q1·Q0**

T1: 1s at 3, 5; 0s at 2, 7 → **T1 = Q1' + Q2'·Q0**

T0: 1s at 2, 7; 0s at 3, 5 → **T0 = Q0' + Q2·Q1**

Check: 2(010): T=001 → 011 ✓; 3(011): T=110 → 101 ✓; 5(101): T=010 → 111 ✓; 7(111): T=101 → 010 ✓.

Circuit: three positive-edge T flip-flops with a common clock; an AND gate (Q1·Q0) to T2; T1 = OR(Q1', AND(Q2', Q0)); T0 = OR(Q0', AND(Q2, Q1)).

### (iv) Count sequence (JA = QC, KA = 1; JB = 1, KB = QA·QC; JC = QB, KC = 1), start QA QB QC = 011
| Clock | QA QB QC | JA KA | JB KB | JC KC | Next |
|---|---|---|---|---|---|
| 0 | 0 1 1 | 1 1 (toggle) | 1 0 (set) | 1 1 (toggle) | 1 1 0 |
| 1 | 1 1 0 | 0 1 (reset) | 1 0 (set) | 1 1 (toggle) | 0 1 1 |
| 2 | 0 1 1 | repeats | | | |

**Sequence: 011 → 110 → 011 → 110 …** (QA QB QC; i.e. 3 → 6 → 3 with QA as MSB). The circuit alternates between two states.

---

## Question 4 (see Common Theory T1–T3)

### (i) Formation of n-type
Pure Si has 4 valence electrons, each forming covalent bonds with 4 neighbours. Dope it with a pentavalent impurity (P, As, Sb). Four of the impurity's electrons form bonds; the **fifth is loosely held** and becomes a free electron. The impurity is called a **donor** and becomes a fixed + ion. Electrons are the majority carriers, holes the minority carriers. Draw the lattice with a P atom in the middle and one spare electron.

### (ii) V-A characteristic of a practical diode
Draw the forward curve rising sharply after **Vb ≈ 0.7 V (Si)**, the flat reverse current **Is** (µA, just below the axis), and the sharp breakdown drop at **−PIV**. See T2 sketch.

### (iii) Half-wave rectifier
Circuit: AC source → diode → load R_L. Positive half cycle: diode forward biased, conducts, Vout ≈ Vin − 0.7 V. Negative half cycle: reverse biased, no current, Vout = 0. Output is pulsating DC with only the positive halves. See T3.

### (iv) Full-wave rectifier
Centre-tapped (2 diodes) or bridge (4 diodes). Positive half: D1 (or D1, D2 in bridge) conducts; negative half: D2 (or D3, D4) conducts; current through R_L is in the same direction both times, so both halves appear positive at the output. Ripple frequency = 2 × supply frequency. See T3.

---

## Question 5

### (i) I-V curves of ON and OFF switches
- ON (closed) switch: V = 0 for all I → vertical line along the I axis.
- OFF (open) switch: I = 0 for all V → horizontal line along the V axis.
(see T2)

### (ii) Reverse and forward bias of a p-n junction
- **Forward:** p to +, n to −; depletion layer narrows; above ≈0.7 V (Si) a large current flows.
- **Reverse:** p to −, n to +; depletion layer widens; only tiny Is flows until breakdown at PIV.
(see T2)

### (iii) Figure 1: Si diode, V = 10 V, R = 2 kΩ
The positive terminal of the battery drives current through R into the diode's anode, so:

a) **Mode: forward biased** (conducting).
b) **VD = 0.7 V** (Si).
c) **VR = V − VD = 10 − 0.7 = 9.3 V**
d) **I = VR / R = 9.3 / 2000 = 4.65 mA**

---

## Question 6

### (i) Two types: **NPN** and **PNP** (see T4 for symbols – arrow on emitter points out for NPN, in for PNP).

### (ii) Figure 2: Si, β = 100, RB = 200 kΩ, RC = 2 kΩ, VCC = 10 V, VBB = 5 V
VBB = 5 V > 0.5 V cut-in → not cut-off. Assume **active** (VBE = 0.7 V):

- IB = (VBB − VBE) / RB = (5 − 0.7) / 200 kΩ = 4.3 / 200 000 = **21.5 µA**
- IC = β·IB = 100 × 21.5 µA = **2.15 mA**
- VCE = VCC − IC·RC = 10 − (2.15 mA × 2 kΩ) = 10 − 4.3 = **5.7 V**

Check: VCE = 5.7 V > VCE(sat) = 0.2 V → assumption valid. **Operating mode: active.**
