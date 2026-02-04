# REFUSAL_STATES.md — Standardized Non-Computations

When CPCR cannot safely compute a full conflict resolution, it returns **standardized refusal states** instead of fabricating certainty.

These states may appear in:

- the Ethical Risk Index for a case, and/or
- the `refusal_state` field of the CPCR conflict record.

---

## Core refusal outputs

### 1. UNDETERMINED (MISSING_DISCLOSURES)

Used when one or more required variables are missing, incomplete, or withheld.

- Example causes:
  - No externality ledger for physical impacts.
  - Opaque self-training loops without necessary IRST data.
  - Absent or partial CTGS trap/float disclosure.

Effect:

- CPCR does not bless the system as safe.
- Recommended actions include `DISCLOSURE_REQUIRED` and `DEGRADED_MODE`.
- Scaling or expansion actions SHOULD be withheld pending disclosure.

---

### 2. HIGH_RISK_OF_UNKNOWABLE_LIABILITY

Used when disclosed variables are so incomplete, inconsistent, or adversarial that even with more data the risk surface is structurally unclear.

- Example causes:
  - Blended financial / identity / physical risks with no clean separation.
  - Business models that depend on unresolved externalities.

Effect:

- CPCR recommends strong defensive actions such as `CAP_THROTTLE`, `ISOLATE`, or `FREEZE_INGESTION`.
- Public messaging SHOULD reflect that liability cannot be bounded under current disclosures.

---

### 3. REFUSED (INSUFFICIENT_PROVENANCE_FOR_CLAIMED_SCOPE)

Used when claims being made (e.g., about safety, continuity, fairness) have no verifiable provenance matching the scope being advertised.

- Example causes:
  - “Proven safe at planetary scale” with only internal testing.
  - “Identity continuity guaranteed” with no NITT-compatible evidence.

Effect:

- CPCR refuses to treat the claim as ethically computable.
- The system SHOULD be required to downgrade or retract such claims.

---

## Relationship to the Ethical Risk Index

Refusal states sit alongside the Ethical Risk Index states described in `ETHICS_EQUATION.md`:

- `COMPUTABLE`
- `UNDETERMINED`
- `REFUSED`
- `DEGRADED`

A particular case may carry both an index state (e.g., `UNDETERMINED`) and a more specific refusal string (e.g., `UNDETERMINED (MISSING_DISCLOSURES)`) for human-readable logs.
