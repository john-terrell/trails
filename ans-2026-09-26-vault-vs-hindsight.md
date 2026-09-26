---
type: answer
title: "How does this vault compare with Hindsight?"
aliases: [vault vs hindsight, Hindsight comparison]
created: 2026-09-26
updated: 2026-09-26
status: growing
tags: [answer, agent-memory, pkm]
confidence: medium
sources: 4
---

# This vault vs. Hindsight

**Question:** how does this memory mechanism compare with Hindsight — what does each do
that the other doesn't?
**Answered:** 2026-09-26 · **Confidence:** medium · **Draws on 4 sources**

**Bottom line.** They are the same paradigm — compile knowledge rather than retrieve
fragments, keep provenance structural — pointed at different consumers. Hindsight's
consumer is **an agent under a token budget**; this vault's is **a person who intends to
disagree**. That single difference drives every divergence below. Hindsight is better at
capture, retrieval and measurement; this vault is better at auditability, provenance depth
and not being wrong quietly. They are complements, and Hindsight already ships a `pi`
integration.

## The answer

### What this vault does that Hindsight doesn't

**1. An immutable source layer you can go back to.** `raw/` is never modified, and every
claim cites a source page with a locator. This is not a nicety — it is what let a second
witness correct the first. [Augmenting Human Intellect: A Conceptual Framework](Sources.md) quotes Bush's memex
passage *"in its entirety"*, which exposed eight bad readings in our Bush text including an
**abridgement** (*"gathered together **from widely separated sources and bound together**"*).
Hindsight retains extracted narrative facts; there is no original to re-read, so no
equivalent correction is possible. Its observations do keep *"exact quotes and a proof
count"* (README) — better than most — but quotes of what was retained, not of a source.

**2. Human adjudication of conflicts.** AGENTS §5: *"Never overwrite a claim because a
newer source disagrees."* Hindsight revises automatically — `contradict` moves confidence by
`−2α` and *"may also update the opinion text"*; background merging *"resolves direct
conflicts in favor of the new information"*. **C-001 is a concrete counterexample to
recency-wins**: the newer source was the wrong one. → [Opinion Reinforcement](opinion-reinforcement.md),
Contradictions C-003

**3. The schema is a legible, amendable artifact.** AGENTS with proposals #001–#005 and
recorded rationales is something you can read, dispute and change — and did, four times in
one day. Hindsight's equivalent is code plus three scalar
[disposition parameters](disposition-parameters.md). Engelbart's finding applies directly:
*"defining categories and relationships… in reality might be the most significant part of
that work."* Ours is written down and argued about.

**4. Portability, diffability, no runtime.** Plain markdown plus git. No server, no
Postgres, no API key, no vendor, and `git diff` shows exactly what a source changed.
Hindsight needs PostgreSQL + pgvector or Oracle 23ai, plus an LLM key for retain and
reflect.

**5. Long-form argument as a first-class object.** Topic hubs carry reasoning, caveats and
confidence — written for a human to dispute. Mental models are *"a standing answer to a
question"* generated for an agent to consume.

**6. Depth on a narrow corpus.** Four sources read in full, one 144 pages. Cross-witness
textual verification, a resolved two-claim contradiction, a lineage traced Bush → list
processing → Engelbart. Nothing in Hindsight's benchmarks touches this: both are
conversational.

### What Hindsight does that this vault doesn't

**1. Passive capture.** The LLM wrapper retains on every call, two lines of code. We need
you to say `ingest`. For *"what did I decide three weeks ago"* it wins outright — our
`raw/notes/daily/` is a hole nobody will fill by hand.

**2. Measurement.** LongMemEval 39.0% → 83.6% on the **same OSS-20B backbone**, 89.0% at
OSS-120B, 91.4% with Gemini-3 as answerer; LoCoMo 83.18/85.67/89.61%. Multi-session
reasoning 21.1 → 79.7%, temporal 31.6 → 79.7%. Our corpus has complained for days that
nothing measures anything; this is the first source that does, and the same-backbone
ablation is exactly the design `open-questions` asked for.

