---
title: "login"
description: "Authenticate user and start a new session"
---

Authenticates a session using `username` and `password`.

There may be additional parameters not listed below as I have not reviewed the
relevant PHP code completely.

See [`photo_login`](/api/syno-photostation-auth/photo_login) for similar functionality.

### Request ###

|Parameter|Description|Required?|
|---------|-----------|---------|
|username|Synology username|Yes
|password|Password|Yes
|remember_me|If set, returned cookie will have 30 day expiration set| Optional

### Sample Response ###

```json
{
  "success": true,
  "data": {
    "sid": "md4ach79mbgrdfa4g17mhgala2",
    "username": "myuser",
    "reg_syno_user": true,
    "is_admin": true,
    "allow_comment": false,
    "permission": {
      "browse": true,
      "upload": true,
      "manage": true
    },
    "enable_face_recog": false,
    "allow_public_share": true,
    "allow_download": true,
    "show_detail": true
  }
}
```

In the event of an incorrect username and/or password, the following response is sent:

```json
{
  "success": false,
  "error": {
    "code": 407
  }
}
```

### Notes ###

In addition to the response above, the `login` method will return a `Set-Cookie` directive
with the key of `PHPSESSID` and a value set to the Session ID (`sid`) seen above.

Additionally, if `remember_me` is set, an expiration date will be set on the cookie for 30 days
from the current time.
