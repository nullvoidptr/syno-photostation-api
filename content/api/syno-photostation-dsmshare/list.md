---
title: "list"
description: "List contents of a DSM share"
---

List contents of a DSM share. Only lists folders (directories) and those files
which can be imported into PhotoStation (photos, music or videos). The type
of file(s) returned can be filtered with the `type` parameter.

### Request ###

Parameter       |Description|Required?
----------------|-----------|---------
`limit`  |Number of items to return per request (integer)|Yes
`offset` |Starting index of return set (integer starting at 0)|Yes
`type`   |Comma separated list of item types to return (`folder`, `music`, `photo` or `video`)|Yes
`id`     |DSM share ID to list

#### About Share IDs ####

- Base directory appears to be `id = fm_root` (*FileManager root?*)
- DSM shares have type prefix `dsmshare_`
- Remainder of ID is full path (eg. `/volume1/path/to/share`)
  hexencoded ascii (eg. `dsmshare_2f766f6c756d65312f706174682f746f2f7368617265`)

### Response ###

```json
{
  "success": true,
  "data": {
    "items": [
      {
        "id": "dsmshare_2f766f6c756d65312f4261636b757073",
        "name": "Backups",
        "type": "folder"
      },
      {
        "id": "dsmshare_2f766f6c756d65312f646f636b6572",
        "name": "docker",
        "type": "folder"
      },
      {
        "id": "dsmshare_2f766f6c756d65312f686f6d6573",
        "name": "homes",
        "type": "folder"
      },
      {
        "id": "dsmshare_2f766f6c756d65312f4d65646961",
        "name": "Media",
        "type": "folder"
      },
      {
        "id": "dsmshare_2f766f6c756d65312f6d75736963",
        "name": "music",
        "type": "folder"
      },
      {
        "id": "dsmshare_2f766f6c756d65312f7375727665696c6c616e6365",
        "name": "surveillance",
        "type": "folder"
      },
      {
        "id": "dsmshare_2f766f6c756d65312f7574696c73",
        "name": "utils",
        "type": "folder"
      }
    ],
    "total": 7,
    "offset": 0
  }
}
```
