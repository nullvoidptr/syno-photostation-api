---
title: "delete"
description: "Delete one or more items"
---

Delete one or more items (photos or videos) from one or more albums.

### Request ###

Parameter|Description|Required?
---------|-----------|---------
id|Comma separated list of item IDs|Yes

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

The `delete` command supports cancellation via the `cancel` command.
In order for `cancel` to stop deletion of the items being processed, the
cancellation `id` parameter must match the delete `id` parameter exactly,
otherwise cancellation will not find a matching operation. This means if
one is deleting multiple items in a single request, all the
item operations must be cancelled (if desired) with a single request.

Also note that cancellation is best effort and does not ensure the item(s)
will not have already been deleted by the time the cancellation
operation is received. There is no undo operation.

### Errors ###

On error, `delete` can return one of the following error values:

Error Value|Description
-----------|-----------
`PHOTOSTATION_PHOTO_BAD_PARAMS`|Missing required parameter