# Commit Cop

[![Build Status](https://travis-ci.com/zieka/commit-cop.svg?branch=master)](https://travis-ci.com/zieka/commit-cop)

> GitHub status check that ensures your pull requests follow the Conventional Commits spec

Enforces [conventional commit messages](https://conventionalcommits.org) with a twist on what is prepended (see below)

## Installation

[github.com/apps/commit-cop](https://github.com/apps/commit-cop)

## How it works

Commit Cop looks for a conventional commit message in:

1. the PR title
2. some or all PR commit

Commit Cop will ignore characters up till the commit type:

-   ✅ - "TICKET#12412312 feat(scope): subject"
-   ✅ - "some stuff we prepend feat: subject"

Commit Cop also makes sure a BREAKING CHANGE is followed by a colon `:`
It will enforce this is both:

1. the PR body
2. any commit message

Commit Cop can also be configured to ensure that JIRA tickets are prepended:

-   ✅ - "ABCD-1234 - feat(scope): subject"
-   ✅ - "ABCD-5678 - feat: subject"

All features can be toggled by **optionally** adding a `commit-cop.yml` file to the `.github` directory of your repo:

```yml
requireTitle: true
requireCommits: 'some'
requirePrBreakingChangeColon: true
requireCommitBreakingChangeColon: true
requireJira: false
```

### requireTitle - `boolean`

-   Set to true to require the title of your PR to be enforced

### requireCommits - `none` | `some` | `all`

-   Set to `some` to require at least 1 of the original commits to be enforced (good for squashes).
-   Set to `all` to have all commits in the PR enforced (good for merges)
-   Set to `none` to not have commits enforced

### requirePrBreakingChangeColon - `boolean`

-   Set to true to require BREAKING CHANGE found in the PR body to be followed by a colon `:`

### requireCommitBreakingChangeColon - `boolean`

-   Set to true to require BREAKING CHANGE found in the any commit message to be followed by a colon `:`

### requireJira - `boolean`

-   Set to true to require a jira ticket be prepended to the commit message in the ALPHACAPS-number format: "WORD-1234 - "
    -   ✅ - "DEV-111 - feat(scope): subject"
    -   ✅ - "DEV-4234 - feat: subject"

## License

[Apache 2.0](LICENSE)
