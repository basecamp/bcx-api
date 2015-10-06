Topics
========

Topics refer to anything in Basecamp that can have comments:

* Messages
* Documents
* Forwards
* Calendar events
* Uploads
* To-do lists
* To-dos

Topics will only appear for resources that have at least one comment, except for Messages, which always have topics.


Get topics
----------

* `GET /projects/1/topics.json` returns active topics in the specified project.
* `GET /projects/1/topics/archived.json` returns archived topics in the specified project.
* `GET /topics.json` returns active topics in all projects.
* `GET /topics/archived.json` returns archived topics in all projects.

```json
[
  {
    "id": 1028592764,
    "title": "Prep the materials before the board meeting with Bezos",
    "excerpt": "I'll be there!",
    "created_at": "2012-03-24T09:53:35-05:00",
    "updated_at": "2012-03-24T09:53:35-05:00",
    "attachments": 0,
    "private": false,
    "trashed": false,
    "last_updater": {
      "id": 149087659,
      "name": "Jason Fried"
    },
    "topicable": {
      "id": 174886926,
      "type": "CalendarEvent",
      "url": "https://basecamp.com/<accountid>/api/v1/projects/605816632/calendar_events/174886926.json",
      "app_url": "https://basecamp.com/<accountid>/projects/605816632/calendar_events/174886926"
    },
    "bucket": {
      "id": 605816632,
      "name": "BCX",
      "type": "Project",
      "url": "https://basecamp.com/<accountid>/api/v1/projects/605816632.json",
      "app_url": "https://basecamp.com/<accountid>/projects/605816632"
    }
  },
  {
    "id": 936075699,
    "title": "Welcome!",
    "excerpt": "Yeah, really, welcome!",
    "created_at": "2012-03-24T09:53:35-05:00",
    "updated_at": "2012-03-24T09:53:35-05:00",
    "attachments": 1,
    "private": false,
    "trashed": false,
    "last_updater": {
      "id": 149087659,
      "name": "Jason Fried"
    },
    "topicable": {
      "id": 936075699,
      "type": "Message",
      "url": "https://basecamp.com/<accountid>/api/v1/projects/605816632/messages/936075699.json",
      "app_url": "https://basecamp.com/<accountid>/projects/605816632/messages/936075699"
    },
    "bucket": {
      "id": 605816632,
      "name": "BCX",
      "type": "Project",
       "url": "https://basecamp.com/<accountid>/api/v1/projects/605816632.json",
      "app_url": "https://basecamp.com/<accountid>/projects/605816632"
    }
  }
]
```

For a topic:

* `title` is the original title of the topicable
* `excerpt` is from the latest comment on the topicable
* `last_updater` is the creator of the latest comment, or the creator of the
  topicable if it has no comments

Buckets are only provided for topics that are not accessed via a project. For
example, topics returned from `GET /topics.json` will include their buckets,
but those returned from `GET /projects/1/topics.json` will not.

### Pagination

We will return 50 topics per page. If the result set has 50 topics, it's your
responsibility to check the next page to see if there are any more topics --
you do this by adding `&page=2` to the query, then `&page=3` and so on.

### Sorting

It's possible to change the order topics are returned in with the `sort`
parameter. Topics can be sorted by their latest update times using the
parameter values `newest` and `oldest`. The default sort is `newest`.

Sorting can be combined with pagination. To get the second page of topics
sorted by oldest first, request `/topics.json?page=2&sort=oldest`.


Archive/activate a topic
------------------------

* `PUT /projects/1/topics/1/archive.json` will archive the specified topic.
* `PUT /projects/1/topics/1/activate.json` will activate (reopen) the specified topic.

No request body is necessary. In response, expect:

* `204 No Content` if archiving/activating is successful
* `403 Forbidden` if the topic's project is not active, or the authenticated user does not have permission
