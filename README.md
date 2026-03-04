# Specifications

Create and manage detailed specifications as folder-based, versioned artifacts.

## Structure

```
Shards/(Dev) Specifications/
├── shard.yaml              # Manifest
├── init-spec.md            # Init file — shard context
├── README.md               # This file
├── skills/
│   ├── sk-spec-create.md           # Create a new specification
│   ├── sk-spec-add_section.md      # Add a section to an existing spec
│   └── sk-spec-archive.md         # Archive a superseded spec
├── workflows/
│   ├── wkfl-spec-start.md         # Start a new specification
│   └── wkfl-spec-amend.md         # Amend a ratified spec
├── templates/
│   ├── tmp-spec-root-v0.1.md      # Root specification template
│   └── tmp-spec-section-v0.1.md   # Sub-spec / section template
├── knowledge/
│   └── knw-spec-conventions.md    # Writing conventions and RFC 2119
└── install/
    └── (Dashboard) Specs.md       # DataviewJS dashboard
```

## Artifact Location

Specs live in `Mesh/Specs/` with one folder per spec:

```
Mesh/Specs/(Spec) Name/
├── (Spec) Name.md                  # Root
├── (Spec) Name . Architecture.md   # Section
└── (Spec) Name . Schema.md         # Section
```
