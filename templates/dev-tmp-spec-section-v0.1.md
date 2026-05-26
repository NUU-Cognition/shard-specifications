# Filename: Mesh/Specs/(Spec) [Parent Name]/(Spec) [Parent Name] . [Section Name].md

/* Sub-spec / section file. Lives inside the parent spec's folder.
   Uses dot notation in filename: (Spec) Parent . Section.md */

```markdown
---
id: [generate-uuid4]
tags:
  - "#spec/spec"
  - "#spec/[architecture|protocol|schema|api|process|requirements|convention]"
status: [draft|approved|implemented]
parent: "[[(Spec) Parent Name]]"
uses-rfc2119: [true|false]
[agent]-sessions:
template: "[[dev-tmp-spec-section-v0.1]]"
authors: /* from .flint/identity.json; omit if no identity set */
  - "[[@Person Name]]"
---

# [Section Name]

/* Sub-specs focus on one aspect of the parent specification.
   They should be self-contained enough to read independently,
   but link back to the parent for overall context. */

## Overview

[1-2 paragraph overview of what this section specifies and how it fits into the parent spec.]

## Specification

/* The normative body for this section. Use RFC 2119 keywords for requirement levels. */

[Detailed specification content. Use headings, tables, code blocks, and diagrams as appropriate.]

## Testing

/* How to verify this section has been correctly implemented. */

- [ ] [Specific testable criterion]
- (continue)

## References

- [[(Spec) Parent Name]]
- [[other reference(s)]]
- (continue)
```
