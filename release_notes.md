# Loop Client Release Notes
This file tracks release notes for the loop client. 

### Developers: 
* When new features are added to the repo, a short description of the feature should be added under the "Next Release" heading.
* This should be done in the same PR as the change so that our release notes stay in sync!

### Release Manager: 
* All of the items under the "Next Release" heading should be included in the release notes.
* As part of the PR that bumps the client version, cut everything below the 'Next Release' heading. 
* These notes can either be pasted in a temporary doc, or you can get them from the PR diff once it is merged. 
* The notes are just a guideline as to the changes that have been made since the last release, they can be updated.
* Once the version bump PR is merged and tagged, add the release notes to the tag on GitHub.

## Next release

#### New Features

* `--private` flag is now available on the `loop in` command, meaning users can
  now loop in to private nodes! This was implemented in [#415](https://github.com/lightninglabs/loop/pull/415)
  and has an implementation of LND's hop hints creation feature for the time
  being. The flag is also available in `loop quote in` as an extension.
* `--route_hints` has also been added on the `loop in` and `loop quote in` cli
  commands, and was also include in [#415](https://github.com/lightninglabs/loop/pull/415).
  While the `--private` flag autogenerates routehints to assist the payer (Lightning Labs),
  `--route_hints` allows the user to feed their own crafted versions if they so please.

#### Breaking Changes

* Failing to load configuration file specified by `--configfile` for any
  reason is now hard error. If you've used `--configfile` to mean "optional
  extra configuration" you will need to create an empty file. This was done in
  [#413](https://github.com/lightninglabs/loop/pull/413) to improve error
  reporting and avoid confusion. Similarly, failure to load any configuration
  file for reason other than NotFound is hard error, though this is not strictly
  breaking because such scenario would be already broken later.

#### Bug Fixes

#### Maintenance

* Updated compile time dependencies of `lnd` to `v0.14.0-beta.rc1`.