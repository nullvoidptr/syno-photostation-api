---
title: "edit"
description: "Edit photo/video metadata"
---

Update the metadata for one or more items (photo or video).

Note all items will be assigned the same values for any metadata settings passed.

### Request ###

Parameter|Description|Required?
---------|-----------|---------
id|Comma separated list of item IDs|Yes
description|Short description of photo/video|Optional
gps_lat|GPS latitude|Optional
gps_lng|GPS longitude|Optional
title|Title of photo/video|Optional
rating|Rating (0-5)|Optional

Note: any `rating` value greater than 5 will be assigned a value of 5.

Both `gps_lat` and `gps_lng` must be present for changes to be made to GPS coordinates.
If both `gps_lat` and `gps_lng` are present but unset, then the GPS location
data will be removed from the item(s).

### Sample Response ###

```json
{
  "success": true
}
```

Unfortunately the response is not particularly informative as it does not
show any per-item status. Additionally, some errors (for example, attempting
to copy an invalid ID) are never reported.

### Errors ###

On error, `edit` can return one of the following error values:

Error Value|Description
-----------|-----------
`PHOTOSTATION_PHOTO_BAD_PARAMS`|Missing or invalid parameters
