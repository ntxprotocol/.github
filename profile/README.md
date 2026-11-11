# NTX — Network Text Exchange

**An open protocol for sending text, not video, between apps on a local network.**

Think of it as NDI, but for text. One app (a lyrics app, a scripture detector, a scoreboard…)
sends text. Other apps (presentation software, video mixers, streaming tools…) receive it and
show it with **their own templates and styling**.

> **Status: early.** The specification is NTX 0.1 Pre-Draft. Everything may still change.

## Repositories

| Repo | What it is | Status |
| --- | --- | --- |
| [spec](https://github.com/ntxprotocol/spec) | The specification, JSON Schemas, and examples | Pre-Draft (0.1) |
| `ntx` | Rust core, C ABI, and language wrappers | Planned |
| `client` | Monitor app, web playground, and bridges | Planned |
| `obs-ntx` | OBS Studio plugin | Planned |
| `ntx-web` | TypeScript browser SDK | Planned |
| `conformance` | Conformance test suite | Planned |
| `brand` | Name and logo files | Planned |

## Get involved

- Read the [spec](https://github.com/ntxprotocol/spec) and tell us what your app needs.
- Questions and ideas: open an issue in the repo it relates to. See [SUPPORT.md](../SUPPORT.md).
- Changes: see [CONTRIBUTING.md](../CONTRIBUTING.md). Contributions need a DCO sign-off (`git commit -s`).
- Be kind: [Code of Conduct](../CODE_OF_CONDUCT.md).

## Licences

- Code repositories: **MIT OR Apache-2.0**.
- OBS plugin (`obs-ntx`): **GPL-2.0-or-later**.
- Specification: **Community Specification License 1.0**.
- Type files: **CC0**.

Copyright © 2026 CamelCase Technologies Ltd and the NTX contributors.
