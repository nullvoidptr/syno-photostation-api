---
title: "Session Login"
weight: 20
---

To interact properly with Synology PhotoStation, one must login first. This is
done via a call to the `login` method of the [`SYNO.PhotoStation.Auth`](/api/syno-photostation-auth/) API.

The default method for session management is to use cookies storing a session ID.
As such, applications should be written to handle HTTP `Set-Cookie` requests.

Note that some APIs may not require an authenticated user if the relevant resources
are publicly viewable.

## Example ##

### Request ###

```text
curl 'http://synology.local/photo/webapi/auth.php?api=SYNO.PhotoStation.Auth&method=login&version=1&username=myuser&password=mypass'
```

### Response ###

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

The most important field of the response is `sid`, ie. session ID. This will need to
be set in a cookie for subsequent requests in order to use the authenticated session.
