---
title: "getinfo"
description: "Fetch info about one or more tags"
---

Retrieve information about one or more defined tags.

### Request ###

Parameter|Description|Required?
---------|-----------|---------
id|Comma separated list of tag IDs|Yes

### Sample Response ###

```json
{
  "success": true,
  "data": {
    "tags": [
      {
        "id": "tag_102",
        "type": "tag",
        "tag_type": "desc",
        "name": "CC"
      },
      {
        "id": "tag_24",
        "type": "tag",
        "tag_type": "desc",
        "name": "Family"
      }
    ]
  }
}

```

### Errors ###

On error, `getinfo` can return one of the following error values:

Error Value|Description
-----------|-----------
`WEBAPI_ERR_BAD_REQUEST`|Missing or invalid parameters
`PHOTOSTATION_TAG_GETINFO_FAIL`|Error fetching tag information
