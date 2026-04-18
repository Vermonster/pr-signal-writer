# pr-signal-writer

An agent skill for generating reviewer-focused pull request descriptions using explicit PR signals.

Helps both humans and agents answer: what changed, why, where the risk is, how it was validated, what deserves attention, and what still needs judgment.

## Why PR signals?

See [MOTIVATION.md](MOTIVATION.md) for the full analysis of why structured PR signals matter in agentic SDLC workflows.

## Install

```bash
npx skills add Vermonster/pr-signal-writer
```

Or install to specific agents:

```bash
npx skills add Vermonster/pr-signal-writer -a github-copilot
npx skills add Vermonster/pr-signal-writer -a claude-code
npx skills add Vermonster/pr-signal-writer -a cursor
```

## What it does

When activated, the skill:

1. Inspects the git diff, changed files, commit messages, tests, and other available context
2. Classifies the change type, scope, and risk
3. Generates a structured PR description covering intent, mental model, risk signals, evidence, review targeting, operations, and uncertainty
4. Validates the generated signals against the actual diff and fixes mismatches

## What's included

| File | Purpose |
|------|---------|
| `skills/pr-signal-writer/SKILL.md` | Agent instructions for generating and validating PR descriptions |
| `skills/pr-signal-writer/reference/template.md` | Output template the agent follows |
| `skills/pr-signal-writer/reference/pr-signals.md` | Team-facing explanation of PR signals |
| `skills/pr-signal-writer/reference/pr-template.md` | GitHub PR template teams can adopt |
| `skills/pr-signal-writer/reference/pr-signal-check.yml` | CI workflow to enforce required sections |

## Adopting PR signals in your project

To enforce the signal structure on your team's PRs:

1. Copy `reference/pr-template.md` to `.github/pull_request_template.md` in your repo
2. Copy `reference/pr-signal-check.yml` to `.github/workflows/pr-signal-check.yml`
3. Install the skill so your coding agents generate signal-compliant PR descriptions

## Goals

- Avoid rubber-stamp review
- Help humans and agents focus on what matters
- Shift review from raw diff reading toward intent, risk, evidence, and deployability
- Create a shared signal contract for PR authors, reviewers, and tooling

## License

MIT
