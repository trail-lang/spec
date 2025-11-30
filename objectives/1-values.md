# TRAIL Values

## 1. AI-First Architecture & Language Design
TRAIL is designed first for AI tools and agents—not for human convenience.
Human readability is welcome, but **machine comprehension is the priority**.

## 2. Intent Over Inference
The language must encode meaning directly.
No ambiguity. No guessing. No heuristics.

If something is intended to be an API, DB, worker, entity etc.,
**the syntax says so explicitly**.

## 3. Single Source of Truth for Architecture + Code
TRAIL treats system topology and code as equal citizens.

One language describes:
- the solution,
- the applications inside it,
- their relationships,
- and the components.

No separate config or infrastructure languages.

## 4. Determinism by Default
The same input always produces the same interpretation.

No magical behavior. No context-based inference.

## 5. Minimal, Predictable Syntax
Syntax principles:
- indentation represents structure
- avoid unnecessary punctuation
- avoid duplication
- avoid ceremony

Lightweight structure, strong semantics.

## 6. Explicit Roles and Boundaries
The language defines both:
- architecture constructs (`api`, `db`, `worker`, `dependency`)
- code constructs (`entity`, `dto`, `service`)

And it encodes ownership:
- `owned` = AI generates or maintains
- `dependency` = external reference

## 7. Compatibility with Existing Ecosystems
TRAIL does not replace runtimes.
It compiles to them.

Initial targets: .NET and JVM.

## 8. Extensibility Without Complexity
The language should grow without:
- exploding syntax,
- breaking conceptual simplicity,
- requiring major rewrites.

New constructs feel like new vocabulary,
not new grammar.

## 9. Transparency of Design
Design intent is explicit in the spec.
No arbitrary decisions.

## 10. Long-Term Stability
The language evolves carefully and safely.
Stability over novelty.

---

These values are foundational. All future design decisions for TRAIL must align with them. If a proposed feature conflicts with these principles, the feature is wrong, not the values.
