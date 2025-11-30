# `dependency <role> <name>`

Dependency blocks represent resources the solution does not own but must
reference explicitly. Examples include databases, queues, SaaS services, or
external APIs.

```
dependency <role> <name>:
    deploy <provider>
```

## Semantics

- `<role>` communicates the kind of dependency (`db`, `queue`, `service`, etc.).
- `<name>` is the identifier used in `connects` statements.
- Child statements describe intent (commonly `deploy`) so tooling knows how to
  bind to the dependency.

## Constraints

1. Dependency names are unique across the solution.
2. Dependency definitions do not require folders or `.trail` files—they are
   references only.
3. Dependencies may appear in `connects` statements declared by owned
   applications or other dependencies, depending on topology needs.

## Common Roles

- `db` — database or data store.
- `queue` — message or event queue.
- `service` — external API/service.

Role-specific semantics (e.g., retention policies) will be introduced as needed
without changing the core syntax above.
