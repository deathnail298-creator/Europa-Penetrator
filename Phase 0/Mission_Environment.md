# Step 0 – Mission & Environment (Europa Penetrator, Phase Zero)

## 0.1 Mission Objective

Design a **Phase Zero** penetrator architecture for **Europa** that:

1. **Punches through the ice shell** without drills, articulating booms, or other complex mechanisms.
2. **Maintains low-bandwidth communication** from the subsurface back to the surface and then to an orbiter or Earth.
3. **Returns basic, structured information** about under-ice structure and motion (e.g., presence of interfaces, broad features, and time-varying activity), using **extremely simple hardware and logic.**

This is a **mission-enabling skeleton**, not a full flight design:
- No attempt is made to optimize trajectory, mass, or detailed GNC.
- No complex science payloads are included.
- The focus is on **“can we build a stupid-simple, robust path through the ice that can talk back?”**

If later missions want higher-resolution instruments or more elaborate payloads, they can bolt onto this skeleton.

---

## 0.2 Environment Assumptions (Europa)

We assume the following about **Europa** and the operational environment:

1. **Ice Shell**
   - Global ice shell with thickness on the order of **several kilometers to tens of kilometers** (exact depth is mission-site dependent and not fixed in this Phase Zero).
   - Ice is **cold, brittle near the surface**, transitioning to **warmer, more ductile** conditions at depth.
   - Shell may contain **fractures, brine pockets, and layered structures.**

2. **Subsurface Ocean**
   - A **global subsurface ocean** exists beneath the ice shell.
   - Ocean is **salty**, likely with **convective motion** and interaction with the rocky mantle below.
   - We only assume **liquid water exists at some depth**; we do **not** assume any particular pressure, chemistry, or biological content for Phase Zero.

3. **Surface Conditions**
   - **Very low temperatures** (well below 0 °C, down toward ~100 K scale).
   - **Vacuum or near-vacuum** at the surface.
   - **High-radiation environment** due to Jupiter’s magnetosphere.
   - Potential for **surface contamination constraints** (planetary protection), but Phase Zero focuses on architecture, not bioburden protocols.

4. **Gravity**
   - Europa’s surface gravity is **~0.13 g** (about 1/7 of Earth’s).
   - This is enough for:
     - A high-velocity impactor to **seat into the ice** rather than bounce away.
     - Passive **gravity-driven descent** of internal components (e.g., acoustic beads) down a melt-tube before it refreezes.

5. **Orbital & Lighting Conditions**
   - Europa is in a **tidally locked orbit** around Jupiter.
   - Day–night cycles and eclipse conditions are governed by Jupiter’s shadow and orbital geometry.
   - For Phase Zero, we assume:
     - There is **some fraction of time with line-of-sight** from the surface antenna to an orbiter or to Earth (direct or relay).
     - Power is extremely limited; **no continuous high-duty-cycle operations**.

---

## 0.3 Mission Success Criteria (Phase Zero)

Phase Zero defines **success in brutally simple terms**:

1. **Impact & Seating**
   - The penetrator impacts the surface and:
     - Seats into the ice in a controlled way, and
     - Releases a surface or shallow-subsurface **communication node** (the mast head / “mother” node).

2. **Melt-Tube Pathway**
   - The penetrator creates or exploits a **temporary melt-tube or cavity** extending downward into the ice.
   - **Acoustic relay beads** are deployed and settle along the path before it fully refreezes.

3. **Under-Ice Sonar Node**
   - An **under-ice sonar node** (the “ocean puck”) ends up:
     - At or near the **ice–ocean interface**, or
     - In a **deep ice cavity** that still provides meaningful acoustic coupling to deeper layers.
   - The puck can:
     - Emit **simple acoustic pings**, and
     - Classify returning echoes into a coarse set of **structural / motion states**.

4. **Data Relay Chain**
   - A **linear acoustic relay chain** is established:
     - Puck → bead chain → surface mast / comm node.
   - Each element operates on **tiny power budgets** and **simple 1-bit style signaling** (e.g., presence/absence, or a small finite set of fixed patterns).

5. **Data Returned to Earth**
   - Over the mission lifetime, the surface mast:
     - Receives valid packets from the bead chain.
     - Stores and **periodically uplinks** small, discrete data packets.
   - Mission counts as Phase Zero success if **any structured under-ice data** (not just noise) is returned with:
     - A known time index, and
     - A decodable mapping to depth and basic structural/motion states.

If we can do that — even with laughably low bandwidth — the architecture is proven.

---

## 0.4 Non-Goals (Explicitly Out of Scope)

For clarity, the Europa Penetrator Phase Zero **does not** try to:

1. **Perform high-resolution imaging** (no cameras, no detailed seafloor maps).
2. **Deliver complex multi-instrument payloads** (e.g., labs, drills, arms, rovers).
3. **Maximize science return** under a fixed mass/power budget.
4. **Solve full mission design** (launch vehicle, cruise stage, detailed navigation, entry trajectory optimizations, etc.).
5. **Guarantee access to the free ocean** at all sites:
   - Some locations may not reach a true liquid layer.
   - Even in those cases, the architecture can still return **useful structural data** (layering, voids, motion signatures).

Phase Zero is intentionally **Ork-simple**:
- No moving parts if they can be avoided.
- Minimal electronics.
- Minimal logic.
- Extreme bias toward **deterministic, predictable behaviour** that can survive shock, cold, and radiation.

---

## 0.5 Architectural Philosophy

Every subsequent step (Strike & Seat, Melt-Tube, Beads, Puck, Data Model, Surface Mast) follows these core principles:

1. **No moving parts** unless absolutely unavoidable.
2. **Passive mechanisms first**, electronics second.
3. **Ultra-low-bandwidth, near 1-bit communication** wherever possible.
4. **Extreme power austerity**:
   - Components sleep almost all of the time.
   - Short, deterministic wake windows.
5. **Graceful degradation**:
   - Partial failure still yields **some** data.
   - The system tolerates lost beads, weaker coupling, and degraded electronics.
6. **Deterministic behavior**:
   - Fixed-state machines rather than adaptive algorithms.
   - Behavior that can be fully reasoned about on a whiteboard.

If a design choice conflicts with these principles, the **simpler, more deterministic option wins**, even if it is less “elegant” in a traditional engineering sense.

---
