The new Basecamp API
====================

The all-new Basecamp has an all-new API. It is not compatible with the [Basecamp Classic API](http://developer.37signals.com/basecamp/). All integrations will have to be updated to use the new API. The core ingredients are still the same, though. This is a REST-style API that uses JSON for serialization and OAuth 2 for authentication.


Making a request
----------------

All URLs start with `https://basecamp.com/999999999/api/v1/`. **SSL only**. The path is prefixed with the account id and the API version. If we change the API in backward-incompatible ways, we'll bump the version marker and maintain stable support for the old URLs.

To make a request for all the projects on your account, you'd append the projects index path to the base url to form something like https://basecamp.com/999999999/api/v1/projects.json. In curl, that looks like:

```shell
curl -u user:pass -H 'User-Agent: MyApp (yourname@example.com)' https://basecamp.com/999999999/api/v1/projects.json
```

To create something, it's the same deal except you also have to include the `Content-Type` header and the JSON data:

```shell
curl -u username:password \
  -H 'Content-Type: application/json' \
  -H 'User-Agent: MyApp (yourname@example.com)' \
  -d '{ "name": "My new project!" }' \
  https://basecamp.com/999999999/api/v1/projects.json
```

That's all!


Authentication
--------------

If you're making a private integration with Basecamp for your own purposes, you can use HTTP Basic authentication. This is secure since all requests in the new Basecamp use SSL.

If you're making a public integration with Basecamp for others to enjoy, you must use OAuth 2. This allows users to authorize your application to use Basecamp on their behalf without having to copy/paste API tokens or touch sensitive login info.

Read the [authentication guide](https://github.com/37signals/api/blob/master/sections/authentication.md) to get started.


Identify your app
-----------------

You must include a `User-Agent` header with the name of your application and a link to it or your email address so we can get in touch in case you're doing something wrong (so we may warn you before you're blacklisted) or something awesome (so we may congratulate you). Here's an example:

    User-Agent: Freshbooks (http://freshbooks.com)

If you don't supply this header, you will get a `400 Bad Request`.


No XML, just JSON
-----------------

We only support JSON for serialization of data. Our format is to have no root element and we use snake\_case to describe attribute keys. This means that you have to send `Content-Type: application/json; charset=utf-8` when you're POSTing or PUTing data into Basecamp. **All API URLs end in .json to indicate that they accept and return JSON.**

You'll receive a `415 Unsupported Media Type` response code if you attempt to use a different URL suffix or leave out the `Content-Type` header.

Use HTTP caching
----------------

You must make use of the HTTP freshness headers to lessen the load on our servers (and increase the speed of your application!). Most requests we return will include an `ETag` or `Last-Modified` header. When you first request a resource, store this value, and then submit them back to us on subsequent requests as `If-None-Match` and `If-Modified-Since`. If the resource hasn't changed, you'll see a `304 Not Modified` response, which saves you the time and bandwidth of sending something you already have.


Handling errors
---------------

If Basecamp is having trouble, you might see a 5xx error. `500` means that the app is entirely down, but you might also see `502 Bad Gateway`, `503 Service Unavailable`, or `504 Gateway Timeout`. It's your responsibility in all of these cases to retry your request later. 

We have another API for checking our system status at http://status.37signals.com/api.


Rate limiting
-------------

You can perform up to 500 requests per 10 second period from the same IP address for the same account. If you exceed this limit, you'll get a [429 Too Many Requests](http://tools.ietf.org/html/draft-nottingham-http-new-status-02#section-4) response for subsequent requests. Check the `Retry-After` header to see how many seconds to wait before retrying the request.



API ready for use
-----------------

* [Projects](https://github.com/37signals/bcx-api/blob/master/sections/projects.md)
* [People](https://github.com/37signals/bcx-api/blob/master/sections/people.md)
* [Accesses](https://github.com/37signals/bcx-api/blob/master/sections/accesses.md)
* [Events](https://github.com/37signals/bcx-api/blob/master/sections/events.md)
* [Topics](https://github.com/37signals/bcx-api/blob/master/sections/topics.md)
* [Messages](https://github.com/37signals/bcx-api/blob/master/sections/messages.md)
* [Comments](https://github.com/37signals/bcx-api/blob/master/sections/comments.md)
* [Todo lists](https://github.com/37signals/bcx-api/blob/master/sections/todolists.md)
* [Todos](https://github.com/37signals/bcx-api/blob/master/sections/todos.md)
* [Documents](https://github.com/37signals/bcx-api/blob/master/sections/documents.md)
* [Attachments](https://github.com/37signals/bcx-api/blob/master/sections/attachments.md)
* [Uploads](https://github.com/37signals/bcx-api/blob/master/sections/uploads.md)
* [Calendars](https://github.com/37signals/bcx-api/blob/master/sections/calendars.md)
* [Calendar events](https://github.com/37signals/bcx-api/blob/master/sections/calendar_events.md)


API still under development
---------------------------

* Live updates: Pushing changes to the browser so they'll appear without needing to refresh
* Notifications: Letting people know by email if new content was added
* Moving todos and todolists: Changing their position in the UI
* Companies/Groups: Organize people in groups


Help us make it better
----------------------

Please tell us how we can make the API better. If you have a specific feature request or if you found a bug, please use GitHub issues. Fork these docs and send a pull request with improvements.

To talk with us and other developers about the API, subscribe to the [37signals-api mailing list](http://groups.google.com/group/37signals-api).
