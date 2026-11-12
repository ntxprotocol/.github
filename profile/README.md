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
  <img alt="Status: early development" src="https://img.shields.io/badge/status-early%20development-0B7A72">
  <img alt="SDKs: Rust, C, Python, Node.js, TypeScript, .NET, Java" src="https://img.shields.io/badge/SDKs-Rust%20%C2%B7%20C%20%C2%B7%20Python%20%C2%B7%20Node.js%20%C2%B7%20TypeScript%20%C2%B7%20.NET%20%C2%B7%20Java-0B7A72">
  <a href="https://github.com/ntxprotocol/.github/blob/main/CODE_STANDARDS.md"><img alt="Coverage target at least 90%" src="https://img.shields.io/badge/coverage%20target-%E2%89%A590%25-0B7A72"></a>
  <a href="https://github.com/ntxprotocol/.github/blob/main/CONTRIBUTING.md"><img alt="Contributions welcome" src="https://img.shields.io/badge/contributions-welcome-0B7A72"></a>
</p>

## What is NTX?

Think of it as **NDI, but for text** (NDI is a common way to send live video between apps on a
network). One app sends text (a lyrics app, a scripture detector, a scoreboard, a caption tool).
Other apps receive it (presentation software, video mixers, streaming tools) and show it with
**their own templates and styling**, exactly as if someone had typed it in.

```json
{ "op": "update", "channel": "program", "seq": 42, "type": "ntx.text",
  "fields": { "text": "Amazing grace, how sweet the sound" } }
```

- **Text, not pictures of text.** Fonts, layouts and transitions stay in the receiving app.
- **Use-case neutral.** Any JSON fields; shared types such as `ntx.text` keep strangers' apps compatible.
- **Live-ready.** Full state on connect, ordered updates, on-air tally, automatic reconnect.
- **Finds itself.** mDNS (automatic discovery on the local network) finds sources, with a manual
  address when needed.
- **Safe by default.** Optional pairing codes; web pages from the internet cannot read or send text
  unless the user allows them.
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

## Repositories and packages

| Use NTX from | Repository | Package | Status |
| --- | --- | --- | --- |
| The protocol itself | [**spec**](https://github.com/ntxprotocol/spec) | Specification, JSON Schemas and examples | 0.1 Pre-Draft |
| Rust | [**ntx**](https://github.com/ntxprotocol/ntx) | crate `ntx` | Early development |
| C and C++ | [**ntx**](https://github.com/ntxprotocol/ntx/tree/main/crates/ntx-ffi) | crate `ntx-ffi`: library `libntx_ffi` and header `ntx.h` | Early development |
| The command line | [**ntx**](https://github.com/ntxprotocol/ntx/tree/main/crates/ntx-cli) | crate `ntx-cli`: the `ntx` test tool (send, receive, list, publish, relay) | Early development |
| Python 3.11+ | [ntx-python](https://github.com/ntxprotocol/ntx-python) | PyPI `ntx-protocol` (`import ntxprotocol`) | Not public yet |
| Node.js 22+ | [ntx-node](https://github.com/ntxprotocol/ntx-node) | npm `@ntxprotocol/ntx` | Not public yet |
| Web pages (TypeScript) | [ntx-web](https://github.com/ntxprotocol/ntx-web) | npm `@ntxprotocol/web` | Not public yet |
| .NET 8 and 10 | [ntx-dotnet](https://github.com/ntxprotocol/ntx-dotnet) | NuGet `Ntx` | Not public yet |
| Java 22+ | [ntx-java](https://github.com/ntxprotocol/ntx-java) | Maven `com.ntxprotocol:ntx` | Not public yet |
| A desktop app | [client](https://github.com/ntxprotocol/client) | NTX Client: monitor sources, test sending, and bridge text into FreeShow, OBS Studio, vMix, files and OSC | Not public yet |
| Testing your app | [conformance](https://github.com/ntxprotocol/conformance) | `ntx-conformance`: checks a source, receiver, publisher or relay against the spec; behind "NTX compatible" | Not public yet |
| OBS Studio | `obs-ntx` | Native OBS plugin | Planned |

- **Repositories "not public yet":** only members of the organisation can open them for now.
- **Packages:** none is on crates.io, PyPI, npm, NuGet or Maven Central yet. Until they are, build
  from source as each README explains.

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
