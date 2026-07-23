# Nomo release integrity policy

Nomo releases are immutable, source-identifiable build records. A version is
never reused for a different commit, and a published tag is never moved.

## Required invariants

Every public artifact must satisfy all of the following:

1. The version in the component manifest matches the signed Git tag.
2. The tag resolves to the exact commit checked out by the release workflow.
3. CI builds the distributable artifact once.
4. GitHub Releases, package registries, and extension marketplaces publish that
   same artifact instead of rebuilding it independently.
5. Checksums and provenance identify the source repository, workflow, commit,
   and artifact bytes.
6. A released version is never overwritten or reused.

Release workflows must fail closed when any invariant cannot be proven.
Credentials or publishing variables being absent may skip an explicitly
optional distribution channel, but they must not weaken build, checksum, or
provenance checks.

## Branch and tag policy

- Develop release changes on a focused child branch and merge them through a
  pull request.
- Require signed commits on protected default branches.
- Create annotated, signed release tags only after the release commit has
  landed on the protected default branch.
- Do not move, replace, or delete a published release tag to repair a release.
  Create a new version instead.
- Do not publish registry or marketplace packages from a maintainer
  workstation. Public package publication must run in the repository release
  workflow.

## Version channels

- Timestamped development snapshots may use
  `0.0.0-YYYYMMDDHHMMSS` where the target registry accepts SemVer
  prerelease identifiers.
- Visual Studio Marketplace extension versions remain three numeric
  components. Preview status is carried by the marketplace `--pre-release`
  flag rather than a SemVer suffix.
- Stable versions use ordinary semantic versions and the default stable
  distribution tag.
- Every component version must be unique even when only one component changes
  between coordinated releases.

## Build once, publish many

The build job owns the canonical distributable. Downstream publication jobs
must download that artifact and publish it unchanged:

```text
signed tag
    -> validate manifest version and checked-out commit
    -> test and build once
    -> checksum and attest
    -> publish the same bytes to every enabled channel
```

The release record must retain the component commit, tag, checksums,
attestations, enabled and skipped channels, and hands-on installation results.

## Correcting a release

Do not rewrite historical evidence. When a release is incomplete or
inconsistent:

1. Stop further promotion of the affected version.
2. Add a dated post-release addendum describing what happened.
3. Publish a new version from a signed tag and the normal release workflow.
4. Deprecate the affected registry version with a pointer to the replacement
   when the registry supports deprecation.
5. Verify the replacement from the public registry or marketplace.

Unpublishing is reserved for security, legal, or credential-compromise
incidents because removal breaks reproducibility.

## Release checklist

- [ ] The default branch is protected and the release commit is signed.
- [ ] The manifest version and signed tag match.
- [ ] Tests and repository-specific release gates pass.
- [ ] Publication jobs consume the canonical build artifact.
- [ ] Checksums and provenance verify against the public artifacts.
- [ ] Installation and a representative user flow pass on supported platforms.
- [ ] Release evidence records all channel outcomes.
