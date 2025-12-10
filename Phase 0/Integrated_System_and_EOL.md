# Step 9 – Integrated System Behavior & End-of-Life Logic  
(Europa Penetrator, Phase Zero)

This step consolidates all subsystems — Strike & Seat, Melt-Tube, Bead Chain, Puck, and Surface Mast — into one unified mission timeline.  
Every subsystem must operate without coordination signals, without moving parts, and without adaptive behavior.  
Mission performance must remain predictable from the moment of launch to the final packet sent.

The Europa Penetrator is designed so that even **partial success** yields scientifically meaningful data.

---

# 9.1 Mission Timeline Overview

The mission unfolds in seven deterministic phases:

1. **DORMANT–CRUISE**  
2. **IMPACT–SEQUENCE**  
3. **MELT–TUBE FORMATION**  
4. **CHAIN–SETTLE**  
5. **PUCK–INIT**  
6. **SURVEY–CYCLE**  
7. **UPLINK–CYCLE**  
8. **EOL–FADE / EOL–SLEEP**

No phase depends on real-time decision-making.  
The entire sequence is driven by timers, physics, and passive transitions.

---

## 9.2 Phase 1 — Dormant–Cruise

Before impact:

- All electronics are in deep sleep.  
- Timing circuits run but no active sensing occurs.  
- Internal thermal mass stabilizes.

There are no events until impact shock forces transition to Phase 2.

---

## 9.3 Phase 2 — Impact–Sequence

Impact instantly produces:

1. **HEAD deformation** (sacrificial crush zone).  
2. **Passive shear-plane separation** between body and mother node.  
3. **Mother node** remains near surface.  
4. **Penetrator body** continues deeper.  
5. **Electronics transition from dormant to “impact-triggered timers.”**

The system does not attempt to react to real-time conditions.  
The impact is the only trigger needed to start the countdowns that govern all later behavior.

---

## 9.4 Phase 3 — Melt–Tube Formation

As the penetrator descends:

- Impact and friction generate a cavity,  
- HOT spine releases stored thermal mass,  
- Melt-tube forms and briefly persists,  
- Tail drags through the softened channel.

This phase ends when:

- The penetrator comes to rest,  
- Melt-tube begins cooling,  
- Cavity starts to refreeze.

---

## 9.5 Phase 4 — Chain–Settle

As the melt-tube softens then cools:

1. Acoustic beads fall out of the bead reservoir.  
2. Gravity, convection, and cavity geometry distribute them along the tube.  
3. Tube refreezes from outside inward, locking beads into an icy waveguide.

No timing, sensors, or triggers are needed.  
This is pure passive physics and is one of the most robust elements of the system.

This phase ends when the internal temperature gradient stabilizes.

---

## 9.6 Phase 5 — Puck–Init

Once the penetrator halts and the tail cools:

- A fixed timer started at impact expires.  
- The puck transitions from deep sleep to **initialization mode**.  
- Initialization performs:
  - internal voltage check,  
  - thermal reference check,  
  - activation of survey cycle timing.

The puck does **not** wait for bead-chain confirmation.  
It does not wait for environment cues.  
It operates on internal timing only.

---

## 9.7 Phase 6 — Survey–Cycle (Core Science Loop)

This is the primary operational loop.

### Each cycle:
1. Wake from deep sleep.  
2. Emit one simple downward sonar ping.  
3. Listen for echo(s).  
4. Classify into 3-bit structural/motion code.  
5. Construct fixed-format packet.  
6. Transmit packet upward.  
7. Return to deep sleep until next interval.

Typical interval: **tens of minutes to several hours**, chosen pre-launch.

This cycle repeats for months or years.

---

## 9.8 Phase 7 — Uplink–Cycle (Mother Node Loop)

The mother node operates on its own non-adaptive schedule.

### Each uplink cycle:
1. Wake.  
2. Listen through acoustic element for incoming packets from bead chain.  
3. Store valid packets in circular buffer.  
4. During scheduled RF window:
   - transmit buffer contents upward,  
   - optionally repeat slow redundancy pattern.  
5. Return to deep sleep.

The mast must operate autonomously even if bead-chain traffic is intermittent or irregular.

---

## 9.9 Integrated Behavior Summary

The entire system acts like a **mechanical clock**:

- Impact → starts all timers.  
- Melt → enables bead deployment.  
- Freeze → locks waveguide.  
- Puck → surveys at fixed intervals.  
- Chain → relays when awake.  
- Mast → uplinks on schedule.

There is **no dependency chain**, only overlapping deterministic behaviors.

---

# 9.10 Failure Tolerance

The architecture tolerates:

- bead loss or breakage,  
- weak acoustic coupling,  
- partial melt-tube collapse,  
- puck drift from ideal depth,  
- mother node burial in shallow frost,  
- intermittent packet relay,  
- radiation damage over time.

Mission success threshold is intentionally low:

> If **any** valid classification packets reach orbit or Earth,  
> the Phase Zero architecture is considered successful.

---

# 9.11 End-of-Life Logic (EOL)

As batteries drop:

### 1. Puck EOL  
- Survey intervals lengthen (due to voltage sag).  
- Eventually pings cease.  
- Puck enters permanent deep sleep.

### 2. Bead EOL  
- Fewer beads wake.  
- Relay becomes intermittent.  
- Chain eventually becomes silent.

### 3. Mother Node EOL  
- RF uplink windows fail first.  
- Then acoustic listening stops.  
- Finally, node powers down permanently.

There is **no active shutdown** procedure.  
EOL behavior is simply progressive dropout of each subsystem.

---

# 9.12 Phase Zero Mission Completion

The mission ends formally when:

- the mother node ceases RF uplink entirely,  
- surface telemetry confirms no further transmission attempts,  
- or analysis shows only noise after multiple expected uplink windows.

Even after death, the architecture’s data is preserved on Earth:
- timestamps,  
- classification sequences,  
- relay performance records.

This dataset becomes the evidence base proving feasibility of a Europa penetrator system.

---

# 9.13 Step 9 Success Criteria

The Integrated System & EOL logic is complete when:

1. All phases operate without coordination signals.  
2. Every subsystem follows deterministic rules.  
3. The mission produces at least some structured under-ice data.  
4. The architecture degrades gracefully rather than failing catastrophically.  
5. EOL behavior requires no intervention.

This completes the **Phase Zero Europa Penetrator** architecture.

---
