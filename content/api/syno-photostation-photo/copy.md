---
title: "copy"
description: "Copy or move photos and/or videos"
---

Copy or move a set of photos and/or videos.

### Request ###

Parameter  |Description|Required?
-----------|-----------|---------
`id`       |Comma separated list of items (photos or videos) |Yes
`sharepath`|Album ID of destination album|Yes
`mode`     |`copy` or `move`|Yes
`duplicate`|`rename`, `ignore` or `overwrite`|Yes

### Sample Response ###

```json
{
  "success": true
}
```

Unfortunately the response is not particularly informative as it does not
show any per-item status. Additionally, some errors (for example, attempting
to copy an invalid ID) are never reported.

### Cancellation ###

The `copy` command supports cancellation via the `cancel` command.
In order for `cancel` to stop copying or moving of the items being processed, the
cancellation `id` parameter must match the copy `id` parameter exactly,
otherwise cancellation will not find a matching operation. This means if
one is copying/moving multiple items in a single request, all the
item operations must be cancelled (if desired) with a single request.

Also note that cancellation is best effort and does not ensure the item(s)
will not have already been copied or moved by the time the cancellation
operation is received. There is no undo operation.

### Errors ###

On error, `cancel` can return one of the following error values:

Error Value|Description
-----------|-----------
`PHOTOSTATION_PHOTO_BAD_PARAMS`|Missing parameters or invalid destination album
`PHOTOSTATION_PHOTO_ACCESS_DENY`|User does not have upload access to destination album
`PHOTOSTATION_PHOTO_SELECT_CONFLICT`|Current and destination album are identical and `duplicate` != `rename`
