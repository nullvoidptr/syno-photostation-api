---
title: "copymusic"
description: "Copy music files from DSM share to PhotoStation"
---

Copy music files from DSM share to PhotoStation on same Synology device
for use in slideshows. The files are stored in the hidden `@eaDir` directory
in the root of the `photo` volume. There is a limit to the number of
music files that can be added (currently 10), if any files in excess of
this limit are attempted to be added, an error will be returned.

### Request ###

Parameter       |Description|Required?
----------------|-----------|---------
`id` |Comma separated list of IDs to copy|Yes

### Response ###

```json
{"success":true}
```