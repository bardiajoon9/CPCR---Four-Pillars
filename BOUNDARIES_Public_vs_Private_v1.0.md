# BOUNDARIES_Public_vs_Private_v1.0.md

This document clarifies what the CPCR Four Pillars repository does and does not publish.

---

## In scope (public)

This repository does publish:

- normative text for the CPCR governor (`CPCR_Spec_v1.0.md`)
- minimal branch-rights disclosure text (`NITT_Branch_Rights_Disclosure_v1.0.md`)
- conceptual framing for computability and refusal states
- a state-based Ethical Risk Index
- minimal JSON Schemas for:
  - CPCR conflict records
  - IRST recursive audits
  - CTGS trap patterns
  - PLANT-COMMONS audits
  - ethical risk records
- example JSON records that satisfy those schemas
- hash and notarization conventions for document integrity

These are interfaces and governance structures, not implementation code.

---

## Out of scope (private)

This repository does not publish:

- calibration run bundles or tuning data
- runtime telemetry from any enforcement engine
- pipeline orchestration logic or internal control flow
- SparkVault hierarchy details
- TraceStack / parsing-engine internals
- Spark Lattice or SparkO$ internal mechanics

Those remain private to Spark’s own tooling and governance experiments.

---

## Implementation-neutral stance

Implementations may be:

- fully manual (human auditors following checklists)
- semi-automated (tools that help log and validate records)
- engine-driven (internal pipelines)

CPCR does not dictate which you must use. It requires only that:

- conflict records conform to the schemas, and
- pillar priorities and refusal semantics are respected.
