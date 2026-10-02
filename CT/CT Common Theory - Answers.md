# Computer Technology – Common Theory Answers

These topics come up in almost every past paper (18.1F – 20.2F). Each paper's answer file gives a short answer and points here for the full version with diagrams.

---

## T1. Semiconductors

### Intrinsic semiconductor
Pure silicon (Si) or germanium (Ge). Each atom has **4 valence electrons** and forms 4 covalent bonds with neighbours in a crystal lattice. At room temperature a few bonds break, giving equal numbers of free electrons and holes. Conductivity is low.

### Extrinsic semiconductors (doping)
Adding a small amount of impurity (doping) greatly increases conductivity.

**n-type**
- Si doped with a **pentavalent** (5 valence electron) impurity: Phosphorus, Arsenic, Antimony (a **donor**).
- 4 electrons of the impurity bond with 4 Si neighbours; the **5th electron is loosely bound** and becomes a free electron at room temperature.
- The donor atom becomes a fixed **positive ion**.
- **Majority carriers: electrons. Minority carriers: holes.**
- The material is still electrically neutral overall.

```
   Si   Si   Si
    \   |   /
 Si — P+ — Si      • = extra free electron
    /   |   \  •
   Si   Si   Si
```

**Conduction in n-type:** when a voltage is applied, the free electrons drift towards the positive terminal (opposite to the field) and the few holes drift towards the negative terminal. Current is carried mainly by electrons. Current I = n·q·A·v (more free electrons → higher current).

**p-type**
- Si doped with a **trivalent** (3 valence electron) impurity: Boron, Aluminium, Gallium, Indium (an **acceptor**).
- Only 3 bonds can be completed; the missing bond is a **hole**. A neighbouring electron can jump into it, so the hole "moves".
- The acceptor atom becomes a fixed **negative ion**.
- **Majority carriers: holes. Minority carriers: electrons.**

```
   Si   Si   Si
    \   |   /
 Si — B− — Si      o = hole (missing bond)
    /   |  o\
   Si   Si   Si
```

| | n-type | p-type |
|---|---|---|
| Impurity | Pentavalent (P, As, Sb) – donor | Trivalent (B, Al, Ga) – acceptor |
| Majority carrier | Electrons | Holes |
| Minority carrier | Holes | Electrons |
| Fixed ion | Positive donor ion | Negative acceptor ion |

---

## T2. The p-n junction diode

When p-type and n-type are joined, electrons diffuse from n to p and holes from p to n and recombine near the junction. This leaves a **depletion region** (no free carriers, only fixed ions) with a **barrier potential** of about **0.7 V (Si)** or **0.3 V (Ge)**.

Symbol: anode (p) ──▷|── cathode (n)

### Forward biased mode
- p side (anode) connected to **+**, n side (cathode) to **−**.
- The applied voltage opposes the barrier potential, so the **depletion region narrows**.
- Once V exceeds the knee/cut-in voltage (≈0.7 V Si, 0.3 V Ge) majority carriers cross the junction easily and a **large forward current** flows (mA range) that rises steeply with voltage.
- Diode behaves like a closed switch with a small drop of ≈0.7 V.

### Reverse biased mode
- p side to **−**, n side to **+**.
- Carriers are pulled away from the junction, the **depletion region widens** and the barrier rises.
- Only a tiny **reverse saturation current Is** flows (nA for Si, µA for Ge) due to minority carriers.
- If the reverse voltage exceeds the **Peak Inverse Voltage (PIV) / breakdown voltage**, avalanche breakdown occurs and the reverse current rises sharply (may damage a normal diode).
- Diode behaves like an open switch.

### V-I characteristic of a practical diode (draw this)
```
                 I_F (mA)
                   |          /
                   |         /   forward region
                   |        /
                   |      _/
 -PIV              |  __-'
 ---+--------------+--|---------- V
    |   reverse    0  Vb (0.7 V Si / 0.3 V Ge) = knee / cut-in voltage
    |  ___________ -Is  (reverse saturation current, µA)
    | /  reverse region
    |/  breakdown (avalanche) at PIV
    |
                 I_R (µA)
```
Label: **Vb / cut-in (knee) voltage** on the +V axis, **Is** as the small flat reverse current just below the axis, **PIV** where the reverse curve drops sharply. The three regions are: forward (conduction) region, reverse (leakage/cut-off) region, and breakdown region.

