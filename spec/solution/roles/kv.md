# [root](../../index.md) > [solution](../../solution.md) > [roles](index.md) > kv

# `kv`

Represents a key-value store optimized for simple lookup/update operations
(e.g., DynamoDB key-partition model, Azure Table Storage, Consul KV).

## Characteristics

- Strict key-based addressing with optional partition/sort keys.
- Flexible schema, often eventually consistent.
- Supports high-throughput read/write patterns.

## Usage Notes

- Ideal for configuration, feature flags, or lightweight aggregates.
- Define access patterns (read-only vs read/write) within the referencing
  application's documentation.
