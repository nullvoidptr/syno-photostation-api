---
title: "move"
description: "Move one or more albums"
---

Moves one or more albums to a new parent album. All albums will be located to the same parent if successful.

### Request ###

Parameter|Description|Required?
---------|-----------|---------
id       |Comma separated list of Album IDs|Yes
sharepath|Destination parent album ID|Yes
duplicate|Duplicate album handing (`overwrite` or any other value)|Yes

`sharepath` must be present but may be empty to indicate the root album.

If `duplicate` is set to `overwrite`, any existing albums with same name as a
source album will be overwritten. Any other value (eg.g `ignore`) will
cause the albums with naming conflicts to be skipped (see below).

### Sample Response ###

```json
{
  "success": true
}
```

If any albums are skipped due to name conflict, the returned data object
will contain a `skip` array containing the IDs of all albums that were
not moved:

```json
{
  "success":true,
  "data": {
    "skip":[
      "album_746573745f31"
    ]
  }
}
```

### Cancellation ###

The `move` command supports cancellation via the `cancel` command.
In order for `cancel` to stop the album(s) being moved, the
cancellation `id` parameter must match the move `id` parameter exactly,
otherwise cancellation will not find a matching operation. This means if
one is moving multiple albums in a single request, all the album moves
must be cancelled (if desired) with a single request.

Also note that cancellation is best effort and does not ensure the album
will not have already been moved by the time the cancellation operation is
received. There is no undo operation but albums can be returned to original
location via a new `move` command.

### Errors ###

On error, `move` can return one of the following error values:

Error Value|Description
-----------|-----------
`WEBAPI_ERR_BAD_REQUEST`|Missing or invalid parameters
`PHOTOSTATION_PHOTO_BAD_PARAMS`|Invalid destination path for album
`PHOTOSTATION_ALBUM_NO_MANAGE_RIGHT`|User does not have upload rights to destination album
`PHOTOSTATION_ALBUM_SELECT_CONFLICT`|One or more source albums are either the destination album or a parent of the destination album