### Ideal switch I-V curves (ON and OFF switches)
- **ON switch (closed):** V = 0 for any current → a **vertical line** on the I axis (I-V graph with V on x-axis).
- **OFF switch (open):** I = 0 for any voltage → a **horizontal line** along the V axis.
- An ideal diode is an ON switch in forward bias and an OFF switch in reverse bias.

---

## T3. Rectifiers

### Half-wave rectifier
```
   AC  ~ ──┬──▷|──┬───── +
  (Vin)    │   D   R_L   Vout
           └──────┴───── −
```
- **Positive half cycle:** anode is positive → diode forward biased → current flows through R_L → Vout ≈ Vin − 0.7 V.
- **Negative half cycle:** diode reverse biased → no current → Vout = 0.
- Output: only the positive half cycles (pulsating DC).
- Ripple frequency = input frequency (e.g. 50 Hz in → 50 Hz ripple). Vdc = Vm/π.

Waveforms: input sine; output = positive humps with gaps where the negative halves were.

### Full-wave rectifier (centre-tapped, 2 diodes)
```
            ┌──▷|── D1 ──┐
   AC ─ )|( ┤ centre tap │──┬──── +
  transformer│  (to −)   │ R_L   Vout
            └──▷|── D2 ──┘  │
                 CT ────────┴──── −
```
- Positive half cycle: top of secondary positive → **D1 conducts**, D2 off → current flows through R_L downward.
- Negative half cycle: bottom positive → **D2 conducts**, D1 off → current flows through R_L **in the same direction**.
- Output: every half cycle becomes positive. Ripple frequency = **2 × input frequency** (50 Hz → 100 Hz). Vdc = 2Vm/π.

### Full-wave bridge rectifier (4 diodes)
- Positive half cycle: **D1 and D2** conduct (two diodes in series) → current through R_L top to bottom.
- Negative half cycle: **D3 and D4** conduct → current through R_L **still top to bottom**.
- Output = both half cycles positive, peak ≈ Vm − 1.4 V (two diode drops). No centre tap needed.

### Full-wave rectifier with capacitor smoothing (very common 10-mark question)
Draw the bridge (or centre-tap) rectifier and put a **capacitor C in parallel with R_L**.

Operation:
1. As the rectified voltage rises towards its peak, the diodes conduct and **charge C** up to Vpeak.
2. After the peak, the rectified voltage falls faster than the capacitor voltage, so the diodes become reverse biased. **C discharges slowly through R_L**, keeping the output voltage high.
3. At the next half-cycle, when the rectified voltage rises above the capacitor voltage again, the diodes conduct and recharge C.
4. The output is therefore an almost-steady DC with a small **ripple** (sawtooth). Larger C or larger R_L → smaller ripple. Ripple voltage ≈ I_load / (2fC) for full-wave.

Waveforms to draw (three stacked graphs, same time axis):
```
Vin (AC):        /\    /\    /\
                   \/    \/    \/

Rectified:       /\/\/\/\/\/\      (all humps positive, twice the frequency)

Vout with C:    /‾‾\_/‾‾\_/‾‾\_    (nearly flat line at Vpeak with small
                                    sawtooth ripple: rises on charge, slow
                                    linear fall on discharge)
```

---

## T4. Bipolar Junction Transistors (BJT)

### Two types and symbols
- **NPN** – emitter arrow points **out** (Not Pointing iN).
- **PNP** – emitter arrow points **in** (Points iN Proudly).
```
 NPN:        C              PNP:        C
             |                          |
     B ──|<                      B ──|<
             \                          ↖ (arrow into base)
              ↘ E                        E
```
(In the exam draw a circle, the base line, collector line and emitter line with the arrow on the emitter; NPN arrow away from base, PNP arrow toward base.)

