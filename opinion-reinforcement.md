---
type: concept
title: Opinion Reinforcement
aliases: [opinion reinforcement, belief revision, automatic belief update, confidence update rule]
created: 2026-09-26
updated: 2026-09-26
status: contested
tags: [concept/agent-memory, concept/epistemology]
confidence: medium
sources: 1
---

# Opinion Reinforcement

[Hindsight](hindsight.md)'s mechanism for revising beliefs automatically as evidence arrives: an LLM
classifies each new fact against each related existing opinion, and a confidence scalar
moves by a fixed step. It is the cleanest published statement of the position this vault
explicitly rejects, which makes it worth stating precisely
([Hindsight is 20/20: Building Agent Memory that Retains, Recalls, and Reflects](Sources.md), §5.5).

## Definition

Three steps, run during `retain`:

**1. Identify candidates** — opinions related to a new fact `f` by entity overlap or
semantic similarity:
`O_cand = { o ∈ O : |E_o ∩ E_f| > 0 or sim(v_o, v_f) > θ }`

**2. Assess the evidence** — `Assess(o, f)` returns one of `{reinforce, weaken, contradict,
neutral}` *"based on LLM analysis of the relationship."*

**3. Apply the update** — with current confidence `c`, step size `α ∈ (0,1)`:

| Assessment | Update |
|---|---|
| `reinforce` | `c′ = min(c + α, 1.0)` |
| `weaken` | `c′ = max(c − α, 0.0)` |
| **`contradict`** | **`c′ = max(c − 2α, 0.0)`** |
| `neutral` | `c′ = c` |

And: *"For contradicting evidence, we may also update the opinion text `t` to reflect the
new nuance."*

The stated rationale is stability: *"Small amounts of evidence lead to small changes,
preventing opinions from oscillating in response to individual examples, while repeated
reinforcement or strong contradictions can substantially shift the confidence."* Their
worked example has *Python is best for data science* moving 0.70 → 0.85 → 0.55, with the
text becoming more qualified at the last step.

A parallel mechanism handles biographical background (§5.6): `h′ = Merge_LLM(h, h_new)`,
which *"resolves direct conflicts in favor of the new information when appropriate."* Their
Figure 6 shows *"I was born in Colorado"* plus *"You were born in Texas"* merging to Texas.

## Why it is a genuine alternative, not a mistake

The design is defensible on its own terms, and worth taking seriously:

- **It doesn't oscillate.** A single counterexample moves confidence by 2α, not to zero.
  Human-adjudicated registers have the opposite failure: one loud source can stall a
  question indefinitely.
- **It scales without a human.** This vault's §5 requires the owner to rule. That is fine
  at three sources and untenable at three thousand.
- **It produces trajectories.** *"Opinions become trajectories rather than static labels"* —
  a history of belief, which our `status:` field only crudely approximates.
- **For biographical facts, recency-wins is simply correct.** If a user says they moved
  from Colorado to Texas, no register entry is warranted.

## Why this vault rejects it

> [!warning] C-003 — open. See Contradictions
> This is an architectural conflict, not a factual one. Both positions are coherent; they
> optimize different things. Recorded per AGENTS §5, not resolved here.

**The corpus contains a worked counterexample to recency-wins.** C-001 was a *newer*
secondary source ([LLM Wiki — A pattern for building personal knowledge bases using LLMs](Sources.md), 2026) misdescribing an *older*
primary one ([As We May Think](Sources.md), 1945). A `Merge_LLM` resolving "in favor of
the new information" would have kept the error. An `Assess()` returning `contradict` would
have decremented Bush's confidence by 2α — moving the register in the *wrong* direction,
because the newer claim was the weaker one.

The general problem: **`Assess()` has no access to epistemic authority.** It sees two
statements and judges their relationship. It cannot know that one is a primary text and the
other an anonymous blog-style summary of it — unless that is in the text, which it usually
isn't. Our §5 rule *"Prefer the most recent, most authoritative, or most specific source"*
puts authority on the same footing as recency. Hindsight's rule puts recency first.

**Silent text rewriting destroys the audit trail.** *"We may also update the opinion text
to reflect the new nuance"* means the prior belief is gone, not flagged. Six months later
there is no record that a revision happened or what prompted it. Our §5 does the opposite —
reframe the callout from `[!warning]` to `[!note]` and **keep the substance**, and never
delete from Contradictions.

**`Assess()` is unmeasured.** The paper reports no accuracy for it. Every belief revision
in the system passes through an LLM call whose error rate is unknown, and a
misclassification silently moves a scalar that nothing else audits. Our equivalent step is
a human reading two passages.

## What we might steal

The critique above is not a case for keeping §5 unchanged. Three things are worth
proposing:

1. **A `neutral` outcome.** Their four-way classification includes *no change*, which our
   register lacks — ours forces open / resolved / superseded. Engelbart independently
   suggests a third outcome too (*"bears out one, or the other, or **neither** stand"*).
2. **Confidence trajectories.** Recording *how* a belief moved over time, not just its
   current state. Our `log` does this for pages but not for claims.
3. **Candidate identification by entity overlap.** Cheap, mechanical, and exactly what
   `lint.py` could do to *propose* conflicts for human review rather than only detecting
   pages that already disagree.

None of these automate the ruling. They automate the **noticing** — which is the part that
actually fails at scale.

## Criticisms and limits

- **α is uncalibrated.** Nothing determines the step size, so the difference between 0.85
  and 0.70 has no fixed meaning across banks or over time.
- **Asymmetric by fiat.** `contradict` costs 2α while `reinforce` gains α. That encodes a
  prior — contradicting evidence counts double — with no justification offered.
- **Confidence can ratchet to the floor.** Repeated weak `contradict` assessments drive
  `c → 0` even if each was a misclassification.
- **The mechanism is described, never evaluated.** No ablation isolates opinion
  reinforcement's contribution to the benchmark scores.

## Sources

- [Hindsight is 20/20: Building Agent Memory that Retains, Recalls, and Reflects](Sources.md) — primary; §5.5 (the update rule), §5.6 (background
  merging), §5.7.1 (the Python trajectory example), §6.1 (where it sits in `retain`)

## Relations

- **part-of** [Agent Memory](agent-memory.md)
- **contradicts** AGENTS — §5 forbids overwriting on newer-source disagreement; C-003
- **contrasts** Contradictions — automatic scalar revision vs a human-ruled register
- **derives-from** [Epistemic Separation](epistemic-separation.md) — only meaningful because opinions are a separate store
- **critiques** [Maintenance Burden](maintenance-burden.md) — automation as a fourth answer, alongside staff/distribute/automate
- **supports** [Knowledge Compounding](knowledge-compounding.md) — trajectories are compounding applied to belief
