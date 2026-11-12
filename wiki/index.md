---
type: meta
title: "Wiki Index"
updated: 2026-11-12
tags:
  - meta
  - index
status: evergreen
related:
  - "[[overview]]"
  - "[[log]]"
  - "[[hot]]"
  - "[[dashboard]]"
  - "[[Wiki Map]]"
  - "[[concepts/_index]]"
  - "[[entities/_index]]"
  - "[[sources/_index]]"
  - "[[LLM Wiki Pattern]]"
  - "[[Hot Cache]]"
  - "[[Compounding Knowledge]]"
  - "[[Andrej Karpathy]]"
---

# Wiki Index

Last updated: 2026-11-12 | Total pages: 33 | Sources ingested: 2

Navigation: [[overview]] | [[log]] | [[hot]] | [[dashboard]] | [[Wiki Map]] | [[getting-started]]

---

## Concepts

- [[dlabs-mosaic-gateway-proxy-diagnostics]] — Dlabs/Mosaic gateway and proxy diagnostics: real-IP chain, blackbox probes, rate limiting, and customer-vs-infra health separation (status: developing)
- [[Agent Architecture Takeaways from OpenAI Agents SDK]] — 5 stealable patterns from OpenAI Agents SDK: agent.asTool(), state taxonomy, lastAgent tracking, resumable delegation, sandbox agents (status: developing)
- [[LLM Wiki Pattern]] — the pattern for building persistent, compounding knowledge bases using LLMs (status: mature)
- [[Hot Cache]] — ~500-word session context file, updated after every ingest and session (status: mature)
- [[Compounding Knowledge]] — why wiki knowledge grows more valuable over time, unlike RAG (status: mature)
- [[cherry-picks]] — prioritized feature backlog from ecosystem research; 13 features to add to claude-obsidian (status: current)

---

## Infrastructure
- [[dns-sovereignty-stack]] — CachyOS devops-cachy machine-wide DNS pipeline: 3-layer split (Global resolved, NM wlan0, wg-quick link-scope). Built 2026-07-03 to kill the manual-DNS-refresh dance (status: evergreen)
- [[bcachefs]] — CachyOS devops-cachy rootfs reference: dual-NVMe bcachefs RAID-1, recovery commands, CONFIG_RUST warning, offline PDF dump. Built 2026-07-04 because agent offline access to upstream docs is non-negotiable for rootfs operators (status: evergreen)

## Sources
- [[simon-dcp-polytime-quantum]] — 2026-08-06 | Simon (AWS) preliminary draft: poly-time quantum DCP ⇒ poly-time SVP/LWE; unverified, existential-if-true for lattice crypto. Response plan: [[lattice-break-scenario-skh]]
- [[bcachefs-principles-of-operation-source]] — 2026-07-04 | bcachefs.org PDF dump (108 pages) | dual extract (pdftotext + markitdown), agent-readable but encoding-broken. Lives at `wiki/sources/bcachefs/`.

## Libertaria
- [[lattice-break-scenario-skh]] — doctrinal response plan for a verified poly-time quantum lattice break: attack surface, hedges, resurface triggers. Parked 2026-08-06 until algo migration or claim verification (status: developing)

---

## Entities

- [[Andrej Karpathy]] — AI researcher, creator of the LLM Wiki pattern, former Tesla AI director (status: developing)
- [[Ar9av-obsidian-wiki]] — multi-agent compatible LLM Wiki plugin; delta tracking manifest (status: current)
- [[Nexus-claudesidian-mcp]] — native Obsidian plugin + MCP bridge; workspace memory, task management (status: current)
- [[ballred-obsidian-claude-pkm]] — goal cascade PKM; auto-commit hooks, /adopt command (status: current)
- [[rvk7895-llm-knowledge-bases]] — 3-depth query system, Marp slides, parallel deep research (status: current)
- [[kepano-obsidian-skills]] — official skills from Obsidian creator; defuddle, obsidian-bases (status: current)
- [[Claudian-YishenTu]] — native Obsidian plugin embedding Claude Code; plan mode, @mention (status: current)
- [[Wigy]] — peer operator (Discord); ed25519 SSH keys for [[wigy-ryzen]] and [[wigy-p16]], cross-checked against GitHub 2026-08-27 (status: current)
- [[wigy-ryzen]] — Wigy's primary working machine (Ryzen-class), ed25519 key verified vs GH id 70976120 (status: current)
- [[wigy-p16]] — Wigy's second working machine (ThinkPad P16), ed25519 key verified vs GH id 142546874 (status: current)
- [[wigy-github-unattributed]] — two additional ed25519 keys on Wigy's GitHub with no host attribution; archive-only, do not assume active (status: archive)

---

## Sources

- [[claude-obsidian-ecosystem-research]] — 2026-04-08 | web research across 16+ repos | 8 wiki pages created

---

## Questions

- [[How does the LLM Wiki pattern work]] — how the pattern works and why it outperforms RAG at human scale (status: developing)
- [[grain-lessons-for-janus-haiku]] — Developer Voices × Cameron Barré (Grain/Clojure/event modeling) mapped onto Janus canon: constraint-as-product, event-store protocol, agent session loop, skills delivery, spec bridge, conformance suite; ALREADY CANON/PARTIAL/NEW tags + Haiku Law pre-flight (status: developing)

---

## Comparisons

- [[Wiki vs RAG]] — when to use a wiki knowledge base versus RAG; verdict: wiki wins at <1000 pages
- [[claude-obsidian-ecosystem]] — feature matrix of 16+ Claude+Obsidian projects; where claude-obsidian wins and gaps

---

## Domains

- [[liturgical-drift]] — Sovereign AI concept: mirror-weapon vs synthetic priest, and the drift from tool to delegated moral authority (status: developing)
- [[the-pantropy-doctrine]] — Libertaria canon concept: pantropy as sovereign biology and exit doctrine; terraforming as reform, pantropy as exit (status: developing)
- [[2026-05-01-wilber-fourfold-axis-for-exitarian-civilizational-design]] — writing backlog seed on Waking/Growing/Cleaning/Showing as civilizational stack for Exitarianism, with anti-priesthood guardrails (status: developing)
- [[2026-05-01-exitarian-way-of-building-technology-and-languages]] — Exitarian engineering doctrine for protocols and language design: exit-first architecture, explicit power, host sovereignty, and institutional mortality (status: developing)
- [[2026-04-30-sovereign-virtue-realism-philosophical-stack]] — composite Libertaria doctrine stack (virtue ethics, covenant, non-domination, decentralism, and crypto enforcement) (status: developing)
- [[2026-04-30-existentialism-as-detox-not-foundation]] — existentialism as anti-collectivist detox but insufficient civilizational foundation for Libertaria (status: developing)
- [[2026-04-30-objectivism-as-solvent-not-operating-system]] — Libertaria framing: preserve Objectivist anti-parasitic strengths while rejecting atomizing civilizational blind spots (status: developing)
- [[2026-04-30-dao-themes-for-libertaria-rubric]] — Dao-aligned governance and architecture themes mapped to Libertaria as future writing rubric (status: developing)
- [[2026-04-30-exitarianism-sex-slavery-covenant-vs-ownership]] — later-topic writing seed on covenant vs ownership in marital doctrine (status: developing)
