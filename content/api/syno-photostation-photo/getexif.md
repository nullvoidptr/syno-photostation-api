---
title: "getexif"
description: "Fetch EXIF data for photo"
---

Fetches EXIF data stored in photo file. Returns array of `label`/`value` pairs
of all EXIF data that can be tranlated by the `exiv2` program.

### Request ###

Parameter|Description|Required?
---------|-----------|---------
id       |Photo item ID|Yes

### Sample Response ###

With `data`, the `exifs` array contains a list of `label`/`value` pairs for all
decoded EXIF data points. The `total` field indicates the number of pairs
that can be read.

```json
{
  "success": true,
  "data": {
    "total": 49,
    "exifs": [
      {
        "label": "Manufacturer",
        "value": "Apple"
      },
      {
        "label": "Model",
        "value": "iPhone 3GS"
      },
      {
        "label": "Orientation",
        "value": "right, top"
      },
      {
        "label": "X-Resolution",
        "value": "72"
      },
      {
        "label": "Y-Resolution",
        "value": "72"
      },
      {
        "label": "Resolution Unit",
        "value": "inch"
      },
      {
        "label": "Software",
        "value": "4.3.3"
      },
      {
        "label": "Date and Time",
        "value": "2011:05:29 17:02:17"
      },
      {
        "label": "YCbCr Positioning",
        "value": "Centered"
      },
      {
        "label": "Exif IFD Pointer",
        "value": "206"
      },
      {
        "label": "Exposure Time",
        "value": "1/15 s"
      },
      {
        "label": "FNumber",
        "value": "F2.8"
      },
      {
        "label": "Exposure Program",
        "value": "Auto"
      },
      {
        "label": "ISO Speed Ratings",
        "value": "320"
      },
      {
        "label": "Exif Version",
        "value": "2.21"
      },
      {
        "label": "Date and Time (original)",
        "value": "2011:05:29 17:02:17"
      },
      {
        "label": "Date and Time (digitized)",
        "value": "2011:05:29 17:02:17"
      },
      ... truncated ...
      {
        "label": "JPEG Interchange Format Length",
        "value": "10790"
      }
    ]
  }
}

```

### Errors ###

On error, `getexif` can return one of the following error values:

Error Value|Description
-----------|-----------
`PHOTOSTATION_PHOTO_BAD_PARAMS`|Missing or invalid parameters. Also if `id` refers to an invalid photo path
