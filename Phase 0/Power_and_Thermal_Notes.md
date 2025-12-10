# Step 6 – Power & Thermal Notes (Europa Penetrator, Phase Zero)

Phase Zero restricts the power and thermal systems to the bare minimum needed to operate the puck, the bead chain, and the surface mast.  
There are **no heaters**, **no active thermal control**, **no power switching logic**, and **no recharge capability** once deployment begins.

This step consolidates the underlying support rules all subsystems depend on.

---

## 6.1 Power Architecture Overview

The system uses three miniature battery systems:

1. **Puck Battery**  
   - Highest endurance requirement.  
   - Operates for months to years on extremely low duty cycles.  
   - Deep-sleep dominant.

2. **Bead Batteries**  
   - Watch-battery–class cells.  
   - Power simple listen → repeat → sleep cycles.  
   - Designed to outlive most expected structural failures.

3. **Mother Node Battery (Surface Mast Core)**  
   - Larger than beads/puck but still small.  
   - Handles periodic RF uplinks to orbit/Earth.  
   - Operates under the harshest radiation and thermal cycling.

There is **no primary-to-secondary power sharing**, no bus hierarchy, and no cross-subsystem dependencies.

Each node is power-autonomous.

---

## 6.2 Power Philosophy

The entire system assumes:

- **Energy is scarce.**  
- **Duty cycles must be microscopic.**  
- **Wake durations must be extremely short.**  
- **Sleep dominates more than 99.9% of operational time.**

### Explicit prohibitions:
- No heaters.  
- No solar panels.  
- No RTGs.  
- No thermoelectric harvesters.  
- No dynamic power management.  

These are beyond Phase Zero’s simplicity constraints.

The only permissible power behavior is:
- *wake → perform fixed action → sleep → repeat.*

---

## 6.3 Puck Power Regime

The puck:
- Wakes at fixed intervals (e.g., every 30–180 minutes).  
- Emits a single acoustic ping.  
- Listens briefly.  
- Classifies echoes.  
- Creates a packet.  
- Transmits upward.  
- Returns to deep sleep.

Wake window:
- Typically a few seconds total.

This regime enables multi-year potential life depending on battery chemistry and thermal environment.

---

## 6.4 Bead Power Regime

Beads follow a simpler version:

1. Wake,
2. Listen for packet patterns,
3. If detected, relay upward,
4. Sleep.

Wake durations: milliseconds to fractions of a second.  
Sleep durations: minutes to hours.

Because relay events are rare, beads expend almost no energy across long timescales.

A bead failure is not mission-fatal — redundancy is baked into the chain.

---

## 6.5 Mother Node Power Regime

The mother node (surface/shallow mast):

- Sleeps most of the time to conserve power.  
- Wakes periodically to:
  - check for acoustic packets relayed from beads,  
  - store the latest packet(s),  
  - perform RF uplink during scheduled windows.  

RF events are the largest single energy cost.  
Therefore:
- Uplink windows are rare,  
- Packets are buffered in a tiny memory,  
- Transmission occurs only during valid geometry (orbiter pass or Earth line-of-sight).

No adaptive window prediction is allowed — timing is fixed pre-launch.

---

## 6.6 Thermal Zones Inside the Penetrator

The penetrator body is divided into three thermal zones:

### **HOT Zone (Spine)**
- Provides melt-tube initiation and sustainment.
- Contains no sensitive electronics.
- High thermal mass allows slow cooldown.
- Physically isolated from bead reservoir.

### **COOL-STABLE Zone (Bead Reservoir)**
- Low-conductance pathways isolate beads from HOT zone.
- Beads remain below material softening thresholds.
- Electronics inside beads are unaffected by short-term thermal transients.

### **COLD Zone (Tail / Puck Housing)**
- The environment cools rapidly after halt.
- Puck’s potting compound buffers thermal swings.
- Relies on insulation, not heating, to maintain survival.

This architecture ensures each subsystem operates within its tolerances without active thermal regulation.

---

## 6.7 Mother Node Thermal Behavior

The surface/shallow-subsurface node endures:

- large radiation load,  
- thermal cycling with Europa’s day/night and eclipse patterns,  
- near-vacuum surface temperatures (extreme cold).

Protection mechanisms:

- heavy potting insulation,  
- durable outer shell,  
- low-conductive pathways to internal electronics,  
- passive thermal buffering through material mass.

There are **no heaters** or active thermal clamps.

Survival depends entirely on:
- materials,  
- potting,  
- geometry,  
- and sleep-dominant duty cycles to limit self-heating.

---

## 6.8 Thermal Behavior of the Bead Chain

Beads become embedded in the refrozen melt-tube sleeve, which provides:

- stable temperature over long periods,  
- low daily thermal cycling compared to surface,  
- mechanical stability,  
- excellent acoustic coupling.

Slow deformation or pressure changes do not threaten bead integrity.  
Even if a bead cracks internally, acoustic reflectivity often persists.

---

## 6.9 Puck Thermal Behavior

The puck is expected to:

1. Experience a cooling phase after deployment,  
2. Settle into a long-term stable temperature profile (either deep ice or ocean interface),  
3. Use potting and internal mass to buffer rapid thermal shifts.

The puck cannot regulate its temperature — it only survives through ruggedness and minimal electronics.

---

## 6.10 Step 6 Success Criteria

Power & Thermal Notes are satisfied if:

1. All subsystems operate autonomously using their own battery supply,  
2. Wake–sleep timing supports long-term endurance,  
3. No active heating or control is required,  
4. Thermal zones protect sensitive components during and after impact,  
5. Puck, beads, and mother node remain functional across expected ice/ocean conditions,  
6. The architecture remains fully deterministic and self-contained.

With these conditions met, the system moves to:

### **Step 7 – Data Model & Mapping Logic**  
(the part the coders will pay attention to).

---
