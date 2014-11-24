Attachments
===========

Uploading files to Basecamp is a two-step process:

1. Create the attachment and receive a token verifying that the upload was successful.
2. Associate the attachment with a message, todo, upload, or comment. See the following endpoints for attaching:

   * [Create messages](https://github.com/basecamp/bcx-api/blob/master/sections/messages.md)
   * [Create todos](https://github.com/basecamp/bcx-api/blob/master/sections/todos.md)
   * [Create uploads](https://github.com/basecamp/bcx-api/blob/master/sections/uploads.md)
   * [Create comments](https://github.com/basecamp/bcx-api/blob/master/sections/comments.md)


Create attachment
-----------------

* `POST /attachments.json` uploads a file. The request body should be the file's binary data. The `Content-Type` and `Content-Length` headers should be set accordingly.

When an upload is successful, you'll get a `200 OK` response, with a token that you use to attach the file to something.

```json
{
  "token": "4f71ea23-134660425d1818169ecfdbaa43cfc07f4e33ef4c"
}
```

Here's an example using `curl`:

```
curl --data-binary @logo.png \
       -u user:pass \
       -H 'Content-Type: image/png' \
       -H 'User-Agent: Rapp (david@basecamp.com)' \
       https://basecamp.com/999999999/api/v1/attachments.json
```

**Note:** If a file is big, uploading can take a long time! Make sure to account for this in your implementation.


Get attachment
--------------

* `GET /projects/1/attachments/1.json` will return the specified attachment with its file metadata, URLs, and associated attachable (a message, todo, upload, or comment).

```json
{
  "id": 999008202,
  "key": "40b8a84cb1a30dbe04457dc99e094b6299deea41",
  "name": "bearwave.gif",
  "byte_size": 508254,
  "content_type": "image/gif",
  "created_at": "2012-03-27T22:48:49-04:00",
  "updated_at": "2012-03-27T22:48:49-04:00",
  "url": "https://asset1.basecamp.com/1111/api/v1/projects/2222/attachments/3333/40b8a84cb1a30dbe04457dc99e094b6299deea41/original/bearwave.gif",
  "app_url": "https://asset1.basecamp.com/1111/projects/2222/attachments/3333/40b8a84cb1a30dbe04457dc99e094b6299deea41/original/bearwave.gif",
  "thumbnail_url": "https://asset1.basecamp.com/1111/projects/2222/attachments/3333/40b8a84cb1a30dbe04457dc99e094b6299deea41/thumbnail.gif",
  "private": false,
  "trashed": false,
  "tags": ["favorite gifs"],
  "creator": {
    "id": 73,
    "name": "Nick Quaranto",
    "avatar_url": "https://asset0.37img.com/global/4113d0a133a32931be8934e70b2ea21efeff72c1/avatar.96.gif?r=3",
    "fullsize_avatar_url": "https://asset0.37img.com/global/4113d0a133a32931be8934e70b2ea21efeff72c1/original.gif?r=3"
  },
  "attachable": {
    "id": 70219655,
    "type": "Upload",
    "url": "https://basecamp.com/1111/api/v1/projects/2222/uploads/70219655.json",
    "app_url": "https://basecamp.com/1111/projects/2222/uploads/70219655"
  }
}
```


Get attachments
---------------

* `GET /projects/1/attachments.json` returns attachments in the specified project, each with its file metadata, URLs, and associated attachable (a message, todo, upload, or comment).
* `GET /attachments.json` returns attachments in all projects.

```json
[
  {
    "id": 999008202,
    "key": "40b8a84cb1a30dbe04457dc99e094b6299deea41",
    "name": "bearwave.gif",
    "byte_size": 508254,
    "content_type": "image/gif",
    "created_at": "2012-03-27T22:48:49-04:00",
    "updated_at": "2012-03-27T22:48:49-04:00",
    "url": "https://asset1.basecamp.com/1111/api/v1/projects/2222/attachments/3333/40b8a84cb1a30dbe04457dc99e094b6299deea41/original/bearwave.gif",
    "app_url": "https://asset1.basecamp.com/1111/projects/2222/attachments/3333/40b8a84cb1a30dbe04457dc99e094b6299deea41/original/bearwave.gif",
    "thumbnail_url": "https://asset1.basecamp.com/1111/projects/2222/attachments/3333/40b8a84cb1a30dbe04457dc99e094b6299deea41/thumbnail.gif",
    "private": false,
    "trashed": false,
    "tags": ["favorite gifs"],
    "creator": {
      "id": 73,
      "name": "Nick Quaranto",
      "avatar_url": "https://asset0.37img.com/global/4113d0a133a32931be8934e70b2ea21efeff72c1/avatar.96.gif?r=3",
      "fullsize_avatar_url": "https://asset0.37img.com/global/4113d0a133a32931be8934e70b2ea21efeff72c1/original.gif?r=3"
    },
    "attachable": {
      "id": 70219655,
      "type": "Upload",
      "url": "https://basecamp.com/1111/api/v1/projects/2222/uploads/70219655.json",
      "app_url": "https://basecamp.com/1111/projects/2222/uploads/70219655"
    }
  }
  {
    "id": 999008203,
    "key": "773c74212f81f5c7d66917fb7236d5aece36c56a",
    "name": "report.pdf",
    "byte_size": 508254,
    "content_type": "application/pdf",
    "created_at": "2012-03-27T22:48:49-04:00",
    "updated_at": "2012-03-27T22:48:49-04:00",
    "url": "https://asset1.basecamp.com/1111/api/v1/projects/2222/attachments/4444/773c74212f81f5c7d66917fb7236d5aece36c56a/original/report.pdf",
    "app_url": "https://asset1.basecamp.com/1111/projects/2222/attachments/4444/773c74212f81f5c7d66917fb7236d5aece36c56a/original/report.pdf",
    "thumbnail_url": "https://asset1.basecamp.com/1111/projects/2222/attachments/4444/773c74212f81f5c7d66917fb7236d5aece36c56a/thumbnail.png",
    "private": false,
    "trashed": false,
    "tags": ["reports"],
    "creator": {
      "id": 73,
      "name": "Nick Quaranto",
      "avatar_url": "https://asset0.37img.com/global/4113d0a133a32931be8934e70b2ea21efeff72c1/avatar.96.gif?r=3",
      "fullsize_avatar_url": "https://asset0.37img.com/global/4113d0a133a32931be8934e70b2ea21efeff72c1/original.gif?r=3"
    },
    "attachable": {
      "id": 12092382,
      "type": "Message",
      "url": "https://basecamp.com/1111/api/v1/projects/2222/messages/12092382.json",
      "app_url": "https://basecamp.com/1111/projects/2222/messages/12092382"
    }
  }
]
```

Linked attachments like [Google Docs](https://basecamp.com/help/guides/projects/google-docs) don't have a `url` attribute and include additional attributes about the source:

```json
{
  "id": 999008204,
  "name": "Business ponderings",
  "byte_size": 0,
  "content_type": "application/vnd.google-apps.document",
  "linked_source": "google",
  "linked_type": "document",
  "link_url": "https://docs.google.com/document/d/1fNihMDicThD....",
  "created_at": "2012-03-28T22:48:49-04:00",
  "updated_at": "2012-03-28T22:48:49-04:00",
  "private": false,
  "trashed": false,
  "tags": ["writing"],
  "creator": {
    "id": 73,
    "name": "Nick Quaranto",
    "avatar_url": "https://asset0.37img.com/global/4113d0a133a32931be8934e70b2ea21efeff72c1/avatar.96.gif?r=3",
    "fullsize_avatar_url": "https://asset0.37img.com/global/4113d0a133a32931be8934e70b2ea21efeff72c1/original.gif?r=3"
  },
  "attachable": {
    "id": 12092383,
    "type": "Message",
    "url": "https://basecamp.com/1111/api/v1/projects/2222/messages/12092383.json",
    "app_url": "https://basecamp.com/1111/projects/2222/messages/12092383"
  }
}
```

If you need more information about what an attachment is attached to, you can
make another request to its `attachable`'s `url` value.

### Pagination

We will return 50 attachments per page. If the result set has 50 attachments,
it's your responsibility to check the next page to see if there are any more
attachments -- you do this by adding `&page=2` to the query, then `&page=3`, and so on.

### Sorting

It's also possible to change the order attachments are returned in with the `sort`
parameter. Attachments can be sorted by name, size, or age using the parameter
values:

* `az` and `za` for name
* `biggest` and `smallest` for size
* `newest` and `oldest` for age

The default sort is `newest`.

Sorting can be combined with pagination. To get the second page of attachments
sorted by oldest first, request `/attachments.json?page=2&sort=oldest`.


Rename attachment
-----------------

* `PUT /projects/1/attachments/1.json` will rename the specified attachment.

```json
{"name": "TPS report.pdf"}
```

This will return `200 OK` if the update was a success, with the current JSON
representation of the attachment in the response body. If the user does not
have permission to update the attachment, you'll receive `403 Forbidden`.

Linked attachments, such as [Google Docs](https://basecamp.com/help/guides/projects/google-docs),
can't be renamed. Their names are automatically synced from their sources when
they are viewed. If you attempt to rename a linked attachment, you'll receive
an error with a `400 Bad Request` response status.


Delete attachment
-----------------

* `DELETE /projects/1/attachments/1.json` will delete the attachment specified and return `204 No Content` if that was successful. If the user does not have access to delete the attachment, you'll see `403 Forbidden`.

If an attachment on an upload with no comments is deleted, the upload will be deleted as well. If an attachment on an upload with comments is deleted, the upload will remain.


Private attachments
-------------------

Attachments inherit the privacy of their containers. For example, an attachment
on a private message is private. Making the message visible to clients will
make all of its attachments visible to clients.
