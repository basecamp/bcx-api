Tags
====

Tags are referred to as "file labels" in Basecamp.

In the API, tags are referenced by name. Tag names may contain characters that are not safe for URLs. When using tag names in API URLs, you **must** be careful to properly encode them.
Failing to do so may result in `404 Not Found` errors if you attempt to access a tag with an unsafe name. For example, to delete a tag named "logos/icons" from a project, you should issue a `DELETE` request to
`/projects/1/tags/logos%2Ficons.json`. More information on URL encoding is available [on Wikipedia](http://en.wikipedia.org/wiki/Percent-encoding).

Tag names must contain at least one non-whitespace character. Leading and trailing whitespace is stripped from all tags.


Add a tag to an attachment
--------------------------

* `POST /projects/1/attachments/1/tags.json` will add a tag to an attachment and return `204 No Content` if that was successful.

```json
{"name": "logos"}
```


Get attachments with a tag
--------------------------

* `GET /projects/1/tags/logos/attachments.json` will return all attachments with the named tag that are visible to the current user.

* `GET /tags/logos/attachments.json` will return all attachments with the named tag in all projects and calendars that are visible to the current user.

Tag names are case-insensitive, so that two tags named "Logos" and "logos" are treated as equivalent. The same attachments will be returned by `GET /tags/logos/attachments.json` and `GET /tags/Logos/attachments.json`.


Remove a tag from an attachment
-------------------------------

* `DELETE /projects/1/attachments/1/tags/logos.json` will remove the named tag from the attachment and return `204 No Content` if that was successful.


Rename a tag
------------

* `PUT /projects/1/attachments/1/tags/logos.json` will update the named tag in the project and return `204 No Content` if that was successful.

* `PUT /tags/logos.json` will update the named tag in all projects and calendars visible to the current user and return `204 No Content` if that was successful.

```json
{"name": "logos and branding"}
```


Delete a tag
------------

* `DELETE /projects/1/tags/logos.json` will delete the named tag from the project, removing it from all attachments in the project, and return `204 No Content` if that was successful.

* `DELETE /tags/logos.json` will delete the named tag from all projects and calendars visible to the current user, removing it from all attachments, and return `204 No Content` if that was successful.
