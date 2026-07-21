# Contributing to Nomo

Thanks for helping Nomo become a small, coherent, and dependable language and
toolchain.

## Before proposing a change

1. Search the relevant repository and the
   [RFC index](https://github.com/nomo-lang/rfcs) for existing work.
2. Use an issue or RFC for changes that affect syntax, semantics, manifests,
   lockfiles, diagnostics, package identity, editor contracts, or stable
   command behavior.
3. Keep the
   [Design Constitution](https://github.com/nomo-lang/rfcs/blob/main/DESIGN-CONSTITUTION.md)
   in view: prefer explicit, testable behavior over hidden convenience.

## Branch and commit policy

- Never develop directly on `main`.
- Create a focused branch such as `feature/<topic>`, `fix/<topic>`, or
  `docs/<topic>`.
- Keep unrelated work in separate pull requests.
- Sign every code commit and every release tag.
- Do not rewrite a shared branch after review has started unless reviewers
  agree.
- Delete merged branches.

## Pull requests

A pull request should:

- explain the user-visible outcome and tradeoffs;
- link the relevant issue or RFC;
- include tests for behavior changes;
- update English and Chinese specifications when language behavior changes;
- update examples, help text, and editor contracts when applicable;
- list the exact validation commands that were run;
- avoid drive-by formatting or unrelated cleanup.

The author is responsible for resolving review threads and keeping CI green.
Development snapshots may use documented release-gate waivers; stable releases
may not waive compatibility, artifact integrity, or installation verification.

## Local validation

Use the repository's own contribution guide and CI workflow as the source of
truth. Common checks include:

```text
cargo fmt --all -- --check
cargo clippy --workspace --all-targets -- -D warnings
cargo test --workspace
pnpm install --frozen-lockfile
pnpm run lint
pnpm test
pnpm run build
```

Run only the commands relevant to the repository you changed, plus any focused
test that proves the new behavior.

## Conduct and security

Participation is governed by the
[Code of Conduct](https://github.com/nomo-lang/.github/blob/main/CODE_OF_CONDUCT.md).
Do not put vulnerability details, credentials, private data, or active exploit
instructions in a public issue. Follow
[SECURITY.md](https://github.com/nomo-lang/.github/blob/main/SECURITY.md)
instead.
