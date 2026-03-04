This workflow belongs to the Specifications shard. Ensure you have [[init-spec]] in context before continuing.

# Workflow: Start Spec

Design and create a new specification with initial sections.

# Input

- Topic or system to specify
- (Optional) Known sections or subtypes needed
- (Optional) Existing documents to draw from

# Actions

## Stage 1: Design

1. Clarify the scope with the user:
   - What system, protocol, or concept is being specified?
   - What subtype fits best? (architecture, protocol, schema, api, process, requirements, convention)
   - What sections will the spec need?
2. If existing documents cover this topic (notes, reports, OrbCode maps), gather them for context
3. Present the proposed structure to the user:
   - Root spec name and subtype
   - Planned sections (sub-specs)
   - Key dependencies or related specs
4. Once the user confirms the design, progress to the next stage

## Stage 2: Create

1. Use [[sk-spec-create]] to create the root spec folder and file
2. Write the Abstract and Scope sections based on the design discussion
3. For each planned section, use [[sk-spec-add_section]] to create sub-spec files
4. Write initial content for each section drawing from gathered context
5. Once all files are created, progress to the next stage

## Stage 3: Review

1. Present the complete spec structure to the user
2. Summarize what each section contains
3. The user reviews and may request:
   - Content revisions
   - Additional sections
   - Scope adjustments
4. Apply revisions as requested
5. Once the user is satisfied, progress to the next stage

## Stage 4: Propose

1. Set the root spec status to `proposed` (ready for formal review)
2. Set all section statuses to `proposed`
3. Update session tracking
4. Inform the user the spec is now in `proposed` state and ready for ratification

# Output

- Complete specification with root and sections in `proposed` status
- Ready for ratification after review
