# Repo settings for repositories in the kpt organization

## LICENSE files

Repositories in the kpt organisation are licensed with the Apache License 2.0 for code and CC BY 4.0 for documentation.
To express this every repo should have a [`LICENSE`](LICENSE) and a [`LICENSE-documentation`](LICENSE-documentation).

## Code of Conduct

A [`code-of-conduct.md`](code-of-conduct.md) file with the same content as [this](code-of-conduct.mds). 

## README

Every repo should have a README.md file with at least the following content: 

- Explanation what is the purpose of the repository and how does it fit to the kpt ecosystem
- A "How to contribute?" section with a link to the [contribution guide](https://github.com/kptdev/kpt/blob/main/CONTRIBUTING.md)
- A "License" section with the text "Code is under the Apache License 2.0, documentation is CC BY 4.0." and link to the license files. For an example see the [README.md of the kpt repo](https://github.com/kptdev/kpt/blob/main/README.md?plain=1).
- A "Governance" section with the text "The governance of the kpt project and KRM Functiona Catalog are described in the governance repo.". For an example see the [README.md of the kpt repo](https://github.com/kptdev/kpt/blob/main/README.md?plain=1).
- A "Code of Conduct" section with the text "The kpt project and the KRM Functions Catalog are following the CNCF Code of Conduct. More information and links about the CNCF Code of Conduct are here.". For an example see the [README.md of the kpt repo](https://github.com/kptdev/kpt/blob/main/README.md?plain=1).
- A "CNCF" section with the text "The kpt project including the KRM Functions Catalog is a CNCF Sandbox project.". For an example see the [README.md of the kpt repo](https://github.com/kptdev/kpt/blob/main/README.md?plain=1).
- [OpenSSF Best Practices Badge](#openssf-best-practices)
- FOSSA Licenses Scanning badge and status

## OpenSSF Best Practices

To get the OpenSSF Best Practices

1. [Add](https://www.bestpractices.dev/en/projects/new) the repo to the OpenSSF Best Practices list
2. Add the embedd code from the projects OpenSSF Best Practices page to the README file. For example the kpt repos OpenSSF Best Practices page is [this](https://www.bestpractices.dev/en/projects/10656).

## FOSSA

To get the FOSSA lincese scaning badge and status the repo should be onboarded to FOSSA.s

## CODEOWNERS

A [CODEOWNERS](CODEOWNERS) file listing the responsible code owners of the project.

## MAINTAINERS

A [MAINTAINERS](MAINTAINERS) file pointing to the [maintainers.yaml](https://github.com/kptdev/governance/blob/main/maintainers.yaml) in this repo. 

## Branch protection rules

Set up branch protection rules for the default branch with the following rules:

- Pull request is needed
- Minimum 2 approvals
- Review needed from code owners

## Branch naming

The default branch should be `main`.

## DCO

There is a DCO app set up on kptdev organisation level, so no setting is needed on indivitual repo level.

