Todos
=====

Get todos
---------

To get an index of all todos on a list, see [todolists](https://github.com/37signals/bcx-api/blob/master/sections/todolists.md).


Get todo
--------

* `GET /projects/1/todos/1.json` will return the specified todo.

```json
{
  "id": 1,
  "todolist_id": 1000,
  "position": 1,
  "content": "Design it",
  "completed": false,
  "due_at": "2012-03-27",
  "created_at": "2012-03-24T09:53:35-05:00",
  "updated_at": "2012-03-24T10:56:33-05:00",
  "comments_count": 1,
  "creator": {
    "id": 127326141,
    "name": "David Heinemeier Hansson",
    "avatar_url": "https://asset0.37img.com/global/9d2148cb8ed8e2e8ecbc625dd1cbe7691896c7d9/avatar.96.gif?r=3"
  },
  "assignee": {
    "id": 149087659,
    "type": "Person",
    "name": "Jason Fried"
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
        "avatar_url": "https://asset0.37img.com/global/9d2148cb8ed8e2e8ecbc625dd1cbe7691896c7d9/avatar.96.gif?r=3"
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
