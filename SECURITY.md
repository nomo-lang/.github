# Security Policy

## Supported versions

Nomo development snapshots are prereleases and do not receive a long-term
support promise. Security fixes are applied to `main` and included in a new,
immutable snapshot. A vulnerable snapshot may be marked as affected or
withdrawn, but its tag and artifacts are never silently replaced.

## Reporting a vulnerability

Do not open a public issue containing vulnerability details.

1. Use the repository's **Security** tab and private vulnerability reporting
   when it is available.
2. If private reporting is unavailable, open a minimal public issue asking a
   maintainer to establish a private channel. Include no exploit, secret,
   private data, or reproduction details in that issue.
3. Identify the affected repository and revision, expected impact, and whether
   you believe active exploitation is occurring once a private channel is
   available.

Maintainers will acknowledge the report, reproduce it when possible, assess
affected versions, prepare a fix on a private branch when necessary, and
coordinate disclosure. Please do not publish details before maintainers have
had a reasonable opportunity to ship mitigations.

## Release integrity

Official releases are published from signed tags. Downloaded archives should
be checked against the release's `SHA256SUMS`. Release evidence and documented
waivers are retained in the
[`rfcs`](https://github.com/nomo-lang/rfcs/tree/main/releases) repository.
