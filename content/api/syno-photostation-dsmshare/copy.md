---
title: "copy"
description: "Copy files from DSM share to PhotoStation"
---

Copy files from DSM share to PhotoStation on same Synology device.

### Request ###

Parameter       |Description|Required?
----------------|-----------|---------
`id` |Comma separated list of IDs to copy|Yes
`sharepath`|Name of destination album|Yes
`duplicate`|`ignore` (default), `rename`, or `overwrite`|Optional

#### `duplicate` Behavior ####

`duplicate` determines how to handle copies which result in the new
file having the same name as an existing file in the album. It can
be one of:

- `ignore` - file will not be copied at all
- `rename` - file will be renamed with a numerical suffix appended
- `overwrite` - existing file will be removed and new file copied in its place

### Response ###

```json
{"success":true}
```
