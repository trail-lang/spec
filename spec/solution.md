# `solution.trail` 

The `solution.trail` file is the canonical entry point for a TRAIL workspace. It
expresses the system-level topology: owned applications, external dependencies,
communication intent, and high-level deployment guidance. Every repository must
contain exactly one `solution.trail` at its root.

---

## File Responsibilities

`solution.trail` answers these questions:

- What is the solution called?
- Which applications does the solution own (SPA, API, worker, etc.)?
- Which dependencies (databases, queues, services) does the solution rely on?
- How do applications connect to each other and to dependencies?
- Where is each component intended to deploy (cloud, region, etc.)?

---

## Syntax Overview

```
solution <SolutionName>:
    (owned|dependency) <role> <identifier>:
        connects <targets>
        deploy <provider>
```

- `solution` introduces the file and must be followed by a unique solution name.
- `<role>` communicates whether the block is an owned application role (spa,
  api, worker, etc.) or a dependency role (db, queue, service, etc.).
- `<identifier>` is the application folder name or dependency handle.
- Child statements are indented and refine the intent of the parent block.

Role-specific details are defined in [`roles/index.md`](roles/index.md).

---

## Owned Applications

```
owned spa orderwebsite:
    connects orderapi
    deploy azure
```

- `owned` indicates the solution is responsible for the lifecycle of the
  application.
- `<role>` is one of the supported application types (spa, api, worker, etc.).
- `<appName>` must match the folder name that contains the application's
  `.trail` files (e.g., `orderwebsite/`).
- Nested statements:
  - `connects` lists other owned apps or dependencies referenced by name.
  - `deploy` specifies the target platform/provider for the application.

Owned entries are declarative; they do not embed environment-specific DSLs.

---

## Dependencies

```
dependency db ordersdb:
    deploy azure
```

- `dependency` marks a resource that exists outside the solution's ownership.
- `<role>` communicates the type of dependency (`db`, `queue`, `service`, etc.).
- `<name>` is the identifier used by `connects` statements.
- Nested statements (such as `deploy`) describe intent so tooling knows how to
  provision or reference the dependency.

Dependencies do not require corresponding folders because they are not owned by
TRAIL. They remain references within the solution graph.

---

## Example File

```
solution CustomerOrderSystem:
  owned spa orderwebsite:
    connects orderapi
    deploy azure

  owned api orderapi:
    connects ordersdb confirmationqueue
    deploy azure

  dependency db ordersdb:
    deploy azure

  dependency queue confirmationqueue:
    deploy azure

  owned worker emailworker:
    connects confirmationqueue
    deploy azure
```

This example:

- Declares the `CustomerOrderSystem` solution.
- Defines three owned tiers (`orderwebsite`, `orderapi`, `emailworker`).
- References two dependencies (`ordersdb`, `confirmationqueue`).
- Captures connectivity (`connects`) and deployment intent (`deploy`).

---

## Validation Rules

1. Exactly one `solution` declaration per file.
2. Each owned application's name must match a folder at the repository root.
3. Dependency names must be unique so `connects` statements are unambiguous.
4. Statements use indentation; tabs are discouraged.
5. Keywords are lowercase; identifiers use `kebab-case` or `camelCase` per team
   conventions, but must be consistent across the solution.

Further semantic rules for individual constructs are defined in the files under
`spec/solution/`.
