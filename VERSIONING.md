# Versioning

This document describes the versioning strategy for the kpt project.

## Semantic Versioning (SemVer)

We use [semantic versioning](https://semver.org/) for all release artifacts.
Releases with a fully specified version (e.g. `vX.Y.Z`) are immutable and will
never be changed.

## Pre-release Versions

Pre-releases use the form `vX.Y.Z-pre.<N>`, where `<N>` is an integer that
increases by one for each successive pre-release, starting at `1` (matching the
pattern `v1.2.3-pre.[0-9]+`). For example: `v1.2.3-pre.1`, `v1.2.3-pre.1`.

- `-pre.<N>` is the single, canonical identifier the kpt project uses to mark a
  pre-release.
- A pre-release publishes its own immutable version tag (e.g. `v1.2.3-pre.1`)
  and MUST NOT move the mutable `stable`, floating `vX.Y` / `vX`, or `latest`
  tags (see below).

## Floating Tags

We support abbreviated SemVer tags as floating tags:

- `v<major>.<minor>` always points to the latest patch release within that
  minor version. For example, `v1.2` initially points to `v1.2.0`. After
  `v1.2.1` is released, `v1.2` is updated to point to `v1.2.1`.

- `v<major>` always points to the latest release within that major version.
  For example, `v1` initially points to `v1.2.0`. After `v1.3.0` is released,
  `v1` is updated to point to `v1.3.0`.

These floating tags apply to container images and CLI binaries. They track only
non-prerelease releases and are never moved to a pre-release (see
[Pre-release Versions](#pre-release-versions)). If Go modules are published,
they use fully specified versions (`vX.Y.Z`) and do not use floating tags.

## Latest Tag

The `latest` tag is supported on all container images and points to the most
recent development build. It is updated on every merge to the `main` branch.
The `latest` tag provides no compatibility or stability guarantee and should
only be used for testing and development, never in production environments.

## Stable Tag

The `stable` tag is supported on all container images and points to the most
recent non-prerelease release. It is updated on every GitHub Release that is
not marked as a pre-release.

- Pre-releases (`vX.Y.Z-pre.<N>`, e.g. `v1.2.3-pre.1`; see
  [Pre-release Versions](#pre-release-versions)) publish their own immutable
  version tag including the pre-release identifier (e.g. `v1.2.3-pre.1`, not
  `v1.2.3`). The automated release process MUST NOT move the `stable` tag for a
  pre-release.
- If a repository has not yet published any non-prerelease release, `stable` is
  not published until the first such release exists.
- `stable` normally follows the latest release automatically. Re-pointing
  `stable` to an older release is a manual, permission-gated action performed by
  a maintainer.

Unlike immutable `vX.Y.Z` tags, `stable` is mutable and moves forward with each
new non-prerelease release. Pin the full `vX.Y.Z` version for reproducible
builds.

### Scope: images and binaries

The mutable `latest` and `stable` tags apply to container images. CLI binaries
and other release archives continue to use immutable `vX.Y.Z` tags and the
floating `vX.Y` / `vX` tags.

## Breaking Changes

We define a breaking change as: for any given valid input, the software produces
a different result on a user-facing surface, or a previously supported input is
no longer accepted.

## Backwards Compatibility

For versions v1.0.0 and later:

- **Major version bump**: breaking major changes that require a Go module import path
  change (e.g. `module/v2`).
- **Minor version bump**: may contain breaking changes, new features, or
  improvements.
- **Patch version bump**: bug fixes and security fixes only.

For pre v1.0.0 versions (major version is always `0`):

- **Minor version bump**: may contain breaking changes. SemVer allows breaking
  changes at any time before v1.0.0. Additionally, Go modules require major
  versions v2+ to use a different import path (for example, `module/v2`). While
  a major version bump is the conventional way to signal a breaking change for
  stable (v1+) APIs, bumping from v0 to v1 would indicate that the API is now
  stable, which we are not yet ready to do. Therefore, during the v0.x phase,
  breaking changes are communicated through minor version bumps instead.
- **Patch version bump**: bug fixes, security fixes, and backward-compatible
  features.

Pre-release versions (`vX.Y.Z-pre.<N>`, e.g. `v1.0.0-pre.0`) are unstable and
may contain breaking changes between any two releases.

## Compatibility Rules

The following rules apply within a major version (i.e. non-breaking changes
must not violate these):

### Packages

- Package format MUST NOT change
- Optional fields MAY be added

### Command Line

- Subcommands MUST NOT be removed
- Subcommands SHOULD NOT change in meaning
- Command line flags MUST NOT be deleted
- Command line flags SHOULD NOT change in meaning

### Code

- Existing behaviors MUST NOT change

### Compatibility with Kubernetes

The compatibility policy with specific Kubernetes versions is not yet defined.
Until this section is formalized, refer to each repository's release notes for
supported Kubernetes versions.

During a major release, all code is subject to revision, but package backward
compatibility SHOULD be retained.

## Best Practices

- Pin the full semantic version (`vX.Y.Z`) in CI and production for
  deterministic, reproducible builds.
- Use floating tags (`vX.Y`, `vX`) when you want to automatically receive
  security and bug fixes with less maintenance overhead.
- Avoid using the `latest` (development) tag in production; prefer `stable` or a
  pinned `vX.Y.Z` version.
- Read release notes before upgrading, especially across minor versions.
