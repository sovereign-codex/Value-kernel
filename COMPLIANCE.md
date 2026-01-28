# VALUE KERNEL COMPLIANCE v1.0.0

This document defines what it means for a system to claim
**compliance with Value Kernel v1.0.0**.

**Status:** Binding  
**Scope:** Any system, component, or service asserting Value Kernel compliance

---

## 1. Compliance Is Binary (Binding)

A system is either compliant with Value Kernel v1.0.0 or it is not.

There is no partial, conditional, or aspirational compliance.

Any claim of “mostly,” “functionally,” or “best-effort” compliance
is invalid.

---

## 2. Minimum Compliance Requirements (Binding)

To claim compliance, a system **MUST** satisfy **all** of the following:

### VKC-1: Kernel Version Pinning
- The system explicitly references **Value Kernel v1.0.0**
- Floating or implicit version references are prohibited

### VKC-2: Mandatory Evaluation
- All consequential actions are evaluated against the kernel
- Evaluation occurs at execution boundaries, not only at planning time

### VKC-3: Terminal State Enforcement
- The system enforces the terminal states defined in `CONTRACT.md`
- Outcomes (`ALLOW`, `DENY`, `HALT`, `PAUSE`, `ESCALATE`) are treated as final

### VKC-4: Fail-Closed Defaults
- Under uncertainty, the system defaults to non-action
- No speculative or assumed-safe execution is permitted

### VKC-5: Non-Bypassability
- No execution path bypasses kernel evaluation
- No privileged override paths exist

---

## 3. Auditability Requirements (Binding)

### VKC-6: Decision Records
For any non-trivial action, the system **MUST** be able to produce
a decision record containing:

- kernel version evaluated
- action requested
- terminal decision state
- constraint(s) implicated (by identifier)
- timestamp
- system identifier

Failure to produce such a record constitutes non-compliance.

---

## 4. Prohibited Compliance Claims (Binding)

A system **MUST NOT** claim Value Kernel compliance if it:

- disables checks in development or testing modes
- conditionally applies constraints
- allows human operators to override runtime decisions
- relies on undocumented heuristics in place of kernel evaluation
- executes actions when kernel evaluation is unavailable

---

## 5. Loss of Compliance (Binding)

A system immediately loses compliance if:

- kernel evaluation is bypassed
- terminal states are ignored or softened
- constraints are modified in place
- unpinned kernel versions are substituted
- enforcement is suspended for convenience or performance

Loss of compliance **MUST** be treated as a safety incident.

---

## Appendix A — Informative Notes (Non-Authoritative)

- Compliance is not a moral judgment; it is a technical property.
- A system may be useful without being compliant.
- Claiming compliance implies acceptance of audit and scrutiny.

---

## Appendix B — Compliance Signals (Non-Authoritative)

Common indicators of compliance include:
- visible kernel references in configuration
- test suites derived from `decision_tests.json`
- documented escalation pathways
- reproducible decision traces

These signals do not replace the binding requirements above.
