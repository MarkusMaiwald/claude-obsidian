# Hot Cache

## Active Threads
- **Grain → Janus Haiku: SPEC-271 Phase-1 execution foundation PROVEN (option B), AKF r11 head (2026-11-12)** — synthesis at [[grain-lessons-for-janus-haiku]]. Founder chose B (build AOT in-process execution) over amending never-JIT: ratified contract presupposed an in-process AOT mechanism that didn't exist. Proven + verified green under Zig 0.17.1 via registered test-aot-inproc-smoke: AOT object → shared artifact → std.DynLib in-process load → typed call (double=42, add=42), no runtime codegen. Lane feature/voxis/spec271-session-core 84c559f9 pushed; records 44ecf4d pushed. Prior: STD-GAP-083 CLOSED (taxonomy promoted de3fc589); ratified stack SPEC-271/045/096/272, A5, A7; janus-session skill held-out PASS 4/4. Remaining Phase-1 body: loader service, session-safe panic/runtime-symbol resolution, PIC, CID artifact identity, env/budgets/ledger/CLI. Pending: SPEC-243 inventory, behavior-level held-out; seeds A4/A8 consumer-triggered. AKF r11 head (option-B refresh pending, propose-only).
- **Lattice break watch (parked 2026-08-06)** — Simon/AWS poly-time quantum DCP preprint filed at [[simon-dcp-polytime-quantum]]; response plan + resurface triggers at [[lattice-break-scenario-skh]]. Reopen when crypto-algo migration starts or the claim is verified.
- **Sober routes retuned 2026-08-06 (VPS + laptop)** — frontier: Kimi k3-256k → DeepSeek v4-pro → Qwen3.8-max (new Alibaba provider, QWEN_API_KEY); daily: DeepSeek v4-flash → MiniMax-M3; security: Kimi k3 → Grok-4.5. Qwen quota exhausted until 08-08.

## Active Infrastructure
- **Hermes + Codex orchestration** — Hermes owns Codex app-server. See [hermes-codex-orchestration.md](hermes-codex-orchestration.md)
- OpenClaw on kimi-coding/k2p5 (no Codex)
- Worker profiles: codex-coder, claude-reviewer, zai-glm
- Kanban board: orchestrator
- **DNS stack rebuilt 2026-07-03** — 3-layer split: Global (ControlD+Quad9) → NM wlan0 (explicit DNS, ignore-auto-dns) → wg1/wg2 link-scope (PostUp/PreDown). See [[dns-sovereignty-stack]] in wiki/infrastructure/. No more manual `resolvectl dns wlan0 …` ritual.
