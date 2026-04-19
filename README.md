# fun-pull-requests

`fun-pull-requests` is a reusable agent skill for preparing and publishing
polished GitHub pull requests with `gh`.

It focuses on the operational parts that often get glossed over in lightweight
PR helpers:

- checking `gh` authentication before trying to publish
- resolving the right base branch instead of assuming `main`
- handling branches with no upstream cleanly
- choosing draft versus ready intentionally
- producing a clear PR title and body with a light touch of personality

The canonical skill identifier is `fun-pull-requests`. The repository is
structured so it can be installed directly with GitHub CLI or copied manually
into an agent skill directory.

## Repository layout

```text
skills/
  fun-pull-requests/
    SKILL.md
```

The main prompt lives at `skills/fun-pull-requests/SKILL.md`.

## Installing the skill

Primary path: install from GitHub CLI with `gh skill install`.

```bash
gh skill install madflojo/fun-pull-requests
```

Optional: pin to a tag or commit for reproducible installs:

```bash
gh skill install madflojo/fun-pull-requests@v1.0.0
gh skill install madflojo/fun-pull-requests@<commit-sha>
```

Fallback path: manually copy `skills/fun-pull-requests/` into either:

- `.agents/skills/`
- `~/.agents/skills/`

## What the skill does

The skill is designed for users who want the branch-to-PR workflow to be
reliable, not just cheerful. It teaches the agent to:

- inspect branch and remote state before proposing a PR
- verify `gh auth status`
- derive a credible base branch from upstream, repo defaults, or remote HEAD
- stop and explain blockers when there is no GitHub remote or no upstream
- create either draft or ready PRs with clear reasoning
- fall back gracefully when `gh pr create` cannot submit directly

## Example output

This is the kind of PR output the skill should generate:

Title:

```text
docs: add gh skill install guidance without the side quest 🗺️
```

Body:

```md
## Summary
Document the new `gh skill install` flow and make it the primary install path,
so readers can get to the good part without spelunking through setup docs.

## Changes
- add direct GitHub CLI install examples
- include pinned install examples for tags and commit SHAs
- keep manual copy instructions as a fallback

## Validation
- docs-only change

## Risks
- none noted
```

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for contribution and release guidance.

## License

Licensed under [Apache-2.0](LICENSE).
