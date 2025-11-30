# TRAIL Meta-Spec  

---
**TRAIL Documentation Navigation**

[Readme](../README.md) | [Versioning](../VERSIONING.md) | [Human Specs](../human-specs.md) | [Objectives](../objectives/index.md) | Meta-Spec | [Spec Index](../spec/index.md)
---
**Topology & Runtime Architecture Intent Language**  
_Meta-specification for defining the TRAIL language and ecosystem_
Traditional languages were optimized for human authors. TRAIL is optimized for:
Architecture-level constructs originate inside [`solution.trail`](../spec/solution.md):
- `solution` — declares the system root.
- `owned` — ties a role to an application folder the solution controls.
- `dependency` — references external systems that remain outside ownership.
- `connects` — captures communication intent between owned apps and dependencies.
- `deploy` — records the target platform or provider per block.
- Role keywords that may follow `owned` or `dependency`. The current set lives
  in [`spec/solution/roles/`](../spec/solution/roles/index.md) and includes application tiers ([`spa`](../spec/solution/roles/spa.md), [`api`](../spec/solution/roles/api.md), [`worker`](../spec/solution/roles/worker.md), [`desktop`](../spec/solution/roles/desktop.md), [`mobile`](../spec/solution/roles/mobile.md)) and infrastructure primitives ([`rdbms`](../spec/solution/roles/rdbms.md), [`nosql`](../spec/solution/roles/nosql.md), [`queue`](../spec/solution/roles/queue.md), [`bus`](../spec/solution/roles/bus.md), [`storage`](../spec/solution/roles/storage.md), [`cache`](../spec/solution/roles/cache.md), [`kv`](../spec/solution/roles/kv.md)).

### 2.1 AI-first
AI is the primary producer and consumer. Human ergonomics are secondary.
### 2.2 Explicit semantics
TRAIL does not infer meaning from usage. Intent is part of syntax.

### 2.3 Determinism > flexibility
When ambiguity exists, the language enforces a single meaning.

TRAIL preserves the OO paradigm as its underlying semantic model.

---

## 3. Paradigm
- explicitly scoped dependencies rather than shared infrastructure folders
- inheritance (if allowed)
- properties
Syntax and semantics describe system-level components and their relationships.
Each `owned` declaration maps to a repository folder that contains
[`software.trail`](../spec/layout.md) plus concept `.trail` files, forming a deterministic
interpretation order: [`solution.trail`](../spec/solution.md) → [`software.trail`](../spec/layout.md) → concept files.
- encapsulation
- contracts

The syntax and representation differ from traditional OO languages, but compilers target existing runtimes (initially .NET & JVM).

---

## 4. Language Design Goals
- AI-friendly authoring and parsing
- Clear signaling of intent
- Deterministic syntax and semantics
- Role-based constructs
- End-to-end system description
- Extensible without syntax explosion

---

