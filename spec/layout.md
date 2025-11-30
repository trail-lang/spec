# [root](index.md) > layout

# TRAIL Solution Structure

This document defines how a TRAIL solution is laid out from the repository root
down to individual `.trail` files. It establishes the entry points and
organizational expectations the language specification will build on.

---

## The `.trail` File Extension

- All TRAIL source files use the `.trail` extension.
- Files are UTF-8 text that rely on indentation for structure (per TOON-style
  rules in the meta-spec).
- Each file captures a cohesive slice of the solution: the root solution model,
  an application’s software descriptor, or the concept-specific code for that
  application.
- Tooling infers concept boundaries from file names.

---

## Required Top-Level Files

| File | Purpose |
| ---- | ------- |
| `solution.trail` | Canonical entry point for the solution. Declares solution metadata, ownership, applications, shared dependencies, and global deployment intent. |

`solution.trail` must exist at the repository root (or the root of the TRAIL
workspace) so AI agents and compilers have a deterministic starting point.
This file alone can describe existing systems (only dependencies, no owned apps)
although the intent of TRAIL is to evolve active solutions.

---

## Application Folder Expectations

Every owned application mentioned in `solution.trail` resides in its own folder
containing only `.trail` files. For example, the `orderapi/` folder represents
the `owned api orderapi` declaration.

### `software.trail`

Each application folder must contain `software.trail`, which captures
non-code-specific details about that tier:

- runtime classification (api, spa, worker, console, etc.),
- infrastructure environments and deployment targets more granular than the
  entries in `solution.trail`,
- dependencies unique to that application,
- local hosting/debug instructions,
- packaging or build metadata.

### Concept `.trail` Files

- All other files inside the application folder are `.trail` source files that
  describe code constructs grouped by concept (e.g., `orders.trail`,
  `customers.trail`).
- These files contain entities, repositories, models, services, endpoints,
  workers, DTOs, and any other behavior or data definitions associated with the
  concept.
- No subfolders are required. The `.trail` files themselves represent the full codebase for that tier.
- Any number of `.trail` files can exist in an application folder. AI tools will tend towards grouping based on concept where possible.
- Concept level `.trail` files may be split into different concepts, or merged, as the AI tooling deems necessary.

## Top-to-Bottom Interpretation Order

1. **`solution.trail`** — Declares the solution, owned apps, dependencies, and
   global deployment intent.
2. **`software.trail` per app folder** — Describes the tier’s runtime type,
   environment mappings, per-app dependencies, deployment strategy, and local
   execution guidance.
3. **Concept `.trail` files inside each app folder** — Contain the actual code
   constructs (entities, services, repositories, endpoints, workers, DTOs,
   etc.) organized by concept.

A compiler or AI agent must evaluate files in this order, flowing intent from
solution → software tier → concept-level implementation without ambiguity.

---

## Example Repository Layout

```
repo-root/
│
├─ .git/
├─ solution.trail
├─ orderapi/
│   ├─ software.trail
│   ├─ orders.trail
│   └─ customers.trail
├─ orderwebsite/
│   ├─ software.trail
│   └─ storefront.trail
├─ emailworker/
│   ├─ software.trail
│   └─ notifications.trail
└─ (additional app folders as needed)
```

`solution.trail` lists each folder (e.g., `owned api orderapi`). Inside every app
folder, `software.trail` captures tier-level intent while the other `.trail`
files hold the actual code constructs grouped by concept.

---

## Example `solution.trail`

```
solution CustomerOrderSystem:
    owned spa orderwebsite:
        connects orderapi
        deploy azure

    owned api orderapi:
        connects ordersdb confirmationqueue
        deploy custom

    dependency db ordersdb:
        deploy google

    dependency queue confirmationqueue:
        deploy aws

    owned worker emailworker:
        connects confirmationqueue
        deploy aws
```

This snippet declares the SPA, API, worker, and shared dependencies that align
with the layout above. Each owned application then elaborates its behavior and
infrastructure details inside its respective `software.trail` and concept files.

