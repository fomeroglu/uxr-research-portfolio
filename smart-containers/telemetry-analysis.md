# Telemetry analysis — container behavioral patterns

**Objective:** Understand how containers actually move through the network using tracker ping data
**Method:** Behavioral analysis of ping data across field-deployed containers

---

## Why telemetry analysis mattered

Deploying trackers on containers generates raw ping data — timestamps, coordinates, battery levels, location accuracy. Raw pings alone don't tell you what a container is doing. The work was about turning raw location events into meaningful behavioral signal:

- Is this container in transit or sitting idle?
- How long has it been at a facility?
- Is it making full cycles or getting stuck somewhere in the network?
- Is the tracker behaving as expected, or showing anomalies?

None of these could be read off the raw data directly — they required defining what "transit," "stopped," and "cycle" actually mean in the context of logistics container movement.

---

## Behavioral pattern identification

By comparing time-since-last-ping against distance-moved between consecutive pings, four distinct behavioral patterns emerged from the data:

- **Stationary, infrequent pings** — the container is at rest, reporting on its normal heartbeat cycle. Expected.
- **Traveling, frequent pings** — the container is in transit and motion detection has correctly increased reporting frequency. Expected.
- **Traveling, delayed pings** — the container is moving but reporting is lagging, most often due to connectivity limits (signal blocked by the metal structure, or a low-connectivity zone). Explainable and addressable through a configuration change.
- **Stationary, frequent pings** — the device is pinging often despite not moving, a noise pattern most common in one class of device. Not expected — it wastes battery and adds noise to the location data.

Distinguishing these four patterns was the analytical foundation for everything downstream: it separated real movement from noise, and explainable delays from genuine problems.

---

## Cycle determination

Understanding container utilization required knowing how many complete cycles each container had made — a cycle being a round trip from origin facility to customer and back.

The challenge: raw ping data is just a series of location points. Determining where one trip ends and another begins requires defining what counts as a "stop" — and in a logistics context, a stop is a sustained presence at a location, not a single ping.

The stop-detection approach was tuned against both synthetic trajectories with known stops and real container trajectories with manually-labeled stops, balancing sensitivity (catching real stops) against specificity (not inventing stops from brief pauses). The method handled several real-world cycle shapes — direct round trips, trips routed through an intermediate hub, partial and interrupted trips, and incomplete one-way trips — and was applied across the deployed fleet to generate cycle counts at scale.

---

## Key findings

- **Reliable reporting.** The selected vendor's containers reported consistently across the evaluation window, which is what made the behavioral analysis trustworthy in the first place.
- **Battery is driven by signal behavior.** Power draw was dominated by how the device searched for location — failed satellite scans cost far more than lighter location fixes. This directly informed a configuration change that improved both battery life and location reliability.
- **Location anomalies traced to a fallback data source.** A rare spurious location was traced to a cellular fallback returning bad data when the primary signal was unavailable — caught in analysis and flagged to the vendor.
- **Dwell time varied meaningfully by facility.** Some containers turned quickly while others sat, which became a direct input into operational conversations about container return velocity.

---

## From telemetry to product decisions

The analysis shaped three decisions:

1. **Default tracker configuration** — changed after the signal-behavior patterns were identified, improving both location reliability and battery performance.
2. **Physical design** — tracker placement guidance for production batches was informed by the signal-blocking patterns seen in the data.
3. **Cycle-count reporting** — the stop-detection method became the foundation for a container-utilization feature, giving customers visibility into how many cycles their containers had completed and where they spent the most time.

---

*Analysis conducted on live field data from deployed containers. Facility names, carrier partners, device identifiers, and exact figures have been genericized or omitted. Full detail available in conversation.*
