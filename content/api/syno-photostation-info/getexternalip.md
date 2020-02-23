---
title: "getexternalip"
description: "Fetch external IP address for PhotoStation"
---

Fetch the external IP address of the PhotoStation device. Depending on the
configuration this may be a static IP address, a dynamically assigned DNS
name or a Synology Quickconnect URL.

NOTE: This requires `version=2` to process.

### Request ###

No additional parameters required.

### Sample Response ###

```json
{
  "success": true,
  "data": {
    "external_host_external_ip": "https://my-synology.us.quickconnect.to"
  }
}
```
