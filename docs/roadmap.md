# Implementation Roadmap

This roadmap describes a realistic path for evolving the case study into a new demonstrable prototype without pretending the original build artifacts still exist.

---

## Stage 1 — Safe bench prototype

Goal: rebuild the architecture using non-hazardous components and simulated fueling behavior.

Possible public evidence:

- identification event
- authorization decision
- sensor input simulation
- actuator or indicator response
- local event logging
- simple fault/stop state

The physical fueling process should remain simulated at this stage.

---

## Stage 2 — Connected prototype

Goal: connect the local controller to a backend service.

Public evidence could include:

- device event submission
- transaction/event records
- device identity
- authenticated communication
- dashboard status
- communication failure handling

---

## Stage 3 — Operational visibility

Goal: demonstrate the software side as a coherent operational system.

Potential features:

- recent events
- authorization outcomes
- device status
- fault/alert records
- basic audit history
- operator-facing dashboard

---

## Stage 4 — Security and resilience testing

Goal: test selected failure and trust-boundary scenarios in a safe environment.

Examples:

- invalid identity
- denied authorization
- backend unavailable
- device reconnect
- malformed input handling
- lost network connectivity

Only safe, non-sensitive test details should be published.

---

## Stage 5 — Robotic interaction research

Goal: explore whether robotic hardware can safely reduce manual physical interaction.

This would require separate mechanical, sensing, safety, and control validation. Until supported by a real prototype, robotics remains a future engineering direction rather than a completed implementation claim.

---

## Definition of done for a future public prototype

A future prototype should only be marked complete when there is reproducible evidence such as:

- current source code
- architecture documentation
- safe hardware photos
- test outputs
- dashboard screenshots
- failure/recovery demonstrations
- clear distinction between simulated and physical behavior

---

## Current status

The current repository is a **completed engineering case study**. Rebuilding a new prototype is optional future work and is not required for the portfolio documentation to remain accurate.
