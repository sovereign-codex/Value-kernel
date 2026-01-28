# VALUE KERNEL GOVERNANCE v1.0.0

This document defines the governance, immutability, and change-control
process for the Value Kernel.

**Status:** Binding  
**Scope:** All versions of the Value Kernel and all systems that reference them

---

## 1. Immutability (Binding)

### VKG-1: Frozen Versions
Once published, a Value Kernel version **MUST NOT** be modified in place.

This includes:
- textual edits
- clarifications
- rewording
- reformatting
- “non-substantive” changes

If a change alters interpretation, it alters the kernel.

---

## 2. Versioning (Binding)

### VKG-2: Major Version Changes Only
All changes to the kernel **MUST** be released as a new **major version**
(e.g., v2.0.0).

Minor or patch versions are not permitted for kernel content.

### VKG-3: Version Coexistence
Multiple kernel versions may coexist.

Downstream systems **MUST** explicitly declare which version they enforce.

---

## 3. Authority and Precedence (Binding)

### VKG-4: Kernel Supremacy
In any conflict between:
- kernel constraints
- contracts
- implementations
- documentation
- operator instructions

**the Value Kernel prevails.**

### VKG-5: No Emergency Overrides
There are no emergency, administrative, or operator overrides
to kernel constraints.

Any override requires:
- proposal of a new kernel version
- review
- publication
- redeployment

---

## 4. Change Proposal Process (Binding)

### VKG-6: Proposal Requirement
All proposed changes **MUST** be submitted as a formal proposal
against a future kernel version.

Proposals **MUST** include:
- motivation
- description of the change
- analysis of impact
- migration considerations

### VKG-7: No Silent Adoption
No change may be adopted implicitly, experimentally, or by convention.

---

## 5. Deprecation and Retirement (Binding)

### VKG-8: No Forced Migration
No kernel version may be forcibly retired.

Systems may continue to enforce older versions
unless explicitly migrated.

### VKG-9: Explicit Deprecation
If a version is deprecated, that status **MUST** be declared explicitly
without altering the version’s content.

---

## 6. Records and Transparency (Binding)

### VKG-10: Public Record
Published kernel versions **MUST** include:
- version identifier
- publication date
- immutable content
- governance documents
- decision tests (where applicable)

### VKG-11: Audit Availability
Kernel artifacts **MUST** remain accessible for audit
for the lifetime of dependent systems.

---

## Appendix A — Informative Notes (Non-Authoritative)

- Governance exists to prevent accidental change, not to enable rapid change.
- Stability is a safety property.
- A kernel that is easy to change is not a kernel.

---

## Appendix B — Relationship to Downstream Systems (Informative)

- Contracts translate kernel constraints into enforcement semantics.
- Compliance defines eligibility to claim alignment.
- Implementations may evolve independently, provided enforcement remains intact.

These relationships do not modify kernel authority.
