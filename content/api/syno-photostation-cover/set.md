---
title: "set"
description: "Set cover photo/video of an album"
---

Set the cover photo or video for an album.

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

On error, `set` can return one of the following error values:

Error Value|Description
-----------|-----------
`WEBAPI_ERR_BAD_REQUEST`|Missing or invalid parameters
`PHOTOSTATION_COVER_ALBUM_NOT_EXIST`|Requested album does not exist
`PHOTOSTATION_COVER_PHOTO_VIDEO_NOT_EXIST`|Requested cover photo/video does not exist
`PHOTOSTATION_COVER_PHOTO_VIDEO_NOT_IN_ALBUM`|COver photo/video is not in album
`PHOTOSTATION_COVER_ACCESS_DENY`|User does not have permissions to set cover photo/video
`PHOTOSTATION_COVER_SET_FAIL`|Error attempting to set cover photo/video
