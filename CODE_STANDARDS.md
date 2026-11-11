# NTX code standards

These rules apply to every repository in the `ntxprotocol` organisation. They are enforced by
tools wherever possible: locally by pre-commit / pre-push hooks, and again in CI. A pull request
that does not pass them is not merged.

## Principles

1. **It must work.** Every change is tested. A bug fix comes with a test that fails without it.
2. **No dead code.** No unused functions, parameters, dependencies, feature flags, commented-out
   code or "for later" stubs. Delete it; git remembers.
3. **No repetition.** Logic written twice is extracted once. Copy-paste is detected in CI.
4. **No over-engineering.** Build what the spec and the current users need, nothing more:
   - no abstraction with only one user
   - no configuration options nobody asked for
   - no "framework" around a few lines of code

   Simple and obvious beats clever.
5. **Follow the spec.** Implementations do what the [NTX specification](https://github.com/ntxprotocol/spec)
   says. Comments cite the clause (`// clause 9.4`). Protocol changes start in the spec repo.
6. **Small public surface.** Make something public only when a user needs it. Every public item is
   documented.
7. **Readable code.** Clear names. Comments explain *why*, not *what*. Match the style of the code
   around you.

## Adopted guidelines

| Area | Guideline | Enforced by |
| --- | --- | --- |
| Rust | [Rust API Guidelines](https://rust-lang.github.io/api-guidelines/) | `rustfmt`, `clippy` (pedantic, warnings are errors), `cargo-machete` |
| TypeScript | [Google TypeScript Style](https://google.github.io/styleguide/tsguide.html) | `eslint` (strict type-checked), `prettier`, `tsc --strict` |
| Python | [PEP 8](https://peps.python.org/pep-0008/) + type hints | `ruff`, `mypy --strict` |
| C / C++ | [C++ Core Guidelines](https://isocpp.github.io/CppCoreGuidelines/) | `clang-format`, `clang-tidy` |
| Commits | [Conventional Commits](https://www.conventionalcommits.org/) + DCO sign-off | `commit-msg` hook, CI |
| Versions | [Semantic Versioning](https://semver.org/), [Keep a Changelog](https://keepachangelog.com/) | review |

## Testing

- **Line coverage of at least 90%** in every code repository. This is checked by `pre-push` and CI.
  Coverage is a floor, not a goal: test behaviour, not lines.
- **Surface tests** drive each program the way a user does: the real binary, real sockets and real
  output. They live in each repository's `tests/` folder and run with the normal test command, so
  they can be rerun at any time.
- Tests are deterministic. No sleeps for timing when an event can be awaited; no internet access.
- Protocol behaviour is checked against the spec's examples and, once it exists, the conformance
  suite.

## Security

- Dependencies: licences and advisories are checked (`cargo-deny` for Rust, `npm audit` /
  `pip-audit` elsewhere). Only permissive licences in libraries.
- No secrets in the repository. `gitleaks` runs before every commit.
- `unsafe` Rust is forbidden except in the C ABI crate, where every block has a `// SAFETY:` comment.
- Treat all received network data as untrusted (spec clause 20).

## Checks before commit and push

Install [pre-commit](https://pre-commit.com) once, then in each repository:

```bash
pre-commit install --hook-type pre-commit --hook-type commit-msg --hook-type pre-push
```

| When | What runs |
| --- | --- |
| `pre-commit` (fast) | formatting, lint, file hygiene, secret scan |
| `commit-msg` | Conventional Commit format and DCO sign-off |
| `pre-push` (full) | all tests including surface tests, coverage ≥ 90%, dependency and security checks, duplication check |

CI runs the same checks on Linux, macOS and Windows. Never skip hooks (`--no-verify`) for work
you push.
