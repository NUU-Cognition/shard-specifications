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
status: [draft|approved|implemented]
increment: [[parent increment hyperlink]]
tasks:
depends-on:
children:
uses-rfc2119: [true|false]
[agent]-sessions:
template: "[[dev-tmp-spec-root-v0.1]]"
authors: /* from .flint/identity.json; omit if no identity set */
  - "[[@Person Name]]"
---

# [Spec Name]

/* The root spec serves as both index and overview. It should be self-contained enough
   to understand the specification domain without reading sub-specs. */

## Abstract

[1-3 paragraph overview of what this specification defines, its scope, and its purpose.
 This should answer: what system/protocol/format does this spec describe, and why does it exist?
 The abstract is informative — no MUST/SHOULD/MAY language here.]

## Scope

[What this specification covers and explicitly does not cover. Be precise about boundaries.]

## Terminology

/* Include this section if the spec introduces domain-specific terms. Remove if not needed. */

| Term | Definition |
|------|-----------|
| [Term] | [Definition] |
| (continue) |

## Specification

/* The normative body. Use RFC 2119 keywords (MUST, SHOULD, MAY) for requirement levels.
   For root specs with sub-specs, this section provides the high-level specification
   and links to sub-specs for details. For standalone root specs, this contains the full spec. */

[Specification content organized by topic. Use headings, tables, code blocks, and diagrams as needed.]

/* Optional: include a Design Principles subsection if the spec benefits from stating
   the guiding philosophy behind its design decisions. This is informative content. */

## Testing

/* How to verify this spec has been correctly implemented. Define acceptance criteria,
   test cases, and edge cases. This section pairs with the tasks that implement the spec —
   the spec says what to verify, the tasks say who does the verifying. */

[Acceptance criteria and verification approach. What must be true when implementation is complete?]

- [ ] [Specific testable criterion]
- (continue)

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
```
