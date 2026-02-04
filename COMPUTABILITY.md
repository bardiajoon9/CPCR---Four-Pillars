# COMPUTABILITY.md — Ethics as a Gate

CPCR treats ethics as a **computability problem**, not a mood or a brand.

The core principles:

1. **Absence of data is itself a result.**  
   If required variables are missing, CPCR does not guess.

2. **Claims without computability are advertising, not ethics.**  
   A system that refuses to disclose what CPCR needs is making a marketing choice, not an ethical one.

3. **The system computes only when required variables are disclosed.**  
   When inputs are sufficient, CPCR can deterministically derive breaker states and allowed/disallowed actions.

4. **Refusal states are standardized.**  
   Instead of silent failures, CPCR returns explicit refusal outputs (see `REFUSAL_STATES.md`).

---

## Required variables (illustrative)

For the minimal CPCR stack, “required variables” include at least:

- PLANT metrics: water usage, soil regeneration, nutrient density, and the presence of an externality ledger.
- IRST metrics: loop gain, update period, correction latency.
- CTGS metrics: information gain flags, repetition counts, refund delays, compounding cost trap detection.
- NITT triggers: identity-claim language in user-facing text.

If any of these are structurally unavailable, CPCR should report an **Ethical Risk Index state** of `UNDETERMINED` or `REFUSED` rather than pretending that a safe answer exists.

---

## Practical implication

Systems that want the social and regulatory legitimacy of “CPCR-compatible” ethics must:

- expose the required variables, or
- accept that their offerings will be flagged as `UNDETERMINED` / `REFUSED` with a public explanation of missing disclosures.

CPCR’s job is not to save such systems from their own opacity.
