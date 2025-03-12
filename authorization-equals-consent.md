---
description: Soura Bhattacharyya | March 12, 2025
---

# Authorization equals consent
Consent is an essential component of any digital health system that connects patients with providers. While designing such a system, I went about looking for a open-source consent manager that could be used for health data. No such luck. 

Then it struck me—consent is nothing but authorization! 

After all, authorization lets us control who gets access to which resources, and for how long. Consent managers serve precisely the same function. And there are plenty of robust, capable, open-source authorization platforms. My favorite is [OpenFGA](https://openfga.dev/), which nests within the Cloud Native Computing Foundation (CNCF). 

Consider how we manage access to a set of folders on Google Drive (or Dropbox or Sharepoint). As an owner, you can provide top-level access—to the parent folder—to anyone. They can be editors, commenters, or viewers. Or, you can provide more granular access—to sub-folders, or individual resources (documents). Finally, child resources inherit access rights from their parents. The use of such object-to-object relationship to manage access is called relationship-based access control, or ReBAC.

Google's ReBAC is called Zanzibar. OpenFGA uses the same principles as Zanzibar.

OpenFGA's ReBAC model can also uses relationships between users. A `supervisor` can be allowed to access all the resources that are available to the subordinate. In a healthcare context, this can be applied to a treating physician, and their immediate supervisor. Groups of users can also be managed collectively, and access can be controlled based on properties such as time[^1] or network address. For more on this, see OpenFGA's [modeling guide](https://openfga.dev/docs/modeling).

Imagine a healthcare consent manager that is as flexible and adaptable as an amped up folder-sharing system, and where a single resource (or document) can belong to multiple folders—folders can be episodes of care, health facilities, or treatment history for a set of diseases. 

Or don't imagine it—build it with OpenFGA.

[^1]: Technically, authorization based on properties such as time is attribute-based access control (ABAC). Attributes include relationships; ABAC is a superset that includes ReBAC.
