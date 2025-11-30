# [root](../../index.md) > [solution](../../solution.md) > [roles](index.md) > nosql

# `nosql`

Represents document, column-family, or graph databases that do not enforce a
relational schema (e.g., Cosmos DB, MongoDB, Cassandra, Neo4j).

## Characteristics

- Flexible data models (documents, wide columns, graphs).
- Tunable consistency and partitioning strategies.
- Query surfaces vary (SQL-like, JSON-based, graph traversals).

## Usage Notes

- Clarify the specific engine and consistency mode in the consuming
  application's specs.
- Denormalized data models and partition keys should be documented where the
  data structures are defined.
