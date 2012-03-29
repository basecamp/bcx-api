Documents
========

> <Clever quote about documents>

All documents are automatically version-tracked. The API only exposes the most recent version of a document, though. Also, in the web UI we provide lock tracking to make sure people don't overwrite each other's work. There's no such automatic protection via the API. You're responsible yourself for managing this. Of course, everything is versioned so there won't be any lost data.

Get documents
-------------

* `GET /projects/1/documents.json` will return all the documents on the project ordered alphabetically by `title`.

```json
[
  {
    "id": 963979453,
    "title": "Manifesto",
    "updated_at": "2012-03-27T13:39:33-05:00",
    "url": "https://basecamp.com/999999999/api/v1/projects/605816632-bcx/documents/963979453-manifesto.json"
  },
  {
    "id": 243535881,
    "title": "Really important notes",
    "updated_at": "2012-03-27T13:39:12-05:00",
    "url": "https://basecamp.com/999999999/api/v1/projects/605816632-bcx/documents/243535881-really-important.json"
  }
]
```


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
        "name": "Jason Fried"
      }
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

This will return `200 OK`, with the location of the new project in the `Location` header, if the creation was a success.


Update document
---------------

* `PUT /projects/1/documents/1.json` will update the message from the parameters passed.

```json
{
  "title": "Really, super duper important business notes",
  "content": "Now I want the report by SUNDAY!"
}
```

This will return `200 OK` if the update was a success.


Delete document
--------------

* `DELETE /projects/1/documents/1.json` will delete the document specified and return `200 OK` if that was successful. If the user does not have access to delete the document, you'll see `403 Forbidden`.