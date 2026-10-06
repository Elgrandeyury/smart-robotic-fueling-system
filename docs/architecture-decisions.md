# Architecture Decisions

This document records the major engineering choices behind the public case study. It focuses on system boundaries and trade-offs rather than implementation secrets.

---

## Decision 1 — Separate identification from authorization

**Choice:** Treat identity recognition and permission checks as different system responsibilities.

**Why:** Knowing who or what is present does not automatically mean an action should be allowed.

**Trade-off:** This adds another logical layer, but improves control, auditability, and future flexibility.

---

## Decision 2 — Keep local control close to the physical process

**Choice:** The embedded/control layer remains responsible for interacting with local inputs and outputs.

**Why:** Physical systems should not depend entirely on a remote cloud round-trip for immediate local actions.

**Trade-off:** Some logic exists near the edge while records and higher-level coordination can exist in the backend.

---

## Decision 3 — Use the backend for visibility and records, not as the only control authority

**Choice:** Backend/cloud services support event storage, operational visibility, integration, and records.

**Why:** Cloud services are useful for traceability and coordination but network loss should not turn a physical controller into an undefined system.

**Trade-off:** The architecture must define what remains local and what depends on connectivity.

---

## Decision 4 — Treat the dashboard as an operational view

**Choice:** The dashboard presents system state, events, records, and alerts rather than directly representing the whole system.

**Why:** A UI is only one layer. Separating it from control and backend responsibilities reduces coupling.

**Trade-off:** More interfaces exist between layers, but the system becomes easier to evolve and reason about.

---

## Decision 5 — Robotics is an extension, not the foundation

**Choice:** Robotic interaction is modeled as a future evolution of the physical process layer.

**Why:** The core engineering problem can be explored without claiming a production-ready autonomous robot.

**Trade-off:** The public case study stays accurate while leaving room for future mechanical automation.

---

## Decision 6 — Publish architecture, not a full blueprint

**Choice:** Keep the public repository high-level.

**Why:** The project involves physical automation around fueling. Detailed wiring, thresholds, control timing, fail-safe implementation, and sensitive backend details do not belong in a public portfolio unless they are safe, verified, and appropriate to disclose.

**Trade-off:** The repository shows less implementation detail, but it remains accurate and avoids overstating what can be reproduced today.

---

## Architectural quality attributes

The system concept is evaluated against these priorities:

- **Safety** — failures should not silently continue automation
- **Traceability** — significant system actions should be visible and recordable
- **Separation of concerns** — identity, authorization, control, backend, and UI remain distinct
- **Resilience** — local physical control should not rely blindly on remote availability
- **Security** — trust boundaries and permissions should be explicit
- **Evolvability** — future robotics or cloud capabilities can be added without redefining the whole system

---

## Current portfolio stance

These decisions describe the intended system architecture and engineering reasoning. They should not be interpreted as proof that every layer is currently implemented in production form.
