# Sortation Platform — Workflow Usability Research

**Scope:** Multi-facility parcel sortation platform, 400+ operators across 12+ facilities
**Outcome:** 28% throughput improvement at the primary bottleneck stage, validated before network-wide rollout

---

## Research question

The weight and dim station was reported as the network's primary bottleneck, and the team was weighing a costly hardware upgrade in response. But the root cause was unknown. Competing hypotheses included system latency, unclear UI feedback, and workflow complexity. Without isolating the real constraint first, any design response — or a capital purchase — risked targeting the wrong layer.

The question the research had to answer was direct: was the equipment genuinely insufficient and in need of replacement, or was something in the workflow driving the errors and slowdowns?

---

## Research methods

Three separate research efforts touched this product. Two were ongoing programs that run independent of any single investigation; the third was the focused study that produced the findings below.

**Ongoing product research (standalone programs)**
A recurring operator survey program benchmarks satisfaction and surfaces priorities across the platform, combining Likert ratings, open-ended pain-point questions, and Kano classification. Separately, a periodic heuristic evaluation assesses the sortation system against 14 usability principles. These are continuous learning programs — they inform the roadmap broadly rather than feeding one investigation.

**The bottleneck investigation (this study)**
The weight-and-dim study itself combined contextual field inquiry with behavioral analysis of scan-event logs. Observation across shifts showed how operators actually worked the station — including the informal workarounds they had built around failures that were never formally documented. Behavioral analysis of the scan data then isolated where packages were stalling and separated two distinct root causes within the one station. Field observation showed the "why"; the behavioral data confirmed the "how often."

**Validation**
The two fixes were shipped sequentially — one per root cause — so the impact of each could be attributed independently, and each was validated at pilot facilities before network rollout.

---

## Key findings

**Finding 1:** Every package required two scans — one to identify the package, one to re-confirm the same equipment. No session memory existed. Operators were re-selecting the same equipment hundreds of times per shift. The system's model didn't match the operator's task.

**Finding 2:** Flats, envelopes, and polybags could not be captured by the dimensioner — the sensor returned a "No Object Detected" error every time. Operators still had to attempt automated capture first and only reach manual measurement after the error, adding roughly 30 seconds per package at high frequency. The manual work itself was legitimate; the forced failure in front of it was not. The fix gave these package types a direct path to manual measurement mode.

---

## Outcome

| Metric | Before | After |
|---|---|---|
| Scans per package | 2 | 1 (−50%) |
| Capture-error rate | 8% | 2% |
| Workflow-induced failures | 7% | <1% |
| Throughput | 266 pkg/hr baseline | ~340 pkg/hr (+28%) |
| Hardware replacement | Considered | Not required ($0 spent) |
| Deployment | — | 12+ facilities, 400+ operators |

---

## Artifacts in this folder

| File | What it is |
|---|---|
| `sortation-workflow-analysis.md` | Full written research narrative — discovery, findings, design responses, decisions |
| `sortation-queries.sql` | 6 BigQuery SQL queries — bottleneck identification and before/after validation |
| `before-flow.png` | Original 2-scan workflow — root cause visualized |
| `scan-flow-before-after.png` | Scan reduction — before and after the activity-area pre-selection fix |
| `manual-mode-flow.png` | Unsupported package flow — before (forced error) and after (direct manual measurement path) |
| `error-validation.png` | Capture-error breakdown — 7 of every 8 errors traced to unsupported formats |
| `throughput-results.png` | Before/after throughput and the full results table |

---

*Field research, operator feedback, and SQL analysis conducted across sortation facilities. Facility names and operator identifying information not included.*
