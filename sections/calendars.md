Calendars
=========

Get calendars
-------------

* `GET /calendars.json` will return all calendars sorted alphabetically.

```json
[
  {
    "id": 336154974,
    "name": "Board Meetings",
    "updated_at": "2012-03-27T13:19:29-05:00",
    "url": "https://basecamp.com/999999999/api/v1/calendars/336154974-board-meetings.json"
  },
  {
    "id": 237581901,
    "name": "General",
    "updated_at": "2012-03-27T13:19:29-05:00",
    "url": "https://basecamp.com/999999999/api/v1/calendars/237581901-general.json"
  }
]
```


Get calendar
------------

* `GET /calendars/1.json` will return the specified calendar.

```json
{
  "id": 567469885,
  "name": "Vacation",
  "created_at": "2012-03-28T13:14:30-05:00",
  "updated_at": "2012-03-28T13:26:07-05:00",
  "creator": {
    "id": 149087659,
    "name": "Jason Fried"
  },
  "accesses": {
    "count": 3,
    "updated_at": "2012-03-28T13:14:31-05:00",
    "url": "https://basecamp.com/999999999/api/v1/calendars/567469885-vacation/accesses.json"
  },
  "calendar_events": {
    "count": 1,
    "updated_at": "2012-03-28T13:26:07-05:00",
    "urls": {
      "upcoming": "https://basecamp.com/999999999/api/v1/calendars/567469885-vacation/calendar_events.json",
      "past": "https://basecamp.com/999999999/api/v1/calendars/567469885-vacation/calendar_events/past.json"
    }
  }
}
```


Create calendar
---------------

* `POST /calendars.json` will create a new calendar from the parameters passed.

```json
{
  "name": "This is my new calendar!"
}
```

This will return `201 Created`, with the location of the new calendar in the `Location` header along with a representation of the calendar in JSON in the response body if the creation was a success (See the **Get calendar** endpoint).


Update calendar
---------------

* `PUT /calendars/1.json` will update the calendar from the parameters passed.

```json
{
  "name": "This is a new name for the calendar!"
}
```

This will return `200 OK` if the update was a success, along with a represenation of the calendar in JSON (See the **Get calendar** endpoint). If the user does not have access to update the calendar, you'll see `403 Forbidden`.


Delete calendar
---------------

* `DELETE /calendars/1.json` will delete the calendar specified and return `204 No Content` if that was successful. If the user does not have access to delete the calendar, you'll see `403 Forbidden`.
