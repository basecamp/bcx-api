To-dos
=====

Get to-dos
---------

To get an index of all to-dos on a list, see [to-do lists](https://github.com/basecamp/bcx-api/blob/master/sections/todolists.md).

Per Project:

* `GET /projects/1/todos.json` shows a list of all to-dos for this project; completed and remaining.
* `GET /projects/1/todos/completed.json` shows a list of all completed to-dos for this project.
* `GET /projects/1/todos/remaining.json` shows a list of all remaining/active to-dos for this project.
* `GET /projects/1/todos.json?due_since=2014-07-10` will return all the to-dos due after the date specified.

Per To-do List:
* `GET /projects/1/todolists/1/todos.json` shows a list of all to-dos for this to-do list; completed and remaining.
* `GET /projects/1/todolists/1/todos/completed.json` shows a list of all completed to-dos for this to-do list.
* `GET /projects/1/todolists/1/todos/remaining.json` shows a list of all remaining to-dos for this to-do list.
* `GET /projects/1/todolists/1/todos/trashed.json` shows a list of all trashed to-dos for this to-do list.

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

Get to-do
--------

* `GET /projects/1/todos/1.json` will return the specified to-do.

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
  "comments": [
      {
        "attachments": [], 
        "content": "such a great comment!", 
        "created_at": "2015-08-05T09:54:18.000+01:00", 
        "creator": {
            "avatar_url": "http://cdn.37img.com/global/t4783t741837tb43bnct34872t87/avatar.gif?r=3", 
            "fullsize_avatar_url": "https://cdn.37img.com/global/4738075413805714038cb7451vb142708/original.gif?r=3", 
            "id": 7408325432, 
            "name": "Jason Fried"
        }, 
        "id": 314405456, 
        "private": false, 
        "trashed": false, 
        "updated_at": "2015-08-05T09:54:18.000+01:00"
      }, 
    ], 
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
  "attachments": [],
  "subscribers": [
    {
      "id": 149087659,
      "name": "Jason Fried"
    },
    {
      "id": 127326141,
      "name": "David Heinemeier Hansson"
    }
  ]
}
```

{
    "app_url": "https://basecamp.com/2896498/projects/10017469/todos/194528828", 
    "attachments": [], 
    "comments": [
        {
            "attachments": [], 
            "content": "unknown student", 
            "created_at": "2015-08-05T09:54:18.000+01:00", 
            "creator": {
                "avatar_url": "http://cdn.37img.com/global/40004903e1eb5bdea8566dde24971bc60010/avatar.gif?r=3", 
                "fullsize_avatar_url": "https://cdn.37img.com/global/40004903e1eb5bdea8566dde24971bc60010/original.gif?r=3", 
                "id": 11686828, 
                "name": "Jason Gwartz"
            }, 
            "id": 314405456, 
            "private": false, 
            "trashed": false, 
            "updated_at": "2015-08-05T09:54:18.000+01:00"
        }, 
        {
            "attachments": [], 
            "content": "unknown student2", 
            "created_at": "2015-08-05T09:56:52.000+01:00", 
            "creator": {
                "avatar_url": "http://cdn.37img.com/global/40004903e1eb5bdea8566dde24971bc60010/avatar.gif?r=3", 
                "fullsize_avatar_url": "https://cdn.37img.com/global/40004903e1eb5bdea8566dde24971bc60010/original.gif?r=3", 
                "id": 11686828, 
                "name": "Jason Gwartz"
            }, 
            "id": 314406143, 
            "private": false, 
            "trashed": false, 
            "updated_at": "2015-08-05T09:56:52.000+01:00"
        }
    ], 
    "comments_count": 2, 
    "completed": false, 
    "content": "MagSafe 1 adapter", 
    "created_at": "2015-08-03T09:51:12.000+01:00", 
    "creator": {
        "avatar_url": "http://cdn.37img.com/builtin/default_avatar_v1_1/avatar.gif?r=3", 
        "fullsize_avatar_url": "https://cdn.37img.com/builtin/default_avatar_v1_1/original.gif?r=3", 
        "id": 12031691, 
        "name": "BasecampHelper"
    }, 
    "due_at": "2015-08-06", 
    "due_on": "2015-08-06", 
    "id": 194528828, 
    "position": 1, 
    "private": false, 
    "subscribers": [
        {
            "id": 11686828, 
            "name": "Jason Gwartz"
        }
    ], 
    "todolist_id": 30550423, 
    "trashed": false, 
    "updated_at": "2015-08-05T09:56:52.000+01:00", 
    "url": "https://basecamp.com/2896498/api/v1/projects/10017469/todos/194528828.json"
}

Create to-do
-----------

* `POST /projects/1/todolists/1/todos.json` will add a new to-do to the specified to-do list from the parameters passed. The `due_at` parameter should be in ISO 8601 format (like "2012-03-27T16:00:00-05:00"). The assignee parameters need a `type` field with the `Person` specified. The `id` is then the id of the person who was assigned.

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

This will return `201 Created`, with the URL of the new to-do in the `Location` header along with the current JSON representation of the to-do if the creation was a success. See the **Get to-do** endpoint for more info. If the assignee type is unrecognized or the `due_at` is in a wrong format, you'll see a `400 Bad Request`.

### Attaching files

Attaching files to a to-do requires both the token and the name of the attachment. The
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


Update to-do
-----------

* `PUT /projects/1/todos/1.json` will update the to-do from the parameters passed. The `completed` field can be set to either `true` or `false` to check or uncheck the to-do.

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

This will return `200 OK` if the update was a success along with the current JSON representation of the to-do in the response body. See the **Get to-do** endpoint for more info. If the assignee type is unrecognized or the `due_at` is in a wrong format, you'll see a `400 Bad Request`.

Sending a payload with `assignee` set to `null` will un-assign the to-do, and setting `due_at` to `null` will remove the due date.

```json
{
  "due_at": null,
  "assignee": null
}
```

### Reordering to-dos

Updating the `position` of a to-do is also possible through this endpoint by passing an integer between `1` and `n`, where `n` is the number of to-dos in this list.

```json
{
  "position": 2
}
```

*Note*: If the position is out of bounds, the to-do will be moved to the bottom.


Delete to-do
----------

* `DELETE /projects/1/todos/1.json` will delete the to-do specified and return `204 No Content` if that was successful. If the user does not have access to delete the to-do, you'll see `403 Forbidden`.


Private to-dos
-------------

To-dos inherit the privacy of their to-do lists. A to-do on a private to-do list is private. If a to-do list is made private or public, so are all of its to-dos.

Comments on a to-do inherit the privacy of its to-do list. If a to-do list is made public or private, so are all comments on all of its to-dos.
