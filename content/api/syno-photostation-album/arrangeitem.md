---
title: "arrangeitem"
description: "Manually arranges order of an album's contents"
---

Manually arranges order of an album's contents (within a given offset and limit slice bounds). This is used by the drag-and-drop reordering of the PhotoStation
Web UI.

The parameter `item_id` indicates the desired order of the items.

TODO: Need to understand implications if `item_id` has a different number of elements than
the original slice defined by `offset` and `limit`).

### Request ###

Parameter|Description|Required?
---------|-----------|---------
id       |Album ID   | Optional
item_id  |Comma separated list of item IDs|Yes
limit    |Limit of current view|Yes
offset   |Offset of current view| Yes

If `id` not passed, assumes root folder.

### Sample Response ###

```json
{
  "success": true
}
```

### Errors ###

On error, `arrangeitem` can return one of the following error values:

Error Value|Description
-----------|-----------
`WEBAPI_ERR_BAD_REQUEST`|Missing parameters or if `item_id` contains IDs that are not `album`, `photo` or `video` types
`PHOTOSTATION_ALBUM_NO_MANAGE_RIGHT`|User does not have management permissions for given album.
