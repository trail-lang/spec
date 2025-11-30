### [root](index.md) > solution

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
  owned <role> <identifier>:
    connects <targets>
    deploy <provider>

  dependency <role> <identifier>:
    connects <targets>
    deploy <provider>
```

- `solution` introduces the file and must be followed by a unique solution name.
- [owned](solution/owned.md) — declares an application tier the solution controls.
- [dependency](solution/dependency.md) — declares an external resource the solution references.
- [role](solution/roles/index.md) — describes the type of owned app or dependency (e.g. spa, api, db, queue).
- `<identifier>` is the application folder name or dependency handle.
- [connects](solution/connects.md) — lists other owned apps or dependencies referenced by name.
- [deploy](solution/deploy.md) — specifies the target platform/provider for the application or dependency.
- `targets` - An `<identifier>` of another owned/dependency app declared in this file.
- Child statements are indented and refine the intent of the parent block.
- New line between apps (owned/dependency).

---


## Example File

```
solution CustomerOrderSystem:
  owned spa orderwebsite:
    connects orderapi
    deploy azure

  owned api orderapi:
    connects ordersdb confirmationqueue
    deploy aws

  dependency db ordersdb:
    deploy azure

  dependency queue confirmationqueue:
    deploy gcp

  owned worker emailworker:
    connects confirmationqueue
    deploy gcp
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
