# Versioning

This document describes the versioning strategy for the kpt project.

## Semantic Versioning (SemVer)

We use [semantic versioning](https://semver.org/) for all release artifacts.
Releases with a fully specified version (e.g. `vX.Y.Z`) are immutable and will
never be changed.

## Floating Tags

We support abbreviated SemVer tags as floating tags:

- `v<major>.<minor>` always points to the latest patch release within that
  minor version. For example, `v1.2` initially points to `v1.2.0`. After
  `v1.2.1` is released, `v1.2` is updated to point to `v1.2.1`.

- `v<major>` always points to the latest release within that major version.
  For example, `v1` initially points to `v1.2.0`. After `v1.3.0` is released,
  `v1` is updated to point to `v1.3.0`.

These floating tags apply to container images and CLI binaries. If Go modules are
published, they use fully specified versions (`vX.Y.Z`) and do not use floating tags.

## Latest Tag

The `latest` tag is supported on all container images and points to the most
recent release. However, it provides no compatibility or stability guarantee.
The `latest` tag should only be used for testing and development, not in
production environments.

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

Pre-release versions (e.g. `v1.0.0-beta.N`) are unstable and may contain
breaking changes between any two releases.

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
- Avoid using the `latest` tag in production.
- Read release notes before upgrading, especially across minor versions.
