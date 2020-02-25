---
title: "list"
description: "Return tag information for item(s)"
---

Fetch tag information for one or more photos/videos.

### Request ###

Parameter|Description|Required?
---------|-----------|---------
id|Comma separated list of item IDs|Yes
type|Comma separated list of tag types (`people`, `geo` or `desc`)|Yes

### Sample Response ###

If only one `id` is provided, `tags` is an array of JSON tag objects:

```json
{
  "success": true,
  "data": {
    "tags": [
      {
        "id": "tag_103",
        "item_tag_id": "item_tag_1435",
        "type": "people",
        "name": "Eli Manning"
      },
      {
        "id": "tag_28",
        "item_tag_id": "item_tag_1436",
        "type": "desc",
        "name": "Sports"
      }
    ]
  }
}

```

If more than one `id` is provided, `tags` has the following
structure incorporating a `photoId` field:

```json
{
  "success": true,
  "data": {
    "tags": [
      {
        "photoId": "photo_74657374_494d475f32303138313031315f3137323731362e4a5047",
        "tags": [
          {
            "id": "tag_103",
            "item_tag_id": "item_tag_1435",
            "type": "people",
            "name": "Eli Manning"
          },
          {
            "id": "tag_28",
            "item_tag_id": "item_tag_1436",
            "type": "desc",
            "name": "Sports"
          }
        ]
      },
      {
        "photoId": "photo_74657374_494d475f32303139313232355f3134313931392e4a5047",
        "tags": [
          {
            "id": "tag_28",
            "item_tag_id": "item_tag_1437",
            "type": "desc",
            "name": "Sports"
          }
        ]
      }
    ]
  }
}
```

### Errors ###

On error, `list` can return one of the following error values:

Error Value|Description
-----------|-----------
`WEBAPI_ERR_BAD_REQUEST`|Missing or invalid parameters
