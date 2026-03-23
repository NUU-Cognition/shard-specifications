---
id: 3ffc60ff-823b-46c6-98e2-04abaa188258
tags:
  - "#f/metadata"
  - "#f/type"
---

# Specification

A versioned, normative document that defines how something works or should work. Specifications are folder-based with a root file and sub-specs. They use RFC 2119 language (MUST, SHOULD, MAY) and are consumed by reference.

## Properties

| Property | Value |
|----------|-------|
| Tag | Subtype-based: `#spec/architecture`, `#spec/protocol`, `#spec/schema`, `#spec/api`, `#spec/process`, `#spec/requirements`, `#spec/convention` |
| Location | `Mesh/Specs/(Spec) Name/` |
| Archive | `Mesh/Archive/Specs/(Spec) Name/` |
| Naming | Root: `(Spec) Name.md` / Sub-specs: `(Spec) Name . Section.md` |
| Numbering | None (name-based) |

## Lifecycle

```
draft → proposed → ratified → stable
                                ↓
                            amended
                                ↓
                            deprecated / superseded
```

## Templates

- [[tmp-spec-root-v0.1]] — Specification root
- [[tmp-spec-section-v0.1]] — Specification section
