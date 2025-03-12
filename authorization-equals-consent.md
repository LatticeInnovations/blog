---
description: Soura Bhattacharyya | March 12, 2025
---

# Authorization equals consent
While working on a digital health blueprint, I went about looking for a open-source consent manager that could be used for health data. No such luck. 

Then it struck me—consent is nothing but authorization! 

After all, authorization lets us control who gets access to which resources, and for how long. Consent managers serve precisely the same function. And there are plenty of robust, capable, open-source authorization platforms. My current favorite[^1] is [OpenFGA](https://openfga.dev/), which nests within the Cloud Native Computing Foundation (CNCF). 

Consider how we manage access to a set of Google Drive folders. As an owner, you can provide top-level access—to the parent folder—to anyone. They can be editors, commenters, or viewers. Or, you can provide access to sub-folders, and individual documents residing within a folder. Finally, access to parent folders are inherited by the children. The use of such object-to-object relationship to manage access is called relationship-based access control (ReBAC)[^2].   

Google's ReBAC is called Zanzibar. OpenFGA uses the same principles as Zanzibar.

Imagine a healthcare consent manager that is as flexible and adaptable as shared folders, and where a single resource (or document) can belong to multiple folders—folders can be episodes of care, health facilities, or treatment history for a set of diseases. 

Or don't imagine it—build it with OpenFGA.


[^1]: Current favorite because I have only explored a few platform, not because of any limitations of OpenFGA.
[^2]: ReBAC can also uses relationships between users. A `supervisor` can be allowed to access all the resources that are available to the subordinate. In a healthcare context, this can be applied to a treating physician, and their immediate supervisor.
