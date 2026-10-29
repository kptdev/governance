# Governance of the kpt project

This repository contains information about how the kpt project is governed. 

## Governance

All repos of kpt, the repos under the [kptdev](https://github.com/kptdev/) organisation, are under the governance
described here. 
Every repo has two code owners defined in the CODEOWNERS file of the repo and the kptdev GitHub organization has an
[approvers](https://github.com/orgs/kptdev/teams/approvers) and a
[maintainers](https://github.com/orgs/kptdev/teams/maintainers) group. Each PR should have at least 2 approvals and the
approvers should not be from the same company. Each PR should have at least 2 approvals from the members of the
[approvers](https://github.com/orgs/kptdev/teams/approvers) group and at least 1 approvals from a member of the
[maintainers](https://github.com/orgs/kptdev/teams/maintainers) group. Each PR should have an approval from one of the
code owners of the repo. Code owners are defined in the CODEOWNERS file in each repo.

### Contributor ladder

- Anyone with a GitHub account can propose a pull request or raise an issue
- We add persons to the kptdev GitHub organization after the community agreed to add someone in one of our regular
  [commnuity calls](https://github.com/kptdev/kpt/discussions/categories/community-meetings?discussions_q=is%3Aopen+category%3A%22Community+meetings%22). Any community member can propose the addition of anyone who has at least one
  merged PR to any of the repos in the kptdev GitHub organization.
- Any members of the kptdev GitHub organization can be promoted to be a code owner of any repository in the kptdev
  GitHub organization if they contribute at least 10% of the code in a release and if they do not work for a company
  already represented as code owner. Code owners are suggested and agreed in our regular
  [commnuity calls](https://github.com/kptdev/kpt/discussions/categories/community-meetings?discussions_q=is%3Aopen+category%3A%22Community+meetings%22). Agreed code owners are added to the CODEOWNERS file of their repo and will
  be part of the [approvers](https://github.com/orgs/kptdev/teams/approvers) team.
- Maintainers of the project are code owners or community managers suggested and agreed our regular
  [commnuity calls](https://github.com/kptdev/kpt/discussions/categories/community-meetings?discussions_q=is%3Aopen+category%3A%22Community+meetings%22). Agreed maintainers are added to the
  [maintainers](https://github.com/orgs/kptdev/teams/maintainers) group and listed in the
  [maintainer list in the .project repo](https://github.com/kptdev/.project/blob/main/maintainers.yaml)

## Release handling

Release handling is described in the [release handling document](release-handling.md)

## Repository settings

All repos should have the settings described in the [repo settings document](repo-settings.md)

## License

All repos of the kpt project use the [Apache Licence 2.0](https://www.apache.org/licenses/LICENSE-2.0) for code and the
[Creative Commons Attribution 4.0 International license](https://creativecommons.org/licenses/by/4.0/) for
documentation.

## Contributors License Agreement

Contributors of the project do not need to sign a Contributors License Agreement, but it is required to sign-off 
commits as an indication that the [Developer Certificate of Origin](https://developercertificate.org/) is followed.

## Code of Conduct

The kpt project follows the [CNCF Code of Conduct](https://github.com/cncf/foundation/blob/main/code-of-conduct.md).
More information and links about the CNCF Code of Conduct are [here](code-of-conduct.md).

## CNCF

The kpt project is a [CNCF Sandbox](https://www.cncf.io/sandbox-projects/) project.

![CNCF Landscape](https://camo.githubusercontent.com/90a2dafef45d080144637ab69d3d750558aa3b585d9dcab0d8786d6778cbd5df/68747470733a2f2f6c616e6473636170652e636e63662e696f2f696d616765732f636e63662d6c616e6473636170652d686f72697a6f6e74616c2d636f6c6f722e737667)

Visit kpt in the [CNCF Landscape](https://landscape.cncf.io/?selected=kpt&item=provisioning--automation-configuration--kpt).