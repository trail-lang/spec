# `deploy`

`deploy` declares the intended hosting or provisioning target for the enclosing
block. It can appear under `owned` applications and `dependency` entries.

```
deploy <provider>
```

Usage example:
```
owned api orderapi:
    deploy azure

dependency queue confirmationqueue:
    deploy aws
```

## Semantics

- The value is a single identifier that represents a provider, platform, or
  environment. Identifiers are arbitrary but must remain consistent across the
  solution so tooling can reason about them. Prefer canonical names such as
  `azure`, `aws`, `gcp`, `onprem`, `local`, `custom`
- `deploy` statements remain single-token intent markers rather than
  provider-specific configuration blocks.

## Constraints

1. Each block can contain at most one `deploy` statement.
2. If omitted, tooling assumes a default environment defined outside the spec
   (e.g., agent configuration). Explicit declarations are strongly recommended.
