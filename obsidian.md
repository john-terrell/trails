---
type: entity
title: Obsidian
aliases: [obsidian]
created: 2026-09-26
updated: 2026-09-26
status: growing
tags: [entity/product, pkm, tooling]
confidence: high
sources: 1
---

# Obsidian

The markdown editor this vault lives in, and the reading surface for the
[LLM Wiki Pattern](llm-wiki-pattern.md): the agent writes files, the owner watches them land and browses
the result. The pattern doc's framing — "Obsidian is the IDE; the LLM is the
programmer; the wiki is the codebase" — makes it a viewer and navigator, not a
note-taking app the human maintains.

## Identity

| | |
|---|---|
| **Type** | product (local-first markdown editor) |
| **Role here** | reader, graph viewer, link resolver, plugin host |
| **Vault path** | `~/Obsidian` |
| **Writes the wiki?** | No — the agent does (AGENTS.md §1) |

## Why it fits the pattern

Four properties do the work
([LLM Wiki](Sources.md)):

**It is plain files on disk.** No database to write into, no API to call. An agent
with filesystem access *is* a fully-privileged Obsidian user. This is also why the
vault is a git repo — "You get version history, branching, and collaboration for free."

**Graph view.** Called out as "the best way to see the shape of your wiki — what's
connected to what, which pages are hubs, which are orphans." It makes
[Maintenance Burden](maintenance-burden.md) visible: a page with no inbound links looks like a page with no
inbound links. The `graph` command in AGENTS.md §11 is the text-mode
equivalent.

**Wikilinks and backlinks.** `like this` resolves by filename alone, and
backlinks are computed automatically — so an agent that links aggressively gets
bidirectional navigation for free. This is why AGENTS.md §6.3 mandates
wikilinks over markdown links for internal references.

It is also a direct implementation of [Associative Indexing](associative-indexing.md). [Vannevar Bush](vannevar-bush.md)'s
objection to hierarchical filing is that an item *"can be in only one place, unless
duplicates are used"* and that *"having found one item … one has to emerge from the
system and re-enter on a new path"* ([As We May Think](Sources.md),
§6). Wikilinks are many-to-many, so neither objection applies. **The operative
consequence for this vault: `wiki/entities/`, `wiki/concepts/` and `wiki/topics/` are
filing convenience, not structure.** A page's meaning lives in its links. The folder
taxonomy should stay shallow, and merge decisions should prefer updating an existing
page over creating a near-duplicate in a different folder.

**Plugins extend it into the workflow:** [Obsidian Web Clipper](obsidian-web-clipper.md) for getting sources
in, [Dataview](dataview.md) for querying page frontmatter, [Marp](marp.md) for slide output.

## Configuration in this vault

Set in `.obsidian/` at setup, 2026-09-26:

| Setting | Value | Why |
|---|---|---|
| Attachment folder path | `raw/assets` | So clips download images into the immutable layer, per the doc's tip |
| Use markdown links | off | Wikilinks → graph view + backlinks |
| New link format | shortest | `[Memex](memex.md)` not `[Memex](memex.md)` |
| Templates folder | `wiki/meta/templates` | The five page templates |
| Daily notes folder | `raw/notes/daily` | Journal entries land in `raw/` where they can be ingested |
| Detect all file extensions | on | So PDFs and data files in `raw/sources/` are visible |

**Still to do by hand** (Obsidian UI, cannot be scripted): Settings → Hotkeys →
search "Download" → bind *Download attachments for current file* to `Ctrl+Shift+D`.
This is the doc's image-localization trick.

## Criticisms and limits

- **Nothing here is load-bearing.** The pattern is markdown files plus an agent;
  Obsidian is a convenience. Any editor, or `rg` in a terminal, would work. The doc
  itself calls all tooling "optional and modular."
- **Graph view degrades at scale** into a hairball. It is diagnostic for hubs and
  orphans at hundreds of pages, not a navigation tool at thousands.
- **Plugin dependency risk.** [Dataview](dataview.md) and [Marp](marp.md) are community plugins; neither
  is core. Anything the wiki depends on them to *display* is invisible in plain
  markdown — so AGENTS.md keeps all content readable without plugins.

## Sources

- [LLM Wiki — A pattern for building personal knowledge bases using LLMs](Sources.md) — "Tips and tricks" section, and the
  IDE/programmer/codebase framing
- [As We May Think](Sources.md) — not about Obsidian; cited here only for §6, the
  argument against hierarchical indexing that wikilinks and graph view implement

## See also

- [Associative Indexing](associative-indexing.md) — what wikilinks and graph view actually implement
- [Obsidian Web Clipper](obsidian-web-clipper.md) — the ingest front door
- [Dataview](dataview.md) — frontmatter queries
- [Marp](marp.md) — slide output
- [qmd](qmd.md) — search; complements Obsidian's own
- [LLM Wiki Pattern](llm-wiki-pattern.md)
- [Personal Knowledge Management](personal-knowledge-management.md)
