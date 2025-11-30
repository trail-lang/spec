# [root](../../index.md) > [solution](../../solution.md) > [roles](index.md) > api

# `api`

Represents a service that exposes programmatic capabilities over HTTP, gRPC, or
similar protocols. An `api` role implies:

- endpoint definitions with verbs, routes, and payload contracts,
- possible integration with data stores, queues, or other services,
- deployment artifacts suitable for servers, containers, or serverless APIs.

## Characteristics

- Entry point: request handler pipeline (controller/action, router, RPC method
  table, etc.).
- Interaction model: synchronous request/response; may also emit events or
  provide streaming endpoints.
- Observability: typically requires logging, tracing, and metrics surfaces for
  downstream tooling.

## Usage Notes

- `api` roles can appear under `owned` or `dependency` declarations. Ownership
  determines who maintains the service, not its syntax.
- Endpoint contracts, authentication policies, and data access strategies are
  specified in the application-level documents that reference this role.