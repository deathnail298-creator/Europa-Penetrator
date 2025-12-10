# Step 1 – Design Rules & Simplicity Constraints (Europa Penetrator, Phase Zero)

Phase Zero is governed by a strict set of construction rules.  
These rules exist to prevent scope creep, eliminate dependencies on delicate mechanisms, and ensure the penetrator can survive **shock, cold, radiation, vacuum, freeze-in, and decades of decay**.

These rules are not suggestions.  
They are the non-negotiable backbone of the Europa Penetrator architecture.

---

## 1.1 Core Guiding Principle

**If a subsystem can be built without moving parts, it must be.**  
If electronics can be replaced by **passive geometry or deterministic state logic**, they must be.

The entire system should be explainable on a whiteboard and robust enough that a non-expert could assemble a functional mockup with basic materials.

---

## 1.2 Phase Zero Simplicity Constraints

These constraints define the boundaries of what can be built in this architecture.

### **Rule 1 — No Moving Parts**

The penetrator cannot rely on:
- drills  
- deployable booms  
- steering fins  
- actuators  
- mechanical release systems  
- hinges, latches, springs, or precision mechanisms  

Every deployment action must arise from:
- **impact physics**
- **thermal gradients**
- **gravity**
- **passive separation**
- **melt-tube collapse**
- **buoyancy**

If it moves, it’s a liability.

---

### **Rule 2 — Prefer Passive Over Electronic**

Whenever the choice exists:
- use **geometry**,  
- use **density differences**,  
- use **thermal expansion / contraction**,  
- use **gravity**,  
- use **fixed materials properties**,  

before invoking:
- sensors  
- processors  
- microcontrollers  
- onboard logic  

Electronics are reserved for:
- the sonar puck’s timed ping  
- minimal classification logic  
- the bead-chain’s acoustic relay  
- the surface mast’s periodic RF packet

Everything else avoids them entirely.

---

### **Rule 3 — Ultra-Low Bandwidth by Design**

The communication system is allowed:
- **tiny packets**
- **fixed-length patterns**
- **near 1-bit acoustic signaling**
- **simple relay logic**

It is *not* allowed:
- continuous transmission  
- variable-length protocols  
- dynamic routing  
- error-correcting codes beyond trivial redundancy  
- any adaptive learning or software updates  

Bandwidth is scarce by design.  
If it cannot fit in a few dozen bits per cycle, it does not belong in Phase Zero.

---

### **Rule 4 — Deterministic State Machines Only**

Every subsystem must behave in a way that can be predicted on the ground with 100% certainty.

No adaptive algorithms.  
No machine learning.  
No environment-dependent decision trees.

Examples of allowed deterministic behavior:
- time-based wake cycles  
- fixed echo classification thresholds  
- preset acoustic pulse sequences  
- dead-simple relay logic (listen → repeat → sleep)

The entire architecture must be provable, testable, and failure-tolerant *before* it ever sees Europa.

---

### **Rule 5 — Power Austerity Is Mandatory**

Energy is the enemy.  
Everything must be designed to:
- sleep nearly all the time  
- wake briefly  
- expend minimal energy per operation  
- reduce heat dissipation  
- avoid long duty cycles  

Power sources (small batteries) must be sufficient for:
- **years** of ultra-low-duty behavior  
- **occasional** communication cycles  
- nothing else  

No heaters other than:
- shock-survival warm packs inside potted electronics  
- the residual heat of electronics during wake windows

Phase Zero cannot afford active thermal management.

---

### **Rule 6 — Radiation, Shock, and Freeze-In Survival Over Performance**

The environment will try to kill the system in every possible way.  
Therefore:
- electronics must be potted  
- wiring lengths minimized  
- interfaces ruggedized  
- bead-shells hardened against pressure and freeze-in  
- the melt-tube must be survivable even as it collapses and refreezes  
- the ocean puck must tolerate refreezing, ice shifts, and brine infiltration  

A subsystem that performs better but is less survivable is rejected.

---

### **Rule 7 — Graceful Degradation**

The architecture must continue functioning even when:
- some beads fail  
- some acoustic paths degrade  
- the puck’s signal weakens  
- partial freeze-in distorts relay coupling  
- packet reception becomes intermittent  
- radiation degrades electronics over time  

Minimum success =  
**Any structured under-ice data returning to Earth over the mission lifetime.**

No single failure may collapse the entire chain.

---

### **Rule 8 — Subsystem Independence**

Every subsystem must be able to:
- initialize independently  
- operate independently  
- fail independently  

No subsystem is allowed to depend on the health or responsiveness of another.  
The chain works because each link is a **simple, self-contained node** with deterministic behavior.

---

### **Rule 9 — Fixed Geometry & Simple Materials**

Materials must be:
- common  
- stable  
- tolerant of huge thermal swings  
- machinable without exotic fabrication  

Complex composites, precision tolerances, wafer-level assemblies, delicate sensors, and fine mechanical structures are out.

If something requires micron precision or an assembly cleanroom, it’s not Phase Zero.

---

### **Rule 10 — Architect for Success at Any Depth**

Phase Zero does not assume the penetrator reaches:
- the true ice–ocean interface  
- a specific depth  
- uniform ice structure  

It must still return useful structural/motion data even if the puck ends up:
- trapped in deep ice  
- sitting in a brine pocket  
- lodged in a cavity  
- at a partial melt boundary  

The mission architecture must succeed **without** relying on precise depth or ideal conditions.

---

### **Rule 11 — Minimize Dependency on Site Conditions**

The penetrator must work whether:
- the surface is fractured or smooth  
- the melt-tube is straight or kinked  
- brines are present or absent  
- the ice is hard, brittle, layered, or slushy  
- the impact site is highlands, plains, or chaos terrain  

If the system needs a “perfect site,” it fails Phase Zero criteria.

---

### **Rule 12 — If There’s Ambiguity, Choose the Stupidly Simple Option**

This is the architectural tiebreaker.

If you have a choice between:
- elegant but fragile  
- sophisticated but high-power  
- clever but sensitive  
- high-performance but risky  
…  
versus:
- dumb  
- brute-force  
- passive  
- tolerant  
- impossible to break  

The system must choose the **dumb** option.

Phase Zero is a prototype architecture meant to prove that Europa can be penetrated and that subsurface communication can be maintained. Nothing more.

---

## 1.3 Success Criterion for This Step

A design that obeys all 12 rules is considered a Phase Zero–compatible subsystem.

A design that violates even one rule must be rejected or re-engineered before integration in later steps.

---
