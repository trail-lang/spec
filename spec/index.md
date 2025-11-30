# TRAIL Specification Index

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
| `spec/layout.md` | Physical workspace expectations (root files, app folders, `.trail` usage). |
| `spec/solution.md` | Normative description of the `solution.trail` file. |
| `spec/solution/` | Keyword-level details for constructs used inside `solution.trail`. |
| `spec/software/` *(future)* | Specification of `software.trail` syntax. |
| `spec/concepts/` *(future)* | Specification of concept-level `.trail` files. |

## Reading Order

1. Start with `layout.md` to understand how a TRAIL workspace is organized.
2. Read `solution.md` to learn how solutions are declared and how applications
   and dependencies are referenced.
3. Dive into the files under `spec/solution/` for construct-specific rules.
4. Subsequent sections (to be added) will cover `software.trail` and concept
   files using the same approach.

This index will expand as additional sections of the language spec are written.
