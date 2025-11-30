### [root](../spec/index.md) > [meta-spec](metaspec.md) > spec-template

# Specification File Template

This template defines the standard structure for all TRAIL spec files. Use this as a starting point for new keyword or construct documentation.

---

## Breadcrumb

```
### [root](../index.md) > [solution](../solution.md) > <keyword>
```
- Use a compact heading (###) for navigation.
- Adjust relative paths as needed for the file's location.

## Definition

# `<keyword> [<parameters>]`

A concise, one-sentence definition of the construct.

> (Optional) See also: [related keyword](related.md) — for complementary or opposite constructs.

## Description

A paragraph or two explaining the purpose and context of the construct.

## Syntax

```
<keyword> <parameters>:
  <child statements>
```
- Provide a minimal, canonical syntax example.

## Semantics

- ```[`<parameter>`](link-if-applicable.md)```: Short explanation of each parameter or child statement.
- ...
- Child statements: Link to other keywords as appropriate.

## Constraints

1. List any rules, uniqueness, or validation requirements.
2. ...

## Related

- See ```[`link`](folder/link.md)``` or other relevant docs for valid values or further reading.
- Cross-link to related constructs as needed.

---

> Copy this structure for all new spec files to ensure consistency and navigability.
