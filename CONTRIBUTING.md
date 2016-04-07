# Contributing to Keystone
The following details the expectations and guidelines for incoming contributions to this project.
To better serve those who intend on contributing, we feel it is important that the acceptance criteria
for acceptable code submissions be defined for reference.  In addition to the rules and guidelines below, we expect 
all contributors will adhere to the [contributor covenant][]

Please make sure you have read the `README` for your given project.

[contributor covenant]: http://contributor-covenant.org/version/1/2/0/

## Pull Requests
When making a PR, the following criteria should be met:

1. Your PR has an issue created that has been reviewed by the Keystone maintaining team.
2. Your branch name follows the expected naming convention `{issue-type}/issue-{issueNumber}-description`, e.g. _bug/issue-111-fix-button-style_.  Issue type will be determined by the label added to the issue in Github by a maintainer.
3. Your PR has passed the build (linting and unit testing checks).
4. Unit tests have been added for code changes.
5. There are no merge conflicts.
6. The entire body of work from the issue has been completed.
7. The issue being resolved should be included in the description of the PR.
8. If applicable, make sure the project's README is kept up-to date.

## Dependency Management
When adding or updating NPM dependencies, please follow these rules

1. If you have added any dependencies to your project, links to their repo and an explanation of their need should 
be provided.
2. Please make sure your dependencies are installed correctly.  `dependencies` are those modules that are explicitly
needed by this package in order to run.  `devDependencies` are only needed for local development or building the 
package.  The rule of thumb is, _if it goes in src/index.js it's a dependency, otherwise it's a devDependency_.
3. NPM package versions should not contain `~` or `^` as we only want to pin to specific versions.  They should be
organized alpha sorted ascending.

## Commit Messages
Commit messages are important when looking at the work history of an application.  Please consider the following as you 
commit your work:

1. Use the present tense ("Add feature" not "Added feature").
2. Use the imperative mood ("Move cursor to..." not "Moves cursor to...").
3. Limit the first line to 72 characters or less.
4. Reference issues and pull requests liberally.

All PRs will be squashed merged through GitHub.

## Continuous Integration
Keystone projects enforce a number of best practices such as JS linting and unit testing.  Each PR will be run against
a continuous integration server with the result getting marked in the PR as pass / fail.  Failing builds will result
in your pull request getting declined.  There will be a `gulp build` task in each project that you can run locally
to test before submitting a PR.
