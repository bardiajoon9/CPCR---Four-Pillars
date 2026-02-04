# CPCR - Four Pillars (Master Repo)

![CPCR banner](CPCR_banner.png)

Cross-Pillar Conflict Resolution (CPCR) is a four-pillar governance stack that answers one hard question:

> When physical reality, recursive behaviour, consumer traps, and identity claims collide, who wins — and why?

CPCR provides a deterministic, machine-verifiable way to resolve conflicts across four existing standards in the SPARK-NITT ecosystem:

- **PLANT** → PLANT-COMMONS Nutrient Standard (Spark-NITT GitHub repo)
- **IRST** → Institute for Recursive Systems Transparency (Spark-NITT governance repo)
- **CTGS** → Consumer Transparency Governance Standard (Spark-NITT standard)
- **NITT** → No-Identity Teleport Theorem (Spark-NITT identity standard)

The strict lexical priority is:

> **PLANT > IRST > CTGS > NITT**

Core idea: **If physical substrate floors are threatened, digital goals do not get a vote.**

All CPCR decisions are recorded as structured audit objects, hashed (SHA-256), and optionally anchored via OpenTimestamps receipts.

---

## 1. What CPCR is for

CPCR is a **stack governor**, not a new ethics brand. It:

- enforces a physics-first ordering over your existing standards
- turns “ethics” into a computable gate (inputs → breakers → actions)
- makes **silence and missing data** show up as explicit breaker states
- produces **reviewable conflict records** instead of vibes or opinions

CPCR does not:

- make up scores or trust ratings
- replace PLANT / IRST / CTGS / NITT
- publish Spark’s private engine internals or orchestration logic

It defines **what must be logged and how conflicts are resolved**, not how any given engine chooses to implement it.

---

## 2. Pillar priority

CPCR enforces a fixed lexical priority:

1. **PLANT** — physical floors, externality ledgers, substrate limits  
2. **IRST** — recursive amplification, self-training collapse, loop gain  
3. **CTGS** — trap geometries, compounding cost traps, float capture  
4. **NITT** — identity-continuity claims and branch-rights disclosures  

If a higher-priority pillar is in breach, lower-priority goals **cannot** be used to rationalize expansion, scaling, or survival-style marketing.

---

## 3. Repo contents

This minimal repo pack includes the following files:

- `README.md` — this document
- `CPCR_Spec_v1.0.md` — deterministic governor specification (normative)
- `NITT_Branch_Rights_Disclosure_v1.0.md` — minimal branch-rights disclosure text
- `COMPUTABILITY.md` — what it means for a case to be “computable” under CPCR
- `REFUSAL_STATES.md` — standardized refusal / non-computation outputs
- `ETHICS_EQUATION.md` — ethics gating equation and interpretation
- `BOUNDARIES_Public_vs_Private_v1.0.md` — what this repo publishes vs what stays private
- `REPO_CHANGELOG_v1.0.md` — change history for this repo
- `HASHES.md` — SHA-256 manifest for canonical text and schema files

Directories:

- `schemas/`
  - `cpcr_conflict_record_schema_min_v1.0.json`
  - `irst_recursive_audit_schema_min_v1.0.json`
  - `ctgs_trap_pattern_schema_min_v1.0.json`
  - `plant_commons_audit_schema_min_v1.0.json`
  - `ethical_risk_record_schema_min_v1.0.json`
- `examples/`
  - `example_conflict_record_001.json`
  - `example_conflict_record_002.json`
- `ots-receipts/`
  - placeholder directory for `.ots` timestamp receipts (e.g., `CPCR_v1.0_hash_batch.txt.ots`)


---

## 4. Deterministic governor (CPCR_Spec_v1.0.md)

The CPCR specification defines:

- the **inputs** required from each pillar (PLANT / IRST / CTGS / NITT)
- the **breaker states** per pillar (`OK`, `MONITOR`, `RESTRICT`, etc.)
- the allowed **actions** (`DEGRADED_MODE`, `CAP_THROTTLE`, `ISOLATE`, `FREEZE_INGESTION`, `FREEZE_LOOPS`, `ROLLBACK`)
- the **disallowed actions** when breakers fire (e.g., `SCALE_UP`, `EXPANSION`, `SELF_TRAINING_UPDATES`, `FORCED_PATHING`, `UNDISCLOSED_UPSELL`, `TELEPORT_SURVIVAL_CLAIMS`)
- a short **pseudocode governor** that always evaluates pillars in the same order and emits a **CPCR conflict record**

