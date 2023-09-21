# Functional E2E Testing Best Practices <!-- omit from toc -->

This document outlines what are considered to be best practices for writing and maintaining Functional End to End (E2E) tests for testing the front end of an application.

## Table of contents <!-- omit from toc -->

- [Best practices](#best-practices)
- [Recommended Tooling](#recommended-tooling)
- [References](#references)

## Best practices

|Best Practice| Note |
| - | - |
| Write clear and concise test cases| Test cases should be easy to understand and follow a logical flow. Each test case should test a specific functionality of the application.|
|Use a testing framework| A testing framework such as [Cypress](https://www.cypress.io/) can make it easier to write tets. They also provide helpful tools for interacting with the application and making assertions.|
|Use page objects|The [Page objects model](https://playwright.dev/docs/pom) can help encapsulate the details of the page, making it easier to write tests and maintain them as the application changes.|
|Use data-driven testing|Data-driven testing involves using different sets of data to test the same functionality. This can help uncover edge cases and make sure the application works as expected for different scenarios.|
|Avoid hard-coded values|Hard-coded values can make tests brittle and difficult to maintain. Instead, use variables or constants to store values that are used multiple times in the tests.|
|Use explicit waits|Explicit waits can help make tests more reliable by waiting for specific conditions to be met before continuing. This can help avoid race conditions and synchronization issues.|
|Keep tests independent|Each test should be independent of other tests. This can help avoid dependencies between tests and make it easier to identify and fix issues.|
|Use continuous integration|Continuous integration can help automate the testing process and ensure that tests are run regularly. This can help catch issues early on and prevent regressions.|
|Cross browser testing|It's important to test your scripts in all browsers that your application supports to ensure cross-browser compatibility.|
|Keep tooling up to date|Tooling is constantly being updated, and different versions may have different functionality or behavior. It's important to keep your tooling up to date|
|Handle Errors gracefully|Test suites can encounter errors for a variety of reasons, such as network issues, element not found, or syntax errors. It's important to handle errors gracefully and provide meaningful error messages so that you can quickly identify and fix issues.|

## Recommended Tooling

The following is an overview of tools that are considered suitable for Functional E2E tests.

|Tool|Use case|
| - | - |
|[Cypress](https://www.cypress.io/)| Web application front end |

## References

- [Cypress Testing Tool](https://www.cypress.io/)
- [Page objects model](https://playwright.dev/docs/pom)
