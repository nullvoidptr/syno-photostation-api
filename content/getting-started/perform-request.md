---
title: "Perform API Request"
weight: 30
---

Once a session is established, requests can be made to the APIs defined in
the [`SYNO.API.Info`](/api/syno-api-info) `query` response.

## Making An API Request ##

PhotoStation API requests are standard HTTP `GET` or `POST` requests made to
a specified URL and containing a required set of parameters, either in URL
query string or URL-encoded in the body of a `POST` request.

NOTE: While responses sent from the PhotoStation API are in JSON format,
requests are not.

### Determining API Path ###

The base URL for PhotoStation is at `http://<synology_host>/photo/webapi`. All
APIs reference specific `cgi` or `php` files contained within this server path. In order
to find the correct path for a given API, reference the response to a
`query` request to `SYNO.API.Info` at `/photo/webapi/query.cgi`.

For example, based on the example response to `SYNO.API.Info` `query` in the
[previous section](/getting-started/get-api-info) the path for `SYNO.PhotoStation.Album`
requests would be `album.php`
(ie. the full URL would be `http://<synology_host>/photo/webapi/album.php`).

### Required Parameters ###

All API requests must contain the following parameters at a minimum (individual
APIs may have additional requirements)

|Parameter|Description|
|---------|-----------|
|api|Name of the API being referenced (eg. `SYNO.PhotoStation.Album`)
|version|Version of the API to use (integer)
|method|Name of the method being accessed (eg. `getinfo`)

As mentioned previously, these can be sent either as query parameters
as part of the request URL or as URL-encoded key-value pairs as part
of the body of a `POST` request.

## Example ##

Below is a sample request using the [`SYNO.PhotoStation.Album`](/api/syno-photostation-album)
API's `list` method. This request returns a listing of all albums in the root of the
PhotoStation service. Note that the `list` method requires the additional parameters
`limit`, `offset` and `type` so these are provided in our `curl` call below.

### Request ###

```text
curl -b PHPSESSID=md4ach79mbgrdfa4g17mhgala2 'http://synology.local/photo/webapi/album.php?api=SYNO.PhotoStation.Album&method=list&version=1&limit=50&type=album&offset=0
```

**NOTE:** We use the `-b KEY=VALUE` option in `curl` to set the cookie
which will be sent with our request. The key is always `PHPSESSID` and
the value is the `sid` value returned from the [`SYNO.PhotoStation.Auth`](/api/syno-photostation-auth) `login` response.

### Response ###

```json
{
  "success": true,
  "data": {
    "total": 3,
    "offset": 3,
    "items": [
      {
        "info": {
          "sharepath": "2019",
          "name": "2019",
          "title": "2019",
          "description": "",
          "hits": 0,
          "type": "public",
          "conversion": true,
          "allow_comment": false,
          "allow_embed": true
        },
        "id": "album_32303139",
        "type": "album",
        "additional": null,
        "thumbnail_status": "small,large"
      },
      {
        "info": {
          "sharepath": "iphone",
          "name": "iphone",
          "title": "iphone",
          "description": "",
          "hits": 0,
          "type": "private",
          "conversion": true,
          "allow_comment": false,
          "allow_embed": false
        },
        "id": "album_6970686f6e65",
        "type": "album",
        "additional": null,
        "thumbnail_status": "small,large"
      },
      {
        "info": {
          "sharepath": "other",
          "name": "other",
          "title": "other",
          "description": "",
          "hits": 0,
          "type": "private",
          "conversion": true,
          "allow_comment": false,
          "allow_embed": false
        },
        "id": "album_6f74686572",
        "type": "album",
        "additional": null,
        "thumbnail_status": "preview,small,large"
      }
    ]
  }
}
```
