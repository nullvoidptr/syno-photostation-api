---
title: "delete"
description: "Delete an album(s)"
---

Delete one or more photo albums.

### Request ###

Parameter|Description|Required?
---------|-----------|---------
id       |Comma separated list of album IDs|Yes

### Sample Response ###

```json
{
  "success": true
}
```

### Cancellation ###

The `delete` command supports cancellation via the `cancel` command.
In order for `cancel` to stop deletion of the album(s) being processed, the
cancellation `id` parameter must match the delete `id` parameter exactly,
otherwise cancellation will not find a matching operation. This means if
one is deleting multiple albums in a single request, all the album deletions
must be cancelled (if desired) with a single request.

Also note that cancellation is best effort and does not ensure the album
will not have already been deleted by the time the cancellation operation is
received. There is no undo operation.

### Errors ###

On error, `delete` can return one of the following error values:

Error Value|Description
-----------|-----------
`WEBAPI_ERR_BAD_REQUEST`|Missing `id` parameter or if `id` is not a valid list of album IDs
`PHOTOSTATION_ALBUM_NO_MANAGE_RIGHT`|User does not have management permissions for given album(s).

Note: When deleting multiple albums, it is possible for some albums to be
deleted successfully even if the API returns an `PHOTOSTATION_ALBUM_NO_MANAGE_RIGHT` error.
