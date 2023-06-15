---
description: Configure Azure and Entra
---

# Setup

{% hint style="info" %}
​[https://learn.microsoft.com/en-us/azure/active-directory/verifiable-credentials/verifiable-credentials-configure-tenant](https://learn.microsoft.com/en-us/azure/active-directory/verifiable-credentials/verifiable-credentials-configure-tenant)
{% endhint %}

### Requirements <a href="#requirements" id="requirements"></a>

* SSL secured domain (Eg. https://did.forme.sbs)
* Webserver to host ./well-known/ tokens

### Quick Start <a href="#quick-start" id="quick-start"></a>

1. 1.Create Microsoft **Azure account**
2. 2.Login to [https://portal.azure.com](https://portal.azure.com/)​
3. 3.Create a new **subscription**
4. 4.Create a new **resource group**
5. 5.Create a new **AD B2C tenant**
   1. 1.Link the subscription and resource group
6. 6.Switch to the newly created tenant
7. 7.Create a new **Azure Key Vault**
8. 8.Setup **Verified ID**
