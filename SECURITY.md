# Security

NTX runs on local networks, often at live events, so security problems matter.

This is the default policy for all repositories in the `ntxprotocol` organisation. A repository
may add its own `SECURITY.md`.

## Reporting a problem

Please **do not open a public issue** for a security problem. Instead, use
[GitHub private vulnerability reporting](https://docs.github.com/en/code-security/security-advisories/guidance-on-reporting-and-writing-information-about-vulnerabilities/privately-reporting-a-security-vulnerability)
on the repository concerned, or email **<security@ntxprotocol.com>**.

We aim to reply within 7 days.

## What counts

- A way to change what is shown on screen without permission.
- A way to bypass pairing or a permission check.
- Input that can crash or hang an NTX implementation.
- A flaw in the specification that makes implementations unsafe when followed correctly.

## Known limits (by design, in version 0.1)

- Connections are unencrypted by default (`ws://`). Anyone on the same network can read the text.
- The optional pairing code stops casual or accidental connections. It does not stop a determined
  attacker who can watch network traffic.
