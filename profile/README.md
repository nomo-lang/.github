# Nomo

**Small language. Native programs.**

Nomo is an early-preview programming language for command-line tools,
systems utilities, and controlled services. The compiler lowers Nomo to
readable C99 and native executables; the browser playground uses the same
compiler front end with a bounded WebAssembly executor.

There is no stable `v0.1.0` release. Published `0.0.0-<timestamp>` builds are
development snapshots, and source, standard-library, manifest, and editor
contracts may change between snapshots.

## Start here

- [Website and downloads](https://www.nomo-lang.org)
- [Install-free playground](https://play.nomo-lang.org)
- [Compiler, CLI, standard library, and examples](https://github.com/nomo-lang/nomo)
- [Specifications, RFCs, roadmap, and release evidence](https://github.com/nomo-lang/rfcs)
- [Shared contribution guide](https://github.com/nomo-lang/.github/blob/main/CONTRIBUTING.md)

Current public download: snapshot
[`v0.0.0-20260721120555`](https://github.com/nomo-lang/nomo/releases/tag/v0.0.0-20260721120555).
The syntax shown here was reviewed against compiler commit
[`6acff2b`](https://github.com/nomo-lang/nomo/commit/6acff2bba0113efa3d49254ec2b9c72e1d442b33).
Use the snapshot for packaged binaries and the named commit when reproducing
current `main` behavior.

## Quick start

Install a preview archive for your platform, put `nomo` on `PATH`, then create
and run a project:

```sh
nomo --version
nomo new hello-world
cd hello-world
nomo fmt .
nomo check .
nomo run .
```

The scaffold derives the source module root from `[package].name`.
`hello-world/src/main.nomo` therefore begins:

```nomo
package hello_world

import std.io

fn main() {
    io.println("Hello, Nomo")
}
```

No-return declarations omit `-> void`; the `void` type remains available in
value positions such as `Result<void, E>` and in callable types such as
`task fn(string) -> void`.

## Verified preview capabilities

The current repositories have automated coverage for:

- parsing, type checking, formatting, C99 emission, native linking, and CLI
  project workflows;
- a WebAssembly compiler/runtime path used by the public playground;
- packages, workspaces, deterministic lockfiles, vendoring, and registry
  integrity flows;
- arrays, ordered maps, generics, interfaces, FFI, structured diagnostics, and
  direct-style `suspend` with bounded runtime primitives;
- LSP diagnostics, completion, hover, signatures, navigation, symbols,
  semantic tokens, formatting, and inlay hints;
- syntax support for VS Code, IntelliJ Platform, Zed, and Tree-sitter.

These are implementation and CI claims, not a production-readiness claim.
Platform coverage, performance, ecosystem depth, API stability, and external
adoption remain preview gates.

## Repository map

| Repository | Responsibility | Primary validation |
| --- | --- | --- |
| [`nomo`](https://github.com/nomo-lang/nomo) | Compiler, C99/WASM backends, runtime, CLI, formatter, docs, package tooling, standard library | Rust workspace, C99/WASM, examples, release gates |
| [`nomo-lsp`](https://github.com/nomo-lang/nomo-lsp) | Language server pinned to a compiler revision | Rust tests, Clippy, release gate |
| [`nomo-playground`](https://github.com/nomo-lang/nomo-playground) | Browser compiler and bounded executor | Vitest, Svelte check, Cloudflare build |
| [`tree-sitter-nomo`](https://github.com/nomo-lang/tree-sitter-nomo) | Incremental grammar and queries | Grammar corpus and binding tests |
| [`vscode-nomo`](https://github.com/nomo-lang/vscode-nomo) | VS Code syntax and LSP client | Contract tests, build, VSIX packaging |
| [`intellij-nomo`](https://github.com/nomo-lang/intellij-nomo) | IntelliJ fallback lexer and LSP integration | Gradle tests and plugin verification |
| [`zed-nomo`](https://github.com/nomo-lang/zed-nomo) | Zed extension and grammar pin | Rust tests and WASM build |
| [`setup-nomo`](https://github.com/nomo-lang/setup-nomo) | Checksum-verifying GitHub Action installer | Action tests and smoke workflows |
| [`www.nomo-lang.org`](https://github.com/nomo-lang/www.nomo-lang.org) | Public website and localized entry docs | Vitest, Svelte check, Cloudflare build |
| [`rfcs`](https://github.com/nomo-lang/rfcs) | Normative specifications, RFC governance, roadmap, release evidence | Metadata, bilingual sync, links |
| [`awesome`](https://github.com/nomo-lang/awesome) | Curated ecosystem index | Link and curation review |
| [`.github`](https://github.com/nomo-lang/.github) | Organization profile, policies, templates, reusable CI | Community-file validation |

## Compatibility and authority

When sources disagree, use this order:

1. accepted English and Chinese specifications in `rfcs`;
2. accepted RFCs with implementation evidence;
3. compiler tests and released CLI behavior;
4. repository READMEs and examples;
5. the non-normative whitepaper and historical material.

For module roots and canonical no-return declarations, start with
[RFC 0021](https://github.com/nomo-lang/rfcs/blob/main/en/0021-module-system-imports.md)
and
[RFC 0041](https://github.com/nomo-lang/rfcs/blob/main/en/0041-implicit-void-return-omission.md).
Both remain governed by their separately recorded decision and implementation
statuses.

## Boundaries

Nomo is suitable for experimentation, compiler/tooling development, and
controlled preview workloads. Do not infer stable language compatibility,
production TLS service readiness, unbounded concurrency safety, or mature
third-party package availability from internal tests alone. Review the
[release gate](https://github.com/nomo-lang/rfcs/blob/main/RELEASE-GATE.md)
before making a readiness claim.

## Contributing and releasing

Changes are developed on focused branches and merged through pull requests.
Code commits and release tags must be signed. Syntax, semantic, manifest,
diagnostic, or public CLI changes require an RFC before implementation and
must update affected compiler, LSP, grammar, editor, example, and documentation
surfaces.

This repository validates its organization entry points with:

```sh
git show --check --oneline --no-renames HEAD
cmp --silent README.md profile/README.md
```

Public releases must follow the shared
[release integrity policy](https://github.com/nomo-lang/.github/blob/main/RELEASING.md).
Report sensitive issues through
[SECURITY.md](https://github.com/nomo-lang/.github/blob/main/SECURITY.md), not a
public issue.
