# Trails

A published trail network from a private second brain.

This is not a notebook and not a blog. It is the **connection layer** of a personal
knowledge base: concept, entity and topic pages that an LLM agent compiles and maintains
from primary sources, exported here so the trails can be followed by someone other than
their owner.

The idea is Vannevar Bush's. In [As We May Think](Sources.md) (1945) he proposed the
memex — a private store of documents whose *associative trails* between them were
first-class objects that could be named, replayed, gifted and inherited. Storage was
private; trails were social. This repo is the social half.

## What is here

Everything under [index.md](index.md). Start with
[overview](overview.md) for the current synthesis, or a topic hub.

## What is not here, and why

- **The raw sources.** Copyrighted text stays private. [Sources.md](Sources.md) is the
  bibliographic record, so citations resolve without republication.
- **Source summaries.** These quote at length and are internal bookkeeping.
- **The conflict register and open-questions list.** Internal deliberation about which
  sources are wrong and what to read next.
- **Journals, notes and anything personal.** This export is generated from an explicit
  allowlist; pages are published only if flagged, and the generator refuses to emit
  anything from the source or notes layers even if flagged by mistake.

## Provenance and reliability

Pages carry frontmatter. Read it:

| Field | Meaning |
|---|---|
| `status: stable` | Well-sourced, unlikely to shift |
| `status: growing` | Real content, still changing as sources are added |
| `status: seed` | A stub — mentioned somewhere, not yet properly sourced |
| `sources: N` | How many source pages back this one |
| `confidence` | The maintainer's calibration, not a guarantee |

**This corpus is young.** As of the export date it rests on very few sources, and early
pages were written before a primary text corrected them. Claims are attributed to their
sources throughout; where a source was wrong, the correction is recorded rather than
silently applied. Treat nothing here as settled.

## Colophon

Maintained by an LLM agent under a written schema, in an Obsidian vault, with a human
curating sources and ruling on conflicts. Regenerated from the private vault by script;
this repo is not edited by hand.
