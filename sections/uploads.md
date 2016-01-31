Uploads
=======

Uploads show up as "Files" inside of Basecamp.


Create uploads
--------------

* `POST /projects/1/uploads.json` will create a new entry in the "Files" section on the given project, with the given attachment token.

This endpoint will return a `201 Created` if successful, with the URL to the new upload in the `Location` header along with the current JSON representation of the upload. See the **Get upload** for more info.

Attaching files requires both the token and the name of the attachment. The
token is returned from the [Create attachments](https://github.com/basecamp/bcx-api/blob/master/sections/attachments.md)
endpoint, which you must hit first before creating an upload.

The `name` parameter *must* be a valid filename with an extension. Only one
attachment is allowed.

The subscribers array is an optional list of people IDs that you want to notify about this comment (see [Get accesses](https://github.com/basecamp/bcx-api/blob/master/sections/accesses.md) on how to get the people IDs for a given project).

```json
{
  "content": "Here's the new logo!",
  "attachments": [
    {
      "token": "4f71ea23-134660425d1818169ecfdbaa43cfc07f4e33ef4c",
      "name": "new_logo.png"
    }
  ],
  "subscribers": [1, 5, 6]
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
  "trashed": false,
  "attachments": [
    {
      "key": "40b8a84cb1a30dbe04457dc99e094b6299deea41",
      "name": "bearwave.gif",
      "byte_size": 508254,
      "content_type": "image/gif",
      "created_at": "2012-03-27T22:48:49-04:00",
      "url": "https://basecamp.com/1111/api/v1/projects/2222/attachments/3333/40b8a84cb1a30dbe04457dc99e094b6299deea41/original/bearwave.gif",
      "app_url": "https://basecamp.com/1111/projects/2222/attachments/3333/40b8a84cb1a30dbe04457dc99e094b6299deea41/original/bearwave.gif",
      "creator": {
        "id": 73,
        "name": "Nick Quaranto",
        "avatar_url": "https://asset0.37img.com/global/4113d0a133a32931be8934e70b2ea21efeff72c1/avatar.96.gif?r=3",
        "fullsize_avatar_url": "https://asset0.37img.com/global/4113d0a133a32931be8934e70b2ea21efeff72c1/original.gif?r=3"
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
        "name": "Nick Quaranto",
        "avatar_url": "https://asset0.37img.com/global/4113d0a133a32931be8934e70b2ea21efeff72c1/avatar.96.gif?r=3",
        "fullsize_avatar_url": "https://asset0.37img.com/global/4113d0a133a32931be8934e70b2ea21efeff72c1/original.gif?r=3"
      }
    }
  ],
  "subscribers": [
    {
      "id": 149087659,
      "name": "Jason Fried"
    },
    {
      "id": 1071630348,
      "name": "Jeremy Kemper"
    }
  ]
}
```

Delete upload
-------------

* `DELETE /projects/1/uploads/2.json` will trash the upload specified and return `204 No Content` if that was successful. If the user does not have access to delete the upload, you'll see `403 Forbidden`. If the upload was deleted accidently simply retrieve it from the trash with the "bring it back" link in the application. Uploads cannot be permanently deleted via the API.

Private uploads
---------------

To hide an upload from clients, set its `private` attribute to `true`.

```json
{
  "content": "Here's the new logo!",
  "attachments": [
    {
      "token": "4f71ea23-134660425d1818169ecfdbaa43cfc07f4e33ef4c",
      "name": "new_logo.png"
    }
  ],
  "subscribers": [1, 5, 6],
  "private": true
}
```

To reveal an upload to clients, set its `private` attribute to `false`.

Comments and attachments on an upload inherit its privacy. If an upload is made public or private, so are all of its comments and attachments.
