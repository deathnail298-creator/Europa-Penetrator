# Step 8 – Surface Mast & Uplink Architecture  
(Europa Penetrator, Phase Zero)

The surface mast — also called the **mother node** — is the final relay between the penetrator system and space-based receivers (orbiter or Earth).  
It must survive a harsh radiation environment, thermal swings, micrometeoroid impacts, and vacuum exposure for years.

It does so without moving parts, heaters, or active alignment.  
Everything is passive, rugged, and deterministic.

---

## 8.1 Purpose of the Mother Node

The mother node performs exactly three functions:

1. **Receive packets** from the acoustic bead chain.  
2. **Store packets** in a circular buffer with timestamps.  
3. **Transmit packets** upward via low-power RF during scheduled windows.

It does not:
- interpret data,  
- filter packets,  
- adapt timing,  
- adjust orientation,  
- negotiate protocols,  
- detect bead-chain health,  
- or implement error correction beyond simple repetition.

The node’s architecture is “listen → store → transmit → sleep.”

---

## 8.2 Physical Architecture

The surface node is a compact, fully potted cylinder or sphere with:

- hardened outer shell (radiation + abrasion resistant),
- embedded antenna stub (fixed, no articulation),
- potted RF electronics,
- small buffer memory,
- tiny battery pack,
- acoustic piezo element for bead-chain reception.

There are **no external ports** and **no seams**.

### **Placement**
Two accepted Phase Zero configurations:
- **Surface placement**  
- **Shallow subsurface placement (~5–10 m)**

Shallow subsurface placement provides radiation shielding but still allows RF propagation through thin ice.

---

## 8.3 Receiving Packets from the Bead Chain

The node contains a piezo receiver embedded directly into its core.

Receive cycle:

1. Wake at preset interval.  
2. Enable acoustic receive mode for a short window.  
3. Detect patterns matching the packet structure (Step 7).  
4. Store valid packets.  
5. Return to sleep.

The node only needs to receive **occasional** packets for mission success.

Even partial sequences are valuable.

---

## 8.4 RF Transmission to Orbiter or Earth

The RF transmitter is:

- low-power,  
- fixed-frequency,  
- fixed-orientation,  
- extremely simple.

There is no:
- beam steering,  
- active pointing,  
- adaptive modulation,  
- or handshake protocol.

The node transmits only during fixed time windows chosen pre-launch.

### **Why fixed windows?**
- Simplicity,  
- Determinism,  
- Radiation tolerance,  
- No fault-prone timing logic.

Even if the node becomes partially buried, a small antenna stub can still radiate through centimeters of ice.

---

## 8.5 Packet Storage (Circular Buffer)

The buffer stores:
- the most recent N packets (small number),
- timestamp metadata based on an internal free-running clock,
- no overwriting protections (when full, oldest packets are lost).

This keeps memory requirements tiny and resilient.

The mast does **not** compress or merge packets.

---

## 8.6 Duty Cycle (Power Logic)

The node’s largest energy draw is RF transmission.  
To conserve power:

- RF events are rare (hours or days apart).  
- Packet reception windows are short.  
- Sleep mode dominates nearly all of the node’s lifetime.  

This ensures years of operation despite battery limits.

---

## 8.7 Environmental Hardening

The surface node must endure:

- radiation from Jupiter,  
- cold vacuum,  
- thermal cycling,  
- ice abrasion,  
- regolith-like shards near impact point.

Hardening includes:

- all electronics potted in radiation-tolerant compound,  
- no delicate conductors or exposed surfaces,  
- thick casing for puncture resistance,  
- passively protected antenna stub.

Longevity depends entirely on materials and passive buffering — no active survival systems.

---

## 8.8 Limited Bandwidth, Maximum Value

Even if the node transmits:

- a few packets per day,  
- or one per orbit,  
- or sporadically across its lifetime,

the uplinked dataset is still valuable because:

- Each packet reflects a discrete structural state beneath Europa’s ice.  
- Trends over time reveal boundary changes, ice shifts, or fluid motion.  
- Even sparse data confirms subsurface acoustic behavior and is a major win for mission architecture.

Phase Zero values **any** structured data over zero.

---

## 8.9 End-of-Life Behavior

Once battery voltage falls below safe operation:

- RF transmissions are dropped first,  
- then packet reception windows cease,  
- finally the node enters a permanent deep-sleep/off state.

There is no attempt to manage graceful shutdown or data preservation beyond the natural function of the circular buffer.

---

## 8.10 Step 8 Success Criteria

Surface Mast & Uplink Architecture is successful if:

1. The node survives impact and remains in place.  
2. It receives at least some packets from the bead chain.  
3. It stores packets in its buffer.  
4. It performs RF uplinks during scheduled windows.  
5. At least one packet reaches orbit or Earth intact.  
6. The architecture remains deterministic and power-autonomous for its operational life.

If these criteria are met, the system moves to:

### **Step 9 – Integrated System Behavior & End-of-Life Logic**

This is the final consolidation of all subsystems into a single mission timeline.

---
