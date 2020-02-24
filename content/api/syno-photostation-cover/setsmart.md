---
title: "setsmart"
description: "Set cover photo/video of a smart album"
---

Set cover photo or video of a smart album

### Request ###

Parameter|Description|Required?
---------|-----------|---------
id|Album ID|Yes
item_id|Cover photo / video ID|Yes

### Sample Response ###

```json
{
  "success": true
}
```

### Errors ###

On error, `setsmart` can return one of the following error values:

Error Value|Description
-----------|-----------
`WEBAPI_ERR_BAD_REQUEST`|Missing or invalid parameter(s)
`PHOTOSTATION_SMARTALBUM_ACCESS_DENY`|User is not an admin user
`PHOTOSTATION_SMARTALBUM_EDIT_FAIL`|Error attempting to set cover photo/video