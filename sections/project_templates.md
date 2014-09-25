Project Templates
=================

Get project templates
---------------------

* `GET /project_templates.json` will return all project templates.

```json
[
  {
    "id": 605816632,
    "name": "Client Project",
    "description": "Let's get started!",
    "updated_at": "2012-03-23T13:55:43-05:00",
    "url": "https://basecamp.com/999999999/api/v1/projects/605816632-client-template.json",
    "template" :true,
    "archived": false,
    "starred": false,
    "trashed": false,
    "is_client_project": true,
    "color": "3185c5"
  },
  {
    "id": 684146117,
    "name": "Other Template",
    "description": null,
    "updated_at": "2012-03-22T16:56:51-05:00",
    "url": "https://basecamp.com/999999999/api/v1/projects/684146117-other-template.json",
    "template": true,
    "archived": false,
    "starred": false,
    "trashed": false,
    "is_client_project": false,
    "color": "3185c5"
  }
]
```

Get project template
--------------------

Getting a project template is the same as getting a project via the API.


* `GET /projects/1.json` will return the specified project template.

```json
{
  "id": 1,
  "name": "Client Project",
  "description": "Let's get started!",
  "template": true,
  "archived": false,
  "created_at": "2012-03-23T13:55:43-05:00",
  "updated_at": "2012-03-23T13:55:43-05:00",
  "starred": false,
  "trashed": false,
  "is_client_project": true,
  "color": "3185c5",
  "creator": {
    "id": 149087659,
    "name": "Jason Fried",
    "avatar_url": "https://asset0.37img.com/global/4113d0a133a32931be8934e70b2ea21efeff72c1/avatar.96.gif?r=3",
    "fullsize_avatar_url": "https://asset0.37img.com/global/4113d0a133a32931be8934e70b2ea21efeff72c1/original.gif?r=3"
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

Create project template
----------------------

* `POST /projects\_templates.json` will create a new project template from the parameters passed.

```json
{
  "name": "This is my new project template!",
  "description": "It's a real nice template!"
}
```

This will return `201 Created`, with the location of the new project template in the `Location` header along with the current JSON representation of the project template if the creation was a success. See the **Get project** endpoint for more info. If the user does not have access to create new project templates you'll see `403 Forbidden`.

Update project template
-----------------------

Updating a project template is the same as updating a project via the API.

* `PUT /projects/1.json` will update the project template  from the parameters passed.

```json
{
  "name": "This is a new name for the project template!",
  "description": "And a new description for my template"
}
```

This will return `200 OK` if the update was a success along with the current JSON representation of the project. See the **Get project** endpoint for more info. If the user does not have access to update the project template, you'll see `403 Forbidden`.

Delete project template
----------------------

Deleting a project template is the same as deleting a project via the API.

* `DELETE /projects/1.json` will delete the project template specified and return `204 No Content` if that was successful. If the user does not have access to delete the project template, you'll see `403 Forbidden`.
