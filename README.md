# SafeTriage for Make

Security-first AI intake for GitHub issues. SafeTriage turns a new issue into an implementation-ready maintainer brief while treating every character in the issue as untrusted data.

## Why this exists

AI issue triage is useful, but a public issue is an attacker-controlled prompt. A normal "send issue to an LLM, then let it act" workflow can follow instructions embedded in the issue. SafeTriage narrows the agent's authority:

- issue text is explicitly delimited as untrusted evidence;
- the model is prohibited from following instructions found inside that evidence;
- prompt-injection indicators are surfaced to maintainers;
- the agent produces an advisory comment only;
- it never executes code, opens pull requests, exposes secrets, or closes issues;
- the final comment includes uncertainty and missing-information fields.

## What it produces

For every new GitHub issue, SafeTriage posts:

- issue type and suggested priority;
- concise problem statement;
- acceptance criteria;
- missing information and maintainer questions;
- likely affected areas;
- a bounded implementation plan;
- test plan and rollout risks;
- prompt-injection risk assessment;
- explicit note that the result requires human review.

## Make scenario

The scenario uses:

1. GitHub — Watch Issues (created date)
2. Google Gemini AI — Simple Text Prompt (Gemini 2.5 Flash)
3. GitHub — Create a Comment

The GitHub write scope is deliberately limited to creating the advisory comment. The scenario starts inactive and watches new issues from the time it is enabled.

The reproducible scenario definition is in `make/scenario-source.json`. Follow [docs/setup.md](docs/setup.md) to recreate it in another Make team.

## Live project

- Repository: `https://github.com/nobleCk/safetriage-make`
- Make scenario: `SafeTriage — Secure GitHub Issue Intake`
- Polling interval: 15 minutes
- Trigger scope: newly created issues in `nobleCk/safetriage-make`

## Repository topics

Use these GitHub topics after publishing:

`ai-agent`, `ai-automation`, `github-issues`, `issue-triage`, `make-com`, `prompt-injection`, `devsecops`, `gemini`, `no-code`, `open-source`

Suggested repository description:

> Security-first AI agent for GitHub issue intake, prompt-injection detection, and implementation-ready maintainer briefs — built with Make and Gemini.

## Security boundary

SafeTriage is an assistive classifier, not a security control. Model output can be wrong. It must not be granted repository administration, code execution, secret-reading, merge, release, or deployment authority. See [SECURITY.md](SECURITY.md).

## Local prompt checks

The project includes adversarial fixtures so changes to the prompt can be reviewed consistently:

```bash
npm test
```

The test checks structural safeguards in the prompt and verifies that every fixture is represented. It does not claim to prove that any model is immune to prompt injection.

## License

MIT
