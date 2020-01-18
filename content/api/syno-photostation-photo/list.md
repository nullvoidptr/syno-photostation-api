---
title: "list"
description: "List photos or videos matching query parameters"
---


See also [`SYNO.PhotoStation.Album list`](/api/syno-photostation-album/list).

### Request ###

Parameter |Description|Required?
----------|-----------|---------
`limit`|Number of items to return per request (integer)|Yes
`offset`|Starting index of return set (integer starting at 0)|Yes
`type`|`photo` or `video` only|Yes
`force_update`||Optional
`sort_by`|`filename`, `takendate`, or `createdate`|Optional
`sort_direction`||Optional
`filter_smart`||Optional
`filter_tag`||Opitonal
`filter_album`|Single album ID containing return results|Optional
`filter_shared_album`||Optional
`filter_public_share`||Optional
`item_id`||Optional
`additional`||Optional
`gps`||Optional
`color_label`||Optional
`password`||Optional