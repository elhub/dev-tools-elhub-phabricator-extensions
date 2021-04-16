# elhub-phabricator-extensions

<!-- PROJECT SHIELDS -->
![TeamCity Build](https://teamcity.elhub.cloud/app/rest/builds/buildType:(id:Tools_DevToolsPhabricatorExtensions_AutoRelease)/statusIcon "TeamCity CI")
[![Quality Gate Status](https://sonar.elhub.cloud/api/project_badges/measure?project=no.elhub.tools%3Adev-tools-elhub-phabricator-extensions&metric=alert_status)](https://sonar.elhub.cloud/dashboard?id=no.elhub.tools%3Adev-tools-elhub-phabricator-extensions)
[![Lines of Code](https://sonar.elhub.cloud/api/project_badges/measure?project=no.elhub.tools%3Adev-tools-elhub-phabricator-extensions&metric=ncloc)](https://sonar.elhub.cloud/dashboard?id=no.elhub.tools%3Adev-tools-elhub-phabricator-extensions)

[![Vulnerabilities](https://sonar.elhub.cloud/api/project_badges/measure?project=no.elhub.tools%3Adev-tools-elhub-phabricator-extensions&metric=vulnerabilities)](https://sonar.elhub.cloud/dashboard?id=no.elhub.tools%3Adev-tools-elhub-phabricator-extensions)
[![Bugs](https://sonar.elhub.cloud/api/project_badges/measure?project=no.elhub.tools%3Adev-tools-elhub-phabricator-extensions&metric=bugs)](https://sonar.elhub.cloud/dashboard?id=no.elhub.tools%3Adev-tools-elhub-phabricator-extensions)
[![Code Smells](https://sonar.elhub.cloud/api/project_badges/measure?project=no.elhub.tools%3Adev-tools-elhub-phabricator-extensions&metric=code_smells)](https://sonar.elhub.cloud/dashboard?id=no.elhub.tools%3Adev-tools-elhub-phabricator-extensions)

## Table of Contents

* [About](#about)
* [Getting Started](#getting-started)
  * [Prerequisites](#prerequisites)
  * [Installation](#installation)
* [Usage](#usage)
* [Testing](#testing)
* [Roadmap](#roadmap)
* [Contributing](#contributing)
* [Owners](#owners)
* [License](#license)

## About

The **elhub-phabricator-extensions** add custom functionality into Elhub's phabricator installation.

This code adds a TeamCity build step for Harbormaster, to be used together with the build feature of
[elhub-teamcity-plugin](https://github.com/elhub/dev-tools-elhub-teamcity-plugin). Like the former, a lot
of the code here is forked from the TeamCity-Phabricator-Plugin of
[x-lab-ltd](https://github.com/x-lab-ltd/Teamcity-Phabricator-Plugin) though in this case with some functional
changes. In particular, our version includes the possibility of adding an [id] wild card into the build step,
which allows us to make more generic build plans.

## Getting Started

### Prerequisites

* Phabricator

### Installation

The simplest way to install this is to simply copy the files from the src directory into
`phabricator/src/extensions/`. 

## Usage

Once the files have been installed, you should be able to create build steps to run jobs in TeamCity.

In this build step, you specify the TeamCity URI and the Build Job ID you want to trigger with the build plan.
In the Build Job, you can insert `[id]` into the string which will then be replaced with repository name in
camelcase form.

Example:
The Elhub TeamCity instance has a "Tools" project, where all the dev-tools projects are built. In each case, we
want to trigger the "CodeReview" build configuration, which handles our diff workload.

We can then create a build plan in Phabricator with the TeamCity build configuration
`Tools_[id]_CodeReview`, and a herald rule that calls this build plan for every dev-tools-* project. Assuming
the repository name in Phabricator and the Build Configuration name in TeamCity are identical, the build 
configuration ID called will be Tools_DevToolsElhubPhabricatorExtensions_CodeReview for this project, which
matches with the automatically generated ID in TeamCity.

## Testing

N/A

## Roadmap

See the [open issues](https://jira.elhub.cloud/issues/?jql=project%20%3D%20TD%20AND%20component%20%3D%20elhub-phabricator-extensions%20AND%20resolution%20%3D%20Unresolved) for a list of proposed features (and known issues).

## Contributing

Contributing, issues and feature requests are welcome. See the
[Contributing](https://github.com/elhub/dev-tools-elhub-phabricator-extensions/blob/main/CONTRIBUTING.md) file.

## Owners

This project is developed by [Elhub](https://elhub.no). For the specific development group responsible for this
code, see the [Codeowners](https://github.com/elhub/dev-tools-elhub-phabricator-extensions/blob/main/CODEOWNERS) file.

## License

This project is [MIT](https://github.com/elhub/dev-tools-elhub-phabricator-extensions/blob/main/LICENSE.md) licensed.
