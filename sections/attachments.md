Attachments
===========

Submitting files to Basecamp is a two step process:

1. Create the attachment, receive a token verifying the upload was successful ("Create attachment" endpoint)
2. Attach the file to a comment, message, or upload. See the following endpoints for attaching:
   * [Create uploads](https://github.com/37signals/bcx-api/blob/master/sections/uploads.md)
   * [Create comments](https://github.com/37signals/bcx-api/blob/master/sections/comments.md)
   * [Create messages](https://github.com/37signals/bcx-api/blob/master/sections/messages.md)

Create attachment
-----------------

* `POST /attachments.json` uploads a file. The request body should be the
binary data of the attachment. Make sure to set the `Content-Type` and
`Content-Length` headers.

Once the upload is successful, you'll get a `200 OK` response, and we'll give
you a token back that you'll need to save locally to attach the file.

```json
{
  "token": "4f71ea23-134660425d1818169ecfdbaa43cfc07f4e33ef4c"
}
```

With `curl`, here's an example:

```
curl --data-binary @logo.png \
       -u user:pass \
       -H 'Content-Type: image/png' \
       -H 'User-Agent: Rapp (david@37signals.com)' \
       https://basecamp.com/999999999/api/v1/attachments.json
```

*Note:* Uploading can take a while, if the file is big! Make sure to account for this in your implementation.


Get attachments
---------------

* `GET /projects/1/attachments.json` shows attachments for this
project with file metadata, urls, and associated attachables (Uploads, Messages,
or Comments) with a `200 OK` response.
* `GET /attachments.json` shows attachments for all projects.

If you need more information about what the attachment is attached to, you can
make another request to the `attachable`'s `url` parameter.

We will return 50 attachments per page. If the
result set has 50 attachments, it's your responsibility to check the next page
to see if there are any more attachments -- you do this by adding `&page=2` to the
query, then `&page=3` and so on.

```json
[
  {
    "key": "40b8a84cb1a30dbe04457dc99e094b6299deea41",
    "name": "bearwave.gif",
    "byte_size": 508254,
    "content_type": "image/gif",
    "created_at": "2012-03-27T22:48:49-04:00",
    "url": "https://asset1.basecamp.com/1111/api/v1/projects/2222/attachments/3333/40b8a84cb1a30dbe04457dc99e094b6299deea41/original/bearwave.gif",
    "creator": {
      "id": 73,
      "name": "Nick Quaranto",
      "avatar_url": "https://asset0.37img.com/global/4113d0a133a32931be8934e70b2ea21efeff72c1/avatar.96.gif?r=3"
    },
    "attachable": {
      "id": 70219655,
      "type": "Upload",
      "url": "https://basecamp.com/1111/api/v1/projects/2222/uploads/70219655.json"
    }
  }
  {
    "key": "773c74212f81f5c7d66917fb7236d5aece36c56a",
    "name": "report.pdf",
    "byte_size": 508254,
    "content_type": "application/pdf",
    "created_at": "2012-03-27T22:48:49-04:00",
    "url": "https://asset1.basecamp.com/1111/api/v1/projects/2222/attachments/4444/773c74212f81f5c7d66917fb7236d5aece36c56a/original/report.pdf",
    "creator": {
      "id": 73,
      "name": "Nick Quaranto",
      "avatar_url": "https://asset0.37img.com/global/4113d0a133a32931be8934e70b2ea21efeff72c1/avatar.96.gif?r=3"
    },
    "attachable": {
      "id": 12092382,
      "type": "Message",
      "url": "https://basecamp.com/1111/api/v1/projects/2222/messages/12092382.json"
    }
  }
]
```
