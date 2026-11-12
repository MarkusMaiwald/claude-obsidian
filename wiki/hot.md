# Hot Cache

## Active Threads
- **Grain → Janus Haiku: session stack RATIFIED + batch 2 filed (2026-11-12)** — synthesis at [[grain-lessons-for-janus-haiku]]. Ratified: SPEC-271 v0.1.0 + SPEC-045 v1.6.0 §6.3.2 + SPEC-096 v0.2.0 §7 (Phase 0 COMPLETE; commits e9acca5+772e1b4). Batch 2 PROPOSED (8da1f37): SPEC-272 backend conformance corpus, A5 desugar reconciliation, A7 skill-assets propagation layer, STD-GAP-083 taxonomy request (NEEDS_RULING, blocks SPEC-271 Phase 3 only). Awaiting Founder ratification of batch 2; seeds A4/A8 consumer-triggered. Nothing implemented; queue untouched. AKF head `janus-session-stack-20261112-r7` (18/18 verified, propose-only); batch-2 AKF refresh awaits ratification; native/fabric candidates owe rebase on r7.
- **Lattice break watch (parked 2026-08-06)** — Simon/AWS poly-time quantum DCP preprint filed at [[simon-dcp-polytime-quantum]]; response plan + resurface triggers at [[lattice-break-scenario-skh]]. Reopen when crypto-algo migration starts or the claim is verified.
- **Sober routes retuned 2026-08-06 (VPS + laptop)** — frontier: Kimi k3-256k → DeepSeek v4-pro → Qwen3.8-max (new Alibaba provider, QWEN_API_KEY); daily: DeepSeek v4-flash → MiniMax-M3; security: Kimi k3 → Grok-4.5. Qwen quota exhausted until 08-08.

## Active Infrastructure
- **Hermes + Codex orchestration** — Hermes owns Codex app-server. See [hermes-codex-orchestration.md](hermes-codex-orchestration.md)
- OpenClaw on kimi-coding/k2p5 (no Codex)
- Worker profiles: codex-coder, claude-reviewer, zai-glm
- Kanban board: orchestrator
- **DNS stack rebuilt 2026-07-03** — 3-layer split: Global (ControlD+Quad9) → NM wlan0 (explicit DNS, ignore-auto-dns) → wg1/wg2 link-scope (PostUp/PreDown). See [[dns-sovereignty-stack]] in wiki/infrastructure/. No more manual `resolvectl dns wlan0 …` ritual.
