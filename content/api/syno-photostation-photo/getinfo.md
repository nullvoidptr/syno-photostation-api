---
title: "getinfo"
description: "Retreive information about one or more items"
---

Retrieve information about one or more photos or videos. Items do not need to
be within the same album (unlike `list`).

### Request ###

Parameter|Description|Required?
---------|-----------|---------
id       |Comma separated list of photo item IDs|Yes
additional|Comma separated list of additional information to return|Optional

### Sample Response ###

```json
{
  "success": true,
  "data": [
    {
      "thumbnail_status": "preview,small,large",
      "id": "photo_6c696272617279_494d475f313636302e4a5047",
      "type": "photo",
      "info": {
        "name": "IMG_1660.JPG",
        "title": "IMG_1660",
        "createdate": "2018-03-05 18:33:18",
        "size": 1344827,
        "takendate": "2011-05-29 17:02:17",
        "resolutionx": 2048,
        "resolutiony": 1536,
        "description": "",
        "rotated": true,
        "rotate_version": 1,
        "rotation": 6,
        "rating": 0
      }
    }
  ]
}
```

#### Additional Information ####

The `getinfo` method `additional` parameter can be used to specify additional
information to return for each album. `additional` is an comma
separated list containing any of the following:

- `photo_exif`
- `video_codec`
- `video_quality`
- `thumb_size`

The returned additional information is contained in the `additional`
field within each return item in the `items` list.

Sample response with `additional=photo_exif,thumb_size`:

```json
{
  "success": true,
  "data": [
    {
      "additional": {
        "photo_exif": {
          "takendate": "2011-05-29 17:02:17",
          "camera": "Apple",
          "camera_model": "iPhone 3GS",
          "exposure": "1/15 sec.",
          "aperture": "f/2.8",
          "iso": 320,
          "gps": {
            "lat": "37.903999",
            "lng": "-122.580666"
          },
          "version": 1,
          "focal_length": "3.8 mm",
          "lens": "",
          "flash": "No flash function"
        },
        "thumb_size": {
          "preview": {
            "resolutiony": 214,
            "resolutionx": 160,
            "mtime": 1579366682
          },
          "small": {
            "resolutiony": 427,
            "resolutionx": 320,
            "mtime": 1579366684
          },
          "large": {
            "resolutiony": 1707,
            "resolutionx": 1280,
            "mtime": 1579366683
          }
        }
      },
      "thumbnail_status": "preview,small,large",
      "id": "photo_6c696272617279_494d475f313636302e4a5047",
      "type": "photo",
      "info": {
        "name": "IMG_1660.JPG",
        "title": "IMG_1660",
        "createdate": "2018-03-05 18:33:18",
        "size": 1344827,
        "takendate": "2011-05-29 17:02:17",
        "resolutionx": 2048,
        "resolutiony": 1536,
        "description": "",
        "rotated": true,
        "rotate_version": 1,
        "rotation": 6,
        "rating": 0
      }
    }
  ]
}
```

### Errors ###

On error, `getinfo` can return one of the following error values:

Error Value|Description
-----------|-----------
`PHOTOSTATION_PHOTO_BAD_PARAMS`|Missing or invalid parameters
`PHOTOSTATION_PHOTO_ACCESS_DENY`|`public_share_id` (if specified) invalid or user does not have permissions to access
