People
======

> The major problems of our work are not so much technological as sociological in nature - T. DeMarco & T. Lister


Get people
----------

* `GET /people.json` will return all people on the account.

```json
[
  {
    "id": 149087659,
    "name": "Jason Fried",
    "email_address": "jason@37signals.com",
    "url": "https://basecamp.com/735644780/api/v1/people/149087659-jason-fried.json"
  },
  {
    "id": 1071630348,
    "name": "Jeremy Kemper",
    "email_address": "jeremy@37signals.com",
    "url": "https://basecamp.com/735644780/api/v1/people/1071630348-jeremy-kemper.json"
  }
]
```

* `GET /people/1.json` will return the specified person.

```json
{
  "id": 149087659,
  "name": "Jason Fried",
  "email_address": "jason@37signals.com",
  "created_at": "2012-03-22T16:56:51-05:00",
  "updated_at": "2012-03-23T13:55:43-05:00",
  "events": {
    "count": 19,
    "updated_at": "2012-03-23T13:55:43-05:00",
    "url": "http://bcx.dev/735644780/api/v1/people/149087659-jason-fried/events.json"
  },
  "assigned_todos": {
    "count": 0,
    "updated_at": null,
    "url": "http://bcx.dev/735644780/api/v1/people/149087659-jason-fried/assigned_todos.json"
  },
  "completed_todos": {
    "count": 0,
    "last_completed_at": null,
    "url": "http://bcx.dev/735644780/api/v1/people/149087659-jason-fried/completed_todos.json"
  },
  "attachments": {
    "count": 3,
    "updated_at": "2012-03-22T16:56:47-05:00",
    "url": "http://bcx.dev/735644780/api/v1/people/149087659-jason-fried/attachments.json"
  }
}
```


Create/update people
--------------------

This has not yet been exposed through the API.