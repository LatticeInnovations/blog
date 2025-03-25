---
description: October 14, 2022 | Anoop K Singh
cover: ../.gitbook/assets/arthur-mazi-a8CxRWIu8yw-unsplash.jpg
coverY: 0
layout:
  cover:
    visible: true
    size: hero
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# API security

## Common API vulnerabilities <a href="#id-3cc6" id="id-3cc6"></a>

### Distributed Denial of service <a href="#id-3cc6" id="id-3cc6"></a>

API DDoS attacks are executed to overload an API service. Since each hacker sends normal traffic volumes, these attacks are difficult to detect.

### SQL Injections and Data Attacks

With the right credentials, insiders and hackers can access any system or data. Examples include Data Extraction or Theft, Data Deletion or Manipulation, Data Injection, Malicious Code Injection, and Extreme Application Activity.

## API security best practices <a href="#id-8469" id="id-8469"></a>

### Authenticate <a href="#id-8469" id="id-8469"></a>

One of the most crucial components of API security is authentication. Always use secure authentication techniques like JWT or OAuth to confirm user identity.

Simple HTTP authentication should never be used as it sends fields without encryption.

### Use API gateways

Always place an API behind a gateway. Since API gateways consolidate both security-related activities and useful business-related operations, this has various advantages.

Rate limitation, barring malicious clients, are all characteristics of API gateways.

### Validate inputs

Specify the acceptable inputs in your API documentation.

Prior to doing any server-side data modification or writing data to the database, don’t forget to verify every input.

### Prevent improper entry attempts

They can be:

* Remote Code Execution (RCE)
* SQL Injection
* Cross-Site Scripting (XSS)

Sending API keys or other sensitive data in the URL is not advised. Always use the Authorization header for them.

### Limit requests (Throttling)

You may avoid DoS/brute-force attacks by limiting the number of queries sent.

Unfortunately, DDoS assaults don’t respond well to this technique.

### Output data

Only the relevant info should be returned. Take care not to return any delicate information, such as API keys or passwords.

Remove the `x-powered-by` and `server` headers from your HTTP response. Potential hackers may receive information from them.



Photo credit: [Arthur Mazi](https://unsplash.com/@arthurbizkit?utm_content=creditCopyText\&utm_medium=referral\&utm_source=unsplash) on [Unsplash](https://unsplash.com/photos/blue-sky-over-white-clouds-a8CxRWIu8yw?utm_content=creditCopyText\&utm_medium=referral\&utm_source=unsplash)

This blog first appeared on [Medium](https://medium.com/lattice-what-is/most-commonly-known-api-vulnerabilities-6f3d69dde671), with the title "Most Commonly Known API Vulnerabilities And API Security Best Practices".&#x20;
