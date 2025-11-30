# [root](../index.md) > [solution](../solution.md) > owned

# `owned <role> <name>`

The `owned` block declares an application tier that the solution controls. Each
block creates a binding between the logical topology and a directory in the
repository that contains the tier's `.trail` files.

```
owned <role> <appName>:
  connects <targets>
  deploy <provider>
```

## Semantics

- `<role>` identifies the application type (e.g., `spa`, `api`, `worker`). Role
  documents provide additional constraints.
- `<appName>` must match a folder at the repository root. Inside that folder,
  `software.trail` and concept `.trail` files describe the tier's details.
- Child statements refine how the tier behaves (connectivity, deployment).

## Constraints

1. App names are unique within a solution.
2. The referenced folder must contain a `software.trail` file.
3. Owned applications may reference dependencies or other owned apps through
  `connects`.

## Roles

The following roles are currently defined:

- `spa` — Single Page Application or other browser-based frontend.
- `api` — Backend service exposing HTTP/gRPC endpoints.
- `worker` — Background or scheduled process.

Additional roles (e.g., `cli`, `gateway`) can be added without changing the
structure of the `owned` block.
