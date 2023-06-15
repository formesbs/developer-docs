---
description: Configure Azure and Entra
---

# Setup

The Verified ID component will need to be created in an AD B2C tenant to issue VCs to the public user base.

{% hint style="info" %}
​[https://learn.microsoft.com/en-us/azure/active-directory/verifiable-credentials/verifiable-credentials-configure-tenant](https://learn.microsoft.com/en-us/azure/active-directory/verifiable-credentials/verifiable-credentials-configure-tenant)
{% endhint %}

### Requirements <a href="#requirements" id="requirements"></a>

* SSL secured domain (Eg. https://did.forme.sbs)
* Webserver to host ./well-known/ tokens

### Quick Start <a href="#quick-start" id="quick-start"></a>

1. Create Microsoft **Azure account**
2. Login to [https://portal.azure.com](https://portal.azure.com/)​
3. Create a new **subscription**
4. Create a new **resource group**
5. Create a new **AD B2C tenant**
   1. Link the subscription and resource group
6. Switch to the newly created tenant
7. Create a new **Web Application** within the B2C tenant
8. Create a new **Azure Key Vault**
9. Setup **Verified ID**
