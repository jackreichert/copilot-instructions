# Workflow Guide

## Feature Development Workflow

For multi-step features, use this three-phase approach:

### Phase 1: Plan (.github/plans/)
Create planning document: `.github/plans/plan-<feature-name>.prompt.md`
- Overview, high-level steps, clarified requirements
- Key design decisions with rationale
- Acceptance criteria, technical notes
- **Purpose:** Answer "what" and "why" before "how"
- Ensure **Project Folder** is at the top of your files which include the relative path to the project dir eg.(`projects/doctors` or `data_import/customers/thekey`)
- When relevant itemize existing business logic to ensure nothing is lost during development

### Phase 2: Create Task Breakdown (.github/tasks/)
Break plan into atomic tasks: `.github/tasks/<TICKET>-task-<N>-<name>.md`
- Objective, dependencies, estimated effort
- Deliverables (checkboxes), implementation details, testing approach
- **Benefits:** Progress tracking, resumability, effort documentation

### Phase 3: Final Summary (docs/features/)
After completion: `docs/features/<TICKET>-<feature-name>.md`
- Status, dates, high-level purpose, implementation summary
- Key discoveries, design decisions, trade-offs
- Maintenance guide (monitoring, troubleshooting)
- **Include project context:** Specify main project directory (e.g., `data_import/customers/thekey`, `projects/doctors`)
- **Important:** NO CODE - use prose descriptions and link to source files
- Validate solution against new and existing business logic

---

## Session Context (CONTEXT.md)
Lightweight session log at repo root (≤50 lines):
- Current focus, active branch, quick links, session notes
- Update when: at every step of the process
- Link to detailed docs, don't duplicate

## Directory Structure
```
/
├── CONTEXT.md                          # Session log (navigation hub)
├── .github/
│   ├── plans/
│   │   ├── plan-<feature>.md          # Feature planning
│   │   └── investigate-<TICKET>.md    # Complex bug investigation
│   ├── tasks/
│   │   ├── <TICKET>-task-*.md         # Feature tasks
│   │   └── <TICKET>-bug-*.md          # Medium bug tasks
│   └── workflow-guide.md              # This file
└── docs/
    ├── features/<TICKET>-<name>.md    # Feature documentation
    ├── decisions/<name>.md            # Architecture decisions
    └── postmortems/<TICKET>-<name>.md # Critical bug postmortems
```

## When to Use Full Workflow
**Use for:** Multi-step features (>4h), complex changes, multi-system features
**Skip for:** Simple bugs, trivial updates, exploratory work, single-file changes

## Bug Handling

**Simple Bugs (<1h):** Skip all phases. Fix + clear commit message with root cause in body.

**Medium Bugs (1-4h):** Task file only: `.github/tasks/<TICKET>-bug-<name>.md` with root cause, solution, files changed, testing notes.

**Complex Bugs (>4h):** Investigation doc in `.github/plans/investigate-<TICKET>.md` with symptoms, root cause, potential solutions. Add task breakdown if multi-step fix. If reveals design flaw, create decision record.

**Critical Production Bugs:** Add postmortem in `docs/postmortems/<TICKET>-<name>.md` with timeline, root cause, fix, prevention measures.

## Guidelines by Phase

**Planning (.github/plans/):** High-level, decision-focused. Why this approach? What constraints? No implementation details.

**Tasks (.github/tasks/):** Atomic (one session), specific files/functions, track progress with checkboxes, document actual vs estimated effort.

**Feature Docs (context/features/):** Written AFTER completion. Implementation summary, key discoveries, maintenance guide. NO CODE - prose + links. Include lessons learned.

**Decision Records (context/decisions/):** Problem statement, options considered, decision + rationale, consequences, date/participants.

## Best Practices
1. Plan first, code second (don't skip for complex work)
2. Link, don't duplicate content between files
3. Update CONTEXT.md at session start, mark features complete when merged
4. No code in feature docs - use prose and file links
5. Document discoveries and actual effort

## Example: AH-832
**Plan:** 8 steps, design decisions documented
**Tasks:** 8 files (doc, writeback, archive, integrate, restore, tests, final docs)
**Result:** 11.5h actual vs 14.5h estimated. Key discovery: TheKey API returns shifts outside requested window.
