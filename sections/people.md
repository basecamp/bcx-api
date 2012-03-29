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
    "updated_at": "2012-03-22T16:56:48-05:00",
    "url": "https://basecamp.com/999999999/api/v1/people/149087659-jason-fried.json"
  },
  {
    "id": 1071630348,
    "name": "Jeremy Kemper",
    "email_address": "jeremy@37signals.com",
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
  "name": "Jason Fried",
  "email_address": "jason@37signals.com",
  "created_at": "2012-03-22T16:56:51-05:00",
  "updated_at": "2012-03-23T13:55:43-05:00",
  "events": {
    "count": 19,
    "updated_at": "2012-03-23T13:55:43-05:00",
    "url": "https://basecamp.com/999999999/api/v1/people/149087659-jason-fried/events.json"
  }
}
```


Create person
-------------

New people can be invited directly to projects via the [accesses API](https://github.com/37signals/bcx-api/blob/master/sections/accesses.md).


Delete person
------------

* `DELETE /people/1.json` will delete the person specified and return `200 OK` if that was successful. If the user does not have access to delete the person, you'll see `403 Forbidden`.