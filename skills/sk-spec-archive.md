This skill belongs to the Specifications shard. Ensure you have [[init-spec]] in context before continuing.

# Skill: Archive Spec

Archive a superseded or deprecated specification by moving its entire folder to the archive.

# Input

- Spec name to archive
- (Optional) Successor spec name (for superseded specs)

# Actions

1. Read the root spec file to confirm status is `deprecated` or `superseded`
   - If not, set status to `superseded` (if successor provided) or `deprecated`
2. If a successor is provided:
   - Set `superseded-by:` in the root spec's frontmatter to link to the successor
   - Set `supersedes:` in the successor's frontmatter to link back
3. Move the entire folder from `Mesh/Specs/(Spec) [Name]/` to `Mesh/Archive/Specs/(Spec) [Name]/`
4. Update session tracking in the root spec

# Output

- Spec folder moved to `Mesh/Archive/Specs/`
- Successor spec cross-linked (if applicable)
- Root spec status set to `superseded` or `deprecated`
