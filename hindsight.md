---
type: entity
title: Hindsight
aliases: [hindsight, Hindsight memory, TEMPR, CARA]
created: 2026-09-26
updated: 2026-09-26
status: growing
tags: [entity/product, agent-memory]
confidence: medium
sources: 1
---

# Hindsight

An open-source (MIT) agent memory system from Vectorize.io, presented in
[a December 2025 technical report](Sources.md). Organizes memory into
four epistemically distinct networks and exposes three operations — **retain, recall,
reflect** — implemented as TEMPR (retrieval) and CARA (reasoning). Relevant to this vault
as the most developed published alternative to the [LLM Wiki Pattern](llm-wiki-pattern.md), and as a design
foil on the one question that matters most here: who resolves a conflict.

## Identity

| | |
|---|---|
| **Type** | product (open source, MIT) + managed cloud |
| **Vendor** | Vectorize.io |
| **Paper** | arXiv:2512.12818v1, 14 Dec 2025 |
| **Components** | TEMPR (retain/recall), CARA (reflect) |
| **Storage** | PostgreSQL + pgvector, or Oracle AI Database 23ai; embedded `pg0` option |
| **Clients** | Python, Node/TS, Go, CLI, REST, MCP server per bank |
| **Integrations** | LLM wrapper (2 lines), 60+ incl. Obsidian. **Pi: 4+ third-party extensions** — see below |
| **Claims** | LongMemEval 91.4%, LoCoMo 89.61% — see caveats below |

## Architecture

**Four networks** (M = {W, B, O, S}), each fact stored in exactly one
(→ [Epistemic Separation](epistemic-separation.md)):

| Network | Holds | Example from the paper |
|---|---|---|
| **W** world | objective external facts | *"Alice works at Google in Mountain View on the AI team"* |
| **B** experience | the agent's own, first-person | *"I recommended Yosemite National Park to Alice for hiking"* |
| **O** opinion | subjective judgments as `(text, confidence ∈ [0,1], time)` | *"Python is better for data science because of libraries like pandas"* (0.85) |
| **S** observation | preference-neutral entity summaries synthesized from W and B | *"Alice is a software engineer at Google specializing in machine learning"* |

**Memory unit:** `f = (u, b, t, v, τs, τe, τm, ℓ, c, x)` — with two temporal axes
(occurrence interval *and* mention time).

**Four link types:** temporal (exponential decay), semantic (cosine above threshold),
entity (weight 1.0, bidirectional over canonical entities), causal
(`causes`/`caused_by`/`enables`/`prevents`, upweighted in traversal).
→ [Typed Links](typed-links.md)

**Recall:** four channels in parallel → Reciprocal Rank Fusion → cross-encoder rerank →
greedy trim to a **token budget**, not a fixed top-k.
→ [Spreading Activation Retrieval](spreading-activation-retrieval.md)

## Why it matters to this vault

**1. It converges with us on provenance.** Its central criticism of the field — that
systems *"blur the line between evidence and inference"* — is what our `status:`,
`confidence:`, `*(inference)*` tags and separated source pages already encode. Two designs
reaching the same conclusion independently is mild evidence the conclusion is right.

**2. It diverges on conflict, and we have a counterexample.** Hindsight revises beliefs
automatically (→ [Opinion Reinforcement](opinion-reinforcement.md)); background merging *"resolves direct conflicts
in favor of the new information."* Our AGENTS §5 forbids that and requires a human
ruling. C-001 — a newer secondary source misdescribing an older primary one — is a case
where recency-wins preserves the error. → Contradictions C-003

**3. Its README describes our design.** *"Knowledge pages … living documents a bank writes
about itself, organized in folders like a wiki, searchable, and projectable onto disk as
ordinary markdown"*, and mental models as *"a standing answer to a question about a bank"*
that is *"rewritten in the background"* and read as *"a database read — no retrieval, no
LLM call."* That is a topic hub and a synthesis page. **Caveat: this is from the README, not
the paper — the vault has no primary source for the feature.**

**4. It is installable here — but through third-party code.** Corrected 2026-09-26 after
checking npm and pi.dev. There are at least four Pi extensions: `pi-hindsight` (anh-chu,
v1.4.2, ISC, ~450 LOC single file, raw `fetch`, .ini config, `#nomem`/`#global`/`#tags`
per-prompt controls, **no credential sanitization**), `@walodayeet/hindsight-pi` (~1500 LOC,
official SDK, JSON config, `tools`-only recall mode, retain batching, **does sanitize
credentials**), `@luxusai/pi-hindsight`, `@abix5/pi-hindsight`. The official
`@vectorize-io/hindsight-coding-agents` is described on npm as **"reflect-only"** — narrower
than its README implies. Adoption is low (126 downloads/mo for `pi-hindsight`).

Backend is heavier than "install a package": self-hosted Hindsight server **+ Postgres with
pgvector** (or Supabase) **+ an embedding API** (Gemini `embedding-001` or compatible) **+
HNSW indexes** for acceptable latency. Published figure: **~4 s** for a parallel
global+project recall on Supabase free tier, injected at `before_agent_start`.

**The load-bearing behaviour for this vault:** auto-retain captures the **full transcript
including tool-call names and inputs** (minus `bash`/`read`/`write`/`edit`). Run inside the
vault with retain enabled and every ingest conversation — source text, quotations, anything
pasted — is written to a Postgres bank automatically. Mitigated by `.hindsight/config` with
`retain_enabled = false` in the project root, which is enforced by the extension rather than
by discipline. → [How does this vault compare with Hindsight?](ans-2026-09-26-vault-vs-hindsight.md)

## Caveats on the claims

- **Vendor-authored**, five of seven authors from Vectorize.io. **No limitations section.**
- **Baselines largely not run by the authors** — *"taken directly from the Supermemory
  technical report"*; Backboard's *"could not be independently reproduced."*
- **91.4% is a hybrid**: Gemini-3 as answer generator over GPT-OSS-120B-powered retrieval
  and judging.
- **LongMemEval S only** (115k tokens, ~50 sessions). The M setting (1.5M tokens) is
  described but not reported.
- **Both benchmarks are conversational.** Nothing evaluates long-document synthesis or
  contradiction adjudication — what this vault actually does.
- **The sound result is the ablation**, not the leaderboard: same OSS-20B backbone,
  39.0% full-context vs 83.6% with the memory layer. That isolates the architecture.
- **The README's independence claim does not survive the author list** → Contradictions C-004.

## Sources

- [Hindsight is 20/20: Building Agent Memory that Retains, Recalls, and Reflects](Sources.md) — primary, vendor-authored (2026-09-26)
- The project README (`github.com/vectorize-io/hindsight`) was read but is **not** ingested
  as a source; README-only claims are flagged inline above.

## Relations

- **part-of** [Agent Memory](agent-memory.md)
- **implements** [Epistemic Separation](epistemic-separation.md)
- **implements** [Opinion Reinforcement](opinion-reinforcement.md)
- **implements** [Spreading Activation Retrieval](spreading-activation-retrieval.md)
- **contrasts** [qmd](qmd.md) — four channels and a token budget vs three and a top-k
- **contrasts** [LLM Wiki Pattern](llm-wiki-pattern.md) — automated consolidation vs human-adjudicated ingest
- **critiques** [Retrieval-Augmented Generation](retrieval-augmented-generation.md) — for conflating evidence and inference
