# `cache`

Represents a distributed cache or in-memory data grid (e.g., Redis, Memcached).

## Characteristics

- Key-based retrieval with low-latency access.
- Supports TTL/expiration policies and optional data structures (lists, sets).
- Usually shared between multiple applications for performance.

## Usage Notes

- Declared as `dependency` or `owned` depending on who operates the cache tier.
- Cache eviction, serialization format, and consistency expectations are
  detailed in the connecting applications' documentation.
