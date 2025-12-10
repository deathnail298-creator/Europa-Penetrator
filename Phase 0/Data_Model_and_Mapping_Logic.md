# Step 7 – Data Model & Mapping Logic (Europa Penetrator, Phase Zero)

The Data Model defines **what information the puck collects**, **how that information is encoded**, and **how it is transmitted upward** through the bead chain to the mother node and ultimately to Earth.

Phase Zero does *not* attempt high-resolution sensing or adaptive data formatting.  
All data structures are fixed-length, deterministic, and extremely small.

This ensures:
- beads require no adaptive logic,
- uplink timing is predictable,
- packet integrity remains decodable even with partial corruption.

---

# 7.1 Overview of the Data Model

The data returned from Europa consists of repeated, extremely small packets.

Each packet represents:
1. A **structural classification** of the region beneath the puck  
2. A **motion/turbulence classification** (if applicable)  
3. A **timestamp index** based on the puck’s internal cycle counter  

The model is intentionally simple to guarantee long-term reliability under extreme constraints.

---

# 7.2 Vertical Grid Model

Phase Zero uses a **1D vertical grid**, not a 2D or 3D map.

- The puck sends data about **the region directly beneath it**.  
- Each reading is classified into one of several fixed categories.  
- Categories are encoded using **3 bits**.

This produces a coarse but scientifically meaningful time series of vertical-structure states.

### The vertical grid cell classification (example mapping):

| Code (3-bit) | Meaning                                 |
|--------------|------------------------------------------|
| 000          | Solid / dense layer                      |
| 001          | Semi-solid / ductile ice                 |
| 010          | Cavity / void                            |
| 011          | Interface zone (ice–brine / layer change)|
| 100          | Fluid-like / absorptive medium           |
| 101          | Irregular echo (possible turbulence)     |
| 110          | Multi-path / ambiguous return            |
| 111          | No valid classification (timeout)        |

The above is an example mapping — designers may refine exact categories, but Phase Zero limits classification to a few deterministic states.

---

# 7.3 Puck-Side Classification Logic (Fixed)

The puck does **not** compute distances or shapes.  
It simply measures:

- echo amplitude,  
- echo delay window,  
- echo deformation,  
- echo multiplicity.

Each measurement is compared to **fixed thresholds** and mapped to one of the 3-bit categories.

There is:
- no adaptive thresholding,  
- no machine learning,  
- no continuous parameter tuning.

All behavior is hardcoded before launch.

---

# 7.4 Packet Structure (Fixed-Length)

Each transmission packet consists of:

[Start Pattern][Header][Payload][End Pattern]

yaml
Copy code

### **Start Pattern (4 bits)**  
A fixed sequence used to:
- mark packet beginning,
- synchronize bead relays,
- support mother node detection.

Example: `1010`

### **Header (3 bits)**  
Encodes:
- cycle counter modulo 8 (or another small modulo space),
- or a fixed rotation index for timing windows.

This ensures packets can be sequenced even if some are lost.

### **Payload (3–6 bits)**  
Minimum requirement:
- 3 bits for structural classification.

Optional additional bits:
- motion/turbulence flag (1 bit),
- confidence code (2 bits, fixed).

### **End Pattern (4 bits)**  
Example: `0101`  
Marks packet termination and ensures that corruption during relay is easier to detect.

### Total Packet Length  
11–17 bits depending on final payload size.  
Phase Zero locks it as **fixed**, never variable.

---

# 7.5 Relay Behavior Through Bead Chain

Each bead performs:

1. Wake,  
2. Listen for start pattern,  
3. If valid pattern detected:
   - capture the entire packet (fixed length),
   - immediately retransmit upward,
4. Return to sleep.

Beads do not interpret packet meaning.  
They only operate on pattern presence or absence.

Relay order naturally progresses upward because beads transmit only **in the upward direction**, dictated by:

- acoustic geometry,  
- bead orientation,  
- and deterministic transmission amplitude shaping.

No routing logic exists.

---

# 7.6 Mother Node Packet Handling

The mother node:

1. Wakes at defined intervals,  
2. Listens for complete packets,  
3. When detected:
   - stores most recent packet(s),
   - enforces small buffer (e.g., last 8 packets),
4. During RF uplink windows:
   - transmits the stored packets as-is,
   - with minimal wrapper metadata (timestamp and sequence index).

Mother node does **not**:
- decode payload meaning,  
- validate classification,  
- attempt correction,  
- compress or reformat packets.

It serves strictly as a pass-through uplink unit.

---

# 7.7 Earth-Side Reconstruction

Earth receives:
- sparse packets,  
- sometimes degraded packets,  
- sometimes repeated packets,  
- sometimes no packets for long intervals.

Reconstruction consists of:

1. Ordering packets by header index,  
2. Filling gaps with "unknown state" markers,  
3. Plotting classifications as a **time–state series**,  
4. Optionally applying smoothing or consistency checks.

The result is a coarse timeline of:
- structural changes,  
- ice–brine transitions,  
- cavity formation/collapse,  
- possible turbulence signatures.

This level of information is sufficient to validate the Phase Zero architecture.

---

# 7.8 Deterministic Puck Timing

Every packet is tied to a fixed schedule:
- e.g., one transmission every 1 hour.

A hardcoded modulo counter (3-bit header) allows Earth to reconstruct higher-level timing.

Examples:
- Counter cycles 0→7 repeatedly,
- Earth increments a virtual clock each time header repeats.

No real-time clock is required inside the puck.

---

# 7.9 Deterministic Bead Timing

Beads wake on fixed internal schedules:
- staggered timing ensures that overlapping transmissions do not require synchronization logic,
- deterministic cycle lengths ensure long-term predictability.

Timing drift is acceptable because:
- beads operate only as pattern detectors,
- they do not require phase alignment.

---

# 7.10 Step 7 Success Criteria

The Data Model & Mapping Logic is considered successful if:

1. The classification system uses fixed, deterministic categories,  
2. The packet format is fixed-length and non-adaptive,  
3. Beads can relay packets without interpreting their meaning,  
4. The mother node can forward packets without decoding,  
5. Earth can reconstruct meaningful time–state series even with missing data,  
6. The entire chain remains functional with extremely low bandwidth.

Upon meeting these criteria, the system moves to:

### **Step 8 – Surface Mast & Uplink Architecture**

---
