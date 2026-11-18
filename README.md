# repops

Cross-repository maintenance ("gardening") for `ajchemist` repositories:
fork/upstream drift briefings and other chores that do not belong in the
repositories they act on.

## Access model

Workflows act on other repositories as the **`ajchemist-repops`** GitHub App.
Each run mints a short-lived installation token scoped to the one target
repository it needs. The App only reaches repositories it is installed on;
add a repository to the installation to bring it under repops.

| Setting | Where |
|---|---|
| App ID | `REPOPS_APP_ID` in each workflow (not secret) |
| Private key | Actions secret `REPOPS_APP_PRIVATE_KEY` |

Commits created through the GraphQL `createCommitOnBranch` API are signed by
GitHub and show as Verified; plain `git push` commits are unsigned.

## Workflows

- `push-smoke.yml` — manual check that repops can push to a target repository.
