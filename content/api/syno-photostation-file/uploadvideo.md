---
title: "uploadvideo"
description: "Upload a video file to PhotoStation"
draft: yes
---
Upload a video file to PhotoStation

### Request ###

Parameter       |Description|Required?
----------------|-----------|---------
dest_folder_path|Destination folder on PhotoStation (relative to root album) |Yes
duplicate       |Defines how to handle duplicate files. Must be one of: `ignore`, `rename` or `overwrite`|Yes
filename        |Destination filename|Yes
mtime           |Modification time  |Yes

In addition the file being uploaded must be sent via HTTP POST method with form name `original`.
Other forms of the same photo can be uploaded at the same time (eg. thumbnails) provided they
are identified by one of the following form names in the request:

- high
- medium
- low
- mobile
- iphone
- android
- flv