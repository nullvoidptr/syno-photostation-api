---
title: "list"
description: "List items in album or matching a query"
---

The `list` method returns a paginated list of items (photos, videos or albums) contained
within a given album or matching a set of user defined queries.

### Request ###

#### Standard Query #####

Standard queries list contents of a particular album. The only filtering is based on type.

Parameter|Description|Required?
---------|-----------|---------
`limit`  |Number of items to return per request (integer)|Yes
`offset` |Starting index of return set (integer starting at 0)|Yes
`type`   |Comma separated list of item types to return (`album`, `photo` and/or `video`)|Yes
`id`     |ID of album being queried (if unset, root album)|Optional
`password` |Password for album (if password protected)|Optional
`additional`|Additional item information to return (see below)|Optional
`sort_by`|Sort method (`filename`, `takendate`, `createdate`, `preference`, `mtime`)|Optional
`sort_direction`|Direction of sorting (`asc` = ascending, `dsc` = descending)|Optional
`force_update`|If `true`, forces update of internal cache before returning|Optional

#### Advanced Queries #####

With advanced queries, users may filter results based on:

- multiple album names
- keywords
- date ranges
- tags
- people
- location
- EXIF information

Each search type contains a value parameter and a corresponding operator parameter which
determines how the query values are treated.

##### Query Values ######

Parameter   |Description|Required?
------------|-----------|---------
`limit`     |Number of items to return per request|Yes
`offset`    |Starting item in return set (starting at 0)|Yes
`type`      |Comma separated list of item types to return (`album`, `photo` and/or `video`)|Yes
`albums`    |Limit query to multiple albums (comma separated). Used in place of `id` above|Optional
`keyword`   |List of keywords (comma separated) to search title and descriptions|Optional
`date`      |Date range (`start_date,end_date`)|Optional
`desc_tag`  |List of general tags to search (comma separated) (maximum 5)|Optional
`people_tag`|List of people tags to search (comma separated) (maximum 20)|Optional
`geo_tag`   |List of location tags to search (comma separated) (maximum 5)|Optional
`camera`    |EXIF Camera Make|Optional
`model`     |EXIF Camera Model|Optional
`exposure`  |EXIF Exposure|Optional
`aperture`  |EXIF Aperature|Optional
`iso`       |EXIF ISO|Optional
`focal`     |EXIF Focal Length|Optional
`lens`      |EXIF Lens|Optional
`flash`     |EXIF Flash|Optional
`rating`    |EXIF Rating|Optional

NOTE: There are `ignore` and `recursive` parameters within the code base, but
it does not appear they are implemented.

###### Query Operators ######

With the exception of `date_op`, the query operators determine whether
all values are required to match or if any single term among the query
values can match. The `date_op` operator determines which type of date
is compared.

Parameter    |Allowed Values
-------------|-----------
keyword_op   |`any`, `all`, `exact`
date_op      |`taken`, `upload`, `recently_add` or `recently_comment`
desc_tag_op  |`any` or `all`
people_tag_op|`any` or `all`
geo_tag_op   |`any` or `all`

While the EXIF values (eg. `camera`, `model`, etc..) also have `_op` parameters (eg. `camera_op`)
the only allowed value is `any` (the default), so they are not required.

### Sample Response ###

Standard query of root album containing four child albums:

```json
{
  "success": true,
  "data": {
    "total": 4,
    "offset": 4,
    "items": [
      {
        "info": {
          "sharepath": "2019",
          "name": "2019",
          "title": "2019",
          "description": "",
          "hits": 0,
          "type": "public",
          "conversion": true,
          "allow_comment": false,
          "allow_embed": true
        },
        "id": "album_32303139",
        "type": "album",
        "additional": null,
        "thumbnail_status": "small,large"
      },
      {
        "info": {
          "sharepath": "2019-08-25",
          "name": "2019-08-25",
          "title": "2019-08-25",
          "description": "",
          "hits": 0,
          "type": "private",
          "conversion": true,
          "allow_comment": false,
          "allow_embed": false
        },
        "id": "album_323031392d30382d3235",
        "type": "album",
        "additional": null,
        "thumbnail_status": "small,large"
      },
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
        "thumbnail_status": "small,large"
      },
      {
        "info": {
          "sharepath": "other",
          "name": "other",
          "title": "other",
          "description": "",
          "hits": 0,
          "type": "private",
          "conversion": true,
          "allow_comment": false,
          "allow_embed": false
        },
        "id": "album_6f74686572",
        "type": "album",
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

The `additional` parameter returns additional optional information for the returned items
based on the list of values provided. The available additional values vary based on the
type of item as shown below:

Value|Type|Description
-----|----|-----------
`file_location`|All|Path to item relative to PhotoStation root directory
`album_createdate`|Album|Creation Date (as UNIX timestamp)
`album_permission`|Album|Permissions (for current user) for album. Each privilege ("browse", "upload", "manage") will have `true` or `false` reported.
`album_sorting`|Album|Default sorting method for album
`delete_permission`|Album|
`item_count`|Album|Number of items within an album (by type)
`thumb_size`|Album|
`photo_exif`|Photo|EXIF metadata information for photo
`video_codec`|Video|Video codec
`video_quality`|Video|Video quality

Any `additional` value that is not compatible with a given item's type will be
silently ignored.

### Errors ###

On error, `list` can return one of the following error values:

Error Value|Description
-----------|-----------
`WEBAPI_ERR_BAD_REQUEST`|Missing or invalid parameter(s) or if album specified by `id` does not exist.
`PHOTOSTATION_ALBUM_NO_ACCESS_RIGHT`|User does not have access rights to album
`PHOTOSTATION_ALBUM_PASSWORD_ERROR`|Incorrect password for album