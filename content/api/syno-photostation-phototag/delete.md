---
title: "delete"
description: "Delete a tag from item(s)"
---

Delete tag references from photos or videos. If any tags are no longer
referenced by other items, the tags will be deleted completely.

### Request ###

Parameter|Description|Required?
---------|-----------|---------
id|Comma separated list of item IDs|Yes
tag_id|Comma separated list of tag IDs|Optional
item_tag_id|Comma separated list of item tag IDs|Optional

Either the `tag_id` or `item_tag_id` must be provided. The `tag_id`
is a global ID for a given `people`, `geo` or `desc` tag that
is common across all items associated with it. The `item_tag_id`
is unique to each item-tag pairing and can be thought of as an
identifier for the tag reference for an item.

`item_tag_id`'s are returned by the [`desc_tag`](../desc_tag) and [`geo_tag`](../geo_tag) methods.

### Sample Response ###

```json
{
  "success": true
}
```

### Errors ###

On error, `delete` can return one of the following error values:

Error Value|Description
-----------|-----------
`WEBAPI_ERR_BAD_REQUEST`|Missing or invalid parameters
`PHOTOSTATION_PHOTO_TAG_ACCESS_DENY`|User does not have manage permissions for album containing item(s)
