---
type: synthesis
title: Glossary
created: 2026-09-26
updated: 2026-09-27
status: growing
tags: [synthesis]
confidence: high
sources: 5
---

# Glossary

One-line definitions of terms used in this wiki, each linking to its concept page.
Alphabetical. Kept short by design — the concept page holds the real explanation.

- **Agent memory** — persistent memory for an LLM agent across sessions — retain, recall, reflect → [Agent Memory](agent-memory.md)
- **Associative indexing** — Bush's mechanism: tie items to each other rather than filing each in one place; the link is the unit of knowledge → [Associative Indexing](associative-indexing.md)
- **Associative trail** — a named, replayable, shareable path between items; Bush's term for what a link graph preserves → [Associative Indexing](associative-indexing.md)
- **Augmentation means** — the four components of [H-LAM/T](h-lam-t.md) — Language, Artifacts, Methodology, Training → [H-LAM/T](h-lam-t.md)
- **Bank** — an isolated memory store in [Hindsight](hindsight.md); one brain per user, agent or project → [Hindsight](hindsight.md)
- **Baseboard management controller (BMC)** — the small always-on computer on a cluster board that mediates power, storage mode, flashing and serial console; what makes remote work possible → Turing Pi
- **Basic capability** — a capability that cannot usefully be changed further; the floor of a decomposition → [Capability Repertoire Hierarchy](capability-repertoire-hierarchy.md)
- **Batch ingest** — processing many sources without per-source discussion, reporting once at the end → AGENTS §4
- **BL31** — the ARM Trusted Firmware binary an RK3588 U-Boot build requires; non-free, from rkbin → rkbin
- **Boot order (`boot_targets`)** — the mutable U-Boot variable listing which devices get asked to boot, and in what order → Boot Order Environment Variable
- **Bootloader-only image** — a raw ~32 MiB image containing just the boot stages at fixed sector offsets, no filesystem → eMMC Bootloader Staging
- **CARA** — Coherent Adaptive Reasoning Agents — the component implementing `reflect` in [Hindsight](hindsight.md) → [Hindsight](hindsight.md)
- **Compile** — to integrate a source into existing wiki pages at ingest time, rather than deferring the work to query time → [LLM Wiki Pattern](llm-wiki-pattern.md)
- **Contested** — page status meaning an unresolved contradiction exists between sources → Contradictions
- **Disposition parameter** — a configured trait (skepticism, literalism, empathy) shaping how an agent reasons → [Disposition Parameters](disposition-parameters.md)
- **eMMC** — soldered flash on an SBC; the device the SoC's ROM trusts, and therefore where boot stages must live → eMMC Bootloader Staging
- **Epistemic separation** — keeping evidence, synthesis and belief in structurally distinct stores → [Epistemic Separation](epistemic-separation.md)
- **Extlinux (`extlinux.conf`)** — the text file U-Boot reads to find kernel, initrd, device tree and root partition → Extlinux Boot Configuration
- **Glossary** — this page; one-line definitions linking to concept pages
- **Growing mountain of research** — Bush's name for output growing faster than the means of consulting it → [Growing Mountain of Research](growing-mountain-of-research.md)
- **H-LAM/T** — *Human using Language, Artifacts, Methodology, in which he is Trained* — the system, not the person, is the unit of analysis → [H-LAM/T](h-lam-t.md)
- **idbloader** — Rockchip's first boot stage: the vendor TPL with U-Boot's SPL appended → U-Boot
- **Ingest** — the operation that reads a new source and propagates it through the wiki, typically touching 10–15 pages → AGENTS §4
- **Intelligence amplification** — raising a system's capability by organizing its parts; the gain belongs to the whole → [Intelligence Amplification](intelligence-amplification.md)
- **Knowledge compounding** — the property by which each new source and each filed answer raises the value of what is already stored → [Knowledge Compounding](knowledge-compounding.md)
- **Lint** — a periodic health check for contradictions, stale claims, orphans, red links, and index drift → AGENTS §9
- **LLM wiki pattern** — a knowledge base an agent compiles and maintains from immutable raw sources, under a written schema → [LLM Wiki Pattern](llm-wiki-pattern.md)
- **Maintenance burden** — the bookkeeping cost of keeping a knowledge base coherent; why humans abandon wikis → [Maintenance Burden](maintenance-burden.md)
- **Maskrom** — the RK3588 ROM download mode; the last-resort recovery path when a flash goes wrong → Turing RK1
- **Memex** — [Vannevar Bush](vannevar-bush.md)'s 1945 desk-sized device for storing and consulting a personal library by following associative trails; private storage, social trails → [Memex](memex.md)
- **Narrative fact** — a coarse-grained, self-contained memory unit covering a whole exchange → [Narrative Fact Extraction](narrative-fact-extraction.md)
- **Neo-Whorfian hypothesis** — the means of external symbol manipulation shape both language and intellectual capability → [Neo-Whorfian Hypothesis](neo-whorfian-hypothesis.md)
- **NVMe** — the PCIe storage device the OS is moved onto, leaving eMMC to hold only boot stages → eMMC Bootloader Staging
- **Observation (Hindsight)** — a preference-neutral entity summary synthesized from facts; carries no confidence score → [Epistemic Separation](epistemic-separation.md)
- **Opinion (Hindsight)** — a subjective judgment stored as (text, confidence, time) and revised by reinforcement → [Opinion Reinforcement](opinion-reinforcement.md)
- **Orphan** — a wiki page with no inbound links; a lint finding → AGENTS §9
- **PARTUUID** — a partition's stable identifier; used in `root=` so the kernel does not depend on device enumeration order → Extlinux Boot Configuration
- **Phase relation** — a *type* of link between terms — Ranganathan's five, extended by Vickery → [Typed Links](typed-links.md)
- **Primary text** — a source by the person or from the period being described; outranks secondary accounts when they conflict → Contradictions
- **Propagation** — step 5 of ingest: updating every entity, concept, topic, and synthesis page a source touches → AGENTS §4
- **RAG** — retrieval-augmented generation: retrieve chunks at query time and generate from them; no persistent synthesis → [Retrieval-Augmented Generation](retrieval-augmented-generation.md)
- **Raw layer** — the immutable source-of-truth directory; read by the agent, never modified → AGENTS §1
- **Regenerative feature** — augmenting the people doing the augmenting, so each gain funds the next → [Regenerative Feature](regenerative-feature.md)
- **Repetitive vs creative thought** — Bush's criterion for what to delegate: selection and choice of method stay human, fixed-procedure manipulation goes to the machine → [Repetitive vs Creative Thought](repetitive-vs-creative-thought.md)
- **RK3588** — Rockchip's octa-core ARM SoC; the chip in a Turing RK1 node → Turing RK1
- **Schema** — `AGENTS.md`: the rules that make an agent a disciplined wiki maintainer rather than a chatbot → AGENTS
- **Seed page** — a stub created because something mentioned it, awaiting a real source → AGENTS §6.2
- **Selection** — Bush's term for the real bottleneck: getting at the right item once storage is solved → [Growing Mountain of Research](growing-mountain-of-research.md)
- **Source page** — the wiki summary of one raw file, named `src-YYYY-MM-DD-slug.md` → {{Source Title}}
- **SPL** — Secondary Program Loader: the U-Boot stage concatenated with the vendor TPL to make `idbloader.img` → U-Boot
- **Spreading activation** — retrieval that walks outward from search hits along typed graph edges → [Spreading Activation Retrieval](spreading-activation-retrieval.md)
- **Symbol structuring** — how concepts are represented; constrained by, and constraining, concept and mental structure → [Symbol Structuring](symbol-structuring.md)
- **Synergetic structuring** — engineering synergism deliberately, by organizing components into higher levels → [Synergism](synergism.md)
- **Synergism** — organization as the source of intelligence — the whole exceeding the sum of its parts → [Synergism](synergism.md)
- **Synthesis layer** — the whole-wiki view: overview, open questions, contradictions, glossary → [Overview](overview.md)
- **TEMPR** — Temporal Entity Memory Priming Retrieval — the component implementing `retain` and `recall` → [Hindsight](hindsight.md)
- **Token budget** — a retrieval interface returning facts up to k tokens, rather than a fixed top-k → [Spreading Activation Retrieval](spreading-activation-retrieval.md)
- **Topic hub** — a map-of-content page linking out to a domain's pages; created at ≥4 related pages → {{Topic Name}}
- **tpi** — the CLI on a Turing Pi BMC: `power`, `usb`, `flash`; the whole remote control surface → tpi CLI
- **TPL** — the DDR-initialization blob from rkbin; the very first code that runs on an RK3588 → rkbin
- **Trail** — an associative-indexing path: named, permanent, replayable, giftable, and joinable from many items → [Associative Indexing](associative-indexing.md)
- **Trail blazer** — the profession Bush proposed to build trails; his answer to the maintenance-labor problem → [Trail Blazer](trail-blazer.md)
- **Typed link** — a link carrying a category as well as a target; eleven types are fixed by AGENTS §6.7 → [Typed Links](typed-links.md)
- **U-Boot** — the open-source bootloader between the SoC ROM and the kernel; owns the environment and reads extlinux → U-Boot
- **View generation** — producing a new projection of a structure on demand, for whatever question is live → [N-Dimensional Projection Problem](n-dimensional-projection-problem.md)
- **Zero-touch provisioning** — configuring a machine you never physically touch, mediated by a service processor → Zero-Touch Provisioning

## See also

- Index
- [Overview](overview.md)
