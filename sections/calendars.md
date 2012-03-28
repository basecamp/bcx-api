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
    "url": "http://bcx.dev/735644780/api/v1/calendars/336154974-board-meetings.json"
  },
  {
    "id": 237581901,
    "name": "General",
    "updated_at": "2012-03-27T13:19:29-05:00",
    "url": "http://bcx.dev/735644780/api/v1/calendars/237581901-general.json"
  }
]
```


Get calendar
------------

* `GET /calendar/1.json` will return the specified calendar.

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
    "url": "http://bcx.dev/735644780/api/v1/calendars/567469885-vacation/accesses.json"
  },
  "calendar_events": {
    "count": 1,
    "updated_at": "2012-03-28T13:26:07-05:00",
    "urls": {
      "upcoming": "http://bcx.dev/735644780/api/v1/calendars/567469885-vacation/calendar_events.json",
      "past": "http://bcx.dev/735644780/api/v1/calendars/567469885-vacation/calendar_events/past.json"
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

This will return `200 OK`, with the location of the new calendar in the `Location` header, if the creation was a success.


Update calendar
---------------

* `PUT /calendars/1.json` will update the calendar from the parameters passed.

```json
{
  "name": "This is a new name for the calendar!"
}
```

This will return `200 OK` if the update was a success. If the user does not have access to update the calendar, you'll see `403 Forbidden`.


Delete calendar
-------------

* `DELETE /calendars/1.json` will delete the calendar specified and return `200 OK` if that was successful. If the user does not have access to delete the calendar, you'll see `403 Forbidden`.