Pull Request Template
=======

### Step-by-step guide
How to add a pull request template to your GitHub repository

1. Create a `.github` folder in the root of your repository if it doesn’t exist.
2. Inside the `.github` folder, create a markdown file named `pull_request_template.md`.
3. Add the markdown from below to the `pull_request_template.md`.
4. Commit and push your changes.
5. Now, whenever someone creates a pull request in your repository, the content of the `pull_request_template.md` file will automatically appear in the pull request description box.

Remember, you can customize the template according to the specific needs of your project. The template below is just a starting point.

***

```
# Pull Request Template

## Description
*Add a technical summary of the change, specifying which issue is resolved. Also, include the motivation and context behind the change if relevant.*

## Related Tickets & Documents
*Provide links to any related tickets or documents.*

## QA Instructions, Screenshots, Recordings
*Include the steps that need to be followed to test your changes. If applicable, include screenshots or recordings to help explain your PR.*

## Checklist before requesting a review
*Please leave a comment to the reviewer if something is not applicable.*
I have:
- [ ] Reviewed my own code
- [ ] Manually verified the changes meet the requirements
- [ ] This PR only contains one feature
- [ ] Only relevant files were touched
- [ ] Tested on relevant devices and screen sizes
- [ ] Added automated tests
- [ ] WCAG compliant
- [ ] SEO optimized
- [ ] Security checks are passed
- [ ] Code is clean and follows guidelines (https://github.com/pondevelopment/restful-api-guidelines & https://github.com/pondevelopment/pon-developer-guide
- [ ] The correct branch name is used, as per the instructions at https://github.com/pondevelopment/guidelines-git-branching)
- [ ] Code is well documented and if applicable non code related documentation is made
```
