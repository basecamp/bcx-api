Projects
========

> Operations keeps the lights on, strategy provides a light at the end of the tunnel,
> but project management is the train engine that moves the organization forward - Joy Gumz


Get projects
------------

* `GET /projects.json` will return all active projects.
* `GET /projects/drafts.json` will return all draft projects.
* `GET /projects/archived.json` will return all archived projects.

```json
[
  {
    "id": 605816632,
    "name": "BCX",
    "description": "The Next Generation",
    "updated_at": "2012-03-23T13:55:43-05:00",
    "url": "https://basecamp.com/999999999/api/v1/projects/605816632.json",
    "template": false,
    "archived": false,
    "starred": true,
    "trashed": false,
    "draft":false,
    "is_client_project": false,
    "color": "3185c5"
  },
  {
    "id": 684146117,
    "name": "Nothing here!",
    "description": null,
    "updated_at": "2012-03-22T16:56:51-05:00",
    "url": "https://basecamp.com/999999999/api/v1/projects/684146117.json",
    "template": false,
    "archived": false,
    "starred": false,
    "trashed": false,
    "draft":false,
    "is_client_project": true,
    "color": "3185c5"
  }
]
```


Get project
-----------

* `GET /projects/1.json` will return the specified project.

```json
{
  "id": 1,
  "name": "BCX",
  "description": "The Next Generation",
  "archived": false,
  "created_at": "2012-03-22T16:56:51-05:00",
  "updated_at": "2012-03-23T13:55:43-05:00",
  "template": false,
  "starred": true,
  "trashed": false,
  "draft":false,
  "is_client_project": false,
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
    "url": "https://basecamp.com/999999999/api/v1/projects/605816632/accesses.json"
  },
  "attachments": {
    "count": 0,
    "updated_at": null,
    "url": "https://basecamp.com/999999999/api/v1/projects/605816632/attachments.json"
  },
  "calendar_events": {
    "count": 3,
    "updated_at": "2012-03-22T17:35:50-05:00",
    "url": "https://basecamp.com/999999999/api/v1/projects/605816632/calendar_events.json"
  },
  "documents": {
    "count": 0,
    "updated_at": null,
    "url": "https://basecamp.com/999999999/api/v1/projects/605816632/documents.json"
  },
  "topics": {
    "count": 2,
    "updated_at": "2012-03-22T17:35:50-05:00",
    "url": "https://basecamp.com/999999999/api/v1/projects/605816632/topics.json"
  },
  "todolists": {
    "remaining_count": 4,
    "completed_count": 0,
    "updated_at": "2012-03-23T12:59:23-05:00",
    "url": "https://basecamp.com/999999999/api/v1/projects/605816632/todolists.json"
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

This will return `201 Created`, with the location of the new project in the `Location` header along with the current JSON representation of the project if the creation was a success. See the **Get project** endpoint for more info. If the user does not have access to create new projects you'll see `403 Forbidden`. If the account has reached the project limit you'll see a `507 Insufficient Storage`.

Create project from template
----------------------------

* `POST /project_templates/1/projects.json` will create a project from the template specified with the parameters passed. If a name and description are not passed the name and description from the template will be used instead. Projects created from templates will automatically be saved as draft projects. Before you start your project, you'll be able to make updates and changes. When you're ready for your project to go live you will need to publish your project. Until the project is published only the person who created the draft will be able to access it.

```json
{
  "name": "This is my new project!",
  "description": "I was created from a template!"
}
```

This will return `201 Created`, with the location of the new project in the `Location` header along with the current JSON representation of the project if the creation was a success. See the **Get project** endpoint for more info. If the user does not have access to create new projects you'll see `403 Forbidden`. If the account has reached the project limit you'll see a `507 Insufficient Storage`.


Publishing a project
--------------------

* `POST /projects/1/publish.json` will publish/activate a project created from a template (draft project). This will automatically send invitations to those you invited and make your project live.

This will return `200 OK` if the update was a success, along with the current JSON representation of the project. If the user does not have access to update the project, you'll see `403 Forbidden`.


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


Client projects
---------------

* When creating or updating a project, set its `is_client_project` attribute to `true` to make it a client project.

```json
{
  "is_client_project": true
}
```

Set a project's `is_client_project` attribute to `false` to prevent content from being newly marked as private. Doing this will not make existing private content visible to clients.

Content in a non-client project cannot be made private. Attempting to make content private in a non-client project will result in an error and a `422 Unprocessable Entity` response status.
