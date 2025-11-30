# `rdbms`

Represents a relational database engine (SQL Server, PostgreSQL, MySQL, etc.)
reachable through SQL semantics.

## Characteristics

- Schema-driven tables, views, and constraints.
- ACID transactions and SQL query surface.
- Connection strings, credentials, and migrations define how applications
  interact with the database.

## Usage Notes

- Can be declared as `owned` when the solution provisions and manages the
  database, or as a `dependency` when it references an external instance.
- `connects` statements referencing an `rdbms` imply read/write capabilities
  unless the application specifies a narrower contract in its own docs.
