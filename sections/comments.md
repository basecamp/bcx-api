Comments
========

> HATERS GONNA HATE


Get comments
------------

Comments are included on the [topics](https://github.com/37signals/bcx-api/blob/master/sections/topics.md) directly. So to see all comments for a message, you'd just GET that message and they're included.


Create comment
--------------

* `POST /projects/1/<section>/1/comments.json` will create a new comment from the parameters passed for the commentable described via <section>/<id> -- for example /projects/1/messages/1/comments.json or /projects/1/todos/1/comments.json.

```json
{
  "content": "Imma let you finish, but..."
}
```

This will return `200 OK`, with the location of the commentable where the comment appears in the `Location` header, if the creation was a success.
