# Contributing to NTX

Thank you for helping. NTX is meant to be used by many different apps, so outside views are
especially welcome: tell us what your app needs.

This is the default guide for all repositories in the `ntxprotocol` organisation. A repository
may add its own `CONTRIBUTING.md` with more detail.

## Sign your commits (DCO)

We use the [Developer Certificate of Origin](https://developercertificate.org/). There is no CLA.
Every commit must carry a sign-off. Add it with `git commit -s`:

```text
Signed-off-by: Your Name <you@example.com>
```

Forgot? Run `git commit --amend -s` (last commit) or `git rebase --signoff main` (a whole branch),
then force-push your branch.

Note: the `spec` repository also asks contributors to accept the Community Specification
Contributor License Agreement. See its CONTRIBUTING.md.

## Code standards

All code follows the [NTX code standards](CODE_STANDARDS.md): tests with at least 90% coverage,
no dead code, no repetition, no over-engineering, and checks that run before every commit and push.

## Pull request flow

1. Open an issue first for anything bigger than a small fix.
2. Fork the repo, make a branch, and keep the change small and focused.
3. Add or update tests and docs.
4. Open a pull request and link the issue.
5. A maintainer reviews it. Please answer comments and keep the branch up to date.
6. A maintainer merges it once checks pass.

## Changes to the protocol

Do not change protocol behaviour in an implementation repository. Proposals for protocol changes go
to the [`spec`](https://github.com/ntxprotocol/spec) repository, as a *Proposal* issue first.
Implementations follow the spec, not the other way round.

## Conformance tests

A change that affects protocol behaviour must pass the conformance suite (`ntx-conformance`)
before merge. New behaviour needs a new conformance test.

## Keep NTX use-case neutral

NTX is a general protocol. Do not add features to the core that only one product needs.
Product-specific needs belong in that product's own message type (reverse-DNS name), not in the
core protocol or core libraries.

## Be kind

Everyone must follow our [Code of Conduct](CODE_OF_CONDUCT.md).
