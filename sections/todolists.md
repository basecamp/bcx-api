To-do lists
==========

Get to-do lists
-------------

* `GET /projects/1/todolists.json` shows active to-do lists for this project sorted by position.
* `GET /projects/1/todolists/completed.json` shows completed to-do lists for this project.
* `GET /projects/1/todolists/trashed.json` shows trashed to-do lists for this project.
* `GET /todolists.json` shows active to-do lists for all projects.
* `GET /todolists/completed.json` shows completed to-do lists for all projects.
* `GET /todolists/trashed.json` shows trashed to-do lists for all projects.

```json
[
  {
    "id": 968316918,
    "name": "Launch list",
    "description": "What we need for launch",
    "created_at": "2012-03-22T16:46:52-05:00",
    "updated_at": "2012-03-22T16:56:52-05:00",
    "url": "https://basecamp.com/999999999/api/v1/projects/605816632/todolists/968316918.json",
    "app_url": "https://basecamp.com/999999999/projects/605816632/todolists/968316918",
    "completed": false,
    "position": 1,
    "private": false,
    "trashed": false,
    "completed_count": 3,
    "remaining_count": 5,
    "creator": {
      "id": 127326141,
      "name": "David Heinemeier Hansson",
      "avatar_url": "https://asset0.37img.com/global/9d2148cb8ed8e2e8ecbc625dd1cbe7691896c7d9/avatar.96.gif?r=3",
      "fullsize_avatar_url": "https://asset0.37img.com/global/9d2148cb8ed8e2e8ecbc625dd1cbe7691896c7d9/original.gif?r=3"
    },
    "bucket": {
      "id": 605816632,
      "name": "BCX",
      "type": "Project",
      "url": "https://basecamp.com/999999999/api/v1/projects/605816632.json",
      "app_url": "https://basecamp.com/999999999/projects/605816632"
    }
  },
  {
    "id": 812358930,
    "name": "Version 2",
    "description": "What we will do next",
    "created_at": "2012-03-22T16:46:52-05:00",
    "updated_at": "2012-03-22T16:56:52-05:00",
    "url": "https://basecamp.com/999999999/api/v1/projects/605816632/todolists/812358930.json",
    "app_url": "https://basecamp.com/999999999/projects/605816632/todolists/812358930",
    "completed": false,
    "position": 2,
    "private": false,
    "trashed": false,
    "completed_count": 0,
    "remaining_count": 4,
    "creator": {
      "id": 127326141,
      "name": "David Heinemeier Hansson",
      "avatar_url": "https://asset0.37img.com/global/9d2148cb8ed8e2e8ecbc625dd1cbe7691896c7d9/avatar.96.gif?r=3",
      "fullsize_avatar_url": "https://asset0.37img.com/global/9d2148cb8ed8e2e8ecbc625dd1cbe7691896c7d9/original.gif?r=3"
    },
    "bucket": {
      "id": 605816632,
      "name": "BCX",
      "type": "Project",
      "url": "https://basecamp.com/999999999/api/v1/projects/605816632.json",
      "app_url": "https://basecamp.com/999999999/projects/605816632"
    }
  }
]
```

Buckets are only provided for to-do lists that are not accessed via a project. For example, to-do lists returned from `GET /todolists.json` will include their buckets,
but those returned from `GET /projects/1/todolists.json` will not.


Get to-do lists with assigned to-dos
---------------------------------

* `GET /people/1/assigned_todos.json` will return all the to-do lists with to-dos assigned to the specified person.
* `GET /people/1/assigned_todos.json?due_since=2014-07-10` will return all the to-do lists with to-dos assigned to the specified person due after the date specified.

