### [root](../index.md) > [solution](../solution.md) > connects

# `connects`

The `connects` statement declares communication intent from the enclosing block
(owned application, worker, or dependency) to other applications or dependencies.

```
owned api orderapi:
    connects ordersdb confirmationqueue orderwebsite
```

## Rules

- Accepts one or more targets separated by spaces.
- Targets must reference either an `owned` application or a `dependency`
  declared in the same `solution.trail` file.
- Order does not imply priority; it is purely declarative.
- Each block declares at most one `connects` line. List every target on that
  single line separated by spaces.

## Semantics

- For owned-to-owned connections, tooling infers bidirectional knowledge but not
  necessarily bidirectional protocols. Each application still documents its own
  contracts in `software.trail` and concept files.
- For owned-to-dependency connections, the statement expresses that the app
  requires access to the dependency at runtime. Provisioning adapters use this
  information to inject configuration or credentials.
- Dependencies may declare `connects` to describe upstream systems they rely on
  or downstream services they expose, keeping the topology explicit.

## Validation

1. All targets must be defined elsewhere in the same solution.
2. Duplicate targets within the line should be treated as redundant and may be
  flagged by tooling.
