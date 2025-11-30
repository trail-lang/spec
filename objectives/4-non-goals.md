# Non-Goals

This document defines what TRAIL is **not** intended to do. These boundaries ensure
the language remains coherent and does not expand into adjacent concerns that are
better handled by existing platforms or tooling.

---

## 1. TRAIL is not a new runtime or virtual machine
TRAIL is a complete programming language specification, not a runtime platform.

TRAIL does **not** provide:
- its own execution engine,
- its own low-level virtual machine,
- memory management,
- threading or scheduling semantics.

Compiled TRAIL applications run on existing runtimes such as .NET or the JVM.
The language targets these platforms directly (e.g. TRAIL → IL or TRAIL → bytecode).

---

## 2. TRAIL is not a low-level provider DSL

TRAIL is not intended to mirror or replace low-level cloud provider languages or
APIs (e.g. ARM, Bicep, CloudFormation, raw Kubernetes YAML).

It can describe deployment and infrastructure intent at the solution level, but
the detailed provisioning mechanics, provider-specific options and imperative
lifecycle logic remain the responsibility of external tooling, adapters or cloud
platform SDKs.

---

## 3. TRAIL is not a templating or scaffolding language
TRAIL is not:
- a code generator template,
- a boilerplate engine,
- a snippet language,
- or a parameterized scaffolding system.

TRAIL expresses actual systems, logic, structure and behavior, not just templates.

---

## 4. TRAIL does not enforce business architecture patterns
TRAIL does **not** dictate the use of:
- domain-driven design,
- layered architecture,
- feature folders,
- hexagonal or onion architecture,
- vertical slices.

These are human-centric patterns. TRAIL supports expressing system architecture but
does not impose any particular model.

---

## 5. TRAIL is not intended to replace general programming languages
TRAIL is a language spec like C#, Java or Assembly in the architectural sense,
but it is not meant to replace them. TRAIL targets existing execution platforms rather
than redefining a new ecosystem.

---

## 6. TRAIL does not duplicate logic or concepts
The language does not require or encourage multiple representations of the same
business entity, value object, or concept. Duplication is considered harmful because
it increases ambiguity for AI reasoning and code generation.

---

## 7. TRAIL is not optimized around human-centric workflows
Human readability and conventional patterns matter, but they are secondary.

The language is designed around:
- semantic clarity,
- intent expression,
- deterministic interpretation by intelligent tooling.

The primary consumer of TRAIL syntax is AI, with humans second.

---

## Summary

> TRAIL is a full programming language specification, but not a runtime, VM,
> infrastructure DSL, templating system or pattern-enforcing framework.
> It compiles directly to existing platforms and focuses on expressing system intent,
> structure and behavior—not replacing runtimes or deployment tooling.
