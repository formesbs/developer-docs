---
description: How groups are made
---

# Object Schema

## Universal Object Schema

<pre class="language-json"><code class="lang-json"><strong>{
</strong>    "nonce": "int - record position",
    "owner": [
        "did:did.forme.sbs.xxxxx"
    ],
    "creds": [
        "vc1", "vc2", "..."
    ],
    "data": "Base64 of JSON data"
}
</code></pre>

## Example - Organizing DID roles in a public organization

```json
// Choose an NFT to represent the group
{
    "nonce": "0",
    "owner": ["did:1.2.3.4"],
    "creds": ["vc0"],
    "data": "{
                'title': 'My Group',
                'link': 'id-0123456789' //nft asset is linked to this group
                'schema': ['title-str', 'schema-list<str>']
            }"
}

// Create a new group to hold the roles
{
    "nonce": "0.0", //nonces are linked by owning group
    "owner": ["None=inherit super"], //only the owner of the above group can manage this group
    "creds": ["None=inherit super"],
    "data": "{
                'title': 'My Roles',
                'schema': ['role-str']
            }"
}

// Each role is a single key-value pair using the universal object schema
{
    "nonce": "0.0.0",  //third layer nonce
    "owner": ["did:1.2.3.4"],
    "creds": ["vc1"], //create a new VC for an admin
    "data": "{'role': 'admin'}"
}

{
    "nonce": "0.0.1",
    "owner": ["did:1.2.3.4"],
    "creds": ["vc2"], //create a new VC for a public user
    "data": "{'role': 'public user'}"
}
```
