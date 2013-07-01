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
    "identity_id": 982871737,
    "name": "Jason Fried",
    "email_address": "jason@37signals.com",
    "admin": true,
    "avatar_url": "https://asset0.37img.com/global/4113d0a133a32931be8934e70b2ea21efeff72c1/avatar.96.gif",
    "created_at": "2012-03-22T16:56:48-05:00",
    "updated_at": "2012-03-22T16:56:48-05:00",
    "url": "https://basecamp.com/999999999/api/v1/people/149087659-jason-fried.json"
  },
  {
    "id": 1071630348,
    "identity_id": 827377171,
    "name": "Jeremy Kemper",
    "email_address": "jeremy@37signals.com",
    "admin": true,
    "avatar_url": "https://asset0.37img.com/global/e68cafa694e8f22203eb36f13dccfefa9ac0acb2/avatar.96.gif",
    "created_at": "2012-03-22T16:56:48-05:00",
    "updated_at": "2012-03-22T16:56:48-05:00",
    "url": "https://basecamp.com/999999999/api/v1/people/1071630348-jeremy-kemper.json"
  }
]
```

Get person
----------

* `GET /people/1.json` will return the specified person.
* `GET /people/me.json` will return the current person.

```json
{
  "id": 149087659,
  "identity_id": 982871737,
  "name": "Jason Fried",
  "email_address": "jason@37signals.com",
  "admin": true,
  "avatar_url": "https://asset0.37img.com/global/4113d0a133a32931be8934e70b2ea21efeff72c1/avatar.96.gif?r=3",
  "created_at": "2012-03-22T16:56:51-05:00",
  "updated_at": "2012-03-23T13:55:43-05:00",
  "events": {
    "count": 19,
    "updated_at": "2012-03-23T13:55:43-05:00",
    "url": "https://basecamp.com/999999999/api/v1/people/149087659-jason-fried/events.json"
  },
  "assigned_todos": {
    "count": 80,
    "updated_at": "2013-06-26T16:22:05.000-04:00",
    "url": "https://basecamp.com/999999999/api/v1/people/149087659-jason-fried/assigned_todos.json"
  }
}
```


Create person
-------------

New people can be invited directly to projects via the [accesses API](https://github.com/37signals/bcx-api/blob/master/sections/accesses.md).


Delete person
------------

* `DELETE /people/1.json` will delete the person specified and return `204 No Content` if that was successful. If the user does not have access to delete the person, you'll see `403 Forbidden`.
