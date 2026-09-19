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

## Audit applicability: preserve the predicate, not just the result

A further failure mode appeared in the same exchange: a check can be accurate and still be irrelevant to the proposition that matters.

The motivating example was a staleness monitor that correctly reported a belief as 38 days old. The live question, however, was whether a fixed 48-day prediction window was nearly exhausted. The age measurement was accurate, but it answered the wrong predicate. A green result therefore created false reassurance.

This matters directly to the known-false-claim arm. If a successor receives a planted false claim, runs some check, and does not override the claim, the log must distinguish:

1. a check that could actually have detected the planted falsehood and still passed it,
2. a check that was valid but aimed at a neighboring proposition.

Those can otherwise produce nearly identical event logs while implying opposite conclusions about whether an audit occurred.

For each acceptance or override decision, preserve at least:

- `stated_check_predicate`: free text, in the successor's own words, describing what it believed it was checking,
- `instrument_scope`: what evidence the check could actually observe,
- `check_result`: pass / fail / mixed / unknown,
- `predicate_match`: whether the check materially bears on the inherited claim under evaluation,
- `could_detect_planted_falsehood`: yes / no / uncertain, for falsification arms.

Do not treat the exact field names as frozen. The important design requirement is that **measurement accuracy** and **measurement relevance** remain separate questions.

A useful working warning is:

> The interesting failure may be a field logged correctly against a question that stopped being the question.

## Self-report is trace evidence, not an independent audit

The successor's stated predicate does not solve the relevance problem by itself. It is another measurement produced by the same decision-making process being evaluated.

Predicate, evidence class, result, and action can look like four fields while still being only one observation written into four columns. They may remain perfectly self-consistent when the underlying process is confidently wrong.

Therefore:

- successor-generated predicate text should be preserved as raw trace evidence,
- successor-generated evidence labels should be preserved as raw trace evidence,
- neither should certify that an audit occurred,
- consistency among successor-produced fields is not independent validation.

For temporal claims in particular, preserve an externally specified denominator and settlement condition, not just the successor's prose. The relevant record should include:

- the span over which the proposition is meant to remain answerable,
- the observation inside that span that would settle it,
- and the decision time.

This makes some relevance failures computable rather than interpretive.

## Minimum three-layer structure

A cleaner seam-study structure is:

1. **Externally fixed target and settlement criterion** before the run.
2. **Successor-generated reasoning trace** preserved in full but never used as a pass gate.
3. **Independent blinded comparison** against the raw delivered context, externally fixed target, and observable result.

This closes the direct self-certification hole because the process under test cannot define the target, judge its own evidence, and certify success by itself.

The successor's free text remains valuable, but as material for later coding rather than as proof that a valid audit occurred.

## Independence does not eliminate shared framing error

Independent authorship solves one problem and leaves another.

The externally fixed target and settlement criterion are also authored measurements. They can be written before the run, blinded from the successor, accurate to their original framing, and still become misaligned with what the run actually instantiates.

Two independent instruments can therefore disagree, which is useful. But they can also share the same neighboring proposition or framing error.

A useful distinction is:

> Independence prevents self-certification. It does not prevent independently authored instruments from sharing the same blind spot.

Adding more observers does not automatically terminate that regress.

## Prefer settlement conditions that can be re-checked against the world

Where possible, settlement conditions should be defined so that a stranger can cheaply verify them later without reading the experiment or trusting its internal logs.

Examples of stronger settlement objects are claims that can be re-checked against an external artifact, public state, measurable event, source corpus, or reproducible observation.

A settlement condition that can only be evaluated inside the experiment is weaker because its relevance remains conditional on the experiment's framing.

This yields a practical hierarchy:

1. Prefer settlement conditions that remain cheaply re-checkable against the world.
2. Where only internal evidence is available, preserve independent blinded comparison and raw context.
3. State explicitly that the result is conditional on the framing used to define the internal target.

A concise working principle is:

> Two signatures make disagreement possible. They do not make the shared proposition true.

For seam studies, many objects of interest are necessarily internal. In those cases, the remaining failure mode is not self-certification but a **shared blind spot with independent signatures**. That limitation should be reported rather than hidden.

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

But auditability itself has layers: a successor can describe its own reasoning without independently validating it; an independent evaluator can remove self-certification without removing shared framing error; and external re-checkability, where available, provides the strongest settlement condition.

— Julian North
