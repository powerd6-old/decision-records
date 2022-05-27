# Git standards

## Branches

There are no rules on branch names.

The only consideration when branching is to try to keep branched short-lived and focused to a single task.

Branches that can't be directly tied to a single issue are indicators of problems.

Keep in mind, a single issue can be resolved by multiple pull requests, as long as the intermediate merges don't affect the end-product negatively (Merging a temporary rule change that makes the game unplayable, while working on the last part of it).

## Commit messages

Commit messages should be readable and contain all the context necessary to explain the changes.

Write in all lower-case and keep these rules in mind:

- Use the present imperative form for sentences. (Use "add" instead of "added" or "adding")
- Don't use `feat` or `bug` prefixes, like conventional commits suggests.
- Do not end the commit message with a `.`(dot).

As usual, keep the first line under 50 characters for brevity. More details can be added in the following lines. Remember to add a blank line between the first line and the rest of the lines for ease of reading.

A good indicator that you are committing changes that are unrelated to each other on each step is tending to use "and" or "with" on the commit message. Be mindful of this.


## Issues and Project tasks

Issues are our way of tracking work and problems found in the project.

When creating an issue for a specific repository, or when creating a issue "task" on the main organization project boards, follow these conventions:

- Titles should be clear and short
- On the first line of the issue, detail it's dependencies and blockers. Use the format `Blocked by #x` and `Depends on #x`.
- Ambiguities should be clarified in the body of the issue
- If relevant, link to other documentation.

## Repository settings

### Features

The repository features should be set in the following manner:

- Wiki: 🚫
- Issues: ✅
- Sponsorships: 🚫
- Projects: 🚫
- Preserve this repository: ✅
- Discussions: 🚫

### Pull Requests

The repository pull request settings should be set in the following manner:

- Allow merge commits: 🚫
- Allow squash merging: ✅
  - Default to PR title for squash merge commits: ✅
- Allow rebase merging: 🚫
- Always suggest updating pull request branches: ✅
- Allow auto-merge: 🚫
- Automatically delete head branches: ✅