# Contributing

Thanks for contributing to `fun-pull-requests`.

This repository packages a focused skill for creating polished GitHub pull
requests. Contributions should improve reliability, clarity, or usability
without turning the skill into a giant generic GitHub handbook.

## Good Contributions

Useful changes include:

- clarifying ambiguous instructions
- improving `gh`-based workflows
- tightening guidance around auth, remotes, base-branch selection, or draft
  handling
- fixing links, grammar, or formatting
- improving examples so they are more realistic and easier to reuse

## Before Opening a PR

Open an issue or start a discussion first if the proposed change would:

- materially change the skill's voice or intended audience
- replace `gh`-first behavior with a different default workflow
- add a large amount of reference material
- broaden the scope beyond PR preparation and publication

Small fixes and focused improvements can go straight to a pull request.

## Contribution Guidelines

1. Keep the skill opinionated and practical.
2. Prefer concrete instructions over vague principles.
3. Keep examples generic and reusable.
4. Update related docs when guidance changes.
5. Preserve the canonical skill name: `fun-pull-requests`.

## Commit Messages and Releases

This repository uses Release Please to manage release PRs, tags, and GitHub
Releases from conventional commit history.

Prefer conventional commit prefixes:

- `feat:` for new capability or materially expanded guidance
- `fix:` for corrections to behavior, instructions, or examples
- `docs:` for documentation updates worth calling out in release notes
- `refactor:` for structural cleanup without changing repository behavior
- `ci:`, `build:`, `chore:`, and `test:` for maintenance work

The `metadata.version` field in `skills/fun-pull-requests/SKILL.md` is
informational. Release Please treats repository tags as the canonical release
version.

## Repository Structure

```text
skills/
  fun-pull-requests/
    SKILL.md
```

The repository-level docs, workflows, and release configuration exist only to
make the skill easier to publish and maintain.
