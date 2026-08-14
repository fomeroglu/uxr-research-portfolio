# Smart Containers — Field Research on a Physical Product in Live Operation

**Scope:** Reusable, collapsible containers deployed across a national logistics network
**Outcome:** Field observation reframed an early deployment failure from a materials problem into a usage problem, producing a severity-ranked failure taxonomy that turned directly into a prioritized design roadmap

---

## Research question

The container was engineered to a clear brief and, on paper, should have held up in the field. Early in deployment, a significant share of the first fleet came back damaged. The team was under pressure to commit tooling and capital to a full redesign, and the instinct in the room was that the product simply needed more material — a stronger, heavier build.

Before the company paid for that, the research had to answer a question the spec sheets could not: was this a materials problem, or a problem in how the product was actually being used in the field?

---

## Method — field observation

The answer could only come from where the product lived. Payload calculations and design specifications had already been done; they said the container should survive. It did not. So the research went to the operation itself — observing how the containers were handled between hubs, on docks, and in trailers, and connecting the physical evidence on the returning fleet back to the behavior that produced it.

Rather than accept a single verdict of "they broke," I treated the returning fleet as a dataset. Each unit was inspected directly and every failure was classified against a consistent framework:

- **What failed** — the specific part of the product involved
- **Why it failed** — the physical mechanism, traced back to how the unit was actually handled
- **How much it mattered** — a severity rating, so fixes could be prioritized by impact rather than treated as one undifferentiated pile

This turned scattered field damage into a legible, decision-ready taxonomy that both engineering and leadership could act on.

---

## Key finding — designed use versus real use

The failures were not random material weakness. They clustered, and the cluster pointed at handling. The container had been engineered for its payload, but the real load was operational — the product was being handled far more roughly than any specification had assumed.

The decisive insight came from the field, not the spec: to fill trailers to capacity and finish the shift, operators were handling the containers in ways the design never anticipated. Operators optimize to get the job done, not to preserve the equipment — so the product had to be designed to survive rough real-world handling, rather than assume care. No payload calculation would ever have surfaced that. You had to observe the operation to see it.

---

## From research into design

Because every failure was tied to an observed usage mechanism, the design response could be targeted rather than blanket. Each finding mapped to a specific, prioritized design requirement — letting engineering reinforce the few things that actually failed instead of over-building everything, which is the difference between a redesign that hits its constraints and one that blows past them.

The field observation also drove direct usability improvements beyond durability — a more reliable retention system, better on-container label handling to remove a refurbishment pain point, and integrated tracker mounting to simplify installation. These came straight out of watching the product in use, not from a requirements document.

---

## Secondary research thread — tracker and telemetry

The container is also the physical mount for an IoT tracker, so a parallel research effort supported the digital layer.

**Tracker vendor evaluation.** A structured field evaluation of three tracking vendors on comparable routes over a multi-week live pilot, scored across a consistent set of dimensions. Selection was made on field evidence rather than vendor claims.

**Telemetry pattern analysis.** Four distinct movement-behavior patterns were derived from raw ping data through original analysis — not taken from vendor documentation — and used to shape tracker configuration and how container cycles were counted at scale.

---

## The design iteration arc

A deliberately staged approach: a controlled field pilot first, then validated refurbishment of the damaged fleet, then progressively larger production batches — each one triggered by field evidence and validated in live conditions before the next was committed. Starting small kept the cost of learning low, and every change was checked against real use before it scaled to 1,000+ deployed units.

---

## Artifacts in this folder

| File | What it is |
|---|---|
| `container-design-iteration.md` | The design arc — how field evidence drove each production stage |
| `tracker-pilot-evaluation.md` | Vendor evaluation — structured field pilot across three vendors |
| `telemetry-analysis.md` | Behavioral pattern analysis from raw ping data |
| `webhook-integration-story.md` | Integration validation before go-live |

---

*Vendor names, carrier names, facility locations, and hardware specifications have been genericized or excluded. Full detail available in conversation.*
