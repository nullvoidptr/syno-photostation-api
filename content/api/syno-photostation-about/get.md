---
title: "get"
description: "Returns personal 'About Me' page"
---

Returns a personal 'About Me' page for the PhotoStation user.

### Request ###

No required or optional parameters.

### Sample Response ###

```json
{
  "success": true,
  "data": {
    "html": "<img src=\"photo_new/images/White/empty_about_me.png\" alt=\"my image\" style=\"padding-bottom: 30px; margin: 10px 20px 50px 0; float: left; width: 150px; height: 150px; opacity: 0.3;\">\n\n<div style=\"line-height: 22px; color: rgb(80, 90, 100); margin-top: 15px;\">\n<span style=\"font-weight: bold;\">Your name</span><br>\n<span>Introduce yourself</span><br>\n<br>\n\n<span style=\"font-weight: bold;\">Contact me:</span><br>\n<span style=\"color: rgb(0, 191, 255);\">Your email address</span><br>\n<span>Your phone number</span><br>\n<span>Your address</span><br>\n<br>\n\n| <span style=\"color: rgb(0, 191, 255);\">Facebook</span>\n| <span style=\"color: rgb(0, 191, 255);\">Twitter</span>\n| <span style=\"color: rgb(0, 191, 255);\">Blog</span> |\n</div>\n",
    "has_content": false
  }
}
```

If there is no personal information provided, `html` will refer to a template
and `has_content` will be `false`.

### Errors ###

On error, `get` can return one of the following error values:

Error Value|Description
-----------|-----------
`WEBAPI_ERR_UNKNOWN`|No 'About Me' HTML page or template can be found
