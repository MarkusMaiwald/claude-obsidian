# Hot Cache

## Active Threads
- **Grain → Janus Haiku: taxonomy PROMOTED + CLOSED under Zig 0.17.1 (2026-11-12)** — synthesis at [[grain-lessons-for-janus-haiku]]. STD-GAP-083 CLOSED: blocker (Zig 0.17.0 build-exe SIGSEGV linking libLLVM) cleared by Zig 0.17.1 (official tarball ~/opt/zig-0.17.1, sha256-verified; fleet nixpkgs predates it, PATH zig still 0.17.0). Registered zb step green; taxonomy merged into active compiler branch feature/voxis/musl-portable-static-20261026 (de3fc589 pushed); smokes re-verified exit 0. SPEC-271 Phase 3 unblocked. Records b3445ad+81698d6 pushed. Ratified stack: SPEC-271/045/096, SPEC-272, A5, A7; janus-session skill landed (held-out PASS 4/4). Pending: SPEC-243 inventory, SPEC-271 Phases 1+, behavior-level held-out; seeds A4/A8 consumer-triggered. AKF head r10 (promotion refresh pending, propose-only).
- **Lattice break watch (parked 2026-08-06)** — Simon/AWS poly-time quantum DCP preprint filed at [[simon-dcp-polytime-quantum]]; response plan + resurface triggers at [[lattice-break-scenario-skh]]. Reopen when crypto-algo migration starts or the claim is verified.
- **Sober routes retuned 2026-08-06 (VPS + laptop)** — frontier: Kimi k3-256k → DeepSeek v4-pro → Qwen3.8-max (new Alibaba provider, QWEN_API_KEY); daily: DeepSeek v4-flash → MiniMax-M3; security: Kimi k3 → Grok-4.5. Qwen quota exhausted until 08-08.

## Active Infrastructure
- **Hermes + Codex orchestration** — Hermes owns Codex app-server. See [hermes-codex-orchestration.md](hermes-codex-orchestration.md)
- OpenClaw on kimi-coding/k2p5 (no Codex)
- Worker profiles: codex-coder, claude-reviewer, zai-glm
- Kanban board: orchestrator
- **DNS stack rebuilt 2026-07-03** — 3-layer split: Global (ControlD+Quad9) → NM wlan0 (explicit DNS, ignore-auto-dns) → wg1/wg2 link-scope (PostUp/PreDown). See [[dns-sovereignty-stack]] in wiki/infrastructure/. No more manual `resolvectl dns wlan0 …` ritual.
