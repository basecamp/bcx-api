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
  ]
}
```


Create message
--------------

* `POST /projects/1/messages.json` will create a new message from the parameters passed.

```json
{
  "subject": "Hello everyone",
  "content": "This is going to be a GREAT Saturday!",
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

This will return `200 OK`, with the location of the new project in the `Location` header, if the creation was a success. See the [files API](https://github.com/37signals/bcx-api/blob/master/sections/files.md) for details on how to upload files to be attachments.


Update message
--------------

* `PUT /projects/1/messages/1.json` will update the message from the parameters passed.

```json
{
  "subject": "This is a new subject for the message!",
  "content": "And new content..."
}
```

This will return `200 OK` if the update was a success. If the user does not have access to update the message, you'll see `403 Forbidden`.


Delete message
-------------

* `DELETE /projects/1/messages/1.json` will delete the message specified and return `200 OK` if that was successful. If the user does not have access to delete the message, you'll see `403 Forbidden`.