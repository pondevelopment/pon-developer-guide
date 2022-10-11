# pon-developer-guide
The Pon developer guide, guidelines, standards and best practices.

## Introduction
Ahoy there fellow Developer 👋 This repository is a good starting point for accelerating your ability to contribute towards our projects, yay! Scouts rules apply, so please keep this page up to date for your colleagues (or future self).

## Best practices

- [The Boy Scout rule](https://www.informit.com/articles/article.aspx?p=1235624&seqNum=6) - Leave your code better than you found it.
- Good, clean and secure code as defined by: "*How much effort is required for another developer of comparable experience to pick up where the previous developer left off to fix, enhance or build upon the source code - without involving the former developer and taking into account the lifetime, quality, security and the business impact of the application.*"
- When reviewing take this cardinal, fundamental law of programming into a account: ["It’s harder to read code than to write it."](https://www.joelonsoftware.com/2000/04/06/things-you-should-never-do-part-i/)

## Documentation
A developer should be a able to self-start by using the documentation available in the source code repository. Github is the preferred hub for (a reference to) all related project and product documentation.

## Recommended software
Every crafts person has his/her preferred tools. While you are free to choose what works best for you, below you will find a list of recommended software to aid you in your development activities:

### Generic development

- [Github Enterprise](https://github.com/enterprise) - Pon wide license, managed by Digital Solutions
- [VSCode](https://code.visualstudio.com/)
- [VSCode - Prettier Extension](https://marketplace.visualstudio.com/items?itemName=SimonSiefke.prettier-vscode)
- [VSCode - StyleLint Plugin](https://marketplace.visualstudio.com/items?itemName=stylelint.vscode-stylelint)
- [VSCode - Live Share](https://marketplace.visualstudio.com/items?itemName=MS-vsliveshare.vsliveshare) - for pair programming
- [Commitizen](https://github.com/commitizen-tools/commitizen)

### Javascript

- [VSCode - ESLint Plugin](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint)
- [VSCode - Jest Extension](https://marketplace.visualstudio.com/items?itemName=Orta.vscode-jest)

### NodeJS Recommended software

The [Github package manager](https://docs.github.com/en/packages/working-with-a-github-packages-registry/working-with-the-npm-registry) preferred as NPM registry. 

- [NVM](https://github.com/nvm-sh/nvm) - Node Version Manager

## Code repository

Pon has a company wide Github Enterprise license managed by PonIT and Digital Solutions. 

## Code quality

On the Pon Github account linters are available and maintend by cross-opco developers. It is strongle suggest to use these linters if applicable.
Several code quality tools are in use:

- [Pon guidelines for SonarCloud](https://github.com/pondevelopment/pon-developer-guide/tree/main/tools/sonarcloud)

## Security

Pon implements security by design

- [Security architecture (internal)](https://ponintranet.com/en/pon-arch-subjects/security-architecture/)

## Architecture

Some basic rules apply at Pon for architecture, please refer to the internal documentation details, the following guidelines apply:

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
