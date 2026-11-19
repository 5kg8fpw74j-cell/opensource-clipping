# Project Instructions

## Knowledge Sources

Before implementing changes, consult:

- README.md for application overview.
- CHANGELOG.md for historical changes.
- Wiki for functional and business requirements.
- docs/architecture.md for system architecture.
- docs/modules.md for module responsibilities.

## Rules

- Follow existing architecture and conventions.
- Reuse existing services before adding new code.
- Check relevant changelog entries before changing
  existing behavior.
- Preserve backward compatibility unless approved.
- Update documentation when behavior changes.
- Add or update tests for affected features.

## Workflow

1. Identify the affected module.
2. Read relevant documentation.
3. Inspect its current implementation.
4. Propose an implementation plan.
5. Implement and test.
6. Review the diff.
7. Summarize changes and documentation updates.

## Persistent project memory

At the beginning of each task, read this file, [project goals](project_memory/GOALS.md), [current progress](project_memory/PROGRESS.md), and the relevant setup, decision, and troubleshooting notes in that directory. Check completed work before repeating it. After meaningful progress, update the relevant files with dated evidence, decisions and reasons, fixes, unresolved issues, and the next action. Clearly distinguish tested behavior from plans. Never record credentials or private source URLs. Keep the notes concise and commit them with the work so future tasks on the fork inherit them.
