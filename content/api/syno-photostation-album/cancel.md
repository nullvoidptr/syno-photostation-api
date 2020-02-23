---
title: "cancel"
description: "Cancel an album operation"
---

Cancels an operation (move, copy or delete) being performed
on an album.

Internally this operates by creating a per-operation temporary sentinel file
which is checked prior to each individual operation. The `id` parameter
of the `cancel` operation must match the `id` of the original operation
exactly (contents and order), or the cancellation operation will not find a
matching operation to cancel.

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

Returns `WEBAPI_ERR_BAD_REQUEST` if parameters are missing.
