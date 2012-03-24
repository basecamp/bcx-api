Messages
========

> What a lot we lost when we stopped writing letters. You can't reread a phone call. - Liz Carpenter


Get messages
------------

Messages are listed alongside all the other [topics](https://github.com/37signals/bcx-api/blob/master/sections/topics.md), so there is no individual index for them.

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
  "content": "This is going to be a GREAT Saturday!"
}
```

This will return `200 OK`, with the location of the new project in the `Location` header, if the creation was a success.


Update message
--------------

* `PUT /projects/1.json` will update the message from the parameters passed.

```json
{
  "subject": "This is a new subject for the message!",
  "content": "And new content..."
}
```

This will return `200 OK` if the update was a success. If the user does not have access to update the message, you'll see `403 Forbidden`.
