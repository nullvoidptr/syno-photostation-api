---
title: "cleararrangeitem"
description: "Removes manually specified ordering from album"
---

Removes any manually specified ordering from album.

### Request ###

Parameter|Description|Required?
---------|-----------|---------
id       |Album ID   | Optional

If `id` not passed, assumes root folder.

### Sample Response ###

```json
{
  "success": true
}
```

### Errors ###

On error, `cleararrangeitem` can return one of the following error values:

Error Value|Description
-----------|-----------
`WEBAPI_ERR_BAD_REQUEST`|`id` is present but is not a proper album ID (does not start with `album_`)
`PHOTOSTATION_ALBUM_NO_MANAGE_RIGHT`|User does not have management permissions for given album.

