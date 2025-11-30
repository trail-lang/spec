# TRAIL Project Handover Instructions (AI / Copilot)

This file explains the purpose of this repository to AI tools such as GitHub
Copilot. It also defines the principles and instructions required for continuing
spec development in the correct direction without introducing drift.

---

# Project Description

This repository contains the early specification of **TRAIL**:

> TRAIL is a full programming language designed for AI-first system development,
> application architecture, deployment intent, and compilation to existing
> runtimes such as .NET IL and JVM bytecode.

TRAIL is not a modeling DSL or configuration language. It is a real language spec
that will eventually compile to production-grade software.

The repository contains:

- `objectives/` — the philosophical and strategic foundation.
- `meta-spec/` — the spec for the spec itself.
- `spec/` — the core language specification (to be filled out).
- `README.md` — human-facing overview.

The Objectives layer is now complete and canonical.

---

# AI Instructions (Copilot, Cursor, Devin, or other agents)

### ❗ These rules must always be followed:

1. Preserve the TRAIL values and goals exactly.
2. Maintain the AI-first philosophy. Humans are secondary consumers.
3. Use semantic clarity and explicit intent in all design.
4. Do not reintroduce domain-driven design, layered architecture,
   or human-centric organization patterns.
5. The language must always support:
   - multi-application solutions (SPA/API/worker/etc),
   - concept-based grouping,
   - deployment and infrastructure intent,
   - direct compilation to IL/JVM/JS/WASM in the future.

### ❗ These are out of scope for the spec:

- Creating a runtime/VM.
- Becoming Terraform/CloudFormation/K8s YAML.
- Template generators or scaffolding engines.

We do allow expressing deployment **intent**, just not cloud-provider dialects.

---

# Where to Continue

The next major work happens inside the `spec/` folder.

Spec work should proceed in this order:

1. Define the root syntax of a TRAIL solution.
2. Define syntax for applications, components, and ownership.
3. Define type system and primitives.
4. Define object/behavior constructs (entities, services, operations).
5. Define imports/includes and file semantics.
6. Define deployment intent semantics.

Do not start compiler design yet. The language spec comes first.

---

# Formatting Rules

- Use Markdown.
- Keep the structure tight and formal.
- Each spec section should live in its own file.
- Prefer short, complete paragraphs and bullet points.
- Do not write code samples in pseudocode—use TRAIL style.

---

# Copilot Prompt (paste this into Copilot chat)

You are continuing work on the TRAIL language specification. TRAIL is a full 
programming language designed for AI-first application development and deployment 
intent. Before making any change, carefully follow these constraints:

- Preserve the philosophy and values in `objectives/`.
- Do not drift toward traditional human-first architecture patterns.
- Do not introduce a runtime, templates, or infrastructure DSLs.
- Always express intent explicitly and semantically.
- Focus on the language spec in `spec/` next, not compilers.

Continue building the language specification by defining:

1. Solution syntax
2. Application syntax
3. Component definitions
4. Type system and code constructs

Work incrementally and keep each section self-contained and precise.

---

# End

If other AI tools join this repository later (Cursor, Devin, etc.), these same
instructions apply.
