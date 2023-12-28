# OWASP

## What is OWASP?

The **Open Web Application Security Project** (OWASP) is a non-profit foundation that works to improve the security of software. It provides impartial, practical, and free information about computer and internet applications. OWASP is renowned for its comprehensive materials on web application security.

## Why OWASP Matters for Developers

As a developer, understanding OWASP guidelines is crucial. These guidelines serve as a cornerstone in developing secure web applications, protecting both users and organizations from potential security threats. By adhering to OWASP standards, developers can mitigate common vulnerabilities and enhance the overall security posture of their applications.

## OWASP's Dynamic Nature

A key characteristic of OWASP is its dynamic nature. The guidelines and recommendations are updated yearly to reflect the evolving landscape of web security. This ensures that the information remains relevant and effective against the latest security threats. Additionally, OWASP provides distinct guidance for different types of applications, with specific sections dedicated to **Web Application Security** and **API Security**, addressing the unique challenges and best practices for each.

## Focus on Relevant Vulnerabilities

In this chapter, special attention will be given to the most relevant and prevalent vulnerabilities as identified by OWASP. This approach ensures that we concentrate on the areas of highest impact and risk in web and API security.


# OWASP API Security

The header of each chapter title refers to the OWASP reference as published on owasp.org.

## API4:2023 Unrestricted Resource Consumption

Satisfying API requests requires resources such as network bandwidth, CPU, memory, and storage. Sometimes required resources are made available by service providers via API integrations, and paid for per request, such as sending emails/SMS/phone calls, biometrics validation, etc.

## Do's

- **Implement Cost Alerts**: Set up alerts for unusual spikes in resource usage and costs to prevent unexpected expenses.
- **Enforce Size Limits**: Establish maximum size limits for file downloads and uploads to prevent overconsumption of resources.
- **Monitor API Usage**: Regularly monitor API usage patterns to identify and mitigate potential abuse or inefficiencies.
- **Plan for Scalability**: Design your API and resource allocation with scalability in mind, accommodating varying loads without compromising performance.
- **Use Efficient Data Formats**: Opt for data formats that balance between size and functionality to reduce unnecessary bandwidth usage.

## Don'ts

- **Ignore Resource Limits**: Do not overlook the limits of your resources, such as bandwidth, memory, and storage capacity.
- **Neglect Cost Monitoring**: Avoid the absence of monitoring tools for resource consumption costs, which can lead to budget overruns.
- **Allow Unlimited Access**: Do not permit unrestricted access to API resources, especially for operations that consume significant resources.
- **Overlook Fail-Safes**: Avoid lacking fail-safe mechanisms like maximum cost allowances or automatic shutoffs in case of excessive usage.
- **Disregard File Size Changes**: Do not ignore changes in file sizes, especially for frequently accessed or large files, as this can significantly impact resource usage.
- **Compromise on Security**: Never compromise security measures in an attempt to reduce resource usage; both aspects should be balanced.

### Example

A service provider allows clients to download arbitrarily large files using its API. These files are stored in cloud object storage and they don't change that often. The service provider relies on a cache service to have a better service rate and to keep bandwidth consumption low. The cache service only caches files up to 15GB.

When one of the files gets updated, its size increases to 18GB. All service clients immediately start pulling the new version. Because there were no consumption cost alerts, nor a maximum cost allowance for the cloud service, the next monthly bill increases from US$13, on average, to US$8k.


## API8:2023 Security Misconfiguration

Attackers will often attempt to find unpatched flaws, common endpoints, services running with insecure default configurations, or unprotected files and directories to gain unauthorized access or knowledge of the system. Most of this is public knowledge and exploits may be available.

### Mitigation

Cloudlfare and security scans will provide partial (!) mitigation. Configure these tools accordingly.

### **Cache only what you'd comfortably share in a public Slack channel.**

In the context of API security and web application performance, a fundamental principle to adhere to is: **"Never cache unless it's absolutely safe."** This cautious approach is crucial because improper caching can lead to the unintended exposure of sensitive data, such as private communications or personal information. The risk is particularly high with browser or proxy caching.

The following HTTP headers play a pivotal role in ensuring that caching is handled securely:

