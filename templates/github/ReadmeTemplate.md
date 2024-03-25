# Project name

Here you can add a project description. Some questions that you can ask to make a description are:
- What is this application?
- What technology is used?
- Is this project dependent on another service/project?

## Table of Contents
1. [Project documentation](#project-documentation)
2. [Project setup](#project-setup)
3. [Available scripts](#available-scripts)
4. [Environments](#environments)

## Project documentation
- Links... (repositories, Jira board, Storyblok, documentation pages, ...)

## Project setup
To setup the project locally, you can follow these steps

### Setup Enviroment Variables
To run this project you have to set some environment variables.
The environment variables can be found in LastPass under * insert name of LastPass *
```
EXAMPLE_VARIABLE_1=<example-variable-1>
EXAMPLE_VARIABLE_2=<example-variable-2>
EXAMPLE_VARIABLE_3=<example-variable-3>
```

## Getting started
Steps that a contributor needs to take to contribute towards the project.

## Environments
This project uses the following environment configurations.

| Environment | Purpose | Domain | Hosting | Deployment |
|-|-|-|-|-|
| `DEV` | Environment to contribute changes to the project | https://localhost:3000 | Local development server | - |
| `PREVIEW` | Verify changes and test integrations | https://*.example.pages.dev/ | Cloudflare Pages (Tenant xxx) | Create a Pull Request to the main branch |
| `PRODUCTION` | Production environment | https://*.example.pages.dev/ | Cloudflare Pages (Tenant xxx) | Merge to the main branch |