```json
[
  {
    "id": 968316918,
    "name": "Launch list",
    "description": "What we need for launch!",
    "created_at": "2012-03-22T16:46:52-05:00",
    "updated_at": "2012-03-29T11:00:39-05:00",
    "url": "https://basecamp.com/999999999/api/v1/projects/605816632/todolists/968316918.json",
    "app_url": "https://basecamp.com/999999999/projects/605816632/todolists/968316918",
    "completed": false,
    "position": 1,
    "private": false,
    "trashed": false,
    "completed_count": 3,
    "remaining_count": 5,
    "creator": {
      "id": 127326141,
      "name": "David Heinemeier Hansson",
      "avatar_url": "https://asset0.37img.com/global/9d2148cb8ed8e2e8ecbc625dd1cbe7691896c7d9/avatar.96.gif?r=3",
      "fullsize_avatar_url": "https://asset0.37img.com/global/9d2148cb8ed8e2e8ecbc625dd1cbe7691896c7d9/original.gif?r=3"
    },
    "assigned_todos": [
      {
        "id": 223304243,
        "content": "Design it",
        "due_at": "2012-03-30",
        "comments_count": 0,
        "created_at": "2012-03-27T13:19:30-05:00",
        "updated_at": "2012-03-29T11:00:38-05:00",
        "url": "https://basecamp.com/999999999/api/v1/projects/605816632/todos/223304243.json",
        "app_url": "https://basecamp.com/999999999/projects/605816632/todos/223304243",
        "position": 1
      }
    ],
    "bucket": {
      "id": 605816632,
      "name": "BCX",
      "type": "Project",
      "url": "https://basecamp.com/999999999/api/v1/projects/605816632.json",
      "app_url": "https://basecamp.com/999999999/projects/605816632"
    }
  },
  {
    "id": 812358930,
    "name": "Version 2",
    "description": "What we will do next",
    "created_at": "2012-03-22T16:46:52-05:00",
    "updated_at": "2012-03-29T10:50:33-05:00",
    "url": "https://basecamp.com/999999999/api/v1/projects/605816632/todolists/812358930.json",
    "app_url": "https://basecamp.com/999999999/projects/605816632/todolists/812358930",
    "completed": false,
    "position": 2,
    "private": false,
    "trashed": false,
    "completed_count": 0,
    "remaining_count": 4,
    "creator": {
      "id": 127326141,
      "name": "David Heinemeier Hansson",
      "avatar_url": "https://asset0.37img.com/global/9d2148cb8ed8e2e8ecbc625dd1cbe7691896c7d9/avatar.96.gif?r=3",
      "fullsize_avatar_url": "https://asset0.37img.com/global/9d2148cb8ed8e2e8ecbc625dd1cbe7691896c7d9/original.gif?r=3"
    },
    "assigned_todos": [
      {
        "id": 270524416,
        "content": "Fix all the bugs",
        "due_at": null,
        "comments_count": 0,
        "created_at": "2012-03-27T13:19:30-05:00",
        "updated_at": "2012-03-29T10:50:33-05:00",
        "url": "https://basecamp.com/999999999/api/v1/projects/605816632/todos/270524416.json",
        "app_url": "https://basecamp.com/999999999/projects/605816632/todos/270524416",
        "position": 1
      }
    ],
    "bucket": {
      "id": 605816632,
      "name": "BCX",
      "type": "Project",
      "url": "https://basecamp.com/999999999/api/v1/projects/605816632.json",
      "app_url": "https://basecamp.com/999999999/projects/605816632"
    }
  }
]
```


Get to-do list
------------

