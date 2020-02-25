---
title: "geo_tag"
description: "Add geographic tag(s) to item(s)"
---

Adds one or more geographic (`geo`) tags to a set of photos or videos.

NOTE: There does not appear to be any implementation difference
with [`desc_tag`](../desc_tag) and it may be possible to intermix both tag types in a single request.

### Request ###

Parameter|Description|Required?
---------|-----------|---------
id|Comma separated list of item IDs|Yes
tag_id|Comma separated list of tag IDs|Yes

### Sample Response ###

On success returns a list of item tag IDs added to the photo.

```json
{
  "success": true,
  "data": {
    "item_tag_ids": [
      "item_tag_1435"
    ]
  }
}
```

### Errors ###

On error, `geo_tag` can return one of the following error values:

Error Value|Description
-----------|-----------
`WEBAPI_ERR_BAD_REQUEST`|Missing or invalid parameter
`PHOTOSTATION_PHOTO_TAG_ACCESS_DENY`|User does not have permissions for album(s)
`PHOTOSTATION_PHOTO_TAG_NOT_EXIST`|One or more tags does not exist
`PHOTOSTATION_PHOTO_TAG_DUPLICATE`|Duplicate tags
`PHOTOSTATION_PHOTO_TAG_ADD_GEO_DESC_FAIL`|Error adding tags

NOTE: It appears that `PHOTOSTATION_PHOTO_TAG_DUPLICATE` and `PHOTOSTATION_PHOTO_TAG_ADD_GEO_DESC_FAIL`
are only returned if **ALL** items have failures. If any
non-zero number of items are successful, no error is returned.
