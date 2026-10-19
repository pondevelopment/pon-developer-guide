# Pull Request Approval Policy

## Why this policy exists

Pull requests should protect quality **and** preserve flow. If every change waits for the same level of review, low-risk work gets stuck in the queue and lead time grows for no good reason.

This policy sets clear boundaries for when an Individual Contributor may merge their own pull request, when peer approval is expected, and when stronger review is mandatory.

This policy assumes changes still go through a pull request to a protected branch. It changes the **approval expectation**, not the expectation to create a PR.

The goal is simple:

* keep the benefits of code review
* reduce avoidable waiting time
* focus human attention where risk is highest
* support modern AI-assisted and agentic development without reducing accountability


## Core principles

1. **Risk determines review depth.** The higher the risk, the stronger the approval requirement.
2. **The author remains accountable.** Using AI tools, pair programming, or automated refactoring tools does not transfer responsibility away from the person opening the PR.
3. **Automated checks come first.** If the repository has tests, linting, security checks, or deployment validation, they must pass before merge unless an incident process explicitly allows otherwise.
4. **Repository protections win.** If branch protection, CODEOWNERS, or compliance rules require more approvals than this document, follow the stricter rule.
5. **Flow matters.** Review is a quality mechanism, not a waiting ritual. Low-risk changes should move quickly.

## Approval policy

Use the highest applicable level below. If a PR contains several kinds of change, apply the strictest approval rule.

| Change level | Typical examples | Approval requirement | Conditions |
| --- | --- | --- | --- |
| **Level 0: Trivial and non-functional** | Documentation only, spelling fixes, comments, formatting-only changes, renames with no behaviour change, generated file refresh with no logic change | **No peer approval required** | Author reviews the full diff, all required checks pass, and the PR does not touch protected or high-risk areas |
| **Level 1: Low-risk implementation change** | Small refactor with unchanged behaviour, isolated bug fix with test coverage, feature-flagged change, dependency patch/minor update with green checks | **Peer review requested, but author may merge after the response window if nobody responds** | PR explains why it is low risk, required checks pass, no unresolved comments, and the author has asked for review in the normal team channel |
| **Level 2: Standard product or code change** | Most feature work, business logic changes, API changes, schema changes, test strategy changes, moderate refactors | **At least 1 peer approval required** | Reviewer should understand the change and be comfortable owning the merge decision |
| **Level 3: High-risk or sensitive change** | Authentication, authorization, permissions, payments, personal data handling, security controls, infrastructure or deployment changes, shared platform code, irreversible migrations | **At least 2 approvals, including an owner or domain-capable reviewer where relevant** | Consider synchronous review for larger or riskier changes |

## Response window for low-risk changes

For **Level 1** changes, the default response window is **4 business hours** during the team's normal working day.

If no reviewer has responded after that window, the author may merge **provided that**:

* the PR was clearly marked or described as low risk
* all required automated checks passed
* there are no unresolved review comments
* the author has reviewed the diff carefully
* the change does not affect a protected or high-risk area

## What cannot be self-merged

The following always require peer approval, even if the code change looks small:

* changes to authentication, authorization, or security controls
* changes affecting personal data, finance, legal, or compliance requirements
* database migrations that are destructive, hard to reverse, or operationally risky
* changes to the production configuration for CI/CD pipelines or infrastructure
* changes in shared libraries or platform components used by multiple teams
* changes where the author is not confident about the impact
* any change where branch protection or CODEOWNERS require approval

## Expectations for authors

Before merging any pull request, the author should be able to say yes to all of the following:

* I understand the change and could explain it without relying on an AI tool to do that for me.
* I reviewed the full diff, including generated files and configuration changes.
* I ran or observed the relevant automated checks.
* I added or updated tests where the change materially affects behaviour.
* I called out risks, rollout notes, and follow-up work in the PR description where relevant.
* I chose the approval level based on risk, not based on urgency or convenience.

## Expectations for reviewers

Reviewers help the team maintain both quality and throughput.

* If you can review, respond promptly.
* If you cannot review in a reasonable time, decline quickly so the author can ask someone else.
* Block only for issues that matter: correctness, security, maintainability, operability, or clarity of intent.
* Prefer comments that improve the change without unnecessarily extending cycle time.

## AI-assisted development

AI assistance does **not** lower the review bar.

If anything, AI can increase the volume and speed of change, which makes risk-based approval even more important. The human author is still responsible for:

* understanding the code being merged
* validating that the solution works
* checking for security, privacy, and operational impact
* choosing the correct approval level

Large AI-generated changes should not be treated as trivial just because they were fast to produce.

## Examples

### May self-merge immediately

* README clarification
* typo fix in UI text
* formatting-only change produced by a standard formatter
* comment cleanup

### May self-merge after the response window

* small refactor with unchanged tests
* dependency patch update with green CI and no breaking changes
* isolated bug fix in a non-sensitive area with clear test coverage

### Must wait for approval

* new endpoint or API contract change
* permission or role logic change
* a destructive database migration
* production deployment pipeline update
* change affecting customer data handling

## Recommended repository settings

Where possible, repositories should support this policy with configuration:

* require pull requests before merging to protected branches
* require status checks to pass
* use CODEOWNERS for sensitive areas
* allow maintainers to bypass approval only where an agreed incident process exists
* use labels such as `trivial`, `low-risk`, and `high-risk` to make review expectations visible

## Emergency changes

Production incidents sometimes require immediate action. In those cases, follow the incident process defined by the team or platform owner.

Where an emergency bypass is used:

* keep the change as small as possible
* document why the normal approval path was bypassed
* request retrospective review after the incident is stable


## Final note

This policy is intended to create **clarity, trust, and speed**. It should reduce unnecessary waiting without normalizing careless merges.

When in doubt, choose the safer path and ask for review.
