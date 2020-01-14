---
title: "Get API Information"
weight: 10
---


In order to interact with the Synology PhotoStation API, one needs to know the
actual API names and versions available on a given running instance. This is
important as software version changes may lead to breaking API changes. Thus
developers would need to know API versioning on a system when interacting with it.

This information is available via the `query` method of the
[`SYNO.API.Info`](/api/syno-api-info/) API
accessible at `photo/webapi/query.cgi`. A request to this API will return the
following information for all available APIs:

- API Name
- CGI path
- Minimum / maximum supported versions

See [`SYNO.API.Info`](/api/syno-api-info/) reference for further details.

## Example ##

Below is an example of accessing the API information for a Synology NAS running PhotoStation.
This and all examples will used the [curl](https://curl.haxx.se/) command line tool
available for most operating systems. Additionally, we are using `synology.local` as the
hostname of the Synology NAS being accessed. This should be replaced with the actual desired
hostname or IP address.

Further information on the request and response formats can be found in the next sections.

### Request ###

```sh
curl 'http://synology.local/photo/webapi/query.php?api=SYNO.API.Info&method=query&version=1&query=all'
```

### Response ###

*NOTE: This response is truncated for clarity. A typical response from SYNO.API.Info would report more APIs available*

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
    }
  }
}
```


