# Hot Cache

## Active Threads
- **Grain → Janus Haiku: session stack RATIFIED end-to-end + AKF r7 head (2026-11-12, Founder)** — synthesis at [[grain-lessons-for-janus-haiku]]. SPEC-271 v0.1.0 + A2 (SPEC-045 v1.6.0 §6.3.2 session-mode) + A3 (SPEC-096 v0.2.0 §7 recorded-effect replay) all ratified and merged; agents repo unstable e9acca5+772e1b4 pushed. Phase 0 COMPLETE. Pending: STL taxonomy allocation (SPEC-064 §S5A), SPEC-243 std.session inventory; seeds A4–A8 consumer-triggered. Nothing implemented; queue untouched. AKF active head `janus-session-stack-20261112-r7` (parent r5) PUBLISHED in LIQUID_COMPUTE agents/akf — 18/18 readback verified, grant propose-only; native/fabric candidates owe rebase on r7.
- **Lattice break watch (parked 2026-08-06)** — Simon/AWS poly-time quantum DCP preprint filed at [[simon-dcp-polytime-quantum]]; response plan + resurface triggers at [[lattice-break-scenario-skh]]. Reopen when crypto-algo migration starts or the claim is verified.
- **Sober routes retuned 2026-08-06 (VPS + laptop)** — frontier: Kimi k3-256k → DeepSeek v4-pro → Qwen3.8-max (new Alibaba provider, QWEN_API_KEY); daily: DeepSeek v4-flash → MiniMax-M3; security: Kimi k3 → Grok-4.5. Qwen quota exhausted until 08-08.

## Active Infrastructure
- **Hermes + Codex orchestration** — Hermes owns Codex app-server. See [hermes-codex-orchestration.md](hermes-codex-orchestration.md)
- OpenClaw on kimi-coding/k2p5 (no Codex)
- Worker profiles: codex-coder, claude-reviewer, zai-glm
- Kanban board: orchestrator
- **DNS stack rebuilt 2026-07-03** — 3-layer split: Global (ControlD+Quad9) → NM wlan0 (explicit DNS, ignore-auto-dns) → wg1/wg2 link-scope (PostUp/PreDown). See [[dns-sovereignty-stack]] in wiki/infrastructure/. No more manual `resolvectl dns wlan0 …` ritual.
