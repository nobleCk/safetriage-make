# Research rationale

## Demand signal

AI-assisted issue triage is an active category. GitHub publishes an agentic issue-triage workflow that classifies reports, assigns priority, detects likely duplicates, and asks for missing details:

- https://github.github.com/gh-aw/gallery/ai-issue-triage/

Independent projects also package AI triage as GitHub Actions:

- https://github.com/3cgbdg/maintainerbot
- https://github.com/tanwigeetika1618/AI-Issue-Triage

## Gap addressed

Most examples emphasize classification and automation. SafeTriage emphasizes the trust boundary created by public issue text:

- issue content is attacker-controlled;
- suspicious instructions are reported, not executed;
- output is advisory and human-reviewed;
- the scenario has no code execution, browsing, merge, release, or deployment action;
- the repository includes adversarial fixtures and a prompt contract test.

This does not make an LLM immune to prompt injection. It makes the workflow narrower, auditable, and less capable of causing damage when the model is wrong.
