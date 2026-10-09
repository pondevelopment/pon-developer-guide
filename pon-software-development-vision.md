# Vision of software development at Pon

## 1 Business understanding becomes a core skill

Product teams combine business knowledge with technical judgment to decide what to build. They challenge assumptions with users throughout development and measure success by improvements in business outcomes.

## 2 Interfaces adapt to the user’s intent

AI interprets what users want to achieve and generates or adapts the interface to support their task. Following rule 4, the underlying systems continue to enforce business rules and permissions. Product teams validate that these interfaces make work easier and keep users in control. The design question becomes: what does this person need to understand or do at this moment?

## 3 Human judgment moves to the system level

AI writes and checks code. A named person is accountable for every change that ships, either by approving it or by approving the conditions under which changes of its kind ship automatically. Human judgment concentrates on changes that alter what the software is meant to do and on failures that are hard to detect or undo. Product teams validate business outcomes, integrations and data access, and keep the understanding needed to investigate what ships.

## 4 AI and deterministic software work together

AI interprets context and coordinates actions through software that executes defined operations and enforces business rules. Product teams design this interaction, including its boundaries and exception handling. Following rule 5, the business rules this software enforces are formalized and checked, and teams test the complete workflow against expected business outcomes.

## 5 Quality means proving the software fulfils its purpose

Following rule 3, product teams define expected outcomes, unacceptable failures and the evidence needed for release. Business rules are supplied or validated by domain experts and business owners, and formalized in a proof-checked language such as Lean. This structure enforces the soundness of the rules as stated: they are consistent, give every declared case an outcome and satisfy the properties the business requires. The specification is the basis for the code and the independent reference against which the code is checked. AI generates and runs extensive end-to-end tests against the expected outcomes, covering real business workflows and failure scenarios. A check is only as trustworthy as its independence from the work it verifies.

## 6 AI changes what we build, buy or reuse

Lower implementation effort makes tailored software a more viable alternative to existing packages. When adapting a package costs more than building what we need, product teams should reconsider the package. We compare business fit and total cost of ownership, including integration, security and ongoing support. Cheap code generation alone does not justify owning another system.

## 7 Purpose determines the programming language

Following rule 3, AI’s role in implementation allows us to choose languages and frameworks based on the software’s purpose and operating requirements, rather than developers’ existing skills.

## 8 Development tools are a means to an end

Editors, terminals and frameworks serve the purpose of building useful software. Following rule 3, AI increasingly operates these tools while product teams direct the work. We choose and change tools based on how well they help us achieve the intended outcomes.

## 9 Code standards must justify their value

Following rules 3 and 5, we judge code by how reliably the software fulfils its purpose and how effectively we can change and operate it. We retain standards that support these outcomes and let go of conventions whose only purpose is to accommodate manual coding.

## 10 Handcrafted code must earn its place

Human-written or hand-optimised code is an exception, justified by business requirements such as speed, scale or operating cost. Following rule 5, product teams verify through testing that it delivers the required benefit.

## 11 The traditional separation between product management, design and engineering disappears

We embrace product teams in which people work across these boundaries, supported by AI. Specialist expertise remains valuable, and teams share responsibility from problem definition through operation, with clear accountability for business outcomes.

## 12 Small product teams have the freedom to move quickly

We actively remove organisational barriers, including unnecessary approvals, handovers and dependencies between teams. Product teams make decisions close to their businesses within shared requirements for security, data access and integration. Shared capabilities reduce the work each team must do, while coordination and approvals remain proportionate to risk. Those accountable for a release have a say in its pace and in how thoroughly it is checked.

## 13 AI capacity is part of our development capacity

We give product teams access to capable models and sufficient usage capacity to build, test and improve software. We assess this investment against business value, delivery time and total cost, and avoid limits that cost more in lost productivity than they save.

## 14 Model choice follows task performance and total cost

Product teams evaluate models on the quality and cost of completing the task successfully, including retries, delays and human correction. Following rule 5, we verify performance on representative tasks and reassess our choices as models improve.

## 15 Different development approaches can coexist

We move towards this vision while accepting that traditional and AI-driven development can operate alongside each other across teams and systems. Product teams choose the approach and pace of transition based on business value and risk. Existing software and expertise retain their place where they serve the business, while we invest in the skills and capabilities needed for this vision.

This vision is inspired by Thorsten Ball’s essay [What I believe about the future of software development](https://thorstenball.com/blog/2026/09/19/what-i-believe-about-the-future-of-software-development/). The fifteen rules above build on that inspiration and set our direction at Pon.
