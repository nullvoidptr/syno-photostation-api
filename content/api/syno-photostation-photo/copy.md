---
title: "copy"
description: "Copy or move photos and/or videos"
---

Copy or move a set of photos and/or videos.

### Request ###

Parameter  |Description|Required?
-----------|-----------|---------
`id`       |Comma separated list of items (photos or videos) |Yes
`sharepath`|Album ID of destination album|Yes
`mode`     |`copy` or `move`|Yes
`duplicate`|`rename`, `ignore` or `overwrite`|Yes

### Sample Response ###

```json
{
  "success": true
}
```

Unfortunately the response is not particularly informative as it does not
show any per-item status. Additionally, some errors (for example, attempting
to copy an invalid ID) are never reported.
