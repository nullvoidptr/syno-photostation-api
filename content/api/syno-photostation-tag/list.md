---
title: "list"
description: "<!-- Enter description -->"
---

<!-- Enter summary here -->

### Request ###

<!-- Enter request parameters here. "Yes" or "Optional" under Required? -->
Parameter|Description|Required?
---------|-----------|---------
limit|Number of items to return per request (integer)|Yes
offset|Starting index of return set (integer starting at 0)|Yes
type|Comma separated list of tag types (`people`, `geo`and/or `desc`)|Yes
sort_direction|Direction of sorting (`asc` = ascending, `dsc` = descending)|Optional
unconfirm_people_tag|If `true`, display unconfirmed people tags as well|Optional

### Sample Response ###

```json
{
  "success": true,
  "data": {
    "total": 11,
    "offset": 5,
    "tags": [
      {
        "id": "tag_102",
        "type": "tag",
        "tag_type": "desc",
        "name": "CC"
      },
      {
        "id": "tag_24",
        "type": "tag",
        "tag_type": "desc",
        "name": "Family"
      },
      {
        "id": "tag_27",
        "type": "tag",
        "tag_type": "desc",
        "name": "Football"
      },
      {
        "id": "tag_7",
        "type": "tag",
        "tag_type": "desc",
        "name": "Halloween"
      },
      {
        "id": "tag_2",
        "type": "tag",
        "tag_type": "desc",
        "name": "Japan"
      }
    ]
  }
}

```

#### Pagination ####

The pagination of returned results is determined by the values of `limit` and `offset`.
`limit` determines how many items to return in each query while `offset` determines
the starting point for the current return set.

In order to fetch all matches from a list query, the following workflow should be followed:

- send request with `offset=0`
- receive response and examine returned `total` and `offset` values
- if `total == offset`, there are no more items to receive and the query is complete
- send request with `offset` equal to the value of `offset` returned in response
- repeat above until `total == offset`

### Errors ###

On error, `list` can return one of the following error values:

Error Value|Description
-----------|-----------
`WEBAPI_ERR_BAD_REQUEST`|Missing or invalid parameters
