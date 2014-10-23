Calendar events
===============

Calendar events are entries on the calendar -- not to be confused with "events", which track all activity in Basecamp. A calendar event can belong to a project or to a standalone calendar.

If a calendar event is an all day affair, its `starts_at` and `ends_at` values will be dates. For a timed calendar event, the `starts_at` and `ends_at` values are times with timezones.


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
    "comments_count": 0,
    "private": false,
    "trashed": false,
    "creator": {
      "id": 149087659,
      "name": "Jason Fried",
      "avatar_url": "https://asset0.37img.com/global/4113d0a133a32931be8934e70b2ea21efeff72c1/avatar.96.gif?r=3",
      "fullsize_avatar_url": "https://asset0.37img.com/global/4113d0a133a32931be8934e70b2ea21efeff72c1/original.gif?r=3"
    },
    "url": "https://basecamp.com/999999999/api/v1/projects/605816632/calendar_events/883432030.json",
    "app_url": "https://basecamp.com/999999999/projects/605816632/calendar_events/883432030"
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
    "comments_count": 0,
    "private": false,
    "trashed": false,
    "creator": {
      "id": 149087659,
      "name": "Jason Fried",
      "avatar_url": "https://asset0.37img.com/global/4113d0a133a32931be8934e70b2ea21efeff72c1/avatar.96.gif?r=3",
      "fullsize_avatar_url": "https://asset0.37img.com/global/4113d0a133a32931be8934e70b2ea21efeff72c1/original.gif?r=3"
    },
    "url": "https://basecamp.com/999999999/api/v1/projects/605816632/calendar_events/883432031.json",
    "app_url": "https://basecamp.com/999999999/projects/605816632/calendar_events/883432031"
  },
  {
    "id": 1030049109,
    "summary": "Weekly meeting",
    "description": "To discuss business",
    "created_at": "2014-07-09T09:40:33.000-05:00",
    "updated_at": "2014-07-09T09:40:33.000-05:00",
    "all_day": true,
    "starts_at": "2014-07-10",
    "ends_at": "2014-07-10",
    "comments_count": 0,
    "private": false,
    "trashed": false,
    "creator": {
      "id": 149087659,
      "name": "Jason Fried",
      "avatar_url": "https://asset0.37img.com/global/4113d0a133a32931be8934e70b2ea21efeff72c1/avatar.96.gif?r=3",
      "fullsize_avatar_url": "https://asset0.37img.com/global/4113d0a133a32931be8934e70b2ea21efeff72c1/original.gif?r=3"
    },
    "recurring": {
      "frequency": "weekly",
      "count": null,
      "until": null,
      "excluding": [2, 3]
    },
    "url": "https://basecamp.com/999999999/api/v1/projects/605816632/calendar_events/1030049109.json",
    "app_url": "https://basecamp.com/999999999/projects/605816632/calendar_events/1030049109"
  }
]
```

* `GET /calendar_events.json?start_date=2014-07-10` will return six weeks of calendar events after the start date for the account, including recurrences.
* `GET /projects/1/calendar_events.json?start_date=2014-07-10` will return six weeks of calendar events after the start date for the project, including recurrences.
* `GET /calendars/1/calendar_events.json?start_date=2014-07-10` will return six weeks of calendar events after the start date for the calendar, including recurrences.

```json
[
  {
    "id": 1030049109,
    "summary": "Weekly meeting",
    "description": "To discuss business",
    "created_at": "2014-07-10T09:40:33.000-05:00",
    "updated_at": "2014-07-10T09:40:33.000-05:00",
    "all_day": true,
    "starts_at": "2014-07-10",
    "ends_at": "2014-07-10",
    "comments_count": 0,
    "private": false,
    "trashed": false,
    "creator": {
      "id": 149087659,
      "name": "Jason Fried",
      "avatar_url": "https://asset0.37img.com/global/4113d0a133a32931be8934e70b2ea21efeff72c1/avatar.96.gif?r=3",
      "fullsize_avatar_url": "https://asset0.37img.com/global/4113d0a133a32931be8934e70b2ea21efeff72c1/original.gif?r=3"
    },
    "recurring": {
      "frequency": "weekly",
      "count": 5,
      "until": null,
      "excluding": [2, 3]
    },
    "url": "https://basecamp.com/999999999/api/v1/projects/605816632/calendar_events/1030049109.json",
    "app_url": "https://basecamp.com/999999999/projects/605816632/calendar_events/1030049109"
  },
  {
    "summary": "Weekly meeting",
    "description": "To discuss business",
    "all_day": true,
    "starts_at": "2014-07-10",
    "ends_at": "2014-07-10",
    "private": false,
    "trashed": false,
    "creator": {
      "id": 149087659,
      "name": "Jason Fried",
      "avatar_url": "https://asset0.37img.com/global/4113d0a133a32931be8934e70b2ea21efeff72c1/avatar.96.gif?r=3",
      "fullsize_avatar_url": "https://asset0.37img.com/global/4113d0a133a32931be8934e70b2ea21efeff72c1/original.gif?r=3"
    },
    "recurrence": {
      "number": 1,
      "master": {
        "id": 1030049109,
        "url": "https://basecamp.com/999999999/api/v1/projects/605816632/calendar_events/1030049109.json",
        "app_url": "https://basecamp.com/999999999/projects/605816632/calendar_events/1030049109"
      }
    }
  },
  {
    "summary": "Weekly meeting",
    "description": "To discuss business",
    "all_day": true,
    "starts_at": "2014-07-10",
    "ends_at": "2014-07-10",
    "comments_count": 0,
    "private": false,
    "trashed": false,
    "creator": {
      "id": 149087659,
      "name": "Jason Fried",
      "avatar_url": "https://asset0.37img.com/global/4113d0a133a32931be8934e70b2ea21efeff72c1/avatar.96.gif?r=3",
      "fullsize_avatar_url": "https://asset0.37img.com/global/4113d0a133a32931be8934e70b2ea21efeff72c1/original.gif?r=3"
    },
    "recurrence": {
      "number": 4,
      "master": {
        "id": 1030049109,
        "url": "https://basecamp.com/999999999/api/v1/projects/605816632/calendar_events/1030049109.json",
        "app_url": "https://basecamp.com/999999999/projects/605816632/calendar_events/1030049109"
      }
    }
  }
]
```

See [Recurring calendar events](#recurring-calendar-events) for more information.

Endpoints that include recurrences are paginated within the specified window and return 50 calendar events per page. It is your responsibility to check if the next page contains more calendar events. You do this by specifying a page parameter -- `/calendar_events.json?start_date=2014-07-10&page=2`, `/calendar_events.json?start_date=2014-07-10&page=3`, and so on.


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
  "private": false,
  "trashed": false,
  "creator": {
    "id": 149087659,
    "name": "Jason Fried",
    "avatar_url": "https://asset0.37img.com/global/4113d0a133a32931be8934e70b2ea21efeff72c1/avatar.96.gif?r=3",
    "fullsize_avatar_url": "https://asset0.37img.com/global/4113d0a133a32931be8934e70b2ea21efeff72c1/original.gif?r=3"
  },
  "url": "https://basecamp.com/999999999/api/v1/projects/605816632/calendar_events/883432030.json",
  "app_url": "https://basecamp.com/999999999/projects/605816632/calendar_events/883432030",
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
        "fullsize_avatar_url": "https://asset0.37img.com/global/4113d0a133a32931be8934e70b2ea21efeff72c1/original.gif?r=3"
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

```json
{
  "summary": "My timed event with a reminder",
  "description": "For an email reminder, set remind_at",
  "starts_at": "2012-03-28T11:50:00-05:00",
  "remind_at": "2012-03-28T11:20:00-05:00"
}
```

This will return `201 Created`, with the URL of the new calendar_event in the `Location` header and a JSON representation of the event in the response body, if the creation was a success. If the dates are not in the proper format, you'll get a `400 Bad Request`.

Basecamp will send a reminder email to all subscribers if `remind_at` is set. `remind_at` can't be more than three days before `starts_at` or any time after `starts_at`.


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


Recurring calendar events
-------------------------

For recurring events:

  * The `frequency` value may be `"daily"`, `"weekly"`, `"monthly"`, or `"yearly"`.
  * The `count` value describes how many times the event occurs.
  * The `until` value specifies the date of the last recurrence.
  * The `count` and `until` values are exclusive -- no event has both.
  * If `count` and `until` are both `null` for an event, it recurs infinitely.
  * The `excluding` value identifies which recurrences, indexed from 1, are skipped.

Here's a sample recurring event:

```json
{
  "id": 1030049109,
  "summary": "Weekly meeting",
  "description": "To discuss business",
  "created_at": "2014-07-10T09:40:33.000-05:00",
  "updated_at": "2014-07-10T09:40:33.000-05:00",
  "all_day": true,
  "starts_at": "2014-07-10",
  "ends_at": "2014-07-10",
  "private": false,
  "trashed": false,
  "creator": {
    "id": 149087659,
    "name": "Jason Fried",
    "avatar_url": "https://asset0.37img.com/global/4113d0a133a32931be8934e70b2ea21efeff72c1/avatar.96.gif?r=3",
    "fullsize_avatar_url": "https://asset0.37img.com/global/4113d0a133a32931be8934e70b2ea21efeff72c1/original.gif?r=3"
  },
  "recurring": {
    "frequency": "weekly",
    "count": 5,
    "until": null,
    "excluding": [2, 3]
  },
  "url": "https://basecamp.com/999999999/api/v1/projects/605816632/calendar_events/1030049109.json",
  "app_url": "https://basecamp.com/999999999/projects/605816632/calendar_events/1030049109"
}
```

For recurrences of an original event, the `number` value specifies which recurrence is represented. Recurrences are numbered starting from 1. The first recurrence of an event is numbered 1, the second is 2, and so forth. A recurrence includes details about its originating event, such as its ID and API URL. Recurrences do not have their own IDs or URLs.

Here's a sample recurrence:

```json
{
  "summary": "Weekly meeting",
  "description": "To discuss business",
  "all_day": true,
  "starts_at": "2014-07-10",
  "ends_at": "2014-07-10",
  "private": false,
  "trashed": false,
  "creator": {
    "id": 149087659,
    "name": "Jason Fried",
    "avatar_url": "https://asset0.37img.com/global/4113d0a133a32931be8934e70b2ea21efeff72c1/avatar.96.gif?r=3",
    "fullsize_avatar_url": "https://asset0.37img.com/global/4113d0a133a32931be8934e70b2ea21efeff72c1/original.gif?r=3"
  },
  "recurrence": {
    "number": 1,
    "master": {
      "id": 1030049109,
      "url": "https://basecamp.com/999999999/api/v1/projects/605816632/calendar_events/1030049109.json",
      "app_url": "https://basecamp.com/999999999/projects/605816632/calendar_events/1030049109"
    }
  }
}
```

Private calendar events
-----------------------

To hide a calendar event on a project from clients, set its `private` attribute to `true`.

```json
{
  "summary": "My timed event with a reminder",
  "description": "For an email reminder, set remind_at",
  "starts_at": "2012-03-28T11:50:00-05:00",
  "remind_at": "2012-03-28T11:20:00-05:00",
  "private": true
}
```

Calendars can't have clients, so you can't make events on calendars private. Attempting to do so will result in an error and a `422 Unprocessable Entity` response status.

To reveal a calendar event to clients, set its `private` attribute to false.

Comments on a calendar event inherit its privacy. If a calendar event is made public or private, so are all of its comments.
