Documents
=========

All documents are automatically version-tracked. The API only exposes the most recent version of a document, though. Also, in the web UI we provide lock tracking to make sure people don't overwrite each other's work. There's no such automatic protection via the API. You're responsible yourself for managing this. Of course, everything is versioned so there won't be any lost data.

Get documents
-------------

* `GET /projects/1/documents.json` shows documents in one project.
* `GET /documents.json` shows documents in all projects.

```json
[
  {
    "id": 963979453,
    "title": "Manifesto",
    "created_at": "2012-03-27T13:19:29-05:00",
    "updated_at": "2012-03-27T13:39:33-05:00",
    "url": "https://basecamp.com/999999999/api/v1/projects/605816632/documents/963979453.json",
    "app_url": "https://basecamp.com/999999999/projects/605816632/documents/963979453",
    "private": false,
    "trashed": false,
    "bucket": {
      "type": "Project",
      "id": 605816632,
      "name": "BCX",
      "color": "3185c5",
      "url": "https://basecamp.com/999999999/api/v1/projects/605816632.json",
      "app_url": "https://basecamp.com/999999999/projects/605816632"
    }
  },
  {
    "id": 243535881,
    "title": "Really important notes",
    "created_at": "2012-03-27T13:19:19-05:00",
    "updated_at": "2012-03-27T13:39:12-05:00",
    "url": "https://basecamp.com/999999999/api/v1/projects/605816632/documents/243535881.json",
    "app_url": "https://basecamp.com/999999999/projects/605816632/documents/243535881",
    "private": false,
    "trashed": false,
    "bucket": {
      "type": "Project",
      "id": 605816632,
      "name": "BCX",
      "color": "3185c5",
      "url": "https://basecamp.com/999999999/api/v1/projects/605816632.json",
      "app_url": "https://basecamp.com/999999999/projects/605816632"
    }
  }
]
```

Buckets are only provided for documents that are not accessed via a project.
For example, documents returned from `GET /documents.json` will include their
buckets, but those returned from `GET /projects/1/documents.json` will not.

### Sorting

It's possible to change the order documents are returned in with the `sort`
parameter. Documents can be sorted by title or latest update time using the
parameter values:

* `az` and `za` for title
* `newest` and `oldest` for latest update time

The default sort is `newest`.


Get document
------------

* `GET /projects/1/documents/1.json` will return the specified document along with all comments.

```json
{
  "id": 963979453,
  "title": "Manifesto",
  "content": "Do this<br>Then that<br>Finally just so!",
  "created_at": "2012-03-27T13:19:29-05:00",
  "updated_at": "2012-03-27T13:53:24-05:00",
  "private": false,
  "trashed": false,
  "last_updater": {
    "id": 149087659,
    "name": "Jason Fried"
  },
  "comments": [
    {
      "content": "I think there should be more sass to it.",
      "created_at": "2012-03-27T13:53:24-05:00",
      "updated_at": "2012-03-27T13:53:24-05:00",
      "creator": {
        "id": 149087659,
        "name": "Jason Fried",
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


Create document
---------------

* `POST /projects/1/documents.json` will create a new document from the parameters passed.

```json
{
  "title": "Very important business notes",
  "content": "The TPS report is due on Monday morning!"
}
```

This will return `201 Created`, with the location of the new project in the `Location` header along with a JSON representation of the document in the response body, if the creation was a success. See the **Get document** endpoint for more info.


Update document
---------------

* `PUT /projects/1/documents/1.json` will update the message from the parameters passed.

```json
{
  "title": "Really, super duper important business notes",
  "content": "Now I want the report by SUNDAY!"
}
```

This will return `200 OK` if the update was a success, along with a JSON representation of the document in the response body. See the **Get document** endpoint for more info.


Delete document
--------------

* `DELETE /projects/1/documents/1.json` will delete the document specified and return `204 No Content` if that was successful. If the user does not have access to delete the document, you'll see `403 Forbidden`.


Private documents
-----------------

To hide a document from clients, set its `private` attribute to `true`.

```json
{
  "title": "Very important business notes",
  "content": "The TPS report is due on Monday morning!",
  "private": true
}
```

To reveal a document to clients, set its `private` attribute to `false`.

Comments on a document inherit its privacy. If a document is made public or private, so are all of its comments.
