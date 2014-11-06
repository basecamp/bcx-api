Events
======

All actions in Basecamp generate an event for the progress log. If you start a new todo list, there's an event. If you give someone access to a project, there's an event. If you add a comment. You get the drill.

If you're using this API for polling, please make sure that you're using the `since` parameter to limit the result set. Use the `created_at` time of the first item on the list for subsequent polls. If there's nothing new since that date, you'll get `[]` back.


Get events
-----------------

* `GET /projects/1/events.json?since=2012-03-24T11:00:00-06:00` will return all events in the specified project since 11am CST on March 24, 2012.
* `GET /people/1/events.json?since=2012-03-24T11:00:00-06:00` will return all the events created by the specified person since 11am CST on March 24, 2012.
* `GET /events.json?since=2012-03-24T11:00:00-06:00` will return all events in all projects and calendars since 11am CST on March 24, 2012.

Note that the `+` character must be url-escaped, while the `-` character can be used as-is. So, use `?since=2014-01-01T01:00:00%2B01:00` as opposed to `?since=2014-01-01T01:00:00+01:00` for east-of-GMT time zones. 

```json
[
  {
    "id": 1054456336,
    "created_at": "2012-03-24T11:00:50-05:00",
    "updated_at": "2012-03-24T11:00:50-05:00",
    "private": false,
    "action": "re-assigned a to-do to Funky ones.<span>:</span>",
    "target": "Design it",
    "eventable": {
      "id": 223304243,
      "type": "Todo",
      "url": "https://basecamp.com/999999999/api/v1/projects/605816632/todos/223304243.json",
      "app_url": "https://basecamp.com/999999999/projects/605816632/todos/223304243"
    },
    "creator": {
      "id": 149087659,
      "name": "Jason Fried",
      "avatar_url": "https://asset0.37img.com/global/4113d0a133a32931be8934e70b2ea21efeff72c1/avatar.96.gif?r=3",
      "fullsize_avatar_url": "https://asset0.37img.com/global/4113d0a133a32931be8934e70b2ea21efeff72c1/original.gif?r=3"
    },
    "summary": "re-assigned a to-do to Funky ones: Design it",
    "url": "https://basecamp.com/999999999/api/v1/projects/605816632/todos/223304243.json",
    "html_url": "https://basecamp.com/999999999/projects/605816632/todos/223304243"
  },
  {
    "id": 1054456334,
    "created_at": "2012-03-24T11:00:39-05:00",
    "updated_at": "2012-03-24T11:00:39-05:00",
    "private": false,
    "action": "created a to-do list<span>:</span>",
    "target": "Launch list",
    "eventable": {
      "id": 1056802576,
      "type": "Todolist",
      "url": "https://basecamp.com/999999999/api/v1/projects/605816632/todolists/1056802576.json",
      "app_url": "https://basecamp.com/999999999/projects/605816632/todolists/1056802576"
    },
    "creator": {
      "id": 149087659,
      "name": "Jason Fried",
      "avatar_url": "https://asset0.37img.com/global/4113d0a133a32931be8934e70b2ea21efeff72c1/avatar.96.gif?r=3",
      "fullsize_avatar_url": "https://asset0.37img.com/global/4113d0a133a32931be8934e70b2ea21efeff72c1/original.gif?r=3"
    },
    "summary": "created a to-do list<span>:</span> Launch list",
    "url": "https://basecamp.com/999999999/api/v1/projects/605816632/todolists/1056802576.json",
    "html_url": "https://basecamp.com/999999999/projects/605816632/todolists/1056802576"
  },
  {
    "id": 973672263,
    "created_at": "2012-03-24T09:53:35-05:00",
    "updated_at": "2012-03-24T09:53:35-05:00",
    "private": false,
    "action": "commented on",
    "target": "Prep the materials before the board meeting with Bezos",
    "eventable": {
      "id": 174886926,
      "type": "CalendarEvent",
      "url": "https://basecamp.com/999999999/api/v1/projects/605816632/calendar_events/174886926.json",
      "app_url": "https://basecamp.com/999999999/projects/605816632/calendar_events/174886926"
    },
    "creator": {
      "id": 149087659,
      "name": "Jason Fried",
      "avatar_url": "https://asset0.37img.com/global/4113d0a133a32931be8934e70b2ea21efeff72c1/avatar.96.gif?r=3",
      "fullsize_avatar_url": "https://asset0.37img.com/global/4113d0a133a32931be8934e70b2ea21efeff72c1/original.gif?r=3"
    },
    "attachments": [],
    "excerpt": "I&#39;ll be there!",
    "raw_excerpt": "I&#39;ll be there!",
    "summary": "commented on Prep the materials before the board meeting with Bezos",
    "url": "https://basecamp.com/999999999/api/v1/projects/605816632/calendar_events/174886926.json",
    "html_url": "https://basecamp.com/999999999/projects/605816632/calendar_events/174886926"
  }
]
```

An event's summary contains a text description. To get the latest structured data, fetch the eventable.

If an event's `created_at` and `updated_at` fields differ, it means that the eventable was updated within the 15 minute correction window we allow for people to fix small mistakes.

Buckets are only provided for events that are not accessed via a project. For example, events returned from `GET /events.json` will include their buckets,
but those returned from `GET /projects/1/events.json` will not.

Creators are only provided for events that are not accessed via a person. For example, events returned from `GET /events.json` will include their creators,
but those returned from `GET /people/1/events.json` will not.

### Pagination

We will return 50 events per page. If the result set has 50 entries, it's your
responsibility to check the next page to see if there are any more events --
you do this by adding `&page=2` to the query, then `&page=3` and so on.
