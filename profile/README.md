# Nomo

**Small language. Native programs.**

Nomo is a small, explicit programming language for systems tools,
command-line programs, and small services. Nomo source is lowered to readable
C99 and compiled into native executables with the platform C compiler.

The project is in active development. Published snapshots are prereleases and
do not carry a compatibility promise between timestamps.

## Start here

- [Read the language and tooling overview](https://github.com/nomo-lang/nomo)
- [Try the browser playground](https://github.com/nomo-lang/nomo-playground)
- [Review accepted and proposed RFCs](https://github.com/nomo-lang/rfcs)
- [Download the current preview](https://github.com/nomo-lang/nomo/releases/tag/v0.0.0-20260720080715)
- [Inspect the release evidence](https://github.com/nomo-lang/rfcs/blob/main/releases/v0.0.0-20260720080715/RELEASE.md)

```nomo
package app.main

import std.io

fn main() -> void {
    io.println("Hello, Nomo")
}
```

## Toolchain

| Project | Purpose |
| --- | --- |
| [`nomo`](https://github.com/nomo-lang/nomo) | Compiler, C99 backend, project tooling, package manager, formatter, docs, and standard library |
| [`nomo-lsp`](https://github.com/nomo-lang/nomo-lsp) | Language server and editor-facing semantic services |
| [`tree-sitter-nomo`](https://github.com/nomo-lang/tree-sitter-nomo) | Tree-sitter grammar |
| [`vscode-nomo`](https://github.com/nomo-lang/vscode-nomo) | Visual Studio Code extension |
| [`zed-nomo`](https://github.com/nomo-lang/zed-nomo) | Zed extension |
| [`intellij-nomo`](https://github.com/nomo-lang/intellij-nomo) | IntelliJ Platform plugin |
| [`setup-nomo`](https://github.com/nomo-lang/setup-nomo) | Checksum-verifying GitHub Action installer |
| [`rfcs`](https://github.com/nomo-lang/rfcs) | Language design, specifications, roadmap, and release policy |

## Design principles

- Nomo is small before it is powerful.
- Nomo favors explicitness over magic.
- Nomo has no null and no exceptions.
- Nomo is immutable by default.
- Nomo compiles to inspectable native code.
- Nomo grows through RFCs, examples, and tests.

Read the complete
[Nomo Design Constitution](https://github.com/nomo-lang/rfcs/blob/main/DESIGN-CONSTITUTION.md).

## Contributing

Changes are developed on focused branches and merged through pull requests.
Code commits and release tags must be signed. Start with the shared
[contribution guide](https://github.com/nomo-lang/.github/blob/main/CONTRIBUTING.md)
and then follow the repository-specific checks in the project you are
changing.

Please report security-sensitive issues using the process in
[SECURITY.md](https://github.com/nomo-lang/.github/blob/main/SECURITY.md).
