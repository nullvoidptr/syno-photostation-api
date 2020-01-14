---
title: "checkauth"
description: "Validate current session and return session info"
---

Performs a validation of the current session and returns the same information returned by
successful [`login`](/api/syno-photostation-auth/login) request.

##### Request #####

No additional parameters required.

##### Sample Response #####

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
