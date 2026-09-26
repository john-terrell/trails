---
type: concept
title: Repetitive vs Creative Thought
aliases: [repetitive thought, mechanizable thought, Bush's division of labor]
created: 2026-09-26
updated: 2026-09-26
status: growing
tags: [concept/pkm, concept/labor, concept/history]
confidence: high
sources: 1
---

# Repetitive vs Creative Thought

[Vannevar Bush](vannevar-bush.md)'s 1945 criterion for what should be handed to a machine: thought that
follows an established groove is mechanizable, thought that selects the data and the
process is not. *"For mature thought there is no mechanical substitute. But creative
thought and essentially repetitive thought are very different things. For the latter
there are, and may be, powerful mechanical aids"* ([As We
May Think](Sources.md), §3). It is the earliest statement in this corpus of the division of labor
that [LLM Wiki Pattern](llm-wiki-pattern.md) proposes — made 81 years earlier, and about arithmetic machines
rather than language models.

## Definition

Bush draws the line twice, and the second statement is the precise one (§4):

> every time one combines and records facts in accordance with established logical
> processes, the creative aspect of thinking is concerned only with the selection of the
> data and the process to be employed, and the manipulation thereafter is repetitive in
> nature and hence a fit matter to be relegated to the machines.

So the split is not "hard thinking vs easy thinking." It is:

- **Creative** — choosing *what* to combine and *by which* procedure. Irreducible.
- **Repetitive** — carrying out the combination once the procedure is fixed. Mechanizable.

He generalizes it in §5 by behavior rather than by difficulty: *"Whenever logical
processes of thought are employed — that is, whenever thought for a time runs along an
accepted groove — there is an opportunity for the machine."*

The test is whether the **groove is already cut**. If it is, a machine can run along it.

## Why it matters

**It is the pattern doc's division of labor, anticipated exactly.**
[LLM Wiki — A pattern for building personal knowledge bases using LLMs](Sources.md) assigns the human to *"curate sources, direct the
analysis, ask good questions, and think about what it all means"* and the LLM to
*"everything else"* — summarizing, cross-referencing, filing, bookkeeping. Map that onto
Bush:

| Bush (1945) | [LLM wiki](llm-wiki-pattern.md) (2026) | This vault |
|---|---|---|
| Selecting the data | Curating sources | What lands in `raw/` |
| Selecting the process | Directing the analysis | "emphasize X, skip Y" at AGENTS.md §4 step 3 |
| Repetitive manipulation | Summarizing, cross-referencing, filing | §4 steps 4–8 |
| No mechanical substitute | "think about what it all means" | The synthesis sections the owner must read |

The alignment is close enough that it is worth treating as **corroboration**: two
independent proposals, 81 years apart, draw the line in the same place. That is the
strongest support [LLM Wiki Pattern](llm-wiki-pattern.md) currently has, and it comes from the primary text
rather than from the pattern doc's own advocacy.

**It justifies the collaborative ingest mode.** The owner chose read → discuss → write
for this vault. On Bush's criterion that is not a preference but the correct allocation:
step 3 (deciding what matters) is the creative selection that has no mechanical
substitute, and steps 4–8 (propagation, bookkeeping) are the repetitive manipulation
that does. A fully automated ingest would mechanize the part Bush says cannot be
mechanized. Batch mode is therefore a genuine trade, not just a speed setting.

**It explains why the machine part is worth automating at all.** Bush's §1 argument is
that the ideas were always sound and the economics were wrong — Leibnitz's calculating
machine *"could not then come into use. The economics of the situation were against it"*;
Babbage's engine, *"his idea was sound enough, but construction and maintenance costs
were then too heavy."* His conclusion: *"The world has arrived at an age of cheap complex
devices of great reliability; and something is bound to come of it."* Substituting
"maintenance" for "construction" gives [LLM Wiki — A pattern for building personal knowledge bases using LLMs](Sources.md)'s entire
argument about the [Memex](memex.md). See [Maintenance Burden](maintenance-burden.md).

## Where the line actually falls in an LLM wiki

Bush's clean binary does not survive contact with the actual work, and this is the most
useful thing the concept now does.

**Summarizing is not purely repetitive.** Deciding which of a source's claims are
load-bearing is a judgment about relevance to *this* corpus — creative on Bush's
definition, since it selects the data. Yet it is exactly the work delegated to the agent.
The same applies to deciding whether a new fact *revises* an existing page or merely
*cites* it, and to noticing that two sources conflict.

**Which means the boundary is negotiated, not derived.** This vault handles it by
keeping the human in the loop at the two points where selection matters most: at ingest
step 3 (what to emphasize) and at Contradictions (how to resolve conflict — §5 makes
this explicitly *"a human call"*). Everything downstream is delegated. That is a design
decision responding to Bush's criterion, not an application of it.

**The risk is direction-specific.** Over-delegating *selection* produces a fluent wiki
that emphasizes the wrong things — and does so silently, in the same way Bush's Mendel
example fails silently ([Growing Mountain of Research](growing-mountain-of-research.md)). Over-delegating *manipulation*
is impossible; that's the point. So the error to guard against is always on the creative
side, which is the side that produces no visible symptom.

## Criticisms and limits

- **The binary is too clean even for Bush's own examples.** He concedes that a keyboard
  adding machine involves *"thought of a sort … in reading the figures and poking the
  corresponding keys"* (§3), then notes that even this is avoidable. The line moves as
  the machines improve, which makes it a statement about the state of the art rather
  than a fixed taxonomy.
- **It is an argument about 1945 machines.** Bush's mechanizable domain is arithmetic,
  formal logic, and selection by code. Whether natural-language summarization belongs in
  the repetitive class is precisely the question the last decade turned on, and Bush
  offers no basis for answering it. Using him as corroboration here is a structural
  analogy, not evidence. *(inference)*
- **He explicitly refuses the stronger claim.** §5: *"If scientific reasoning were
  limited to the logical processes of arithmetic, we should not get far in our
  understanding of the physical world. One might as well attempt to grasp the game of
  poker entirely by the use of the mathematics of probability."* A mathematician, he
  says, *"is primarily an individual who is skilled in the use of symbolic logic on a
  high plane, and especially he is a man of intuitive judgment in the choice of the
  manipulative processes he employs."* The judgment is in the *choice* — which is the
  creative side by his own definition.
- **The comfortable reading is the wrong one.** It is tempting to file this page as
  "Bush predicted LLMs." He predicted that fixed procedures would be mechanized, and
  warned that intuitive judgment would not be. The second half is the load-bearing half.

## Sources

- [As We May Think](Sources.md) — primary; §3 introduces the distinction, §4 states it
  precisely, §5 generalizes it and limits it

## See also

- [Vannevar Bush](vannevar-bush.md) — the author
- [LLM Wiki Pattern](llm-wiki-pattern.md) — the modern instance of the same division
- [Maintenance Burden](maintenance-burden.md) — the work being delegated, and the economics of delegating it
- [Growing Mountain of Research](growing-mountain-of-research.md) — the problem the delegation serves
- AGENTS — §4 step 3 and §5, where this vault keeps selection human
