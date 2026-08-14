# Tracker integration — catching problems before they reached production

**Context:** After the tracker vendor was selected on field evidence, the integration work began. This is a short account of two implementation problems caught during integration — before either could become a silent data-quality issue in production.

---

## The requirement

The platform needed tracker location and telemetry events in real time and at scale. The vendor's default was a polling model — the platform would repeatedly ask for new data on a timer. That is fragile as a fleet grows: it adds latency, forces the platform to manage state between pulls, and runs constantly even when nothing has happened.

The requirement set to the vendor was a push-based integration instead: the vendor's system delivers events to the platform as they occur, so the platform simply has to be ready to receive. This scales cleanly — adding more containers doesn't increase the polling burden.

---

## Problem 1 — the wrong delivery pattern

The vendor's first implementation used a persistent-connection approach that carried real infrastructure cost and operational complexity for what was, in effect, a one-way event stream. It works, but it was the wrong tool for the job — over-engineered for simple event notification.

This was flagged immediately and the vendor moved to the simpler, standard push pattern. Turnaround was fast.

---

## Problem 2 — a timestamp mismatch that would have created phantom duplicates

Once data was flowing, a subtle inconsistency surfaced: the live event feed and the vendor's backup data source represented time differently. On its own that looks harmless — but if the live feed ever went down and the platform had to backfill from the backup source, the mismatch would have caused existing records to be read as brand-new duplicates.

Two options: compensate for the difference in downstream logic, or fix it at the source. Fixing it at the source was cleaner — data consistency where the data originates beats patching around it everywhere it's consumed. The vendor aligned the formats within days.

---

## Why this is a research story, not just an integration one

Both problems are the kind that surface as silent data-quality issues weeks or months after go-live — the moment when a researcher's behavioral analysis quietly starts resting on bad data. Catching them during integration protected the integrity of every downstream analysis: the behavioral patterns, the cycle counts, the dwell-time findings all depend on the event data being clean and trustworthy. The judgment calls here — push over pull, simple over complex, fix-at-source over patch-downstream — were about protecting the evidence base before it was ever built on.

---

*All identifying information has been genericized. Integration was conducted with a real IoT tracking vendor as part of a production deployment. Full technical detail available in conversation.*
