---
title: "people_tag"
description: "Add a people tag to a photo"
---

Adds a people tag to a photo. Requires coordinates of a
bounding box for facial recognition.

### Request ###

Parameter|Description|Required?
---------|-----------|---------
id|Photo ID|Yes
tag_id|Tag ID|Yes
x|Bounding box origin (horizontal) (0.0 - 1.0)|Yes
y|Bounding box origin (vertical) (0.0 - 1.0)|Yes
width|Bounding box width (0.0 - 1.0)|Yes
height|Bounding box height (0.0 - 1.0)|yes

Coordinates are percentages of the photo dimensions expressed
as floats between 0.0 and 1.0.

### Sample Response ###

On success returns a list of item tag IDs added to the photo.

```json
{
  "success": true,
  "data": {
    "item_tag_ids": [
      "item_tag_1435"
    ]
  }
}
```

### Errors ###

On error, `people_tag` can return one of the following error values:

Error Value|Description
-----------|-----------
`WEBAPI_ERR_BAD_REQUEST`|Missing or invalid parameters
`PHOTOSTATION_PHOTO_TAG_ACCESS_DENY`|User does not have manage permissions in item's album
`PHOTOSTATION_PHOTO_TAG_NOT_EXIST`|Tag ID does not exist
`PHOTOSTATION_PHOTO_TAG_DUPLICATE`|Tag ID already associated with photo
`PHOTOSTATION_PHOTO_TAG_ADD_PEOPLE_FAIL`|Error adding people tag
