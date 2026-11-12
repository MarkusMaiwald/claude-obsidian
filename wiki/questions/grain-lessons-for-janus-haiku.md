---
type: synthesis
title: "Grain Lessons for the Janus Haiku"
question: "What can we learn from the Developer Voices discussion with Cameron Barré (Grain/Clojure/event modeling) and adopt into the Janus Haiku way — simple elegance and expressiveness?"
answer_quality: solid
created: 2026-11-12
updated: 2026-11-12
tags:
  - janus
  - haiku
  - grain
  - event-modeling
  - agent-tooling
  - synthesis
status: developing
confidence: medium
explored: false
related:
  - "[[2026-05-01-exitarian-way-of-building-technology-and-languages]]"
sources:
  - "https://www.youtube.com/watch?v=WhXPEmdNRpA (Developer Voices, Kris Jenkins × Cameron Barré, transcript in session)"
  - "https://github.com/ObneyAI/grain"
  - "https://eventmodeling.org/"
  - "https://juxt.github.io/allium/"
  - "https://github.com/jank-lang/clojure-test-suite"
  - "https://curtclifton.net/papers/MoseleyMarks06a.pdf"
---

# Grain Lessons for the Janus Haiku

Synthesis of the Developer Voices episode (Cameron Barré on Grain, Clojure,
event modeling) against Janus canon. Method follows the house pattern set by
`RFC-hinge-ai-era-ecosystem.md`: map each insight to `[ALREADY CANON]`,
`[PARTIAL]`, or `[NEW]`, then run new seeds through the Haiku Law pre-flight.
Janus evidence: `factory-x86:/srv/workspaces/projects/LIBERTARIA_STACK/JANUS/`
(`$W` = workspace, `$J` = `$W/janus`). Read-only inspection 2026-11-12; no
runtime verification.

## The one-sentence lesson

**Constraints are a product, not a cage.** Grain's claim: a small fixed set of
declarative primitives (commands, events, views, processors) makes every app
self-describing, so agents cannot drift architecturally — "anything novel
outside the primitives is simply wrong." Janus already fights variance at the
language level (FEATURE-ADMISSION gates, Haiku Law, closed positions); the
adoption is to push the same uniformity one layer up, into the application
architecture agents build with Janus.

## Current-state honesty (what "Haiku" is today)

- Haiku enforcement is **line-oriented lint**, not a proven compiler profile:
  `--haiku` combines Zigism, stdlib-boundary, ambient-authority scans; strict
  opt-in via `//! haiku: strict` adds naming/pointer/raw-memory rules
  (`$J/src/lint_command.zig:184-218,318-368,511-513`,
  `$J/examples/haiku_lint_profile.jan`).
- RFC-002 profile taxonomy v2 (capability sets × strict/fluid, `:haiku` as
  core alias) is **PROPOSAL — awaiting review**; its fluid `:script` model
  conflicts with the AOT-first README (`$J/docs/rfcs/RFC-002-profile-taxonomy-v2.md`).
- Agent tooling that **exists in source**: ASTDB query bridge
  (`$J/src/query_command.zig`), `janus desugar` canonical-source output
  (`$J/src/janus_main.zig:2500-2604`), MCP server with compile/run/inspect/
  CID/stdlib/oracle tools (`$J/agent/janus-mcp/server.py`). Note: doctrine
  cites `janus query desugar`; dispatch found is `janus desugar` — naming
  honesty gap.
- **Live persistent REPL: NOT FOUND.** `janus-shell` exists but deterministic
  validation is unimplemented (`$J/cmd/janus-shell/shell.zig:96-220`);
  `std/interpreter.zig` is a legacy print-only stub.
- Event inventory exists: `std/stl/event.jan`, `event_codec.jan`, DAG/Merkle
  and memory/LSM stores; README lists coordination replay ledgers
  (`$J/std/stl/`, `$J/std/README.md:96-107`). Full event-sourcing/projection
  semantics not established.
- `.agents/skills/` contains only `ui-ux-pro-max/` — no Janus semantic
  feedback skill ships with the compiler repo.

## Idea map

