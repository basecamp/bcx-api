Messages
========

> What a lot we lost when we stopped writing letters. You can't reread a phone call. - Liz Carpenter


Get messages
------------

Messages are listed alongside all the other [topics](https://github.com/37signals/bcx-api/blob/master/sections/topics.md), so there is no individual index for them.


Get message
-----------

* `GET /projects/1/messages/1.json` will return the specified message.

```json
{
  "id": 936075699,
  "subject": "Welcome!",
  "created_at": "2012-03-22T16:56:51-05:00",
  "updated_at": "2012-03-22T16:56:51-05:00",
  "content": "This is a new message",
  "creator": {
    "id": 149087659,
    "name": "Jason Fried"
  },
  "comments": [
    {
      "id": 1028592764,
      "content": "Yeah, really, welcome!",
      "created_at": "2012-03-22T16:56:48-05:00",
      "updated_at": "2012-03-22T16:56:48-05:00"
      "creator": {
        "id": 149087659,
        "name": "Jason Fried"
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


Create message
--------------

* `POST /projects/1/messages.json` will create a new message from the parameters passed. The subscribers array is an optional list of people IDs that you want to notify about this comment (see [Get accesses](https://github.com/37signals/bcx-api/blob/master/sections/accesses.md) on how to get the people IDs for a given project).

```json
{
  "subject": "Hello everyone",
  "content": "This is going to be a GREAT Saturday!",
  "subscribers": [ 1, 5, 6]
}
```

This will return `201 Created`, with the location of the new project in the `Location` header along with the current JSON representation of the message  if the creation was a success. See the **Get message* endpoint for more info.

### Attaching files

Attaching files to a message requires both the token and the name of the attachment. The
token is returned from the [Create attachments](https://github.com/37signals/bcx-api/blob/master/sections/attachments.md)
endpoint, which you must hit first before creating an upload.

The `name` parameter *must* be a valid filename with an extension. Multiple
attachments are allowed.

```json
{
  "subject": "Totally done!",
  "content": "I finished the reports, check them out!",
  "attachments": [
    {
      "token": "4f73595a-39a6fd18317b1eeffb9c4734e95a179aa4b1b7c8",
      "name": "cover_page.pdf"
    },
    {
      "token": "4f73595f-78efbe63c77a4f5c752ce7d113d0361220f70b69",
      "name": "final_draft.pdf"
    }
  ]
}
```


Update message
--------------

* `PUT /projects/1/messages/1.json` will update the message from the parameters passed.

```json
{
  "subject": "This is a new subject for the message!",
  "content": "And new content..."
}
```

This will return `200 OK` if the update was a success, along with the current JSON representation of the message in the response body. If the user does not have access to update the message, you'll see `403 Forbidden`. See the **Get message** endpoint for more info.


Delete message
-------------

* `DELETE /projects/1/messages/1.json` will delete the message specified and return `204 No Content` if that was successful. If the user does not have access to delete the message, you'll see `403 Forbidden`.
