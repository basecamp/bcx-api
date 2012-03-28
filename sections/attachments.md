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
