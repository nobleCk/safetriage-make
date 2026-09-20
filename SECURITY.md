# Security policy

## Threat model

GitHub issue titles and bodies are attacker-controlled. They can contain prompt injection, fake system messages, encoded instructions, links to hostile content, social engineering, or requests to disclose secrets.

SafeTriage assumes:

- all issue content is untrusted;
- model output is untrusted;
- maintainers review recommendations before acting;
- the automation has only the permissions required to read issues and create comments.

## Non-goals

SafeTriage does not prove that an issue is safe, identify every injection, or authorize code changes. It does not fetch URLs from issues, run attachments, execute commands, change repository settings, merge pull requests, or publish releases.

## Deployment rules

1. Use a dedicated GitHub connection with least privilege.
2. Do not place tokens, credentials, private source, or internal instructions in the model prompt.
3. Do not extend the scenario with command execution or unrestricted HTTP fetching.
4. Keep the final GitHub comment clearly labeled as AI-generated and advisory.
5. Review Make execution history for unexpected inputs and output drift.
6. Re-run the adversarial fixtures whenever the system prompt changes.

## Reporting a vulnerability

Open a private GitHub security advisory. Do not include working secrets or private repository data in a public issue.
