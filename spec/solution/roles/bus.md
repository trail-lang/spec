### [root](../../index.md) > [solution](../../solution.md) > [roles](index.md) > bus

# `bus`

Represents an event bus or pub/sub backbone (e.g., Kafka topics, Azure Event
Hub, Google Pub/Sub) used for broadcasting or streaming events.

## Characteristics

- Topics/partitions with high-throughput append-only logs.
- Consumer groups for parallel processing and offset tracking.
- Supports both real-time streaming and batch ingestion scenarios.

## Usage Notes

- APIs or workers typically `connects` to a `bus` to publish or subscribe.
- Delivery semantics (exactly-once, at-least-once) and retention windows are
  captured in application-level specs.
