# Step 4 – Acoustic Relay Beads (Europa Penetrator, Phase Zero)

The acoustic relay beads form the **communication backbone** between the under-ice sonar puck and the surface mast.  
They are intentionally simple: no processors, no radios, no advanced electronics.  
Each bead is a **tiny, hardened, shock-tolerant acoustic repeater** operating on:

- deterministic wake/sleep timing,  
- ultra-low-duty listening windows,  
- 1-bit (or near 1-bit) acoustic relay logic, and  
- passive survival mechanisms.

The bead chain is designed so that **even partial functionality** yields meaningful mission results.

---

## 4.1 Purpose of the Beads

The relay beads serve three functions:

1. **Create a redundant acoustic ladder** from puck → surface mast.  
2. **Amplify** simple binary acoustic pulses via repeat-and-forward logic.  
3. **Maintain transmission** even if:
   - some beads fail,
   - coupling degrades,
   - refreeze introduces scattering zones.

The chain converts a difficult, long-distance propagation problem into many short hops, each a few meters apart.

---

## 4.2 Physical Form of Each Bead

Each bead is:

- roughly **marble-sized** (6–15 mm range),
- spherical or near-spherical,
- solid-state potted electronics,
- hardened exterior shell,
- no connectors, no ports, no seams,
- designed to survive:
  - pressure,
  - freeze-in,
  - slow deformation,
  - radiation,
  - impacts.

### **Exterior Shell**
- High acoustic impedance,  
- Thin enough to permit clean transmission,  
- Thick enough to resist freeze-crack and brine infiltration.

### **Internal Layout**
- tiny power cell (watch-battery scale),
- piezo transmitter/receiver pair or single bidirectional piezo element,
- minimal timing and relay circuit (deterministic),
- no microcontroller if avoidable.

---

## 4.3 Deployment Mechanism (Gravity Only)

Beads are **stored in a passive channel** inside the midsection.

They deploy because:

- The penetrator decelerates,
- The bead reservoir transitions from “compressed” to “gravity dominant,”
- Beads fall out the rear of the midsection,
- They **settle into the melt-tube cavity** as it forms and refreezes.

There is no mechanism.  
No actuator.  
No dispenser.  
Just gravity and geometry.

---

## 4.4 Spacing Distribution

The beads naturally form a roughly continuous downward chain:

- Spacing ≈ **0.3 m to 3 m** depending on:
  - melt-tube geometry,
  - bead mass,
  - local ice dynamics.

Perfect spacing is not required.  
The architecture only demands **probabilistic continuity** — missing beads do not collapse the chain.

---

## 4.5 Wake–Sleep Power Regime

Each bead follows a **fixed cycle** determined before launch:

1. **Sleep** for long intervals (minutes to hours).  
2. **Wake briefly** (milliseconds to seconds).  
3. **Listen** for incoming acoustic pulses.  
4. **Forward** detected pulses according to deterministic logic.  
5. **Return to sleep**.

There is no negotiation, no handshaking, no dynamic timing.

All beads are synchronized not by communication but by **pre-set timing offsets** that remain deterministic even after decades.

---

## 4.6 Acoustic Relay Logic (Three-State)

Beads operate on a minimal logic set:

### **State 0 — Sleep**
- No transmission,
- No reception,
- Extreme power conservation.

### **State 1 — Listen**
- Piezo element enabled,
- Listens for pulse patterns,
- Only active for a short window.

### **State 2 — Relay**
- If a recognizable pattern is received,
- Emit the corresponding relay pulse upward (toward surface),
- Then return to sleep.

Pattern recognition is trivial:
- e.g., presence vs absence,
- Short vs long pulse,
- One of a few fixed hardcoded patterns.

No bead ever generates new information.  
They only **repeat what they receive**.

---

## 4.7 Redundancy & Failure Tolerance

The chain is designed to lose beads and continue working.

Failure modes tolerated:

- bead dies (battery exhaustion),
- bead cracks but remains acoustically reflective,
- bead partially couples but transmits weakly,
- bead shifts slightly in its refrozen shell.

Because each bead covers only a small transmission distance:
- missing nodes create **attenuation**, not **total disconnect**,
- reflections off ice sleeve can occasionally bypass a bead entirely.

The system is deliberately over-provisioned with beads, expecting some loss.

---

## 4.8 Environmental Hardening

Beads must tolerate:

- refreeze pressure,
- slow deformation from ice flow,
- micro-cracking around the sleeve,
- brine exposure,
- low temperatures,
- radiation.

Hardening strategies include:

- full potting of all internal components,
- corrosion-proof exterior,
- minimal internal air gaps,
- rigid spherical geometry,
- material choice with low brittleness at cryogenic temperatures.

---

## 4.9 Acoustic Behavior After Freeze-In

After refreezing, beads become embedded in an **acoustic waveguide**:

- Ice sleeve = medium,
- Beads = transmission nodes,
- Higher acoustic impedance contrast yields sharper pulses.

This structure remains stable for decades.

Some beads may shift slightly due to local ice creep.  
The architecture tolerates this without concern.

---

## 4.10 Why Acoustic Instead of EM or Wire?

**RF fails** under kilometers of ice.  
**Optical fails** because scattering is catastrophic in Europa’s shell.  
**Wires fail** due to strain, freeze-in stress, and long-term ice motion.

Acoustics are:
- simple,
- low-power,
- mechanically robust,
- tolerant to refreeze,
- capable of long life,
- fully compatible with one-shot deployment.

This is the only communication method consistent with Phase Zero constraints.

---

## 4.11 Step 4 Success Criteria

The bead subsystem is successful if:

1. Beads deploy by gravity into the melt-tube.  
2. At least partial spacing continuity is achieved.  
3. Freeze-in produces a stable acoustic sleeve.  
4. Each bead cycles through deterministic wake–sleep states.  
5. At least one upward relay path forms between puck and mother node.  
6. The system tolerates partial bead failure without collapse.

Upon achieving these, the mission moves to **Step 5 – Ocean Puck / Under-Ice Sonar Node**.

---
