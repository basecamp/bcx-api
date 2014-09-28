Stars
=====

Starring a project has its own API because people who don’t have permission to change a project can still star it.

Note: Stars are included in project JSON as the `starred` attribute.


Star a project
--------------

* `POST /projects/123/star.json` stars the project.

No request body is required. Expect a `201 Created` response with an empty body.


Unstar a project
----------------

* `DELETE /projects/123/star.json` removes the star from the project.

Expect a `204 No Content` response.


List all stars
--------------

* `GET /stars.json` lists stars on active projects.

Expect a `200 OK` response with the JSON collection of starred project IDs, creation timestamps, and star URLs.

```json
[
  {
    "project_id": 605816632,
    "created_at": "2012-03-23T13:55:43-05:00",
    "url": "https://basecamp.com/999999999/api/v1/projects/605816632/star.json",
  },
  {
    "project_id": 684146117,
    "created_at": "2012-03-22T16:56:51-05:00",
    "url": "https://basecamp.com/999999999/api/v1/projects/684146117/star.json",
  }
]
```
