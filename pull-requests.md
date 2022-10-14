Pull Request
=======

### Why do we use a Pull Request workflow?

PRs are a great way of sharing information, and can help us be aware of the changes that are occurring in our codebase. They are also an excellent way of getting peer review on the work that we do, without the need to work in direct pairs.

**Ultimately though, the primary reason we use PRs is to encourage quality contributions to our code repositories**

Done well, the commits (and their attached messages) contained within tell a story to people examining the code at a later date. If we are not careful to ensure the quality of these commits, we silently lose this ability.

**Poor quality code can be refactored. A terrible commit lasts forever.**


### What constitutes a good PR?

A good quality PR will have the following characteristics:

* It will be a complete piece of work that adds value in some way.
* It will have a title that reflects the work within, and a summary that helps to understand the context of the change.
* There will be well written commit messages, with well crafted commits that tell the story of the development of this work.
* Ideally it will be small and easy to understand. Single commit PRs are usually easy to submit, review, and merge.
* The code contained within will meet the [best practices](./README.md#best-practices) wherever possible.

A PR does not end at submission though. A code change is not made until it is merged and used in production.

A good PR should be able to flow through a peer review system easily and quickly.


Submitting Pull Requests
----

### Ensure there is a human readable title and summary

PRs are a Github workflow tool, so it's important to understand that the PR title, summary and eventual discussion are not as trackable as the the commit history. If we ever move away from Github, we'll likely lose this information.

That said however, they are a very useful aid in ensuring that PRs are handled quickly and effectively.

Ensure that your PR title is scannable. People will read through the list of PRs attached to a repo, and must be able to distinguish between them based on title. Include a ticket/issue reference if possible, so the reviewer can get any extra context. Include a reference to the subsystem affected, if this is a large codebase.

It is recommended to use the [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/) commit structure where appropriate. It provides an easy set of rules for creating an explicit commit history; which makes it easier to write automated tools on top of.


### Rebase before you make the PR, if needed

Unless there is a good reason not to rebase - typically because more than one person has been working on the branch - it is often a good idea to rebase your branch to tidy up before submitting the PR.

Use `git rebase -i main # or other reference`

You should not rewrite commits that have been pushed unless you:

* are very sure that no-one else will be affected by you rewriting the branch history
* have an Extremely Good Reason. For example: someone has committed sensitive information (personally identifiable data, passwords and suchlike) and it needs purging from history

### Aim for one succinct commit

In an ideal world, your PR will be one small(ish) commit, doing one thing - in which case your life will be made easier, since the commit message and PR title/summary are equivalent.

If your change contains more work than can be sensibly covered in a single commit though, **do not** try to squash it down into one. Commit history should tell a story, and if that story is long then it may require multiple commits to walk the reviewer through it. Instead, use the "Squash and merge" option to combine all your commits into one a single commit on the target branch.


### Describe your changes well in each commit

Commit messages are invaluable to someone reading the history of the code base, and are critical for understanding why a change was made.

Try to ensure that there is enough information in there for a person with no context or understanding of the code to make sense of the change.

Where external information references are available - such as Issue Tracker Ticket, PR numbers - ensure that they are included in the commit message.

Remember that your commit message must survive the ravages of time. Try to link to something that will be preserved equally well -- another commit for example, rather than linking to main.

** Each commit message should include the reason why this commit was made. **


### Keep it small

Try to only fix one issue or add one feature within the pull request. The larger the pull request is, the more complex it is to review and the more likely it will be delayed. Remember that reviewing PRs is taking time from someone else's day.

If you must submit a large PR, try to at least make someone else aware of this fact, and arrange for their time to review and get the PR merged. It's not fair to the team to dump large pieces of work on their laps without warning.

If you can break up your changes into multiple pull requests then do that.





Reviewing Pull Requests
-----

It's a reviewers responsibility to ensure:

* Commit history is excellent
* Good changes are propagated quickly
* Code review is performed
* Anti patterns are flagged
* Out of scope changes are omitted
* They understand what is being changed, from the perspective of someone examining the code in the future.

### Reviewers are the guardians of the commit history

The importance of ensuring a quality commit history cannot be stressed enough. It is the historical context of all of the work that we do, and is vital for understanding the reasons why changes were made in the past. What is obvious now, will not be obvious 2-3 years in the future.

Without a decent commit history, we may as well be storing all our code in files ending yyyy-mm-dd. The commit history of a code base is what allows people to understand **why** a change was made - the when, what, and where are automatically evident.

When looking at a commit message, ask yourself the question - from the perspective of someone looking at this change without any knowledge of the codebase - 'do I understand *why* this change was made?'



### Keep the flow going

Pull Requests are the fundamental unit of how we progress change. If PRs are getting clogged up in the system, pending review, they are preventing a piece of work from being completed.

As PRs clog up in the system, merges become more difficult, as other features and fixes are applied to the same codebase. This in turn slows them down further, and often completely blocks progress on a given codebase.

There is a balance between flow and ensuring the quality of our PRs. As a reviewer you should make a call as to whether a code quality issue is sufficient enough to block the PR.

Any quality issue that will obviously result in a bug should be fixed.


### We are all reviewers

To make sure PRs flow through the system speedily, we must scale the PR review process. It is not sufficient (or fair!) to expect one or two people to review all PRs to our code. For starters, it creates a blocker every time those people are busy.

Hopefully with the above guidelines, we can all start sharing the responsibility of being a reviewer.

NB: With this in mind - if you are the first to comment on a PR, you are that PRs reviewer. If you feel that you can no longer be responsible for the subsequent merge or closure of the PR, then flag this up in the PR conversation, so someone else can take up the role.

There's no reason why multiple people cannot comment on a PR and review it, and this is to be encouraged.


### Don't add to the PR yourself.

It's sometimes tempting to fix a bug in a PR yourself, or to rework a section to meet coding standards, or just to make a feature better fit your needs.

If you do this, you are no longer the reviewer of the PR. You are a collaborator, and so should not merge the PR.

It is of course possible to find a new reviewer, but generally change will be speedier if you require the original contributor to fix the code themselves. Tell them what you see (the attention point) and what you expect to see (the desired result). Alternatively, if the original PR is not'good enough', raise the changes you'd like to see in your own PR.

### Be supportive
If the code is good, or solves something in a clever way, say so. Call out individual bits of quality - it signposts good practice for others, and rewards the person submitting the request.

On the other hand if you see something that should be changed try to avoid judgemental language like "bad", "should not" as it might trigger an undesirable reaction. Keep you feedback objective:

1. Write a description of what you see (the observation)
2. Explain the result of this observation
3. Give an example of what you expect (the alternative) preferably supported by examples and/or references to documentation.

### It is not the reviewers responsibility to test the code

We are all busy people, and in the case of many PRs against our codebase we are not able or time-permitted to test the new code.

We need to assume that the contributor has tested their code to the point of being happy with the work to be merged to main and subsequently released.

If you, as a reviewer, are suspicious that the work in the PR has not been tested, raise this with the contributor. Ask them to provide evidence of how they tested it. They may not have a mechanism to test it, in which case you may need to help.

If, as a contributor, you know that this change is not fully tested, highlight this in the PR as a comment.


## Some relevant links
* [Github's recommendations for PRs](https://github.com/blog/1943-how-to-write-the-perfect-pull-request)
* [Conventional Commits specification](https://www.conventionalcommits.org/en/v1.0.0/)
* [Commitizen CLI tool](https://github.com/commitizen-tools/commitizen)
