The new Basecamp API
====================

The all-new Basecamp has an all-new API. It is not compatible with the [Basecamp Classic API](http://developer.37signals.com/basecamp/). All integrations will have to be updated to use the new API. The core ingredients are still the same, though. This is a REST-style API that uses JSON for serialization and OAuth2 for authentication.

NOTE: This has yet to go live. We're putting the final touches on everything now. It should be available very shortly.


Authentication
--------------

If you're making a private integration with Basecamp for your own purposes, you can use HTTP Basic authentication. This is secure since all requests in the new Basecamp happens over SSL.

If you're making a public integration with Basecamp for others to enjoy, you must use OAuth2. This allows users to authorize your application to use Basecamp on their behalf and avoids having you storing their actual password. Please [register your OAuth2 app](http://integrate.37signals.com/apps/new) before use. If you already have a registration, you can also [update it](http://integrate.37signals.com/).


No XML, just JSON
-----------------

We only support JSON for serialization of data. Our format is to have no root element and we use snake\_case to describe attribute keys. This means that you have to send `Content-Type: application/json; charset=utf-8` when you're POSTing or PUTing data into Basecamp. All API URLs end in .json to indicate that they accept JSON.


Use HTTP caching
----------------

It's strongly encouraged that you use the HTTP freshness headers to increase the speed of your application and lessen the load on our servers. Most requests we return will include `Last-Modified` and `ETag` headers. When you first request a resource, store these values, and then submit them back to us on subsequent requests as `If-Modified-Since` and `If-None-Match`. If the resource hasn't changed, you'll see a `304 Not Modified` response, which saves you the bandwidth and us the computation of sending something you already have.


Include a user agent
--------------------

Please include a `User-Agent` header with the name of your application and a link to it or your email address, so we can get in touch in case you're doing something wrong (so we may warn you before you're blacklisted) or something awesome (so we may congratulate you). Example `User-Agent: Freshbooks (http://freshbooks.com)`.


Rate limiting
-------------

You can perform up to 500 requests per 10 second period from the same IP address for the same account. If you exceed this limit, you'll get a [429 Too Many Requests](http://tools.ietf.org/html/draft-nottingham-http-new-status-02#section-4) response for subsequent requests. Check the `Retry-After` header to see how many seconds to wait before trying again.


Making a request
----------------

All URLs in the API sections assume a base like this: https://basecamp.com/999999999/api/v1/. That includes the account id and the version of the API. If we change the API in backwards incompatible ways, we'll be able to bump the version marker and still have old integrations work.

So to make a request for all the projects on your account, you'd append the projects index path to the base url to form something like https://basecamp.com/999999999/api/v1/projects.json. In curl, that'd look like:

```shell
curl -u user:pass -H 'User-Agent: Rapp (david@37signals.com)' https://basecamp.com/999999999/api/v1/projects.json
```

To create something, it's the same deal except you also have to include the content-type header and the data. Example:

```shell
curl -u user:pass -H 'Content-Type: application/json'  -H 'User-Agent: Rapp (david@37signals.com)' \
-d '{ "name": "My new project!" }' \
https://basecamp.com/999999999/api/v1/projects.json
```

That's all!


Sections ready for use
----------------------

* [Projects](https://github.com/37signals/bcx-api/blob/master/sections/projects.md)
* [People](https://github.com/37signals/bcx-api/blob/master/sections/people.md)
* [Accesses](https://github.com/37signals/bcx-api/blob/master/sections/accesses.md)
* [Messages](https://github.com/37signals/bcx-api/blob/master/sections/messages.md)
* [Comments](https://github.com/37signals/bcx-api/blob/master/sections/comments.md)
* [Todo lists](https://github.com/37signals/bcx-api/blob/master/sections/todolists.md)
* [Todos](https://github.com/37signals/bcx-api/blob/master/sections/todos.md)


Concerns still under development
--------------------------------

* Calendars: Working with events
* Companies/Groups: Organize people in groups
* Documents: Collaborative texts
* Events: We audit log just about everything, share the firehose
* Topics: Everything can have comments, see what does
* Uploads/Attachments: Uploading and downloading of files
* Notifications: Letting people know by email if new content was added
* Trashing: Deleting content
* Moving todos and todolists: Changing their position in the UI


Help us make it better
----------------------

Please tell us how we can make the API better. If you have a specific feature request or if you found a bug, please use Github issues. If you just want to talk with us or other developers about the API, you can subscribe to the [37signals-api mailing list](http://groups.google.com/group/37signals-api).
