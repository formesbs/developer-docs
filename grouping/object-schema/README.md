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
        "vc:0", "vc:1", "..."
    ],
    "data": "Base64 of JSON data"
}
</code></pre>

## Group Data Object&#x20;

```json
{
    "title": <string>, //title for the data object
    "link": <string>, //a link to an anchor object, only required for top level grouping
    "schema": [{<string>: <string>}] //a list containing key: value pairs
}
```

