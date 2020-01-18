---
title: "uploadphoto"
description: "Upload a photo to PhotoStation"
---

Upload a photo file (and optional thumbnails) to an album within PhotoStation.

### Request ###

Parameter       |Description|Required?
----------------|-----------|---------
dest_folder_path|Destination folder on PhotoStation (relative to root album) |Yes
duplicate       |Defines how to handle duplicate files. Must be one of: `ignore`, `rename` or `overwrite`|Yes
filename        |Destination filename (see Notes below)|Yes
mtime           |Modification time (UNIX timestamp) |Yes

In addition the file being uploaded must be sent via HTTP POST method with form name `original`.
Other forms of the same photo can be uploaded at the same time (eg. thumbnails) provided they
are identified by one of the following form names in the request:

- thumb_small (FILE_THUMB_M)
- thumb_large (FILE_THUMB_XL)

### Sample Request ###

```text
curl -b PHPSESSID=xxx \
     -F 'original=@/path/to/original/file' \
     -F 'thumb_small=@/path/to/small/thumb' \
     -F 'thumb_large=@/path/to/large/thumb' \
     'http://synology.local/photo/webapi/file.php?api=SYNO.PhotoStation.File&method=uploadphoto&version=1&dest_folder_path=&duplicate=ignore&filename=myfilename.jpg&mtime=1579384308'
```

### Sample Response ###

```json
{"success":true}
```

### Notes ###

- The destination filename (`filename`) must end in a supported file extension:

Type|Extension
----|---------
Photo| 'jpg', 'jpeg', 'jpe', 'bmp', 'gif', 'png', 'tiff', 'tif'
Photo (raw) (Sony)| `arw`, `srf`, `sr2`
Photo (raw) (Kodak)|`dcr`, `k25`, `kdc`
Photo (raw) (Canon)|`cr2`,`crw`
Photo (raw) (Nikon)|`nef`
Photo (raw) (Minolta)|`mrw`
Photo (raw) (Pentax)|`ptx`, `pef`
Photo (raw) (Fuji)|`raf`
Photo (raw) (Hasselblad)|`3fr`
Photo (raw) (Epson)|`erf`
Photo (raw) (Mamiya)|`mef`
Photo (raw) (Leaf)|`mos`
Photo (raw) (Olympus)|`orf`
Photo (raw) (Panasonic)|`rw2`
Photo (raw) (Adobe Digital Negative)|`dng`
Photo (raw) (Sigma Raw Image)|`x3f`
Photo (raw) (Panasonic)|`raw`
Video| `mpg`, `mpeg`, `avi`, `wmv`, `asf`, `mov`, `flv`, `f4v`, `3gp`, `3g2`,  `mp4`, `m4v`, `qt`, `divx`, `xvid`, `dat`, `m2ts`, `m2t`, `mts`
