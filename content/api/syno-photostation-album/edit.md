---
title: "edit"
description: "Edit metadata or settings of an album"
---

Edit the metadata or settings for an album.

### Request ###

<!-- Enter request parameters here. "Yes" or "Optional" under Required? -->
Parameter|Description|Required?
---------|-----------|---------
id       |ID of album|Yes
allow_comment|Allow comments (only allowed for first level albums)|Optional
conversion|Unknown. Enabled by default, can only disable in first level albums|Optional
description|Description of album|Optional
inheritParent|(boolean)|Optional
name     |Name of album|Optional
sort_by  |Sorting method for album. One of `filename`, `takendate`, `createdate`, `preference` or `default`|Optional
sort_direction|One of `asc` or `desc`|Optional
title    |Title to assign to album|Optional
type     |One of `public`, `private` or `password`|Optional
watermark_path|Path to watermark file|Optional *
watermark_opacity|Opacity of watermark|Optional *
watermark_gravity|Gravity of watermark file|Optional *
watermark_size|Size of watermark file|Optional *

In order to apply a watermark, all four `watermark_*` parameters must be present.

If setting `type` to `password`, one must include a `password` parameter and
value as well.

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
`WEBAPI_ERR_BAD_REQUEST`|Missing or invalid parameter(s)
`PHOTOSTATION_ALBUM_EDIT_FAIL`|General error during album update
`PHOTOSTATION_ALBUM_NO_MANAGE_RIGHT`|User does not have manage rights for album
`PHOTOSTATION_ALBUM_NOT_ADMIN`|Admin user required for some settings (`title`, `sort_by`, `sort_direction`, `allow_comment`, `type`, `password`, `conversion`)