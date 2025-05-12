## kpt release handling process

This is currently a work-in-progress, based on ongoing discussions in the kpt development team.

### Semantic Versioning

We follow semantic versioning. This can mean we have to reject non-backward-compatible changes until
a breaking release in order to preserve backward compatibility.

For kpt this means:

Packages:
* Package format MUST NOT change
* Optional fields can be added

Command line:
* Subcommands MUST NOT be removed
* Subcommands SHOULD NOT change in meaning
* Command line flags MUST NOT be deleted
* Command line flags SHOULD NOT change in meaning

Code: 
* Existing behaviours MUST NOT change

Compatibility with Kubernetes:
TBD

During a major release, all code is subject to revision, but package backward compatibility SHOULD be retained.

### Issue Triaging

Core maintainers take turns triaging the issue queue (week on, week off). The responsibilities of a triaging run are:

#### Issue tagging
* Bug, feature, question/support, documentation
* Simple fixes tagged as “good first issue”
* Good idea but not prioritised: “help wanted”

#### Addressing / channeling questions/support
* We expect discussion, so features, bugs can be tagged as “question” until a full understanding of the need is achieved

#### Allocating bugs to releases
* High severity bugs go into the next patch release
* Otherwise they go into the next minor release

#### Triaging feature requests:
* Differentiate between core features and kpt functions
* Significant features and breaking changes MUST be described in a “kpt improvement proposal”

#### PR Reviews
* TBD

### Merging PRs

A PR can only be merged only if:
* All tests are passing for that PR
* The PR has has approvals from two maintainers from two organizations. The GitHub Review tool is used to approve
* The PR's milestone is set to the current Minor or Patch release. Ensure that in the course of Minor and Patch release work,
  you never merge PRs labeled with the next Major version. For example, while v1 is the current Major version,
  we do not merge PRs labeled with v2.x.

### The release process

Corresponding to SemVer, we have three different types of release:
* Major: 1.0.0, 2.0.0, etc. Breaks compatibility with previous releases.
* Minor: 2.1.0, 2.2.0, etc. Maintains compatibility per our SemVer rules above, but may add new features, fix bugs.
* Patch: 2.1.1, 2.1.2, etc. Maintains compatibility, adds no features, but fixes bugs.

Major releases and Minor releases are done by tagging *main* with the version number, and then running the release scripts (TBD).

Patch versions are done by a more complex process. They start from the release-X.Y branch and cherry-pick from main.
A release branch is forked from the last minor release, and is then maintained in parallel with the *main*:


```
---- v1.3.0 ---- Fix #1 --- Feature #2 --- Fix #3 --- ...  [main]
        \              \                     \
        release-1.3 ---- Fix #1 ------------- Fix #3 --- v1.3.1
```

Only fixes are pulled from `main` onto the `release-X.Y` branch. Features are not.