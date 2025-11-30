# TRAIL Specification Index

---
**TRAIL Documentation Navigation**

[Readme](../README.md) | [Versioning](../VERSIONING.md) | [Human Specs](../human-specs.md) | [Objectives](../objectives/index.md) | [Meta-Spec](../meta-spec/metaspec.md) | Spec Index
---

This index explains how the TRAIL specification is structured and where to find
normative guidance for each layer of the language. The spec focuses on three
progressive layers:

1. **Solution layer** — the `solution.trail` entry point that defines owned apps,
   dependencies, and global deployment intent.
2. **Application layer** — per-application `software.trail` files that describe a
   tier's runtime classification, environments, and local intent.
3. **Concept layer** — `.trail` source files that capture entities, services,
   endpoints, and other code constructs grouped by concept.

## Files and Directories

| Path | Purpose |
| ---- | ------- |
| [`layout.md`](layout.md) | Physical workspace expectations (root files, app folders, `.trail` usage). |
| [`solution.md`](solution.md) | Normative description of the `solution.trail` file. |
| [`solution/`](solution/) | Keyword-level details for constructs used inside `solution.trail`. |
| `software/` *(future)* | Specification of `software.trail` syntax. |
| `concepts/` *(future)* | Specification of concept-level `.trail` files. |

## Reading Order

1. Start with [`layout.md`](layout.md) to understand how a TRAIL workspace is organized.
2. Read [`solution.md`](solution.md) to learn how solutions are declared and how applications
   and dependencies are referenced.
3. Dive into the files under [`solution/`](solution/) for construct-specific rules.
4. Subsequent sections (to be added) will cover `software.trail` and concept
   files using the same approach.

This index will expand as additional sections of the language spec are written.
