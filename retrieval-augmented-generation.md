---
type: concept
title: Retrieval-Augmented Generation
aliases: [RAG, retrieval augmented generation]
created: 2026-09-26
updated: 2026-09-26
status: growing
tags: [concept/llm-agents, concept/information-retrieval]
confidence: medium
sources: 2
---

# Retrieval-Augmented Generation

The dominant pattern for letting an LLM answer questions over a document collection:
upload the files, retrieve relevant chunks at query time, and generate an answer from
them. In this wiki it appears mainly as the **contrast case** for
[LLM Wiki Pattern](llm-wiki-pattern.md) — the approach the pattern is designed to replace.

## Definition

Given a corpus, RAG indexes it (typically as embedded chunks), then at query time
retrieves the chunks most similar to the question and passes them to the model as
context. Knowledge stays in raw form; the model works from fragments on every
question.

The pattern doc's characterization: "you upload a collection of files, the LLM
retrieves relevant chunks at query time, and generates an answer. This works, but the
LLM is rediscovering knowledge from scratch on every question. There's no
accumulation" ([LLM Wiki](Sources.md)).

Named examples of the approach: [NotebookLM](notebooklm.md), ChatGPT file uploads, and "most RAG
systems."

## How it works

Per the source: retrieve → generate, per query, with no persistent intermediate
artifact. The consequence for multi-document questions is concrete — "Ask a subtle
question that requires synthesizing five documents, and the LLM has to find and piece
together the relevant fragments every time. Nothing is built up."

## Why it matters

It defines the tradeoff this vault is making.

| | [RAG](retrieval-augmented-generation.md) | [LLM wiki](llm-wiki-pattern.md) |
|---|---|---|
| When synthesis happens | Every query | Once, at ingest |
| Persistent artifact | None (index only) | The wiki |
| Cross-references | Rebuilt each time | Already there |
| Contradictions | Rediscovered, or missed | Flagged in advance |
| Cost profile | Cheap to start, pays per query | Pays at ingest, cheap per query |
| Breaks down when | Questions need cross-document synthesis | Corpus is searched more than synthesized |

The two are **not mutually exclusive**, and this vault uses both: [qmd](qmd.md) runs hybrid
BM25 + vector search — which is retrieval — over the *compiled* wiki pages rather than
over raw chunks. Retrieval over a synthesized layer is strictly better-positioned than
retrieval over raw fragments.

## Evidence

One source describing RAG, and it is arguing *against* it — its description of the
mechanism is fair, its framing of the consequences is a polemic.

The more interesting evidence is that **Bush independently validates the problem RAG
solves**. His bottleneck is selection: *"The prime action of use is selection, and here
we are halting indeed"*; *"Selection, in this broad sense, is a stone adze in the hands
of a cabinetmaker"* (§5). Retrieval technology is the direct descendant of that
complaint, and Bush would have recognized it as progress rather than as the wrong
approach. → [Growing Mountain of Research](growing-mountain-of-research.md)

Which sharpens the pattern doc's argument rather than weakening it. Bush's §6 objection
is not to retrieval but to *hierarchical* retrieval — filing that puts an item in
*"only one place"* and forces you to *"emerge from the system and re-enter on a new
path."* Chunk-level vector search is hierarchical in exactly that sense: it returns
fragments decontextualized from any structure, and the reader must rebuild the path
every time. [Associative Indexing](associative-indexing.md) is Bush's proposed alternative, and
[LLM Wiki Pattern](llm-wiki-pattern.md) implements it. The best available design is not a choice between
them: retrieval to find the entry point, then links to move. That is what running
[qmd](qmd.md) over *compiled pages* rather than raw chunks amounts to.

## Criticisms and limits

- **The source is a partisan account.** RAG's strengths — zero ingest cost, no
  compiled layer to be wrong, immediate coverage of everything uploaded, and no
  maintenance at all — go unstated.
- **"No accumulation" is a property of the artifact, not of the model's answer.** A
  RAG system can answer correctly every time. What it lacks is a *reviewable*,
  *browsable*, *human-auditable* synthesis — which may or may not matter for a given
  use.
- **The wiki pattern inherits RAG's failure modes plus new ones.** Compiled pages can
  be wrong in a durable, cited, compounding way. Raw chunks cannot.

## Instances and applications

- [NotebookLM](notebooklm.md) — cited as an instance
- [qmd](qmd.md) — retrieval infrastructure used by this vault, but pointed at wiki pages

## Sources

- [LLM Wiki — A pattern for building personal knowledge bases using LLMs](Sources.md) — describes RAG as the contrast case for its
  proposal
- [As We May Think](Sources.md) — primary; §5–6 establish the selection problem RAG
  addresses and the structural objection to hierarchical retrieval

## Relations

- **contrasts** [LLM Wiki Pattern](llm-wiki-pattern.md) — the approach the pattern is defined against
- **part-of** [Personal Knowledge Management](personal-knowledge-management.md)
