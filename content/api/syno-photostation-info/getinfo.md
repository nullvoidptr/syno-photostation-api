---
title: "getinfo"
description: "Fetch general information about the PhotoStation service"
---

Fetch general information about the PhotoStation service.

### Request ###

No additional parameters

### Sample Response ###

```json
{
  "success": true,
  "data": {
    "version": "3400",
    "title": "",
    "about_me_title": "About Me",
    "sort_by": "filename",
    "sort_direction": "asc",
    "use_album_explorer": true,
    "paging_use_bar": true,
    "paging_item_count": 50,
    "folder_sort_direction": "asc",
    "folder_sort_only_name": false,
    "allow_download_album": false,
    "allow_download_orig": false,
    "allow_download_video": false,
    "disable_right_button": false,
    "hide_search": false,
    "hide_gps_from_normal_user": false,
    "hide_rss_feed": false,
    "enable_blog": false,
    "external_host": "http://10.20.30.40",
    "external_host_quickconnect": "https://my-synology.us.quickconnect.to",
    "allow_social_share": true,
    "allow_social_upload": false,
    "allow_social_upload_guest": false,
    "social_network_list": [
      {
        "name": "Facebook",
        "enable": false,
        "allowShare": true,
        "allowSingleUpload": true,
        "allowMultiUpload": true,
        "allowPhoto": true,
        "allowVideo": false
      },
      {
        "name": "Twitter",
        "enable": true,
        "allowShare": true,
        "allowSingleUpload": true,
        "allowMultiUpload": false,
        "allowPhoto": true,
        "allowVideo": false
      },
      {
        "name": "Plurk",
        "enable": false,
        "allowShare": true,
        "allowSingleUpload": false,
        "allowMultiUpload": false,
        "allowPhoto": false,
        "allowVideo": false
      },
      {
        "name": "Weibo",
        "enable": false,
        "allowShare": true,
        "allowSingleUpload": true,
        "allowMultiUpload": false,
        "allowPhoto": true,
        "allowVideo": false
      },
      {
        "name": "QQ",
        "enable": false,
        "allowShare": true,
        "allowSingleUpload": true,
        "allowMultiUpload": false,
        "allowPhoto": true,
        "allowVideo": false
      },
      {
        "name": "YouTube",
        "enable": false,
        "allowShare": false,
        "allowSingleUpload": true,
        "allowMultiUpload": false,
        "allowPhoto": false,
        "allowVideo": true
      },
      {
        "name": "Flickr",
        "enable": true,
        "allowShare": false,
        "allowSingleUpload": true,
        "allowMultiUpload": true,
        "allowPhoto": true,
        "allowVideo": false
      }
    ],
    "virtual_tag": {
      "desc_tag": true,
      "geo_tag": false,
      "people_tag": false
    },
    "default_geo_location": {
      "lng": "",
      "lat": ""
    },
    "home_category": null,
    "default_album_public": false,
    "disable_aboutme": false,
    "show_album_hit": false,
    "use_dsm_account": true,
    "collapse_left_panel": false,
    "show_lightbox_information": false,
    "use_pop_window_to_edit_desc": false,
    "def_album_disable_conversion": false,
    "support_large_file": true,
    "support_moments": true
  }
}
```
