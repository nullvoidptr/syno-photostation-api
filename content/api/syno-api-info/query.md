---
title: "query"
description: "Fetch information on available APIs"
---

Returns a list of matching API names and their supported versions.

### Request ###

|Parameter|Description|Required?|
|---------|-----------|---------|
|query    |Comma separated list of API names to return. Use `all` to return all APIs.| Yes

### Sample Response ###

```json
{
  "success": true,
  "data": {
    "SYNO.PhotoStation.Auth": {
      "path": "auth.php",
      "minVersion": 1,
      "maxVersion": 1
    },
    "SYNO.PhotoStation.Info": {
      "path": "info.php",
      "minVersion": 1,
      "maxVersion": 2
    },
    "SYNO.PhotoStation.Album": {
      "path": "album.php",
      "minVersion": 1,
      "maxVersion": 1
    },
    "SYNO.PhotoStation.Permission": {
      "path": "permission.php",
      "minVersion": 1,
      "maxVersion": 1
    },
    "SYNO.PhotoStation.Photo": {
      "path": "photo.php",
      "minVersion": 1,
      "maxVersion": 1
    },
    "SYNO.PhotoStation.Thumb": {
      "path": "thumb.php",
      "minVersion": 1,
      "maxVersion": 1
    },
    ...
    "SYNO.API.Info": {
      "path": "query.php",
      "minVersion": 1,
      "maxVersion": 1
    }
  }
}
```

### Notes ###

As the general [API workflow](/getting-started) recommends querying `SYNO.API.Info`
prior to authentication, no session cookie or token is required for this API call.