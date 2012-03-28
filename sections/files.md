Files
=====

Uploading files to Basecamp is a two step process:

1. Create the attachment, receive a token verifying the upload was successful ("Create attachment" endpoint)
2. Attach the file to a comment, message, or upload ("Create (comment|message|upload)" endpoint)

Some notes on files:

* Files can only be attached to one "attachable".
* Check out the [comments API](https://github.com/37signals/bcx-api/blob/master/sections/comments.md) or [messages API](https://github.com/37signals/bcx-api/blob/master/sections/messages.md) to see how to attach files to those endpoints.


Create attachment
-----------------

* `POST /attachments.json` uploads a file. The request body should be the binary data of the attachment. Make sure to set the `Content-Type` and `Content-Length` headers.

Once the upload is successful, we'll give you a token back that you'll need to save locally to attach the file.

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


Create uploads
--------------

* `POST /projects/1/uploads.json` will create a new entry in the "Files" section on the given project, with the given attachment token.

Attaching files requires both the token, and the name of the attachment. This *must* be a valid filename with an extension.

```json
{
  "content": "Here's the new logo!",
  "attachments": [
    {
      "token": "4f71ea23-134660425d1818169ecfdbaa43cfc07f4e33ef4c",
      "name": "new_logo.png"
    }
  ]
}
```

*Note*: Uploads can only have one attachment, despite the json blob accepting plural `attachments`. This is for consistency across the other endpoints that accept attachments. Hit the endpoint multiple times if you need to create multiple uploads. Also, make sure that the `name` matches the name of the file, or else your attachment won't display properly.