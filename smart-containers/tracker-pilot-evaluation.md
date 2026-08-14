# Tracker Pilot Evaluation

**Research objective:** Select a tracking solution for a reusable container fleet through evidence-based field evaluation
**Design:** Three vendors evaluated side by side, in live conditions, over a multi-week field pilot

---

## Research design

Containers were configured with one tracker from each vendor installed at the same time, on comparable routes and regions, so the comparison controlled for environmental variables. This was deliberately not a lab test — the containers ran in live customer environments under real handling and transit: loading docks, trailers, metal structures, patchy connectivity, and multi-day routes.

That mattered because the core question — would these trackers behave reliably in a logistics environment — is exactly the question vendor documentation cannot answer. Only field conditions could. A small number of units per vendor was enough to distinguish consistent signal from noise without over-committing before a decision was made.

---

## Evaluation framework

Vendors were scored on a consistent set of dimensions: tracking technology, tracking performance, battery behavior under real conditions, dashboard usability, integration fit, price and total cost of ownership, and overall reliability across the full window.

---

## What the field evaluation surfaced

**A whole approach was eliminated in week one — from field data, not specs.** One vendor relied on a location approach that produced acceptable-looking numbers on paper but fell apart in practice: in a logistics environment, its devices reported constantly regardless of whether a container had actually moved. The result was noise, not interpretable behavioral signal. No spec-sheet comparison would have caught this; watching the data come in from the field did.

**Behavioral patterns had to be built, not read off a label.** Comparing time-between-pings against distance-moved produced a four-pattern framework — at rest, in transit, moving-but-delayed, and a noise pattern — that made it possible to tell reliable devices from unreliable ones and explainable delays from genuine failures. That framework was developed through the analysis; it was the analytical backbone of the whole evaluation.

**Battery behavior traced to a usage condition, not a hardware defect.** Some devices projected far shorter battery life than others. The difference wasn't a defective unit — it traced to how the device searched for a location signal inside a metal container, where the primary signal was often blocked. Failed signal searches drained power far faster than lighter fixes. A configuration change addressed it. This was invisible in vendor specifications and only surfaced by analyzing real per-device behavior.

**Integration fit was a decisive differentiator.** The platform needed real-time event delivery at scale, not a standalone dashboard. Only one vendor could support a clean push-based integration; the others would have forced fragile workarounds regardless of how well they tracked.

---

## Decision

The selected vendor won on the three dimensions that mattered most: tracking performance in real conditions, integration fit, and total cost of ownership. The runner-up tracked adequately but couldn't support the integration architecture the platform needed. The eliminated vendor failed on field evidence — its data was noise, not signal — a conclusion available only from the field, not the spec.

---

## Implications for physical design

The pilot produced findings that fed directly back into the physical container — an instance of the telemetry-to-design feedback loop that ran throughout the program:

- **Tracker placement** — signal-blocking patterns seen in the field led to placement guidance built into production specifications
- **Orientation** — signal performance was sensitive to how the tracker sat relative to the container wall; added to installation guidance
- **Maintenance access** — battery access was designed into the container so field maintenance didn't require full disassembly

---

*Vendor names, exact figures, and device-identifying information genericized or omitted. Evaluation conducted using live field data from real deployments. Full detail available in conversation.*
