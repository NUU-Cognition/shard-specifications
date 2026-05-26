> [!important] THIS FILE IS AN INSTRUCTION. WHEN REFERENCED IT IS MEANT TO BE TAKEN AS AN ACTION.

This skill belongs to the Specifications shard. Ensure you have [[dev-init-spec]] in context before continuing.

# Skill: Create Spec

Create a new specification folder and root file.

# Input

- Spec name (descriptive title)
- Subtype (architecture, protocol, schema, api, process, requirements, convention)
- Increment (parent increment for this spec)
- (Optional) Brief description of what the spec will define

# Actions

1. Create the spec folder at `Mesh/Specs/(Spec) [Name]/`
2. Create the root spec file using [[dev-tmp-spec-root-v0.1]] with:
   - Folder: `Mesh/Specs/(Spec) [Name]/`
   - File: `(Spec) [Name].md`
   - Status: `draft`
   - Tag: `#spec/[subtype]`
   - `increment:` linking to the parent increment
   - `uses-rfc2119: true` (default)
3. Fill in the Abstract and Scope sections based on the provided description
4. Leave the Specification and Testing sections with placeholders for the author to fill

# Output

- New spec folder with root file in `draft` status
- Ready for content to be added via [[dev-sk-spec-add_section]] or direct editing
