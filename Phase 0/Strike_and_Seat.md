# Step 2 – Strike & Seat Architecture (Europa Penetrator, Phase Zero)

The Strike & Seat phase defines how the penetrator impacts Europa’s surface, survives deceleration, and passively establishes the two essential components:

1. The **penetrator body**, which continues downward into the ice column.
2. The **surface or shallow-subsurface communication node** (“mother node”), which remains behind to communicate uplink signals later.

No moving parts, no actuators, no deployment mechanisms — everything must occur through **impact physics**, **geometry**, **material gradients**, and **passive separation**.

---

## 2.1 Impact Philosophy

The penetrator is designed to:
- **Hit hard enough** to embed in the ice,
- **Not so hard** that it shatters itself or over-compresses internal electronics,
- **Transfer momentum** into ice disruption, fracture initiation, and cavity formation,
- **Initiate melt-tube generation** through a combination of impact heating and heat-dissipation from the HOT internal spine.

Europa's low gravity (~0.13 g) helps:
- The penetrator will **not bounce** off surface ice as easily as it might on a rocky moon,
- It will embed, even at high velocity, instead of ricocheting back to vacuum.

---

## 2.2 Structural Layout: Head → Mid → Tail

Phase Zero adopts a deliberately simple three-section body:

### **HEAD (Sacrificial Strike Section)**
- Blunt, mass-forward architecture,
- Thick-walled, overbuilt, no cavities,
- Designed to **take the full deceleration load**,
- Sacrificial crush zone (material deformation absorbs energy),
- Houses *no critical electronics*.

### **MIDSECTION (Melt-Tube Body + Storage Spine)**
- Contains:
  - HOT spine (thermal gradient source),
  - CO₂/thermal-block materials for melt-tube propagation,
  - Acoustic relay beads in a passive channel,
  - Tail-to-head passive separation plane.
- Survives and continues downward after the head’s crush event.

### **TAIL (Electronics Core, Ocean Puck Housing, Separation Plane)**
- Potted electronics (shock-hardened, radiation-hardened),
- Battery reserve core,
- Puck housing and release zone,
- Passive thermal routing elements,
- Designed to withstand high-G deceleration without moving parts.

---

## 2.3 Deceleration & Shock Management

The strike deceleration is absorbed through:

1. **Sacrificial deformation of HEAD**  
   - Metal and composite layers collapse predictably.
   - Energy absorbed mechanically, not thermally.

2. **Midsection flex and compression tolerance**  
   - Internal channels allow micro-deformation without crushing the beads or electronics.

3. **Potted electronics**  
   - All critical electronics are embedded in solid potting compound.
   - No voids, no connectors, no moving components.

4. **Rigid-to-flex material transitions**  
   - Prevents single-point failure from brittle fracture.

This architecture avoids the need for:
- gimbals,  
- damping assemblies,  
- shock absorbers,  
- isolation cages.  

All failure points that involve movement are removed.

---

## 2.4 Passive Separation (No Mechanisms)

Upon impact, the HEAD’s deformation creates **differential deceleration**:

- The HEAD experiences the highest g-load and deforms.
- The MIDSECTION experiences less.
- The TAIL experiences the least.

This produces a **shear-plane separation** at a deliberately weakened interface between the MIDSECTION and the mother-node housing.

### **How Separation Works (Passively)**

At the shear plane:
- Tabs or crushable supports fold,
- A frangible ring fractures,
- The mother node is left behind,
- The penetrator body continues to descend into the ice column.

No springs.  
No pyros.  
No actuators.  
No timing circuits.

Just **physics**.

---

## 2.5 Mother Node Deployment Options (Two Allowed Configurations)

Like you specified earlier: *Phase Zero supports both options*, because site conditions are unknown and designers may choose either.

### **Option A — Mother Node on the Surface**
The surface is clean, fracture-dominated, and open enough for RF transmission.  
Mother node sits *on or near* the impact point.

### **Option B — Mother Node Just Below the Surface**
If radiation environment is severe or surface abrasion risk is high, the mother node can be intentionally designed to remain **~5–10 meters below** the ice surface.

Benefits:
- Radiation shielding from shallow ice cover,
- Reduced thermal cycling,
- Potentially more stable long-term operation.

Both options satisfy Phase Zero criteria, and both are included intentionally.

---

## 2.6 Melt-Tube Initiation

Impact generates:
- Shock heating,
- Material friction,
- Bulk thermal diffusion from the HOT spine in the midsection.

This combination begins the **melt-tube**:
- A temporary cavity forms behind the moving penetrator,
- Slight melting + fracture pulverization creates space,
- The tube later refreezes into a sleeve, supporting bead acoustics.

Critical: the melt-tube exists *long enough* for the acoustic relay beads to settle.

---

## 2.7 Deterministic Boot Sequence

After separation, each component behaves in a **fully deterministic** manner, not relying on sensors or conditions.

### **Mother Node Boot**
- Wakes after a fixed time delay (e.g., T+30 minutes).
- Performs:
  - Self-check (voltage, internal stable reference).
  - Transition to low-duty idle.
- Waits for bead-chain signals.

### **Penetrator Body Boot**
As it descends:
- Maintains passive thermal routing.
- Releases beads by **gravity** as it slows and halts.

### **Ocean Puck Boot**
- Boots only after:
  - Depth threshold reached (gravity relocation),
  - Tail temperature change stabilized (deterministic timer trigger).

No subsystem depends on receiving a signal from another.  
No logic branches based on environment.  
Everything flows according to **timers** and **internal state**.

---

## 2.8 Step 2 Success Criteria

Strike & Seat is successful if:

1. The penetrator embeds into the ice.
2. The mother node remains behind, intact, and in its designated layer.
3. The body continues downward into the melt-tube.
4. The melt-tube cavity persists long enough for beads to settle.
5. All subsystems survive the initial impact shock.
6. Deterministic boot sequences activate without external inputs.

If all six occur, the mission transitions cleanly into Step 3.

---