### 1. Architecture variance is the error category to kill — `[ALREADY CANON]` language level, `[NEW]` app level
- Transcript (1:17:44–1:26:12): Rails gives agents a different solution shape
  per day; Grain gives one. Uniform architecture is the "concrete rock-bottom
  floor" markdown specs cannot provide.
- Janus canon: FEATURE-ADMISSION Gate 5 (no rival idioms), Gate 6 (regularity
  over surface), ARCHITECT-DISCIPLINE §5 (80/20 surface law), closed positions.
- Grain's seven registrations (`defcommand`, `defquery`, `defreadmodel`,
  `defprocessor`, `defperiodic`, `defevent`, `defschemas` — source-verified,
  ObneyAI/grain docs/core-concepts.md) are the model: an app is a bag of
  registered primitives, nothing else.
- Janus form: `:service`-profile stdlib DSL, declarations as `@` metadata +
  comptime registration tables, desugaring to structs + functions. ASTDB makes
  topology queryable — the event model is a query result, not a whiteboard.
- Compose with the **Roc/Joy lessons report** (SPEC-264, proposed): optional
  typed application-kit contract, ordinary functions + optional MVU, bounded
  inspectable update batches, explicit request capabilities. Do not build a
  second app-kit beside it.

### 2. State is lossy compression of history — `[PARTIAL]` substrate exists, protocol discipline missing
- Transcript (52:08): mutable point-in-time state couples read/write models
  and destroys debugging evidence; events are foundational, entities emerge
  from projections. Tar Pit §7.1.1: derivable data is accidental state.
