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

## Data Object Schema

```json
{
    "title": <string>, //title for the data object
    "link": <string>, //a link to an anchor object, only required for top level grouping
    "schema": [{<string>: <string>}] //a list containing key: value pairs
}
```

## Example - Organizing DID roles in a public organization

```json
// Choose an NFT to represent the group
{
    "nonce": "0",
    "owner": ["did:1.2.3.4"],
    "creds": ["vc:0"],
    "data": "{
                'title': 'My Group',
                'link': 'id-0123456789', //nft asset is linked to this group
                'schema': [{'title': 'str'}, {'schema': 'list<str>'}]
            }"
}

// Create a new group to hold the roles
{
    "nonce": "0.0", //nonces are linked by owning group
    "owner": ["None=inherit super"], //only the owner of the above group can manage this group
    "creds": ["None=inherit super"],
    "data": "{
                'title': 'My Roles',
                'schema': [{'role': 'str'}]
            }"
}

// Each role is a single key-value pair using the universal object schema
{
    "nonce": "0.0.0",  //third layer nonce
    "owner": ["did:1.2.3.4"],
    "creds": ["vc:0.1"], //create a new VC for an admin
    "data": "{'role': 'admin'}"
}

// An end user will be issued a VC
{
    "nonce": "0.0.1",
    "owner": ["did:1.2.3.4"],
    "creds": ["vc:0.2"], //create a new VC for a public user
    "data": "{'role': 'public user'}"
}
```

## Example - Adding a subscription to the group

```json
// Create a new group under nonce 0 to hold the posts
{
    "nonce": "0.1",
    "owner": ["did:1.2.3.4"],
    "creds": ["vc:0"], 
    "data": "{
                'title': 'My Posts',
                'schema': [{'title':'str'}, {'post':'str'}]
            }"
}

// Add a new post to the group that is accessible to public users
{
    "nonce": "0.1.0",
    "owner": ["did:1.2.3.4"],
    "creds": ["vc:0.2"],
    "data": "{
                'title': 'Hello World!',
                'post': 'Welcome to my group.'
            }"
}

// Add a new post that is accessible to admins only
{
    "nonce": "0.1.1",
    "owner": ["did:1.2.3.4"],
    "creds": ["vc:0.1"],
    "data": "{
                'title': 'Hello Mods!',
                'post': 'Thank you for helping out.'
            }"
}
```

## Example - Adding user ratings to the posts

```json
// create a new group below the posts
{
    "nonce": "0.0.0.0",
    "owner": ["did:1.2.3.4"],
    "creds": ["vc:0.2"],
    "data": "{
                'title': 'Rating',
                'schema': [{'selection': ['👍', '👎']}]
            }"
}
```
