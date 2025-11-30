### [root](../../index.md) > [solution](../../solution.md) > [roles](index.md) > worker

# `worker`

Represents long-running or event-driven processing units: background jobs,
queue consumers, schedulers, or pipelines. A `worker` role typically handles:

- message consumption from queues/topics,
- scheduled tasks or cron-style jobs,
- asynchronous processing triggered by other services.

## Characteristics

- Entry point: function, handler, or loop that responds to incoming work items.
- Interaction model: pull (polling queues) or push (event subscription), often
  with eventual consistency guarantees.
- Deployment: suited to platforms that support background workloads such as
  containerized workers, serverless functions, or dedicated job hosts.

## Usage Notes

- `worker` roles can be declared as owned or dependency; ownership simply
  indicates who controls the worker's lifecycle.
- Specific triggers, schedules, and retry behaviors are defined in the
  application-level documentation associated with the worker.