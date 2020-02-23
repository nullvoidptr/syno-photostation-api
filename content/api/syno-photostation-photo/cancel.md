---
title: "cancel"
description: "Cancel a photo operation"
---

Cancels an operation (move, copy or delete) being performed
on a photo or video.

Internally this operates by creating a per-operation temporary sentinel file
which is checked prior to each individual operation. The `id` parameter
of the `cancel` operation must match the `id` of the original operation
exactly (contents and order), or the cancellation operation will not find
a matching operation to cancel.

### Request ###

Parameter|Description|Required?
---------|-----------|---------
action   |Name of action `mvcp` or `delete`|Yes
id       |Comma separated list of album IDs|Yes

If `id` not passed, assumes root folder.

### Sample Response ###

```json
{
  "success": true
}
```

### Errors ###

On error, `cancel` can return one of the following error values:

Error Value|Description
-----------|-----------
`PHOTOSTATION_PHOTO_BAD_PARAMS`|Missing parameters
