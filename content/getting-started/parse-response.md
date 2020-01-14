---
title: "Parse API Response"
weight: 40
---

Each API request should result in a response from the PhotoStation server. The response
data is in JSON format allowing easy decoding of returned data. Note that for
the most part, HTTP response codes are not used for errors. Instead one must
check the JSON data for the `success` field to detect errors.

## Parsing Responses ##

All responses should return a `200 OK` HTTP status (regardless of success or failure of
the operation itself) and contain a JSON-formatted body with the following fields:

Field|Type|Description
-----|----|-----------
`success`|Boolean|`true` if operation was successful, `false` otherwise.
`data`|Object|If successful, contains any API specific return data. On error, no `data` object is returned.
`error`|Object|If unsuccessful, an `error` object is returned containing a `code` field with a numeric error code describing the condition.

### Successful Response ###

```json
{
    "success": true,
    "data": {...}
}
```

### Error Response ###

```json
{
    "success": false,
    "error": {
        "code": 101
    }
}
```

## Common Error Codes ##

The following are error codes common for all APIs. Additional codes may
be defined on a per-API basis to handle more specific error conditions.

Code|Name                              |Description
----|----------------------------------|-----------
100 |`WEBAPI_ERR_UNKNOWN`              |Unknown error
101 |`WEBAPI_ERR_BAD_REQUEST`          |The request is malformed. Typically this means a required argument is missing.
102 |`WEBAPI_ERR_NO_SUCH_API`          |The requested API is not defined.
103 |`WEBAPI_ERR_NO_SUCH_METHOD`       |The requested method for this API is not defined.
104 |`WEBAPI_ERR_NOT_SUPPORTED_VERSION`|The requested version is not supported.
105 |`WEBAPI_ERR_NO_PERMISSION`        |The user session does not have required permissions.
106 |`WEBAPI_ERR_SESSION_TIMEOUT`      |The session has timed out.
107 |`WEBAPI_ERR_SESSION_INTERRUPT`    |The session was interrupted by a duplicate login

Note: The names above are taken from `photo/webapi/sdk/WebAPI.inc.php` from the
PhotoStation package code.

## Example ##

See [Perform API Request](/getting-started/perform-request) in prior step for
example successful response to an API request.