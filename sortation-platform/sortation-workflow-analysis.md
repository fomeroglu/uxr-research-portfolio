# Sortation Platform — Workflow Usability Research

## Research question

The weight and dim station was the first scan any package received and the reported primary bottleneck in the sortation process. Every package passed through it before moving to secondary sort. The root cause was unknown — competing hypotheses included system latency, unclear UI feedback, and workflow complexity.

The station's operator behavior had never been formally observed, so the investigation combined direct observation with behavioral data to separate a workflow explanation from a hardware one.

**Baseline throughput: 266 packages per hour** at the weight and dim station, measured across package types.

---

## Research methods

Three separate research efforts touched this product. Two are ongoing programs that run independent of any single investigation; the third is the focused study that produced the findings below.

### Ongoing product research (standalone programs)

A **recurring operator survey program** benchmarks satisfaction and surfaces priorities across the platform — Likert ratings, open-ended pain-point questions, and Kano classification for features under consideration. Across cycles, scanning friction consistently registered as a high-priority concern while several assumed priorities did not, which helped direct attention toward the scanning experience over time.

A **periodic heuristic evaluation** assesses the sortation system against 14 usability principles, scored against observable operator behavior and system response. The lowest-scoring areas consistently cluster around error prevention, recovery, and feedback — pointing to where the experience most needed attention.

These are continuous learning programs. They inform the roadmap broadly rather than feeding one investigation.

---

### The bottleneck investigation (this study)

**Contextual field inquiry.** Observation sessions across facilities with distinct operational profiles — different volumes, package mixes, and operator configurations — watching operators process packages through the full sortation sequence across multiple shifts, with structured feedback from operations managers.

*Finding:* Operators had developed informal workarounds for limitations the product team hadn't formally documented. The scanning sequence was repetitive and interruptible, and certain package types caused unpredictable stops.

**Behavioral analysis.** Analysis of raw scan-event logs turned a flat log of timestamps into a behavioral timeline, showing where operators were actually losing time between scans.

*Finding:* The weight-and-dim station carried significantly higher dwell time than any other stage, and two distinct root causes were separated within that one station.

---

## Findings

### Finding 1 — Redundant equipment scan

Every package required two scans: one to identify the package, one to trigger the specific dimensioning unit. The equipment never changed between scans within a session — operators were re-selecting the same equipment hundreds of times per shift with no session memory.

**Original flow:**
```
Pick up pallet → Scan package → Place on scale → Scan equipment → Dim triggered
```

The system's model didn't match the operator's task. This is a classic gulf of execution — the system required an action the operator's workflow didn't need.

---

### Finding 2 — Manual dimension entry for incompatible package types

Flats, envelopes, and polybags regularly triggered a "No Object Detected" error — the dimensioner was never designed to capture these formats, so the failure was structural, not intermittent. Operators had to attempt automated capture, watch it fail, then switch modes and hand-enter dimensions — approximately 30 additional seconds per package at high frequency throughout a shift. The manual measurement itself was legitimate; the forced failure the system placed in front of it was not.

This mapped to one of the weaker areas in the heuristic evaluation — error recovery — where operators had no guideline, no first-level resolution, and no way to recover independently.

---

## Design responses

### Response to Finding 1 — Activity area pre-selection

Operators scan their equipment once at the start of each session. For the remainder of the session, they scan packages only.

**New flow:**
```
[Once per session] Select activity area — scan equipment once
[Per package] Pick up pallet → Scan package only → Place on scale → Dim triggered
```

The design decision was to add session memory as a deliberate product feature rather than an assumed default. Operator task model now matches system operation model.

**Result: 50% reduction in scans per package.**

---

### Response to Finding 2 — Direct manual measurement path

For package types the dimensioner could not capture — flats, envelopes, and polybags — operators were given a direct path to manual measurement mode. Instead of being forced through automated capture, watching it fail, and only then reaching manual entry, operators now select manual measurement mode upfront and enter dimensions directly.

The design was operator-initiated rather than auto-detected. The research showed operators reliably knew what package type they were handling. The system didn't. Keeping operator judgment in the loop, rather than automating around it, was a deliberate research-informed decision. The manual work itself was legitimate; the forced failure in front of it was what the fix removed.

**Affected package types:** Flats, envelopes, polybags
**Unaffected:** Standard and medium boxes

**Result: Forced-error step eliminated for all affected package types.**

---

## Validation

Two interventions shipped sequentially — not together — so impact could be attributed to each change independently. Each validated at pilot facilities using before/after dwell time analysis before network rollout was approved.

| Metric | Before | After |
|---|---|---|
| Scans per package (standard) | 2 | 1 |
| Forced error before manual entry (flats/envelopes/polybags) | Required | Eliminated |
| Capture-error rate | 8% | 2% |
| Workflow-induced failures | 7% | <1% |
| Throughput | 266 pkg/hr baseline | ~340 pkg/hr (+28%) |
| Hardware replacement | Considered | Not required ($0 spent) |
| Deployment | — | 12+ facilities, 400+ operators |

---

## Research decisions

**Why two interventions instead of one?**
The two bottlenecks had different root causes and different solutions. Combining them into one release would have made causal attribution impossible. Sequential shipping allowed independent validation of each change.

**Why operator-initiated manual measurement mode instead of auto-detection?**
Auto-detection would introduce new failure modes and require additional engineering. The research showed operators knew the package type. Encoding operator judgment as a deliberate system affordance — rather than automating around it — was the finding, not an assumption.

**Why validate at pilot facilities before network rollout?**
Each change was proven at pilot sites using before/after analysis before it was approved for the wider network. This kept the rollout evidence-based — no change scaled until its impact was confirmed in live operation.

---

*Field research, operator feedback, and SQL analysis conducted across sortation facilities. Facility names and operator identifying information not included.*
