# Step 5 – Ocean Puck / Under-Ice Sonar Node (Europa Penetrator, Phase Zero)

The Ocean Puck is the mission’s **primary sensing instrument** and the deepest functional component of the Europa Penetrator architecture.  
Its job is not to produce images, maps, or high-resolution science — Phase Zero forbids that level of complexity.

Its job is to:

1. Emit extremely simple acoustic pings downward,  
2. Listen to the resulting echoes,  
3. Classify them using deterministic, hardcoded thresholds,  
4. Encode the classification into **tiny binary packets**, and  
5. Send those packets upward into the acoustic relay chain.

The puck is the “eye” of the entire system.  
But in Phase Zero, that eye is intentionally low-fidelity and brutally simple.

---

## 5.1 Physical Architecture

The puck is:

- A small, solid, potted sphere or disk (~5–10 cm diameter),
- Hardened against pressure, freeze-in, and ocean brine,
- Mass-balanced for predictable orientation,
- Equipped with:
  - A single piezo transmitter/receiver or a paired set,
  - A tiny battery core,
  - A fixed-timing state machine (no microcontroller required),
  - A minimal classification circuit.

All components are **fully potted**:
- No exposed seams,
- No articulating panels,
- No detachable segments.

This maximizes survivability and minimizes required testing.

---

## 5.2 Passive Deployment via Melt-Tube Collapse

The puck deploys without mechanisms or sensors.

Sequence:

1. As the penetrator tail slows and halts, the puck is freed inside the tail housing.  
2. Thermal gradients begin to collapse the melt-tube behind the penetrator.  
3. The puck is **carried downward** by:
   - gravity,
   - buoyancy gradients,
   - local melt-water flow,
   - cavity collapse dynamics.

Two allowed outcomes:

### **Outcome A: Puck Reaches the Ice–Ocean Interface**
Ideal case.  
The puck becomes buoyant and anchors beneath the underside of the ice.

### **Outcome B: Puck Rests in a Deep Ice Cavity**
Still acceptable.  
Acoustic coupling to deeper layers remains sufficient for Phase Zero structural/motion detection.

Phase Zero does **not** require the puck to reach true open ocean, only to reach an acoustically meaningful zone.

---

## 5.3 Anchoring Under the Ice

If the puck reaches the underside of the ice shell:

- It **floats upward** due to buoyancy,
- Presses gently against the ice–brine boundary,
- Remains stable for long-term operations.

There are no anchors, spikes, adhesives, or mechanisms.  
Just buoyancy physics.

---

## 5.4 Sonar Emission (Simple Downward Ping)

The puck emits:
- A fixed-frequency,
- Fixed-amplitude,
- Fixed-duration  
**downward acoustic ping**.

No beamforming.  
No chirps.  
No adaptive pulse shaping.  
Just a repeatable “tick.”

Duty cycle is extremely low:
- One ping per minute, hour, or even per several hours depending on power budget.

---

## 5.5 Echo Reception & Classification

Echo returns are classified using **fixed thresholds**:

- Strong return → “Solid Layer Below”
- Weak return → “Soft Layer / Cavity”
- Delayed or multi-bounce → “Possible Interface”
- No meaningful return → “Fluid-like Region / Absorptive Medium”
- Irregular jitter → “Motion / Turbulence State”

Each classification is encoded into a **3-bit state** (exact mapping finalized in Step 7).

No attempt is made to:
- measure distance,
- map topography,
- estimate material composition,  
- or track continuous motion.

The puck is *not* a science instrument — it’s a binary classifier.

---

## 5.6 Packet Creation (Fixed Pattern)

The classification result is inserted into a tiny, deterministic binary packet with:

- **start pattern** (e.g., 1010),
- **payload** (3–6 bits),
- **end pattern** (e.g., 0101).

All packets are the same length.  
There is no negotiation or dynamic resizing.

This ensures:
- acoustic relay beads do not need adaptive logic,
- uplink timing is predictable,
- packet integrity can be interpreted even with partial corruption.

---

## 5.7 Transmission Upward

The puck emits the packet acoustically:

- upward through ice,
- where the nearest bead receives it,
- repeats it,
- and passes it bead-by-bead to the mother node.

The puck never hears the chain;  
it does not receive acknowledgments;  
it does not retry.

It simply **transmits** its classification at fixed intervals.

---

## 5.8 Power Regime

The puck uses:

- a tiny, high-density battery cell,
- extremely rare wake cycles,
- short ping and transmission events,
- long periods of deep sleep.

Expected operational life:  
**years** in the best case;  
**months** in high-loss environments.

Phase Zero requires endurance long enough for at least some data to reach the surface mast.

---

## 5.9 Survivability Requirements

The puck must survive:

- refreeze pressures,
- thermal cycling,
- ice creep,
- brine infiltration,
- ocean salinity exposure,
- radiation penetrating deep ice layers.

Survival is achieved through:
- Full potting,
- No seams,
- No openings,
- No moving parts,
- Thick, crack-resistant outer shell,
- Internal redundancy only at the materials level.

---

## 5.10 Step 5 Success Criteria

The puck subsystem is successful if:

1. It passively deploys into a meaningful depth zone,  
2. Anchors against the underside of ice or rests stably in a deep cavity,  
3. Emits deterministic sonar pings,  
4. Classifies echoes into fixed structural/motion categories,  
5. Encodes packets correctly,  
6. Transmits packets upward in a way beads can relay,  
7. Survives long enough to send multiple cycles of data.

If these conditions hold, the architecture proceeds naturally to **Step 6 – Power & Thermal Notes** (consolidated support logic).

---
