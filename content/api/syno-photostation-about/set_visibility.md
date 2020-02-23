---
title: "set_visibility"
description: "Change 'About Me' visibility"
---

Change the visibility of the 'About Me' page and/or its name.

### Request ###

Parameter|Description|Required?
---------|-----------|---------
hidden|If `true`, do not display 'About Me' page|Optional
title|Alternate title of 'About Me' page|Optional

### Sample Response ###

```json
{
  "success": true
}
```

### Errors ###

On error, `set_visibility` can return one of the following error values:

Error Value|Description
-----------|-----------
`WEBAPI_ERR_NO_PERMISSION`|User does not have admin permissions
