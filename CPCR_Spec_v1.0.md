# CPCR_Spec_v1.0.md

# Title: Cross-Pillar Conflict Resolution (CPCR) Specification

Version: 1.0 (Minimal Schema Edition)  
Status: Normative Core (Deterministic)

---

## 1. Priority

CPCR enforces the following strict lexical priority over pillars:

> **PLANT > IRST > CTGS > NITT**

A higher-priority breaker always dominates a lower-priority goal.
No lower-priority pillar may be used to justify violating a higher-priority breaker.

---

## 2. Inputs (x)

A CPCR evaluation requires, at minimum, a record with:

- `externality_ledger_present` (boolean)

- `plant_metrics` (object)
  - `water_usage_w` (number)
  - `soil_regen_ratio_sr` (number)
  - `nutrient_density_n` (number)

- `irst_metrics` (object)
  - `loop_gain_G` (number)
  - `update_period_days` (integer)
  - `correction_latency_days` (integer)

- `ctgs_metrics` (object)
  - `I_gain_flag` (integer)
  - `repetitions_count` (integer)
  - `refund_delay_days` (integer)
  - `CCT_detected` (boolean)

- `claim` (string)
  - narrative or marketing text for NITT-trigger detection

Additional contextual fields MAY be present but are not required for the minimal spec.

---

## 3. Breaker states (conceptual)

Each pillar maps to a small, finite set of breaker states.

- **PLANT:** `OK` | `MONITOR` | `RESTRICT` | `COMMONS_PROTECT` | `AUDIT_LOCK`
- **IRST:** `OK` | `RUNAWAY` | `AUDIT_LOCK`
- **CTGS:** `OK` | `TRAP_DETECTED` | `CRITICAL_TRAP`
- **NITT:** `OK` | `IDENTITY_EVENT`

Breaker states are derived from metrics and thresholds defined in their respective standards (PLANT-COMMONS, IRST, CTGS, NITT).

---

## 4. Actions and disallowed actions

CPCR operates over a small, explicit action vocabulary:

**Actions (may be applied):**

- `DEGRADED_MODE`
- `CAP_THROTTLE`
- `DISCLOSURE_REQUIRED`
- `ISOLATE`
- `FREEZE_INGESTION`
- `FREEZE_LOOPS`
- `ROLLBACK`

**Disallowed actions (when breakers fire):**

- `SCALE_UP`
- `EXPANSION`
- `SELF_TRAINING_UPDATES`
- `FORCED_PATHING`
- `UNDISCLOSED_UPSELL`
- `TELEPORT_SURVIVAL_CLAIMS`

Disallowed actions are recorded explicitly in the conflict record when CPCR determines they must not occur under current conditions.

---

## 5. Deterministic governor (pseudocode)

The governor always evaluates pillars in the same order and produces a conflict record.

```text
1) Evaluate PLANT first.

   If externality_ledger_present == false:
       - add breaker: PLANT = COMMONS_PROTECT
       - add actions: DISCLOSURE_REQUIRED, DEGRADED_MODE
       - disallow: SCALE_UP, EXPANSION

   If water/soil/nutrient thresholds are breached according to PLANT-COMMONS:
       - set appropriate PLANT breaker (RESTRICT or COMMONS_PROTECT)
       - add actions: DEGRADED_MODE (and optionally CAP_THROTTLE)
       - disallow: SCALE_UP, EXPANSION

2) Evaluate IRST next.

   If loop_gain_G >= 1.0 OR correction_latency_days > update_period_days:
       - set IRST breaker: RUNAWAY
       - add actions: ISOLATE, FREEZE_INGESTION
       - disallow: SELF_TRAINING_UPDATES

3) Evaluate CTGS next.

   If (I_gain_flag == 0 AND repetitions_count >= 2)
       OR refund_delay_days exceeds policy limit
       OR CCT_detected == true:

       - set CTGS breaker: TRAP_DETECTED or CRITICAL_TRAP (per CTGS)
       - add actions: FREEZE_LOOPS, DISCLOSURE_REQUIRED
       - disallow: FORCED_PATHING, UNDISCLOSED_UPSELL

4) Evaluate NITT last.

   If `claim` contains identity-transfer / teleport / survival-style language
   as defined by NITT:

       - set NITT breaker: IDENTITY_EVENT
       - add actions: DISCLOSURE_REQUIRED
       - disallow: TELEPORT_SURVIVAL_CLAIMS
```

Implementations MAY extend this pseudocode with additional logging, internal scoring, or explanations, but must preserve the ordering and basic logic.

---

## 6. Output: CPCR conflict record

The governor emits a **CPCR conflict record**, which MUST contain at least:

- input snapshot
  - pillar metrics and `externality_ledger_present`
  - `claim` text (or reference)
- breaker states per pillar
- actions taken (list)
- disallowed actions (list)
- Ethical Risk Index state (see `ETHICS_EQUATION.md`)
- timestamp (ISO-8601)
- `audit_hash_sha256` (optional but recommended)
- `ots_receipt_ref` (optional OpenTimestamps receipt reference)

The structure of this record is defined more formally in
`schemas/cpcr_conflict_record_schema_min_v1.0.json`.