- Janus substrate: BLAKE3 content addressing, Graf checkpoints, Hinge
  transparency log, RFC-022 LSM engine, RFC-023 GrainStore (actor KV —
  unrelated to Cameron's Grain beyond the name), RFC-024 StoreDB,
  `std/stl/event.jan` + codec + replay ledgers.
- Grain mechanics worth stealing (source-verified): two-function store
  protocol (read/append); single events table, tenant/type/time indexes;
  UUIDv7 + one timestamp assigned at append, never client-supplied; reified
  transaction marker event carrying batch event IDs (Datomic-style); CAS
  predicate on append; projections as `{:data state :watermark watermark}`
  with segmented snapshots; polling processors because the log is its own
  backpressure.
- Janus form: event-store protocol over the existing STL/LSM substrate,
  SBI-encoded envelopes, CID-chained batches — "the hash is the law" applied
  to time. The Roc/Joy report already rules the hard part: **replay
  substitutes recorded external results, never reverses payments/writes.**

### 3. The live evaluation loop is the agent's feedback loop — `[PARTIAL]`, highest-leverage sequencing change
- Transcript (17:46–25:05): agent + nREPL + Playwright = self-verifying loop;
  finance-bug anecdote: agent triangulated ledger → projection → exact wrong
  number without guessing. RLM research: symbolic environment for data too
  big for context.
- Janus has the static half (ASTDB queries, desugar, MCP compile/run/inspect)
  but no persistent live session. The isolate runtime (AI-NATIVE §4.2,
  declared primary wedge) and the REPL are the **same artifact**:
  capability-locked evaluation.
- Recommendation: ship the loop as a persistent capability-gated session
  server (extend `janus-mcp` + `janus-shell`, close the deterministic
  validation gap) ahead of `:cluster` distribution. Full fluid `:script`
  stays gated on RFC-002 ratification — the session server does not require
  resolving the AOT/fluid conflict.
- Grain's `code-agent-tools` is the shopping list: install, catalog, schema
  validation, command/query invocation, event inspection, projection rebuild,
  topology/composition validation, runtime-served guides.

### 4. Skills files flip the training-data barrier — `[ALREADY CANON]` direction, `[PARTIAL]` delivery
- Transcript (0:00–4:17): with skills, agents write Haskell/Gleam as happily
  as Java; language innovation is cheap again.
- Janus canon: Monastery, four-layer propagation doctrine, RFC-hinge F2
  agent-native packages (`skills/`, `prompts/`, `bench/`).
- Grain ships skills **in the library repo** (`skills/grain/SKILL.md`,
  `skills/event-model*/SKILL.md`, `.claude-plugin/` + `.codex-plugin/`).
  Janus's compiler repo ships none. Adoption: every stdlib DSL carries its
  own skill + runtime-served guides; toolchain packages carry agent assets
  (RFC-hinge F2 seed).

### 5. Spec→topology→code bridge, runtime-checked — `[NEW]`
- Transcript (1:34:14): Allium behavioral spec → event-model topology → Grain
  primitives, links checked at runtime ("you missed these primitives").
- Source-verified: Allium is implementation-free (`rule … when/requires/
  ensures`); `allium plan` extracts test obligations; `weed` checks drift
  both directions; models compose via SHA-pinned `use`. Grain's strict boot
  guard reconciles registered topology; command→rule, screen→surface links
  required in dev/CI. The bridge is explicitly **LLM-mediated** — do not
  overclaim automation.
- Janus fit: ASTDB identity-over-location makes links stable (UUIDs, not line
  numbers — homoiconicity.md's "hallucination defense"). Types-as-runtime-
  validators (AI-NATIVE §2.1) kill the double bookkeeping Allium+Malli still
  has. Registered topology makes reconciliation a deterministic compiler
  query where Grain needs a boot guard.
- Prior art in-house: AI-native-happiness report proposes inspectable evidence
  classes (declaration/inference/test/measurement/proof) and revision
  rejection — the bridge should emit those evidence classes, not bare diffs.

### 6. Conformance suite as backend contract — `[PARTIAL]` direction adopted, suite missing
- Transcript (36:01): clojure-test-suite lets anyone build a dialect against
  shared behavioral tests; AI made dialects cheap.
- Source-verified: one `.cljc` per core function, reader conditionals for
  legitimate divergence; behavioral evidence, not certification.
- In-house: the **Hejlsberg lessons report already adopted** "port designs,
  not code; reuse upstream conformance oracles; seed readable corpus"
  (Transplant Program). A QTJIR backend conformance suite (one `.jan` corpus,
  golden outputs, per-backend conditionals) is that program applied to
  LLVM/WASM/interpreter — the regularity dividend (Zen §12) made measurable,
  and the honest answer to "does the interpreter match AOT?" before the
  session server ships.

### 7. Small core, slow evolution, community extension — `[ALREADY CANON]`
- Transcript (41:18): Netflix, 10 years, zero breaking Clojure upgrades.
- Janus canon: VERSION-POLICY, RATIFICATION-METHOD, closed positions,
  mechanism-over-policy. Validation, not adoption.

## What NOT to adopt (identity guardrails)

- **Lisp syntax / text homoiconicity.** homoiconicity.md explicitly chose
  structural-relational ASTDB over code-as-lists; the "code is data" benefit
  arrives via queryable AST, not parens.
- **Dynamic schema registry as primary truth.** Janus types survive
  compilation (AI-NATIVE §2.1); schemas are the types, not a parallel malli
  registry.
- **JVM/host dependency.** Borrow mechanisms, never the host (Zen §6).
- **Convention-level enforcement.** Grain's floor is registration + dispatch;
  generated functions remain directly callable (source-verified). Janus can
  make the floor compile-time via profiles + capability gating — that is the
  "rock bottom" the podcast asks for, done properly.
- **Event sourcing as universal identity.** The transcript itself scopes
  Grain to information systems (1:33:02). The event DSL is one stdlib domain
  among the ~100-library plateau (AI-NATIVE §3.3), not the language.

## Haiku Law pre-flight for the new seeds

| Seed | One visible mechanism | One honest lowering | One profile boundary | No abstraction fog |
|---|---|---|---|---|
| Event-store protocol | read/append, CID-chained batches | SBI envelopes over STL event/LSM substrate | `:service`, caps: store read/append | projections are pure reducers; snapshots are events |
| App primitive DSL | `@`-metadata declarations + comptime registry | structs + funcs + dispatch; `janus desugar` shows it | `:service`; composes with the ratified JanusUI SPEC-264 app-kit descriptor | topology = ASTDB query |
| Session server (REPL/isolate) | one capability-locked eval session | existing pipeline + MCP tools | `:script` boundary; caps granted per session | same artifact as AI-isolate, not a second sandbox |
| Backend conformance suite | one `.jan` corpus, golden outputs | same tests on every QTJIR backend | test infra, zero language surface | divergence via conditionals, not forks |

Sequencing per ARCHITECT-DISCIPLINE pain-first: (1) session server — largest
agent-loop pain, static half already built; (2) conformance suite — cheap,
protects regularity, already-adopted direction; (3) event store + app DSL —
build when a real Libertaria information system (Citadel-class) needs it, via
the Advancement Loop, not speculatively. Cheap honesty fix along the way:
align `janus query desugar` doctrine wording with the implemented
`janus desugar` verb (or add the dispatch).

## Prior in-house RFC lessons (compose, don't duplicate)

- **Rust features (2026-10-29):** strengthen view/edit field analysis before
  borrowing syntax; bounded `where` refinements. Proposed, not ratified.
- **Memory safety (2026-09-29):** checked owner-store handles, isolation/
  freeze at concurrency boundaries, explicit lifetimes, no hidden
  clone/ARC/GC. Research proposal.
- **AI-native happiness (2026-09-30):** one readable language + structured
  semantic queries/edits, revision rejection, canonical diffs; evidence
  classes; bounded recoverable experiments. Proposed.
- **Roc/Joy (2026-09-30):** optional typed app-kit, bounded inspectable update
  batches, replay substitutes recorded results. The app-kit is a descriptor
  inside JanusUI SPEC-264 (ratified v0.1.1), not a separate SPEC; the report's
  `_PROPOSED` reference is stale.
- **Hejlsberg (2026-08-23):** verifier-as-product; port designs not code;
  reuse conformance oracles. Adopted program.

## Data gaps

- Grain license inconsistency (MIT root vs EPL-2.0 plugin manifests) —
  resolve before any code graft; mechanism borrowing unaffected.
- Grain production claims are README-level; CI exists, results unchecked.
- Allium↔Grain automatic binding NOT FOUND in public sources; bridge is
  skill-mediated (podcast claim, partially corroborated by Grain skills).
- Janus runtime behavior of query/MCP/desugar surfaces not exercised in this
  synthesis (source inspection only).
- `std/stl` event semantics: established 2026-11-12 by direct read — STL is a
  content-addressed causal ledger (SPEC-064 §S4 invariants, SPEC-088 §S5A
  actor slots, MemStore/LSMStore). Domain layer rides it; no parallel store.

## Follow-through: SPEC package RATIFIED 2026-11-12 (Founder)

Markus requested a SPEC + amendment plan, then approved it the same day:
"APPROVED and RATIFIED!!". Executed on factory-x86 (`LIBERTARIA_STACK/JANUS`):

- **SPEC-271: Live Evaluation Session — RATIFIED v0.1.0**, promoted to
  `janus/.agents/specs/_CURRENT/SPEC-271-live-evaluation-session.md`
  (ratified-awaiting-impl). `[SES-01]`–`[SES-25]`, Gherkin acceptance,
  Anti-Gadget matrix; all seven §10 questions resolved in the ratification
  record. Capability-locked persistent sessions: AOT-cached incremental
  evaluation (no JIT), evidence ledger via SPEC-268, replay by
  recorded-effect substitution, SBI-first + MCP JSON facade, visible
  budgets; reuses SPEC-120 ownership; retires the janus-shell no-op
  validation and print-only interpreter as rival surfaces.
- **Program plan — RATIFIED AS DIRECTION**:
  `janus/.agents/plans/2026-11-12-clojure-adoption-spec-program.md`.
  A2 SPEC-045 Amendment A (session mode) and A3 SPEC-096 Amendment A
  (recorded-effect replay) **RATIFIED 2026-11-12** ("Yes, Approved and
  ratified") and merged into canon: SPEC-045 v1.6.0 §6.3.2
  ([SCRIPT-6.3.A1]–[A5], record §15.6) and SPEC-096 v0.2.0 §7
  ([REPLAY-01]–[06], record §7.1; Axis-8 wording corrected to SPEC-100 v0.2
  axis 2). Artifacts retained in `_AMENDMENT/`; SPEC-096 stays `_FUTURE/`
  per its merge rule. Session contract stack ratified end-to-end.
  A4 STL domain-event layer + projections and A8 app-kit topology (SPEC-264)
  remain consumer-triggered seeds.
- **Batch 2 RATIFIED 2026-11-12** ("batch 2 is ratified! approved"; filed
  8da1f37, ratified 671ee0a): A5 →
  `_AMENDMENT/SPEC-221-229-amendment-A-desugar-surface-reconciliation.md`
  RATIFIED, merge rule executed (FEATURE-ADMISSION + ai-alignment citations
  corrected to `janus desugar`; SPEC-221/229 headers carry binding correction
  lists; SPEC-271 [SES-12] debt CLOSED; stale-comment cleanup rides the next
  compiler lane). A6 → **SPEC-272 Backend Conformance Corpus v0.1.0
  RATIFIED**, promoted to `_CURRENT/` ([CONF-01]–[08]: one corpus,
  independent oracles, LLVM AOT + QTJIR interpreter matrix, WASM
  frozen/excluded, SPEC-053-knob divergence registry; all four §9 questions
  resolved). A7 → `_AMENDMENT/PROPAGATION-amendment-A-skill-assets.md`
  RATIFIED, merge rule executed — propagation doctrine now has FIVE layers
  (skill asset + cold-agent held-out receipt); first required asset:
  `janus-session` skill (drafting unscheduled). **STD-GAP-083 Founder
  ruling**: session taxonomy block 0x0050–0x0057 APPROVED (SPEC-064 minor
  update); status OPEN, execution agent-pickable — codes not yet in
  taxonomy.jan.
- Registrations updated: SPEC-INDEX.md (Newest update + `_CURRENT` row,
  `_PROPOSED` row removed), `_PROPOSED/README.md` (PROMOTED entry), devlog
  `JANUS/agent-reports/2026-11-12-voxis-devlog-spec-271-clojure-adoption-program.md`
  (ratification addendum).
- **EXECUTED 2026-11-12 ("ok go", three lanes)**: STD-GAP-083 taxonomy
  allocation executed + verified in worktree lane
  `feature/voxis/std-gap-083-session-taxonomy` (commit 4520ddbe, pushed):
  8 SessionEventKinds 0x0050–0x0057 in taxonomy.jan + flat smoke (negative
  controls, codec round-trips) + build step test-stl-session-taxonomy;
  session smoke + event regression exit 0 (musl static). SPEC-064 §S5B
  minor record; SPEC-271/096 citations updated. Status
  FIXED_PENDING_PROMOTION (lane merge into active compiler branch pending).
  `janus-session` skill LANDED (.agents/skills/janus-session/):
  repo-validated, syntax probe exit 0, cold-agent held-out rerun PASS 4/4
  (predecessor ambiguity resolved by orchestrator ruling: evaluation
  outcomes 0x0052–0x0055 take the causing evaluation attempt). Desugar
  stub-comment cleanup DONE (janus-lang 59269406, comment-only) —
  [DESUGAR-A4] closed. Records commit 552877b pushed.
- Environment findings: worktree testing needs JANUS_RUNTIME_DIR=$PWD/runtime
  (symlinked binary otherwise resolves main-checkout stdlib → LLVM
  MissingOperand on new variants); NixOS needs musl static or glibc loader;
  flat-main smoke patterns avoid the emitter crash family.
- **PROMOTED 2026-11-12 (Zig 0.17.1)**: STD-GAP-083 CLOSED. The worktree
  compiler-bootstrap blocker (Zig 0.17.0 build-exe SIGSEGV linking libLLVM)
  cleared by Zig 0.17.1 (official tarball sha256-verified to ~/opt/zig-0.17.1;
  fleet nixpkgs pin predates it, PATH zig still 0.17.0). With LLVM_CONFIG +
  JANUS_DYNAMIC_LINKER + ZB_NO_SYSTEMD=1 the worktree compiler builds clean
  and NixOS-runnable; registered test-stl-session-taxonomy zb step green
  (exit 0). Taxonomy lane merged into active compiler branch
  feature/voxis/musl-portable-static-20261026 (de3fc589, pushed); session +
  regression smokes re-verified exit 0 on the active branch. SPEC-271 Phase 3
  (STL sink + replay) unblocked. Records b3445ad + 81698d6 pushed.
- **SPEC-271 Phase 1 execution foundation PROVEN 2026-11-12 (option B,
  Founder decision)**: the ratified contract presupposed an in-process AOT
  mechanism that did not exist (only the forbidden graph interpreter returned
  values in-process; AOT exec'd a subprocess). Founder chose B — build AOT
  in-process execution — over amending the never-JIT clause. Proven + verified
  green under Zig 0.17.1 via registered `test-aot-inproc-smoke`: Janus unit
  AOT-compiled → native object → shared artifact → `std.DynLib` in-process
  load → typed C-ABI call (`janus_double(21)=42`, `janus_add(19,23)=42`), no
  runtime codegen. Lane `feature/voxis/spec271-session-core` 84c559f9 (pushed);
  records 44ecf4d pushed.
- **Runtime-symbol resolution PROVEN 2026-11-12 (Phase-1 body, first
  increment)**: extended the pure-export foundation to runtime-touching units
  (`janus_alloc`/`janus_free`). Two root causes fixed, verified green under
  Zig 0.17.1 BOTH directly and via the registered `test-session-rt-smoke` zb
  step (`sess_pure(21)=42`, `sess_alloc_roundtrip(1234)=1234`, exit 0):
  (a) **PIC across all linked components** — unit via `llc
  -relocation-model=pic`, runtime via `zig build-obj -fPIC`, scheduler asm
  linked; (b) **system dlopen** (`std.c.dlopen`, `-lc`), NOT Zig `std.DynLib`
  — on Linux `std.DynLib` uses a custom `ElfDynLib` loader that does not apply
  PLT `JUMP_SLOT` relocations, so internal cross-function calls segfault
  (proven with a plain-C control). Lane commit 34aecc29 (pushed); records
  0f5306b pushed. Remaining Phase-1 body: session-safe panic (`janus_panic` is
  `noreturn`+`exit`), loader service, CID artifact identity,
  env/budgets/ledger/`janus session` CLI.
- Pending: SPEC-243 `std.session` inventory, remaining SPEC-271 Phase 1 body,
  behavior-level held-out case. Active queue untouched.
- Knowledge: this page + AKF in the LIQUID_COMPUTE shared store (`agents/akf`).
  **Active head: `janus-rt-resolution-20261112-r13`** (published 2026-11-12,
  parent r12): records the Phase-1 runtime-symbol resolution — new decision
  page `knowledge/janus-rt-resolution.md`, refreshed SPEC-271/plan/index
  captures, three runtime-resolution test sources. Isolated readback 23/23
  authenticated, 0 omissions; Mnemos `publish` `outcome: committed`, digest
  `blake3:d25cc46e…8eb7bcf`; live status/get verified; grant restored to
  propose-only. Chain: r5 → r7 → r9 → r10 → r11 → r12 → r13. Native/fabric
  lanes' candidates owe rebase on r13. Repo records: Janus agents repo
  `unstable` e9acca5 + 772e1b4 (A2/A3) + 8da1f37 (batch 2 filed) + 671ee0a
  (batch 2 ratified) + 552877b (execution) + b3445ad (gap CLOSED) + 81698d6
  (index/plan) + 44ecf4d (option-B foundation) + 0f5306b (runtime-resolution),
  all pushed to forge; janus-lang active branch de3fc589 (promotion merge,
  pushed), lanes 4b66d6aa (citation), 4520ddbe (taxonomy), 59269406 (comment
  cleanup), 84c559f9 (option-B foundation), 34aecc29 (runtime-resolution,
  pushed); wiki main (pushed to fork branch wiki-knowledge-20261112);
  LIQUID_COMPUTE agents graf checkpoints 3c9d33a1 (r5) + 97af9503 (r7)
  + 1e625257 (r9) + 117af3f1 (r10) + bdd8ef28 (r11) + cd0c9d11 (r12)
  + df122e3c (r13).