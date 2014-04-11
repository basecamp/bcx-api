Comments
========

> HATERS GONNA HATE


Get comments
------------

Comments are included on the [topics](https://github.com/basecamp/bcx-api/blob/master/sections/topics.md) directly. So to see all comments for a message, you'd just GET that message and they're included and look like this:

```json
{
  "comments": [
    {
      "id": 1028592764,
      "content": "Yeah, really, welcome!",
      "created_at": "2012-03-22T16:56:48-05:00",
      "updated_at": "2012-03-22T16:56:48-05:00",
      "attachments":[
         {
            "key": "40b8a84cb1a30dbe04457dc99e094b6299deea41",
            "name": "bearwave.gif",
            "byte_size": 508254,
            "content_type":"image/png",
            "created_at":"2012-03-27T22:48:49-04:00",
            "url":"https://basecamp.com/1111/api/v1/projects/2222/attachments/3333/40b8a84cb1a30dbe04457dc99e094b6299deea41/original/bearwave.gif",
            "creator":{
               "id": 73,
               "name": "Nick Quaranto",
               "avatar_url": "https://asset0.37img.com/global/4113d0a133a32931be8934e70b2ea21efeff72c1/avatar.96.gif?r=3",
               "fullsize_avatar_url": "https://asset0.37img.com/global/4113d0a133a32931be8934e70b2ea21efeff72c1/original.gif?r=3"
            }
         }
      ],
      "creator": {
        "id": 149087659,
        "name": "Jason Fried",
        "avatar_url": "https://asset0.37img.com/global/4113d0a133a32931be8934e70b2ea21efeff72c1/avatar.96.gif?r=3",
        "fullsize_avatar_url": "https://asset0.37img.com/global/4113d0a133a32931be8934e70b2ea21efeff72c1/original.gif?r=3"
      }
    }
  ]
}
```


Create comment
--------------

* `POST /projects/1/<section>/1/comments.json` will create a new comment from the parameters passed for the commentable described via <section>/<id> -- for example /projects/1/messages/1/comments.json or /projects/1/todos/1/comments.json. The subscribers array is an optional list of people IDs that you want to notify about this comment (see [Get accesses](https://github.com/basecamp/bcx-api/blob/master/sections/accesses.md) on how to get the people IDs for a given project).

```json
{
  "content": "Imma let you finish, but...",
  "subscribers": [ 1, 5, 6]
}
```

This will return `201 Created`, with a representation of the comment just created in the response body if the creation was a success. The topic can be accessed via the `topic_url` parameter. For example:

```json
{
  "id": 1028592764,
  "content": "Yeah, really, welcome!",
  "created_at": "2012-03-22T16:56:48-05:00",
  "updated_at": "2012-03-22T16:56:48-05:00",
  "creator": {
    "id": 149087659,
    "name": "Jason Fried",
    "avatar_url": "https://asset0.37img.com/global/4113d0a133a32931be8934e70b2ea21efeff72c1/avatar.96.gif?r=3",
    "fullsize_avatar_url": "https://asset0.37img.com/global/4113d0a133a32931be8934e70b2ea21efeff72c1/original.gif?r=3"
  },
  "topic_url": "https://basecamp.com/9999999/api/v1/messages/888888.json"
}
```

### Attaching files

Attaching files to a comment requires both the token and the name of the attachment. The
token is returned from the [Create attachments](https://github.com/basecamp/bcx-api/blob/master/sections/attachments.md)
endpoint, which you must hit first before creating an upload.

The `name` parameter *must* be a valid filename with an extension. Multiple
attachments are allowed.

```json
{
  "content": "Here's the stuff",
  "attachments": [
    {
      "token": "4f71ea23-134660425d1818169ecfdbaa43cfc07f4e33ef4c",
      "name": "final_mockup.png"
    },
    {
      "token": "4f71ea23-458294fc0d87927301c5d54b69a7517602939e2c",
      "name": "draft_agreement.png"
    }
  ]
}
```


Delete comment
-------------

* `DELETE /projects/1/comments/1.json` will delete the comment specified and return `204 No Content` if that was successful. If the user does not have access to delete the comment, you'll see `403 Forbidden`.
