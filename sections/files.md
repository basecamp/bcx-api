Files
=====

Uploading files to Basecamp is a two step process:

# Create the attachment, receive a token verifying the upload was successful ("Create attachment" endpoint)
# Attach the file to a comment, message, or upload ("Create (comment|message|upload)" endpoint)

Some notes on files:

* Files can only be attached to one "attachable".
* Check out the [comments API](https://github.com/37signals/bcx-api/blob/master/sections/comments.md) or [todos API](https://github.com/37signals/bcx-api/blob/master/sections/todos.md) to see how to attach files to those endpoints.

Create attachment
-----------------

* `POST /attachments.json` uploads a file. The request body should be the binary data of the attachment. Make sure to set the `CONTENT_TYPE` and `CONTENT_LENGTH` header.

Once the upload is successful, we'll give you a token back that you'll need to
save locally to attach the file.

```json
{
  "token": "4f71ea23-134660425d1818169ecfdbaa43cfc07f4e33ef4c"
}
```

With `curl`, here's an example of testing this endpoint with an example file `logo.png`:

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

* `POST /projects/1/uploads.json` will create a new entry in the "Files"
section on the given project, with the given attachment token.

Attaching files requires both the token, and the name of the attachment. This
*must* be a valid filename with an extension.

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

*Note*: Uploads can only have one attachment, despite the json blob accepting
plural `attachments`. This is for consistency across the other endpoints that
accept attachments. Hit the endpoint multiple times if you need to create
multiple uploads.
