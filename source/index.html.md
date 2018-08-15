---
title: MyCurrency API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a> <!--- need to add link here --->
  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the MyCurrency API! The MyCurrency API endpoints are hosted at https://api.mycurrency.com


This example API documentation page was created with [Slate](https://github.com/lord/slate) <!--- need to add link here -->. Feel free to make pull requests if you have suggestions on how to augment it.

# Users

## Get a User

```shell
curl 'https://api.mycurrency.com/users/2' 
  -H 'Host: api.mycurrency.com' -H 'Accept: application/json' -H 'Content-Type: application/json'
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "id": "2",
    "type": "users",
    "attributes": {
      "username": "RonaldMcDonald",
      "created-at": "2018-08-08T01:22:54.571-07:00",
      "active": true,
      "get-avatar-url": "/system/users/avatars/000/000/002/original/afternoon_portrait.jpg?1534139495"
    }
  }
}
```

This endpoint retrieves a particular user by ID and its basic public information.

### HTTP Request

`GET https://api.mycurrency.com/users/<ID>`

<aside class="notice">
Authentication: not required
</aside>
## Get Authorized User

```shell
curl "https://api.mycurrency.com/users/2"
  -H "Authorization: Bearer j47lbjj8r9n5yy8mup6cxqc8h70yvhnilm0g84kg0raqckus0k1koj9f75ao" 
  -H 'Host: api.mycurrency.com' -H 'Accept: application/json' -H 'Content-Type: application/json'
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "id": "2",
    "type": "users",
    "attributes": {
      "username": "RonaldMcDonald",
      "created-at": "2018-08-08T01:22:54.571-07:00",
      "active": true,
      "get-avatar-url": "/system/users/avatars/000/000/002/original/afternoon_portrait.jpg?1534139495"
      "email": "RonaldMcDonald@mcdonalds.com",
      "sub-location-id": 1,
      "updated-at": "2018-08-14T14:51:07.965-07:00"
    }
  }
}
```

This endpoint retrieves the current user and its full information.

### HTTP Request

`GET https://api.mycurrency.com/users/<ID>`

<aside class="notice">
Authentication: the request requires the OAuth access-token associated with the User referenced by the ID 
</aside>

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

## Get a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl "http://example.com/api/kittens/2"
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.get(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific kitten.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to retrieve

## Delete a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.delete(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.delete(2)
```

```shell
curl "http://example.com/api/kittens/2"
  -X DELETE
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.delete(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ":("
}
```

This endpoint deletes a specific kitten.

### HTTP Request

`DELETE http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete

