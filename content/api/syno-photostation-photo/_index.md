---
title: "SYNO.PhotoStation.Photo"
description: "Manage photos within PhotoStation albums"
---

### Common Request Fields ###

Parameter |Description|Required?
----------|-----------|---------
public_share_id||Optional
filter_public_share||Optional

These optional settings determine the public share session cache used during processing.
These parameters may be set for all `Photo` API requests.

TODO - what does this mean?

### Error Codes ###

The following error codes are specific to `SYNO.PhotoStation.Photo`:

Code|Name                                 |Description
----|-------------------------------------|-----------
456 |`PHOTOSTATION_PHOTO_BAD_PARAMS`      |Missing or invalid parameters in request
457 |`PHOTOSTATION_PHOTO_ACCESS_DENY`     |
458 |`PHOTOSTATION_PHOTO_SELECT_CONFLICT` |

### Available Methods ###
