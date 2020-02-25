---
title: "people_tag_confirm"
description: "Confirm people tag for photo"
---

Confirm (or deny) an unconfirmed people tag for a photo.

### Request ###

Parameter|Description|Required?
---------|-----------|---------
id|Item ID||Yes
tag_id|Person tag ID|Yes
confirm|`true` or `false`|Yes

### Sample Response ###

```json
{
  "success": true
}
```

### Errors ###

On error, `people_tag_confirm` can return one of the following error values:

Error Value|Description
-----------|-----------
`WEBAPI_ERR_BAD_REQUEST`|Missing or invalid parameters
`PHOTOSTATION_PHOTO_TAG_ACCESS_DENY`|User does not have manage permissions for album containing photo
`PHOTOSTATION_PHOTO_TAG_NOT_EXIST`|`tag_id` does not exist
`PHOTOSTATION_PHOTO_TAG_PEOPLE_TAG_CONFIRM_FAIL`|Error confirming people tag
