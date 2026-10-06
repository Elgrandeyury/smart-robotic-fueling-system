# Security and Safety Design Principles

## Purpose

This document captures the high-level security and safety principles for the Smart / Robotic Fueling System case study.

It intentionally avoids publishing operational control parameters, detailed hardware protections, exact sensor thresholds, or other implementation details that could be unsafe or commercially sensitive.

---

## Security principles

### 1. Identity must not equal authorization

Recognizing a vehicle or user is only the first step. The system should treat identification and authorization as separate decisions.

An identifier such as RFID can provide identity context, while a separate authorization layer determines whether the requested action is permitted.

### 2. Least privilege

Each software, device, and service component should receive only the access it requires.

Examples at the architectural level include:

- devices should not receive broad backend permissions
- dashboard users should see only the data relevant to their role
- backend services should use narrowly scoped credentials
- administrative actions should be separated from normal operational actions

### 3. Protect operational data

Operational records may include vehicle, user, authorization, and fueling event information. That data should be protected in transit and at rest where appropriate.

Public repositories must never contain real credentials, secrets, or production identifiers.

### 4. Audit important events

The system should make significant actions traceable, including:

- identity presented
- authorization decision
- process start and stop
- faults or interruptions
- operator actions
- backend or device communication failures

### 5. Trust boundaries matter

The architecture crosses several boundaries:

```text
Vehicle / User
      ↓
Identification Device
      ↓
Embedded Controller
      ↓
Network / Backend
      ↓
Dashboard / Operator
```

Each boundary should be treated as a point where input validation, authentication, authorization, or integrity controls may be required.

---

## Safety principles

### 1. Safe failure is more important than uninterrupted automation

If the system enters an unknown or unsafe state, the preferred behavior should be to stop or prevent the automated action rather than continue blindly.

### 2. Automation must remain bounded

Software should not be treated as the only safety mechanism for a physical process. Mechanical, electrical, operational, and procedural controls may also be required in a real implementation.

### 3. Faults must be observable

A system that fails silently is difficult to operate safely. Important faults should produce visible state changes or alerts for the relevant operator or service.

### 4. Manual intervention must remain possible

A real-world automated physical system should include a documented path for safe human intervention and recovery.

### 5. Production deployment requires specialist validation

This repository is a portfolio case study. It is not a production fuel-handling design and should not be interpreted as certification, safety approval, or deployment guidance.

---

## Threat areas considered at a high level

| Area | Example concern |
|---|---|
| Identity | cloned, invalid, or untrusted identifier |
| Authorization | permitted identity attempting an unauthorized action |
| Device control | malformed or unexpected input reaching the controller |
| Network | loss of connectivity, spoofed traffic, or unauthorized access |
| Backend | exposed credentials, weak access control, incomplete audit trail |
| Dashboard | excessive privileges or sensitive information exposure |
| Physical process | sensor faults, actuator faults, or unsafe operating state |

---

## Public documentation boundary

This document intentionally does not describe:

- exact fail-safe logic
- hardware interlock implementation
- operational sensor thresholds
- security credentials or keys
- production network topology
- real-world fueling control procedures

The objective is to demonstrate security and safety thinking without publishing an unsafe implementation blueprint.
