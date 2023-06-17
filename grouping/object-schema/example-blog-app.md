# Example Blog App

## Organizing roles for an example blog

```json
// Choose an NFT to represent the group
{
    "nonce": "0", //anchor nonce
    "owner": ["did:1.2.3.4"],
    "creds": ["vc:0"],
    "data": "{
                'title': 'My Group',
                'link': 'eth.address:0123456789', //nft asset is linked to this group
                'schema': [{'title': 'str'}, {'schema': 'list<str>'}]
            }"
}

// Create a new group to hold the roles
{
    "nonce": "0.0", //nonces are linked by owning group
    "owner": ["did:1.2.3.4"], 
    "creds": ["vc:0"],
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
    "data": "{'role': 'admin'}"]
}

// An end user will be issued a VC
{
    "nonce": "0.0.1",
    "owner": ["did:1.2.3.4"],
    "creds": ["vc:0.2"], //create a new VC for a public user
    "data": "{'role': 'public user'}"
}
```

## Adding Posts to the group

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

// Add a new post that is only accessible to the owner
{
    "nonce": "0.1.2",
    "owner": ["did:1.2.3.4"],
    "creds": ["vc:0"],
    "data": "{
                'title': 'My Private Post',
                'post': 'For my eyes only.'
            }"
}
```

## Adding user ratings to the posts

```json
// create a new group below the posts
{
    "nonce": "0.1.0.0",
    "owner": ["did:1.2.3.4"],
    "creds": ["vc:0.2"],
    "data": "{
                'title': 'Ratings',
                'schema': [{'selection': ['👍', '👎']}]
            }"
}

// an example rating on the first post
{
    "nonce": "0.1.0.0.0",
    "owner": ["did:5.2.3.4"], //this owner is different than the id making the post
    "creds": ["vc:0.2"],
    "data": "{'selection': '👍'}"
}
```

## Result

```
// One asset is anchored creating the base group
- "My Group" (Group w/ Schema) [0]

// Three Groups w/ schemas are created 
   (1) -- "My Roles" (Group w/ Schema) [0.0]
        --- "admin" [0.0.0]
        --- "public user" [0.0.1]
   (2) -- My Posts (Group w/ Schema) [0.1]
        --- "Hello World" [0.1.0]
        --- "Hello Mods!" [0.1.1]
        --- "My Private Post" [0.1.2]
       (3) ---- "Ratings" (Group w/ Schema) [0.1.0.0]
                ----- Rating #1 [0.1.0.0.0] //rating on the "Hello World!" post
```
