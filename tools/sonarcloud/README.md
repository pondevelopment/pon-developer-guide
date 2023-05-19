# Pon SonarCloud guide

## Onboarding

SonarCloud licenses go on a per-organization base, where each organization is a single code repository link. So if your organization uses multiple code repositories (Github, Bitbucket, etc.) there will be additional organizations in SonarCloud.

### User management

User management is preferred through repository user synchronization.

### Quality profiles

Quality profiles per language are available in this repository, currently, there is no automated process to share these profiles with all SonarCloud 
organizations.

The following Pon maintained quality profiles are available:

- [Javascript](https://github.com/pondevelopment/pon-developer-guide/blob/main/tools/sonarcloud/sonarcloud_quality_profile_javascript.xml)

### Code Coverage Reporting
SonarCloud supports [reporting of test coverage](https://docs.sonarcloud.io/enriching/test-coverage/overview/) information. This enables teams and Management to get more insight into the code coverage of their project.

To set this up, the steps are as follows:

 1. Switch SonarCloud configuration to CI based analysis (instead of automatic analysis).
 2. Update CI workflow to generate test coverage report.
 3. Add or update `sonar-project.properties` file adding field `sonar.javascript.lcov.reportPaths` that points to the location of the coverage report.
 4. Configure a CI workflow to generate the code coverage report for `main` or `master` and feature branches.


### Analysis Scope

> “Paid plans are tiered according to the total number of lines of code (LOC) analyzed in your private repositories. This LOC calculation does not count code in excluded files (nor does it count blank lines or comments).” 

Ref: https://docs.sonarcloud.io/advanced-setup/analysis-scope/#effect-on-pricing

There are many cases where you do not want to analyze every aspect of every source file in a project. `sonar.sources` and `sonar.tests` fields can be used to define the initial scope in file `sonar-project.properties`

While SonarCloud respects .`gitignore` exclusions you can reduce the scope of the analysis to only the files that you intend to analyze.

### External Analyser Reports
Many languages have dedicated analyzers (also known as linters) that are commonly used to spot problems in code. SonarCloud can integrate the results from many of these external analyzers. Again here CI based analysis is a requirement and the sonar-project.properties file needs to be updated adding the [relevant field](https://docs.sonarcloud.io/enriching/external-analyzer-reports/) to the configuration.

## References

https://docs.sonarcloud.io/organizations/overview/