* `GET /projects/1/todolists/1.json` will return the specified to-do list including the to-dos.
* `GET /projects/1/todolists/1.json?exclude_todos=true` will return the specified to-do list excluding the to-dos.
If your to-do lists have a 1000+ total to-dos we request you use the to-do list with the exclude_todos parameter and
retrieve to-dos from the [to-do endpoints](https://github.com/basecamp/bcx-api/blob/master/sections/todos.md#get-todos).

```json
{
  "id": 968316918,
  "name": "Launch list",
  "description": "What we need for launch!",
  "created_at": "2012-03-24T09:53:35-05:00",
  "updated_at": "2012-03-24T09:59:35-05:00",
  "completed": false,
  "position": 1,
  "private": false,
  "trashed": false,
  "completed_count": 3,
  "remaining_count": 5,
  "creator": {
    "id": 127326141,
    "name": "David Heinemeier Hansson",
    "avatar_url": "https://asset0.37img.com/global/9d2148cb8ed8e2e8ecbc625dd1cbe7691896c7d9/avatar.96.gif?r=3",
    "fullsize_avatar_url": "https://asset0.37img.com/global/9d2148cb8ed8e2e8ecbc625dd1cbe7691896c7d9/original.gif?r=3"
  },
  "todos": {
    "remaining": [
      {
        "id": 223304243,
        "content": "Design it",
        "due_at": "2012-03-24",
        "comments_count": 0,
        "created_at": "2012-03-24T09:53:35-05:00",
        "updated_at": "2012-03-24T09:55:52-05:00",
        "assignee": {
          "id": 149087659,
          "type": "Person",
          "name": "Jason Fried"
        },
        "position": 1,
        "url": "https://basecamp.com/999999999/api/v1/projects/605816632/todos/223304243.json",
        "app_url": "https://basecamp.com/999999999/projects/605816632/todos/223304243"
      },
      {
        "id": 411008527,
        "content": "Test it",
        "due_at": null,
        "comments_count": 0,
        "created_at": "2012-03-24T09:53:35-05:00",
        "updated_at": "2012-03-24T09:53:35-05:00",
        "assignee": {},
        "position": 2,
        "url": "https://basecamp.com/999999999/api/v1/projects/605816632/todos/411008527.json",
        "app_url": "https://basecamp.com/999999999/projects/605816632/todos/411008527"
      }
    ],
    "completed": [
      {
        "id": 1046098401,
        "content": "Think of it",
        "due_at": null,
        "comments_count": 0,
        "created_at": "2012-03-24T09:59:33-05:00",
        "updated_at": "2012-03-24T09:59:35-05:00",
        "completed_at": "2012-03-24T09:59:35-05:00",
        "url": "https://basecamp.com/999999999/api/v1/projects/605816632/todos/1046098401.json",
        "app_url": "https://basecamp.com/999999999/projects/605816632/todos/1046098401",
        "assignee": {},
        "position": 3,
        "completer": {
          "id": 149087659,
          "name": "Jason Fried"
        }
      }
    ],
    "trashed": [
      {
        "id": 1046098402,
        "content": "Ship it",
        "due_at": null,
        "comments_count": 0,
        "created_at": "2012-03-24T09:59:33-05:00",
        "updated_at": "2012-03-24T09:59:35-05:00",
        "completed_at": "2012-03-24T09:59:35-05:00",
        "url": "https://basecamp.com/999999999/api/v1/projects/605816632/todos/1046098402.json",
        "app_url": "https://basecamp.com/999999999/projects/605816632/todos/1046098402",
        "assignee": {},
        "position": 4,
        "completer": {
          "id": 149087659,
          "name": "Jason Fried"
        }
      }
    ]
  },
  "comments": [
    {
      "id": 1028592764,
      "content": "+1",
      "created_at": "2012-03-24T09:53:34-05:00",
      "updated_at": "2012-03-24T09:53:34-05:00",
      "creator": {
        "id": 127326141,
        "name": "David Heinemeier Hansson",
        "avatar_url": "https://asset0.37img.com/global/9d2148cb8ed8e2e8ecbc625dd1cbe7691896c7d9/avatar.96.gif?r=3",
        "fullsize_avatar_url": "https://asset0.37img.com/global/9d2148cb8ed8e2e8ecbc625dd1cbe7691896c7d9/original.gif?r=3"
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


Create to-do list
---------------

* `POST /projects/1/todolists.json` will create a new to-do list from the parameters passed.

```json
{
  "name": "My really important list of stuff to do",
  "description": "I'm serial guys, this stuff matters!"
}
```

This will return `201 Created`, with the URL of the new to-do list in the `Location` header along with the current JSON representation of the to-do list if the creation was a success. See the **Get to-do list** endpoint for more info.


Update to-do list
---------------

* `PUT /projects/1/todolists/1.json` will update the to-do list from the parameters passed.

```json
{
  "name": "Think of a new title?",
  "description": "And a new description!"
}
```

This will return `200 OK` if the creation was a success along with the current JSON representation of the to-do list in the response body. See the **Get to-do list** endpoint for more info. If the user does not have access to update the to-do list, you'll see `403 Forbidden`.

### Reordering to-do lists

Updating the `position` of a to-do list is also possible through this endpoint by passing an integer between `1` and `n`, where `n` is the number of to-do lists in this project.

```json
{
  "position": 2
}
```

*Note*: If the position is out of bounds, the to-do will be moved to the bottom.


Delete to-do list
--------------

* `DELETE /projects/1/todolists/1.json` will delete the to-do list specified and return `204 No Content` if that was successful. If the user does not have access to delete the to-do list, you'll see `403 Forbidden`.


Private to-do lists
-----------------

To hide a to-do list and its to-dos from clients, set its `private` attribute to `true`.

```json
{
  "name": "My really important list of stuff to do",
  "description": "I'm serial guys, this stuff matters!",
  "private": true
}
```

To reveal a to-do list and its to-dos to clients, set its `private` attribute to `false`.

Comments on a to-do list inherit its privacy. If a to-do list is made public or private, so are all of its comments.
