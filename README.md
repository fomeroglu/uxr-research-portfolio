# UXR Research Portfolio

Fatih Omeroglu — UX Researcher · [LinkedIn](https://www.linkedin.com/in/fomeroglu) · [fbomeroglu.com](https://fbomeroglu.com) · fatihbaha92@gmail.com

---

## About this portfolio

I research how people work within complex systems and use what I find to inform design decisions that hold up in the real world. This portfolio documents three research programs — a multi-method operational study, a physical + digital product validation program, and a 0-to-1 marketplace research program.

Each project folder contains the artifacts produced during the actual research: SQL behavioral analysis, field pilot evaluations, telemetry pattern analysis, integration validation documents, and API contracts. These are not case-study writeups — every artifact was produced during live research, for products deployed to real users.

---

## Research programs

### [Sortation Platform](./sortation-platform/)
**Multi-method research program — 28% throughput improvement across 400+ operators**

Quarterly operator surveys, heuristic evaluation, contextual field inquiry, and behavioral log analysis combined to locate and validate the root cause of a network-wide throughput constraint. What looked like a hardware problem was a workflow problem — the fix improved throughput 28% with zero hardware spend. Each method informed the next.

**Artifacts:** Workflow analysis · SQL queries (6 BigQuery queries, window functions) · Before/after flow diagrams · Error validation · Results

---

### [Smart Containers](./smart-containers/)
**Vendor evaluation, telemetry analysis, and iterative field validation — 1,000+ units deployed**

Structured 3-vendor tracker evaluation using live field telemetry. Four behavioral patterns identified from raw ping data through original analysis. Integration validated through three correction rounds before go-live. Physical design iterated across staged production batches, each triggered by field failure data.

**Artifacts:** Tracker pilot evaluation · Telemetry pattern analysis · Webhook integration story · Container design iteration · Case study

---

### [Exchange Marketplace](./exchange-marketplace/)
**0-to-1 research program — discovery through field validation**

Generative discovery interviews, competitive analysis, journey mapping, concept testing, and RITE evaluation. Research overturned a planned supplier-publishing feature before engineering started, and drew the line on MVP scope. API contracts produced before any engineering build began.

**Artifacts:** API contract · OpenAPI spec · Entity-relationship model · ERD diagram

---

## Research methods demonstrated in this portfolio

| Method | Where |
|---|---|
| Behavioral log analysis (SQL) | Sortation Platform — 6 BigQuery queries, LAG window functions, before/after validation |
| Heuristic evaluation | Sortation Platform — 14 principles scored, field observation |
| Survey design + Kano analysis | Sortation Platform — quarterly program, 150–200 responses per cycle |
| Vendor evaluation | Smart Containers — 3-vendor structured pilot, 29 days live field data |
| Telemetry pattern analysis | Smart Containers — 4 behavioral patterns identified from raw ping data |
| Integration validation | Smart Containers — 3 correction rounds, timestamp mismatch caught pre-launch |
| Iterative field design | Smart Containers — staged production batches, each triggered by field data |
| Generative discovery (JTBD) | Exchange Marketplace — 10 moderated sessions, both sides of market |
| Journey mapping | Exchange Marketplace — current-state workflow, custody handshake points |
| Concept testing | Exchange Marketplace — 3 studies, 20 unique participants, fresh per study |
| RITE evaluation | Exchange Marketplace — 10 sessions, revise/hold classification |
| API contract design | Exchange Marketplace — contract-first, geofence validation, idempotency patterns |

---

## Background

- **Doctor of Engineering** — Human-Computer Interaction & Industrial Engineering, Lamar University
- **5+ peer-reviewed publications** — cognitive performance, HCI, UI/UX effects (*Physiology & Behavior 2025*, *HCII 2022–2023*)
- Previously: FedEx Operations Research, Lactalis Project Engineering
