---
title: "delete"
description: "Delete one or more tags"
---

Deletes one or more tags

### Request ###

Parameter|Description|Required?
---------|-----------|---------
id|Comma separated list of tag IDs|Yes

### Sample Response ###

```json
{
  "success": true
}
```

### Errors ###

On error, `delete` can return one of the following error values:

Error Value|Description
-----------|-----------
`WEBAPI_ERR_BAD_REQUEST`|Missing or invalid parameters