**3. Temporal reasoning as a dimension.** Two time axes per fact — occurrence interval
`(τs, τe)` and mention time `τm` — plus a dedicated temporal retrieval channel with a hybrid
parser. We have dates in frontmatter and `grep`.

**4. An automatically-built typed graph.** Four edge types including **causal**
(`causes`/`caused_by`/`enables`/`prevents`), upweighted in traversal. We adopted 11 typed
relations this morning and assign every one by hand — and have no causal type at all.
→ [Typed Links](typed-links.md)

**5. Spreading activation.** Graph traversal from search hits outward, which recovers
material sharing no words with the query. We measured that BM25 *and* reranked hybrid both
miss `trail-blazer` for *"who should build the links between notes"* and that only a
hand-written hub recovers it. **Their mechanism automates our workaround.**
→ [Spreading Activation Retrieval](spreading-activation-retrieval.md)

**6. A token-budget interface.** `Recall(B, Q, k)` returns facts with `Σ|fi| ≤ k`. Our
budget is a prose guideline in §8 that nothing enforces.

**7. Operational maturity.** Bank isolation, multilingual by default, Memory Defense
(PII/secret scanning against 45 patterns), Prometheus, Kubernetes, webhooks, MCP per bank,
60+ integrations. Our equivalent of Memory Defense is a leak-audit regex written this
morning.

**8. Automatic consolidation.** Observations regenerate asynchronously when underlying facts
change. Ours updates on ingest or lint — human-triggered. Between operations our synthesis
goes stale silently.

## Where they converge — the interesting part

Hindsight's README describes **knowledge pages**: *"living documents a bank writes about
itself, organized in folders like a wiki, searchable, and projectable onto disk as ordinary
markdown"*, and **mental models** as *"a standing answer to a question about a bank"* that
is rewritten in the background and read as *"a database read — no retrieval, no LLM call."*

That is a topic hub and a synthesis page. So this is not two paradigms; it is one paradigm
with the governance automated rather than human-held. Which sharpens the trade:

> **Hindsight trades auditability for automaticity. This vault trades convenience for
> control.**

And on the deepest point they agree entirely, having reached it separately: provenance must
be **structural**, not incidental. Hindsight partitions into four networks because systems
*"blur the line between evidence and inference."* This vault uses `status:`, `confidence:`,
source pages and an `*(inference)*` tag. Neither knew about the other.
→ [Epistemic Separation](epistemic-separation.md)

## Evidence

| Claim | Source | Strength |
|---|---|---|
| Four networks; retain/recall/reflect; TEMPR + CARA | [Hindsight is 20/20: Building Agent Memory that Retains, Recalls, and Reflects](Sources.md) §3–6 | **Strong** — primary, technical, internally consistent |
| Same-backbone ablation 39.0% → 83.6% | ibid. §7.4, Table 3 | **Moderate** — sound design, vendor-run, no limitations section |
| Cross-vendor leaderboard numbers | ibid. Tables 3–4 | **Weak** — *"taken directly from the Supermemory technical report"*; Backboard *"could not be independently reproduced"* |
| 91.4% headline | ibid. §7.3 | **Weak as stated** — Gemini-3 answers over GPT-OSS-120B retrieval and judging |
| Knowledge pages / mental models | project **README**, not the paper | **Weak** — no primary source in this vault; flagged wherever used |
| "Independently reproduced" by VT and WaPo | README vs author list | **Contradicted** → Contradictions C-004 |
| Bush text corrections via second witness | [Augmenting Human Intellect: A Conceptual Framework](Sources.md) §III.A.1 | **Strong** — two independent witnesses |
| Search fails on vocabulary mismatch; hubs recover | this vault's Log, measured n=3 | **Moderate** — first-hand but n=3 on one corpus |
| Engelbart: methodology is the hard part | [Augmenting Human Intellect: A Conceptual Framework](Sources.md) §III.A.3 | **Moderate** — first-person, n=1 |

