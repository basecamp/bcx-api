Todos
=====

Get todos
---------

To get an index of all todos on a list, see [todolists](https://github.com/basecamp/bcx-api/blob/master/sections/todolists.md).

Per Project:

* `GET /projects/1/todos.json` shows a list of all todos for this project; completed and remaining.
* `GET /projects/1/todos/completed.json` shows a list of all completed todos for this project.
* `GET /projects/1/todos/remaining.json` shows a list of all remaining/active todos for this project.
* `GET /projects/1/todos.json?due_since=2014-07-10` will return all the todos due after the date specified.

Per To-do List:
* `GET /projects/1/todolists/1/todos.json` shows a list of all todos for this todolist; completed and remaining.
* `GET /projects/1/todolists/1/todos/completed.json` shows a list of all completed todos for this todolist.
* `GET /projects/1/todolists/1/todos/remaining.json` shows a list of all remaining todos for this todolist.
* `GET /projects/1/todolists/1/todos/trashed.json` shows a list of all trashed todos for this todolist.

```json
[
  {
    "id": 1,
    "todolist_id": 1000,
    "position": 1,
    "content": "Test it",
    "due_at": null,
    "due_on": null,
    "created_at": "2012-03-24T09:53:35-05:00",
    "updated_at": "2012-03-24T10:56:33-05:00",
    "completed_at": false,
    "comments_count": 1,
    "private": false,
    "trashed": false,
    "creator": {
      "id": 127326141,
      "name": "David Heinemeier Hansson",
      "avatar_url": "https://asset0.37img.com/global/9d2148cb8ed8e2e8ecbc625dd1cbe7691896c7d9/avatar.96.gif?r=3",
      "fullsize_avatar_url": "https://asset0.37img.com/global/9d2148cb8ed8e2e8ecbc625dd1cbe7691896c7d9/original.gif?r=3"
    },
    "assignee": {
      "id": 149087659,
      "type": "Person",
      "name": "Jason Fried"
    },
    "completed": false,
    "url": "http://37s.bcx.dev/999999999/api/v1/projects/605816632/todos/1.json",
    "app_url": "http://37s.bcx.dev/999999999/projects/605816632/todos/1",
    "todolist": {
      "completed": false,
      "completed_count": 1,
      "created_at": "2012-03-24T09:53:35-05:00",
      "creator": {
        "id": 127326141,
        "name": "David Heinemeier Hansson",
        "avatar_url": "https://asset0.37img.com/global/9d2148cb8ed8e2e8ecbc625dd1cbe7691896c7d9/avatar.96.gif?r=3",
        "fullsize_avatar_url": "https://asset0.37img.com/global/9d2148cb8ed8e2e8ecbc625dd1cbe7691896c7d9/original.gif?r=3"
      },
      "description": "What we will do next",
      "id": 1000,
      "name": "Launch list",
      "position": 3,
      "private": false,
      "remaining_count": 2,
      "trashed": false,
      "created_at": "2012-03-24T09:53:35-05:00",
      "url": "http://37s.bcx.dev/735644780/api/v1/projects/605816632/todolists/1.json",
      "app_url": "https://basecamp.com/999999999/projects/605816632/todolists/1"
    }
  },
  {
    "id": 2,
    "todolist_id": 1000,
    "position": 2,
    "content": "Test it",
    "due_at": null,
    "due_on": null,
    "created_at": "2012-03-24T09:53:35-05:00",
    "updated_at": "2012-03-24T10:56:33-05:00",
    "completed_at": false,
    "comments_count": 0,
    "private": false,
    "trashed": false,
    "creator": {
      "id": 127326141,
      "name": "David Heinemeier Hansson",
      "avatar_url": "https://asset0.37img.com/global/9d2148cb8ed8e2e8ecbc625dd1cbe7691896c7d9/avatar.96.gif?r=3",
      "fullsize_avatar_url": "https://asset0.37img.com/global/9d2148cb8ed8e2e8ecbc625dd1cbe7691896c7d9/original.gif?r=3"
    },
    "assignee": {
      "id": 149087659,
      "type": "Person",
      "name": "Jason Fried"
    },
    "completed": false,
    "url": "http://37s.bcx.dev/999999999/api/v1/projects/605816632/todos/2.json",
    "app_url": "http://37s.bcx.dev/999999999/projects/605816632/todos/2",
    "todolist": {
      "completed": false,
      "completed_count": 1,
      "created_at": "2012-03-24T09:53:35-05:00",
      "creator": {
        "id": 127326141,
        "name": "David Heinemeier Hansson",
        "avatar_url": "https://asset0.37img.com/global/9d2148cb8ed8e2e8ecbc625dd1cbe7691896c7d9/avatar.96.gif?r=3",
        "fullsize_avatar_url": "https://asset0.37img.com/global/9d2148cb8ed8e2e8ecbc625dd1cbe7691896c7d9/original.gif?r=3"
      },
      "description": "What we will do next",
      "id": 1000,
      "name": "Launch list",
      "position": 3,
      "private": false,
      "remaining_count": 2,
      "trashed": false,
      "created_at": "2012-03-24T09:53:35-05:00",
      "url": "http://37s.bcx.dev/735644780/api/v1/projects/605816632/todolists/1.json",
      "app_url": "https://basecamp.com/999999999/projects/605816632/todolists/1"
    }
  }
]
```

Get todo
--------

* `GET /projects/1/todos/1.json` will return the specified todo.

```json
{
  "id": 1,
  "todolist_id": 1000,
  "position": 1,
  "content": "Test it",
  "due_at": null,
  "due_on": null,
  "created_at": "2012-03-24T09:53:35-05:00",
  "updated_at": "2012-03-24T10:56:33-05:00",
  "completed_at": false,
  "comments_count": 1,
  "private": false,
  "trashed": false,
  "creator": {
    "id": 127326141,
    "name": "David Heinemeier Hansson",
    "avatar_url": "https://asset0.37img.com/global/9d2148cb8ed8e2e8ecbc625dd1cbe7691896c7d9/avatar.96.gif?r=3",
    "fullsize_avatar_url": "https://asset0.37img.com/global/9d2148cb8ed8e2e8ecbc625dd1cbe7691896c7d9/original.gif?r=3"
  },
  "assignee": {
    "id": 149087659,
    "type": "Person",
    "name": "Jason Fried"
  },
  "completed": false,
  "url": "http://37s.bcx.dev/999999999/api/v1/projects/605816632/todos/1.json",
  "app_url": "http://37s.bcx.dev/999999999/projects/605816632/todos/1",
  "todolist": {
    "completed": false,
    "completed_count": 1,
    "created_at": "2012-03-24T09:53:35-05:00",
    "creator": {
      "id": 127326141,
      "name": "David Heinemeier Hansson",
      "avatar_url": "https://asset0.37img.com/global/9d2148cb8ed8e2e8ecbc625dd1cbe7691896c7d9/avatar.96.gif?r=3",
      "fullsize_avatar_url": "https://asset0.37img.com/global/9d2148cb8ed8e2e8ecbc625dd1cbe7691896c7d9/original.gif?r=3"
    },
    "description": "What we will do next",
    "id": 1000,
    "name": "Launch list",
    "position": 3,
    "private": false,
    "remaining_count": 2,
    "trashed": false,
    "created_at": "2012-03-24T09:53:35-05:00",
    "url": "http://37s.bcx.dev/735644780/api/v1/projects/605816632/todolists/1.json",
    "app_url": "https://basecamp.com/999999999/projects/605816632/todolists/1"
  }
}
```

Create todo
-----------

* `POST /projects/1/todolists/1/todos.json` will add a new todo to the specified todolist from the parameters passed. The `due_at` parameter should be in ISO 8601 format (like "2012-03-27T16:00:00-05:00"). The assignee parameters need a `type` field with the `Person` specified. The `id` is then the id of the person who was assigned.

```json
{
  "content": "This is my new thing!",
  "due_at": "2012-03-27",
  "assignee": {
    "id": 149087659,
    "type": "Person"
  }
}
```

This will return `201 Created`, with the URL of the new todo in the `Location` header along with the current JSON representation of the todo if the creation was a success. See the **Get todo** endpoint for more info. If the assignee type is unrecognized or the `due_at` is in a wrong format, you'll see a `400 Bad Request`.

### Attaching files

Attaching files to a todo requires both the token and the name of the attachment. The
token is returned from the [Create attachments](https://github.com/basecamp/bcx-api/blob/master/sections/attachments.md)
endpoint, which you must hit first before creating an upload.

The `name` parameter *must* be a valid filename with an extension. Multiple
attachments are allowed.

```json
{
  "content": "This is my new thing!",
  "due_at": "2012-03-27",
  "assignee": {
    "id": 149087659,
    "type": "Person"
  },
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


Update todo
-----------

* `PUT /projects/1/todos/1.json` will update the todo from the parameters passed. The `completed` field can be set to either `true` or `false` to check or uncheck the todo.

```json
{
  "content": "New content thing!",
  "due_at": "2012-03-27",
  "assignee": {
    "id": 149087659,
    "type": "Person"
  },
  "completed": true
}
```

This will return `200 OK` if the update was a success along with the current JSON representation of the todo in the response body. See the **Get todo** endpoint for more info. If the assignee type is unrecognized or the `due_at` is in a wrong format, you'll see a `400 Bad Request`.

Sending a payload with `assignee` set to `null` will un-assign the todo, and setting `due_at` to `null` will remove the due date.

```json
{
  "due_at": null,
  "assignee": null
}
```

### Reordering todos

Updating the `position` of a todo is also possible through this endpoint by passing an integer between `1` and `n`, where `n` is the number of todos in this list.

```json
{
  "position": 2
}
```

*Note*: If the position is out of bounds, the todo will be moved to the bottom.


Delete todo
----------

* `DELETE /projects/1/todos/1.json` will delete the todo specified and return `204 No Content` if that was successful. If the user does not have access to delete the todo, you'll see `403 Forbidden`.


Private todos
-------------

Todos inherit the privacy of their todolists. A todo on a private todolist is private. If a todolist is made private or public, so are all of its todos.

Comments on a todo inherit the privacy of its todolist. If a todolist is made public or private, so are all comments on all of its todos.
