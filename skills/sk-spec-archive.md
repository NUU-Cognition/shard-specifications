This skill belongs to the Specifications shard. Ensure you have [[init-spec]] in context before continuing.

# Skill: Archive Spec

Archive a completed or obsolete specification by moving its entire folder to the archive.

# Input

- Spec name to archive

# Actions

1. Read the root spec file to confirm status is `implemented`
   - If not yet implemented, confirm with the user before archiving
2. Move the entire folder from `Mesh/Specs/(Spec) [Name]/` to `Mesh/Archive/Specs/(Spec) [Name]/`
3. Update session tracking in the root spec

# Output

- Spec folder moved to `Mesh/Archive/Specs/`
