---
title: "listfeatureditem"
description: "<!-- Enter description -->"
draft: true
---

NOTE: It is currently unclear what "Featured Item" means

### Request ###

<!-- Enter request parameters here. "Yes" or "Optional" under Required? -->
Parameter|Description|Required?
---------|-----------|---------
count|Numer of items to return (-1 means return all)|Yes
taken_date|Date taken (can be a single date or range)|Yes
filter_album|Optional *
filter_smart||Optional *
filter_tag|Comma separated list of tag IDs|Optional *

NOTE: one of either `filter_album`, `filter_smart` or `filter_tag` must be set.

Dates may be entered in `Y-m-d` format as either single values or ranges
(either closed or open-ended):

- `DATE`
- `START,END`
- `START,`
- `,END`

### Sample Response ###

```json
{
  "success": true
}
```

### Errors ###

On error, `listfeatureditem` can return one of the following error values:

Error Value|Description
-----------|-----------
`PHOTOSTATION_PHOTO_BAD_PARAMS`|Missing or invalid parameters