### Operating regions / transfer and output characteristics
Output characteristic = graph of **Ic vs VCE** for different values of **IB**.
```
 Ic
  |   saturation
  |   |  ___________________ IB4
  |   | /___________________ IB3
  |   |/____________________ IB2     ACTIVE REGION
  |   /_____________________ IB1     (Ic = β·IB, flat lines)
  |  /
  |_/______________________ IB = 0   CUT-OFF (Ic ≈ 0)
  +-------------------------------- VCE
   VCE(sat) ≈ 0.2 V
```
- **Cut-off:** VBE < 0.5 V (Si), IB = 0, Ic ≈ 0. Transistor = OFF switch. VCE ≈ VCC.
- **Active:** base-emitter forward biased (VBE ≈ 0.7 V), base-collector reverse biased. Ic = β·IB. Used as an **amplifier**.
- **Saturation:** both junctions forward biased, VCE = VCE(sat) ≈ 0.2 V, Ic = (VCC − 0.2)/RC (maximum). Transistor = ON switch.

**Transfer characteristic** (Vout = VCE vs Vin = VBB or IB): output stays at VCC (cut-off) while Vin < 0.5 V, then falls linearly (active region), then flattens at ≈0.2 V (saturation).
```
 Vout(VCE)
 VCC |‾‾‾‾‾\
     |cut-  \   active
     | off   \
     |        \_________ 0.2 V  saturation
     +-----|-----|------------ Vin
          0.5   ~0.8
```

### Switched-mode operation
The BJT is used as a digital switch by driving it between **cut-off (OFF)** and **saturation (ON)**, avoiding the active region:
- Input LOW → IB = 0 → cut-off → Ic = 0, VCE = VCC → output HIGH (switch open).
- Input HIGH → IB large enough that β·IB > Ic(sat) → saturation → VCE ≈ 0.2 V → output LOW (switch closed).
On the output characteristic the operating point jumps between the bottom-right end of the load line (cut-off) and the top-left end (saturation). This is how a transistor acts as a NOT gate / logic switch.

### Standard method for the "find IB, IC, VCE" circuit
Circuit: VBB – RB – base; VCC – RC – collector; emitter to ground.
1. Assume **active**: IB = (VBB − VBE(act)) / RB, with VBE(act) = 0.7 V for Si.
2. IC = β·IB.
3. VCE = VCC − IC·RC.
4. Check: if VCE > VCE(sat) (0.2 V) the assumption is correct → **active mode**. If VCE comes out below 0.2 V (or negative) the transistor is actually **saturated**: use VBE(sat) = 0.8 V, VCE = 0.2 V, IC = (VCC − 0.2)/RC.
5. If VBB < VBE(cut-in) (0.5 V) → cut-off: IB = IC = 0, VCE = VCC.

---

## T5. JFET

### Construction (n-channel)
A bar of n-type silicon (the **channel**) with **Drain** at one end and **Source** at the other. Two p-type regions are diffused on either side and joined to form the **Gate**. Symbol: arrow on the gate pointing **into** the channel for n-channel (out for p-channel).

### Operation when VGS < 0 and VDS > 0 (n-channel)
- **VDS > 0:** drain positive w.r.t. source, so electrons flow from source to drain through the channel → drain current ID.
- **VGS < 0:** the gate-channel p-n junctions are **reverse biased**, so gate current ≈ 0 (very high input impedance). The reverse bias creates **depletion regions** that extend into the channel, making it narrower and increasing its resistance → ID decreases.
- The depletion regions are **wider near the drain** because the reverse bias there is VGS − VDS (larger), so the channel is wedge-shaped.
- As VDS increases, the channel near the drain gets narrower until it **pinches off** (VDS = VP + VGS). Beyond this ID stays nearly constant (**saturation / pinch-off region**).
- If VGS is made negative enough (VGS = VGS(off)), the depletion regions meet along the whole channel and ID = 0 (**cut-off**).
- So the JFET is a **voltage-controlled** device: VGS controls ID. ID = IDSS(1 − VGS/VGS(off))².

