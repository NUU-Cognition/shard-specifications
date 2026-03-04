This skill belongs to the Specifications shard. Ensure you have [[init-spec]] in context before continuing.

# Skill: Add Section

Add a sub-spec (section) to an existing specification.

# Input

- Parent spec name (must exist in `Mesh/Specs/`)
- Section name
- (Optional) Subtype tag override (defaults to parent's subtype)
- (Optional) Brief description of what this section specifies

# Actions

1. Read the parent root spec to get its name, subtype, and current children
2. Create the section file using [[tmp-spec-section-v0.1]] with:
   - File: `(Spec) [Parent Name] . [Section Name].md`
   - Location: inside the parent's folder
   - Status: `draft`
   - `parent:` linking to the root spec
3. Update the parent root spec:
   - Append the new section to `children:` in frontmatter
   - Add the section to the Sections table in the body
4. Fill in the Overview based on the provided description

# Output

- New section file in the parent spec's folder
- Parent root spec updated with the new child reference
