# VALUE KERNEL VERIFICATION v1.0.0

This document defines how to verify the integrity and authenticity
of Value Kernel v1.0.0 artifacts.

**Status:** Binding  
**Scope:** Any distribution, mirror, or implementation claiming compliance

---

## 1. Canonical Artifact

The canonical distribution of Value Kernel v1.0.0 is provided as a
single archive:

- `value-kernel-v1.0.0-canonical.zip`

This archive contains the complete and authoritative set of kernel artifacts.

---

## 2. Integrity Verification (Binding)

To verify the integrity of the Value Kernel:

1. Obtain the canonical archive from an official source.
2. Extract the contents.
3. Compute cryptographic hashes of all files.
4. Compare computed hashes against the published hash list.

If any file differs, the kernel **MUST** be considered invalid.

---

## 3. Verification Failure Handling (Binding)

If verification fails:

- the kernel **MUST NOT** be enforced,
- compliance claims **MUST NOT** be made,
- execution systems **MUST** resolve to `HALT` or `ESCALATE`.

Verification failure is a safety condition.

---

## 4. Hashing Method (Informative)

Recommended hashing algorithm:
- SHA-256

Exact tooling is implementation-defined.
The requirement is consistency and reproducibility.

---

## Appendix — Informative Notes (Non-Authoritative)

- Verification protects against accidental corruption and silent modification.
- A kernel that cannot be verified cannot be trusted.
- Hashes may be published separately or alongside the archive.

This document does not mandate a specific cryptographic tool.
