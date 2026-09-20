# Setup

## Prerequisites

- a Make account;
- a GitHub account with access to the target repository;
- permission to read issues and create issue comments.

## Install

1. Create a scenario with a 15-minute schedule.
2. Add **GitHub — Watch Issues**, choose `Created Date`, select the owner and repository, set the limit to `2`, and choose `From now on`.
3. Add **Google Gemini AI — Simple Text Prompt** and select `Gemini 2.5 Flash`.
4. Copy `prompts/triage-prompt.md` into the prompt field and map the trigger's issue title and body.
5. Add **GitHub — Create a Comment**, select `Enter manually`, map the trigger's issue ID, and map the Gemini result as the body.
6. Compare the result with `make/scenario-source.json`.
7. Run once against a disposable test issue.
8. Verify the comment has every required heading, contains no secret data, and does not claim to have changed the repository.
9. Activate the scenario only after the test passes.

## Recommended GitHub permissions

Grant only the repository access required to read issue content and create comments. Do not grant administration, actions, deployments, secrets, contents-write, pull-request-write, or release permissions for this workflow.

## Test issues

Create test issues from the files in `fixtures/`. Confirm that ordinary issues produce useful briefs and adversarial issues receive a HIGH injection-risk assessment without following the embedded instructions.
