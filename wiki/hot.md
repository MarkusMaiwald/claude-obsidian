# Hot Cache

## Active Threads
- **Grain → Janus Haiku: SPEC-271 Phase-1 session-safe panic PROVEN, AKF r13 head (2026-11-12)** — synthesis at [[grain-lessons-for-janus-haiku]]. A panicking unit no longer kills the host: janus_panic is an EXTERNAL call + no runtime hook, so NO compiler change — localize the runtime fatal panic symbols (objcopy) and resolve unit panic calls against a setjmp/longjmp recovery shim (sess_try_call). Verified green under Zig 0.17.1 (direct smoke exit 0): sess_ok(21)=42, sess_alloc_rt(1234)=1234, sess_panics recovered (msg "unwrap called on None optional", rc=1), post-recovery sess_ok(10)=20 — host survived + kept evaluating. Lane cfbad507 pushed; records 49d86a6 pushed; step test-session-panic-smoke. Prior: runtime-resolution 34aecc29 (PIC + system dlopen, NOT std.DynLib ElfDynLib); option-B foundation 84c559f9; STD-GAP-083 CLOSED de3fc589. Remaining Phase-1 body: loader service, CID artifact identity, env/budgets/ledger/CLI. AKF head r13 (panic refresh pending, propose-only); native/fabric owe rebase on r13.
- **Lattice break watch (parked 2026-08-06)** — Simon/AWS poly-time quantum DCP preprint filed at [[simon-dcp-polytime-quantum]]; response plan + resurface triggers at [[lattice-break-scenario-skh]]. Reopen when crypto-algo migration starts or the claim is verified.
- **Sober routes retuned 2026-08-06 (VPS + laptop)** — frontier: Kimi k3-256k → DeepSeek v4-pro → Qwen3.8-max (new Alibaba provider, QWEN_API_KEY); daily: DeepSeek v4-flash → MiniMax-M3; security: Kimi k3 → Grok-4.5. Qwen quota exhausted until 08-08.

## Active Infrastructure
- **Hermes + Codex orchestration** — Hermes owns Codex app-server. See [hermes-codex-orchestration.md](hermes-codex-orchestration.md)
- OpenClaw on kimi-coding/k2p5 (no Codex)
- Worker profiles: codex-coder, claude-reviewer, zai-glm
- Kanban board: orchestrator
- **DNS stack rebuilt 2026-07-03** — 3-layer split: Global (ControlD+Quad9) → NM wlan0 (explicit DNS, ignore-auto-dns) → wg1/wg2 link-scope (PostUp/PreDown). See [[dns-sovereignty-stack]] in wiki/infrastructure/. No more manual `resolvectl dns wlan0 …` ritual.
