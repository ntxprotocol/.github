<!-- markdownlint-disable-file MD013 MD033 MD041 -- centred logo and badge links in HTML -->
<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="assets/ntx-lockup-reverse.svg">
    <img src="assets/ntx-lockup.svg" alt="NTX — Network Text Exchange" height="64">
  </picture>
</p>

<p align="center">
  <strong>An open protocol for sending text, not video, between apps on a local network.</strong>
</p>

<p align="center">
  <a href="https://github.com/ntxprotocol/spec"><img alt="Spec: NTX 0.1 Pre-Draft" src="https://img.shields.io/badge/spec-0.1%20pre--draft-0B7A72"></a>
  <a href="https://github.com/ntxprotocol/ntx/actions/workflows/ci.yml"><img alt="Core CI" src="https://github.com/ntxprotocol/ntx/actions/workflows/ci.yml/badge.svg"></a>
  <a href="https://github.com/ntxprotocol/.github/blob/main/CODE_STANDARDS.md"><img alt="Coverage target at least 90%" src="https://img.shields.io/badge/coverage%20target-%E2%89%A590%25-0B7A72"></a>
  <a href="https://github.com/ntxprotocol/.github/blob/main/CONTRIBUTING.md"><img alt="Contributions welcome" src="https://img.shields.io/badge/contributions-welcome-0B7A72"></a>
</p>

## What is NTX?

Think of it as **NDI, but for text**. One app sends text (a lyrics app, a scripture detector, a
scoreboard, a caption tool). Other apps receive it (presentation software, video mixers,
streaming tools) and show it with **their own templates and styling**, exactly as if someone had
typed it in.

```json
{ "op": "update", "channel": "program", "seq": 42, "type": "ntx.text",
  "fields": { "text": "Amazing grace, how sweet the sound" } }
```

- **Text, not pictures of text.** Fonts, layouts and transitions stay in the receiving app.
- **Use-case neutral.** Any JSON fields; shared types such as `ntx.text` keep strangers' apps compatible.
- **Live-ready.** Full state on connect, ordered updates, on-air tally, automatic reconnect.
- **Finds itself.** mDNS discovery on the local network, with a manual address when needed.
- **Open.** An open specification with a royalty-free patent commitment, and permissive code.

### Words you will meet

| Word | Meaning |
| --- | --- |
| **Source** | The app that sends text (for example a lyrics or scripture app). |
| **Receiver** | The app that shows it (presentation software, OBS, vMix…). |
| **Channel** | `program` is what is on air now; `preview` is what comes next. |
| **Tally** | The receiver telling the source "your text is on air". |
| **Publisher / relay** | A web page sends through a relay app on its own computer, which serves it as a source. |
| **Binding** | Wiring a receiver's text box to a field such as `text` or `{reference} · {version}`. |

## Try it

Install [Rust](https://rustup.rs), then send text from one terminal and receive it in another:

```bash
git clone https://github.com/ntxprotocol/ntx && cd ntx
cargo run -p ntx-cli -- send --name Test          # type lines and press Enter
cargo run -p ntx-cli -- recv 127.0.0.1 --field text   # in a second terminal
```

On two computers, run `cargo run -p ntx-cli -- list` to find the sender's address. More in the
[ntx README](https://github.com/ntxprotocol/ntx#try-it).

## Repositories

| Repository | What it is | Status |
| --- | --- | --- |
| [**spec**](https://github.com/ntxprotocol/spec) | The specification, JSON Schemas and examples | 0.1 Pre-Draft |
| [**ntx**](https://github.com/ntxprotocol/ntx) | Rust core library, C library (`ntx.h`) and the `ntx` test tool | Early development |
| Python bindings | `pip install ntx-protocol`, import `ntxprotocol` (in the ntx repo) | In review |
| `client` | Desktop app: monitor, playground, custom types and bridges (FreeShow, OBS, vMix, files, OSC) | Early development, not public yet |
| `ntx-web` | TypeScript SDK for web pages (`@ntxprotocol/web`) | Early development, not public yet |
| `conformance` | Conformance test suite behind "NTX compatible" | Early development, not public yet |
| Node, Java and .NET bindings | On top of the C library | Planned |
| `obs-ntx` | Native OBS Studio plugin | Planned |

Nothing is published to crates.io, PyPI or npm yet.

## Get involved

- **Read the [spec](https://github.com/ntxprotocol/spec)** and tell us what your app needs.
- **Building a presentation, broadcast or streaming app?** Open an issue: we want to hear from you early.
- **Questions:** see [SUPPORT.md](https://github.com/ntxprotocol/.github/blob/main/SUPPORT.md).
- **Contributing:** see [CONTRIBUTING.md](https://github.com/ntxprotocol/.github/blob/main/CONTRIBUTING.md)
  and the [code standards](https://github.com/ntxprotocol/.github/blob/main/CODE_STANDARDS.md).
  Every commit needs a DCO sign-off (`git commit -s`).
- **Security:** see [SECURITY.md](https://github.com/ntxprotocol/.github/blob/main/SECURITY.md).
- **Be kind:** [Code of Conduct](https://github.com/ntxprotocol/.github/blob/main/CODE_OF_CONDUCT.md).

## Licences

| What | Licence |
| --- | --- |
| Specification | Community Specification License 1.0 (royalty-free patent commitment) |
| Code | MIT OR Apache-2.0 (scripts in the spec repository: MIT; the OBS plugin will be GPL-2.0-or-later) |
| Shared type files and examples | CC0 1.0 |
| The NTX name and logo | Trademarks: see the [trademark policy](https://github.com/ntxprotocol/.github/blob/main/TRADEMARKS.md) |

<sub>Copyright © 2026 CamelCase Technologies Ltd and the NTX contributors.</sub>
