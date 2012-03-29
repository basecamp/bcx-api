Todo lists
==========

> <Clever quote about todo lists>


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
    "url": "https://basecamp.com/999999999/api/v1/projects/605816632-bcx/todolists/968316918-launch-list.json"
  },
  {
    "id": 812358930,
    "name": "Version 2",
    "description": "What we will do next",
    "updated_at": "2012-03-22T16:56:52-05:00",
    "url": "https://basecamp.com/999999999/api/v1/projects/605816632-bcx/todolists/812358930-version-2.json"
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
    "assigned_todos": [
      {
        "id": 223304243,
        "content": "Design it",
        "due_at": "2012-03-30T09:00:00-05:00",
        "comments_count": 0,
        "created_at": "2012-03-27T13:19:30-05:00",
        "updated_at": "2012-03-29T11:00:38-05:00",
        "url": "http://bcx.dev/735644780/api/v1/projects/605816632-bcx/todos/223304243-design-it.json"
      }
    ]
  },
  {
    "id": 812358930,
    "name": "Version 2",
    "description": "What we will do next",
    "updated_at": "2012-03-29T10:50:33-05:00",
    "url": "http://bcx.dev/735644780/api/v1/projects/605816632-bcx/todolists/812358930-version-2.json",
    "assigned_todos": [
      {
        "id": 270524416,
        "content": "Fix all the bugs",
        "due_at": null,
        "comments_count": 0,
        "created_at": "2012-03-27T13:19:30-05:00",
        "updated_at": "2012-03-29T10:50:33-05:00",
        "url": "http://bcx.dev/735644780/api/v1/projects/605816632-bcx/todos/270524416-fix-all-the-bugs.json"
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
  "name": "Launch list",
  "description": "What we need for launch!",
  "created_at": "2012-03-24T09:53:35-05:00",
  "updated_at": "2012-03-24T09:59:35-05:00",
  "todos": {
    "remaining": [
      {
        "id": 223304243,
        "content": "Design it",
        "due_at": "2012-03-24T16:00:00-05:00",
        "comments_count": 0,
        "created_at": "2012-03-24T09:53:35-05:00",
        "updated_at": "2012-03-24T09:55:52-05:00",
        "assignee": {
          "id": 149087659,
          "type": "Person",
          "name": "Jason Fried"
        },
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
        "completer": {
          "id": 149087659,
          "name": "Jason Fried"
        }
      }
    ]
  }
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

This will return `200 OK`, with the URL of the new todolist in the `Location` header, if the creation was a success.


Update todolist
---------------

* `PUT /projects/1/todolists/1.json` will update the todolist from the parameters passed.

```json
{
  "name": "Think of a new title?",
  "description": "And a new description!"
}
```

This will return `200 OK` if the creation was a success. If the user does not have access to update the todolist, you'll see `403 Forbidden`.


Delete todolist
--------------

* `DELETE /projects/1/todolists/1.json` will delete the todolist specified and return `200 OK` if that was successful. If the user does not have access to delete the todolist, you'll see `403 Forbidden`.