## 5. Non-Goals
TRAIL does **not** aim to:
- replace general-purpose languages for humans
- provide a new computation model
- rewrite runtime infrastructure
- match existing syntaxes (C#/Java/etc.)
- optimize brevity over clarity

---

## 6. Core Abstractions

Concepts describe cohesive clusters of related behavior (for example, an
`orders.trail` file that holds every class intent (entity, service, repository, etc) for
Orders). Concepts are defined by authors or AI agents through file boundaries and
naming—they are **not** reserved keywords in the syntax. Tooling infers concept
membership based on how source is organized.

### Code-level constructs (roles):
- `entity`
- `service`
- `dto`
- `value`
- `record`
- `contract`

Architecture-level constructs originate inside `solution.trail`:
- `solution` — declares the system root.
- `owned` — ties a role to an application folder the solution controls.
- `dependency` — references external systems that remain outside ownership.
- `connects` — captures communication intent between owned apps and dependencies.
- `deploy` — records the target platform or provider per block.
- Role keywords that may follow `owned` or `dependency`. The current set lives
  in `spec/solution/roles/` and includes application tiers (`spa`, `api`,
  `worker`, `desktop`, `mobile`) and infrastructure primitives (`rdbms`,
  `nosql`, `queue`, `bus`, `storage`, `cache`, `kv`).

Architecture is not an afterthought. It is built into the language.

---

## 7. Architectural Principles
Architecture and code share the same syntax and grammar.

TRAIL supports expressing:
- frontends, APIs, workers
- data stores and message queues
- ownership and dependency
- communication topology
- concept-level organization of related types and behaviors
- deployment intent (packaging, regions, environments, delivery flows)

These declarations start in `solution.trail` and flow into each application's
`software.trail` plus concept `.trail` files so tooling can deterministically
reason from solution topology down to code intent.

---

## 8. Syntax Principles
Indentation-based and TOON-inspired:
- no braces unless required
- minimal punctuation
- parentheses rarely used
- structure = hierarchy

Example:
```
solution OrderSystem:
    owned api orderapi:
        connects ordersdb confirmationqueue
        deploy azure
```

---

## 9. Semantic Principles
- semantics are role-based
- syntax always conveys meaning directly
- topology and deployment hinting are supported

No compiler inference is needed to understand the model.

---

## 10. Target Platforms & Compilers

### Initial targets:
- .NET IL
- JVM bytecode

### Secondary targets:
- WASM
- TypeScript
- Python

Compilers are separate deliverables. The spec is runtime agnostic.

---

## 11. Developer Experience Principles
Human considerations:
- readable
- structured
- explicit

AI considerations:
- deterministic
- minimal parsing ambiguity
- role-driven abstraction

---

## 12. AI Interaction Principles
The language supports:
- clear ownership semantics
- metadata without external config
- reasoning about code and architecture together

AI should not need heuristics to deduce component roles.

---

## 13. Extensibility
The language supports new constructs without grammar rewrites:
- `gateway`
- `eventbus`
- `state`
- `cache`

Syntax + semantics are independently versioned.

---

## 14. Versioning Strategy
- TRAIL uses Semantic Versioning.
- Only the latest spec lives in the repo.
- Historical versions via Git tags & releases.
- `main` = working draft of the next version.

---

## 15. Solution Architecture Principles

### 15.1 Unified Syntax
Architecture and code share syntax and grammar.

### 15.2 Ownership semantics
- `owned`: generated/maintained by AI
- `dependency`: known but external

### 15.3 System-level intent
TRAIL can define:
- topology
- dependencies
- deployment preferences
- explicitly scoped dependencies rather than shared infrastructure folders

### 15.4 Workspace structure
Syntax and semantics describe system-level components and their relationships.
Each `owned` declaration maps to a repository folder that contains
`software.trail` plus concept `.trail` files, forming a deterministic
interpretation order: `solution.trail` → `software.trail` → concept files.

### 15.5 Concept-oriented organization
The syntax encourages grouping related entities, services, values, and behaviors
inside concept-focused files or directories (e.g., `orders.trail`). These
semantic clusters are user/AI defined; there is no `concept` keyword. Compilers
and tooling treat each cluster as a cohesive unit so AI agents know which
artifacts evolve together without relying on ad-hoc folder heuristics.

### 15.6 Deployment & infrastructure intent
Solution syntax includes constructs for declaring packaging models, target
environments, regions, networking constraints, and delivery flows (CI/CD). These
statements remain high-level intent; compilers and adapters translate them to
provider-specific representations while honoring the semantics captured in TRAIL.

---

## 16. Open Questions (future)
- inheritance model
- generic types?
- deployment semantics deeper specification
- module system?
- optional syntax rules?
- code generation boundaries


### Example `solution.trail`

```
solution CustomerOrderSystem:
  owned spa orderwebsite:
    connects orderapi
    deploy azure

  owned api orderapi:
    connects ordersdb confirmationqueue
    deploy azure

  dependency db ordersdb:
    deploy azure

  dependency queue confirmationqueue:
    deploy azure

  owned worker emailworker:
    connects confirmationqueue
    deploy azure
```

