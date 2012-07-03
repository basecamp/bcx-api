Uploads
=======

Uploads show up as "Files" inside of Basecamp.


Create uploads
--------------

* `POST /projects/1/uploads.json` will create a new entry in the "Files" section on the given project, with the given attachment token.

This endpoint will return a `201 Created` if successful, with the URL to the new uplaod in the `Location` header along with the current JSON representation of the upload. See the **Get upload** for more info.

Attaching files requires both the token and the name of the attachment. The
token is returned from the [Create attachments](https://github.com/37signals/bcx-api/blob/master/sections/attachments.md)
endpoint, which you must hit first before creating an upload.

The `name` parameter *must* be a valid filename with an extension. Only one
attachment is allowed.

The subscribers array is an optional list of people IDs that you want to notify about this comment (see [Get accesses](https://github.com/37signals/bcx-api/blob/master/sections/accesses.md) on how to get the people IDs for a given project).

```json
{
  "content": "Here's the new logo!",
  "attachments": [
    {
      "token": "4f71ea23-134660425d1818169ecfdbaa43cfc07f4e33ef4c",
      "name": "new_logo.png"
    }
  ],
  "subscribers": [ 1, 5, 6]
}
```

*Note*: Uploads can only have one attachment, despite the json blob accepting plural `attachments`. This is for consistency across the other endpoints that accept attachments. Hit the endpoint multiple times if you need to create multiple uploads.


Get upload
----------

* `GET /projects/1/uploads/2.json` will show the content, comments, and attachments for this upload.

Each attachment blob includes the `url` parameter, which you can make a
`GET` request (with authentication) in order to directly download the attachment.

```json
{
  "id": 31709,
  "created_at": "2012-03-27T22:48:49-04:00",
  "updated_at": "2012-03-28T11:36:10-04:00",
  "content": "Hi there!",
  "attachments": [
    {
      "key": "40b8a84cb1a30dbe04457dc99e094b6299deea41",
      "name": "bearwave.gif",
      "byte_size": 508254,
      "content_type": "image/gif",
      "created_at": "2012-03-27T22:48:49-04:00",
      "url": "https://basecamp.com/1111/api/v1/projects/2222/attachments/3333/40b8a84cb1a30dbe04457dc99e094b6299deea41/original/bearwave.gif",
      "creator": {
        "id": 73,
        "name": "Nick Quaranto"
      }
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
        "id": 73,
        "name": "Nick Quaranto"
      }
    }
  ]
}
```
