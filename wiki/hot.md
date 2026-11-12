# Hot Cache

## Active Threads
- **Grain → Janus Haiku: SPEC-271 Phase-1 runtime-symbol resolution PROVEN, AKF r12 head (2026-11-12)** — synthesis at [[grain-lessons-for-janus-haiku]]. Runtime-touching units (janus_alloc/janus_free) now execute in-process. Two root causes fixed, verified green under Zig 0.17.1 BOTH directly and via registered test-session-rt-smoke (sess_pure(21)=42, sess_alloc_roundtrip(1234)=1234, exit 0): (a) PIC across all linked components (unit llc -relocation-model=pic, runtime zig build-obj -fPIC, scheduler asm); (b) SYSTEM dlopen (std.c.dlopen, -lc) NOT Zig std.DynLib — on Linux std.DynLib uses a custom ElfDynLib loader that skips PLT JUMP_SLOT relocations (proven with plain-C control). Lane 34aecc29 pushed; records 0f5306b pushed. Prior: option-B pure foundation 84c559f9; STD-GAP-083 CLOSED (de3fc589). Remaining Phase-1 body: session-safe panic (janus_panic noreturn+exit), loader service, CID artifact identity, env/budgets/ledger/CLI. AKF head r12 (runtime-resolution refresh pending, propose-only); native/fabric owe rebase on r12.
- **Lattice break watch (parked 2026-08-06)** — Simon/AWS poly-time quantum DCP preprint filed at [[simon-dcp-polytime-quantum]]; response plan + resurface triggers at [[lattice-break-scenario-skh]]. Reopen when crypto-algo migration starts or the claim is verified.
- **Sober routes retuned 2026-08-06 (VPS + laptop)** — frontier: Kimi k3-256k → DeepSeek v4-pro → Qwen3.8-max (new Alibaba provider, QWEN_API_KEY); daily: DeepSeek v4-flash → MiniMax-M3; security: Kimi k3 → Grok-4.5. Qwen quota exhausted until 08-08.

## Active Infrastructure
- **Hermes + Codex orchestration** — Hermes owns Codex app-server. See [hermes-codex-orchestration.md](hermes-codex-orchestration.md)
- OpenClaw on kimi-coding/k2p5 (no Codex)
- Worker profiles: codex-coder, claude-reviewer, zai-glm
- Kanban board: orchestrator
- **DNS stack rebuilt 2026-07-03** — 3-layer split: Global (ControlD+Quad9) → NM wlan0 (explicit DNS, ignore-auto-dns) → wg1/wg2 link-scope (PostUp/PreDown). See [[dns-sovereignty-stack]] in wiki/infrastructure/. No more manual `resolvectl dns wlan0 …` ritual.