```
        D (+VDS)
        |
   ┌────┴────┐
 p █ ◢ n  ◣ █ p     depletion (shaded) wider at the drain end
 G─█ ▐    ▌ █─G     G tied together, VGS < 0
   █ ◥    ◤ █
   └────┬────┘
        |
        S
```

### Regions of the drain characteristic (ID vs VDS)
1. **Ohmic (linear) region** – small VDS, ID rises roughly linearly with VDS (JFET acts as a voltage-controlled resistor).
2. **Saturation (active / pinch-off) region** – curves are flat; ID depends on VGS only. Used for amplification.
3. **Cut-off region** – VGS ≤ VGS(off), ID = 0 (the bottom axis).
(4. Breakdown – very large VDS, ID rises sharply; usually not drawn.)

---

## T6. Combinational vs Sequential logic circuits

| Combinational | Sequential |
|---|---|
| Output depends **only on present inputs** | Output depends on present inputs **and past outputs (state)** |
| **No memory** | Has **memory** (flip-flops / latches) |
| No feedback path from output to input | Uses **feedback** |
| No clock needed | Usually clocked (synchronous) |
| Faster, simpler to design | Slower, more complex |
| Examples: adders, multiplexers, decoders, encoders, comparators | Examples: flip-flops, counters, shift registers, registers |

---

## T7. Flip-flop tables

### JK flip-flop
Reduced (characteristic) truth table:

| J | K | Q(n+1) | Action |
|---|---|---|---|
| 0 | 0 | Qn | No change (hold) |
| 0 | 1 | 0 | Reset |
| 1 | 0 | 1 | Set |
| 1 | 1 | Qn' | Toggle |

Characteristic equation: Q(n+1) = J·Qn' + K'·Qn

Excitation table (what J, K must be to go from Qn to Q(n+1)):

| Qn | Q(n+1) | J | K |
|---|---|---|---|
| 0 | 0 | 0 | X |
| 0 | 1 | 1 | X |
| 1 | 0 | X | 1 |
| 1 | 1 | X | 0 |

Derivation: 0→0 can be done by "hold" (J=0,K=0) or "reset" (J=0,K=1) → J=0, K=X. 0→1 by "set" (1,0) or "toggle" (1,1) → J=1, K=X. 1→0 by "reset" (0,1) or "toggle" (1,1) → J=X, K=1. 1→1 by "hold" (0,0) or "set" (1,0) → J=X, K=0.

### T flip-flop
Complete truth table:

| T | Qn | Q(n+1) |
|---|---|---|
| 0 | 0 | 0 |
| 0 | 1 | 1 |
| 1 | 0 | 1 |
| 1 | 1 | 0 |

Q(n+1) = T ⊕ Qn (T=0 hold, T=1 toggle).

Excitation table:

| Qn | Q(n+1) | T |
|---|---|---|
| 0 | 0 | 0 |
| 0 | 1 | 1 |
| 1 | 0 | 1 |
| 1 | 1 | 0 |

(T = 1 whenever the output must change.)

### D flip-flop
Q(n+1) = D. On each active (positive) clock edge the output copies D; between edges it holds.

### Counter design recipe (used in every paper)
1. Choose the number of flip-flops (3 for values up to 7). Name them Q2 Q1 Q0 (Q2 = MSB).
2. Write the **state table**: present state → next state (last state goes back to the first).
3. Using the excitation table, fill in the flip-flop inputs (J,K or T) for each transition.
4. Unused states are **don't cares (X)**.
5. Simplify each input with a 3-variable K-map.
6. Draw the circuit: all clocks tied together (synchronous), gates feeding J/K or T inputs.

---

## T8. Adders, MUX and DEMUX

### Half adder
| A | B | Carry | Sum |
|---|---|---|---|
| 0 | 0 | 0 | 0 |
| 0 | 1 | 0 | 1 |
| 1 | 0 | 0 | 1 |
| 1 | 1 | 1 | 0 |

Sum = A'B + AB' = **A ⊕ B** (XOR gate). Carry = **A·B** (AND gate).

