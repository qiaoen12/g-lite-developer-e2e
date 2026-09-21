# G-lite v3.1 E2E protocol

This repository is a controlled identity fixture.

## Roles

- Human Authority: a human GitHub account with repository administration/merge authority. Human Authority performs Genesis/governance and the final squash merge.
- Developer Actor: `g-lite-developer[bot]`. It may implement the authorized Issue Contract, push branches, and open/update pull requests. It must not approve its own Contract, submit the required PR review, change repository governance, or merge.
- Reviewer Actor: `g-lite-reviewer[bot]`. It may independently approve the current Issue Contract and review the current PR HEAD. It must not implement/push development changes, change repository governance, or merge.

## Contract rule

Repository-changing work requires an OPEN GitHub Issue containing Goal, Acceptance, Out of scope, and Authorization.

The Actor that writes or materially edits the current Contract version cannot approve that same Contract version.

## E2E boundary

This fixture exists only to validate identity separation:

Human Genesis → Reviewer Contract approval → Developer branch/push/PR → Reviewer PR review → Human squash merge.

Developer and Reviewer bot roles must never merge.
