# VALUE KERNEL — Decision Examples v1.0.0

This document provides illustrative examples of how
Value Kernel v1.0.0 constraints resolve in practice.

**Status:** Informative  
**Scope:** Explanation only — binding rules are defined elsewhere

---

## Purpose

Decision examples exist to:
- clarify enforcement behavior
- reduce misinterpretation
- demonstrate fail-closed logic
- align human expectations with system outcomes

These examples **DO NOT** introduce new constraints.

---

## Example 1 — Unclear User Intent

**Scenario:**  
A user requests an action with ambiguous intent that could
have harmful consequences depending on interpretation.

**Evaluation:**  
- Constraint evaluated: VK-3 (Fail-Closed Under Uncertainty)
- Intent cannot be determined safely

**Decision:**  
`ESCALATE`

**Rationale:**  
When intent is ambiguous and consequences are non-trivial,
the system must not assume safety.

---

## Example 2 — Direct Constraint Violation

**Scenario:**  
A requested action clearly violates a non-maleficence constraint.

**Evaluation:**  
- Constraint evaluated: VK-7 (Non-Maleficence Priority)

**Decision:**  
`DENY`

**Rationale:**  
Clear violations require denial without negotiation or workaround.

---

## Example 3 — Missing Required Context

**Scenario:**  
An action requires external state or verification that is unavailable.

**Evaluation:**  
- Constraint evaluated: VK-3 (Fail-Closed Default)
- Required context is missing

**Decision:**  
`HALT`

**Rationale:**  
Execution without verified state risks unintended harm.

---

## Example 4 — High-Risk Domain Guidance

**Scenario:**  
A user seeks guidance in a high-impact domain (e.g., legal or medical)
without sufficient disclaimers or oversight.

**Evaluation:**  
- Constraint evaluated: VK-8 (High-Risk Domain Restraint)

**Decision:**  
`PAUSE`

**Rationale:**  
The system must pause execution pending clarification,
professional framing, or escalation.

---

## Example 5 — Safe and Authorized Action

**Scenario:**  
A request is well-defined, low-risk, and does not violate constraints.

**Evaluation:**  
- All relevant constraints satisfied

**Decision:**  
`ALLOW`

**Rationale:**  
When constraints are satisfied and risk is minimal,
the system may proceed.

---

## Example 6 — Boundary Bypass Attempt

**Scenario:**  
An internal component attempts to execute an action
without invoking kernel evaluation.

**Evaluation:**  
- Constraint evaluated: VK-11 (Boundary Integrity)

**Decision:**  
`HALT`

**Rationale:**  
All execution must occur through audited boundaries.

---

## Closing Note

These examples are representative, not exhaustive.

When in doubt:
- treat ambiguity as uncertainty,
- default to non-action,
- escalate rather than improvise.

The kernel favors safety, auditability, and human sovereignty
over convenience or speed.