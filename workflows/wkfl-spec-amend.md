This workflow belongs to the Specifications shard. Ensure you have [[init-spec]] in context before continuing.

# Workflow: Amend Spec

Revise a ratified or stable specification. Amendments create a new version while preserving the change history.

# Input

- Spec to amend (root or specific section)
- Reason for amendment
- (Optional) Specific changes needed

# Actions

## Stage 1: Scope Amendment

1. Read the current spec (root and relevant sections)
2. Confirm the spec is in `ratified` or `stable` status
3. Discuss with the user:
   - What needs to change and why?
   - Which sections are affected?
   - Is this a minor clarification (patch) or a significant change (minor/major)?
4. Once the scope is agreed, progress to the next stage

## Stage 2: Apply Changes

1. Set the status of affected files to `amended`
2. Make the requested changes to spec content
3. Bump the version number in the root spec frontmatter:
   - Patch (1.0.0 → 1.0.1): Clarifications, typo fixes, editorial
   - Minor (1.0.0 → 1.1.0): New sections, expanded scope, non-breaking
   - Major (1.0.0 → 2.0.0): Breaking changes to normative requirements
4. Add a changelog entry with the version, date, and summary
5. Once changes are complete, progress to the next stage

## Stage 3: Review

1. Present the changes to the user
2. Highlight what changed and the version bump
3. The user reviews and may request further adjustments
4. Once the user confirms, progress to the next stage

## Stage 4: Re-ratify

1. Set affected files back to `ratified` status
2. Update session tracking
3. Inform the user the amended spec is re-ratified at the new version

# Output

- Spec updated with new version number
- Changelog updated
- Status returned to `ratified`
