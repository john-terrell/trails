---
type: concept
title: Typed Links
aliases: [typed links, phase relations, link types, relation types]
created: 2026-09-26
updated: 2026-09-26
status: growing
tags: [concept/augmentation, concept/pkm]
confidence: medium
sources: 1
---

# Typed Links

Links that carry a **category** as well as a target: not just "these two are related" but
"this *contradicts* that", "this *implements* that". Adopted by this vault on 2026-09-26
as AGENTS §6.7, on the strength of [Douglas Engelbart](douglas-engelbart.md)'s report of experimenting
with them.

## Definition

Engelbart's system allowed arbitrary user-defined link types (*"You can designate as many
different kinds of links as you wish, so that you can specify different display or
manipulative treatment for the different types"*), most of them directional (§III.B.4).
His worked example is an **argument structure**: `antecedent` links point to the
statements a claim rests on, and reversing them yields `consequent` links — so "How come?"
and "So what?" both become traversals of one typed graph.

For a controlled vocabulary he turned to library science (§III.B.8), citing **Ranganathan**'s
five *phase relations* between terms — one *biasing* the other, being a *tool* used to
study it, being an *aspect* of it, being in *comparison* with it, or *influencing* it —
and **Vickery**'s extensions: *effect on*, *cause of*, *use for*, *substitute for*,
*source for*, *implication of*, *explanation of*, *representation of*.

## The reported tradeoff

The single most useful sentence in the report for anyone considering this:

> It turned out to be a very invigorating innovation, and we began to take more pains with
> our structuring. It took longer to set up links and nodes in our structures, to be sure,
> but we found on the one hand that the structures became much cleaner and required fewer
> members, and on the other hand that we could get considerably more sophisticated help
> from the computer in doing significant chores for us.

Three claims: **slower to author**, **cleaner and smaller structures**, **more machine
assistance available**. The last follows from the first two — a machine can only automate
over a relation it can distinguish.

Note also what typing did to their *attitude*: categories they had treated as overhead
became the work. *"We initially felt that defining categories and relationships… were
things to be done as quickly as possible so that we could get on with the work. But… we
began to realize that they in reality might be the most significant part of that work."*

## Why it matters

**Untyped links discard the one thing the author knew.** When a page says `See also:
[Maintenance Burden](maintenance-burden.md)`, the relationship existed in the writer's head and was thrown away
on the way to disk. Typing preserves it, and preserves it *machine-readably* — which is
what makes `lint.py` able to enforce a vocabulary, and what would make queries like "show
everything that contradicts this" possible.

**It is the mechanism behind [Symbol Structuring](symbol-structuring.md)'s chain.** Better symbol structure
permits better concept structure. A typed link is a finer-grained symbol than a bare one.

**The retrofit cost is real and was paid.** Converting 20 pages and 5 templates on
2026-09-26 required a judgment per link — no script could supply the type. One genuine
finding came out of it: the original ten-type vocabulary could not express *"is the
problem that motivates this solution"*, the most common relation in a corpus about
problems and remedies, so `explains` was added as an eleventh mid-retrofit. Vocabulary
gaps surface on contact with real pages, not in design.

## Criticisms and limits

- **The evidence is qualitative, and partly fictional.** *"Cleaner and required fewer
  members"* carries no numbers. And the argument-structure demonstration sits in §III.B,
  which the report declares to be **fiction** (AGENTS §6.8). The Ranganathan/Vickery
  discussion in §III.B.8 is in the same section. What survives as evidence is that
  Engelbart considered typing worth proposing — not that it was measured.
- **Vocabulary maintenance is a standing cost.** Eleven types is already enough to
  hesitate over. Every addition needs a rationale; every ambiguous pair (`critiques` vs
  `contradicts`, `contrasts` vs `critiques`) is a recurring decision. A vocabulary that
  grows to thirty types is a vocabulary nobody applies consistently.
- **It can crowd out prose.** A relation worth explaining belongs in a sentence; a
  Relations block is an index, not an argument. §6.7 therefore requires a gloss on
  `contradicts`, `critiques` and `contrasts` and forbids `related` outright.
- **Reciprocity is expensive and here unenforced.** If A `contradicts` B, should B say so?
  §6.7 says expected but not linted. Unenforced reciprocity tends to decay.

## Sources

- [Augmenting Human Intellect: A Conceptual Framework](Sources.md) — primary; §III.B.4 (typed and directional
  links, antecedent/consequent), §III.B.5, §III.B.8 (phase relations, the tradeoff).
  **§III.B is fiction** — the report's declaration, not a caveat added here.

## Relations

- **part-of** [Augmenting Human Intellect](augmenting-human-intellect.md)
- **part-of** [Personal Knowledge Management](personal-knowledge-management.md)
- **implements** [Symbol Structuring](symbol-structuring.md) — a finer-grained symbol for relations
- **derives-from** [Associative Indexing](associative-indexing.md) — Bush's trails are the untyped ancestor
- **supports** [Knowledge Compounding](knowledge-compounding.md) — typed relations accumulate more than bare ones
- **contrasts** [N-Dimensional Projection Problem](n-dimensional-projection-problem.md) — typing recovers some of what serial prose loses
