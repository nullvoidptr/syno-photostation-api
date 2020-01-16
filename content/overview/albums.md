---
title: "Albums"
draft: true
---

## Albums Overview ##

Albums are collections of photos, videos and other albums. There are three
types of albums:

- standard albums
- shared albums
- smart albums

Standard albums are simply directories within the Synology storage volume
used by PhotoStation. Any photo, video or album within a directory will
be associated with the album of that directory.

Shared albums are albums that have been deliberately shared with the public.
These albums are accessible via a public shared link that can then be sent
to friends, posted on social media or otherwise shared with people who do
not have direct access to the Synology NAS.

Smart albums are dynamic collections of photos and videos based on various
user-defined filters. For example, a smart album could be created to collect
all photos taken in a specific year or having a particular tag. Photos and
videos in smart albums remain stored in their original standard album.

## Album Permission Types ##

Each standard album can have one of the following permission types:

- public
- private
- password

Public albums are viewable by anyone with access to the Synology PhotoStation
GUI. With respect to API access, these can be seen without requiring authentication.
These are not the same as shared albums which are accessible via the internet
via a special shared link.

Private albums are only viewable by specific users (by default the owner and
any administrator users). Additional users can be granted permission to
these albums separately (see below).

Password albums are accessible to all users (without user-level authentication)
but have album-specific password that must be entered to view.

NOTE: Only albums in the PhotoStation root or with an immediate parent
in the PhotoStation root (ie. second level albums) can have permission
types set. Any albums below the second level will inherit their permission
model from their parent.

## Album User Privileges ##

Beyond the permission types mentioned above, each album can has a set of specific
privileges that can be enabled or disabled on a user or group basis:

- Browse
- Upload
- Manage

Users with "Browse" privilege will be able to view photos in private albums they
do not own (they will already be able to view public albums).

Users with "Upload" privilege can upload new photos or videos to the album.

Users with "Manage" privilege can perform most operation on photos and albums
including editing metadata, etc...

Users in the DSM administrator group will automatically have all privileges for
all albums in PhotoStation.

## Download Privileges ##

By default, even users with "Browse" access to an album will not see any button
to download the original image or video file. There is PhotoStation global setting
that will allow all users to download any file they have viewing permissions for.