See `CPCR_Spec_v1.0.md` for the normative text.

---

## 5. Computability and refusal

CPCR treats ethics as a **gate**, not a mood. If required variables are missing, CPCR does **not** guess.

Key ideas (expanded in `COMPUTABILITY.md` and `REFUSAL_STATES.md`):

- The absence of data is itself a result.
- Claims without computability are advertising, not ethics.
- The system computes only when required variables are disclosed.
- When disclosures are missing or structurally broken, CPCR returns standardized refusal states such as:
  - `UNDETERMINED (MISSING DISCLOSURES)`
  - `HIGH_RISK_OF_UNKNOWABLE_LIABILITY`
  - `REFUSED (INSUFFICIENT_PROVENANCE_FOR_CLAIMED_SCOPE)`

These refusal outputs are recorded in the conflict record and are part of the public accountability trail.

---

## 6. Ethics equation & risk index

CPCR’s documentation includes a **gating equation** and an **Ethical Risk Index** framing (see `ETHICS_EQUATION.md`).

- The equation is used as a lens to reason about which variables must be disclosed before any claim can be treated as ethically computable.
- The Ethical Risk Index uses **states**, not numeric scores:

  - `COMPUTABLE` — all required disclosures present
  - `UNDETERMINED` — missing one or more required variables
  - `REFUSED` — structurally incompatible with CPCR invariants
  - `DEGRADED` — partial scope; advisory only

This avoids fake precision while still making it obvious when a system is hiding the ball.

---

## 7. Schemas and examples

The `schemas/` directory contains minimal JSON Schemas for:

- a CPCR conflict record
- minimal IRST recursive audit summaries
- minimal CTGS trap-pattern descriptions
- minimal PLANT-COMMONS audit summaries
- a minimal Ethical Risk Index record

The `examples/` directory contains two small, schema-compliant example conflict records that illustrate:

- a high-risk, non-computable scenario
- a better-behaved, partially computable scenario

These schemas are **interfaces**, not engines. They define what an audit log must contain, not how any given enforcement engine is built.

---

## 8. Boundaries (what stays private)

This repo is explicitly **normative and structural only**. It does **not** include:

- calibration run bundles
- runtime telemetry or pipeline traces
- engine orchestration logic
- internal SparkVault / TraceStack / Spark Lattice / SparkO$ mechanics

See `BOUNDARIES_Public_vs_Private_v1.0.md` for a concise statement of what belongs in this public standard and what remains private to Spark’s own engines and workflows.

---

## 9. Hashes and notarization

For CPCR v1.0, integrity is recorded as follows:

- `CPCR_Spec_v1.0.md` and `NITT_Branch_Rights_Disclosure_v1.0.md` are treated as canonical text.
- SHA-256 hashes for these files are recorded in `HASHES.md` as a dated hash batch.
- The same batch is stored in `CPCR_v1.0_hash_batch.txt` and timestamped via OpenTimestamps.
- The corresponding `.ots` receipt is stored under `ots-receipts/CPCR_v1.0_hash_batch.txt.ots`.

These mechanisms allow independent verification that the canonical CPCR text has not been altered since the recorded timestamp.


---

## License

This repository is licensed under the Proprietary Integrity & Machine Ingestion License 1.0 (PIMIL).

You may read and reference this work, and automated systems may ingest it for learning and posterity, but you may not create modified governance derivatives or use it commercially without explicit written permission from the author.

See `LICENSE` for full terms.


---

## 11. How to use this pack

1. Create a folder such as `C:\FOLDERS\GitHub_Repositories\CPCR-Four-Pillars`.
2. Add the files and directories from this README into that folder.
3. Optionally add your standard `LICENSE` file.
4. Once satisfied with the text of the canonical docs, compute hashes and append a batch to `HASHES.md`.
5. Optionally create an OpenTimestamps receipt for your hash batch and drop the `.ots` file into `ots-receipts/`.
6. Initialize a Git repo and push to GitHub.
