This document describes the repository strategy for projects.

### General conventions

The branching strategy utilized for any project follows a similar approach to git flow.

This strategy follows these conventions:

* There is a `main` branch that reflects what is deployed to production
* All new branches have to follow the convention `TYPE/TICKET_NUMBER-DESCRIPTION`
* Allowed **TYPE**: `feat fix release`
* If there is no ticket for your change you have to create one prior to the branch
* When creating new branch you should always branch from `main`

### Merges
* Before merging back to `main` you should open a new `release` branch
* Merge to `release, prod` needs to be triggered via Pull Request (PR)
* Merge to `prod` needs approval from a lead member
* Merge to `release` needs approval from a senior or lead member
* All merge issues should be solved in your `feat, fix` branch before merging to `release`

### Deploys
* Deploys to `qa, prod` are triggered from `release` branches
* Deploys to `qa` needs approval from a senior, qa or lead member
* Deploys to `prod` needs approval from a lead member

### Releases
* `release` branches are deployed to `prod` after `qa` tests are **done** and **approved** 
* `release` branches are merged to `main` after healthcare window
* `release` branches are archived after successfully merged to `main`

### Triggers
* Merges to `release` triggers ci/cd workflow
* Approval steps are triggers after ci/cd is successful
* Tagged merges to `release` triggers deploy approval for both `qa, prod`
* Non-Tagged merges to `release` triggers deploy approval for `qa`

### Tags
* Tags should follow the pattern: `v#.#.#` (`v<major>.<minor>.<patch>`)
* Breaking changes should bump the `major` version
* New features (`feat`) should bump the `minor` version
* Fixes (`fix`) should bump the `patch` version

### Hooks
* [Git Hooks](https://git-scm.com/book/en/v2/Customizing-Git-Git-Hooks) are in place to force code patterns and standards
* Commits have to follow [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/#specification) pattern  (e.g. `feat(game_over): Add game over logic`)
* Commits are only allowed when code linting has successfuly compiled the code following the standards in place

## Unity Games Projects

For game projects using Unity it is recommended to make the minimal changes to scenes as possible and avoid conflicts in scenes.
That is due to the fact that managing merges of scenes are really difficult and up to this point I haven't found any good tools to do that nor implemented one myself yet.

