Forwards
========

Get forwards
-------------

* `GET /projects/1/forwards.json` shows forwards in one project.
* `GET /forwards.json` shows forwards in all projects.

```json
[
  {
    "id": 1072010356,
    "subject": "Proposal",
    "from": null,
    "created_at": "2014-08-19T15:33:08.000-05:00",
    "updated_at": "2014-08-19T15:33:12.000-05:00",
    "private": false,
    "trashed": false,
    "url": "https://basecamp.com/999999999/api/v1/projects/605816632/forwards/1072010356.json",
    "app_url": "https://basecamp.com/999999999/projects/605816632/forwards/1072010356",
    "bucket": {
      "id": 605816632,
      "name": "BCX",
      "type": "Project",
      "url": "https://basecamp.com/999999999/api/v1/projects/605816632.json",
      "app_url": "https://basecamp.com/999999999/projects/605816632"
    }
  },
  {
    "id": 617311580,
    "subject": "Prices",
    "from": "Tom McSalesman (tom@example.com)",
    "created_at": "2014-08-19T15:33:08.000-05:00",
    "updated_at": "2014-08-19T15:33:15.000-05:00",
    "private": false,
    "trashed": false,
    "url": "https://basecamp.com/999999999/api/v1/projects/605816632/forwards/617311580.json",
    "app_url": "https://basecamp.com/999999999/projects/605816632/forwards/617311580",
    "bucket": {
      "id": 605816632,
      "name": "BCX",
      "type": "Project",
      "url": "https://basecamp.com/999999999/api/v1/projects/605816632.json",
      "app_url": "https://basecamp.com/999999999/projects/605816632"
    }
  }
]
```

Buckets are only provided for forwards that are not accessed via a project. For example, todolists returned from `GET /forwards.json` will include their buckets,
but those returned from `GET /projects/1/forwards.json` will not.

### Sorting

It's possible to change the order forwards are returned in with the `sort`
parameter. Forwards can be sorted by subject or age using the parameter values:

* `az` and `za` for subject
* `newest` and `oldest` for age

The default sort is `newest`.


Get forward
------------

* `GET /projects/1/forwards/1.json` will return the specified forward along with all comments.

```json
{
  "id": 617311580,
  "subject": "Prices",
  "from": "Tom McSalesman (tom@example.com)",
  "created_at": "2014-08-19T15:33:08.000-05:00",
  "updated_at": "2014-08-19T15:33:15.000-05:00",
  "private": false,
  "trashed": false,
  "content": "These prices are even better!",
  "content_html": "<html><body><h1>These prices are even better!</h1><p><a href=\"https://basecamp.com\">Check out Basecamp!</a></p></body></html>",
  "creator": {
    "id": 149087659,
    "name": "Jason Fried",
    "avatar_url": "https://asset0.37img.com/global/4113d0a133a32931be8934e70b2ea21efeff72c1/avatar.96.gif?r=3",
    "fullsize_avatar_url": "https://asset0.37img.com/global/4113d0a133a32931be8934e70b2ea21efeff72c1/original.gif?r=3"
  },
  "attachments": [
    {
      "key": "40b8a84cb1a30dbe04457dc99e094b6299deea41",
      "name": "bearwave.gif",
      "byte_size": 508254,
      "content_type": "image/gif",
      "created_at": "2012-03-27T22:48:49-04:00",
      "url": "https://basecamp.com/999999999/api/v1/projects/2222/attachments/3333/40b8a84cb1a30dbe04457dc99e094b6299deea41/original/bearwave.gif",
      "creator": {
        "id": 149087659,
        "name": "Jason Fried",
        "avatar_url": "https://asset0.37img.com/global/4113d0a133a32931be8934e70b2ea21efeff72c1/avatar.96.gif?r=3",
        "fullsize_avatar_url": "https://asset0.37img.com/global/4113d0a133a32931be8934e70b2ea21efeff72c1/original.gif?r=3"
      },
    }
  ],
  "comments": [
    {
      "id": 5566323,
      "content": "Testing a comment",
      "created_at": "2012-03-28T11:36:10-04:00",
      "updated_at": "2012-03-28T11:36:10-04:00",
      "attachments": [],
      "creator": {
        "id": 149087659,
        "name": "Jason Fried",
        "avatar_url": "https://asset0.37img.com/global/4113d0a133a32931be8934e70b2ea21efeff72c1/avatar.96.gif?r=3",
        "fullsize_avatar_url": "https://asset0.37img.com/global/4113d0a133a32931be8934e70b2ea21efeff72c1/original.gif?r=3"
      }
    }
  ],
  "subscribers": [
    {
      "id": 127326141,
      "name": "David Heinemeier Hansson"
    }
  ],
  "bucket": {
    "id": 605816632,
    "name": "BCX",
    "type": "Project",
    "url": "https://basecamp.com/999999999/api/v1/projects/605816632.json"
  }
}
```
