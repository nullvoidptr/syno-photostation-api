---
title: "uploadphoto"
description: "Upload a photo to PhotoStation"
draft: true
---

Upload a photo file (and optional thumbnails) to an album within PhotoStation.

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

- thumb_small (FILE_THUMB_M)
- thumb_large (FILE_THUMB_XL)

### Sample Request ###

```text
curl -b xxx -F 'original=@/path/to/original/file' -F 'thumb_small=@/path/to/small/thumb' -F 'thumb_large=@/path/to/large/thumb' 'http://synology.local/photo/webapi/file.php?api=SYNO.PhotoStation.File&method=uploadphoto&version=1&dest_folder_path=&duplicate=ignore&filename=myfilename&mtime=XXX'
```

TODO - what is mtime format?

### Sample Response ###