### Full adder from 2 half adders + OR gate
- HA1: inputs A, B → S1 = A ⊕ B, C1 = A·B
- HA2: inputs S1, Cin → **Sum = A ⊕ B ⊕ Cin**, C2 = (A ⊕ B)·Cin
- OR gate: **Cout = C1 + C2 = AB + (A ⊕ B)Cin**
```
 A ─┐      S1 ┌─────┐
    │ HA1 ├───┤ HA2 ├─── Sum
 B ─┘   │ Cin ─┤     │
        │C1   └──┬──┘C2
        └────[ OR ]──── Cout
```
Truth table: Sum = 1 for an odd number of 1s among A,B,Cin; Cout = 1 when two or more inputs are 1.

### Multiplexer (MUX) used to implement a function
An 8:1 MUX implements any 4-variable function: connect 3 variables to the select lines S2 S1 S0 and, for each select combination, connect the data input to **0, 1, the 4th variable, or its complement**, by looking at the pair of truth-table rows that share those 3 variables.

### Demultiplexer (1:4 DEMUX)
A demultiplexer takes **one input** and routes it to **one of many outputs**, chosen by select lines (the reverse of a MUX). A 1:4 DEMUX has 1 data input D, 2 select lines S1 S0 and 4 outputs Y0–Y3.

| S1 | S0 | Y0 | Y1 | Y2 | Y3 |
|---|---|---|---|---|---|
| 0 | 0 | D | 0 | 0 | 0 |
| 0 | 1 | 0 | D | 0 | 0 |
| 1 | 0 | 0 | 0 | D | 0 |
| 1 | 1 | 0 | 0 | 0 | D |

Y0 = S1'S0'D, Y1 = S1'S0D, Y2 = S1S0'D, Y3 = S1S0D. Built from 4 three-input AND gates and 2 NOT gates. Uses: serial-to-parallel conversion, routing data to one of several devices, memory address decoding.

### NAND-only / NOR-only conversion
- **SOP → NAND-NAND:** F = AB + CD = ((AB)'·(CD)')' → first-level NAND for each product, second-level NAND combines them. Single inverted literals: X' = NAND(X, X).
- **POS → NOR-NOR:** F = (A+B)(C+D) = ((A+B)' + (C+D)')' → first-level NOR for each sum, second-level NOR combines them. X' = NOR(X, X).

---

## T9. Measuring current (the LED question)
- Instrument: **ammeter** (or a digital multimeter set to DC mA range).
- Method: switch off the supply, **break the circuit** at the LED branch, and connect the ammeter **in series** with the LED (red/+ lead towards the higher potential, i.e. from R1 side, black/− lead to the LED anode). Select a range higher than the expected current, switch on and read the value. An ammeter has **very low resistance** so it does not change the current it measures.
- (Voltage would be measured with a voltmeter **in parallel**; a voltmeter has very high resistance.)

---

## T10. AND gate using transistor-resistor logic
Two NPN transistors are connected **in series** between VCC and the output resistor (emitter of Q1 → collector of Q2; emitter of Q2 → R_out → ground; output taken across R_out). Each base is driven by an input (A or B) through a base resistor.
```
 VCC ──────┐
          C│
 A ─RB─ B─Q1
          E│
          C│
 B ─RB─ B─Q2
          E│
           ├──── Output (Y)
           R_out
           │
          GND
```
- If **either** input is 0 V, that transistor is in cut-off → series path is open → no current in R_out → **Y = 0**.
- Only when **both** A and B are HIGH do both transistors saturate → current flows from VCC through both transistors and R_out → Y ≈ VCC (HIGH) → **Y = A·B**.

| A | B | Q1 | Q2 | Y |
|---|---|---|---|---|
| 0 | 0 | off | off | 0 |
| 0 | 1 | off | on | 0 |
| 1 | 0 | on | off | 0 |
| 1 | 1 | on | on | 1 |

(Transistors in parallel with a common collector resistor would give NOR; in series with a collector resistor, NAND.)
