# DSE 19.1F Computer Technology (22 Aug 2019) – Model Answers

Answer ALL questions (50 marks). Full theory with diagrams: `CT Common Theory - Answers.md` (referred to as Tx).

---

## Question 1

### (a) Current conduction in an n-type semiconductor (5 marks)
- n-type = Si doped with a pentavalent donor (P, As, Sb). The 5th valence electron of each donor is free, so there are many free electrons (**majority carriers**) and few holes (**minority carriers**). Donor atoms become fixed + ions.
- When a voltage is applied across the crystal, an electric field is set up. **Free electrons drift towards the positive terminal**, and the few holes drift towards the negative terminal.
- Electrons leaving the crystal at the + end are replaced by electrons entering from the − terminal, so a continuous current flows. Conventional current flows from + to − (opposite to electron flow).
- Current is carried almost entirely by electrons; conductivity is much higher than intrinsic Si.

Diagram: a block of n-type material between + and − battery terminals; free electrons (−) with arrows pointing towards +, fixed ⊕ donor ions shown in the lattice, a few holes (o) moving towards −; conventional current arrow in the external wire from + through the block to −. (See T1.)

### (b) Forward-biased operating mode (5 marks)
- p side (anode) connected to +, n side (cathode) to −.
- The applied voltage opposes the barrier potential, so the **depletion region becomes narrower**.
- Once the applied voltage exceeds the cut-in voltage (0.7 V Si / 0.3 V Ge), electrons from n and holes from p cross the junction and recombine → **large forward current**, rising exponentially with voltage.
- Current is limited only by the external resistance; the diode acts like a closed switch with ≈0.7 V drop. (See T2.)

### (c) Full-wave rectifier with smoothing capacitor (10 marks)
Draw a bridge (4 diodes) or centre-tapped (2 diodes) rectifier, with **C in parallel with R_L**.
- Positive half cycle: D1, D2 conduct (bridge) → current through R_L, C charges to Vpeak.
- Negative half cycle: D3, D4 conduct → current through R_L in the **same direction**, C recharges.
- Between peaks, when the rectified voltage falls below the capacitor voltage, the diodes switch off and **C discharges slowly through R_L**, holding the output up.
- Result: nearly steady DC with small ripple at **2× supply frequency**. Larger C → less ripple.

Waveforms: (1) AC input sine; (2) full-wave rectified humps (all positive); (3) smoothed output – almost flat near Vpeak with small sawtooth ripple. (See T3.)

### (d) Figure 1.1 with a Ge diode, V = 9 V, using the curves in Figure 1.2 (5 marks)

**i. PIV and reverse saturation current (Ge curve)**
- The Ge reverse curve breaks down at about **−50 V → PIV ≈ 50 V**.
- The flat part of the Ge reverse curve sits at about **1–2 µA → Is ≈ 2 µA**.
(For comparison, Si: PIV ≈ 100 V, Is < 1 µA.)

**ii. Forward voltage at IF = 40 mA**
From the Germanium forward curve: **VF ≈ 0.4 V** at 40 mA. (Si would need ≈ 0.75 V.)

**iii. Voltage across R and value of R at I = 40 mA**
- VR = V − VF = 9 − 0.4 = **8.6 V**
- R = VR / I = 8.6 / 0.040 = **215 Ω**

(Values read from a graph: small differences, e.g. VF = 0.35–0.45 V, are acceptable if the method is shown.)

---

## Question 2

### (a) Two types of BJT (5 marks)
**NPN** and **PNP**. NPN: emitter arrow points **out** of the base. PNP: arrow points **in**. Label C, B, E on each. (See T4.)

### (b) Switched-mode operation (5 marks)
Draw the output characteristic (IC vs VCE for several IB) with a load line from (VCC, 0) to (0, VCC/RC).
- **OFF:** IB = 0 → operating point at the bottom of the load line in the **cut-off region**; IC ≈ 0, VCE ≈ VCC. Acts like an open switch.
- **ON:** IB large (β·IB ≥ IC(sat)) → operating point at the top of the load line in the **saturation region**; VCE ≈ 0.2 V, IC ≈ VCC/RC. Acts like a closed switch.
- The transistor is switched quickly between these two points and never rests in the active region. This is how BJTs act as logic switches / inverters. (See T4.)

### (c) Si, β = 50, RB = 200 kΩ, RC = 1 kΩ, VCC = 12 V, VBB = 6 V (5 marks)
Assume **active** (VBE = 0.7 V):
- IB = (6 − 0.7) / 200 kΩ = 5.3 / 200 000 = **26.5 µA**
- IC = β·IB = 50 × 26.5 µA = **1.325 mA**
- VCE = VCC − IC·RC = 12 − 1.325 mA × 1 kΩ = 12 − 1.325 = **10.675 V**

VCE > 0.2 V → **active mode** confirmed.

### (d) JFET circuit: VDD = 10 V, VGG = 0.9 V, RG = 1 kΩ, RD = 8 kΩ (10 marks)

**i. Type:** **n-channel JFET** (the gate arrow points into the channel, and the characteristic has positive ID/VDS with negative VGS values and VGS(off) = −3 V).

**ii. Three regions** (mark on Figure 2.2):
1. **Ohmic / linear region** – left of the knee (VDS below ~1–2 V), ID rises almost linearly with VDS.
2. **Saturation / active (pinch-off) region** – flat part of the curves; ID set by VGS.
3. **Cut-off region** – VGS ≤ VGS(off) = −3 V, ID = 0 (along the VDS axis).

**iii. Gate-source voltage**
The gate-channel junction is reverse biased, so gate current IG ≈ 0 and there is no drop across RG:
VGS = −VGG − IG·RG = **−0.9 V**

**iv. Load line**
KVL around the drain loop: VDD = ID·RD + VDS
→ **ID = (VDD − VDS) / RD = (10 − VDS) / 8 kΩ**
- VDS = 0 → ID = 10 / 8 kΩ = **1.25 mA** (point (0 V, 1.25 mA))
- ID = 0 → VDS = **10 V** (point (10 V, 0 mA))
Draw a straight line between these two points on Figure 2.2.

**v. Operating point**
The load line is very low (maximum 1.25 mA) while the VGS = −0.9 V curve saturates at about 5.5 mA, so the line crosses that curve on its steep **ohmic** part, close to the origin.
Approximate slope of the VGS = −0.9 V curve near the origin ≈ 5 mA per 0.8 V (≈ 160 Ω). Solving ID = VDS/0.16 kΩ with ID = (10 − VDS)/8 kΩ gives VDS ≈ 0.2 V.

**Q-point ≈ (VDS ≈ 0.2 V, ID ≈ 1.2 mA) → JFET is in the ohmic (linear) region.**

(Tip: if your printed paper actually had RD = 0.8 kΩ, the load line would run from 12.5 mA to 10 V and cross the −0.9 V curve in saturation at about (VDS ≈ 5.6 V, ID ≈ 5.5 mA). With RD = 8 kΩ as printed, the answer is the ohmic-region point above.)
