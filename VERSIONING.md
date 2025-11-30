# TRAIL Versioning Policy

---
**TRAIL Documentation Navigation**

[Readme](README.md) | Versioning | [Human Specs](human-specs.md) | [Objectives](objectives/index.md) | [Meta-Spec](meta-spec/metaspec.md) | [Spec Index](spec/index.md)
---

TRAIL uses semantic versioning for the language and specification.

## Version Format
MAJOR.MINOR.PATCH

- MAJOR: breaking changes to syntax or semantics
- MINOR: backward-compatible additions
- PATCH: clarifications and non-functional changes

## Canonical Version
Defined by Git tags and GitHub Releases. The repository contains only the latest version of the spec on `main`.

Previous versions are accessed via tags:

    git checkout v1.0

## Development Model
- `main` contains the working draft of the next version.
- Releases are tagged using `vMAJOR.MINOR.PATCH`.

We do not store multiple copies of the spec in the repo.
