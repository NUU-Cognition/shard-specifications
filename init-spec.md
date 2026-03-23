# Specifications

Create and execute detailed specifications — prescriptive design documents that define how systems should be built. A spec is written once, approved, and then implemented via tasks.

## What Is a Specification

A specification is a **one-shot design document**. It defines constraints, interfaces, behavior, and conventions for a system that needs to be built. Unlike plans (high-level direction) or reports (retrospective), specs are **precise and normative** — they use RFC 2119 language (MUST, SHOULD, MAY) to express exact requirement levels.

Specs are like sophisticated plans: you write them, approve the design, then execute them through tasks. Once implemented, the spec is complete — it doesn't get amended or versioned. If the system changes significantly later, write a new spec.

### When to Use a Spec

| Use a Spec when... | Use something else when... |
|---------------------|--------------------------|
| You need to define precise requirements (MUST/SHOULD/MAY) | You need to brainstorm → use a **Notepad** |
| The system has multiple components that need coordinated design | You need high-level direction → use a **Plan** |
| Multiple agents or humans will implement different parts | You need to record findings → use a **Report** |
| You want a reference document during implementation | You need to track a single unit of work → use a **Task** |

### Spec → Task Flow

Specs don't exist in isolation — they drive tasks. The typical flow:

1. **Brainstorm** in a Notepad to explore the design space
2. **Write the spec** to formalize the design (this shard)
3. **Create tasks** from the spec's requirements (Projects shard)
4. **Implement** the tasks, referring back to the spec
5. Spec reaches `implemented` when all tasks are done

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

### When to Split Into Sections

- Split when a section would exceed ~200 lines of normative content
- Split when different people/agents will implement different parts
- Split when sections have distinct testing criteria
- Keep it as one file if the spec is focused and under ~300 lines total

## Lifecycle

```
draft → approved → implemented
```

| Status | Meaning |
|--------|---------|
| `draft` | Being written, design not yet accepted |
| `approved` | Design accepted, ready for task creation and implementation |
| `implemented` | All tasks complete, spec is realized in code |

### Transitions

- **draft → approved**: The spec has been reviewed and the design is accepted. This is the point where tasks get created against the spec.
- **approved → implemented**: All linked tasks are done. The spec's requirements are realized in the codebase.

A spec does not get amended. If the system changes significantly, write a new spec.

## Linkage

Specs connect to the broader workspace through frontmatter fields:

```yaml
increment: "[[(Increment) 6.10 - Shard Improvements]]"
tasks:
  - "[[(Task) 282 Specifications Shard Polish]]"
depends-on:
  - "[[(Spec) NUU CLI Infrastructure]]"
```

- **`increment:`** — which increment this spec belongs to
- **`tasks:`** — tasks that implement this spec (appended as tasks are created)
- **`depends-on:`** — other specs this one requires (for ordering implementation)

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
| Archive Spec | `sk-spec-archive.md` | Archive a completed or obsolete specification |

## Workflows

| Workflow | File | Purpose |
|----------|------|---------|
| Start Spec | `wkfl-spec-start.md` | Design and create a new specification with review |

## Templates

| Template | File | Purpose |
|----------|------|---------|
| Root Spec | `tmp-spec-root-v0.1.md` | Root specification file (index + overview) |
| Section | `tmp-spec-section-v0.1.md` | Sub-spec / section file |

## Knowledge

| Knowledge | File | Topic |
|-----------|------|-------|
| Conventions | `knw-spec-conventions.md` | Specification writing conventions and RFC 2119 |
