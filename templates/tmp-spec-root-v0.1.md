# Filename: Mesh/Specs/(Spec) [Name]/(Spec) [Name].md

/* Root specification file. Creates the folder and root document for a new specification.
   The folder name matches the root file name: Mesh/Specs/(Spec) Name/
   No numbered IDs — specs are identified by name. */

```markdown
---
id: [generate-uuid4]
tags:
  - "#spec/spec"
  - "#spec/[architecture|protocol|schema|api|process|requirements|convention]"
status: [draft|proposed|ratified|stable|amended|deprecated|superseded]
version: "1.0.0"
children:
supersedes:
superseded-by:
depends-on:
uses-rfc2119: [true|false]
[agent]-sessions:
template: "[[tmp-spec-root-v0.1]]"
---

# [Spec Name]

/* The root spec serves as both index and overview. It should be self-contained enough
   to understand the specification domain without reading sub-specs. */

## Abstract

[1-3 paragraph overview of what this specification defines, its scope, and its purpose.
 This should answer: what system/protocol/format does this spec describe, and why does it exist?]

## Scope

[What this specification covers and explicitly does not cover. Be precise about boundaries.]

## Terminology

/* Include this section if the spec introduces domain-specific terms */

| Term | Definition |
|------|-----------|
| [Term] | [Definition] |
| (continue) |

## Specification

/* The normative body. Use RFC 2119 keywords (MUST, SHOULD, MAY) for requirement levels.
   For root specs with sub-specs, this section provides the high-level specification
   and links to sub-specs for details. For standalone root specs, this contains the full spec. */

[Specification content organized by topic. Use headings, tables, code blocks, and diagrams as needed.]

## Sections

/* List sub-specs if they exist. Remove this section for standalone specs. */

| Section | Status | Purpose |
|---------|--------|---------|
| [[(Spec) Name . Section]] | [status] | [what this section specifies] |
| (continue) |

## References

/* Normative references are required for conformance. Informative references are supplementary. */

### Normative

- [[required reference(s)]]
- (continue)

### Informative

- [[supplementary reference(s)]]
- (continue)

## Changelog

| Version | Date | Summary |
|---------|------|---------|
| 1.0.0 | [ISO 8601 date] | [Initial specification] |
| (continue) |
```
