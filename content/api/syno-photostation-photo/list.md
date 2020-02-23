---
title: "list"
description: "List photos or videos matching query parameters"
---

List photos and/or videos matching a set of query parameters. Unlike
[`SYNO.PhotoStation.Album list`](/api/syno-photostation-album/list) these
items need not be within a certain directory.

### Request ###

Parameter |Description|Required?
----------|-----------|---------
limit|Number of items to return per request (integer)|Yes
offset|Starting index of return set (integer starting at 0)|Yes
type|`photo` or `video` only|Yes
additional|Additional item information to return (see below)|Optional
color_label|Comma separated list of color labels|Optional
filter_album|Parent album ID|Optional
filter_public_share|ID of public share to list|Optional
filter_shared_album|ID of shared album to list|Optional
filter_smart|Smart album ID (predefined query)|Optional
filter_tag|Comma separated list of tag IDs (including `tag_unconfirm`)|Optional
force_update|If `true`, forces update of internal cache before returning|Optional
gps|Display items containing GPS information|Optional
item_id|???|Optional
password|Password for album (if password protected)|Optional
sort_by|`filename`, `takendate`, or `createdate`|Optional
sort_direction|Direction of sorting (`asc` = ascending, `dsc` = descending)|Optional
taken_date|Date taken (can be a single date or range)|Optional

`color_label`, `filter_album`, `filter_public_share`, `filter_shared_album`, `filter_smart`,
`filter_tag`, `gps` and `item_id` are all query parameters that can be used
to restrict the set of items returned to those matching the given values.

Dates may be entered in `Y-m-d` format as either single values or ranges
(either closed or open-ended):

- `DATE`
- `START,END`
- `START,`
- `,END`

#### Query Parameter Precedence ####

Not all queries can be performed simultaneously. The response returned will
depend on which query parameters are present according the following priority:

- If `filter_tag_` is present and set to `tag_unconfirm`, a list of all
 photos with unconfirmed people tags will be returned.
- If `filter_shared_album` is set, the contents of that shared album
  will be returned
- If `filter_public_share` is set, the contents of that public share will
  be returned
- If `filter_smart` is set, the predefined smart album query will be
  performed

If none of the above conditions are met, a query will be performed using the
values of `color_label`, `filter_album`, `filter_tag` and `gps`.

### Sample Response ###

Request with `gps=true`:

```json
{
  "success": true,
  "data": {
    "total": 20216,
    "offset": 4,
    "items": [
      {
        "id": "photo_323031392f323031392d30322d3130_494d472d32303139303231302d32313035333230382e6a7067",
        "type": "photo",
        "pos": 0,
        "info": {
          "name": "IMG-20190210-21053208.jpg",
          "title": "IMG-20190210-21053208",
          "description": "keyword",
          "createdate": "2019-09-17 17:46:14",
          "takendate": "2019-02-10 21:05:32",
          "size": 2811748,
          "resolutionx": 5020,
          "resolutiony": 4016,
          "rotated": false,
          "rotate_version": 0,
          "rotation": 1,
          "lat": 43.05999495,
          "lng": 141.34818732344,
          "rating": 3
        },
        "additional": null,
        "thumbnail_status": "small,large"
      },
      {
        "id": "photo_6c696272617279_494d475f313636302e4a5047",
        "type": "photo",
        "pos": 1,
        "info": {
          "name": "IMG_1660.JPG",
          "title": "IMG_1660",
          "description": "",
          "createdate": "2018-03-05 18:33:18",
          "takendate": "2011-05-29 17:02:17",
          "size": 1344827,
          "resolutionx": 2048,
          "resolutiony": 1536,
          "rotated": true,
          "rotate_version": 1,
          "rotation": 6,
          "lat": 37.903999,
          "lng": -122.580666,
          "rating": 0
        },
        "additional": null,
        "thumbnail_status": "preview,small,large"
      },
      {
        "id": "photo_6c696272617279_494d475f313636342e4a5047",
        "type": "photo",
        "pos": 2,
        "info": {
          "name": "IMG_1664.JPG",
          "title": "IMG_1664",
          "description": "",
          "createdate": "2018-03-05 18:33:18",
          "takendate": "2011-05-29 17:07:01",
          "size": 1236049,
          "resolutionx": 2048,
          "resolutiony": 1536,
          "rotated": true,
          "rotate_version": 1,
          "rotation": 6,
          "lat": 37.903999,
          "lng": -122.580666,
          "rating": 0
        },
        "additional": null,
        "thumbnail_status": "preview,small,large"
      },
      {
        "id": "photo_6c696272617279_494d475f313636352e4a5047",
        "type": "photo",
        "pos": 3,
        "info": {
          "name": "IMG_1665.JPG",
          "title": "IMG_1665",
          "description": "",
          "createdate": "2018-03-05 18:33:18",
          "takendate": "2011-05-29 17:07:04",
          "size": 1179836,
          "resolutionx": 2048,
          "resolutiony": 1536,
          "rotated": true,
          "rotate_version": 1,
          "rotation": 6,
          "lat": 37.903999,
          "lng": -122.580666,
          "rating": 0
        },
        "additional": null,
        "thumbnail_status": "preview,small,large"
      }
    ]
  }
}
```

#### Pagination ####

The pagination of returned results is determined by the values of `limit` and `offset`.
`limit` determines how many items to return in each query while `offset` determines
the starting point for the current return set.

In order to fetch all matches from a list query, the following workflow should be followed:

- send request with `offset=0`
- receive response and examine returned `total` and `offset` values
- if `total == offset`, there are no more items to receive and the query is complete
- send request with `offset` equal to the value of `offset` returned in response
- repeat above until `total == offset`

#### Additional Information ####

The `list` method `additional` parameter can be used to specify additional
information to return for each album. `additional` is an comma
separated list containing any of the following:

- `photo_exif`
- `video_codec`
- `video_quality`
- `thumb_size`

The returned additional information is contained in the `additional`
field within each return item in the `items` list.

### Errors ###

On error, `list` can return one of the following error values:

Error Value|Description
-----------|-----------
`PHOTOSTATION_PHOTO_BAD_PARAMS`|Missing or invalid parameters
`PHOTOSTATION_PHOTO_ACCESS_DENY`|User does not have permissions to `filter_album`