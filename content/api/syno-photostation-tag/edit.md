---
title: "edit"
description: "Edit tag values"
---

Modify tag values. All elements of a tag can be changed except for
the tag type.

### Request ###

Parameter|Description|Required?
---------|-----------|---------
id|Original tag ID|Yes
name|Tag name|Optional
place_id|Place ID (`geo` tag only)|Optional
reference|Geographic reference (`geo` tag only)|Optional
lat|Latitude (`geo` tag only)|Optional
lng|Longitude (`geo` tag only)|Optional
address|Address (`geo` tag only)|Optional

### Sample Response ###

```json
{
  "success": true
}
```

### Errors ###

On error, `edit` can return one of the following error values:

Error Value|Description
-----------|-----------
`WEBAPI_ERR_BAD_REQUEST`|Missing or invalid parameters
`PHOTOSTATION_TAG_EDIT_FAIL`|Error modifying tag
`PHOTOSTATION_TAG_HAS_EXIST`|Modified tag equal to an existing tag
