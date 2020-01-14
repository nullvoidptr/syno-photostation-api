---
title: "getinfo"
description: "Fetch information for one or more albums"
---

Get information about one or more albums

### Request ###

TODO: Verify comma separated album IDs works

|Parameter|Description|Required?|
|---------|-----------|---------|
|id |Comma separated list of album IDs (root album if none)|Optional
|additional|Comma separated list of additional information to return (see below)|Optional

If no `id` is set, information on the root album will be returned.

Other parameters ?

### Response ###

```json
{
  "success": true,
  "data": {
    "items": [
      {
        "info": {
          "sharepath": "iphone",
          "name": "iphone",
          "title": "iphone",
          "description": "",
          "hits": 0,
          "type": "private",
          "conversion": true,
          "allow_comment": false,
          "allow_embed": false
        },
        "id": "album_6970686f6e65",
        "type": "album",
        "additional": null,
        "thumbnail_status": "default",
        "cover": {
          "w": 0,
          "h": 0,
          "hash": ""
        }
      }
    ]
  }
}
```

##### Additional Information #####

The `getinfo` method `additional` parameter can be used to specify additional
information to return for each album. `additional` is an comma
separated list containing any of the following:

- `album_createdate`
- `album_permission`
- `album_sorting`
- `delete_permission`
- `file_location`
- `item_count`
- `thumb_size`

The returned additional information is contained in the `additional`
field within each return item in the `items` list.

Sample response with all `additional` flags set:

```json
{
  "success": true,
  "data": {
    "items": [
      {
        "info": {
          "sharepath": "iphone",
          "name": "iphone",
          "title": "iphone",
          "description": "",
          "hits": 0,
          "type": "private",
          "conversion": true,
          "allow_comment": false,
          "allow_embed": false
        },
        "id": "album_6970686f6e65",
        "type": "album",
        "additional": {
          "album_sorting": {
            "sort_by": "preference",
            "sort_direction": "asc",
            "has_preference_sort": true
          },
          "album_permission": {
            "browse": false,
            "upload": false,
            "manage": false
          },
          "item_count": {
            "photo": 2531,
            "video": 264
          },
          "delete_permission": false,
          "album_createdate": 1578419832,
          "file_location": "iphone",
          "thumb_size": {
            "preview": {
              "resolutionx": 0,
              "resolutiony": 0
            },
            "small": {
              "resolutionx": 0,
              "resolutiony": 0
            },
            "large": {
              "resolutionx": 0,
              "resolutiony": 0
            },
            "sig": ""
          }
        },
        "thumbnail_status": "default",
        "cover": {
          "w": 0,
          "h": 0,
          "hash": ""
        }
      }
    ]
  }
}
```
