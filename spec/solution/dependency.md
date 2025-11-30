### [root](../index.md) > [solution](../solution.md) > dependency

# `dependency <role> <identifier>`

> See also: [`owned`](owned.md) — for application tiers the solution controls (opposite of dependency).

Dependency blocks represent resources the solution does not own but must
reference explicitly. Examples include databases, queues, SaaS services, or
external APIs.


```
dependency <role> <identifier>:
   deploy <provider>
```

## Semantics

- [`<role>`](roles/index.md) communicates the kind of dependency (e.g., `db`, `queue`, `service`).
- `<identifier>` is the identifier used in [`connects`](connects.md) statements.
- Child statements refine how the tier behaves ([`connects`](connects.md), [`deploy`](deploy.md)).

## Constraints

1. Dependency names are unique across the solution.
2. Dependency definitions do not require folders or `.trail` files—they are
   references only.
3. Dependencies may appear in [`connects`](connects.md) statements declared by owned
   applications or other dependencies, depending on topology needs.

## Roles

See [`roles`](roles/index.md) for all valid roles that can be used in the `<role>` position.
