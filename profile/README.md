## Wise.Est Systems

Verifiable correctness and governance discipline for systems that change real things.

Our public stack is four repositories in three layers:

- [**wop**](https://github.com/Wise-Est-Systems/wop) — WISEATA / WiseDigest-3 primitives. The deterministic hash function and structural-processing math the protocol depends on. Apache-2.0, tagged.
- [**wiseorder-protocol**](https://github.com/Wise-Est-Systems/wiseorder-protocol) — governance kernel + hash-chained audit memory + conformance vectors + three-language verifiers. Private during pre-v0.1.0 packaging; reviewer access on request.
- [**wiseorder**](https://github.com/Wise-Est-Systems/wiseorder) — event-driven operational runtime. One workflow: commit → summarize → draft → human approval. Private during pre-v0.1.0.
- [**winstack-network**](https://github.com/Wise-Est-Systems/winstack-network) — `.win` tags: files that prove themselves. Portable, offline-verifiable file-integrity proofs. MIT.

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
