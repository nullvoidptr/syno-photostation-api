---
title: "create"
description: "Create a new album"
---

Create a new album of the given name. Optionally can specify additional album settings.

##### Request #####

|Parameter|Description|Required?|
|---------|-----------|---------|
|name |Name of album to be created|Yes
|allow_comment|Allow comments (only allowed for first level albums)|Optional
|conversion|Unknown. Enabled by default, can only disable in first level albums|Optional
|description|Description of album|Optional
|id |ID of parent album|Optional
|inheritParent|(boolean)|Optional
|sort_by|Sorting method for album. One of `filename`, `takendate`, `createdate`, `preference` or `default`|Optional
|sort_direction|One of `asc` or `desc`|Optional
|title|Title to assign to album|Optional
|type|One of `public`, `private` or `password`|Optional
|watermark_path|Path to watermark file|Optional *
|watermark_opacity|Opacity of watermark|Optional *
|watermark_gravity|Gravity of watermark file|Optional *
|watermark_size|Size of watermark file|Optional *

If no ID is set, the album will be created in the root album of PhotoStation.

In order to apply a watermark, all four `watermark_*` parameters must be present.

### Sample Response ###

```json
{
  "success": true
}
```

### Errors ###

On error, `create` can return one of the following error values:

Error Value|Description
-----------|-----------
`WEBAPI_ERR_BAD_REQUEST`|Missing or invalid parameter(s)
`PHOTOSTATION_ALBUM_NOT_ADMIN`|Attempting to specify options and are not an admin user
`PHOTOSTATION_ALBUM_NO_UPLOAD_RIGHT`|User cannot upload to parent album
`PHOTOSTATION_ALBUM_HAS_EXIST`|Album already exists
`PHOTOSTATION_ALBUM_CREATE_FAIL`|Any other error during creation
