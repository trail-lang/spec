### [root](../../index.md) > [solution](../../solution.md) > [roles](index.md) > queue

# `queue`

Represents a message queue that preserves ordering guarantees per-queue or
per-partition (e.g., Azure Service Bus queues, AWS SQS, RabbitMQ).

## Characteristics

- FIFO or at-least-once delivery semantics.
- Supports enqueue/dequeue operations, dead-letter handling, and visibility
  timeouts.
- Often paired with workers that consume messages.

## Usage Notes

- Can be modeled as `owned` when the solution controls queue creation and
  configuration, or as `dependency` when referencing an existing queue.
- Additional attributes such as batching, lock duration, or retry strategy are
  specified in the consuming application's documentation.
