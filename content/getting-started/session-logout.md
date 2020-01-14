---
title: "Session Logout"
weight: 50
---

Once interaction is complete, it is desirable to logout of the session to
ensure any session IDs stored locally are not valid.

Logging out requires a call the [`SYNO.PhotoStation.Auth`](/api/syno-photostation-auth) `logout`
method. This will render the current session invalid.

## Example ##

### Request ###

```text
curl  -b PHPSESSID=md4ach79mbgrdfa4g17mhgala2 'http://synology.local/photo/webapi/auth.php?api=SYNO.PhotoStation.Auth&method=logout&version=1'
```

### Response ###

```json
{ "success": true }
```
