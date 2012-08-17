Projects
========

> Operations keeps the lights on, strategy provides a light at the end of the tunnel, 
> but project management is the train engine that moves the organization forward - Joy Gumz


Get projects
------------

* `GET /projects.json` will return all active projects.
* `GET /projects/archived.json` will return all archived projects.

```json
[
  {
    "id": 605816632,
    "name": "BCX",
    "description": "The Next Generation",
    "updated_at": "2012-03-23T13:55:43-05:00",
    "url": "https://basecamp.com/999999999/api/v1/projects/605816632-bcx.json",
    "archived": false
    "starred": true
  },
  {
    "id": 684146117,
    "name": "Nothing here!",
    "description": null,
    "updated_at": "2012-03-22T16:56:51-05:00",
    "url": "https://basecamp.com/999999999/api/v1/projects/684146117-nothing-here.json",
    "archived": false
    "starred": false
  }
]
```


Get project
-----------

* `GET /projects/1.json` will return the specified project.

```json
{
  "id": 605816632,
  "name": "BCX",
  "description": "The Next Generation",
  "archived": false,
  "created_at": "2012-03-22T16:56:51-05:00",
  "updated_at": "2012-03-23T13:55:43-05:00",
  "starred": true,
  "creator": {
    "id": 149087659,
    "name": "Jason Fried"
  },
  "accesses": {
    "count": 5,
    "updated_at": "2012-03-23T13:55:43-05:00",
    "url": "https://basecamp.com/999999999/api/v1/projects/605816632-bcx/accesses.json"
  },
  "attachments": {
    "count": 0,
    "updated_at": null,
    "url": "https://basecamp.com/999999999/api/v1/projects/605816632-bcx/attachments.json"
  },
  "calendar_events": {
    "count": 3,
    "updated_at": "2012-03-22T17:35:50-05:00",
    "url": "https://basecamp.com/999999999/api/v1/projects/605816632-bcx/calendar_events.json"
  },
  "documents": {
    "count": 0,
    "updated_at": null,
    "url": "https://basecamp.com/999999999/api/v1/projects/605816632-bcx/documents.json"
  },
  "topics": {
    "count": 2,
    "updated_at": "2012-03-22T17:35:50-05:00",
    "url": "https://basecamp.com/999999999/api/v1/projects/605816632-bcx/topics.json"
  },
  "todolists": {
    "remaining_count": 4,
    "completed_count": 0,
    "updated_at": "2012-03-23T12:59:23-05:00",
    "url": "https://basecamp.com/999999999/api/v1/projects/605816632-bcx/todolists.json"
  }
}
```


Create project
--------------

* `POST /projects.json` will create a new project from the parameters passed.

```json
{
  "name": "This is my new project!",
  "description": "It's going to run real smooth"
}
```

This will return `201 Created`, with the location of the new project in the `Location` header along with the current JSON representation of the project if the creation was a success. See the **Get project** endpoint for more info. If the user does not have access to create new projects or the account has reached the project limit, you'll see `403 Forbidden`.


Update project
---------------

* `PUT /projects/1.json` will update the project from the parameters passed.

```json
{
  "name": "This is a new name for the project!",
  "description": "And a new description..."
}
```

This will return `200 OK` if the update was a success along with the current JSON representation of the project. See the **Get project** endpoint for more info. If the user does not have access to update the project, you'll see `403 Forbidden`.


Archiving/activating a project
------------------------------

* `PUT /projects/1.json` with the following JSON payload will archive a project (pass false to activate it again).

```json
{
  "archived": true
}
```

This will return `200 OK` if the update was a success, along with the current JSON representation of the project. If the user does not have access to update the project, you'll see `403 Forbidden`.


Delete project
-------------

* `DELETE /projects/1.json` will delete the project specified and return `204 No Content` if that was successful. If the user does not have access to delete the project, you'll see `403 Forbidden`.
