---
title: "set"
description: "Upload a personal 'About Me' webpage"
---

Upload a personal 'About Me' webpage for the PhotoStation owner.

### Request ###

Parameter|Description|Required?
---------|-----------|---------
html|HTML contents of desired webpage|Yes

### Sample Response ###

```json
{
  "success": true
}
```

### Errors ###

On error, `set` can return one of the following error values:

Error Value|Description
-----------|-----------
`WEBAPI_ERR_BAD_REQUEST`|Missing parameter
`WEBAPI_ERR_NO_PERMISSION`|User does not have admin permissions
`WEBAPI_ERR_UNKNOWN`|Error saving webpage
