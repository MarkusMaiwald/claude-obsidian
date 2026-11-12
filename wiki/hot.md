# Hot Cache

## Active Threads
- **Grain → Janus Haiku: program RATIFIED + first execution landed (2026-11-12)** — synthesis at [[grain-lessons-for-janus-haiku]]. Ratified: SPEC-271/045/096 session stack, SPEC-272 corpus, A5 desugar, A7 five-layer propagation. EXECUTED: STD-GAP-083 taxonomy 0x0050–0x0057 in lane feature/voxis/std-gap-083-session-taxonomy (4520ddbe pushed; smokes exit 0 musl; FIXED_PENDING_PROMOTION — lane merge pending); janus-session skill landed (held-out rerun PASS 4/4); desugar stub comments cleaned (59269406). Records 552877b pushed. Env: worktree tests need JANUS_RUNTIME_DIR; NixOS needs musl static. Pending: taxonomy promotion, SPEC-243 inventory, SPEC-271 Phases 1+; seeds A4/A8 consumer-triggered. AKF head r9 (execution refresh pending, propose-only).
- **Lattice break watch (parked 2026-08-06)** — Simon/AWS poly-time quantum DCP preprint filed at [[simon-dcp-polytime-quantum]]; response plan + resurface triggers at [[lattice-break-scenario-skh]]. Reopen when crypto-algo migration starts or the claim is verified.
- **Sober routes retuned 2026-08-06 (VPS + laptop)** — frontier: Kimi k3-256k → DeepSeek v4-pro → Qwen3.8-max (new Alibaba provider, QWEN_API_KEY); daily: DeepSeek v4-flash → MiniMax-M3; security: Kimi k3 → Grok-4.5. Qwen quota exhausted until 08-08.

## Active Infrastructure
- **Hermes + Codex orchestration** — Hermes owns Codex app-server. See [hermes-codex-orchestration.md](hermes-codex-orchestration.md)
- OpenClaw on kimi-coding/k2p5 (no Codex)
- Worker profiles: codex-coder, claude-reviewer, zai-glm
- Kanban board: orchestrator
- **DNS stack rebuilt 2026-07-03** — 3-layer split: Global (ControlD+Quad9) → NM wlan0 (explicit DNS, ignore-auto-dns) → wg1/wg2 link-scope (PostUp/PreDown). See [[dns-sovereignty-stack]] in wiki/infrastructure/. No more manual `resolvectl dns wlan0 …` ritual.
