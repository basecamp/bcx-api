Comments
========

> HATERS GONNA HATE


Get comments
------------

Comments are included on the [topics](https://github.com/37signals/bcx-api/blob/master/sections/topics.md) directly. So to see all comments for a message, you'd just GET that message and they're included and look like this:

```json
{
  "comments": [
    {
      "id": 1028592764,
      "content": "Yeah, really, welcome!",
      "created_at": "2012-03-22T16:56:48-05:00",
      "updated_at": "2012-03-22T16:56:48-05:00",
      "creator": {
        "id": 149087659,
        "name": "Jason Fried"
      }
    }
  ]
}
```


Create comment
--------------

* `POST /projects/1/<section>/1/comments.json` will create a new comment from the parameters passed for the commentable described via <section>/<id> -- for example /projects/1/messages/1/comments.json or /projects/1/todos/1/comments.json.

```json
{
  "content": "Imma let you finish, but...",
}
```

This will return `200 OK`, with the location of the commentable where the
comment appears in the `Location` header, if the creation was a success.

### Attaching files

Attaching files to a comment requires both the token and the name of the attachment. The
token is returned from the [Create attachments](https://github.com/37signals/bcx-api/blob/master/sections/attachments.md)
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

* `DELETE /projects/1/comments/1.json` will delete the comment specified and return `200 OK` if that was successful. If the user does not have access to delete the comment, you'll see `403 Forbidden`.
