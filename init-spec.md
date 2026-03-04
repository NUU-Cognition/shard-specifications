# Specifications

Create and manage detailed specifications — prescriptive, normative documents that define how things work or should work. Specs are the source of truth that persists alongside the systems they describe.

## What Is a Specification

A specification is a **normative document** — it defines constraints, interfaces, behavior, and conventions. Unlike plans (consumed by execution) or reports (descriptive, retrospective), specs are **consumed by reference**. They stay active as long as the system they describe exists.

Specs use RFC 2119 language (MUST, SHOULD, MAY) for precise requirement levels. See [[knw-spec-conventions]] for writing conventions.

## Structure

Every spec lives in its own folder under `Mesh/Specs/`:

```
Mesh/Specs/
├── (Spec) Shard Protocol/
│   ├── (Spec) Shard Protocol.md                    ← Root (index + overview)
│   ├── (Spec) Shard Protocol . Wire Format.md      ← Sub-spec
│   └── (Spec) Shard Protocol . Lifecycle.md        ← Sub-spec
│
└── (Spec) Flint File Format/
    ├── (Spec) Flint File Format.md
    └── (Spec) Flint File Format . Frontmatter.md
```

**Rules:**
- Every spec gets a folder: `Mesh/Specs/(Spec) Name/`
- Root file matches folder name: `(Spec) Name.md`
- Sub-specs use dot notation: `(Spec) Name . Section.md`
- Root specs list children in `children:` frontmatter
- Sub-specs link back via `parent:` frontmatter

## Lifecycle

```
draft → proposed → ratified → stable
                                 ↓
                          amended → ratified (cycle)
                                 ↓
                            deprecated
                                 ↓
                            superseded
```

| Status | Meaning |
|--------|---------|
| `draft` | Being written, not yet normative |
| `proposed` | Ready for review, seeking consensus |
| `ratified` | Accepted as source of truth |
| `stable` | Proven through use, unlikely to change |
| `amended` | Active revision of a ratified spec |
| `deprecated` | Should not guide new work |
| `superseded` | Replaced by another spec |

## Spec Subtypes

Subtypes are expressed as tags. Common subtypes:

| Subtype | Tag | What It Defines |
|---------|-----|----------------|
| Architecture | `#spec/architecture` | System structure, components, boundaries |
| Protocol | `#spec/protocol` | Message formats, state machines, behavior |
| Schema | `#spec/schema` | Data shapes, validation rules, formats |
| API | `#spec/api` | Endpoints, parameters, responses |
| Process | `#spec/process` | Workflows, procedures, lifecycle rules |
| Requirements | `#spec/requirements` | Functional/non-functional constraints |
| Convention | `#spec/convention` | Naming, style, patterns to follow |

## File Structure

- Location: `Mesh/Specs/(Spec) Name/`
- Archive: `Mesh/Archive/Specs/(Spec) Name/`
- Dashboard: `(Dashboard) Specs.md`

## Skills

| Skill | File | Purpose |
|-------|------|---------|
| Create Spec | `sk-spec-create.md` | Create a new specification folder and root file |
| Add Section | `sk-spec-add_section.md` | Add a sub-spec to an existing specification |
| Archive Spec | `sk-spec-archive.md` | Archive a superseded specification |

## Workflows

| Workflow | File | Purpose |
|----------|------|---------|
| Start Spec | `wkfl-spec-start.md` | Start a new specification with design review |
| Amend Spec | `wkfl-spec-amend.md` | Amend a ratified specification |

## Templates

| Template | File | Purpose |
|----------|------|---------|
| Root Spec | `tmp-spec-root-v0.1.md` | Root specification file (index + overview) |
| Section | `tmp-spec-section-v0.1.md` | Sub-spec / section file |

## Knowledge

| Knowledge | File | Topic |
|-----------|------|-------|
| Conventions | `knw-spec-conventions.md` | Specification writing conventions and RFC 2119 |
