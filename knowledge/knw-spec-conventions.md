# Knowledge: Specification Writing Conventions

Reference for writing clear, precise specifications in Flint. Covers RFC 2119 requirement language, normative vs. informative content, and structural patterns.

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
| **Informative** | Provides context, examples, rationale — not binding | No RFC 2119 keywords | Abstract, examples, rationale notes, appendices |

### Marking Informative Content

Use blockquotes with a label for informative notes within normative sections:

```markdown
> **Note:** This example is informative and does not constitute a normative requirement.
```

## Spec Document Structure

### Universal Skeleton

Every spec follows this layered structure:

1. **Frontmatter** — Metadata (id, tags, status, version, relationships)
2. **Abstract** — What this spec defines and why (informative)
3. **Scope** — What is and is not covered (informative)
4. **Terminology** — Domain-specific terms (normative definitions)
5. **Specification** — The normative body (MUST/SHOULD/MAY language)
6. **References** — Normative (required) and Informative (supplementary)
7. **Changelog** — Version history

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

## Versioning

Specs use semantic versioning in frontmatter:

| Change Type | Version Bump | Example |
|------------|-------------|---------|
| Clarification, typo, editorial | Patch (1.0.0 → 1.0.1) | Fixed ambiguous wording |
| New section, expanded scope | Minor (1.0.0 → 1.1.0) | Added error handling section |
| Breaking normative change | Major (1.0.0 → 2.0.0) | Changed required field name |

The changelog in the spec body tracks all version bumps.

## Cross-Referencing

### Within a Spec

Link between root and sections using wikilinks:

```markdown
See [[(Spec) Shard Protocol . Wire Format]] for message format details.
```

### Between Specs

Use the `depends-on:` frontmatter field for normative dependencies:

```yaml
depends-on:
  - "[[(Spec) Flint File Format]]"
```

Use inline wikilinks for informative references.

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
