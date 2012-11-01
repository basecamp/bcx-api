Calendar events
===============

> <Clever quote about todo lists>

A calendar event is an entry on the calendar (not to be confused with "events", which track activity in Basecamp -- yes, they could have been named better!).

The `starts_at` and `ends_at` are either dates if the calendar event is an all day affair or times with timezones if they're not.


Get calendar events
-------------------

* `GET /projects/1/calendar_events.json` will return upcoming calendar events for the project.
* `GET /calendars/1/calendar_events.json` will return upcoming calendar events for the calendar.
* `GET /projects/1/calendar_events/past.json` will return past calendar events for the project.
* `GET /calendars/1/calendar_events/past.json` will return past calendar events for the calendar.

```json
[
  {
    "id": 883432030,
    "summary": "something coming up",
    "description": "",
    "created_at": "2012-03-28T11:50:00-05:00",
    "updated_at": "2012-03-28T12:24:59-05:00",
    "all_day": false,
    "starts_at": "2012-03-28T07:00:00-05:00",
    "ends_at": "2012-03-28T07:00:00-05:00",
    "creator": {
      "id": 149087659,
      "name": "Jason Fried",
      "avatar_url": "https://asset0.37img.com/global/4113d0a133a32931be8934e70b2ea21efeff72c1/avatar.96.gif?r=3"
    },
    "url": "https://basecamp.com/999999999/api/v1/projects/605816632-bcx/calendar_events/883432030-something-coming-up.json"
  },
  {
    "id": 883432031,
    "summary": "More stuff for later",
    "description": "Details will follow",
    "created_at": "2012-03-28T12:29:16-05:00",
    "updated_at": "2012-03-28T12:29:16-05:00",
    "all_day": true,
    "starts_at": "2012-03-28",
    "ends_at": "2012-03-28",
    "creator": {
      "id": 149087659,
      "name": "Jason Fried",
      "avatar_url": "https://asset0.37img.com/global/4113d0a133a32931be8934e70b2ea21efeff72c1/avatar.96.gif?r=3"
    },
    "url": "https://basecamp.com/999999999/api/v1/projects/605816632-bcx/calendar_events/883432031-more-stuff-for-later.json"
  }
]
```

Get calendar event
------------------

* `GET /projects/1/calendar_events/1.json` will return the specified calendar event. 
* `GET /calendars/1/calendar_events/1.json` will return the specified calendar event. 

```json
{
  "id": 883432030,
  "summary": "something coming up",
  "description": "",
  "created_at": "2012-03-28T11:50:00-05:00",
  "updated_at": "2012-03-28T12:24:59-05:00",
  "all_day": false,
  "starts_at": "2012-03-28T07:00:00-05:00",
  "ends_at": "2012-03-28T07:00:00-05:00",
  "creator": {
    "id": 149087659,
    "name": "Jason Fried",
    "avatar_url": "https://asset0.37img.com/global/4113d0a133a32931be8934e70b2ea21efeff72c1/avatar.96.gif?r=3"
  },
  "url": "https://basecamp.com/999999999/api/v1/projects/605816632-bcx/calendar_events/883432030-something-coming-up.json"
  "comments": [
    {
      "id": 1028592772,
      "content": "let's get it taken care of?",
      "created_at": "2012-03-28T12:24:59-05:00",
      "updated_at": "2012-03-28T12:24:59-05:00",
      "attachments": [],
      "creator": {
        "id": 149087659,
        "name": "Jason Fried",
        "avatar_url": "https://asset0.37img.com/global/4113d0a133a32931be8934e70b2ea21efeff72c1/avatar.96.gif?r=3"
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


Create calendar event
---------------------

* `POST /projects/1/calendar_events.json` will create a new calendar event for a project.
* `POST /calendars/1/calendar_events.json` will create a new calendar event for a calendar.

Examples:

```json
{
  "summary": "My single, all-day event",
  "description": "Details to follow",
  "all_day": true,
  "starts_at": "2012-03-28"
}
```

```json
{
  "summary": "My all-day event spanning two days",
  "description": "Details to follow",
  "all_day": true,
  "starts_at": "2012-03-28",
  "ends_at": "2012-03-30"
}
```

```json
{
  "summary": "My single event for a specific time",
  "description": "Details to follow",
  "starts_at": "2012-03-28T11:50:00-05:00"
}
```

This will return `201 Created`, with the URL of the new calendar_event in the `Location` header and a JSON representation of the event in the response body, if the creation was a success. If the dates are not in the proper format, you'll get a `400 Bad Request`.


Update calendar event
---------------------

* `PUT /projects/1/calendar_events/1.json` will update the specific calendar event on a project.
* `PUT /calendars/1/calendar_events/1.json` will update the specific calendar event on a calendar.

```json
{
  "summary": "My all-day event spanning two days",
  "description": "Details to follow",
  "all_day": true,
  "starts_at": "2012-03-28",
  "ends_at": "2012-03-30"
}
```

This will return `200 OK` if the creation was a success, with a JSON representation of the resource in the response body. If the dates are not in the proper format, you'll get a `400 Bad Request`.


Delete calendar event
---------------------

* `DELETE /projects/1/calendar_events/1.json` will delete the calendar event specified and return `204 No Content` if that was successful. (The same for /calendars/)
