# Knowledge: Specification Writing Conventions

Reference for writing clear, precise specifications in Flint. Covers RFC 2119 requirement language, normative vs. informative content, structural patterns, and testing.

## RFC 2119 Keywords

When `uses-rfc2119: true` in frontmatter, the following keywords have precise meaning. They MUST be capitalized when used normatively.

| Keyword | Meaning |
|---------|---------|
| **MUST** / **REQUIRED** / **SHALL** | Absolute requirement. No exceptions. |
| **MUST NOT** / **SHALL NOT** | Absolute prohibition. No exceptions. |
| **SHOULD** / **RECOMMENDED** | Valid reasons may exist to deviate, but implications must be understood and weighed. |
| **SHOULD NOT** / **NOT RECOMMENDED** | Behavior may be acceptable in particular circumstances, but implications must be understood. |
| **MAY** / **OPTIONAL** | Truly optional. Implementations must interoperate regardless of whether this is included. |

When these words appear in lowercase ("should", "must"), they carry their ordinary English meaning, not their RFC 2119 meaning.

## Normative vs. Informative

Every section of a spec is either **normative** (binding) or **informative** (advisory).

| Type | Purpose | Keywords | Examples |
|------|---------|----------|---------|
| **Normative** | Defines requirements that implementations MUST follow | Uses RFC 2119 keywords | Specification body, schemas, algorithms |
| **Informative** | Provides context, examples, rationale — not binding | No RFC 2119 keywords | Abstract, Scope, examples, rationale notes |

### Marking Informative Content

Use blockquotes with a label for informative notes within normative sections:

```markdown
> **Note:** This example is informative and does not constitute a normative requirement.
```

## Spec Document Structure

### Universal Skeleton

Every spec follows this layered structure:

1. **Frontmatter** — Metadata (id, tags, status, increment, tasks, relationships)
2. **Abstract** — What this spec defines and why (informative)
3. **Scope** — What is and is not covered (informative)
4. **Terminology** — Domain-specific terms (normative definitions)
5. **Specification** — The normative body (MUST/SHOULD/MAY language)
6. **Testing** — Acceptance criteria and verification (how to confirm implementation)
7. **References** — Normative (required) and Informative (supplementary)

### Writing the Abstract

- 1-3 paragraphs maximum
- Answer: What does this spec define? Why does it exist? Who is the audience?
- Do not include requirements (no MUST/SHOULD/MAY)

### Writing the Scope

- State what is covered explicitly
- State what is NOT covered explicitly
- Link to related specs that cover adjacent topics

### Writing Normative Sections

- Lead with the requirement, then explain
- Use tables for structured data (field definitions, enumerations)
- Use code blocks for formats, schemas, examples
- One topic per heading — if a heading covers two things, split it

### Writing the Testing Section

The Testing section defines how to verify the spec has been correctly implemented. It pairs with the tasks that execute the spec.

- Write testable acceptance criteria as checkboxes
- Each criterion should be verifiable — someone can look at the implementation and say yes/no
- Cover the critical requirements from the Specification section
- Include edge cases and error conditions where relevant
- These checkboxes get ticked as tasks complete implementation

## Cross-Referencing

### Within a Spec

Link between root and sections using wikilinks:

```markdown
See [[(Spec) Shard Protocol . Wire Format]] for message format details.
```

### Between Specs

Use the `depends-on:` frontmatter field for specs that must be implemented before this one:

```yaml
depends-on:
  - "[[(Spec) Flint File Format]]"
```

Use inline wikilinks for informative references.

### To Tasks

As tasks are created against a spec, append them to the `tasks:` frontmatter field:

```yaml
tasks:
  - "[[(Task) 282 Specifications Shard Polish]]"
  - "[[(Task) 283 Implement Wire Format]]"
```

## Common Patterns

### Defining a Schema

```markdown
## Config Schema

A config file MUST be valid YAML and MUST contain the following fields:

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `name` | string | MUST | Display name |
| `version` | semver | MUST | Current version |
| `description` | string | SHOULD | Brief description |
| `tags` | string[] | MAY | Classification tags |
```

### Defining a Lifecycle

```markdown
## Status Lifecycle

An artifact MUST be in exactly one of the following states:

\`\`\`
draft → active → archived
\`\`\`

An artifact in `draft` status MUST NOT be referenced by other artifacts.
An artifact MAY transition directly from `draft` to `archived` if it is abandoned.
```

### Defining a Protocol

```markdown
## Message Format

Every message MUST contain a `type` field as the first property.
Messages SHOULD include a `timestamp` field with ISO 8601 format.
Receivers MUST ignore unknown fields (forward compatibility).
```

## Anti-Patterns

Things to avoid when writing specs:

| Anti-Pattern | Problem | Fix |
|-------------|---------|-----|
| Vague requirements | "The system should be fast" — not testable | Quantify: "Response time MUST be under 200ms" |
| Missing boundary | No Scope section — unclear what's in/out | Always write Scope with explicit exclusions |
| MUST everything | Over-constraining leaves no room for implementation | Reserve MUST for true invariants, use SHOULD for recommendations |
| Spec as tutorial | Mixing how-to guidance with normative requirements | Keep tutorials in Guides, specs define *what*, not *how to use* |
| Untestable criteria | Testing section says "works correctly" | Each criterion must be independently verifiable |
