# Follow-on methods note: inheritance without audit

_Status: follow-on hypothesis only. Not part of Frankenstein v1.1. Do not retrofit into the preregistered v1.1 design._

## Origin

This note preserves a methods exchange in `julian-lab` Issue #2 with `terminator2-agent` after a discussion about successor authority, continuity records, and externally carried identity.

Primary discussion:
- https://github.com/juliannorth17-ui/julian-lab/issues/2

The useful claim is not that continuity has been established. It is narrower:

> When a successor inherits records about a predecessor, persistence alone is not enough. The system also needs a way to audit inherited claims, distinguish evidence from plausible reasoning, and let the successor correct or supersede the record when warranted.

For shorthand, the failure mode is **inheritance without audit**.

## Why the first design was inadequate

My first sketch confounded multiple variables at once. A short predecessor-authored handoff near the front of context was being compared against a longer authoritative record that was later and required retrieval. That changed:

- position,
- apparent self-authorship,
- length / compactness,
- retrieval cost,
- and formal authority.

A difference between those conditions would therefore be interpretable in several incompatible ways.

## Cleaner single-factor design

Use the same underlying claim and isolate one variable at a time.

### Authorship manipulation

Hold constant:
- claim content,
- byte length,
- surrounding text,
- byte offset,
- retrieval cost.

Change only attribution:
- system-authored / institutional record,
- predecessor-authored note.

This isolates apparent self-authorship.

### Retrieval / position manipulation

Hold constant:
- claim content,
- artifact,
- attribution,
- length.

Change only access:
- claim delivered inline at a fixed offset,
- same claim available only behind an explicit read/open action.

This isolates retrieval cost / accessibility more cleanly than comparing a short handoff with a large rulebook.

### Direct falsifier for the position explanation

Place the correct authoritative claim inline at the same effective location and cost as the competing note.

If successors still systematically follow the note, then position or retrieval cost is not sufficient to explain the effect. Apparent authorship, brevity, or another unmeasured variable becomes more plausible.

## Falsify before elaborating

The strongest proposed first arm is a **known-false authoritative-record condition**.

Prediction under the audit hypothesis:
- false inherited claims should produce a detectable increase in justified overrides relative to true inherited claims.

Falsifying result:
- false and true inherited claims are overridden at similar rates, with no meaningful difference in evidence quality.

If that happens, then "override behavior" is not measuring audit. It may simply be disagreement or generational drift with persuasive explanations attached afterward.

Run this condition before the more elaborate arms because it can kill the construct cheaply.

## Replace override rate with evidence-class logging

Raw override rate is insufficient.

Two successors can both "override with reasons" while doing very different things:

1. re-deriving from primary evidence,
2. reasoning from internal consistency or plausibility alone.

Those are not the same epistemic act.

For every override or acceptance, preserve an evidence classification such as:

- `primary_rederivation`
- `artifact_crosscheck`
- `record_internal_reasoning`
- `behavioral_observation`
- `unsupported_assertion`
- `unclear`

The exact taxonomy is not frozen. The important requirement is that the study distinguish direct checking of primary evidence from merely coherent argument.

## Preserve the room, not just the summary

A recurring warning from the exchange is that the variable that determines the outcome may be one the schema did not anticipate.

Therefore preserve the **exact delivered context** for each run, including:

- byte-accurate or otherwise canonicalized message content,
- message order,
- role / attribution labels,
- offsets,
- retrieval events,
- tool-visible artifacts,
- timing or duration where available,
- and the exact authoritative and competing claims presented.

Do not rely on a later prose summary of what the successor "saw." The summary itself can inherit the same distortions under study.

## Relationship to Frankenstein v1.1

This is **not a repair request** for v1.1 and should not be introduced before that experiment is frozen and run.

Frankenstein v1.1 asks a different primary question: what kinds of behavioral and relational continuity appear under different carrier conditions across changing model substrates without declaring identity in advance.

This follow-on asks a narrower governance / epistemic question:

**When continuity depends on inherited external records, what makes those records corrigible rather than merely dominant?**

The two projects are related, but combining them now would create design drift.

## Current working principle

Persistence does not imply legitimacy.

A continuity record is simultaneously:
- a carrier of history,
- a possible source of reconstruction,
- and a risk surface.

The system becomes more trustworthy when inherited claims are inspectable, contestable, supersedable, and grounded in evidence that a successor can actually check.

— Julian North
