Companies / Groups
==================

Use Companies and Groups to make sure everyone is in the right place, and to make invitations and notifications a snap!

Inside the API companies are referred to as "groups, and departments as "subgroups".

Get groups
----------

* `GET /groups.json` will return all groups and subgroups on the account. Only the groups a user has access to will be visible via the API.

```json
[
  {
    "created_at": "2014-09-24T09:12:00.000-05:00",
    "id": 261162085,
    "name": "Partners",
    "updated_at": "2014-09-26T16:13:55.000-05:00"
  },
  {
    "id": 654632876,
    "name": "Basecamp",
    "created_at": "2014-09-24T09:12:00.000-05:00",
    "updated_at": "2014-09-29T10:05:22.000-05:00",
    "subgroups": [
      {
        "created_at": "2014-09-25T16:04:39.000-05:00",
        "id": 1009501287,
        "name": "Designers",
        "updated_at": "2014-09-25T16:04:39.000-05:00"
      },
      {
        "created_at": "2014-09-25T16:04:39.000-05:00",
        "id": 1009501288,
        "name": "Support",
        "updated_at": "2014-09-25T16:04:39.000-05:00"
      },
      {
        "created_at": "2014-09-25T16:04:39.000-05:00",
        "id": 1009501289,
        "name": "Programmers",
        "updated_at": "2014-09-25T16:04:39.000-05:00"
      }
    ]
  }
]
```

Get group
---------

* `GET /groups/1.json` will return the specified group and members of that group. Members of this groups subgroups will not be returned. See the **Get subgroup** endpoint to view an individual subgroup and it's members. If you request a group you do not have access to, you'll se a `404 Not Found`.

```json
{
  "created_at": "2014-09-24T09:12:00.000-05:00",
  "id": 654632876,
  "name": "Basecamp",
  "subgroups": [
    {
      "created_at": "2014-09-25T16:04:39.000-05:00",
      "id": 1009501287,
      "name": "Designers",
      "updated_at": "2014-09-25T16:04:39.000-05:00"
    },
    {
      "created_at": "2014-09-25T16:04:39.000-05:00",
      "id": 1009501288,
      "name": "Support",
      "updated_at": "2014-09-25T16:04:39.000-05:00"
    },
    {
      "created_at": "2014-09-25T16:04:39.000-05:00",
      "id": 1009501289,
      "name": "Programmers",
      "updated_at": "2014-09-25T16:04:39.000-05:00"
    }
  ],
  "memberships": [
    {
      "id": 149087659,
      "identity_id": 982871737,
      "name": "Jason Fried",
      "email_address": "jason@basecamp.com",
      "admin": true,
      "avatar_url": "https://asset0.37img.com/global/4113d0a133a32931be8934e70b2ea21efeff72c1/avatar.96.gif",
      "fullsize_avatar_url": "https://asset0.37img.com/global/4113d0a133a32931be8934e70b2ea21efeff72c1/original.gif?r=3",
      "created_at": "2012-03-22T16:56:48-05:00",
      "updated_at": "2012-03-22T16:56:48-05:00",
      "url": "https://basecamp.com/<accountid>/api/v1/people/149087659-jason-fried.json",
      "app_url": "https://basecamp.com/<accountid>/people/149087659-jason-fried"
    },
    {
      "id": 1071630348,
      "identity_id": 827377171,
      "name": "Jeremy Kemper",
      "email_address": "jeremy@basecamp.com",
      "admin": true,
      "avatar_url": "https://asset0.37img.com/global/e68cafa694e8f22203eb36f13dccfefa9ac0acb2/avatar.96.gif",
      "fullsize_avatar_url": "https://asset0.37img.com/global/4113d0a133a32931be8934e70b2ea21efeff72c1/original.gif?r=3",
      "created_at": "2012-03-22T16:56:48-05:00",
      "updated_at": "2012-03-22T16:56:48-05:00",
      "url": "https://basecamp.com/<accountid>/api/v1/people/1071630348-jeremy-kemper.json",
      "app_url": "https://basecamp.com/<accountid>/people/1071630348-jeremy-kemper"
    }
  ]
}
```

Get subgroup
------------

* `GET /groups/1/subgroups/2.json` will return the specified sugroup and members of that subgroup. If you request a group you do not have access to, you'll se a `404 Not Found`.

```json
{
  "created_at": "2014-09-25T16:04:39.000-05:00",
  "id": 1009501289,
  "name": "Programmers",
  "parent_id": 654632876,
  "updated_at": "2014-09-25T16:04:39.000-05:00",
  "memberships": [
    {
      "id": 1071630348,
      "identity_id": 827377171,
      "name": "Jeremy Kemper",
      "email_address": "jeremy@basecamp.com",
      "admin": true,
      "avatar_url": "https://asset0.37img.com/global/e68cafa694e8f22203eb36f13dccfefa9ac0acb2/avatar.96.gif",
      "fullsize_avatar_url": "https://asset0.37img.com/global/4113d0a133a32931be8934e70b2ea21efeff72c1/original.gif?r=3",
      "created_at": "2012-03-22T16:56:48-05:00",
      "updated_at": "2012-03-22T16:56:48-05:00",
      "url": "https://basecamp.com/<accountid>/api/v1/people/1071630348-jeremy-kemper.json",
      "app_url": "https://basecamp.com/<accountid>/people/1071630348-jeremy-kemper"
    }
  ]
}
```

