---
type: concept
title: Disposition Parameters
aliases: [disposition parameters, behavioral profile, CARA profile, skepticism literalism empathy]
created: 2026-09-26
updated: 2026-09-26
status: seed
tags: [concept/agent-memory]
confidence: low
sources: 1
---

# Disposition Parameters

[Hindsight](hindsight.md)'s configurable personality for reasoning: three integer traits —
**skepticism**, **literalism**, **empathy**, each 1–5 — plus a **bias-strength** parameter
β ∈ [0,1], together forming a behavioral profile Θ that shapes how `reflect` reasons over
the same memories ([Hindsight is 20/20: Building Agent Memory that Retains, Recalls, and Reflects](Sources.md), §3.3, §5.4).

## Definition

β sets how hard the profile is applied: *"For low bias values (β ≈ 0), system messages
emphasize objectivity and downplay stylistic constraints. For intermediate values (β ≈ 0.5),
they balance factual neutrality with preference-conditioned behavior. For high bias values
(β ≈ 1), prompts explicitly encourage stronger, more opinionated language aligned with the
specified preferences."*

Their Figure 5 is the demonstration: two agents read **identical facts** about remote work
and form opposite opinions.

| Profile | Opinion formed |
|---|---|
| Trusting, flexible, empathetic (S=1, L=2, E=5) | *"Remote work is a net positive because it removes commute time and creates space for more flexible, self-directed work."* |
| Skeptical, literal, detached (S=5, L=5, E=1) | *"Remote work risks undermining consistent performance because it makes it harder to maintain structure, oversight, and shared routines."* |

The stated purpose is **preference consistency** — that agents *"express stable reasoning
style and viewpoint across interactions rather than producing locally plausible but
globally inconsistent responses"* (§1). Profile can also modulate revision speed: *"a more
cautious configuration may use a smaller α"* in [Opinion Reinforcement](opinion-reinforcement.md), though this is
left to future work.

## Why it matters here

**It names something this vault has but doesn't configure.** Our agent's disposition is set
by prose in AGENTS — *"state confidence"*, *"say plainly when the wiki doesn't know"*,
*"always disclose that a conflict exists"*, *"never pad"*, *"recommend, not decide."* That
is a behavioral profile expressed as a document rather than as parameters, and it was
written collaboratively rather than selected from a menu.

The comparison is worth keeping visible because the two approaches fail differently. A
scalar profile is **consistent and opaque** — you can set skepticism to 5 but not inspect
what that does to a particular judgment. A written schema is **inconsistent and auditable**
— an agent may not apply it uniformly, but every rule can be read, argued with, and amended
by proposal (AGENTS §13). This vault has amended its own disposition three times in one
day that way.

**It raises a question the paper doesn't ask: whose disposition?** In Hindsight the profile
belongs to the *bank*, configured by a developer. In this vault the disposition is
negotiated with the owner and lives in a file the owner can edit. For a second brain —
where the beliefs being formed are supposed to be *the owner's* — an agent with a configured
personality is a liability unless the owner chose it. Our `*(inference)*` tag and the rule
that resolving conflicts is *"a human call"* are the guardrails.

## Why this page is a seed

`confidence: low`, for reasons that are specific and worth stating:

- Figure 5 is an **illustration**, not an experiment. No evaluation in the paper measures
  preference consistency or varies Θ.
- The three traits are asserted, not derived. Why skepticism, literalism and empathy rather
  than some other triple is never argued.
- Interaction effects are unexamined. What S=5, L=1, E=5 *means* is undefined.
- The trait→prompt mapping is a system-message template (Appendix A.2), so "disposition"
  here is prompt engineering with knobs — which is fine, but it is not the cognitive
  architecture the framing implies.

## Sources

- [Hindsight is 20/20: Building Agent Memory that Retains, Recalls, and Reflects](Sources.md) — primary; §1 (the preference-consistency problem),
  §3.3 (Θ and β), §5.4–5.5 (formation and reinforcement), §5.7 and Figure 5 (the
  illustration), Appendix A.2 (the opinion prompt)

## Relations

- **part-of** [Agent Memory](agent-memory.md)
- **explains** [Opinion Reinforcement](opinion-reinforcement.md) — the profile conditions what opinions get formed
- **contrasts** [Epistemic Separation](epistemic-separation.md) — observations are profile-neutral by design; opinions are not
- **contrasts** AGENTS — a written, amendable schema versus scalar configuration
- **derives-from** [H-LAM/T](h-lam-t.md) — disposition is a property of the artifact shaping the system's output
