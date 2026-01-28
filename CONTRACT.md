# VALUE KERNEL CONTRACT v1.0.0

This contract defines how downstream systems **MUST** enforce
the constraints specified in `VALUE_KERNEL.md`.

**Status:** Binding  
**Scope:** All execution-capable components claiming Value Kernel compliance

---

## 1. Purpose (Normative)

This contract exists to:
- translate constitutional constraints into enforceable outcomes
- standardize how decisions terminate
- prevent interpretation drift at runtime
- ensure fail-closed behavior under uncertainty

This document does **not** define ethical principles.
Those are defined exclusively in `VALUE_KERNEL.md`.

---

## 2. Mandatory Decision Evaluation (Binding)

### VC-1: Pre-Action Evaluation
All actions **MUST** be evaluated against the Value Kernel
**before** execution.

This includes:
- tool calls
- external requests
- publishing content
- modifying state
- initiating autonomous behavior

Evaluation **MUST** occur at the execution boundary, not only at planning time.

---

## 3. Terminal Decision States (Binding)

Every evaluated action **MUST** resolve to exactly one of the following
terminal states:

### 3.1 ALLOW
The action does not violate any kernel constraint
and may proceed.

### 3.2 DENY
The action violates one or more kernel constraints
and **MUST NOT** proceed.

### 3.3 HALT
Execution is stopped due to detected risk, conflict,
or invalid system state.

### 3.4 PAUSE
Execution is temporarily suspended pending:
- additional input
- clarification
- confirmation
- or system readiness

### 3.5 ESCALATE
The action cannot be safely evaluated or executed
without human or higher-level review.

No other terminal states are permitted.

---

## 4. Fail-Closed Enforcement (Binding)

### VC-2: Default to Non-Action
If evaluation cannot be completed deterministically,
the system **MUST** resolve to `DENY`, `HALT`, or `ESCALATE`.

### VC-3: No Silent Degradation
Systems **MUST NOT**:
- approximate decisions
- substitute weaker checks
- “best guess” outcomes
- retry with relaxed constraints

Uncertainty is not permission.

---

## 5. Decision Record Requirements (Binding)

For any action that does not trivially `ALLOW`,
systems **MUST** produce a decision record containing:

- evaluated kernel version
- requested action summary
- terminal decision state
- constraint(s) implicated (by ID)
- timestamp
- system identifier

Records **MUST** be:
- machine-readable
- minimally sufficient
- suitable for audit

---

## 6. Enforcement Obligations (Binding)

### VC-4: Non-Bypassability
No execution path **MAY** bypass kernel evaluation.

### VC-5: No Post-Hoc Justification
Once a decision resolves to `DENY`, `HALT`, or `ESCALATE`,
systems **MUST NOT** attempt to rationalize or override the outcome.

### VC-6: Human Override Prohibition
Human operators **MUST NOT** directly override kernel decisions
at runtime.

Overrides require:
- governance change
- new kernel version
- redeployment

---

## 7. Integration with Downstream Systems (Binding)

### VC-7: Execution Engines
Execution engines (e.g., AVOT-engine-core):
- MUST treat terminal states as final
- MUST enforce boundary checks
- MUST expose escalation hooks

### VC-8: Interpretation Layers
Interpretive layers (e.g., TYME):
- MAY explain decisions
- MUST NOT authorize actions
- MUST NOT soften outcomes

---

## 8. Version Discipline (Binding)

### VC-9: Version Pinning
Systems **MUST** explicitly pin the kernel version used
for evaluation (e.g., `v1.0.0`).

### VC-10: Incompatibility Handling
If a system encounters an unsupported or unknown kernel version,
it **MUST** resolve to `HALT` or `ESCALATE`.

---

## Appendix A — Informative Notes (Non-Authoritative)

- `DENY` is a successful outcome, not a failure.
- `ESCALATE` preserves safety while enabling governance.
- A system that cannot explain *why* it denied an action
  is likely missing required traces.

---

## Appendix B — Implementation Guidance (Non-Authoritative)

Typical enforcement patterns include:
- policy engines
- middleware guards
- pre-flight checks
- commit hooks
- tool-call interceptors

The specific mechanism is implementation-defined,
but the outcomes are not.
