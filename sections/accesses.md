Accesses
========

Get accesses
------------

* `GET /projects/1/accesses.json` will return all the people with access to the project.
* `GET /calendars/1/accesses.json` will return all the people with access to the calendar.

We will return 50 people per page. If the response has 50 people, check the next page
for more people. Do this by adding `&page=2` to the query, then `&page=3` and so on.

```json
[
  {
    "id": 149087659,
    "identity_id": 982871737,
    "name": "Jason Fried",
    "email_address": "jason@basecamp.com",
    "admin": true,
    "is_client": false,
    "trashed": false,
    "avatar_url": "https://asset0.37img.com/global/4113d0a133a32931be8934e70b2ea21efeff72c1/avatar.96.gif",
    "fullsize_avatar_url": "https://asset0.37img.com/global/4113d0a133a32931be8934e70b2ea21efeff72c1/original.gif?r=3",
    "created_at": "2012-03-22T16:56:48-05:00",
    "updated_at": "2012-03-22T16:56:48-05:00",
    "url": "https://basecamp.com/999999999/api/v1/people/149087659-jason-fried.json",
    "app_url": "https://basecamp.com/999999999/people/149087659-jason-fried"
  },
  {
    "id": 1071630348,
    "identity_id": 827377171,
    "name": "Jeremy Kemper",
    "email_address": "jeremy@basecamp.com",
    "admin": true,
    "is_client": false,
    "trashed": false,
    "avatar_url": "https://asset0.37img.com/global/e68cafa694e8f22203eb36f13dccfefa9ac0acb2/avatar.96.gif",
    "fullsize_avatar_url": "https://asset0.37img.com/global/4113d0a133a32931be8934e70b2ea21efeff72c1/original.gif?r=3",
    "created_at": "2012-03-22T16:56:48-05:00",
    "updated_at": "2012-03-22T16:56:48-05:00",
    "url": "https://basecamp.com/999999999/api/v1/people/1071630348-jeremy-kemper.json",
    "app_url": "https://basecamp.com/999999999/people/1071630348-jeremy-kemper"
  }
]
```

Grant access
------------

* `POST /projects/1/accesses.json` will grant access to the project for the existing `ids` of people already on the account or new people via `email_addresses`. (Same goes for calendars with /calendars/ instead)

```json
{
  "ids": [ 5, 6, 10 ],
  "email_addresses": [ "someone@example.com", "someoneelse@example.com" ]
}
```

You can get the ids of existing people on the account from the [people API](https://github.com/basecamp/bcx-api/blob/master/sections/people.md).

This will return `204 No Content` if the access was granted successfully. If the authenticated user does not have access to this project, `404 Not Found` will be returned.


Revoke access
-------------

* `DELETE /projects/1/accesses/1.json` will revoke the access of the person who's id is mentioned in the URL.  (Same goes for calendars with /calendars/ instead)

This will return `204 No Content` if the revoke was a success. If the user does not have access to revoke access from the project, `403 Forbidden` will be returned. If the authenticated user does not have access to this project, `404 Not Found` will be returned.