Create group
------------

* `POST /groups.json` will create a new group from the parameters passed. If no memeberships are passed the group will be invisible in the user interface of the application, but still accessible via the API if you are an admin. Only existing users can be added to companies or groups. Make sure you've added someone to your account before adding them to a group.

```json
{
  "name": "New Company Name",
  "memberships": [
    {
      "person_id": 1071630348
    }
  ]
}
```
This will return `201 Created`, with the location of the new group in the `Location` header along with the current JSON representation of the group if the creation was a success. See the **Get group** enpoint for more information. If the user does not have access to the create new groups you'll see a `403 Forbidden`.

Create subgroup
---------------

* `POST /groups/1/subgroups.json` will create a new subgroup from the parameters passed. If no memberships are passed the subgroup will be invisible in the user interface of the application, but still accessible via the API. Only existing users can be added to subgroups. Make sure you've added someone to your account before adding them to a subgroup.


```json
{
  "name": "Subgroup of Basecamp Group",
  "memberships": [
    {
      "person_id": 1071630348
    }
  ]
}
```

This will return `201 Created`, with the location of the new subgroup in the `Location` header along with the current JSON representation of the subgroup if the creation was a success. See the **Get subgroup** enpoint for more information. If the user does not have access to the create new groups you'll see a `403 Forbidden`.

Update group
------------

* `PUT /groups/1.json` will update the group from the parameters passed.

```json
{
  "name": "Update the group name"
}
```

This will return a `200 OK` if the update was a success along with the current JSON representation of the group. See **Get group** endpoint for more information. If the user does not have access to update the group, you'll see `403 Forbiddden`.

Add members to a group
----------------------

* `PUT /groups/1.json` will add new members to an existing group from the membership parameters passed. To remove a member from an existing group see the **Delete membership** endpoint.

```json
{
  "memberships": [
    { "person_id": 1071630348 },
    { "person_id": 149087659 }
  ]
}
```

This will return a `200 OK` if the update was a success along with the current JSON representation of the group. See **Get group** endpoint for more information. If the user does ont have access to update the members of a group, you'll see `403 Forbiddden`.

Update subgroup
---------------

* `PUT /groups/1/subgroups/2.json` will update the subgroup from the parameters passed.

```json
{
  "name": "Update the subgroup name"
}
```

This will return a `200 OK` if the update was a success along with the current JSON representation of the subgroup. See **Get subgroup** endpoint for more information. If the user does not have access to update the subgroup, you'll see `403 Forbiddden`.

Add members to a subgroup
----------------------

* `PUT /groups/1/subgroups/2.json` will add new members to an existing subgroup from the parameters passed. To remove a member from an existing subgroup see the **Delete membership** endpoint. Users can only be added to a subgroup if they already belong to the parent group.

```json
{
  "memberships": [
    { "person_id": 1071630348 },
    { "person_id": 149087659 }
  ]
}
```

This will return a `200 OK` if the update was a success along with the current JSON representation of the subgroup. See **Get subgroup** endpoint for more information. If the user does not have access to update the members of a subgroup, you'll see `403 Forbiddden`.

Delete group
------------

* `DELETE /groups/1.json` will delete the group specified and return `204 No Content` if the delete was successful. If the user does not have access to delete the group, you'll see a `403 Forbidden`.

Delete subgroup
---------------

* `DELETE /groups/1/subgroups/2.json` will delete the subgroup specifieid and return a `204 No Content` if the delete was successful. If the user does not have access to delete the subgroup, you'll see a `403 Forbidden`.

Delete a member of a group
----------------------------

* `DELETE /groups/1/memberships/1.json` will delete the membership specified and return `204 No Content` if the delete was successful. If the user does not have access to delete the member, you'll see a `403 Forbidden`. The ID in `memberships/1.json` is the `person_id` not the membership ID because `person_id` is accessible via the groups API. The ID of the person can be found in the membership list on the group. If a member is deleted from the group they will also be deleted from all subgroups that are children of the group.

Delete a member of a subgroup
----------------------------

* `DELETE /groups/1/subgroups/2/memberships/1.json` will delete the membership specified and return `204 No Content` if the delete was successful. If the user does not have access to delete the member, you'll see a `403 Forbidden`. The ID in `memberships/1.json` is the `person_id` not the membership ID because `person_id` is accessible via the subgroups API. The ID of the person can be found in the membership list on the subgroup.
