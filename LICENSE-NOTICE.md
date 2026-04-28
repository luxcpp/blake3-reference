# LICENSE-NOTICE — luxcpp/blake3-reference

Snapshot of [BLAKE3-team/BLAKE3](https://github.com/BLAKE3-team/BLAKE3) at
release v1.5.0 — the official BLAKE3 reference implementation.

| Field      | Value                                                    |
| ---------- | -------------------------------------------------------- |
| Upstream   | https://github.com/BLAKE3-team/BLAKE3                    |
| Pinned     | tag `1.5.0` (upstream) → re-tagged `v1.5.0` here         |
| License    | Dual-licensed CC0-1.0 OR Apache-2.0 (with LLVM exception |
|            | for the LLVM-derived assembly files)                     |
| SPDX       | `SPDX-License-Identifier: CC0-1.0 OR Apache-2.0`         |
|            | (assembly files: `CC0-1.0 OR Apache-2.0 WITH LLVM-exception`) |
| Tag        | `v1.5.0`                                                 |

## Why a fork

luxcpp/crypto/blake3 ships a first-party BLAKE3 implementation in
`cpp/blake3.cpp`. The reference C tree from this fork is FetchContent'd by
luxcpp/crypto and built as the `blake3_reference` OBJECT library, used as a
byte-equality oracle for the KAT test corpus (35 input lengths × 4 modes,
matching upstream `test_vectors/test_vectors.json`).

Pinning to a specific upstream release tag guarantees reproducible KAT
oracles across CI hosts and audits.

## Tag policy

* Semver tags mirroring upstream: `v1.5.0`, `v1.6.0`, etc.
* No `latest` / no `master` consumption — luxcpp/crypto pins by tag.
* New tags are cut only after BLAKE3 KATs in luxcpp/crypto pass against the
  new tree.

## Updating

1. `git fetch upstream master`
2. Check for new upstream release tag.
3. Audit the diff against upstream changelog.
4. Run `ctest -R blake3` against the candidate.
5. Tag the corresponding `vX.Y.Z` (matching upstream) only after KATs pass.

The dual CC0 / Apache-2.0 license means upstream attribution is preferred but
not legally required. This notice exists so the provenance and licensing
status are unambiguous.