1. **Cache-Control**: Used to specify directives for caching mechanisms in both requests and responses.
2. **Expires**: Defines the date/time after which the response is considered stale.
3. **Pragma**: Includes implementation-specific directives that might apply to response caching.
4. **Vary**: Determines how to match future request headers to decide whether a cached response can be used rather than requesting a fresh one.
5. **ETag**: Used for validating cached responses; it helps to determine if the content has changed since the last fetch.

Before enabling caching for any data, especially in API responses, critically assess the sensitivity of the information. If there's any doubt about its security, err on the side of caution and do not cache. Keep in mind the rule of thumb: **"Never cache unless it's absolutely safe"** to ensure that performance optimizations do not come at the cost of compromising data security and user privacy.

### Do's

- **Regularly Update and Patch**: Keep all systems, software, and dependencies up-to-date with the latest security patches.
- **Use Secure Configurations**: Always start with secure configurations, and avoid leaving systems in their default insecure state.
- **Conduct Security Scans**: Regularly perform security scans to detect and rectify misconfigurations or unpatched vulnerabilities.
- **Implement Robust Access Control**: Restrict access to files, directories, and services to authorized personnel only.
- **Utilize Security Headers**: Implement necessary HTTP security headers, like `Cache-Control`, to prevent sensitive data caching.

### Don'ts

- **Neglect Regular Audits**: Avoid skipping regular audits of system configurations and security settings.
- **Overlook Endpoint Security**: Do not ignore the security of common endpoints and services that can be targeted by attackers.
- **Rely Solely on External Tools**: While tools like Cloudflare provide an additional layer of security, don't rely on them solely for protection.
- **Expose Sensitive Information**: Ensure that sensitive information, such as API endpoints for private features, is not inadvertently exposed.
- **Underestimate Configuration Errors**: Misconfigurations can be as damaging as software flaws; never underestimate their impact.
- **Ignore Browser Caching Behaviors**: Be aware of how browsers handle caching and ensure sensitive data is not unintentionally cached.

### Example

A social network website offers a "Direct Message" feature that allows users to keep private conversations. To retrieve new messages for a specific conversation, the website issues the following API request (user interaction is not required):

```GET /dm/user_updates.json?conversation_id=1234567&cursor=GRlFp7LCUAAAA```

Because the API response does not include the Cache-Control HTTP response header, private conversations end-up cached by the web browser, allowing malicious actors to retrieve them from the browser cache files in the filesystem.


## API6:2023 Unrestricted Access to Sensitive Business Flows

When creating an API Endpoint, it is important to understand which business flow it exposes. Some business flows are more sensitive than others, in the sense that excessive access to them may harm the business.

## Addressing Business Impact of Unrestricted Access to Sensitive Flows

**API6:2023 Unrestricted Access to Sensitive Business Flows** underscores the critical importance of understanding and securing business-critical API endpoints from a business perspective. Ensuring the business team is fully aware of the implications of API vulnerabilities is key. For example, the scenario of the gaming console release by the technology company illustrates how exploitation of these vulnerabilities can have significant business repercussions.

### Educating the Business on API Security

- **Understand Business Flow Sensitivity**: It’s crucial for both technical teams and business stakeholders to recognize which business flows are sensitive and why. This understanding guides effective protection strategies.
- **Evaluate Business Impact**: Assess the potential business impact of unrestricted access to each API endpoint. Understanding the consequences helps in prioritizing security efforts.
- **Collaborative Security Planning**: Involve business stakeholders in security planning to ensure that protective measures align with business objectives and customer experience.
- **Anomaly Detection in User Behavior**: Monitor for patterns that indicate automated or abnormal usage, allowing for early detection of potential exploitation.
- **Implementing Business Logic in APIs**: Incorporate business logic that detects and prevents abuse, like restricting quantities per purchase or flagging unusually rapid transaction sequences.
- **Audit and Log Analysis**: Regularly audit and analyze logs to identify suspicious activities, helping in proactive security enhancements.

### Key Takeaway for Businesses

