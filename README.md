> [!WARNING]  
> This project has been archived and is no longer being actively developed by Elhub.
 
# elhub-phabricator-extensions

[<img src="https://img.shields.io/badge/repo-github-blue" alt="">](https://github.com/elhub/devxp-elhub-phabricator-extensions)
[<img src="https://img.shields.io/badge/issues-jira-orange" alt="">](https://jira.elhub.cloud/issues/?jql=project%20%3D%20%22Team%20Dev%22%20AND%20component%20%3D%20devxp-elhub-phabricator-extensions%20AND%20status%20!%3D%20Done)
[<img src="https://teamcity.elhub.cloud/app/rest/builds/buildType:(id:DevXp_DevXpElhubPhabricatorExtensions_PublishDocs)/statusIcon" alt="">](https://teamcity.elhub.cloud/project/DevXp_DevXpElhubPhabricatorExtensions?mode=builds#all-projects)
[<img src="https://sonar.elhub.cloud/api/project_badges/measure?project=no.elhub.devxp%3Adevxp-elhub-phabricator-extensions&metric=alert_status" alt="">](https://sonar.elhub.cloud/dashboard?id=no.elhub.devxp%3Adevxp-elhub-phabricator-extensions)
[<img src="https://sonar.elhub.cloud/api/project_badges/measure?project=no.elhub.devxp%3Adevxp-elhub-phabricator-extensions&metric=ncloc" alt="">](https://sonar.elhub.cloud/dashboard?id=no.elhub.devxp%3Adevxp-elhub-phabricator-extensions)
[<img src="https://sonar.elhub.cloud/api/project_badges/measure?project=no.elhub.devxp%3Adevxp-elhub-phabricator-extensions&metric=bugs" alt="">](https://sonar.elhub.cloud/dashboard?id=no.elhub.devxp%3Adevxp-elhub-phabricator-extensions)
[<img src="https://sonar.elhub.cloud/api/project_badges/measure?project=no.elhub.devxp%3Adevxp-elhub-phabricator-extensions&metric=vulnerabilities" alt="">](https://sonar.elhub.cloud/dashboard?id=no.elhub.devxp%3Adevxp-elhub-phabricator-extensions)
[<img src="https://sonar.elhub.cloud/api/project_badges/measure?project=no.elhub.devxp%3Adevxp-elhub-phabricator-extensions&metric=coverage" alt="">](https://sonar.elhub.cloud/dashboard?id=no.elhub.devxp%3Adevxp-elhub-phabricator-extensions)

## About

The **elhub-phabricator-extensions** add custom functionality into Elhub's phabricator installation.

This code adds a TeamCity build step for Harbormaster, to be used together with the build feature of
[elhub-teamcity-plugin](https://github.com/elhub/devxp-elhub-teamcity-plugin). Like the former, a lot
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
`DevXp_[id]_CodeReview`, and a herald rule that calls this build plan for every dev-tools-* project. Assuming
the repository name in Phabricator and the Build Configuration name in TeamCity are identical, the build 
configuration ID called will be DevXp_DevToolsElhubPhabricatorExtensions_CodeReview for this project, which
matches with the automatically generated ID in TeamCity.

## Testing

N/A

## Contributing

Contributing, issues and feature requests are welcome. See the
[Contributing](https://github.com/elhub/devxp-elhub-phabricator-extensions/blob/main/CONTRIBUTING.md) file.

## Owners

This project is developed by [Elhub](https://elhub.no). For the specific development group responsible for this
code, see the [Codeowners](https://github.com/elhub/devxp-elhub-phabricator-extensions/blob/main/CODEOWNERS) file.

## License

This project is [MIT](https://github.com/elhub/devxp-elhub-phabricator-extensions/blob/main/LICENSE.md) licensed.
