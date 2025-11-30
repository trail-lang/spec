# Scope

This document defines what is included in the scope of the TRAIL language and what 
falls outside it. Scope determines the boundaries of the language and ensures that 
the specification evolves with clear constraints.

---

## In Scope

### 1. A Unified Language for Architecture and Code
TRAIL defines syntax and semantics for describing:
- a complete software solution,
- its apps and services,
- relationships and communication,
- data sources and infrastructure,
- and the code that implements it.

Architecture is a first-class part of the language.

### 2. Declarative Representation of System Intent
TRAIL can express:
- topology,
- ownership,
- dependencies,
- deployment hints,
- and semantic roles.

Intent must always be encoded directly.

### 3. OO Semantics as the Foundation
The language follows the Object-Oriented paradigm for:
- type systems,
- inheritance (if enabled),
- contracts/interfaces,
- objects and behavior.

TRAIL does not redefine computation; it redefines representation.

### 4. Compatibility With Existing Runtimes
TRAIL is designed so that compilers can target existing modern OO runtimes and 
platforms. The language specification defines semantics that are compatible with 
platforms such as .NET and the JVM, but the compilers themselves are not part of 
the language specification.

### 5. Minimal, Deterministic Syntax
The syntax layer is part of the scope:
- indentation defines scope,
- TOON-style structural rules,
- explicit role-based keywords.

### 6. Extensibility Model
TRAIL supports extension without requiring new syntax constructs or breaking 
changes. New constructs can enter the language as first-class concepts.

### 7. Concept-Based Source Organization
TRAIL encourages grouping code and architecture by semantic concepts instead of 
human-centric patterns (domains, layers, feature folders). Concepts cluster types, 
behaviors, and data that evolve together so AI agents can reason about related 
concerns without inferring intent from naming conventions or file placement. There
is no `concept` keyword—authors and AI agents define concepts through solution 
structure (for example, an `orders.trail` file that owns every Orders artifact), 
and tooling infers those semantic boundaries from organization.

### 8. Deployment and Infrastructure Intent
The language can encode desired runtime topology, packaging, environments, and 
delivery behavior. Spec authors may describe how applications should deploy, 
communicate, and interact with infrastructure so compilers or adapters can map 
intent onto existing platforms (Azure, AWS, Kubernetes, etc.). TRAIL expresses the 
intent; external tooling handles provider-specific realization.

---

## Out of Scope (at this stage)

### 1. Creating a New Runtime Platform
TRAIL is not:
- a VM,
- a runtime,
- a compiler framework.

### 2. Redefining Programming Paradigms
TRAIL does not replace or rewrite:
- OO fundamentals,
- functional principles,
- distributed algorithms,
- or runtime models.

It optimizes the representation, not the execution model.

### 3. Direct Infrastructure Provisioning
Declarative infrastructure deployment is **not** directly in scope for the core 
language. Hints like:
- `deploy azure`
- `deploy aws`

are in-scope as intent,
but the implementation details belong to tooling or compilers.

### 4. Becoming a Pure Configuration Language
TRAIL is not an alternative to:
- Terraform,
- ARM templates,
- YAML,
- or JSON.

Those may integrate with TRAIL, but do not define it.

### 5. Business Domain Specification
TRAIL does not tell users:
- how to model a domain,
- how many services to build,
- what architecture is best.

It provides the language to express those decisions.

---

## Scope Summary

TRAIL’s scope is:
> A language that unifies architecture and code, encodes intent explicitly, and
> compiles to existing runtimes with deterministic rules.

TRAIL is **not** intended to replace:
- programming language runtimes,
- or traditional languages used by humans.

---