It is not just about implementing technical security measures; it’s about integrating the understanding of business flows into the security framework. Businesses must recognize the importance of securing API endpoints against unrestricted access as a part of their overall strategy to protect their interests and maintain trust with their customers.

### Example
A technology company announces they are going to release a new gaming console on Thanksgiving. The product has a very high demand and the stock is limited. An attacker writes code to automatically buy the new product and complete the transaction.

On the release day, the attacker runs the code distributed across different IP addresses and locations. The API doesn't implement the appropriate protection and allows the attacker to buy the majority of the stock before other legitimate users.

Later on, the attacker sells the product on another platform for a much higher price.


## API9:2023 Improper Inventory Management

The sprawled and connected nature of APIs and modern applications brings new challenges. It is important for organizations not only to have a good understanding and visibility of their own APIs and API endpoints, but also how the APIs are storing or sharing data with external third parties.

### Do's

- **Maintain a Comprehensive API Inventory**: Keep an up-to-date inventory of all API endpoints, including those in different stages of development like beta versions.
- **Consistent Security Across All Environments**: Implement security mechanisms uniformly across all API endpoints, regardless of their stage in the development lifecycle.
- **Regular Audits and Reviews**: Periodically audit APIs for security consistency and compliance with organizational standards.
- **Visibility of Third-Party API Integrations**: Keep track of external APIs integrated into your system and understand how they handle data.
- **Implement Version Control and Decommissioning Strategies**: Use version control for APIs and have clear strategies for decommissioning outdated or unused APIs.

### Don'ts

- **Overlook Non-Production Environments**: Do not ignore the security of APIs in development, testing, or beta stages.
- **Allow Unmonitored API Changes**: Avoid making changes to APIs without proper review and documentation.
- **Lack a Centralized API Management System**: Do not rely on fragmented management systems that can lead to gaps in security and visibility.


### Example
A social network implemented a rate-limiting mechanism that blocks attackers from using brute force to guess reset password tokens. 

This mechanism wasn't implemented as part of the API code itself but in a separate component between the client and the official API (api.socialnetwork.owasp.org). 

A researcher found a beta API host (beta.api.socialnetwork.owasp.org) that runs the same API, including the reset password mechanism, but the rate-limiting mechanism was not in place. The researcher was able to reset the password of any user by using simple brute force to guess the 6 digit token.


## API10:2023 Unsafe Consumption of APIs

Developers tend to trust data received from third-party APIs more than user input. This is especially true for APIs offered by well-known companies. Because of that, developers tend to adopt weaker security standards, for instance, in regards to input validation and sanitization.

### Do's:

- **Treat Third-Party API Data as Untrusted**: Apply the same security measures to third-party API data as you would to user input.
- **Implement Rigorous Input Validation**: Ensure all incoming data, regardless of its source, undergoes thorough validation.
- **Use Parameterized Queries**: Protect your databases by using parameterized queries to prevent SQL injection attacks.
- **Regularly Update and Audit Third-Party Services**: Keep track of updates and security patches for all third-party services used.
- **Monitor and Log API Interactions**: Keep detailed logs of interactions with third-party APIs to identify potential security breaches.

### Don'ts:

- **Assume Third-Party APIs Are Safe**: Never operate under the assumption that data from third-party APIs is inherently secure.
- **Neglect Input Sanitization**: Avoid the pitfall of not sanitizing data from third-party APIs as rigorously as user input.
- **Overlook Endpoint Security**: Do not ignore the security of your API endpoints, even when they interact with trusted third-party services.
- **Underestimate the Need for Regular Audits**: Do not skip regular security audits and updates of the APIs and their integrations.
- **Ignore Anomalies in Data Patterns**: Stay vigilant and do not disregard unusual patterns or anomalies in data received from third-party APIs.

### Example
An API relies on a third-party service to enrich user provided business addresses. When an address is supplied to the API by the end user, it is sent to the third-party service and the returned data is then stored on a local SQL-enabled database.

Bad actors use the third-party service to store an SQLi payload associated with a business created by them. Then they go after the vulnerable API providing specific input that makes it pull their "malicious business" from the third-party service. The SQLi payload ends up being executed by the database, exfiltrating data to an attacker's controlled server.


# OWASP web Security

TBD