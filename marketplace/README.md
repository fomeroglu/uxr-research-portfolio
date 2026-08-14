# Marketplace — 0-to-1 Research for a Two-Sided Product

**Scope:** A two-sided marketplace for exchanging less-than-truckload and truckload freight capacity between buyers and suppliers
**Outcome:** Research shaped the product at every stage — it defined what was built, who it was for, and what was deliberately not built. Now in closed beta.

---

## Research question

The opportunity was a mismatch: suppliers ran established lanes with unused backhaul capacity sitting idle, while buyers struggled to find reliable, consistently priced capacity. The two sides had complementary needs and no good way to find each other.

But a two-sided marketplace is risky to build blind. Before committing engineering resources, the research had to answer three things: what were both sides actually trying to accomplish, which product concepts genuinely fit their work, and where was the line between what to build and what to leave out.

---

## Research program

Research ran at every stage, each phase feeding the next.

**Jobs-to-be-done discovery**
10 moderated sessions — 5 buyers and 5 suppliers — to understand both sides of the marketplace: their day-to-day jobs, existing tools, current workflow, pain points, decision factors, and desired future state. A competitive analysis ran in parallel across existing capacity services. Output was a two-sided opportunity map. Participants were recruited externally against the buyer and supplier personas — none were existing customers, so no prior product exposure could bias the findings.

**Bullseye customer definition (2 rounds)**
Two rounds of customer-definition work to sharpen who the earliest, best-fit adopters were — narrowing from a broad two-sided market to the specific buyer profile most likely to adopt first.

**Concept testing (3 studies, 20 unique participants)**
Three concept studies turned the value propositions into testable concepts, each with fresh, role-matched participants:
- **Study 1 (5 buyers):** fixed gateway-to-gateway lanes, using low-fidelity prototypes and storyboards
- **Study 2 (10: 5 buyers + 5 suppliers):** the recurring-capacity model — pricing, commitment, and cancellation terms
- **Study 3 (5 supplier/ops):** capacity participation and QR-based handoff execution

These were concept sessions, not task-based usability tests. The question was never "do you like this" — it was "does this make sense for how you actually operate, and would it change what you do."

**RITE evaluation (10 sessions)**
Once functional prototypes existed, 10 moderated RITE sessions — 5 buyer-side, 5 supplier-side — refined the critical workflows. A clear interaction failure was fixed before the next session; anything structural, ambiguous, or preference-based was held for more evidence. The rule ran in both directions, which prevented overfitting to any single participant.

---

## Key findings

**Finding 1 — Gateway-to-gateway fit both sides, from opposite directions.** Buyers valued fixed, predictable lanes; separately, suppliers confirmed those routes already matched how they operated. Two sides of the market, interviewed independently, converged on the same model.

**Finding 2 — Suppliers would not manage a publishing interface.** This overturned a planned product model. Suppliers were already integrated with their own TMS platforms and would not maintain capacity in a second system. The decision became: supply integrates via API, no dedicated supplier UI. This changed the architecture — the marketplace was two-sided, but the experience did not need to be symmetrical.

**Finding 3 — "Subscription" was the wrong frame.** Buyers thought in terms of recurring relationships and individual shipments, not subscriptions. The terminology and pricing structure did not match freight purchasing mental models, so it was reframed as capacity reservation.

---

## How research shaped what was built

| Decision | What the research showed |
|---|---|
| Supply integrates via API, no supplier UI | Suppliers already maintain lanes in their TMS; a second interface would duplicate work |
| Build the buyer-facing experience as the product | Buyers needed a dedicated space to find, compare, reserve, and manage capacity |
| Gateway-to-gateway as the core lane model | Confirmed by both sides independently |
| Subscription reframed as capacity reservation | Matched how buyers actually think about freight purchasing |
| Target sharpened to SMB buyers + local transport managers | Enterprise found the flow tedious for their volume; SMB adopted most readily |
| Deferred: supplier lane-building UI, enterprise bulk booking | Research drew the MVP line — not product instinct |

The principle behind the scope: the smallest connected experience that let supply enter, buyers reserve it, and status move through real operational handoffs.

---

## Artifacts in this folder

| File | What it is |
|---|---|
| `API_Contract_v1.md` | Contract-first API design — philosophy, surface overview, and the key design tradeoffs |
| `exchange_marketplace_erd.dbml` | Entity-relationship model for the marketplace domain |
| `erd_diagram.mmd` | Rendered ERD diagram (Mermaid) |

---

*Discovery, concept testing, and RITE evaluation conducted for a live 0-to-1 product. Company names, participant identities, and closed-beta specifics are not included.*
