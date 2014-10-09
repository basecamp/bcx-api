Topics
========

> <Clever topics quote>

Topics are anything in Basecamp that can have comments: Messages, Calendar Events, Uploads, Todos. Messages will appear in the topics index even before they have any comments, but any other topicable type will only appear if there's at least one comment posted.


Get topics
----------

* `GET /projects/1/topics.json` shows topics for this project.
* `GET /topics.json` shows topics for all projects.

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
      "url": "https://basecamp.com/999999999/api/v1/projects/605816632/calendar_events/174886926.json",
      "app_url": "https://basecamp.com/999999999/projects/605816632/calendar_events/174886926"
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
      "url": "https://basecamp.com/999999999/api/v1/projects/605816632/messages/936075699.json",
      "app_url": "https://basecamp.com/999999999/projects/605816632/messages/936075699"
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
