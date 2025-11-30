### [root](../index.md) > [solution](../solution.md) > owned

# `owned <role> <identifier>`

> See also: [`dependency`](dependency.md) — for external resources not owned by the solution.

The `owned` block declares an application tier that the solution controls. Each
block creates a binding between the logical topology and a directory in the
repository that contains the tier's `.trail` files.


```
owned <role> <identifier>:
  connects <targets>
  deploy <provider>
```

## Semantics

- [`<role>`](roles/index.md) identifies the application type (e.g., `spa`, `api`, `worker`). Role documents provide additional constraints.
- `<identifier>` must match a folder at the repository root. Inside that folder,
  `software.trail` and concept `.trail` files describe the tier's details.
- Child statements refine how the tier behaves ([`connects`](connects.md), [`deploy`](deploy.md)).

## Constraints

1. App names are unique within a solution.
2. The referenced folder must contain a `software.trail` file.
3. Owned applications may reference dependencies or other owned apps through
  [`connects`](connects.md).

## Roles

See [`roles`](roles/index.md) for all valid roles that can be used in the `<role>` position.
