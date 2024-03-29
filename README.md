# pon-developer-guide
The Pon developer guide, guidelines, standards and best practices.

## Introduction
Ahoy there fellow Developer 👋 This repository is a good starting point for accelerating your ability to contribute towards our projects, yay! Scouts rules apply, so please keep this page up to date for your colleagues (or future self).

## Best practices

- [The Boy Scout rule](https://www.informit.com/articles/article.aspx?p=1235624&seqNum=6) - Leave your code better than you found it.
- Good, clean and secure code as defined by: "*How much effort is required for another developer of comparable experience to pick up where the previous developer left off to fix, enhance or build upon the source code - without involving the former developer and taking into account the lifetime, quality, security and the business impact of the application.*"
- When reviewing take this cardinal, fundamental law of programming into account: ["It’s harder to read code than to write it."](https://www.joelonsoftware.com/2000/04/06/things-you-should-never-do-part-i/)
- You have an email signature so people know who you are; if you work at Digital Solutions you can use [the generator](https://digitalsolutions.pon.com/signature/), feel free to contact us if you require a custom generator for your OpCo.

## Documentation
A developer should be a able to self-start by using the documentation available in the source code repository. Github is the preferred hub for (a reference to) all related project and product documentation.

## Recommended software
Every crafts person has his/her preferred tools. While you are free to choose what works best for you, below you will find a list of recommended software to aid you in your development activities:

### Generic development

- [Github Enterprise](https://github.com/enterprise) - Pon wide license, managed by Digital Solutions
- [VSCode](https://code.visualstudio.com/)
- [VSCode - Prettier Extension](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)
- [VSCode - StyleLint Plugin](https://marketplace.visualstudio.com/items?itemName=stylelint.vscode-stylelint)
- [VSCode - Live Share](https://marketplace.visualstudio.com/items?itemName=MS-vsliveshare.vsliveshare) - for pair programming
- [VSCode - Code Spell Checker Extension](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker)
- [Commitizen](https://github.com/commitizen-tools/commitizen)

### Javascript

- [VSCode - ESLint Plugin](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint)
- [VSCode - Jest Extension](https://marketplace.visualstudio.com/items?itemName=Orta.vscode-jest)

### NodeJS Recommended software

The [Github package manager](https://docs.github.com/en/packages/working-with-a-github-packages-registry/working-with-the-npm-registry) preferred as NPM registry. 

- [NVM](https://github.com/nvm-sh/nvm) - Node Version Manager

### Golang

- [Linter - GolangCI](https://golangci-lint.run/)

### PHP

- [Linter - phpcs](https://marketplace.visualstudio.com/items?itemName=shevaua.phpcs)

## Logging

Logging is preferred through a library, avoiding printf, console.log, etc. Logging should use logging levels such as "error," "debug," or "notice using the  Elastic Common Schema (ECS).

- [Elastic Common Schema](https://www.elastic.co/guide/en/ecs-logging/overview/current/intro.html)
- [Sentry](https://sentry.io/)

### Key Principles of Secure Logging

- **Avoid Logging Sensitive Data**: Ensure that logs do not contain sensitive information such as passwords, email addresses, or personally identifiable information (PII). Scrubbing or masking such data is crucial to maintaining privacy and security.
- **Regular Review and Audit of Log Files**: Periodically review and audit log files to ensure they contain appropriate information and do not inadvertently capture sensitive data.
- **Secure Log Storage and Access**: Store logs securely and restrict access. Logs can contain sensitive information and should be protected against unauthorized access.
- **Integration with Monitoring Tools**: Utilize tools like Sentry for real-time error tracking and monitoring, enhancing the ability to respond to issues promptly.

### Useful Resources

- [Elastic Common Schema (ECS) Logging](https://www.elastic.co/guide/en/ecs-logging/overview/current/intro.html): Guidelines and standards for structured logging.
- [Sentry](https://sentry.io/): A tool for real-time monitoring and error tracking.

Incorporating these secure logging practices ensures that while logs provide valuable insights for development and maintenance, they do not become a liability by exposing sensitive information.




## Code Repository

Pon has a company-wide GitHub Enterprise license managed by PonIT and Digital Solutions.

### Repository Guidelines

- Avoid creating repositories in your personal account; use the company repository.
- Adhere to the naming conventions for repositories, which should be descriptive and follow the format: `<ProjectName>-<RepoPurpose>`.
- Ensure that the `README.md` file is well-documented, providing an overview of the project, setup instructions, and how to contribute.
- Label issues and pull requests appropriately to help organize and prioritize work.

### Repository Security

- Open sourcing repositories, including making a repository public, must only be done after explicit approval from Pon Privacy & Security.
- Ensure all repositories have the necessary protections in place, such as requiring pull request reviews before merging, and protecting sensitive branches.
- Regularly review user access levels to ensure they are appropriate, removing access for individuals who no longer require it.
- Utilize GitHub's security features such as Dependabot for monitoring dependencies for known vulnerabilities.
- Ensure that no sensitive information, such as passwords or API keys, is committed to the repository. Refer to the [Pon secrets management guidelines](https://drive.google.com/file/d/1q5JVUer6uvnYthcLcQrY1MXxckBfsu7S/view).
- Conduct regular security audits to identify and address potential vulnerabilities.

## Code quality

On the Pon Github account linters are available and maintained by cross-opco developers. It is strongle suggest to use these linters if applicable.
Several code quality tools are in use:

- [Pon guidelines for SonarCloud](https://github.com/pondevelopment/pon-developer-guide/tree/main/tools/sonarcloud)
### Golang style guide
Code formatting is handled in Go automatically by gofmt. The following guides take it some steps further by describing the Do's and Don'ts when writing Go code.
- [Uber Go Style guide](https://github.com/uber-go/guide/blob/master/style.md)
- [Google Go Style guide](https://google.github.io/styleguide/go/)

### Pull requests

Pull requests are an important tool for code quality, in summary the Pon best practices for pull requests are:

- Keep your pull requests small
- The title contains the issue reference
- A pull request handles about a single issue or ticket (linting updates are usually considered a single issue)

For more details please refer to [pull requests best practices](https://github.com/pondevelopment/pon-developer-guide/blob/main/pull-requests.md)

## Security

Pon implements security by design

- [Privacy and Security generic (internal)](https://securityprivacy.pon.com/)
- [Privacy and Security intake (internal)](https://securityprivacy.pon.com/sp-intake/)
- [Security architecture (internal)](https://ponintranet.com/en/pon-arch-subjects/security-architecture/)

## Architecture

Some basic rules apply at Pon for architecture, please refer to the internal documentation details, the following guidelines apply:

- API first
- Mulesoft is the preferred integration tool
- Integrations do not contain business logic
- When using events the [Cloudevent.io](https://cloudevents.io/) structure is preferred

## Guilds

Pon has several guilds which are responsible for guidelines and standards for the guilds subject

- VueJS guild
- Software development guild
- Cloudflare guild
- Architecture guild

## Reading list 📚
Below is a curated list of recommended reading to get you up to speed with internal guidelines, principles, policies, principles and processes. Be sure to familiarise yourself with the content below:

- [Branching guidelines](https://guidelines-git-branching.pages.dev/)
- [Pon Tech Blog](https://medium.com/pon-tech-talk)
- [Development Guidelines](https://pondigitalsolutions.github.io/restful-api-guidelines/)

### Internal (non public)

- [Enterprise Architecture](https://docs.google.com/presentation/d/1kXin45YKe33LdTjuywHIafoU0LTjxzi_-kCaPqcyHbI)
- [IT Architecture](https://ponintranet.com/en/it-architecture/)
- [Software Development at Pon](https://ponintranet.com/en/pon-arch-subjects/software-development/)
- [Software Development Principles](https://docs.google.com/presentation/d/1tcgcg4OAxkFY-WhnsqEQn8J_wQHlADKankxaGlfSfjE)
- [Microservice Principles](https://docs.google.com/presentation/d/1Wtu6kSWgfz6B2anCBWBdqREgRzD55kPGC9pA_ZbSieY)
- [Software Testing & QA Principles](https://docs.google.com/presentation/d/1hhRo2mgResA5cheyEv9czfg4sfQH2Csx-YI_H4ApmQM)
