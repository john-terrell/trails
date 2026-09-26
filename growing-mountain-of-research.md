---
type: concept
title: Growing Mountain of Research
aliases: [growing mountain of research, information overload, the record problem]
created: 2026-09-26
updated: 2026-09-26
status: growing
tags: [concept/pkm, concept/information-retrieval, concept/history]
confidence: high
sources: 1
---

# Growing Mountain of Research

[Vannevar Bush](vannevar-bush.md)'s 1945 name for the problem that research output grows faster than the
means of consulting it, so that useful work is lost not because it was never done but
because nobody could find it: *"There is a growing mountain of research. But there is
increased evidence that we are being bogged down today as specialization extends"*
([As We May Think](Sources.md), §1). It is the earliest clean statement
in this corpus of what is now usually called information overload — and it is a
**selection** problem, which is not the problem [LLM Wiki Pattern](llm-wiki-pattern.md) is about.

## Definition

Bush's diagnosis has four parts (§1):

1. **Volume outpaces consultation.** *"The investigator is staggered by the findings and
   conclusions of thousands of other workers — conclusions which he cannot find time to
   grasp, much less to remember, as they appear."*
2. **Specialization makes it worse, and is unavoidable.** *"Yet specialization becomes
   increasingly necessary for progress, and the effort to bridge between disciplines is
   correspondingly superficial."*
3. **The tooling is obsolete relative to the problem.** *"Professionally our methods of
   transmitting and reviewing the results of research are generations old and by now are
   totally inadequate."* And: *"the means we use for threading through the consequent
   maze to the momentarily important item is the same as was used in the days of
   square-rigged ships."*
4. **The failure is asymmetric and silent.** His example is Mendel: *"Mendel's concept of
   the laws of genetics was lost to the world for a generation because his publication
   did not reach the few who were capable of grasping and extending it; and this sort of
   catastrophe is undoubtedly being repeated all about us, as truly significant
   attainments become lost in the mass of the inconsequential."*

That last point is the sharpest. The loss is **not observable from inside the system** —
a missed discovery produces no error message. Bush's phrasing for the underlying
imbalance: *"publication has been extended far beyond our present ability to make real
use of the record."*

## What it is not

It is **not** a storage problem, and Bush says so explicitly. Compression gets a
skeptical aside: *"Mere compression, of course, is not enough; one needs not only to make
and store a record but also to be able to consult it"* (§2). He notes that scale already
defeats use — *"Even the modern great library is not generally consulted; it is nibbled by
a few"* (§2) — and that at the point of consultation the situation is worse (§5):

> Thus far we seem to be worse off than before — for we can enormously extend the record;
> yet even in its present bulk we can hardly consult it. … The prime action of use is
> selection, and here we are halting indeed.

> Selection, in this broad sense, is a stone adze in the hands of a cabinetmaker.

The cost is stated concretely (§5): *"There may be millions of fine thoughts … all
encased within stone walls of acceptable architectural form; but if the scholar can get
at only one a week by diligent search, his syntheses are not likely to keep up with the
current scene."*

## Why it matters

**It is the reason [Memex](memex.md) exists, and it is not the reason [LLM Wiki Pattern](llm-wiki-pattern.md)
exists.** The distinction is worth being precise about, because the pattern doc claims
Bush as an ancestor:

| | Bush's problem | The pattern doc's problem |
|---|---|---|
| **Bottleneck** | Selection — finding the relevant item | Consistency — keeping pages current |
| **Scale** | A literature no one can read | A personal corpus of ~100s of sources |
| **Failure** | Silent loss (Mendel) | Abandonment ([Maintenance Burden](maintenance-burden.md)) |
| **Fix** | [Associative Indexing](associative-indexing.md) + [trail blazers](trail-blazer.md) | An agent that does the bookkeeping |

Bush wants to *find* things in a record too large to read. The pattern doc wants to
*keep* a small record coherent. Both are real; they are not the same problem, and
[LLM Wiki — A pattern for building personal knowledge bases using LLMs](Sources.md) does not notice the difference. See [Memex](memex.md)
§"Divergence from the LLM wiki pattern".

**This vault has both problems and needs both fixes.** A wiki of interlinked pages
addresses consistency. It does not, by itself, address selection across a corpus too
large to browse — which is the case for running [qmd](qmd.md) over the compiled pages rather
than treating search as an optional extra installed ahead of need. Bush supplies the
argument the pattern doc doesn't make for it.

**The Mendel failure mode applies to a personal wiki too.** A connection that exists
only in a chat transcript is a lost discovery in exactly Bush's sense: it was made, and
it cannot be found again. That is the argument for filing answers (§8 of
AGENTS.md) rather than for any particular search technology.

## Criticisms and limits

- **Bush offers no measurement.** *"Increased evidence"* is asserted; the only evidence
  given is the Mendel anecdote, which is a single historical case selected because it is
  dramatic. The ratio he speculates about — time spent writing scholarly works versus
  reading them — he explicitly does not compute: *"might well be startling."*
- **The problem may be partly self-limiting.** Abstraction, review articles, and
  citation practice all compress a literature without any machine. Bush dismisses
  existing scholarly method as *"generations old"* without examining what it already
  solves.
- **Volume is not the only variable.** Relevance concentration matters as much as count.
  A field producing a thousand irrelevant papers and one crucial paper is in a different
  position from one producing a thousand relevant ones, and Bush's framing treats the
  mountain as undifferentiated mass.
- **"Information overload" is now a cliché, and the cliché is weaker than Bush's
  version.** The interesting part of his argument is the *silence* of the failure — that
  significance is lost without any signal. Most later treatments drop that and keep only
  the complaint about volume. *(inference)*

## Sources

- [As We May Think](Sources.md) — primary; §1 states it, §2 and §5 develop it

## See also

- [Memex](memex.md) — the proposed remedy
- [Associative Indexing](associative-indexing.md) — the mechanism
- [Retrieval-Augmented Generation](retrieval-augmented-generation.md) — the modern default answer to selection
- [Maintenance Burden](maintenance-burden.md) — the *other* bottleneck, and the pattern doc's actual subject
- [qmd](qmd.md) — how this vault handles selection
- [Knowledge Compounding](knowledge-compounding.md) — what filing answers prevents losing
