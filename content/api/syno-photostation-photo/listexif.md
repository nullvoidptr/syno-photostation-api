---
title: "listexif"
description: "Returns a list of EXIF values"
---

Returns a list of EXIF values of a certain type read from database of all
photos in the PhotoStation instance. For instance, querying with `type=exposure`
will return all the exposure values recorded in the EXIF data across all
imported photos.

### Request ###

Parameter|Description|Required?
---------|-----------|---------
type|One of defined EXIF labels (see below)|Yes

`type` must be one of the following:

- `focal_length`
- `focal_length_v2`
- `flash`
- `flash_v2`
- `lens`
- `lens_v2`
- `rating`
- `camera_make`
- `camera_model`
- `exposure`
- `aperature`
- `iso`

### Sample Response ###

Request with `type=rating`:

```json
{
  "success": true,
  "data": {
    "total": 6,
    "tags": [
      {
        "id": "rating_0",
        "name": "0",
        "type": "exif",
        "tag_type": "rating"
      },
      {
        "id": "rating_1",
        "name": "1",
        "type": "exif",
        "tag_type": "rating"
      },
      {
        "id": "rating_2",
        "name": "2",
        "type": "exif",
        "tag_type": "rating"
      },
      {
        "id": "rating_3",
        "name": "3",
        "type": "exif",
        "tag_type": "rating"
      },
      {
        "id": "rating_4",
        "name": "4",
        "type": "exif",
        "tag_type": "rating"
      },
      {
        "id": "rating_5",
        "name": "5",
        "type": "exif",
        "tag_type": "rating"
      }
    ]
  }
}
```

### Errors ###

On error, `listexif` can return one of the following error values:

Error Value|Description
-----------|-----------
`PHOTOSTATION_PHOTO_BAD_PARAMS`|Missing or invalid parameters
