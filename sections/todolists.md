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
    "url": "https://basecamp.com/735644780/api/v1/projects/605816632-bcx/todolists/968316918-launch-list.json"
  },
  {
    "id": 812358930,
    "name": "Version 2",
    "description": "What we will do next",
    "updated_at": "2012-03-22T16:56:52-05:00",
    "url": "https://basecamp.com/735644780/api/v1/projects/605816632-bcx/todolists/812358930-version-2.json"
  }
]
```

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
        "comments_count": 0,
        "created_at": "2012-03-24T09:53:35-05:00",
        "updated_at": "2012-03-24T09:55:52-05:00",
        "url": "https://basecamp.com/735644780/api/v1/projects/605816632-bcx/todos/223304243-design-it.json",
        "assignee": {
          "id": 149087659,
          "name": "Jason Fried"
        }
      },
      {
        "id": 411008527,
        "content": "Test it",
        "comments_count": 0,
        "created_at": "2012-03-24T09:53:35-05:00",
        "updated_at": "2012-03-24T09:53:35-05:00",
        "url": "https://basecamp.com/735644780/api/v1/projects/605816632-bcx/todos/411008527-test-it.json",
        "assignee": {}
      }
    ],
    "completed": [
      {
        "id": 1046098401,
        "content": "Think of it",
        "comments_count": 0,
        "created_at": "2012-03-24T09:59:33-05:00",
        "updated_at": "2012-03-24T09:59:35-05:00",
        "url": "https://basecamp.com/735644780/api/v1/projects/605816632-bcx/todos/1046098401-think-of-it.json",
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

* `POST /projects/1/todolists/1.json` will update the todolist from the parameters passed.

```json
{
  "name": "Think of a new title?",
  "description": "And a new description!"
}
```

This will return `200 OK`, with the URL of the new todolist in the `Location` header, if the creation was a success. If the user does not have access to update the todolist, you'll see `403 Forbidden`.
