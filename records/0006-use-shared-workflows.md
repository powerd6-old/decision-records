# Use shared workflows

## Status

Accepted

## Context

Generic tasks such as compiling typescript projects, publishing packages, compiling modules and attaching their results to releases are repetitive and can be written once ans used elsewhere.

In addition to these more practical things, smaller repeated tasks like linting, running tests on PRs, setting up repository permissions, etc can be shared across multiple repositories.

The two main options are to create [reusable workflows](https://docs.github.com/en/actions/using-workflows/reusing-workflows) or [starter workflows](https://docs.github.com/en/actions/using-workflows/sharing-workflows-secrets-and-runners-with-your-organization).

While logic points that the *reusable workflows* solution would be better, in actuality it has more limitations and issues that the *starter workflows* don´t have.

Considering that reusable workflows can't be chained together, and that they require secrets and environment variables to be passed as "normal variables" introduce a security risk. This is not the case for starter workflows.

On the other hand, starter workflows allow for workflow definitions to drift apart, creating an opportunity for repository-specific workflows to be created, taking us back to the state before this change is implemented.

## Decision

Considering that for both cases good hygiene is necessary, the drawbacks from reusable workflows are enough to discredit it.

A repository of starter workflows will be created, making available a multitude of repeated tasks and workflows for repository owners to start from.

Whenever modifications are required on these workflows, careful consideration should be taken to access if they are indeed a unique case, or could be contributed back to the starter workflow repository.

## Consequences

- Common tasks can be automated once and then leveraged in multiple projects.
- Project-specific changes will be harder to integrate without risking widespread impact
