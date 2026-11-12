# Hot Cache

## Active Threads
- **Grain → Janus Haiku: SPEC-271 RATIFIED + PUBLISHED (2026-11-12, Founder)** — synthesis at [[grain-lessons-for-janus-haiku]]. SPEC-271 Live Evaluation Session v0.1.0 ratified, in `_CURRENT` on factory-x86 JANUS, committed+pushed (agents repo unstable e9acca5). Clojure/Grain adoption program ratified as direction; A2/A3 amendments PROPOSED in `_AMENDMENT/`; seeds consumer-triggered. Pending: STL taxonomy allocation, SPEC-243 std.session inventory, A2/A3 ratification. Nothing implemented; queue untouched. AKF r5 `janus-spec-271-adoption-20261112-r5` PUBLISHED in LIQUID_COMPUTE agents/akf (outcome committed, live readback verified, grant restored propose-only); fabric-r3/x86-r6 candidates owe rebase on r5.
- **Lattice break watch (parked 2026-08-06)** — Simon/AWS poly-time quantum DCP preprint filed at [[simon-dcp-polytime-quantum]]; response plan + resurface triggers at [[lattice-break-scenario-skh]]. Reopen when crypto-algo migration starts or the claim is verified.
- **Sober routes retuned 2026-08-06 (VPS + laptop)** — frontier: Kimi k3-256k → DeepSeek v4-pro → Qwen3.8-max (new Alibaba provider, QWEN_API_KEY); daily: DeepSeek v4-flash → MiniMax-M3; security: Kimi k3 → Grok-4.5. Qwen quota exhausted until 08-08.

## Active Infrastructure
- **Hermes + Codex orchestration** — Hermes owns Codex app-server. See [hermes-codex-orchestration.md](hermes-codex-orchestration.md)
- OpenClaw on kimi-coding/k2p5 (no Codex)
- Worker profiles: codex-coder, claude-reviewer, zai-glm
- Kanban board: orchestrator
- **DNS stack rebuilt 2026-07-03** — 3-layer split: Global (ControlD+Quad9) → NM wlan0 (explicit DNS, ignore-auto-dns) → wg1/wg2 link-scope (PostUp/PreDown). See [[dns-sovereignty-stack]] in wiki/infrastructure/. No more manual `resolvectl dns wlan0 …` ritual.
