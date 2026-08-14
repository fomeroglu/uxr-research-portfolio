# Logistics Platform — API Contract (Overview)

A capability overview of a contract-first API designed for the marketplace platform. This is an abridged version — it shows the design philosophy, the shape of the surface, and the reasoning behind the key decisions, without the full request/response schemas.

---

## Design Philosophy

This API is **contract-first** — the spec was written before any implementation. Every endpoint is designed from the consumer's perspective: what does the field operator app need? What does the dashboard need? What does the payment system need?

Three design principles govern every endpoint:

**1. Immutability over updates**
Scan events are never updated or deleted. The append-only event log is the source of truth. Projections (like unit status) are derived from events — never directly mutated via API.

**2. Hard-fail over silent degradation**
If a scan event's GPS coordinates fall outside the zone geofence, the request is rejected rather than accepted and quietly corrected later. Trust is built on verified physical presence, not assumed proximity.

**3. Idempotency by default**
Every write endpoint is idempotent and retry-safe by design. An operator who loses connectivity mid-scan and retries will never create duplicate records.

---

## The surface, at a glance

The contract covers three consumer-facing needs:

- **Recording physical events** — the field operator app submits scan events as containers move through the network. Each event passes a sequential validation pipeline before it is written; a failure at any step rejects the whole request, so nothing is partially recorded.
- **Discovering available capacity** — buyers query available capacity tokens, filtered to what is relevant to them, without exposing confidential supplier detail.
- **Checking payment eligibility** — the payment system asks whether a given handling unit is eligible, and eligibility is computed live from the event log rather than read from a stored flag.

---

## Design Decisions & Tradeoffs

The decisions below are the parts of the contract most worth understanding — each was a deliberate tradeoff, not a default.

**Why is eligibility computed, not stored?**
Storing an `eligible: true/false` flag creates two sources of truth. If a scan event is added retroactively, a stored flag goes stale. Computing from the event log means eligibility is always consistent with the actual record — no reconciliation job needed. *Tradeoff:* slightly more expensive to compute, mitigated by indexing.

**Why is a supplier's address hidden until a transaction is confirmed?**
Supplier confidentiality is a core marketplace trust requirement — suppliers will not list capacity if buyers can extract location data without completing a transaction. The blind-board design was the minimum viable trust model for supplier participation. *Tradeoff:* reduces search precision, mitigated by area-level search that is precise enough for operational planning.

**Why is geofence validation a hard fail?**
A warning model pushes trust enforcement to the UI layer, where any client with API access can bypass it. A hard fail at the API layer means an accepted scan event is guaranteed to represent verified physical presence, regardless of which client submitted it. *Tradeoff:* legitimate GPS drift can generate false rejections, mitigated by a configurable geofence radius per zone.

**Why is the event-type list a reference table, not a database enum?**
Adding a new event type to a database enum requires a schema migration — downtime and deployment risk. A reference table requires only a new row, with zero downtime and no engineering involvement to extend.

---

*This is an abridged reference overview demonstrating research-informed API design applied to a B2B logistics platform. Full schemas are intentionally omitted. No proprietary data or company-specific information is included.*