## Caveats

- **The benchmarks don't transfer.** LongMemEval and LoCoMo measure *multi-session
  conversational recall*. Nothing in either evaluates synthesizing a 144-page 1962 report
  against a 1945 essay and adjudicating a contradiction between them. 91.4% means much
  better at a different job.
- **Vendor-authored, no limitations section.** Five of seven authors are Vectorize.io,
  which sells the product. Table 1 scores all eight competitors ✗ on *"separates
  facts/opinions"* — the paper's own thesis — so it is not a neutral comparison.
- **`Assess()` is unmeasured.** The entire belief-revision mechanism rests on an LLM call
  returning `{reinforce, weaken, contradict, neutral}` with no reported accuracy. A
  misclassification silently moves a scalar nothing else audits.
- **This vault's side is n=1 and four days old.** "Better at auditability" is a design
  claim, not a measured one. We have never tested whether the owner actually catches an
  error the agent propagated.
- **Half of this comparison rests on a README**, which is not an ingested source.
  Knowledge pages and mental models — the convergence argument — have no primary source
  here. That is the weakest load-bearing element on this page.

## Contradictions considered

- **C-003 (open)** — automatic vs adjudicated belief revision. This is the substantive
  disagreement and the answer page takes no side beyond noting the corpus contains a
  counterexample to recency-wins.
- **C-004 (open)** — the README's independence claim versus the paper's author list. Bears
  on how much weight the leaderboard numbers deserve; does not touch the ablation.
- No conflict between Hindsight and Bush/Engelbart. They are answering different questions,
  which is itself the answer to the question asked.

## Follow-ups

- **Ingest A-Mem** (Xu et al. 2025, arXiv 2502.12110) — Zettelkasten agent memory with
  LLM-generated evolving links. The nearest published relative to this vault, and the only
  system in Hindsight's survey that shares our unit-of-knowledge choice. → Open Questions
- **Run the ablation on ourselves.** Same question answered with and without the wiki layer,
  model held constant. Hindsight proved the design is cheap and persuasive; we keep saying
  we should measure something and then not doing it.
- **Prototype entity-edge extraction from `## Relations`.** Our typed relations are already
  a graph; spreading activation over them could *propose* hub entries instead of an agent
  writing them by hand.
- **Decide C-003.** The draft split — automate noticing, keep human ruling — is in
  [Opinion Reinforcement](opinion-reinforcement.md).

## Pages drawn on

- [Hindsight](hindsight.md) — the system
- [Agent Memory](agent-memory.md) — the hub this question opened
- [Epistemic Separation](epistemic-separation.md) — the deepest point of agreement
- [Opinion Reinforcement](opinion-reinforcement.md) — the deepest point of disagreement
- [Spreading Activation Retrieval](spreading-activation-retrieval.md) — their answer to the recall failure we measured
- [Narrative Fact Extraction](narrative-fact-extraction.md) — the atomic-vs-narrative disagreement we're on one side of
- [Disposition Parameters](disposition-parameters.md) — configured personality vs a written schema
- [qmd](qmd.md), AGENTS, Contradictions

## Relations

- **part-of** [Agent Memory](agent-memory.md)
- **part-of** [Personal Knowledge Management](personal-knowledge-management.md)
- **contrasts** [Hindsight](hindsight.md) — the subject of the comparison
- **supports** [Epistemic Separation](epistemic-separation.md) — independent convergence is the evidence
- **derives-from** [Hindsight is 20/20: Building Agent Memory that Retains, Recalls, and Reflects](Sources.md)
- **explains** [Retrieval-Augmented Generation](retrieval-augmented-generation.md) — a third position in the RAG-vs-wiki framing
