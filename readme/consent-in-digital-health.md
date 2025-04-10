---
description: Soura Bhattacharyya | April 10, 2025
---

# Consent in Digital Health

_This post was preceded by a less thorough, more geeky, and less boring one, available_ [_here_](../authorization-equals-consent.md)_. It is better to read this one first—till we take the time to merge them into a single thread._

***

The collection, storage and exchange of digital health data needs the consent of the patient—the data subject.

As per the EU's General Data Protection Regulation (GDPR), consent has to be "explicit, informed, specific, freely given, and unambiguous". This position is echoed in India's Digital Data Protection Act, 2021.

Legislation has shifted from data **ownership** to data **stewardship**. Data controllers and processors are custodians, and the **data subject is, unambiguously, the owner**. Consequently, data processing, especially in sensitive categories such as health and finance, needs consent.

Effective consent management is more than legal compliance—it is a way to gain users' trust. It empowers patients to exercise granular control over their health data, allowing them to monitor who accesses their information and for what purposes.

## Consent and authorization

When a patient _consents_ to an entity's request to access their data—for a defined purpose and duration—then this action _authorizes_ the system to permit that access. Conversely, the revocation of consent must translate to a denial of authorization.

Thus, consent and authorization are two sides of the same coin.

## Challenges in consent management

Implementing a comprehensive consent management system faces several challenges:

* **Complexity:** Healthcare scenarios often involve layered and complex consent requirements, including consent for different data types, purposes, timeframes, and actors.
* **Usability:** Interfaces for obtaining and managing consent must be patient-friendly, simple to understand, yet comprehensive in their coverage.
* **Interoperability:** Consent management needs to interface with a variety healthcare information systems operated by different service providers.
* **Compliance:** Consent logs must be **externally verifiable** by regulatory bodies without revealing the underlying health data.
* **Proxies:** The system needs to accommodate consent provided by legal guardians and caregivers.

## Open-source authorization models as consent managers

Open-source authorization models offer a powerful and cost-effective approach to address these challenges.

Relationship-Based Access Control (ReBAC), exemplified by OpenFGA, allow for defining access based on the relationships between users and resources. In the context of consent, this can model the relationship between a patient and a healthcare practitioner they have granted access to, or the relationship between a patient and different categories of their health data.&#x20;

OpenFGA enables fast queries to determine if a user can perform an action on a resource. This can directly translate to checking if a practitioner has valid consent to access specific patient records.&#x20;

Access can be highly granular, based on factors such as the practitioner's attributes (`practitioner P is a general physician`), their relationships to other entities (`P is a member of clinic C`), and their relationship to the patient (`patient Q has an appointment with P`).

Furthermore, the transparency of open-source allows for community review—shifting power from institutions to individuals.

Finally, Adapting costs less than [building from scratch](#user-content-fn-1)[^1].

[^1]: Of course, nothing is ever built from scratch. As Carl Sagan said, "If you wish to make an apple pie from scratch, you must first invent the universe."&#x20;
