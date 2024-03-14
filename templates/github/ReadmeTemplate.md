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
- [Jira board](https://pondevelopment.atlassian.net/jira/projects)
- [GitHub](https://github.com/pondigitalsolutions)
- Other... (projects you're dependent on, Storyblok, documentation pages, ...)

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

### Generate local SSL

We use a local SSL so that we can use the preview in Storyblok when doing changes locally.
Use the following command to generate a local SSL:

```
openssl genrsa 2048 > localhost.key
chmod 400 localhost.key
openssl req -new -x509 -nodes -sha256 -days 365 -key localhost.key -out localhost.crt
```

After installing the local SSL, you can run your local environment on https using the following command:

```
npm run dev-ssl
```

### Install dependencies
Project dependencies can be installed using the following command:
```
npm run install
```

## Available scripts
In the project directory, you can run:

### `npm start`
Runs the app in the development mode.
Open http://localhost:3000 to view it in your browser.

The page will reload when you make changes.
You may also see any lint errors in the console.

### `npm test`
Launches the test runner in the interactive watch mode.

## Environments
This project uses the following environment configurations.

| Environment | Purpose | Domain | Hosting | Deployment |
|-|-|-|-|-|
| `DEV` | Environment to contribute changes to the project | https://localhost:3000 | Local development server | - |
| `PREVIEW` | Verify changes and test integrations | https://*.example.pages.dev/ | Cloudflare Pages (Digital Solutions Tenant) | Create a Pull Request to the main branch |
| `PRODUCTION` | Production environment | https://example.com | Cloudflare Pages (Digital Solutions Tenant) | Merge to the main branch |
