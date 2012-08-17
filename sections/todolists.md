Todo lists
==========

Get todolists
-------------

* `GET /projects/1/todolists.json` will return all todolists with remaining todos on them sorted by position.
* `GET /projects/1/todolists/completed.json` will return all the completed todolists.

```json
[
  {
    "id": 968316918,
    "name": "Launch list",
    "description": "What we need for launch",
    "updated_at": "2012-03-22T16:56:52-05:00",
    "url": "https://basecamp.com/999999999/api/v1/projects/605816632-bcx/todolists/968316918-launch-list.json",
    "completed": false,
    "position": 1,
    "completed_count": 3,
    "remaining_count": 5,
    "creator": {
      "id": 127326141,
      "name": "David Heinemeier Hansson"
    },
  },
  {
    "id": 812358930,
    "name": "Version 2",
    "description": "What we will do next",
    "updated_at": "2012-03-22T16:56:52-05:00",
    "url": "https://basecamp.com/999999999/api/v1/projects/605816632-bcx/todolists/812358930-version-2.json",
    "completed": false,
    "position": 2,
    "completed_count": 0,
    "remaining_count": 4,
    "creator": {
      "id": 127326141,
      "name": "David Heinemeier Hansson"
    },
  }
]
```

Get todolists with assigned todos
---------------------------------

* `GET /people/1/assigned_todos.json` will return all the todolists with todos assigned to the specified person.

```json
[
  {
    "id": 968316918,
    "name": "Launch list",
    "description": "What we need for launch!",
    "updated_at": "2012-03-29T11:00:39-05:00",
    "url": "http://bcx.dev/735644780/api/v1/projects/605816632-bcx/todolists/968316918-launch-list.json",
    "completed": false,
    "position": 1,
    "completed_count": 3,
    "remaining_count": 5,
    "creator": {
      "id": 127326141,
      "name": "David Heinemeier Hansson"
    },
    "assigned_todos": [
      {
        "id": 223304243,
        "content": "Design it",
        "due_at": "2012-03-30",
        "comments_count": 0,
        "created_at": "2012-03-27T13:19:30-05:00",
        "updated_at": "2012-03-29T11:00:38-05:00",
        "url": "http://bcx.dev/735644780/api/v1/projects/605816632-bcx/todos/223304243-design-it.json",
        "position": 1
      }
    ]
  },
  {
    "id": 812358930,
    "name": "Version 2",
    "description": "What we will do next",
    "updated_at": "2012-03-29T10:50:33-05:00",
    "url": "http://bcx.dev/735644780/api/v1/projects/605816632-bcx/todolists/812358930-version-2.json",
    "completed": false,
    "position": 2,
    "completed_count": 0,
    "remaining_count": 4,
    "creator": {
      "id": 127326141,
      "name": "David Heinemeier Hansson"
    },
    "assigned_todos": [
      {
        "id": 270524416,
        "content": "Fix all the bugs",
        "due_at": null,
        "comments_count": 0,
        "created_at": "2012-03-27T13:19:30-05:00",
        "updated_at": "2012-03-29T10:50:33-05:00",
        "url": "http://bcx.dev/735644780/api/v1/projects/605816632-bcx/todos/270524416-fix-all-the-bugs.json",
        "position": 1
      }
    ]
  }
]
```


Get todolist
------------

* `GET /projects/1/todolists/1.json` will return the specified todolist including the todos.

```json
{
  "id": 968316918,
  "name": "Launch list",
  "description": "What we need for launch!",
  "created_at": "2012-03-24T09:53:35-05:00",
  "updated_at": "2012-03-24T09:59:35-05:00",
  "completed": false,
  "position": 1,
  "completed_count": 3,
  "remaining_count": 5,
  "creator": {
    "id": 127326141,
    "name": "David Heinemeier Hansson"
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
        "url": "https://basecamp.com/999999999/api/v1/projects/605816632-bcx/todos/223304243-design-it.json"
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
        "url": "https://basecamp.com/999999999/api/v1/projects/605816632-bcx/todos/411008527-test-it.json"
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
        "url": "https://basecamp.com/999999999/api/v1/projects/605816632-bcx/todos/1046098401-think-of-it.json",
        "assignee": {},
        "position": 3,
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
        "name": "David Heinemeier Hansson"
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


Create todolist
---------------

* `POST /projects/1/todolists.json` will create a new todolist from the parameters passed.

```json
{
  "name": "My really important list of stuff to do",
  "description": "I'm serial guys, this stuff matters!"
}
```

This will return `201 Created`, with the URL of the new todolist in the `Location` header along with the current JSON representation of the todolist if the creation was a success. See the **Get todolist** endpoint for more info.


Update todolist
---------------

* `PUT /projects/1/todolists/1.json` will update the todolist from the parameters passed.

```json
{
  "name": "Think of a new title?",
  "description": "And a new description!"
}
```

This will return `200 OK` if the creation was a success along with the current JSON representation of the todolist in the response body. See the **Get todolist** endpoint for more info. If the user does not have access to update the todolist, you'll see `403 Forbidden`.

### Reordering todolists

Updating the `position` of a todolist is also possible through this endpoint by passing an integer between `1` and `n`, where `n` is the number of todolists in this project.

```json
{
  "position": 2
}
```

*Note*: If the position is out of bounds, the todo will be moved to the bottom.

Delete todolist
--------------

* `DELETE /projects/1/todolists/1.json` will delete the todolist specified and return `204 No Content` if that was successful. If the user does not have access to delete the todolist, you'll see `403 Forbidden`.
