## Wise.Est Systems

Verifiable correctness and governance discipline for systems that change real things.

**Live:** [truth.systems](https://truth.systems) — drop a file, get the truth · [proofs.systems](https://proofs.systems) — how the proofs work

Our public stack is four repositories in three layers:

- [**wop**](https://github.com/Wise-Est-Systems/wop) — WISEATA / WiseDigest-3 primitives. The deterministic hash function and structural-processing math the protocol depends on. Apache-2.0, tagged.
- [**wiseorder-protocol**](https://github.com/Wise-Est-Systems/wiseorder-protocol) — governance kernel + hash-chained audit memory + conformance vectors + three-language verifiers. Apache-2.0, pre-v0.1.0.
- [**wiseorder**](https://github.com/Wise-Est-Systems/wiseorder) — event-driven operational runtime. One workflow: commit → summarize → draft → human approval. Apache-2.0, pre-v0.1.0.
- [**winstack-network**](https://github.com/Wise-Est-Systems/winstack-network) — **WIN**, the Wise Independent Network: `.win` files that prove themselves. Portable, offline-verifiable file-integrity proofs. Try it at [truth.systems](https://truth.systems). MIT.

Everything else under this org is either an archived predecessor or a pre-canonical experiment. Pinned repos above are the canonical set.

### What we do not do

- We do not ship general-purpose AI agents. The protocol governs action, it does not act.
- We do not host data. Every verifier in our stack runs offline against local files.
- We do not claim cryptographic primitives are externally audited until they are. WiseDigest-3 cryptanalysis is deferred and documented as such in [wop](https://github.com/Wise-Est-Systems/wop).

### Operating discipline

- Real code, real tests, real CI. No pseudocode. No "TODO: implement later" in load-bearing paths.
- Every claim in a README is backed by a test, a workflow run, or a verifiable artifact in the repo.
- Conformance is class-scoped: an implementation can claim conformance for a subset of regimes; the spec defines what each one means.
- External validation status (`NOT_COMPLETE` / `COMPLETE`) is published in each repo's release packet. We do not call first-party verifier tracks "externally validated."

### Status

| repo                | maturity         | license     | CI         |
|---|---|---|---|
| wop                 | tagged v0.1.x    | Apache-2.0  | ✅ |
| wiseorder-protocol  | pre-v0.1.0       | Apache-2.0  | ✅ tests · conformance · verify-chain · lint |
| wiseorder           | pre-v0.1.0       | Apache-2.0  | ✅ tests · lint · migration-check |
| winstack-network    | working on main  | MIT         | ✅ CI · WASM · audit |

### Architecture

```
                       Wise.Est Systems
                              │
                              ▼
                    ┌──────────────────┐
                    │    WiseOrder     │   ← framework
                    └──────────────────┘
                              │
            ┌─────────────────┼─────────────────┐
            ▼                 ▼                 ▼
       SPEC / KERNEL      RUNTIME            IMPLEMENTATIONS
       ─────────────      ───────            ───────────────
       wiseorder-         wiseorder          winstack-network
       protocol           (Python,           (Rust crates +
       (canon, vectors,   commit→approval)   WASM verifier +
        Go + Rust                            desktop drop)
        verifiers, audit
        chain)                               wop / WISEATA
                                             (research primitives,
                                              WiseDigest-3,
                                              cryptanalysis fleet)
```

### Drift control

Each canonical repo carries a `STACK_ROLE.md` declaring its layer and non-goals. The SHA-256 fingerprint of every `STACK_ROLE.md` is recorded in [`wiseorder-protocol/STRUCTURE.md`](https://github.com/Wise-Est-Systems/wiseorder-protocol/blob/main/STRUCTURE.md) and verified by CI on every push, both in the publishing repo and in `wiseorder-protocol`'s daily cross-stack verifier. A change to a repo's role is a pull request against `STRUCTURE.md`. Drift fails CI.

### Roadmap

Dates are commitments, not estimates. Misses get logged here with a new date and a one-line reason. Hits get logged with the closing commit SHA. Both are public.

| target     | what ships                                                                                                          | status |
|---|---|---|
| 2026-06-15 | `wiseorder-protocol` v0.1.0 audit bundle published; conformance vector set frozen                                   | open |
| 2026-07-15 | `wiseorder` v0.1.0 — operational runtime hardened end-to-end (Postgres + Redis + Chroma; `commit_pipeline`)         | open |
| 2026-09-01 | `winstack-network` v0.2.0 — public WASM verifier hosted; macOS + Windows drop-target builds                         | open |
| 2026-10-01 | First external conformance run by a non-Wise.Est party; result (`PASS` / `FAIL`) published verbatim                 | open |
| 2026-12-01 | `wop` v0.2.0 — WiseDigest-3 cryptanalysis status update; second external review track invited                       | open |

### Who built this

Built by **Henry Wayne Wise III**, working solo. Day job: pipe-fitter on a US data center build. Started 2026.

Licenses are chosen per repo: Apache-2.0 on the kernel (`wiseorder-protocol`), the runtime (`wiseorder`), and the primitives (`wop`) so contributions return to the commons; MIT on the production `.win` implementation (`winstack-network`) so any receiver can vendor the verifier without obligation.

Contact: GitHub issues for non-sensitive bugs; `security@truth.systems` for vulnerability reports per each repo's `SECURITY.md`. No public chat, no Discord server, no announcements list. Everything ships via the dated roadmap above; misses get logged in the same place.
