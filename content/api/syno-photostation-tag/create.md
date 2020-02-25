---
title: "create"
description: "Create a new tag"
---

Creates a new tag. Tags are indexed so they can easily be queried.
Creating a tag allows it to be associated with a photo or video
but does not add it to an item.
See the [`SYNO.PhotoStation.PhotoTag`](/api/syno-photostation-phototag)
API for associating tags to photos/videos.

### Request ###

Parameter|Description|Required?
---------|-----------|---------
name|Tag name|Yes
type|Type of tag (one of `people`, `geo` or `desc`)|Yes
place_id|Place ID (`geo` tag only)|Optional
reference|Geographic reference (`geo` tag only)|Optional
lat|Latitude (`geo` tag only)|Optional
lng|Longitude (`geo` tag only)|Optional
address|Address (`geo` tag only)|Optional

### Sample Response ###

On success returns the tag ID for the newly formed tag.

```json
{
  "success": true,
  "data": {
    "id": [
      "tag_1234"
    ]
  }
}
```

### Errors ###

On error, `create` can return one of the following error values:

Error Value|Description
-----------|-----------
`WEBAPI_ERR_BAD_REQUEST`|Missing or invalid parameters
`PHOTOSTATION_TAG_CREATE_FAIL`|Error creating tag
