Events
======

> <Clever quote about accesses>

All actions in Basecamp generate an event for the progress log. If you start a new todo list, there's an event. If you give someone access to a project, there's an event. If you add a comment. You get the drill.

If you're using this API for polling, please make sure that you're using the `since` parameter to limit the result set. Use the `created_at` time of the first item on the list for subsequent polls. If there's nothing new since that date, you'll get `[]` back.


Get global events
-----------------

* `GET /events.json?since=2012-03-24T11:00:00-06:00` will return all the events on the account since 11am CST March 24, 2012. We will return 50 events per page. If the result set has 50 entries, it's your responsibility to check the next page to see if there are any more events -- you do this by adding `&page=2` to the query, then `&page=3` and so on.

```json
[
  {
    "id": 1054456336,
    "created_at": "2012-03-24T11:00:50-05:00",
    "updated_at": "2012-03-24T11:00:50-05:00",
    "creator": {
      "id": 149087659,
      "name": "Jason Fried"
    },
    "bucket": {
      "id": 605816632,
      "name": "BCX",
      "type": "Project",
      "url": "https://basecamp.com/999999999/api/v1/projects/605816632-bcx.json"
    },
    "summary": "re-assigned a to-do to Funky ones: Design it",
    "url": "https://basecamp.com/999999999/api/v1/projects/605816632-bcx/todos/223304243-design-it.json"
  },
  {
    "id": 1054456334,
    "created_at": "2012-03-24T11:00:39-05:00",
    "updated_at": "2012-03-24T11:00:39-05:00",
    "creator": {
      "id": 149087659,
      "name": "Jason Fried"
    },
    "bucket": {
      "id": 605816632,
      "name": "BCX",
      "type": "Project",
      "url": "https://basecamp.com/999999999/api/v1/projects/605816632-bcx.json"
    },
    "summary": "created a to-do list: lists",
    "url": "https://basecamp.com/999999999/api/v1/projects/605816632-bcx/todolists/1056802576-lists.json"
  },
  {
    "id": 973672263,
    "created_at": "2012-03-24T09:53:35-05:00",
    "updated_at": "2012-03-24T09:53:35-05:00",
    "creator": {
      "id": 149087659,
      "name": "Jason Fried"
    },
    "bucket": {
      "id": 605816632,
      "name": "BCX",
      "type": "Project",
      "url": "https://basecamp.com/999999999/api/v1/projects/605816632-bcx.json"
    },
    "summary": "commented on Prep the materials before the board meeting with Bezos",
    "url": "https://basecamp.com/999999999/api/v1/projects/605816632-bcx/calendar_events/174886926-prep-the-materials.json"
  }
]
```

As you can see from the result set, the summary only contains a text version of what happened. You'll want to check the url of the eventable to get the latest structured data. Also note that if the `created_at` and `updated_at` fields are different, it means that the event was updated within the 15 minutes "correction window" we allow for people to fix spelling mistakes etc.

The bucket type can either be `Project` or `Calendar`.


Get project events
------------------

* `GET /projects/1/events.json?since=2012-03-24T11:00:00-06:00` will return all the events on the project like the global GET, except there won't be a bucket included. Similar use of the since term and the pagination.

```json
[
  {
    "id": 1054456336,
    "created_at": "2012-03-24T11:00:50-05:00",
    "updated_at": "2012-03-24T11:00:50-05:00",
    "creator": {
      "id": 149087659,
      "name": "Jason Fried"
    },
    "summary": "re-assigned a to-do to Funky ones: Design it",
    "url": "https://basecamp.com/999999999/api/v1/projects/605816632-bcx/todos/223304243-design-it.json"
  },
  {
    "id": 1054456335,
    "created_at": "2012-03-24T11:00:44-05:00",
    "updated_at": "2012-03-24T11:00:44-05:00",
    "creator": {
      "id": 149087659,
      "name": "Jason Fried"
    },
    "summary": "added a to-do: t",
    "url": "https://basecamp.com/999999999/api/v1/projects/605816632-bcx/todos/1046098402-t.json"
  }
]
```


Get person events
------------------

* `GET /people/1/events.json?since=2012-03-24T11:00:00-06:00` will return all the events by that person like the global GET, except there won't be creator parameter. Similar use of the since term and the pagination.

```json
[
  {
    "id": 1054456336,
    "created_at": "2012-03-24T11:00:50-05:00",
    "updated_at": "2012-03-24T11:00:50-05:00",
    "bucket": {
      "id": 605816632,
      "name": "BCX",
      "type": "Project",
      "url": "https://basecamp.com/999999999/api/v1/projects/605816632-bcx.json"
    },
    "summary": "re-assigned a to-do to Funky ones: Design it",
    "url": "https://basecamp.com/999999999/api/v1/projects/605816632-bcx/todos/223304243-design-it.json"
  },
  {
    "id": 1054456334,
    "created_at": "2012-03-24T11:00:39-05:00",
    "updated_at": "2012-03-24T11:00:39-05:00",
    "bucket": {
      "id": 605816632,
      "name": "BCX",
      "type": "Project",
      "url": "https://basecamp.com/999999999/api/v1/projects/605816632-bcx.json"
    },
    "summary": "created a to-do list: lists",
    "url": "https://basecamp.com/999999999/api/v1/projects/605816632-bcx/todolists/1056802576-lists.json"
  }
]
```