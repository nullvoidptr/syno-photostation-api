---
title: "photo_login"
description: "Authenticate user and start a new session (with client verification)"
---

Behave identically to [`login`](/api/syno-photostation-auth/login), but does not set the internal session variable
`skipIPCheckForMobile`. The implication is that `photo_login` will cause the IP
address of the requester (as defined by the server variable `REMOTE_ADDR`) to be
verified against a previously stored value.

It is unclear in which cases this check is performed, if at all.

### Request ###

|Parameter|Description|Required?|
|---------|-----------|---------|
|username |Synology username|Yes
|password |Password|Yes
|remember_me|If set, returned cookie will have 30 day expiration set| Optional

### Sample Response ###

```json
{
  "success": true,
  "data": {
    "sid": "flru8d67ud08plncn12it8fpl0",
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
