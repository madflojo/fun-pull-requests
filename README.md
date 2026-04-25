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

The goal is straightforward: produce PRs that are operationally reliable,
reviewer-friendly, and just a little more alive than stock boilerplate.

## Repository layout

```text
skills/
  fun-pull-requests/
    SKILL.md
```

The main prompt lives at `skills/fun-pull-requests/SKILL.md`.

## Installing the skill

Install with GitHub CLI:

```bash
gh skill install madflojo/fun-pull-requests
```

Install with `npx`:

```bash
npx skills add -g -y madflojo/fun-pull-requests
```

Optional: pin the GitHub CLI install to a tag or commit for reproducible installs:

```bash
gh skill install madflojo/fun-pull-requests@v1.0.0
gh skill install madflojo/fun-pull-requests@<commit-sha>
```

Manual fallback: copy `skills/fun-pull-requests/` into either:

- `.agents/skills/` in a repository
- `~/.agents/skills/` for a user-level install

## Compatibility notes

This skill assumes:

- `git` is installed
- GitHub CLI (`gh`) is installed
- the current directory is inside a cloned git repository
- `gh auth status` can identify a usable GitHub account when the user wants to
  publish a PR

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

These are the kinds of PR titles and summaries this skill should generate.

Lighter-touch titles can carry a small contextual wink:

- `docs: add gh skill install guidance without the side quest 🗺️`
- `refactor(ci): trim release wiring before it grows a second head`
- `docs: tune PR copy so release notes keep their tie on`

For more serious changes, the title should stay fully straight:

- `fix(auth): handle expired token refresh before retries`
- `fix(api): preserve webhook signature verification on retries`
- `security: rotate leaked development credentials`

That same balance applies to the summary section in the body:

- `Document the new install flow so readers can get to the good part without`
  `spelunking through setup docs.`
- `Tighten the release steps so future updates feel more like a routine and`
  `less like archaeology.`
- `Replace exposed credentials and close the window before it becomes a`
  `skylight.`

For a full PR body, the output should still stay structured and reviewer-first:

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

When the change is riskier or more sensitive, the humor should fade into the
background or disappear entirely.

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for contribution and release guidance.

## License

Licensed under [Apache-2.0](LICENSE).
