---
title: MyCurrency API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell

toc_footers:

includes:
  - errors

search: true
---

# Introduction

The MyCurrency REST API is hosted at https://api.mycurrency.com and provides the ability to fully interact with the MyCurrency application. 

This API reference provides information on available endpoints.

# Users

## Get a User

```shell
curl 'https://api.mycurrency.com/users/2' \
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
      "public-email": null,
      "get-avatar-url": "/system/users/avatars/000/000/002/original/afternoon_portrait.jpg?1534139495"
      "number-of-reviews": 0,
      "average-score": null,
      "product-count": 0,
      "product-cancellation-count": 0,
      "store-count": 0,
      "currency-count": 1,
      "listing-count": 0
    }
  }
}
```

This endpoint retrieves a particular user and its basic public information by ID.

### HTTP Request

`GET https://api.mycurrency.com/users/<ID>`

<aside class="notice">
Authentication: not required
</aside>

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the user
username | The username that the user is identified by
created-at | The time and date when the user was created
active | Whether the user is active or not
public-email | An email that is viewable by the public
get-avatar-url | The URL at which the user profile picture can be found
number-of-reviews | The total number of reviews received by all of the user's stores
average-score | The average score of all the reviews received by the user's stores, out of 5
product-count | The number of products offered by all of the user's stores
product-cancellation-count | The number of product cancellations created by the user
store-count | The number of stores belonging to the user
currency-count | The number of currencies belonging to the user
listing-count | The number of active listings belonging to the user

## Get a User from Username

```shell
curl 'https://api.mycurrency.com/get_user_from_username?q=RonaldMcDonald' \
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
      "public-email": null,
      "get-avatar-url": "/system/users/avatars/000/000/002/original/afternoon_portrait.jpg?1534139495"
      "number-of-reviews": 0,
      "average-score": null,
      "product-count": 0,
      "product-cancellation-count": 0,
      "store-count": 0,
      "currency-count": 1,
      "listing-count": 0
    }
  }
}
```

This endpoint retrieves a particular user and its basic public information by ID.

### HTTP Request

`GET https://api.mycurrency.com/get_user_from_username?q=RonaldMcDonald`

<aside class="notice">
Authentication: not required
</aside>

### ARGUMENTS

Parameter | Type | Required | Description
--------- | ------- | ------- | -----------
q | string | yes | The username of the user queried

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the user
username | The username that the user is identified by
created-at | The time and date when the user was created
active | Whether the user is active or not
public-email | An email that is viewable by the public
get-avatar-url | The URL at which the user profile picture can be found
number-of-reviews | The total number of reviews received by all of the user's stores
average-score | The average score of all the reviews received by the user's stores, out of 5
product-count | The number of products offered by all of the user's stores
product-cancellation-count | The number of product cancellations created by the user
store-count | The number of stores belonging to the user
currency-count | The number of currencies belonging to the user
listing-count | The number of active listings belonging to the user

## Get a User with Authorization

```shell
curl "https://api.mycurrency.com/users/2" \
  -H "Authorization: Bearer j47lbjj8r9n5yy8mup6cxqc8h70yvhnilm0g84kg0raqckus0k1koj9f75ao" \
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
      "public-email": null,
      "get-avatar-url": "/system/users/avatars/000/000/002/original/afternoon_portrait.jpg?1534139495"
      "number-of-reviews": 0,
      "average-score": null,
      "product-count": 0,
      "product-cancellation-count": 0,
      "store-count": 0,
      "currency-count": 1,
      "listing-count": 0
      "email": "RonaldMcDonald@mcdonalds.com",
      "sub-location-id": 1,
      "sub-location-name": "San Francisco",
      "updated-at": "2018-08-22T01:28:56.872-07:00"
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

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the user
username | The username that the user is identified by
created-at | The time and date when the user was created
active | Whether the user is active or not
public-email | An email that is viewable by the public
get-avatar-url | The URL at which the user profile picture can be found
number-of-reviews | The total number of reviews received by all of the user's stores
average-score | The average score of all the reviews received by the user's stores, out of 5
product-count | The number of products offered by all of the user's stores
product-cancellation-count | The number of product cancellations created by the user
store-count | The number of stores belonging to the user
currency-count | The number of currencies belonging to the user
listing-count | The number of active listings belonging to the user
email | The email address associated with the user account
sub-location-id | The ID of the sub location associated with the user account
sub-location-name | The name of the sub location associated with the user account
updated-at | The time and date when the user was last updated

## List User Contacts

```shell
curl "https://api.mycurrency.com/user_contacts" \
  -H "Authorization: Bearer j47lbjj8r9n5yy8mup6cxqc8h70yvhnilm0g84kg0raqckus0k1koj9f75ao" \
  -H 'Host: api.mycurrency.com' -H 'Accept: application/json' -H 'Content-Type: application/json'
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": "3",
      "type": "users",
      "attributes": {
        "username": "Hannibal",
        "created-at": "2018-11-04T12:08:04.094-08:00",
        "active": true,
        "public-email": null,
        "get-avatar-url": "/avatars/original/missing.png",
        "number-of-reviews": 3,
        "average-score": "3.67",
        "product-count": 1,
        "product-cancellation-count": 3,
        "store-count": 1,
        "currency-count": 1,
        "listing-count": 0
      }
    },
    {
      "id": "18",
      "type": "users",
      "attributes": {
        "username": "ariastark",
        "created-at": "2019-06-12T06:57:52.302-07:00",
        "active": true,
        "public-email": null,
        "get-avatar-url": "/system/users/avatars/000/000/018/original/avatar.jpg?1561108444",
        "number-of-reviews": 0,
        "average-score": null,
        "product-count": 0,
        "product-cancellation-count": 0,
        "store-count": 0,
        "currency-count": 2,
        "listing-count": 0
      }
    },
    {
      "id": "17",
      "type": "users",
      "attributes": {
        "username": "eddardstark",
        "created-at": "2019-06-12T01:53:25.132-07:00",
        "active": true,
        "public-email": null,
        "get-avatar-url": "/system/users/avatars/000/000/017/original/avatar.jpg?1560946499",
        "number-of-reviews": 0,
        "average-score": null,
        "product-count": 0,
        "product-cancellation-count": 0,
        "store-count": 0,
        "currency-count": 12,
        "listing-count": 0
      }
    },
    {
      "id": "16",
      "type": "users",
      "attributes": {
        "username": "the_hulk",
        "created-at": "2019-06-06T11:18:50.759-07:00",
        "active": true,
        "public-email": null,
        "get-avatar-url": "/avatars/original/missing.png",
        "number-of-reviews": 0,
        "average-score": null,
        "product-count": 0,
        "product-cancellation-count": 0,
        "store-count": 0,
        "currency-count": 0,
        "listing-count": 0
      }
    },
    {
      "id": "2",
      "type": "users",
      "attributes": {
        "username": "spiderman",
        "created-at": "2018-11-04T12:04:25.987-08:00",
        "active": true,
        "public-email": null,
        "get-avatar-url": "/avatars/original/missing.png",
        "number-of-reviews": 0,
        "average-score": null,
        "product-count": 0,
        "product-cancellation-count": 0,
        "store-count": 0,
        "currency-count": 1,
        "listing-count": 0
      }
    }
  ],
  "links": {
    "self": "https://api.mycurrency.com/user_contacts?",
    "first": "https://api.mycurrency.com/user_contacts?page=1&per_page=25",
    "prev": null,
    "next": null,
    "last": "https://api.mycurrency.com/user_contacts?page=1&per_page=25"
  },
  "meta": {
    "pagination": {
      "per-page": null,
      "total-pages": "1",
      "total-count": "5"
    }
  }
}
```

This endpoint retrieves a list of users that the logged-in user has sent or received transfers and issuances to and from, ordered from users that received the most transfers and issuances from the subject to those that received the fewest, followed by users that sent the most transfers and issuances to the subject to those that sent the fewest.

### HTTP Request

`GET https://api.mycurrency.com/user_contacts`

<aside class="notice">
Authentication: required 
</aside>

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the user
username | The username that the user is identified by
created-at | The time and date when the user was created
active | Whether the user is active or not
public-email | An email that is viewable by the public
get-avatar-url | The URL at which the user profile picture can be found
number-of-reviews | The total number of reviews received by all of the user's stores
average-score | The average score of all the reviews received by the user's stores, out of 5
product-count | The number of products offered by all of the user's stores
product-cancellation-count | The number of product cancellations created by the user
store-count | The number of stores belonging to the user
currency-count | The number of currencies belonging to the user
listing-count | The number of active listings belonging to the user

## Search Users

```shell
curl "https://api.mycurrency.com/search_users?input=scip" \
  -H "Authorization: Bearer j47lbjj8r9n5yy8mup6cxqc8h70yvhnilm0g84kg0raqckus0k1koj9f75ao" \
  -H 'Host: api.mycurrency.com' -H 'Accept: application/json' -H 'Content-Type: application/json'
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": "4",
      "type": "users",
      "attributes": {
        "username": "ScipioAfricanus",
        "created-at": "2018-11-05T02:07:30.134-08:00",
        "active": true,
        "public-email": "test@test.com",
        "get-avatar-url": "/system/users/avatars/000/000/004/original/1.jpg?1559736060",
        "number-of-reviews": 0,
        "average-score": null,
        "product-count": 2,
        "product-cancellation-count": 0,
        "store-count": 5,
        "currency-count": 6,
        "listing-count": 1
      }
    }
  ],
  "links": {
    "self": "https://api.mycurrency.com/search_users?input=scip",
    "first": "https://api.mycurrency.com/search_users?input=scip&page=1&per_page=25",
    "prev": null,
    "next": null,
    "last": "https://api.mycurrency.com/search_users?input=scip&page=1&per_page=25"
  },
  "meta": {
    "pagination": {
      "per-page": null,
      "total-pages": "1",
      "total-count": "1"
    }
  }
}
```

This endpoint retrieves a list of users that have usernames that contain the search input. Only active users are included in the search results. 

### HTTP Request

`GET https://api.mycurrency.com/search_users?input={}`

<aside class="notice">
Authentication: required 
</aside>

### ARGUMENTS

Parameter | Type | Required | Description
--------- | ------- | ------- | -----------
input | string | yes | The characters that are searched against the usernames of the users

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the user
username | The username that the user is identified by
created-at | The time and date when the user was created
active | Whether the user is active or not
public-email | An email that is viewable by the public
get-avatar-url | The URL at which the user profile picture can be found
number-of-reviews | The total number of reviews received by all of the user's stores
average-score | The average score of all the reviews received by the user's stores, out of 5
product-count | The number of products offered by all of the user's stores
product-cancellation-count | The number of product cancellations created by the user
store-count | The number of stores belonging to the user
currency-count | The number of currencies belonging to the user
listing-count | The number of active listings belonging to the user

## Update User

```shell
curl -X PUT https://api.mycurrency.com/users/2 \
  -d 'user[sub_location_id]=2' \
  -H 'Authorization: Bearer j47lbjj8r9n5yy8mup6cxqc8h70yvhnilm0g84kg0raqckus0k1koj9f75ao' \
  -H 'Accept: application/json' \
  -H 'Content-Type: multipart/form-data'
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
      "public-email": null,
      "get-avatar-url": "/system/users/avatars/000/000/002/original/afternoon_portrait.jpg?1534139495"
      "number-of-reviews": 0,
      "average-score": null,
      "product-count": 0,
      "product-cancellation-count": 0,
      "store-count": 0,
      "currency-count": 1,
      "listing-count": 0
      "email": "RonaldMcDonald@mcdonalds.com",
      "sub-location-id": 2,
      "sub-location-name": "Vancouver",
      "updated-at": "2018-08-22T01:28:56.872-07:00"
    }
  }
}
```

Updates a user. Upon user creation, a new user is inactive and its username and sub_location_id fields are empty. A valid username and sub_location_id need to be provided in the first update that sets the user's active field to true. After the first update, the sub_location_id, avatar and active fields can be changed, but the username field cannot.

### HTTP Request

`PUT https://api.mycurrency.com/users/<ID>`

<aside class="notice">
Authentication: the request requires the OAuth access-token associated with the User referenced by the ID 
</aside>

### ARGUMENTS

Parameter | Type | Required | Description
--------- | ------- | ------- | -----------
active | boolean | no | Whether the user is active or not
avatar | filename | no | The image file to be uploaded as user's avatar picture
username | string | no | The username that the user is identified by 
sub_location_id | integer | no | The ID of the sub location associated with the user account

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the user
username | The username that the user is identified by
created-at | The time and date when the user was created
active | Whether the user is active or not
public-email | An email that is viewable by the public
get-avatar-url | The URL at which the user profile picture can be found
number-of-reviews | The total number of reviews received by all of the user's stores
average-score | The average score of all the reviews received by the user's stores, out of 5
product-count | The number of products offered by all of the user's stores
product-cancellation-count | The number of product cancellations created by the user
store-count | The number of stores belonging to the user
currency-count | The number of currencies belonging to the user
listing-count | The number of active listings belonging to the user
email | The email address associated with the user account
sub-location-id | The ID of the sub location associated with the user account
sub-location-name | The name of the sub location associated with the user account
updated-at | The time and date when the user was last updated

# Issuers

## Get an Issuer 

```shell
curl 'https://api.mycurrency.com/issuers/2' \
  -H 'Host: api.mycurrency.com' -H 'Accept: application/json' -H 'Content-Type: application/json'
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "id": "2",
    "type": "issuers",
    "attributes": {
      "user-id": 2
      "created-at": "2018-08-08T01:22:54.571-07:00",
      "updated-at": "2018-08-08T01:22:54.571-07:00",
    }
  }
}
```

This endpoint retrieves a particular issuer and its basic public information by its ID.

### HTTP Request

`GET https://api.mycurrency.com/issuers/<ID>`

<aside class="notice">
Authentication: not required
</aside>

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the issuer
user-id | The ID of the user that owns the issuer account
created_at | The time and date when the issuer account was created
updated_at | The time and date when the issuer account was last updated

## Get a User's Issuer Account

```shell
curl 'https://api.mycurrency.com/users/2/issuer' \
  -H 'Host: api.mycurrency.com' -H 'Accept: application/json' -H 'Content-Type: application/json'
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "id": "2",
    "type": "issuers",
    "attributes": {
      "user-id": 2
      "created-at": "2018-08-08T01:22:54.571-07:00",
      "updated-at": "2018-08-08T01:22:54.571-07:00",
    }
  }
}
```

This endpoint retrieves a particular issuer and its basic public information by the ID of its associated user.

### HTTP Request

`GET https://api.mycurrency.com/users/<USER-ID>/issuer`

<aside class="notice">
Authentication: not required
</aside>

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the issuer
user-id | The ID of the user that owns the issuer account
created_at | The time and date when the issuer account was created
updated_at | The time and date when the issuer account was last updated

# Currencies

## Get a Currency

```shell
curl 'https://api.mycurrency.com/currencies/2' \
  -H 'Accept: application/json' -H 'Content-Type: application/json'
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "id": "2",
    "type": "currencies",
    "attributes": {
      "issuer-id": 2,
      "issuer-user-id": 3,
      "issuer-user-username": "Hannibal",
      "issuer-user-avatar-url": "/system/users/avatars/000/000/004/original/1.jpg?1559736060",
      "issuer-public-currency-holding-id": 4,
      "burn-rate": 450,
      "daily-burn-rate": "0.00012614",
      "store-count": 2,
      "listing-count": 5,
      "product-count": 20,
      "name": "ACME Toon Shop dollars",
      "description": "Spendable at any ACME Toon Shop",
      "created-at": "2018-08-12T01:17:31.176-07:00",
      "updated-at": "2018-08-12T23:49:56.793-07:00",
      "get-icon-url": "/system/currencies/icons/000/000/002/original/DaffyDuck.png?1534142996"
      "number-of-reviews": 5,
      "average-score": "3.67",
      "user-is-active": true
    }
  }
}
```

This endpoint retrieves a particular currency and its basic public information by ID.

### HTTP Request

`GET https://api.mycurrency.com/currencies/<ID>`

<aside class="notice">
Authentication: not required
</aside>

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the currency
issuer-id | The ID of the issuer account that issued the currency
issuer-user-id | The ID of the user account that issued the currency
issuer-user-username | The ID of the user account that issued the currency
issuer-user-avatar-url | The URL at which the avatar picture of the user that issues the currency can be found
issuer-public-currency-holding-id | The user ID of the public currency holding of the issuer of the currency
burn-rate | The annual rate at which holdings of the currency burn, by basis point (100 = 1%) 
daily-burn-rate | The daily rate at which the currency burns, by fraction of 1 (0.01 = 1%)
store-count | The number of stores associated with the currency
listing-count | The number of active listings associated with the currency
product-count | The number of products associated with the currency
name | The name of the currency
description | The description of the currency
created-at | The time and date when the currency was created
updated-at | The time and date when the currency was last updated
get-icon-url | The URL at which the currency icon picture can be found
number-of-reviews | The number of store reviews created for all stores associated with the currency
average-score | The average score of store reviews created for all stores associated with the currency, out of 5
user-is-active | Whether the user that issues the currency is active

## Get a Currency with Authorization

```shell
curl 'https://api.mycurrency.com/authorized_currencies/4' \
  -H 'Authorization: Bearer j47lbjj8r9n5yy8mup6cxqc8h70yvhnilm0g84kg0raqckus0k1koj9f75ao' \
  -H 'Accept: application/json' -H 'Content-Type: application/json'
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "id": "10",
    "type": "currencies",
    "attributes": {
      "issuer-id": 4,
      "issuer-user-id": 4,
      "issuer-user-name": "ScipioAfricanus",
      "issuer-user-avatar-url": "/system/users/avatars/000/000/004/original/1.jpg?1559736060",
      "issuer-public-currency-holding-id": 24,
      "burn-rate": 600,
      "daily-burn-rate": "0.000169508",
      "store-count": 1,
      "listing-count": 0,
      "product-count": 1,
      "name": "Turbo points",
      "description": "use to buy all sorts of turbo engines",
      "created-at": "2019-06-12T03:24:27.658-07:00",
      "updated-at": "2019-06-12T03:24:27.658-07:00",
      "get-icon-url": "/icons/original/missing.png",
      "number-of-reviews": 0,
      "average-score": null,
      "private-amount-atomic": 40000000000000,
      "public-amount-atomic": 62000000000000,
      "total-amount-atomic": 102000000000000,
      "number-of-burn-rate-changes": 0,
      "number-public-currency-holdings": 2,
      "next-daily-burn-amount": "17289816000.0",
      "private-currency-holding-id": 18,
      "public-currency-holding-id": 12,
      "timedate-of-last-private-tx": "2019-06-12T10:41:24-07:00",
      "amount-of-last-private-tx": -70000000000000,
      "timedate-of-last-public-tx": "2019-06-17T17:06:45-07:00",
      "amount-of-last-public-tx": 2000000000000
      "private-burn-amount-atomic": 86714320326,
      "public-burn-amount-atomic": 13092929333,
      "total-burn-amount-atomic": 99807249659
    }
  }
}
```

This endpoint retrieves a particular currency and more detailed public information by ID as well as details about logged-in user's holdings of that currency 

### HTTP Request

`GET https://api.mycurrency.com/authorized_currencies/<ID>`

<aside class="notice">
Authentication: required
</aside>

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the currency
issuer-id | The ID of the issuer account that issued the currency
issuer-user-id | The ID of the user account that issued the currency
issuer-user-username | The ID of the user account that issued the currency
issuer-user-avatar-url | The URL at which the avatar picture of the user that issues the currency can be found
issuer-public-currency-holding-id | The user ID of the public currency holding of the issuer of the currency
burn-rate | The annual rate at which holdings of the currency burn, by basis point (100 = 1%) 
daily-burn-rate | The daily rate at which the currency burns, by fraction of 1 (0.01 = 1%)
store-count | The number of stores associated with the currency
listing-count | The number of active listings associated with the currency
product-count | The number of products associated with the currency
name | The name of the currency
description | The description of the currency
created-at | The time and date when the currency was created
updated-at | The time and date when the currency was last updated
get-icon-url | The URL at which the currency icon picture can be found
number-of-reviews | The number of store reviews created for the store
average-score | The average score of store reviews created for all stores associated with the currency, out of 5
private-amount-atomic | The amount held in the logged-in user's private holding of the specified currency, in atomic units (each whole unit is composed of 10^10 atomic units)
public-amount-atomic | The amount held in the logged-in user's public holding of the specified currency, in atomic units (each whole unit is composed of 10^10 atomic units)
total-amount-atomic | The total amount held in the logged-in user's public and private holdings of the specified currency, in atomic units (each whole unit is composed of 10^10 atomic units)
number-of-burn-rate-changes | The number of burn rate changes that the currency has undergone since its creation
number-of-public-currency-holdings | The number of public holdings of the currency
next-daily-burn-amount | The total amount of units in the logged-in user's public and private currency holdings of the specified currency that will be burned over the next day, in atomic units (each whole unit is composed of 10^10 atomic units) 
private-currency-holding-id | The ID of the logged-in user's private holding of the specified currency
public-currency-holding-id | The ID of the logged-in user's public holding of the specified currency
timedate-of-last-private-tx | The date when the last transaction in the logged-in user's private holding of the specified currency took place
amount-of-last-private-tx | The amount, in atomic units, that was transferred in the last transaction to/from the logged-in user's private holding of the specified currency
timedate-of-last-public-tx | The date when the last transaction in the logged-in user's public holding of the specified currency took place
amount-of-last-public-tx | The amount, in atomic units, that was transferred in the last transaction to/from the logged-in user's public holding of the specified currency
private-burn-amount-atomic | The amount, in atomic units, that was burned in the logged-in user's private holding of the specified currency
public-burn-amount-atomic | The amount, in atomic units, that was burned in the logged-in user's public holding of the specified currency
total-burn-amount-atomic | The total amount, in atomic units, that was burned in the logged-in user's public and private holdings of the specified currency

## List Currencies

```shell
curl "https://api.mycurrency.com/currencies" \
  -H 'Host: api.mycurrency.com' -H 'Accept: application/json' -H 'Content-Type: application/json'
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": "5",
      "type": "currencies",
      "attributes": {
        "issuer-id": 5,
        "issuer-user-id": 6,
        "issuer-user-username": "Estevan",
        "issuer-user-avatar-url": "/system/users/avatars/000/000/007/original/face.jpg?1560144110",
        "issuer-public-currency-holding-id": 24,
        "burn-rate": 500,
        "daily-burn-rate": "0.00014052",
        "store-count": 16,
        "listing-count": 4,
        "product-count": 31,
        "name": "Chilli pesos",
        "description": "Chilli pesos are backed by chillis",
        "created-at": "2018-09-22T18:57:27.193-07:00",
        "updated-at": "2018-09-22T18:57:27.193-07:00",
        "get-icon-url": "/system/currencies/icons/000/000/005/original/chilli-pesos.png?153414511"
        "number-of-reviews": 14,
        "average-score": "4.61"
      }
    },
    {
      "id": "4",
      "type": "currencies",
      "attributes": {
        "issuer-id": 4,
        "issuer-user-id": 5,
        "issuer-user-username": "Tom",
        "issuer-user-avatar-url": "/system/users/avatars/000/000/006/original/face.jpg?1560144110",
        "issuer-public-currency-holding-id": 13,
        "burn-rate": 550,
        "daily-burn-rate": "0.000154976",
        "store-count": 1,
        "listing-count": 10,
        "product-count": 19,
        "name": "Tom's Fruitstand bucks",
        "description": "Redeem Tom's Fruitstand bucks for delicious fruit",
        "created-at": "2018-09-22T17:10:21.588-07:00",
        "updated-at": "2018-09-22T17:10:21.588-07:00",
        "get-icon-url": "/system/currencies/icons/000/000/004/original/Tom-bucks.png?1534148467"
        "number-of-reviews": 7,
        "average-score": "5.00"
      }
    },
    {
      "id": "3",
      "type": "currencies",
      "attributes": {
        "issuer-id": 3,
        "issuer-user-id": 4,
        "issuer-user-username": "ScipioAfricanus",
        "issuer-user-avatar-url": "/system/users/avatars/000/000/005/original/portrait.jpg?1559144410",
        "issuer-public-currency-holding-id": 7,
        "burn-rate": 420,
        "daily-burn-rate": "0.000117548",
        "store-count": 4,
        "listing-count": 1,
        "product-count": 16,
        "name": "Horizon Cloud Computing dollars",
        "description": "Redeemable for Horizon Cloud Computing services",
        "created-at": "2018-09-22T17:10:21.588-07:00",
        "updated-at": "2018-09-22T17:10:21.588-07:00",
        "get-icon-url": "/system/currencies/icons/000/000/003/original/horizon-cloud.png?1534243939"
        "number-of-reviews": 3,
        "average-score": "4.00"
      }
    },
    {
      "id": "2",
      "type": "currencies",
      "attributes": {
        "issuer-id": 2,
        "issuer-user-id": 3,
        "issuer-user-username": "Hannibal",
        "issuer-user-avatar-url": "/system/users/avatars/000/000/004/original/1.jpg?1559736060",
        "issuer-public-currency-holding-id": 4,
        "burn-rate": 450,
        "daily-burn-rate": "0.00012614",
        "store-count": 2,
        "listing-count": 5,
        "product-count": 52,
        "name": "ACME Toon Shop dollars",
        "description": "Spendable at any ACME Toon Shop",
        "created-at": "2018-08-12T01:17:31.176-07:00",
        "updated-at": "2018-08-12T23:49:56.793-07:00",
        "get-icon-url": "/system/currencies/icons/000/000/002/original/DaffyDuck.png?1534142996"
        "number-of-reviews": 5,
        "average-score": "3.67"
      }
    },
    {
      "id": "1",
      "type": "currencies",
      "attributes": {
        "issuer-id": 2,
        "issuer-user-id": 3,
        "issuer-user-username": "Hannibal",
        "issuer-user-avatar-url": "/system/users/avatars/000/000/004/original/1.jpg?1559736060",
        "issuer-public-currency-holding-id": 3,
        "burn-rate": 740,
        "daily-burn-rate": "0.000210611",
        "store-count": 3, 
        "listing-count": 0,
        "product-count": 12,
        "name": "Calm dollars",
        "description": "Redeemable for services at Calm Massage Therapy",
        "created-at": "2017-08-10T17:03:08.287-07:00",
        "updated-at": "2017-08-10T17:58:08.738-07:00",
        "get-icon-url": "/system/currencies/icons/000/000/001/original/calm_dollars.jpg?1534619841"
        "number-of-reviews": 3,
        "average-score": "2.61"
      }
    }
  ],
  "links": {
    "self": "http://api.mycurrency.com/currencies?",
    "first": "http://api.mycurrency.com/currencies?page=1&per_page=25",
    "prev": null,
    "next": null,
    "last": "http://api.mycurrency.com/currencies?page=1&per_page=25"
  },
  "meta": {
    "pagination": {
      "per-page": null,
      "total-pages": "1",
      "total-count": "5"
    }
  }
}
```

This endpoint retrieves all currencies with an active issuer, sorted by ID in descending order.

### HTTP Request

`GET https://api.mycurrency.com/currencies`

<aside class="notice">
Authentication: not required
</aside>

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the currency
issuer-id | The ID of the issuer account that issued the currency
issuer-user-id | The ID of the user account that issued the currency
issuer-user-username | The ID of the user account that issued the currency
issuer-user-avatar-url | The URL at which the avatar picture of the user that issues the currency can be found
issuer-public-currency-holding-id | The user ID of the public currency holding of the issuer of the currency
burn-rate | The annual rate at which holdings of the currency burn, by basis point (100 = 1%) 
daily-burn-rate | The daily rate at which the currency burns, by fraction of 1 (0.01 = 1%)
store-count | The number of stores associated with the currency
listing-count | The number of active listings associated with the currency
product-count | The number of products associated with the currency
name | The name of the currency
description | The description of the currency
created-at | The time and date when the currency was created
updated-at | The time and date when the currency was last updated
get-icon-url | The URL at which the currency icon picture can be found
number-of-reviews | The number of store reviews created for all stores associated with the currency
average-score | The average score of the store reviews, out of 5

## List a User's Currencies

```shell
curl "https://api.mycurrency.com/currencies?user_id=3" \
  -H 'Host: api.mycurrency.com' -H 'Accept: application/json' -H 'Content-Type: application/json'
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": "75",
      "type": "currencies",
      "attributes": {
        "issuer-id": 3,
        "issuer-user-id": 3,
        "issuer-user-name": "Hannibal",
        "issuer-user-avatar-url": "/system/users/avatars/000/000/003/original/avatar.jpg?1562578009",
        "issuer-public-currency-holding-id": null,
        "burn-rate": 1000,
        "daily-burn-rate": "0.000288618",
        "store-count": 0,
        "listing-count": 0,
        "product-count": 0,
        "name": "Saint Patricks Day Money",
        "description": "Money for saint paddies",
        "created-at": "2019-07-16T22:39:39.161-07:00",
        "updated-at": "2019-07-16T22:39:39.161-07:00",
        "get-icon-url": "/system/currencies/icons/000/000/075/original/currency.jpg?1563341979",
        "number-of-reviews": 0,
        "average-score": null,
        "public-amount-atomic": 0,
        "public-currency-holding-id": null
      }
    },
    {
      "id": "74",
      "type": "currencies",
      "attributes": {
        "issuer-id": 3,
        "issuer-user-id": 3,
        "issuer-user-name": "Hannibal",
        "issuer-user-avatar-url": "/system/users/avatars/000/000/003/original/avatar.jpg?1562578009",
        "issuer-public-currency-holding-id": 53,
        "burn-rate": 0,
        "daily-burn-rate": "0.0",
        "store-count": 0,
        "listing-count": 0,
        "product-count": 0,
        "name": "sam dollar",
        "description": "store clothing",
        "created-at": "2019-07-14T14:32:28.237-07:00",
        "updated-at": "2019-07-14T14:32:28.237-07:00",
        "get-icon-url": "/system/currencies/icons/000/000/074/original/currency.jpg?1563139948",
        "number-of-reviews": 0,
        "average-score": null,
        "public-amount-atomic": 3000000000000,
        "public-currency-holding-id": 53
      }
    },
    {
      "id": "60",
      "type": "currencies",
      "attributes": {
        "issuer-id": 3,
        "issuer-user-id": 3,
        "issuer-user-name": "Hannibal",
        "issuer-user-avatar-url": "/system/users/avatars/000/000/003/original/avatar.jpg?1562578009",
        "issuer-public-currency-holding-id": 50,
        "burn-rate": 500,
        "daily-burn-rate": "0.00014052",
        "store-count": 0,
        "listing-count": 0,
        "product-count": 0,
        "name": "Hoola Hoop Cash",
        "description": "Hoola hoop cash is redeemable for hoola hoop branded clothing",
        "created-at": "2019-07-08T02:31:29.667-07:00",
        "updated-at": "2019-07-14T13:16:22.734-07:00",
        "get-icon-url": "/system/currencies/icons/000/000/060/original/currency.jpg?1562578289",
        "number-of-reviews": 0,
        "average-score": null,
        "public-amount-atomic": 2400000000000,
        "public-currency-holding-id": 50
      }
    },
    {
      "id": "1",
      "type": "currencies",
      "attributes": {
        "issuer-id": 3,
        "issuer-user-id": 3,
        "issuer-user-name": "Hannibal",
        "issuer-user-avatar-url": "/system/users/avatars/000/000/003/original/avatar.jpg?1562578009",
        "issuer-public-currency-holding-id": 2,
        "burn-rate": 450,
        "daily-burn-rate": "0.00012614",
        "store-count": 2,
        "listing-count": 0,
        "product-count": 19,
        "name": "Micro Asteroid bucks",
        "description": "credit toward asteroid mining missions",
        "created-at": "2018-11-05T02:19:23.338-08:00",
        "updated-at": "2019-07-14T13:13:50.979-07:00",
        "get-icon-url": "/system/currencies/icons/missing.png",
        "number-of-reviews": 1,
        "average-score": "4.29",
        "public-amount-atomic": 3599957849922,
        "public-currency-holding-id": 2
      }
    }
  ],
  "links": {
    "self": "https://api.mycurrency.com/currencies?user_id=3",
    "first": "https://api.mycurrency.com/currencies?page=1&per_page=25&user_id=3",
    "prev": null,
    "next": null,
    "last": "https://api.mycurrency.com/currencies?page=1&per_page=25&user_id=3"
  },
  "meta": {
    "pagination": {
      "per-page": null,
      "total-pages": "1",
      "total-count": "4"
    }
  }
}
```

This endpoint retrieves all currencies belonging to the user associated with the ID provided, sorted by ID in descending order.

### HTTP Request

`GET https://api.mycurrency.com/currencies?user_id={}`

<aside class="notice">
Authentication: not required
</aside>

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the currency
issuer-id | The ID of the issuer account that issued the currency
issuer-user-id | The ID of the user account that issued the currency
issuer-user-username | The ID of the user account that issued the currency
issuer-user-avatar-url | The URL at which the avatar picture of the user that issues the currency can be found
issuer-public-currency-holding-id | The user ID of the public currency holding of the issuer of the currency
burn-rate | The annual rate at which holdings of the currency burn, by basis point (100 = 1%) 
daily-burn-rate | The daily rate at which the currency burns, by fraction of 1 (0.01 = 1%)
store-count | The number of stores associated with the currency
listing-count | The number of active listings associated with the currency
product-count | The number of products associated with the currency
name | The name of the currency
description | The description of the currency
created-at | The time and date when the currency was created
updated-at | The time and date when the currency was last updated
get-icon-url | The URL at which the currency icon picture can be found
number-of-reviews | The number of store reviews created for the store
average-score | The average score of the store reviews created for all stores associated with the currency, out of 5
public-amount-atomic | The amount held in the logged-in user's public holding of the specified currency, in atomic units (each whole unit is composed of 10^10 atomic units)
public-currency-holding-id | The ID of the logged-in user's public holding of the specified currency

## Search Currencies

```shell
curl "https://api.mycurrency.com/search_currencies?keyword=ACME%20Toon" \
  -H 'Host: api.mycurrency.com' \
  -H 'Accept: application/json' \
  -H 'Content-Type: application/json'
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": "2",
      "type": "currencies",
      "attributes": {
        "issuer-id": 2,
        "issuer-user-id": 3,
        "issuer-user-username": "Hannibal",
        "issuer-user-avatar-url": "/system/users/avatars/000/000/004/original/1.jpg?1559736060",
        "issuer-public-currency-holding-id": 4,
        "burn-rate": 450,
        "daily-burn-rate": "0.00012614",
        "store-count": 2,
        "listing-count": 5,
        "product-count": 52,
        "name": "ACME Toon Shop dollars",
        "description": "Spendable at any ACME Toon Shop",
        "created-at": "2018-08-12T01:17:31.176-07:00",
        "updated-at": "2018-08-12T23:49:56.793-07:00",
        "get-icon-url": "/system/currencies/icons/000/000/002/original/DaffyDuck.png?1534142996"
        "number-of-reviews": 5,
        "average-score": "3.67"
        "public-amount-atomic": 0,
        "public-currency-holding-id": null
      }
    }
  ],
  "links": {
    "self": "https://api.mycurrency.com/search_currencies?keyword=ACME%20Toon",
    "first": "https://api.mycurrency.com/search_currencies?keyword=ACME%20Toon&page=1&per_page=25",
    "prev": null,
    "next": null,
    "last": "https://api.mycurrency.com/search_currencies?keyword=ACME%20Toon&page=1&per_page=25"
  },
  "meta": {
    "pagination": {
      "per-page": null,
      "total-pages": "1",
      "total-count": "1"
    }
  }
}
```

This endpoint retrieves all currencies that have an active owner that have a name that contains text that matches the search keyword provided, sorted by ID in descending order.

### HTTP Request

`GET https://api.mycurrency.com/search_currencies?keyword={}`

<aside class="notice">
Authentication: required
</aside>

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the currency
issuer-id | The ID of the issuer account that issued the currency
issuer-user-id | The ID of the user account that issued the currency
issuer-user-username | The ID of the user account that issued the currency
issuer-user-avatar-url | The URL at which the avatar picture of the user that issues the currency can be found
issuer-public-currency-holding-id | The user ID of the public currency holding of the issuer of the currency
burn-rate | The annual rate at which holdings of the currency burn, by basis point (100 = 1%) 
daily-burn-rate | The daily rate at which the currency burns, by fraction of 1 (0.01 = 1%)
store-count | The number of stores associated with the currency
listing-count | The number of active listings associated with the currency
product-count | The number of products associated with the currency
name | The name of the currency
description | The description of the currency
created-at | The time and date when the currency was created
updated-at | The time and date when the currency was last updated
get-icon-url | The URL at which the currency icon picture can be found
number-of-reviews | The number of store reviews created for the store
average-score | The average score of the store reviews created for all stores associated with the currency, out of 5
public-amount-atomic | The amount held in the logged-in user's public holding of the specified currency, in atomic units (each whole unit is composed of 10^10 atomic units)
public-currency-holding-id | The ID of the logged-in user's public holding of the specified currency

## Create Currency

```shell
curl -X POST https://api.mycurrency.com/users/2/issuer/currencies \
  -d '{"currency": { "burn_rate": 740, "name": "Calm dollars", "description": "Redeemable for services at Calm Massage Therapy" } }' \
  -H 'Authorization: Bearer j47lbjj8r9n5yy8mup6cxqc8h70yvhnilm0g84kg0raqckus0k1koj9f75ao' \
  -H 'Accept: application/json' -H 'Content-Type: application/json'
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "id": "1",
    "type": "currencies",
    "attributes": {
      "issuer-id": 3,
      "issuer-user-id": 3,
      "issuer-user-name": "Hannibal",
      "issuer-user-avatar-url": "/avatars/original/missing.png",
      "issuer-public-currency-holding-id": 3,
      "burn-rate": 500,
      "daily-burn-rate": "0.00014052",
      "store-count": 1,
      "listing-count": 0,
      "product-count": 0,
      "name": "Micro Asteroid bucks",
      "description": "credit toward asteroid mining missions",
      "created-at": "2018-11-05T02:19:23.338-08:00",
      "updated-at": "2018-11-05T02:19:23.338-08:00",
      "get-icon-url": "/icons/original/missing.png",
      "number-of-reviews": 0,
      "average-score": null 
    }
  }
}
```

Creates a currency.

### HTTP Request

`POST https://api.mycurrency.com/users/<USER-ID>/issuer/currencies`

<aside class="notice">
Authentication: the request requires the OAuth access-token associated with the User referenced by the ID 
</aside>

### ARGUMENTS

Parameter | Type | Required | Description
--------- | ------- | ------- | -----------
burn_rate | integer | yes | The annual rate at which holdings of the currency burn, by basis point (100 = 1%)
name | string | yes |  The name of the currency
description | string | no | The description of the currency
icon | filename | no | The image file to be uploaded as currency's icon picture

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the currency
issuer-id | The ID of the issuer account that issued the currency
issuer-user-id | The ID of the user account that issued the currency
issuer-user-username | The ID of the user account that issued the currency
issuer-user-avatar-url | The URL at which the avatar picture of the user that issues the currency can be found
issuer-public-currency-holding-id | The user ID of the public currency holding of the issuer of the currency
burn-rate | The annual rate at which holdings of the currency burn, by basis point (100 = 1%) 
daily-burn-rate | The daily rate at which the currency burns, by fraction of 1 (0.01 = 1%)
store-count | The number of stores associated with the currency
listing-count | The number of active listings associated with the currency
name | The name of the currency
description | The description of the currency
created-at | The time and date when the currency was created
updated-at | The time and date when the currency was last updated
get-icon-url | The URL at which the currency icon picture can be found
number-of-reviews | The number of store reviews created for the store
average-score | The average score of the store reviews, out of 5

## Update Currency

```shell
curl -X PUT https://api.mycurrency.com/users/2/issuer/currencies/1 \
  -F 'currency[icon]=@calm_dollars.jpg' \
  -H 'Authorization: Bearer j47lbjj8r9n5yy8mup6cxqc8h70yvhnilm0g84kg0raqckus0k1koj9f75ao' \
  -H 'Accept: application/json' -H 'Content-Type: multipart/form-data'
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "id":"1",
    "type":"currencies",
    "attributes": {
      "issuer-id": 3,
      "issuer-user-id": 3,
      "issuer-user-name": "Hannibal",
      "issuer-user-avatar-url": "/avatars/original/missing.png",
      "issuer-public-currency-holding-id": 3,
      "burn-rate": 500,
      "daily-burn-rate": "0.00014052",
      "store-count": 1,
      "listing-count": 0,
      "product-count": 0,
      "name": "Micro Asteroid bucks",
      "description": "credit toward asteroid mining missions",
      "created-at": "2018-11-05T02:19:23.338-08:00",
      "updated-at": "2018-11-05T02:19:23.338-08:00",
      "get-icon-url": "/system/currencies/icons/000/000/001/original/calm_dollars.jpg?1514241100"
      "number-of-reviews": 0,
      "average-score": null
    }
  }
}
```

Updates a currency.

### HTTP Request

`PUT https://api.mycurrency.com/users/<USER-ID>/issuer/currencies/<ID>`

<aside class="notice">
Authentication: the request requires the OAuth access-token associated with the User referenced by the ID 
</aside>

### ARGUMENTS

Parameter | Type | Required | Description
--------- | ------- | ------- | -----------
description | string | no | The description of the currency
icon | filename | no | The image file to be uploaded as currency's icon picture

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the currency
issuer-id | The ID of the issuer account that issued the currency
issuer-user-id | The ID of the user account that issued the currency
issuer-user-username | The ID of the user account that issued the currency
issuer-user-avatar-url | The URL at which the avatar picture of the user that issues the currency can be found
issuer-public-currency-holding-id | The user ID of the public currency holding of the issuer of the currency
burn-rate | The annual rate at which holdings of the currency burn, by basis point (100 = 1%) 
daily-burn-rate | The daily rate at which the currency burns, by fraction of 1 (0.01 = 1%)
store-count | The number of stores associated with the currency
listing-count | The number of active listings associated with the currency
name | The name of the currency
description | The description of the currency
created-at | The time and date when the currency was created
updated-at | The time and date when the currency was last updated
get-icon-url | The URL at which the currency icon picture can be found
number-of-reviews | The number of store reviews created for the store
average-score | The average score of the store reviews, out of 5

# Burnrate Change

## Get a Burnrate Change

```shell
curl "https://api.mycurrency.com/currencies/1/burnrate_changes/1" \
  -H 'Host: api.mycurrency.com' \
  -H 'Accept: application/json' \
  -H 'Content-Type: application/json'
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "id":"1",
    "type":"burnrate-changes",
    "attributes": {
      "old-burn-rate": 740,
      "new-burn-rate": 500,
      "currency-id": 1,
      "comment": "lowering the burn rate",
      "created-at":"2018-08-19T17:00:50.093-07:00",
      "updated-at":"2018-08-19T17:00:50.093-07:00"
    }
  }
}
```

This endpoint retrieves a particular burnrate change by ID.

### HTTP Request

`GET https://api.mycurrency.com/currencies/<CURRENCY-ID>/burnrate_changes/<ID>`

<aside class="notice">
Authentication: not required
</aside>

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the burnrate_change
old-burn-rate | The burn rate before the burnrate_change 
new-burn-rate | The burn rate after the burnrate_change name
currency-id | The ID of the currency that the burnrate_change applies to
comment | A comment to explain to currency holders why the burn rate was changed
created-at | The time and date when the currency was created
updated-at | The time and date when the currency was last updated

## List Burnrate Changes

```shell
curl "https://api.mycurrency.com/currencies/1/burnrate_changes" \
  -H 'Host: api.mycurrency.com' \
  -H 'Accept: application/json' \
  -H 'Content-Type: application/json'
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": "3",
      "type": "burnrate-changes",
      "attributes": {
        "old-burn-rate": 580,
        "new-burn-rate": 600,
        "currency-id": 1,
        "comment": "a slight increase in burn rate",
        "created-at": "2018-08-22T09:54:07.685-07:00",
        "updated-at": "2018-08-22T09:54:07.685-07:00"
      }
    },
    {
      "id": "2",
      "type": "burnrate-changes",
      "attributes": {
        "old-burn-rate": 500,
        "new-burn-rate": 580,
        "currency-id": 1,
        "comment": "increasing the burn rate",
        "created-at": "2018-08-20T12:27:48.716-07:00",
        "updated-at": "2018-08-20T12:27:48.716-07:00"
      }
    },
    {
      "id":"1",
      "type":"burnrate-changes",
      "attributes": {
        "old-burn-rate": 740,
        "new-burn-rate": 500,
        "currency-id": 1,
        "comment": "lowering the burn rate",
        "created-at":"2018-08-19T17:00:50.093-07:00",
        "updated-at":"2018-08-19T17:00:50.093-07:00"
    }
  ],
  "links": {
    "self": "http://api.mycurrency.com/currencies/1/burnrate_changes?",
    "first": "http://api.mycurrency.com/currencies/1/burnrate_changes?page=1&per_page=25",
    "prev": null,
    "next": null,
    "last": "http://api.mycurrency.com/currencies/1/burnrate_changes?page=1&per_page=25"
  },
  "meta": {
    "pagination": {
      "per-page": null,
      "total-pages": "1",
      "total-count": "3"
    }
  }
}
```

This endpoint retrieves all of the specified currency's burnrate changes, sorted by created_at date, starting from the most recent

### HTTP Request

`GET https://api.mycurrency.com/currencies/<CURRENCY-ID>/burnrate_changes`

<aside class="notice">
Authentication: not required
</aside>

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the burnrate_change
old-burn-rate | The burn rate before the burnrate_change 
new-burn-rate | The burn rate after the burnrate_change name 
currency-id | The ID of the currency that the burnrate_change applies to
comment | A comment to explain to currency holders why the burn rate was changed
created-at | The time and date when the currency was created
updated-at | The time and date when the currency was last updated

## Update Currency's Burn Rate

```shell
curl -X POST https://api.mycurrency.com/currencies/1/burnrate_change \
  -d '{"burnrate_change": { "new_burn_rate": 500, "comment": "lowing the burn rate" } }' \
  -H 'Authorization: Bearer j47lbjj8r9n5yy8mup6cxqc8h70yvhnilm0g84kg0raqckus0k1koj9f75ao' \
  -H 'Accept: application/json' \
  -H 'Content-Type: application/json'
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "id":"1",
    "type":"burnrate-changes",
    "attributes": {
      "old-burn-rate": 740,
      "new-burn-rate": 500,
      "currency-id": 1,
      "comment": "lowering the burn rate",
      "created-at":"2018-08-19T17:00:50.093-07:00",
      "updated-at":"2018-08-19T17:00:50.093-07:00"
    }
  }
}
```

Updating a currency's burn rate requires accessing the `burnrate_change` endpoint and creating a burnrate change record. Burnrate change records create an auditable and publicly accessible log of changes to a currency's burn rate.

### HTTP Request

`POST https://api.mycurrency.com/currencies/<CURRENCY-ID>/burnrate_change`

<aside class="notice">
Authentication: the request requires the OAuth access-token associated with the User that issued the currency being updated 
</aside>

### ARGUMENTS

Parameter | Type | Required | Description
--------- | ------- | ------- | -----------
new_burn_rate | integer | yes | The value that you want to update the currency's burn rate to, maximum value of 2,000 basis points, or 20 percent
comment | string | no | A comment to explain to currency holders why the burn rate was changed

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the burnrate_change
old-burn-rate | The burn rate before the burnrate_change 
new-burn-rate | The burn rate after the burnrate_change name 
currency-id | The ID of the currency that the burnrate_change applies to
comment | A comment to explain to currency holders why the burn rate was changed
created-at | The time and date when the currency was created
updated-at | The time and date when the currency was last updated

# Stores

## Get a Store

```shell
curl 'https://api.mycurrency.com/stores/2' \
  -H 'Accept: application/json' -H 'Content-Type: application/json'
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "id": "2",
    "type": "stores",
    "attributes": {
      "number-of-reviews": 3
      "average-score": "3.67",
      "number-of-products": 1,
      "number-of-product-cancellations": 3,
      "owner-id": 3,
      "owner-username": "Hannibal",
      "owner-avatar-url": "/system/users/avatars/000/000/004/original/1.jpg?1559736060",
      "issuer-public-currency-holding-id": 4,
      "currency-id": 2,
      "currency-name": "ACME Toon Shop dollars"
      "currency-icon-url": "/system/currencies/icons/000/000/002/original/DaffyDuck.png?1534142996"
      "sub-location-id": 2,
      "sub-location-name": "Vancouver",
      "mid-location-id": 1,
      "mid-location-name": "British Columbia",
      "can-be-deleted": false,
      "physical": true,
      "store-name": "Vancouver ACME Toon Shop",
      "store-description": "All manner of ACME Toon items available",
      "index": "Vancouver ACME Toon Shop All manner of ACME Toon items available\nBugs Bunny Q-Tips - q-tips that work on the biggest ears, Fictional items, Toon products - 1550\n",
      "created-at": "2018-08-12T02:11:46.512-07:00",
      "updated-at": "2018-08-12T02:11:46.512-07:00"
    }
  }
}
```

This endpoint retrieves a particular store.

### HTTP Request

`GET https://api.mycurrency.com/stores/<ID>`

<aside class="notice">
Authentication: not required
</aside>

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the store
number-of-reviews | The number of store reviews created for the store
average-score | The average score of the store reviews, out of 5
number-of-products | The number of products belonging to the store where both the :active and :continued fields have a value of true
number-of-product-cancellations | The number of products belonging to the store that have been discontinued without the store owner providing advance notice
owner-id | The ID of the user that owns the store
owner-username | The username of the user that owns the store
owner-avatar-url | The URL of the avatar of the user that owns the store
issuer-public-currency-holding-id | The user ID of the public currency holding of the issuer of the currency that the store's products are purchasable with
currency-id | The ID of the currency that the store's products are purchasable with
currency-name | The name of the currency that the store's products are purchasable with
currency-icon-url | The URL of the icon of the currency that the store's products are purchasable with
sub-location-id | The sub location where the store is located
sub-location-name | The name of the sub location where the store is located
mid-location-id | The mid location where the store is located
mid-location-name | The name of the mid location where the store is located
can-be-deleted | Whether the store can be deleted. Stores with one or more products that have both their :active and :continued attributes set to true cannot be deleted. The owning user must deactivate or cancel the store's products first.
physical | Whether the store is a physical location that customers can visit
store-name | The name of the store
store-description | The description of the store
index | Keywords derived from the description of the store and its products that are checked against in searches
created-at | The time and date when the currency was created
updated-at | The time and date when the currency was last updated

## List Stores

```shell
curl "https://api.mycurrency.com/stores" \
  -H 'Host: api.mycurrency.com' \
  -H 'Accept: application/json' \
  -H 'Content-Type: application/json'
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": "3",
      "type": "stores",
      "attributes": {
        "number-of-reviews": 0
        "average-score": null,
        "number-of-products": 2,
        "number-of-product-cancellations": 0,
        "issuer-public-currency-holding-id": 4,
        "currency-id": 2,
        "currency-name": "ACME Toon Shop dollars",
        "currency-icon-url": "/system/currencies/icons/000/000/002/original/DaffyDuck.png?1534142996",
        "sub-location-id": 1,
        "sub-location-name": "San Francisco",
        "mid-location-id": "2",
        "mid-location-name": "California",
        "can-be-deleted": false,
        "physical": true,
        "store-name": "San Francisco ACME Toon Shop",
        "store-description": "San Francisco's premier shop for toons",
        "index": "San Francisco ACME Toon Shop San Francisco's premier shop for toons\nBugs Bunny Q-Tips - q-tips that work on the biggest ears, Toon products, products usable by toons - 1550\nTeleport hole - can turn any rock face into a tunnel, Toon products, products usable by toons - 4000\n",
        "created-at": "2018-08-12T02:11:46.512-07:00",
        "updated-at": "2018-08-12T02:11:46.512-07:00"
      }
    },
    {
      "id": "2",
      "type": "stores",
      "attributes": {
        "number-of-reviews": 3
        "average-score": "3.67",
        "number-of-products": 1,
        "number-of-product-cancellations": 3 
        "issuer-public-currency-holding-id": 4,
        "currency-id": 2,
        "currency-name": "ACME Toon Shop dollars"
        "currency-icon-url": "/system/currencies/icons/000/000/002/original/DaffyDuck.png?1534142996",
        "sub-location-id": 2,
        "sub-location-name": "Vancouver",
        "mid-location-id": 1,
        "mid-location-name": "British Columbia",
        "can-be-deleted": false,
        "physical": true,
        "store-name": "Vancouver ACME Toon Shop",
        "store-description": "All manner of ACME Toon items available",
        "index": "Vancouver ACME Toon Shop All manner of ACME Toon items available\nBugs Bunny Q-Tips - q-tips that work on the biggest ears, Fictional items, Toon products - 1550\n",
        "created-at": "2018-08-12T02:11:46.512-07:00",
        "updated-at": "2018-08-12T02:11:46.512-07:00"
      }
    },
    {
      "id": "1",
      "type": "stores",
      "attributes": {
        "number-of-reviews": 0
        "average-score": null,
        "number-of-products": 1,
        "number-of-product-cancellations": 0,
        "issuer-public-currency-holding-id": 2,
        "currency-id": 1,
        "currency-name": "Calm dollars",
        "currency-icon-url": "/system/currencies/icons/000/000/001/original/calm_dollars.jpg?1534619841",
        "sub-location-id": 1,
        "sub-location-name": "San Francisco",
        "mid-location-id": "2",
        "mid-location-name": "California",
        "can-be-deleted": false,
        "physical": true,
        "store-name": "Calm Spa",
        "store-description": "A full service spa for full relaxation",
        "index": "Calm Spa A full service spa for full relaxation\nFacial - standard facial, spa services, includes facials, manicures and pedicures - 5000\n",
        "created-at": "2018-08-11T12:11:16.475-07:00",
        "updated-at": "2018-08-12T02:21:49.458-07:00"
      }
    }
  ],
  "links": {
    "self": "http://api.mycurrency.com/stores?",
    "first": "http://api.mycurrency.com/stores?page=1&per_page=25",
    "prev": null,
    "next": null,
    "last": "http://api.mycurrency.com/stores?page=1&per_page=25"
  },
  "meta": {
    "pagination": {
      "per-page": null,
      "total-pages": "1",
      "total-count": "3"
    }
  }
}
```

This endpoint retrieves all stores that have an active owner, sorted by ID in descending order.

### HTTP Request

`GET https://api.mycurrency.com/stores`

<aside class="notice">
Authentication: not required
</aside>

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the store
number-of-reviews | The number of store reviews created for the store
average-score | The average score of the store reviews, out of 5
number-of-products | The number of products belonging to the store where both the :active and :continued fields have a value of true
number-of-product-cancellations | The number of products belonging to the store that have been discontinued without the store owner providing advance notice
owner-id | The ID of the user that owns the store
owner-username | The username of the user that owns the store
owner-avatar-url | The URL of the avatar of the user that owns the store
issuer-public-currency-holding-id | The user ID of the public currency holding of the issuer of the currency that the store's products are purchasable with
currency-id | The ID of the currency that the store's products are purchasable with
currency-name | The name of the currency that the store's products are purchasable with
currency-icon-url | The URL of the icon of the currency that the store's products are purchasable with
sub-location-id | The sub location where the store is located
sub-location-name | The name of the sub location where the store is located
mid-location-id | The mid location where the store is located
mid-location-name | The name of the mid location where the store is located
can-be-deleted | Whether the store can be deleted. Stores with one or more products that have both their :active and :continued attributes set to true cannot be deleted. The owning user must deactivate or cancel the store's products first.
physical | Whether the store is a physical location that customers can visit
store-name | The name of the store
store-description | The description of the store
index | Keywords derived from the description of the store and its products that are checked against in searches
created-at | The time and date when the currency was created
updated-at | The time and date when the currency was last updated

## List a User's Stores

```shell
curl "https://api.mycurrency.com/users/4/stores" \
  -H 'Host: api.mycurrency.com' \
  -H 'Accept: application/json' \
  -H 'Content-Type: application/json'
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": "4",
      "type": "stores",
      "attributes": {
        "number-of-reviews": 0,
        "average-score": null,
        "number-of-products": 0,
        "number-of-product-cancellations": 0,
        "issuer-public-currency-holding-id": 3,
        "currency-id": 3,
        "currency-name": "Moon hotel coins",
        "currency-icon-url": "/icons/original/missing.png",
        "sub-location-id": 45,
        "sub-location-name": "san francisco bay area",
        "mid-location-id": 5,
        "mid-location-name": "California",
        "can-be-deleted": true,
        "physical": false,
        "store-name": "Moon Hotel",
        "store-description": "situated on the edge of the Sea of Tranquility",
        "index": "Moon Hotel situated on the edge of the Sea of Tranquility",
        "created-at": "2019-02-05T16:19:54.194-08:00",
        "updated-at": "2019-02-05T16:19:54.194-08:00"
      }
    },
    {
      "id": "3",
      "type": "stores",
      "attributes": {
        "number-of-reviews": 0,
        "average-score": null,
        "number-of-products": 0,
        "number-of-product-cancellations": 0,
        "issuer-public-currency-holding-id": 4,
        "currency-id": 2,
        "currency-name": "solar electricity zaps",
        "currency-icon-url": "/icons/original/missing.png",
        "sub-location-id": 45,
        "sub-location-name": "san francisco bay area",
        "mid-location-id": 5,
        "mid-location-name": "California",
        "can-be-deleted": true,
        "physical": true,
        "store-name": "San Fran Solar Zap",
        "store-description": "San Francisco's premium solar electricity source",
        "index": "San Fran Solar Zap San Francisco's premium solar electricity source",
        "created-at": "2019-02-05T16:16:48.844-08:00",
        "updated-at": "2019-02-05T16:29:05.167-08:00"
      }
    },
    {
      "id": "2",
      "type": "stores",
      "attributes": {
        "number-of-reviews": 0,
        "average-score": null,
        "number-of-products": 0,
        "number-of-product-cancellations": 0,
        "issuer-public-currency-holding-id": 4,
        "currency-id": 2,
        "currency-name": "solar electricity zaps",
        "currency-icon-url": "/icons/original/missing.png",
        "sub-location-id": 436,
        "sub-location-name": "vancouver",
        "mid-location-id": 54,
        "mid-location-name": "British Columbia",
        "can-be-deleted": true,
        "physical": true,
        "store-name": "Vancouver Solar Zap",
        "store-description": "Vancouver's premium solar electricity source",
        "index": "Vancouver Solar Zap Vancouver's premium solar electricity source",
        "created-at": "2019-02-05T16:14:24.041-08:00",
        "updated-at": "2019-02-05T16:28:54.269-08:00"
      }
    }
  ],
  "links": {
    "self": "https://api.mycurrency.com/users/4/stores?",
    "first": "https://api.mycurrency.com/users/4/stores?page=1&per_page=25",
    "prev": null,
    "next": null,
    "last": "https://api.mycurrency.com/users/4/stores?page=1&per_page=25"
  },
  "meta": {
    "pagination": {
      "per-page": null,
      "total-pages": "1",
      "total-count": "3"
    }
  }
}
```

This endpoint retrieves all stores belonging to the user associated with the ID provided, sorted by ID in descending order.

### HTTP Request

`GET https://api.mycurrency.com/users/<USER-ID>/stores`

<aside class="notice">
Authentication: not required
</aside>

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the store
number-of-reviews | The number of store reviews created for the store
average-score | The average score of the store reviews, out of 5
number-of-products | The number of products belonging to the store where both the :active and :continued fields have a value of true
number-of-product-cancellations | The number of products belonging to the store that have been discontinued without the store owner providing advance notice
owner-id | The ID of the user that owns the store
owner-username | The username of the user that owns the store
owner-avatar-url | The URL of the avatar of the user that owns the store
issuer-public-currency-holding-id | The user ID of the public currency holding of the issuer of the currency that the store's products are purchasable with
currency-id | The ID of the currency that the store's products are purchasable with
currency-name | The name of the currency that the store's products are purchasable with
currency-icon-url | The URL of the icon of the currency that the store's products are purchasable with
sub-location-id | The sub location where the store is located
sub-location-name | The name of the sub location where the store is located
mid-location-id | The mid location where the store is located
mid-location-name | The name of the mid location where the store is located
can-be-deleted | Whether the store can be deleted. Stores with one or more products that have both their :active and :continued attributes set to true cannot be deleted. The owning user must deactivate or cancel the store's products first.
physical | Whether the store is a physical location that customers can visit
store-name | The name of the store
store-description | The description of the store
index | Keywords derived from the description of the store and its products that are checked against in searches
created-at | The time and date when the currency was created
updated-at | The time and date when the currency was last updated

## List a Currency's Stores

```shell
curl "https://api.mycurrency.com/currencies/2/stores" \
  -H 'Host: api.mycurrency.com' \
  -H 'Accept: application/json' \
  -H 'Content-Type: application/json'
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": "3",
      "type": "stores",
      "attributes": {
        "number-of-reviews": 0
        "average-score": null,
        "number-of-products": 2,
        "number-of-product-cancellations": 0,
        "issuer-public-currency-holding-id": 4,
        "currency-id": 2,
        "currency-name": "ACME Toon Shop dollars",
        "currency-icon-url": "/system/currencies/icons/000/000/002/original/DaffyDuck.png?1534142996",
        "sub-location-id": 1,
        "sub-location-name": "San Francisco",
        "mid-location-id": "2",
        "mid-location-name": "California",
        "can-be-deleted": false,
        "physical": true,
        "store-name": "San Francisco ACME Toon Shop",
        "store-description": "San Francisco's premier shop for toons",
        "index": "San Francisco ACME Toon Shop San Francisco's premier shop for toons\nBugs Bunny Q-Tips - q-tips that work on the biggest ears, Toon products, products usable by toons - 1550\nTeleport hole - can turn any rock face into a tunnel, Toon products, products usable by toons - 4000\n",
        "created-at": "2018-08-12T02:11:46.512-07:00",
        "updated-at": "2018-08-12T02:11:46.512-07:00"
      }
    },
    {
      "id": "2",
      "type": "stores",
      "attributes": {
        "number-of-reviews": 3
        "average-score": "3.67",
        "number-of-products": 1,
        "number-of-product-cancellations": 3 
        "issuer-public-currency-holding-id": 4,
        "currency-id": 2,
        "currency-name": "ACME Toon Shop dollars"
        "currency-icon-url": "/system/currencies/icons/000/000/002/original/DaffyDuck.png?1534142996"
        "sub-location-id": 2,
        "sub-location-name": "Vancouver",
        "mid-location-id": 1,
        "mid-location-name": "British Columbia",
        "can-be-deleted": false,
        "physical": true,
        "store-name": "Vancouver ACME Toon Shop",
        "store-description": "All manner of ACME Toon items available",
        "index": "Vancouver ACME Toon Shop All manner of ACME Toon items available\nBugs Bunny Q-Tips - q-tips that work on the biggest ears, Fictional items, Toon products - 1550\n",
        "created-at": "2018-08-12T02:11:46.512-07:00",
        "updated-at": "2018-08-12T02:11:46.512-07:00"
      }
    }
  ],
  "links": {
    "self": "http://api.mycurrency.com/currencies/2/stores?",
    "first": "http://api.mycurrency.com/currencies/2/stores?page=1&per_page=25",
    "prev": null,
    "next": null,
    "last": "http://api.mycurrency.com/currencies/2/stores?page=1&per_page=25"
  },
  "meta": {
    "pagination": {
      "per-page": null,
      "total-pages": "1",
      "total-count": "2"
    }
  }
}
```

This endpoint retrieves all stores belonging to the currency associated with the ID provided, sorted by ID in descending order.

### HTTP Request

`GET https://api.mycurrency.com/currencies/<CURRENCY-ID>/stores`

<aside class="notice">
Authentication: not required
</aside>

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the store
number-of-reviews | The number of store reviews created for the store
average-score | The average score of the store reviews, out of 5
number-of-products | The number of products belonging to the store where both the :active and :continued fields have a value of true
number-of-product-cancellations | The number of products belonging to the store that have been discontinued without the store owner providing advance notice
owner-id | The ID of the user that owns the store
owner-username | The username of the user that owns the store
owner-avatar-url | The URL of the avatar of the user that owns the store
issuer-public-currency-holding-id | The user ID of the public currency holding of the issuer of the currency that the store's products are purchasable with
currency-id | The ID of the currency that the store's products are purchasable with
currency-name | The name of the currency that the store's products are purchasable with
currency-icon-url | The URL of the icon of the currency that the store's products are purchasable with
sub-location-id | The sub location where the store is located
sub-location-name | The name of the sub location where the store is located
mid-location-id | The mid location where the store is located
mid-location-name | The name of the mid location where the store is located
can-be-deleted | Whether the store can be deleted. Stores with one or more products that have both their :active and :continued attributes set to true cannot be deleted. The owning user must deactivate or cancel the store's products first.
physical | Whether the store is a physical location that customers can visit
store-name | The name of the store
store-description | The description of the store
index | Keywords derived from the description of the store and its products that are checked against in searches
created-at | The time and date when the currency was created
updated-at | The time and date when the currency was last updated

## Search Stores by Keywords

```shell
curl "https://api.mycurrency.com/stores?keyword=spa%20services" \
  -H 'Host: api.mycurrency.com' \
  -H 'Accept: application/json' \
  -H 'Content-Type: application/json'
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": "1",
      "type": "stores",
      "attributes": {
        "number-of-reviews": 0
        "average-score": null,
        "number-of-products": 1,
        "number-of-product-cancellations": 0,
        "issuer-public-currency-holding-id": 2,
        "currency-id": 1,
        "currency-name": "Calm dollars",
        "currency-icon-url": "/system/currencies/icons/000/000/001/original/calm_dollars.jpg?1534619841",
        "sub-location-id": 1,
        "sub-location-name": "San Francisco",
        "mid-location-id": "2",
        "mid-location-name": "California",
        "can-be-deleted": false,
        "physical": true,
        "store-name": "Calm Spa",
        "store-description": "A full service spa for full relaxation",
        "index": "Calm Spa A full service spa for full relaxation\nFacial - standard facial, spa services, includes facials, manicures and pedicures - 5000\n",
        "created-at": "2018-08-11T12:11:16.475-07:00",
        "updated-at": "2018-08-12T02:21:49.458-07:00"
      }
    }
  ],
  "links": {
    "self": "https://api.mycurrency.com/stores?keyword=spa+services",
    "first": "https://api.mycurrency.com/stores?keyword=spa+services&page=1&per_page=25",
    "prev": null,
    "next": null,
    "last": "https://api.mycurrency.com/stores?keyword=spa+services&page=1&per_page=25"
  },
  "meta": {
    "pagination": {
      "per-page": null,
      "total-pages": "1",
      "total-count": "1"
    }
  }
}
```

This endpoint retrieves all stores that have an active owner that have an index that contains text that matches the search keyword provided, sorted by ID in descending order.

### HTTP Request

`GET https://api.mycurrency.com/stores?keyword={}`

<aside class="notice">
Authentication: not required
</aside>

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the store
number-of-reviews | The number of store reviews created for the store
average-score | The average score of the store reviews, out of 5
number-of-products | The number of products belonging to the store where both the :active and :continued fields have a value of true
number-of-product-cancellations | The number of products belonging to the store that have been discontinued without the store owner providing advance notice
owner-id | The ID of the user that owns the store
owner-username | The username of the user that owns the store
owner-avatar-url | The URL of the avatar of the user that owns the store
issuer-public-currency-holding-id | The user ID of the public currency holding of the issuer of the currency that the store's products are purchasable with
currency-id | The ID of the currency that the store's products are purchasable with
currency-name | The name of the currency that the store's products are purchasable with
currency-icon-url | The URL of the icon of the currency that the store's products are purchasable with
sub-location-id | The sub location where the store is located
sub-location-name | The name of the sub location where the store is located
mid-location-id | The mid location where the store is located
mid-location-name | The name of the mid location where the store is located
can-be-deleted | Whether the store can be deleted. Stores with one or more products that have both their :active and :continued attributes set to true cannot be deleted. The owning user must deactivate or cancel the store's products first.
physical | Whether the store is a physical location that customers can visit
store-name | The name of the store
store-description | The description of the store
index | Keywords derived from the description of the store and its products that are checked against in searches
created-at | The time and date when the currency was created
updated-at | The time and date when the currency was last updated

## List a Sub Location's Stores

```shell
curl "https://api.mycurrency.com/sub_locations/1/stores" \
  -H 'Host: api.mycurrency.com' \
  -H 'Accept: application/json' \
  -H 'Content-Type: application/json'
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": "3",
      "type": "stores",
      "attributes": {
        "number-of-reviews": 0
        "average-score": null,
        "number-of-products": 2,
        "number-of-product-cancellations": 0,
        "issuer-public-currency-holding-id": 4,
        "currency-id": 2,
        "currency-name": "ACME Toon Shop dollars",
        "currency-icon-url": "/system/currencies/icons/000/000/002/original/DaffyDuck.png?1534142996",
        "sub-location-id": 1,
        "sub-location-name": "San Francisco",
        "mid-location-id": "2",
        "mid-location-name": "California",
        "can-be-deleted": false,
        "physical": true,
        "store-name": "San Francisco ACME Toon Shop",
        "store-description": "San Francisco's premier shop for toons",
        "index": "San Francisco ACME Toon Shop San Francisco's premier shop for toons\nBugs Bunny Q-Tips - q-tips that work on the biggest ears, Toon products, products usable by toons - 1550\nTeleport hole - can turn any rock face into a tunnel, Toon products, products usable by toons - 4000\n",
        "created-at": "2018-08-12T02:11:46.512-07:00",
        "updated-at": "2018-08-12T02:11:46.512-07:00"
      }
    },
    {
      "id": "1",
      "type": "stores",
      "attributes": {
        "number-of-reviews": 0
        "average-score": null,
        "number-of-products": 1,
        "number-of-product-cancellations": 0,
        "issuer-public-currency-holding-id": 2,
        "currency-id": 1,
        "currency-name": "Calm dollars",
        "currency-icon-url": "/system/currencies/icons/000/000/001/original/calm_dollars.jpg?1534619841",
        "sub-location-id": 1,
        "sub-location-name": "San Francisco",
        "mid-location-id": "2",
        "mid-location-name": "California",
        "can-be-deleted": false,
        "physical": true,
        "store-name": "Calm Spa",
        "store-description": "A full service spa for full relaxation",
        "index": "Calm Spa A full service spa for full relaxation\nFacial - standard facial, spa services, includes facials, manicures and pedicures - 5000\n",
        "created-at": "2018-08-11T12:11:16.475-07:00",
        "updated-at": "2018-08-12T02:21:49.458-07:00"
      }
    }
  ],
  "links": {
    "self": "https://api.mycurrency.com/sub_locations/1/stores?",
    "first": "http://api.mycurrency.com/sub_locations/1/stores?page=1&per_page=25",
    "prev": null,
    "next": null,
    "last": "http://api.mycurrency.com/sub_locations/1/stores?page=1&per_page=25"
  },
  "meta": {
    "pagination": {
      "per-page": null,
      "total-pages": "1",
      "total-count": "2"
    }
  }
}
```

This endpoint retrieves all stores that have an active owner belonging to the sub location associated with the ID provided, sorted by ID in descending order.

### HTTP Request

`GET https://api.mycurrency.com/sub_locations/<SUB-LOCATION-ID>/stores`

<aside class="notice">
Authentication: not required
</aside>

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the store
number-of-reviews | The number of store reviews created for the store
average-score | The average score of the store reviews, out of 5
number-of-products | The number of products belonging to the store where both the :active and :continued fields have a value of true
number-of-product-cancellations | The number of products belonging to the store that have been discontinued without the store owner providing advance notice
owner-id | The ID of the user that owns the store
owner-username | The username of the user that owns the store
owner-avatar-url | The URL of the avatar of the user that owns the store
issuer-public-currency-holding-id | The user ID of the public currency holding of the issuer of the currency that the store's products are purchasable with
currency-id | The ID of the currency that the store's products are purchasable with
currency-name | The name of the currency that the store's products are purchasable with
currency-icon-url | The URL of the icon of the currency that the store's products are purchasable with
sub-location-id | The sub location where the store is located
sub-location-name | The name of the sub location where the store is located
mid-location-id | The mid location where the store is located
mid-location-name | The name of the mid location where the store is located
can-be-deleted | Whether the store can be deleted. Stores with one or more products that have both their :active and :continued attributes set to true cannot be deleted. The owning user must deactivate or cancel the store's products first.
physical | Whether the store is a physical location that customers can visit
store-name | The name of the store
store-description | The description of the store
index | Keywords derived from the description of the store and its products that are checked against in searches
created-at | The time and date when the currency was created
updated-at | The time and date when the currency was last updated

## Search a Sub Location's Stores by Keyword

```shell
curl "https://api.mycurrency.com/sub_locations/1/stores?keyword=Bugs%20Bunny" \
  -H 'Host: api.mycurrency.com' \
  -H 'Accept: application/json' \
  -H 'Content-Type: application/json'
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": "3",
      "type": "stores",
      "attributes": {
        "number-of-reviews": 0
        "average-score": null,
        "number-of-products": 2,
        "number-of-product-cancellations": 0,
        "issuer-public-currency-holding-id": 4,
        "currency-id": 2,
        "currency-name": "ACME Toon Shop dollars",
        "currency-icon-url": "/system/currencies/icons/000/000/002/original/DaffyDuck.png?1534142996",
        "sub-location-id": 1,
        "sub-location-name": "San Francisco",
        "mid-location-id": "2",
        "mid-location-name": "California",
        "can-be-deleted": false,
        "physical": true,
        "store-name": "San Francisco ACME Toon Shop",
        "store-description": "San Francisco's premier shop for toons",
        "index": "San Francisco ACME Toon Shop San Francisco's premier shop for toons\nBugs Bunny Q-Tips - q-tips that work on the biggest ears, Toon products, products usable by toons - 1550\nTeleport hole - can turn any rock face into a tunnel, Toon products, products usable by toons - 4000\n",
        "created-at": "2018-08-12T02:11:46.512-07:00",
        "updated-at": "2018-08-12T02:11:46.512-07:00"
      }
    }
  ],
  "links": {
    "self": "http://api.mycurrency.com/sub_locations/1/stores?keyword=Bugs+Bunny",
    "first": "http://api.mycurrency.com/sub_locations/1/stores?keyword=Bugs+Bunny&page=1&per_page=25",
    "prev": null,
    "next": null,
    "last": "http://api.mycurrency.com/sub_locations/1/stores?keyword=Bugs+Bunny&page=1&per_page=25"
  },
  "meta": {
    "pagination": {
      "per-page": null,
      "total-pages": "1",
      "total-count": "1"
    }
  }
}
```

This endpoint retrieves all stores that have an active owner that belong to the sub location associated with the ID provided and contain text that matches the search keyword provided, sorted by ID in descending order.

### HTTP Request

`GET https://api.mycurrency.com/sub_locations/<SUB-LOCATION-ID>/stores?keyword={}`

<aside class="notice">
Authentication: not required
</aside>

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the store
number-of-reviews | The number of store reviews created for the store
average-score | The average score of the store reviews, out of 5
number-of-products | The number of products belonging to the store where both the :active and :continued fields have a value of true
number-of-product-cancellations | The number of products belonging to the store that have been discontinued without the store owner providing advance notice
owner-id | The ID of the user that owns the store
owner-username | The username of the user that owns the store
owner-avatar-url | The URL of the avatar of the user that owns the store
issuer-public-currency-holding-id | The user ID of the public currency holding of the issuer of the currency that the store's products are purchasable with
currency-id | The ID of the currency that the store's products are purchasable with
currency-name | The name of the currency that the store's products are purchasable with
currency-icon-url | The URL of the icon of the currency that the store's products are purchasable with
sub-location-id | The sub location where the store is located
sub-location-name | The name of the sub location where the store is located
mid-location-id | The mid location where the store is located
mid-location-name | The name of the mid location where the store is located
can-be-deleted | Whether the store can be deleted. Stores with one or more products that have both their :active and :continued attributes set to true cannot be deleted. The owning user must deactivate or cancel the store's products first.
physical | Whether the store is a physical location that customers can visit
store-name | The name of the store
store-description | The description of the store
index | Keywords derived from the description of the store and its products that are checked against in searches
created-at | The time and date when the currency was created
updated-at | The time and date when the currency was last updated

## Create Store

```shell
curl -X POST https://api.mycurrency.com/users/4/issuer/currencies/5/stores \
  -d '{"store": { "store_name": "Freds Fishing Supplies", "store_description": "Fishing supply shop", "sub_location_id": "2", "physical": "true"} }' \
  -H 'Authorization: Bearer j47lbjj8r9n5yy8mup6cxqc8h70yvhnilm0g84kg0raqckus0k1koj9f75ao' 
  -H 'Accept: application/json' -H 'Content-Type: application/json'
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "id": "3",
    "type": "stores",
    "attributes": {
      "number-of-reviews": 0
      "average-score": null,
      "number-of-products": 0,
      "number-of-product-cancellations": 0,
      "issuer-public-currency-holding-id": 7,
      "currency-id": 5,
      "currency-name": "Chilli pesos",
      "currency-icon-url": "/system/currencies/icons/000/000/005/original/chilli-pesos.png?153414511"
      "sub-location-id": 2,
      "sub-location-name": "Vancouver",
      "mid-location-id": 1,
      "mid-location-name": "British Columbia",
      "can-be-deleted": true,
      "physical": true,
      "store-name": "Freds Fishing Supplies",
      "store-description": "Fishing supply shop",
      "index": "Freds Fishing Supplies Fishing supply shop",
      "created-at": "2018-08-26T16:09:40.080-07:00",
      "updated-at": "2018-08-26T16:09:40.080-07:00"
    }
  }
}
```

Creates a store.

### HTTP Request

`POST https://api.mycurrency.com/users/<USER-ID>/issuer/currencies/<CURRENCY-ID>/stores`

<aside class="notice">
Authentication: the request requires the OAuth access-token associated with the User referenced by the USER-ID 
</aside>

### ARGUMENTS

Parameter | Type | Required | Description
--------- | ------- | ------- | -----------
currency_id | integer | yes | The ID of the currency that the store's products are purchasable with, provided in URL path
sub_location_id | integer | yes | The sub location where the store is located
physical | boolean | yes | Whether the store is a physical location that customers can visit
store-name | string | yes | The name of the store
store-description | string | no | The description of the store

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the store
number-of-reviews | The number of store reviews created for the store
average-score | The average score of the store reviews, out of 5
number-of-products | The number of products belonging to the store where both the :active and :continued fields have a value of true
number-of-product-cancellations | The number of products belonging to the store that have been discontinued without the store owner providing advance notice
owner-id | The ID of the user that owns the store
owner-username | The username of the user that owns the store
owner-avatar-url | The URL of the avatar of the user that owns the store
issuer-public-currency-holding-id | The user ID of the public currency holding of the issuer of the currency that the store's products are purchasable with
currency-id | The ID of the currency that the store's products are purchasable with
currency-name | The name of the currency that the store's products are purchasable with
currency-icon-url | The URL of the icon of the currency that the store's products are purchasable with
sub-location-id | The sub location where the store is located
sub-location-name | The name of the sub location where the store is located
mid-location-id | The mid location where the store is located
mid-location-name | The name of the mid location where the store is located
can-be-deleted | Whether the store can be deleted. Stores with one or more products that have both their :active and :continued attributes set to true cannot be deleted. The owning user must deactivate or cancel the store's products first.
physical | Whether the store is a physical location that customers can visit
store-name | The name of the store
store-description | The description of the store
index | Keywords derived from the description of the store and its products that are checked against in searches
created-at | The time and date when the currency was created
updated-at | The time and date when the currency was last updated

## Update Store

```shell
curl -X PUT https://api.mycurrency.com/users/4/issuer/currencies/5/stores/3 \
  -d 'store[sub_location_id]=1&store[physical]=false&store[store_description]="The finest Fishing shop in San Francisco"' \   
  -H 'Authorization: Bearer j47lbjj8r9n5yy8mup6cxqc8h70yvhnilm0g84kg0raqckus0k1koj9f75ao' \
  -H 'Accept: application/json' \
  -H 'Content-Type: multipart/form-data'
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "id": "3",
    "type": "stores",
    "attributes": {
      "number-of-reviews": 0
      "average-score": null,
      "number-of-products": 0,
      "number-of-product-cancellations": 0,
      "issuer-public-currency-holding-id": 7,
      "currency-id": 5,
      "currency-name": "Chilli pesos",
      "currency-icon-url": "/system/currencies/icons/000/000/005/original/chilli-pesos.png?153414511"
      "sub-location-id": 1,
      "sub-location-name": "San Francisco",
      "mid-location-id": 2,
      "mid-location-name": "California",
      "can-be-deleted": true,
      "physical": false,
      "store-name": "Freds Fishing Supplies",
      "store-description": "The finest Fishing shop in San Francisco",
      "index": "Freds Fishing Supplies The finest fishing shop in San Francisco",
      "created-at": "2018-08-26T16:09:40.080-07:00",
      "updated-at": "2018-08-26T17:43:32.080-07:00"
    }
  }
}
```

Updates a store.

### HTTP Request

`PUT https://api.mycurrency.com/users/<USER-ID>/issuer/currencies/<CURRENCY-ID>/stores/<ID>`

<aside class="notice">
Authentication: the request requires the OAuth access-token associated with the User referenced by the USER-ID 
</aside>

### ARGUMENTS

Parameter | Type | Required | Description
--------- | ------- | ------- | -----------
store_id | integer | yes | The ID of the store that the product is sold, provided in URL path
sub_location_id | integer | yes | The sub location where the store is located
physical | integer | yes | Whether the store is a physical location that customers can visit
store_name | string | yes | The name of the store
store_description | string | no | The description of the product
active

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the store
number-of-reviews | The number of store reviews created for the store
average-score | The average score of the store reviews, out of 5
number-of-products | The number of products belonging to the store where both the :active and :continued fields have a value of true
number-of-product-cancellations | The number of products belonging to the store that have been discontinued without the store owner providing advance notice
issuer-public-currency-holding-id | The user ID of the public currency holding of the issuer of the currency that the store's products are purchasable with
currency-id | The ID of the currency that the store's products are purchasable with
currency-name | The name of the currency that the store's products are purchasable with
sub-location-id | The sub location where the store is located
sub-location-name | The name of the sub location where the store is located
mid-location-id | The mid location where the store is located
mid-location-name | The name of the mid location where the store is located
can-be-deleted | Whether the store can be deleted. Stores with one or more products that have both their :active and :continued attributes set to true cannot be deleted. The owning user must deactivate or cancel the store's products first.
physical | Whether the store is a physical location that customers can visit
store-name | The name of the store
store-description | The description of the store
index | Keywords derived from the description of the store and its products that are checked against in searches
created-at | The time and date when the currency was created
updated-at | The time and date when the currency was last updated

## Delete Store

```shell
curl -X DELETE https://api.mycurrency.com/users/2/issuer/currencies/2/stores/12 \
  -H 'Authorization: Bearer j47lbjj8r9n5yy8mup6cxqc8h70yvhnilm0g84kg0raqckus0k1koj9f75ao' \
  -H 'Accept: application/json' \
  -H 'Content-Type: multipart/form-data'
```

> The above command returns no JSON

Deletes a store. The user must deactivate or cancel all of their store's products before they can delete the store. If there are any products which have both their :active and :continued values set to true belonging to the store, the delete action will fail and an error message will be returned.

### HTTP Request

`DELETE https://api.mycurrency.com/users/<USER-ID>/issuer/currencies/<CURRENCY-ID>/stores/<ID>`

<aside class="notice">
Authentication: the request requires the OAuth access-token associated with the User referenced by the USER-ID 
</aside>

### RESPONSE

no response

# Store Reviews

## Get a Store Review

```shell
curl 'https://api.mycurrency.com/stores/1/store_reviews/1' \
  -H 'Accept: application/json' \
  -H 'Content-Type: application/json'
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "id": "1", 
    "type": "store-reviews",
    "attributes": {
      "store-id": 1,
      "user-id": 4,
      "comment": "Schrauder Export Consulting is one of the best business strategy consultancy's I've had the pleasure to use. They have a deep understanding of how to navigate the legal and commercial landscape to achieve international sales",
      "score": 4,
      "user-name": "ScipioAfricanus",
      "user-avatar-url": "/system/users/avatars/000/000/004/original/1.jpg?1559736060",
      "created-at": "2018-08-29T00:51:11.631-07:00",
    }
  }
}
```

This endpoint retrieves a particular store review.

### HTTP Request

`GET https://api.mycurrency.com/stores/<STORE-ID>/store_reviews/<ID>`

<aside class="notice">
Authentication: not required
</aside>

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the store review
store-id | The ID of the store that the store review relates to
comment | The written content of the review
score | A score between 0 and 5 (inclusive) by the store reviewer 
user-name | The user name of the store review author
user-avatar-url | The URL of the store review author's avatar
created-at | The time and date when the store review was created

## List Issuer's Received Store Reviews

```shell
curl "https://api.mycurrency.com/issuers/3/received_store_reviews" \
  -H 'Host: api.mycurrency.com' -H 'Accept: application/json' -H 'Content-Type: application/json'
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": "1",
      "type": "store-reviews",
      "attributes": {
        "store-id": 1,
        "user-id": 4,
        "comment": "Schrauder Export Consulting is one of the best business strategy consultancies I've had the pleasure to use. They have a deep understanding of how to navigate the legal and commercial landscape to achieve international sales",
        "score": 5,
        "user-name": "ScipioAfricanus",
        "user-avatar-url": "/system/users/avatars/000/000/004/original/1.jpg?1559736060",
        "created-at": "2018-08-29T00:51:11.631-07:00"
      }
    },
    {
      "id": "2",
      "type": "store-reviews",
      "attributes": {
        "store-id": 2,
        "user-id": 4,
        "comment": "Schrauder Japan knows the ins and outs of the Japanese import market. Their professionalism was impressive.",
        "score": 4,
        "user-name": "ScipioAfricanus",
        "user-avatar-url": "/system/users/avatars/000/000/004/original/1.jpg?1559736060",
        "created-at": "2018-08-29T22:11:23.788-07:00"
      }
    },
    {
      "id": "3",
      "type": "store-reviews",
      "attributes": {
        "store-id": 5,
        "user-id": 4,
        "comment": "I've been using McRyan's Grocers for about two years and am very happy with their growing selection of fresh fruits and vegetables",
        "score": 4,
        "user-name": "ScipioAfricanus",
        "user-avatar-url": "/system/users/avatars/000/000/004/original/1.jpg?1559736060",
        "created-at": "2018-08-29T22:15:34.052-07:00"
      }
    }
  ],
  "links": {
    "self": "https://api.mycurrency.com/issuers/3/received_store_reviews?",
    "first": "https://api.mycurrency.com/issuers/3/received_store_reviews?page=1&per_page=25",
    "prev": null,
    "next": null,
    "last": "https://api.mycurrency.com/issuers/3/received_store_reviews?page=1&per_page=25"
  },
  "meta": {
    "pagination": {
      "per-page": null,
      "total-pages": "1",
      "total-count": "3"
    }
  }
}
```

This endpoint retrieves all store reviews received by stores belonging to currencies associated with a particular issuer.

### HTTP Request

`GET https://api.mycurrency.com/issuers/<ISSUER-ID>/received_store_reviews`

OR

`GET https://api.mycurrency.com/users/<USER-ID>/issuer/received_store_reviews`

<aside class="notice">
Authentication: not required
</aside>

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the store review
store-id | The ID of the store that the store review relates to
comment | The written content of the review
score | A score between 0 and 5 (inclusive) by the store reviewer 
user-name | The user name of the store review author
user-avatar-url | The URL of the store review author's avatar
created-at | The time and date when the store review was created

## List Currency's Received Store Reviews

```shell
curl "https://api.mycurrency.com/currencies/3/received_store_reviews" \
  -H 'Host: api.mycurrency.com' -H 'Accept: application/json' -H 'Content-Type: application/json'
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": "1",
      "type": "store-reviews",
      "attributes": {
        "store-id": 1,
        "user-id": 4,
        "comment": "Schrauder Export Consulting is one of the best business strategy consultancies I've had the pleasure to use. They have a deep understanding of how to navigate the legal and commercial landscape to achieve international sales",
        "score": 5,
        "user-name": "ScipioAfricanus",
        "user-avatar-url": "/system/users/avatars/000/000/004/original/1.jpg?1559736060",
        "created-at": "2018-08-29T00:51:11.631-07:00"
      }
    },
    {
      "id": "2",
      "type": "store-reviews",
      "attributes": {
        "store-id": 2,
        "user-id": 4,
        "comment": "Schrauder Japan knows the ins and outs of the Japanese import market. Their professionalism was impressive.",
        "score": 4,
        "user-name": "ScipioAfricanus",
        "user-avatar-url": "/system/users/avatars/000/000/004/original/1.jpg?1559736060",
        "created-at": "2018-08-29T22:11:23.788-07:00"
      }
    }
  ],
  "links": {
    "self": "https://api.mycurrency.com/currencies/3/received_store_reviews?",
    "first": "https://api.mycurrency.com/currencies/3/received_store_reviews?page=1&per_page=25",
    "prev": null,
    "next": null,
    "last": "https://api.mycurrency.com/currencies/3/received_store_reviews?page=1&per_page=25"
  },
  "meta": {
    "pagination": {
      "per-page": null,
      "total-pages": "1",
      "total-count": "2"
    }
  }
}
```

This endpoint retrieves all store reviews received by stores belonging to the currency specified by the CURRENCY-ID.

### HTTP Request

`GET https://api.mycurrency.com/currencies/<CURRENCY-ID>/received_store_reviews`

<aside class="notice">
Authentication: not required
</aside>

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the store review
store-id | The ID of the store that the store review relates to
comment | The written content of the review
score | A score between 0 and 5 (inclusive) by the store reviewer 
user-name | The user name of the store review author
user-avatar-url | The URL of the store review author's avatar
created-at | The time and date when the store review was created

## List Store's Received Store Reviews

```shell
curl "https://api.mycurrency.com/stores/5/received_store_reviews" \
  -H 'Host: api.mycurrency.com' -H 'Accept: application/json' -H 'Content-Type: application/json'
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": "3",
      "type": "store-reviews",
      "attributes": {
        "store-id": 5,
        "user-id": 4,
        "comment": "I've been using McRyan's Grocers for about two years and am very happy with their growing selection of fresh fruits and vegetables",
        "score": 4,
        "user-name": "ScipioAfricanus",
        "user-avatar-url": "/system/users/avatars/000/000/004/original/1.jpg?1559736060",
        "created-at": "2018-08-29T22:15:34.052-07:00"
      }
    }
  ],
  "links": {
    "self": "https://api.mycurrency.com/stores/5/received_store_reviews?",
    "first": "https://api.mycurrency.com/stores/5/received_store_reviews?page=1&per_page=25",
    "prev": null,
    "next": null,
    "last": "https://api.mycurrency.com/stores/5/received_store_reviews?page=1&per_page=25"
  },
  "meta": {
    "pagination": {
      "per-page": null,
      "total-pages": "1",
      "total-count": "1"
    }
  }
}
```

This endpoint retrieves all store reviews received by stores belonging to the store specified by the STORE-ID.

### HTTP Request

`GET https://api.mycurrency.com/stores/<STORE-ID>/received_store_reviews`

<aside class="notice">
Authentication: not required
</aside>

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the store review
store-id | The ID of the store that the store review relates to
comment | The written content of the review
score | A score between 0 and 5 (inclusive) by the store reviewer 
user-name | The user name of the store review author
user-avatar-url | The URL of the store review author's avatar
created-at | The time and date when the store review was created

## Create Store Review

```shell
curl -X POST https://api.mycurrency.com/users/4/store_reviews \
  -d '{"store_review": { "store_id": "1", "score": "4", "comment": "Lucy'\''s Tom Yum Soup is as good as anything I had in Thailand"} }' \
  -H 'Authorization: Bearer j47lbjj8r9n5yy8mup6cxqc8h70yvhnilm0g84kg0raqckus0k1koj9f75ao' \
  -H 'Accept: application/json' -H 'Content-Type: application/json'
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "id": "4",
    "type": "store-reviews",
    "attributes": {
      "store-id": 1,
      "user-id": 4,
      "comment": "Lucy's Tom Yum Soup is as good as anything I had in Thailand",
      "score": 4,
      "user-name": "ScipioAfricanus",
      "user-avatar-url": "/system/users/avatars/000/000/004/original/1.jpg?1559736060",
      "created-at": "2018-08-29T22:45:12.219-07:00"
    }
  }
}
```

Creates a store review.

### HTTP Request

`POST https://api.mycurrency.com/users/<USER-ID>/store_reviews`

<aside class="notice">
Authentication: the request requires the OAuth access-token associated with the User referenced by the USER-ID 
</aside>

### ARGUMENTS

Parameter | Type | Required | Description
--------- | ------- | ------- | -----------
store_id | integer | yes | The ID of the store that the store review is written for
user_id | integer | yes | The ID of the user that the store review is written by, provided in URL path
comment | string | no | The written content of the review
score | integer | yes | A score between 0 and 5 (inclusive)

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the store review
store-id | The ID of the store that the store review relates to
comment | The written content of the review
score | A score between 0 and 5 (inclusive) by the store reviewer. If error is generated, it may state that the maximum allowed value is 10, because the API multiplies the user inputted value by two before submitting it to the database
user-name | The user name of the store review author
user-avatar-url | The URL of the store review author's avatar
created-at | The time and date when the store review was created

# Products

## Get a Product

```shell
curl 'https://api.mycurrency.com/products/1' \
  -H 'Accept: application/json' -H 'Content-Type: application/json'
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "id": "1",
    "type": "products",
    "attributes": {
      "sub-category-id": 57,
      "sub-category-name": "general labor",
      "currency-id": 1,
      "currency-name": "Micro Asteroid bucks",
      "currency-icon-url": "/icons/original/missing.png",
      "issuer-public-currency-holding-id": 2,
      "days-to-cancellation": null,
      "minutes-to-cancellation": null,
      "store-id": 1,
      "store-name": "Asteroid Industries",
      "product-name": "mine 1 pound of X-group asteroid",
      "product-description": "will mine 1 pound of material from an X-group asteroid and deliver it to the LEO processing facility",
      "price-cents": 1000000,
      "active": true,
      "continued": true,
      "last-activated-at": "2018-11-30T08:29:04.233-08:00",
      "created-at": "2018-11-30T08:29:04.233-08:00",
      "updated-at": "2018-11-30T08:29:04.233-08:00",
      "get-image-url": "/images/original/missing.png",
      "owner-id": 3,
      "owner-username": "Hannibal",
      "owner-avatar-url": "/system/users/avatars/000/000/003/original/avatar.jpg?1562578009",
      "public-amount-atomic": 0,
      "private-amount-atomic": 2000000000000,
      "total-amount-atomic": 2000000000000
    }
  }
}
```

This endpoint retrieves a particular product. The product must be active and not discontinued to be viewable by a non-authorized user.

### HTTP Request

`GET https://api.mycurrency.com/products/<ID>`

<aside class="notice">
Authentication: not required for active products that have not been discontinued. To view details of products that are inactive or discontinued, the request requires the OAuth access-token associated with the User that the product's store belongs to
</aside>

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the product
sub-category-id | The sub category that the product belongs to
sub-category-name | The name of the sub category that the product belongs to
currency-id | The ID of the currency that the product can be redeemed by
currency-name | The name of the currency that the product can be redeemed by
currency-icon-url | The URL of the icon of the currency that the product can be redeemed by 
issuer-public-currency-holding-id | The user ID of the public currency holding of the issuer of the currency that the store's products are purchasable with
days-to-cancellation | How many days until the product's product-discontinual is activated and the product is cancelled. A NULL value if the product has no product discontinual
minutes-to-cancellation | How many minutes until the product's product-discontinual is activated and the product is cancelled. A NULL value if the product has no product discontinual
store-id | The ID of the store where the product is sold
store-name | The name of the store where the product is sold
product-name | The name of the product
product-description | The description of the product
price-cents | The price of the product by multiple of 100, and denominated in the currency of the store where the product is sold
active | Whether the product is active or not
continued | Whether the product is continued or not. Discontinued products cannot be recontinued
last-activated-at | The time and date when the product was last activated
created-at | The time and date when the product was created
updated-at | The time and date when the product was last updated
get-image-url | The URL at which the product image picture can be found
owner-id | The ID of the owner of the store where the product is sold
owner-username | The username of the owner of the store where the product is sold
owner-avatar-url | The URL of the avatar of the owner of the store where the product is sold 
public-amount-atomic | The number of atomic units in the logged-in user's public holding of the currency that the product can be redeemed by, only shown if logged-in user is not the owner of the store that sells the product
private-amount-atomic | The number of atomic units in the logged-in user's private holding of the currency that the product can be redeemed by, only shown if logged-in user is not the owner of the store that sells the product
total-amount-atomic | The total number of atomic units in the logged-in user's public and private holding of the currency that the product can be redeemed by, only shown if logged-in user is not the owner of the store that sells the product

## List Products

```shell
curl "https://api.mycurrency.com/products" \
  -H 'Host: api.mycurrency.com' -H 'Accept: application/json' -H 'Content-Type: application/json'
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": "1",
      "type": "products",
      "attributes": {
        "sub-category-id": 3,
        "sub-category-name": "standard facial",
        "currency-id": 1,
        "currency-name": "Calm dollars",
        "currency-icon-url": "/icons/original/missing.png",
        "issuer-public-currency-holding-id": 2,
        "days-to-cancellation": null,
        "store-id": 1,
        "store-name": "Calm Spa",
        "product-name": "Facial",
        "product-description": "standard facial",
        "price-cents": 5000,
        "active": true,
        "continued": true,
        "last-activated-at": "2018-08-12T02:17:48.614-07:00",
        "created-at": "2018-08-12T02:17:48.614-07:00",
        "updated-at": "2018-08-12T18:02:24.284-07:00",
        "get-image-url": "/system/products/images/000/000/001/original/facial.jpg"
      }
    },
    {
      "id": "2",
      "type": "products",
      "attributes": {
        "sub-category-id": 6,
        "sub-category-name": "cartoon products",
        "currency-id": 2,
        "currency-name": "ACME Toon Shop dollars"
        "currency-icon-url": "/icons/original/missing.png",
        "issuer-public-currency-holding-id": 4,
        "days-to-cancellation": null,
        "store-id": 2,
        "store-name": "Vancouver ACME Toon Shop",
        "product-name": "Bugs Bunny Q-Tips",
        "product-description": "q-tips that work on the biggest ears",
        "price-cents": 1500,
        "active": true,
        "continued": true,
        "last-activated-at": "2018-08-24T05:01:25.879-07:00",
        "created-at": "2018-08-24T05:01:25.879-07:00",
        "updated-at": "2018-08-24T05:01:25.879-07:00",
        "get-image-url": "/system/products/images/000/000/002/original/bugs_q_tips.jpg"
      }
    },
    {
      "id": "3",
      "type": "products",
      "attributes": {
        "sub-category-id": 6,
        "sub-category-name": "cartoon products",
        "currency-id": 2,
        "currency-name": "ACME Toon Shop dollars"
        "currency-icon-url": "/icons/original/missing.png",
        "issuer-public-currency-holding-id": 4,
        "days-to-cancellation": null,
        "store-id": 3,
        "store-name": "San Francisco ACME Toon Shop",
        "product-name": "Bugs Bunny Q-Tips",
        "product-description": "q-tips that work on the biggest ears",
        "price-cents": 1500,
        "active": true,
        "continued": true,
        "last-activated-at": "2018-08-25T01:34:30.413-07:00",
        "created-at": "2018-08-25T01:34:30.413-07:00",
        "updated-at": "2018-08-25T01:34:30.413-07:00",
        "get-image-url": "/system/products/images/000/000/003/original/bugs_q_tips.jpg"
      }
    }
    {
      "id": "4",
      "type": "products",
      "attributes": {
        "sub-category-id": 6,
        "sub-category-name": "cartoon products",
        "currency-id": 2,
        "currency-name": "ACME Toon Shop dollars"
        "currency-icon-url": "/icons/original/missing.png",
        "issuer-public-currency-holding-id": 4,
        "days-to-cancellation": null,
        "store-id": 3,
        "store-name": "San Francisco ACME Toon Shop",
        "product-name": "Teleport hole",
        "product-description": "can turn any rock face into a tunnel",
        "price-cents": 4000,
        "active": true,
        "continued": true,
        "last-activated-at": "2018-08-25T02:14:35.984-07:00",
        "created-at": "2018-08-25T01:34:30.413-07:00",
        "updated-at": "2018-08-25T02:14:35.984-07:00",
        "get-image-url": "/system/products/images/000/000/004/original/teleport_hole.jpg"
      }
    }
  ],
  "links": {
    "self": "http://api.mycurrency.com/products?",
    "first": "http://api.mycurrency.com/products?page=1&per_page=25",
    "prev": null,
    "next": null,
    "last": "http://api.mycurrency.com/products?page=1&per_page=25"
  },
  "meta": {
    "pagination": {
      "per-page": null,
      "total-pages": "1",
      "total-count": "4"
    }
  }
}
```

This endpoint retrieves all products that are active and not discontinued.

### HTTP Request

`GET https://api.mycurrency.com/products`

<aside class="notice">
Authentication: not required 
</aside>

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the product
sub-category-id | The sub category that the product belongs to
sub-category-name | The name of the sub category that the product belongs to
currency-id | The ID of the currency that the product can be redeemed by
currency-name | The name of the currency that the product can be redeemed by
currency-icon-url | The URL of the icon of the currency that the product can be redeemed by 
issuer-public-currency-holding-id | The user ID of the public currency holding of the issuer of the currency that the store's products are purchasable with
days-to-cancellation | How many days until the product's product-discontinual is activated and the product is cancelled. A NULL value if the product has no product discontinual
store-id | The ID of the store where the product is sold
store-name | The name of the store where the product is sold
product-name | The name of the product
product-description | The description of the product
price-cents | The price of the product by multiple of 100, and denominated in the currency of the store where the product is sold
active | Whether the product is active or not
continued | Whether the product is continued or not. Discontinued products cannot be recontinued
last-activated-at | The time and date when the product was last activated
created-at | The time and date when the product was created
updated-at | The time and date when the product was last updated
get-image-url | The URL at which the product image picture can be found

## List a Store's Products

```shell
curl "https://api.mycurrency.com/stores/3/products" \
  -H 'Host: api.mycurrency.com' -H 'Accept: application/json' -H 'Content-Type: application/json'
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": "3",
      "type": "products",
      "attributes": {
        "sub-category-id": 6,
        "sub-category-name": "cartoon products",
        "currency-id": 2,
        "currency-name": "ACME Toon Shop dollars"
        "currency-icon-url": "/icons/original/missing.png",
        "issuer-public-currency-holding-id": 4,
        "days-to-cancellation": null,
        "store-id": 3,
        "store-name": "San Francisco ACME Toon Shop",
        "product-name": "Bugs Bunny Q-Tips",
        "product-description": "q-tips that work on the biggest ears",
        "price-cents": 1500,
        "active": true,
        "continued": true,
        "last-activated-at": "2018-08-25T01:34:30.413-07:00",
        "created-at": "2018-08-25T01:34:30.413-07:00",
        "updated-at": "2018-08-25T01:34:30.413-07:00",
        "get-image-url": "/system/products/images/000/000/003/original/bugs_q_tips.jpg"
      }
    }
    {
      "id": "4",
      "type": "products",
      "attributes": {
        "sub-category-id": 6,
        "sub-category-name": "cartoon products",
        "currency-id": 2,
        "currency-name": "ACME Toon Shop dollars"
        "currency-icon-url": "/icons/original/missing.png",
        "issuer-public-currency-holding-id": 4,
        "days-to-cancellation": null,
        "store-id": 3,
        "store-name": "San Francisco ACME Toon Shop",
        "product-name": "Teleport hole",
        "product-description": "can turn any rock face into a tunnel",
        "price-cents": 4000,
        "active": true,
        "continued": true,
        "last-activated-at": "2018-08-25T02:14:35.984-07:00",
        "created-at": "2018-08-25T01:34:30.413-07:00",
        "updated-at": "2018-08-25T02:14:35.984-07:00",
        "get-image-url": "/system/products/images/000/000/004/original/teleport_hole.jpg"
      }
    }
  ],
  "links": {
    "self": "http://api.mycurrency.com/stores/3/products?",
    "first": "http://api.mycurrency.com/stores/3/products?page=1&per_page=25",
    "prev": null,
    "next": null,
    "last": "http://api.mycurrency.com/stores/3/products?page=1&per_page=25"
  },
  "meta": {
    "pagination": {
      "per-page": null,
      "total-pages": "1",
      "total-count": "2"
    }
  }
}
```

This endpoint retrieves all products belonging to a particular currency. Only products that are active and not discontinued are shown to non-authorized users. If a user is viewing the products of their own store, they are shown only products that have not been discontinued, whether active or inactive, by default. If they pass :show_canceled argument set to TRUE, they will also be shown products that have been discontinued.

### HTTP Request

`GET https://api.mycurrency.com/stores/<STORE-ID>/products`

<aside class="notice">
Authentication: not required to see the products of a store that are active and that have not been discontinued. To view details of a store's products that are inactive and/or discontinued, the request requires the OAuth access-token associated with the User that the specified store belongs to
</aside>

### ARGUMENTS

Parameter | Type | Required | Description
--------- | ------- | ------- | -----------
show_canceled | boolean | no | Whether canceled products will be shown when user is looking at products of stores they own

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the product
sub-category-id | The sub category that the product belongs to
sub-category-name | The name of the sub category that the product belongs to
currency-id | The ID of the currency that the product can be redeemed by
currency-name | The name of the currency that the product can be redeemed by
currency-icon-url | The URL of the icon of the currency that the product can be redeemed by 
issuer-public-currency-holding-id | The user ID of the public currency holding of the issuer of the currency that the store's products are purchasable with
days-to-cancellation | How many days until the product's product-discontinual is activated and the product is cancelled. A NULL value if the product has no product discontinual
store-id | The ID of the store where the product is sold
store-name | The name of the store where the product is sold
product-name | The name of the product
product-description | The description of the product
price-cents | The price of the product by multiple of 100, and denominated in the currency of the store where the product is sold
active | Whether the product is active or not
continued | Whether the product is continued or not. Discontinued products cannot be recontinued
last-activated-at | The time and date when the product was last activated
created-at | The time and date when the product was created
updated-at | The time and date when the product was last updated
get-image-url | The URL at which the product image picture can be found

## Create Product

```shell
curl -X POST https://api.mycurrency.com/users/3/issuer/currencies/1/stores/1/products \
  -d '{"product": { "sub_category_id": "15", "product_name": "goliath rocket 2", "product_description": "second version of rocket for reaching the moon", "active": "true", "price_cents": "1000000"} }' \
  -H 'Authorization: Bearer eyJhbGciOiJIUzI1NiJ9.eyJzdWIiOiI0Iiwic2NwIjoidXNlciIsImF1ZCI6bnVsbCwiaWF0IjoxNTM1MzQyNzY4LCJleHAiOjE1MzU0MjkxNjgsImp0aSI6IjcxMTU1YWEwLTBjYWItNDJmNi1hY2FjLWNjYTA0MDM5ZGUzMSJ9.vUfErKhiJ4fB5QueiWAUoxQLE8gsqyzNIBFibzcztT8' \
  -H 'Accept: application/json' -H 'Content-Type: application/json'
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "id": "40",
    "type": "products",
    "attributes": {
      "sub-category-id": 15,
      "sub-category-name": "audio equipment",
      "currency-id": 1,
      "currency-name": "Micro Asteroid bucks",
      "currency-icon-url": "/system/currencies/icons/missing.png",
      "issuer-public-currency-holding-id": 2,
      "days-to-cancellation": null,
      "minutes-to-cancellation": null,
      "store-id": 1,
      "store-name": "Asteroid Industries",
      "product-name": "goliath rocket 2",
      "product-description": "second version of rocket for reaching the moon",
      "price-cents": 1000000,
      "active": true,
      "continued": true,
      "last-activated-at": "2019-07-26T04:57:32.173-07:00",
      "created-at": "2019-07-26T04:57:32.173-07:00",
      "updated-at": "2019-07-26T04:57:32.173-07:00",
      "get-image-url": "/system/products/images/original/missing.png",
      "owner-id": 3,
      "owner-username": "Hannibal",
      "owner-avatar-url": "/system/users/avatars/000/000/003/original/avatar.jpg?1562578009"
    }
  }
}
```

Creates a product.

### HTTP Request

`POST https://api.mycurrency.com/users/<USER-ID>/issuer/currencies/<CURRENCY-ID>/stores/<STORE-ID>/products`

<aside class="notice">
Authentication: the request requires the OAuth access-token associated with the User referenced by the USER-ID 
</aside>

### ARGUMENTS

Parameter | Type | Required | Description
--------- | ------- | ------- | -----------
sub_category_id | integer | yes | The sub category that the product belongs to
store_id | integer | yes | The ID of the store where the product is sold, provided in URL path
product_name | string | yes | The name of the product
product_description | string | no | The description of the product
price_cents | integer | yes | The price of the product by multiple of 100, and denominated in the currency of the store where the product is sold
active | boolean | yes | Whether the product is active or not
image | filename | no | The image file to be uploaded as product's image picture

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the product
sub-category-id | The sub category that the product belongs to
sub-category-name | The name of the sub category that the product belongs to
currency-id | The ID of the currency that the product can be redeemed by
currency-name | The name of the currency that the product can be redeemed by
currency-icon-url | The URL of the icon of the currency that the product can be redeemed by 
issuer-public-currency-holding-id | The user ID of the public currency holding of the issuer of the currency that the store's products are purchasable with
days-to-cancellation | How many days until the product's product-discontinual is activated and the product is cancelled. A NULL value if the product has no product discontinual
store-id | The ID of the store where the product is sold
store-name | The name of the store where the product is sold
product-name | The name of the product
product-description | The description of the product
price-cents | The price of the product by multiple of 100, and denominated in the currency of the store where the product is sold
active | Whether the product is active or not
continued | Whether the product is continued or not. Discontinued products cannot be recontinued
last-activated-at | The time and date when the product was last activated
created-at | The time and date when the product was created
updated-at | The time and date when the product was last updated
get-image-url | The URL at which the product image picture can be found
owner-id | The ID of the owner of the store where the product is sold
owner-username | The username of the owner of the store where the product is sold
owner-avatar-url | The URL of the avatar of the owner of the store where the product is sold 

## Update Product

```shell
curl -X PUT https://api.mycurrency.com/users/4/issuer/currencies/5/stores/3/products/5 \
  -F 'product[image]=@fish_bait.jpg' \
  -H 'Authorization: Bearer eyJhbGciOiJIUzI1NiJ9.eyJzdWIiOiI0Iiwic2NwIjoidXNlciIsImF1ZCI6bnVsbCwiaWF0IjoxNTM1MzQyNzY4LCJleHAiOjE1MzU0MjkxNjgsImp0aSI6IjcxMTU1YWEwLTBjYWItNDJmNi1hY2FjLWNjYTA0MDM5ZGUzMSJ9.vUfErKhiJ4fB5QueiWAUoxQLE8gsqyzNIBFibzcztT8' \
  -H 'Accept: application/json' \
  -H 'Content-Type: multipart/form-data'
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "id": "5",
    "type": "products",
    "attributes": {
      "sub-category-id": 4,
      "sub-category-name": "fishing supplies",
      "currency-id": 5,
      "currency-name": "Freds Fishing Supplies dollars",
      "currency-icon-url": "/icons/original/missing.png",
      "issuer-public-currency-holding-id": 2,
      "days-to-cancellation": null,
      "store-id": 3,
      "store-name": "Freds Fishing Supplies",
      "product-name": "fishing bait",
      "product-description": "natural fishing bait made of worms",
      "price-cents": 1000,
      "active": true,
      "continued": true,
      "last-activated-at": "2018-08-26T17:15:53.011-07:00",
      "created-at": "2018-08-26T17:15:53.011-07:00",
      "updated-at": "2018-08-26T21:07:27.184-07:00",
      "get-image-url": "/system/products/images/000/000/005/original/fish_bait.jpg?1535342847"
      "owner-id": 4,
      "owner-username": "ScipioAfricanus",
      "owner-avatar-url": "/system/users/avatars/000/000/004/original/1.jpg?1559736060"
    }
  }
}
```

Updates a product.

### HTTP Request

`PUT https://api.mycurrency.com/users/<USER-ID>/issuer/currencies/<CURRENCY-ID>/stores/<STORE-ID>/products/<ID>`

<aside class="notice">
Authentication: the request requires the OAuth access-token associated with the User referenced by the USER-ID 
</aside>

### ARGUMENTS

Parameter | Type | Required | Description
--------- | ------- | ------- | -----------
sub_category_id | integer | yes | The sub category that the product belongs to
store_id | integer | yes | The ID of the store where the product is sold, provided in URL path
product_description | string | no | The description of the product
price_cents | integer | yes | The price of the product by multiple of 100, and denominated in the currency of the store where the product is sold, can only be updated when the product is inactive
active | boolean | yes | Whether the product is active or not, can only be updated within 24 hours of the product's last activation
image | filename | no | The image file to be uploaded as product's image picture

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the product
sub-category-id | The sub category that the product belongs to
sub-category-name | The name of the sub category that the product belongs to
currency-id | The ID of the currency that the product can be redeemed by
currency-name | The name of the currency that the product can be redeemed by
currency-icon-url | The URL of the icon of the currency that the product can be redeemed by 
issuer-public-currency-holding-id | The user ID of the public currency holding of the issuer of the currency that the store's products are purchasable with
days-to-cancellation | How many days until the product's product-discontinual is activated and the product is cancelled. A NULL value if the product has no product discontinual
store-id | The ID of the store where the product is sold
store-name | The name of the store where the product is sold
product-name | The name of the product
product-description | The description of the product
price-cents | The price of the product by multiple of 100, and denominated in the currency of the store where the product is sold
active | Whether the product is active or not
continued | Whether the product is continued or not. Discontinued products cannot be recontinued
last-activated-at | The time and date when the product was last activated
created-at | The time and date when the product was created
updated-at | The time and date when the product was last updated
get-image-url | The URL at which the product image picture can be found
owner-id | The ID of the owner of the store where the product is sold
owner-username | The username of the owner of the store where the product is sold
owner-avatar-url | The URL of the avatar of the owner of the store where the product is sold 

# Product Cancellations

## Get a Product Cancellation

```shell
curl 'https://api.mycurrency.com/products/5/product_cancellation' \
  -H 'Accept: application/json' -H 'Content-Type: application/json'
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "id": "1",
    "type": "product-cancellations",
    "attributes": {
      "store-id": 3,
      "store-name": "Freds Fishing Supplies",
      "product-id": 5,
      "product-discontinual-id": null,
      "cancellation-message": "cancelling fishing bait due to health code regulations",
      "with-advance-notice": false,
      "created-at": "2018-09-06T00:07:27.093-07:00",
      "updated-at":"2018-09-06T00:07:27.093-07:00"
    }
  }
}
```

This endpoint retrieves a particular product cancellation. 

### HTTP Request

`GET https://api.mycurrency.com/products/<PRODUCT-ID>/product_cancellation`

<aside class="notice">
Authentication: not required
</aside>

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the product cancellation
store-id | The ID of the store where the cancelled product was sold
store-name | The name of the store where the cancelled product was sold
product-id | The ID of the product that was cancelled
product-discontinual-id | The ID of the product_discontinual that created the product_cancellation
product-name | The name of the cancelled product
cancellation-message | The message explaining why the product was cancelled
with-advance-notice | Whether there was advance notice of the product's cancellation given to those holding the currency that was redeemable in the product, in order to give them the opportunity to spend their currency on the product before its cancellation
created-at | The time and date when the product was cancelled

## List Issuer's Product Cancellations

```shell
curl 'https://api.mycurrency.com/users/4/issuer/product_cancellations' \
  -H 'Accept: application/json' -H 'Content-Type: application/json'
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": "1",
      "type": "product-cancellations",
      "attributes": {
        "store-id": 3,
        "store-name": "Freds Fishing Supplies",
        "product-id": 5,
        "product-discontinual-id": null,
        "cancellation-message": "cancelling fishing bait due to health code regulations",
        "with-advance-notice": false,
        "created-at": "2018-09-06T00:07:27.093-07:00"
      }
    },
    {
      "id": "4",
      "type": "product-cancellations",
      "attributes": {
        "store-id": 4,
        "store-name": "Jeffreys outdoor supplies",
        "product-id": 9,
        "product-discontinual-id": null,
        "cancellation-message": "the Defense Ministry classified the synthetic skin used to provide tent's chameleon effect",
        "with-advance-notice": false,
        "created-at": "2018-09-07T14:04:44.141-07:00"
      }
    },
    {
      "id": "5",
      "type": "product-cancellations",
      "attributes": {
        "store-id": 6,
        "store-name": "Honolulu pizza joint",
        "product-id": 12,
        "product-discontinual-id": null,
        "cancellation-message": "change of menu",
        "with-advance-notice": false,
        "created-at": "2018-09-08T11:18:31.411-07:00"
      }
    }
  ],
  "links": {
    "self": "https://api.mycurrency.com/users/4/issuer/product_cancellations?",
    "first": "https://api.mycurrency.com/users/4/issuer/product_cancellations?page=1&per_page=25",
    "prev": null,
    "next": null,
    "last": "https://api.mycurrency.com/users/4/issuer/product_cancellations?page=1&per_page=25"
  },
  "meta": {
    "pagination": {
      "per-page": null,
      "total-pages": "1",
      "total-count": "3"
    }
  }
}
```

This endpoint retrieves all product cancellations associated with the stores of a particular issuer, by the USER-ID of the issuer's associated user account

### HTTP Request

`GET https://api.mycurrency.com/users/<USER-ID>/issuer/product_cancellations`

<aside class="notice">
Authentication: not required
</aside>

### ARGUMENTS

Parameter | Type | Required | Description
--------- | ------- | ------- | -----------
without_advance_notice | boolean | no | If set to true, only returns the product cancellations in the set that have the :with_advance_notice field set to false

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the product cancellation
store-id | The ID of the store where the cancelled product was sold
store-name | The name of the store where the cancelled product was sold
product-id | The ID of the product that was cancelled
product-discontinual-id | The ID of the product_discontinual that created the product_cancellation
cancellation-message | The message explaining why the product was cancelled
with-advance-notice | Whether there was advance notice of the product's cancellation given to those holding the currency that was redeemable in the product, in order to give them the opportunity to spend their currency on the product before its cancellation
created-at | The time and date when the product cancellation was cancelled

## List Currency's Product Cancellations

```shell
curl 'https://api.mycurrency.com/currencies/5/product_cancellations' \
  -H 'Accept: application/json' -H 'Content-Type: application/json'
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": "1",
      "type": "product-cancellations",
      "attributes": {
        "store-id": 3,
        "store-name": "Freds Fishing Supplies",
        "product-id": 5,
        "product-discontinual-id": null,
        "cancellation-message": "cancelling fishing bait due to health code regulations",
        "with-advance-notice": false,
        "created-at": "2018-09-06T00:07:27.093-07:00"
      }
    },
    {
      "id": "4",
      "type": "product-cancellations",
      "attributes": {
        "store-id": 4,
        "store-name": "Jeffreys outdoor supplies",
        "product-id": 9,
        "product-discontinual-id": null,
        "cancellation-message": "the Defense Ministry classified the synthetic skin used to provide tent's chameleon effect",
        "with-advance-notice": false,
        "created-at": "2018-09-07T14:04:44.141-07:00"
      }
    }
  ],
  "links": {
    "self": "https://api.mycurrency.com/currencies/5/product_cancellations?",
    "first": "https://api.mycurrency.com/currencies/5/product_cancellations?page=1&per_page=25",
    "prev": null,
    "next": null,
    "last": "https://api.mycurrency.com/currencies/5/product_cancellations?page=1&per_page=25"
  },
  "meta": {
    "pagination": {
      "per-page": null,
      "total-pages": "1",
      "total-count": "2"
    }
  }
}
```

This endpoint retrieves all product cancellations associated with the stores belonging to the currency referenced by CURRENCY-ID

### HTTP Request

`GET https://api.mycurrency.com/currencies/<CURRENCY-ID>/product_cancellations`

<aside class="notice">
Authentication: not required
</aside>

### ARGUMENTS

Parameter | Type | Required | Description
--------- | ------- | ------- | -----------
without_advance_notice | boolean | no | If set to true, only returns the product cancellations in the set that have the :with_advance_notice field set to false

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the product cancellation
store-id | The ID of the store where the cancelled product was sold
store-name | The name of the store where the cancelled product was sold
product-id | The ID of the product that was cancelled
product-discontinual-id | The ID of the product_discontinual that created the product_cancellation
cancellation-message | The message explaining why the product was cancelled
with-advance-notice | Whether there was advance notice of the product's cancellation given to those holding the currency that was redeemable in the product, in order to give them the opportunity to spend their currency on the product before its cancellation
created-at | The time and date when the product cancellation was cancelled

## List Store's Product Cancellations

```shell
curl 'https://api.mycurrency.com/stores/3/product_cancellations' \
  -H 'Accept: application/json' -H 'Content-Type: application/json'
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": "1",
      "type": "product-cancellations",
      "attributes": {
        "store-id": 3,
        "store-name": "Jeffreys outdoor supplies",
        "product-id": 5,
        "product-discontinual-id": null,
        "cancellation-message": "cancelling fishing bait due to health code regulations",
        "with-advance-notice": false,
        "created-at": "2018-09-06T00:07:27.093-07:00"
      }
    }
  ],
  "links": {
    "self": "https://api.mycurrency.com/currencies/5/product_cancellations?",
    "first": "https://api.mycurrency.com/currencies/5/product_cancellations?page=1&per_page=25",
    "prev": null,
    "next": null,
    "last": "https://api.mycurrency.com/currencies/5/product_cancellations?page=1&per_page=25"
  },
  "meta": {
    "pagination": {
      "per-page": null,
      "total-pages": "1",
      "total-count": "1"
    }
  }
}
```

This endpoint retrieves all product cancellations associated with the store referenced by STORE-ID

### HTTP Request

`GET https://api.mycurrency.com/stores/<STORE-ID>/product_cancellations`

<aside class="notice">
Authentication: not required
</aside>

### ARGUMENTS

Parameter | Type | Required | Description
--------- | ------- | ------- | -----------
without_advance_notice | boolean | no | If set to true, only returns the product cancellations in the set that have the :with_advance_notice field set to false

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the product cancellation
store-id | The ID of the store where the cancelled product was sold
store-name | The name of the store where the cancelled product was sold
product-id | The ID of the product that was cancelled
product-discontinual-id | The ID of the product_discontinual that created the product_cancellation
cancellation-message | The message explaining why the product was cancelled
with-advance-notice | Whether there was advance notice of the product's cancellation given to those holding the currency that was redeemable in the product, in order to give them the opportunity to spend their currency on the product before its cancellation
created-at | The time and date when the product cancellation was cancelled

## Create Product Cancellation

```shell
curl -X POST https://api.mycurrency.com/users/4/issuer/currencies/5/stores/3/products/5/product_cancellation \
  -d '{"product_cancellation": { "cancellation_message": "cancelling fishing bait due to health code regulations"} }' \
  -H 'Authorization: Bearer j47lbjj8r9n5yy8mup6cxqc8h70yvhnilm0g84kg0raqckus0k1koj9f75ao' \
  -H 'Accept: application/json' -H 'Content-Type: application/json'
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "id": "1",
    "type": "product-cancellations",
    "attributes": {
      "store-id": 3,
      "store-name": "Freds Fishing Supplies",
      "product-id": 5,
      "product-discontinual-id": null,
      "cancellation-message": "cancelling fishing bait due to health code regulations",
      "with-advance-notice": false,
      "created-at": "2018-09-06T00:07:27.093-07:00",
      "updated-at":"2018-09-06T00:07:27.093-07:00"
    }
  }
}
```

Creates a product cancellation.

### HTTP Request

`POST https://api.mycurrency.com/users/<USER-ID>/issuer/currencies/<CURRENCY-ID>/stores/<STORE-ID>/products/<PRODUCT-ID>/product_cancellation`

<aside class="notice">
Authentication: the request requires the OAuth access-token associated with the User referenced by the USER-ID 
</aside>

### ARGUMENTS

Parameter | Type | Required | Description
--------- | ------- | ------- | -----------
user_id | integer | yes | The ID of the user which offered the product that was cancelled, provided in URL path
currency_id | integer | yes | The ID of the currency which was redeemable in the product that was cancelled, provided in URL path
store_id | integer | yes | The ID of the store where the product being cancelled is sold, provided in URL path
product_id | integer | yes | The ID of the product that is being cancelled, provided in URL path
cancellation_message | string | no | The message explaining why the product is being cancelled

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the product cancellation
store-id | The ID of the store where the cancelled product was sold
store-name | The name of the store where the cancelled product was sold
product-id | The ID of the product that was cancelled
product-discontinual-id | The ID of the product_discontinual that created the product_cancellation
cancellation-message | The message explaining why the product was cancelled
with-advance-notice | Set to false, indicating there was no advance notice of the product's cancellation given to those holding the currency that was redeemable in the product. To provide advance notice, a product_discontinual must be created instead of a product_cancellation
created-at | The time and date when the product cancellation was cancelled

# Product Discontinuals

## Get a Product Discontinual

```shell
curl 'https://api.mycurrency.com/products/4/product_discontinual' \
  -H 'Accept: application/json' -H 'Content-Type: application/json'
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "id": "1",
    "type": "product-discontinuals",
    "attributes": {
      "store-id": 2,
      "product-id": 4,
      "product-name": "skin exfoliation",
      "discontinual-message": "will be replacing this with coconut milk exfoliant",
      "executed": true,
      "created-at": "2018-09-07T14:23:25.000-07:00"
    }
  }
}
```

This endpoint retrieves a particular product discontinual. 

### HTTP Request

`GET https://api.mycurrency.com/products/<PRODUCT-ID>/product_discontinual`

<aside class="notice">
Authentication: not required
</aside>

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the product discontinual
store-id | The ID of the store where the product being cancelled is sold
product-id | The ID of the product that will be cancelled
product-name | The name of the product that will be cancelled
discontinual-message | The message explaining why the product will be cancelled
executed | Whether the product discontinual has been executed in order to create a product cancellation. Product discontinuals are executed 30 days after being created, giving holders of the currency that the product is redeemable in time to trade in their currency for that product before it is cancelled
created-at | The time and date when the product discontinual was cancelled

## List Store's Product Discontinuals

```shell
curl 'https://api.mycurrency.com/stores/2/product_discontinuals' \
  -H 'Accept: application/json' -H 'Content-Type: application/json'
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": "2",
      "type": "product-discontinuals",
      "attributes": {
        "store-id": 2,
        "product-id": 6,
        "product-name": "banana leaf wrap treatment",
        "discontinual-message": "is superseded by the new dragonfruit skin wrap treatment",
        "executed": false,
        "created-at": "2018-09-10T15:31:50.306-07:00"
      }
    },
    {
      "id": "3",
      "type": "product-discontinuals",
      "attributes": {
        "store-id": 2,
        "product-id": 7,
        "product-name": "glacier cryotherapy",
        "discontinual-message": "this has been replaced by the mountain hot springs treatment",
        "executed": false,
        "created-at": "2018-09-10T15:33:11.074-07:00"
      }
    },
    {
      "id": "4",
      "type": "product-discontinuals",
      "attributes": {
        "store-id": 2,
        "product-id": 8,
        "product-name": "drum massage",
        "discontinual-message": "replaced by the ashiatsu back walking treatment",
        "executed": false,
        "created-at": "2018-09-10T15:34:33.801-07:00"
      }
    }
  ],
  "links": {
    "self": "https://api.mycurrency.com/stores/2/product_discontinuals?",
    "first": "https://api.mycurrency.com/stores/2/product_discontinuals?page=1&per_page=25",
    "prev": null,
    "next": null,
    "last": "https://api.mycurrency.com/stores/2/product_discontinuals?page=1&per_page=25"
  },
  "meta": {
    "pagination": {
      "per-page": null,
      "total-pages": "1",
      "total-count": "3"
    }
  }
}
```

This endpoint retrieves all product discontinuals associated with the store specified by the STORE-ID

### HTTP Request

`GET https://api.mycurrency.com/stores/<STORE-ID>/product_discontinuals`

<aside class="notice">
Authentication: not required for product discontinuals that have not been executed. To view details of all product discontinuals, including those that have already been executed, the request requires the OAuth access-token associated with the User that the product's store belongs to
</aside>

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the product discontinual
store-id | The ID of the store where the product being cancelled is sold
product-id | The ID of the product that will be cancelled
product-name | The name of the product that will be cancelled
discontinual-message | The message explaining why the product will be cancelled
executed | Whether the product discontinual has been executed in order to create a product cancellation. Product discontinuals are executed 30 days after being created, giving holders of the currency that the product is redeemable in time to trade in their currency for that product before it is cancelled
created-at | The time and date when the product discontinual was cancelled

## Create Product Discontinual

```shell
curl -X POST https://api.mycurrency.com/users/4/issuer/currencies/4/stores/2/products/8/product_discontinual \
  -d '{"product_discontinual": { "discontinual_message": "replaced by the ashiatsu back walking treatment"} }' \
  -H 'Authorization: Bearer j47lbjj8r9n5yy8mup6cxqc8h70yvhnilm0g84kg0raqckus0k1koj9f75ao' \
  -H 'Accept: application/json' -H 'Content-Type: application/json'
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "id": "4",
    "type": "product-discontinuals",
    "attributes": {
      "store-id": 2,
      "product-id": 8,
      "product-name": "drum massage",
      "discontinual-message": "replaced by the ashiatsu back walking treatment",
      "executed": false,
      "created-at": "2018-09-10T15:34:33.801-07:00"
    }
  }
}
```

Creates a product discontinual.

### HTTP Request

`POST https://api.mycurrency.com/users/<USER-ID>/issuer/currencies/<CURRENCY-ID>/stores/<STORE-ID>/products/<PRODUCT-ID>/product_discontinual`

<aside class="notice">
Authentication: the request requires the OAuth access-token associated with the User referenced by the USER-ID 
</aside>

### ARGUMENTS

Parameter | Type | Required | Description
--------- | ------- | ------- | -----------
user_id | integer | yes | The ID of the user which offered the product that is being cancelled, provided in URL path
currency_id | integer | yes | The ID of the currency which was redeemable in the product that is being cancelled, provided in URL path
store_id | integer | yes | The ID of the store where the product being cancelled is sold, provided in URL path
product_id | integer | yes | The ID of the product that is being cancelled, provided in URL path
discontinual_message | string | no | The message explaining why the product will be cancelled

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the product discontinual
store-id | The ID of the store where the product being cancelled is sold
product-id | The ID of the product that will be cancelled
product-name | The name of the product that will be cancelled
discontinual-message | The message explaining why the product will be cancelled
executed | Whether the product discontinual has been executed in order to create a product cancellation. Product discontinuals are executed 30 days after being created, giving holders of the currency that the product is redeemable in time to trade in their currency for that product before it is cancelled
created-at | The time and date when the product discontinual was cancelled

# Currency Holdings

## List User's Self-Issued Currency Holdings with Authorization

```shell
curl 'https://api.mycurrency.com/users/4/authorized_self_issued_currency_holdings' \
  -H 'Accept: application/json' -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer j47lbjj8r9n5yy8mup6cxqc8h70yvhnilm0g84kg0raqckus0k1koj9f75ao'
```

> The above command returns JSON structured like this:

```json
{
  "data": [{
      "currency-holding-pair": {
        "data": [{
          "id": 2,
          "type": "PrivateCurrencyHolding",
          "attributes": {
            "currency-id": 2,
            "currency-name": "solar electricity zaps",
            "currency-icon-url": "/icons/original/missing.png",
            "currency-burn-rate": 640,
            "currency-daily-burn-rate": "0.000181189",
            "store_count": 2,
            "amount-atomic": 4884625096360,
            "burn-amount-out": 5374903640,
            "is-issuer-active": true,
            "issuer-user-id": 4,
            "issuer-user-name": "ScipioAfricanus",
            "issuer-user-avatar-url": "/system/users/avatars/000/000/004/original/1.jpg?1559736060",
            "created-at": "2018-11-05 13:27:52 -0800",
            "updated-at": "2018-12-17 05:15:10 -0800"
          }
        }]
      }
    },
    {
      "currency-holding-pair": {
        "data": [{
          "id": 5,
          "type": "PrivateCurrencyHolding",
          "attributes": {
            "currency-id": 3,
            "currency-name": "Moon hotel coins",
            "currency-icon-url": "/icons/original/missing.png",
            "currency-burn-rate": 550,
            "currency-daily-burn-rate": "0.000154976",
            "store_count": 1,
            "amount-atomic": 9795351440488,
            "burn-amount-out": 4648559512,
            "is-issuer-active": true,
            "issuer-user-id": 4,
            "issuer-user-name": "ScipioAfricanus",
            "issuer-user-avatar-url": "/system/users/avatars/000/000/004/original/1.jpg?1559736060",
            "created-at": "2018-11-05 13:27:52 -0800",
            "updated-at": "2018-12-20 06:18:37 -0800"
          }
        }]
      }
    },
    {
      "currency-holding-pair": {
        "data": [{
          "id": 10,
          "type": "PrivateCurrencyHolding",
          "attributes": {
            "currency-id": 5,
            "currency-name": "Home Repair dollars",
            "currency-icon-url": "/icons/original/missing.png",
            "currency-burn-rate": 450,
            "currency-daily-burn-rate": "0.00012614",
            "store_count": 0,
            "amount-atomic": 4998738679556,
            "burn-amount-out": 1261320444,
            "is-issuer-active": true,
            "issuer-user-id": 4,
            "issuer-user-name": "ScipioAfricanus",
            "issuer-user-avatar-url": "/system/users/avatars/000/000/004/original/1.jpg?1559736060",
            "created-at": "2018-11-06 13:27:52 -0800",
            "updated-at": "2018-11-08 13:26:13 -0800"
          }
        }]
      }
    },
    {
      "currency-holding-pair": {
        "data": [{
          "id": 11,
          "type": "PrivateCurrencyHolding",
          "attributes": {
            "currency-id": 6,
            "currency-name": "Wholesome foods tokens",
            "currency-icon-url": "/icons/original/missing.png",
            "currency-burn-rate": 710,
            "currency-daily-burn-rate": "0.000201751",
            "store_count": 0,
            "amount-atomic": 9995965387034,
            "burn-amount-out": 4034612966,
            "is-issuer-active": true,
            "issuer-user-id": 4,
            "issuer-user-name": "ScipioAfricanus",
            "issuer-user-avatar-url": "/system/users/avatars/000/000/004/original/1.jpg?1559736060",
            "created-at": "2018-11-06 13:27:52 -0800",
            "updated-at": "2018-11-08 13:26:13 -0800"
          }
        }]
      }
    },
    {
      "currency-holding-pair": {
        "data": [{
            "id": 17,
            "type": "PrivateCurrencyHolding",
            "attributes": {
              "currency-id": 9,
              "currency-name": "Alabama steak coins",
              "currency-icon-url": "/icons/original/missing.png",
              "currency-burn-rate": 550,
              "currency-daily-burn-rate": "0.000154976",
              "store_count": 1,
              "amount-atomic": 130000000000000,
              "burn-amount-out": 0,
              "is-issuer-active": true,
              "issuer-user-id": 4,
              "issuer-user-name": "ScipioAfricanus",
              "issuer-user-avatar-url": "/system/users/avatars/000/000/004/original/1.jpg?1559736060",
              "created-at": "2019-06-12 03:23:26 -0700",
              "updated-at": "2019-06-12 03:39:39 -0700"
            }
          },
          {
            "id": 11,
            "type": "PublicCurrencyHolding",
            "attributes": {
              "currency-id": 9,
              "currency-name": "Alabama steak coins",
              "currency-icon-url": "/icons/original/missing.png",
              "currency-burn-rate": 550,
              "currency-daily-burn-rate": "0.000154976",
              "store_count": 1,
              "amount-atomic": 80000000000000,
              "burn-amount-out": 0,
              "is-issuer-active": true,
              "issuer-user-id": 4,
              "issuer-user-name": "ScipioAfricanus",
              "issuer-user-avatar-url": "/system/users/avatars/000/000/004/original/1.jpg?1559736060",
              "created-at": "2019-06-12 03:39:39 -0700",
              "updated-at": "2019-06-12 03:39:39 -0700"
            }
          }
        ]
      }
    },
    {
      "currency-holding-pair": {
        "data": [{
            "id": 18,
            "type": "PrivateCurrencyHolding",
            "attributes": {
              "currency-id": 10,
              "currency-name": "Turbo points",
              "currency-icon-url": "/icons/original/missing.png",
              "currency-burn-rate": 600,
              "currency-daily-burn-rate": "0.000169508",
              "store_count": 1,
              "amount-atomic": 40000000000000,
              "burn-amount-out": 0,
              "is-issuer-active": true,
              "issuer-user-id": 4,
              "issuer-user-name": "ScipioAfricanus",
              "issuer-user-avatar-url": "/system/users/avatars/000/000/004/original/1.jpg?1559736060",
              "created-at": "2019-06-12 03:24:27 -0700",
              "updated-at": "2019-06-12 03:41:24 -0700"
            }
          },
          {
            "id": 12,
            "type": "PublicCurrencyHolding",
            "attributes": {
              "currency-id": 10,
              "currency-name": "Turbo points",
              "currency-icon-url": "/icons/original/missing.png",
              "currency-burn-rate": 600,
              "currency-daily-burn-rate": "0.000169508",
              "store_count": 1,
              "amount-atomic": 62000000000000,
              "burn-amount-out": 0,
              "is-issuer-active": true,
              "issuer-user-id": 4,
              "issuer-user-name": "ScipioAfricanus",
              "issuer-user-avatar-url": "/system/users/avatars/000/000/004/original/1.jpg?1559736060",
              "created-at": "2019-06-12 03:41:24 -0700",
              "updated-at": "2019-06-17 10:06:45 -0700"
            }
          }
        ]
      }
    }
  ],
  "meta": {
    "user-data": {
      "number-of-reviews": 23,
      "currency-count": 6
    }
  }
}
```

This endpoint retrieves the full details of all of a user's public and private holdings of currencies that the user is also the issuer of, grouped in sets of up to two holdings containing the same currency 

### HTTP Request

`GET https://api.mycurrency.com/users/<USER-ID>/authorized_self_issued_currency_holdings`

<aside class="notice">
Authentication: the request requires the OAuth access-token associated with the User referenced by the ID 
</aside>

### ARGUMENTS

Parameter | Type | Required | Description
--------- | ------- | ------- | -----------
user_id | integer | yes | The ID of the user which owns the currency holdings, provided in URL path
exclude_empty | boolean | no | If set to true, currency holding public private pairs where neither holding has an amount_atomic value greater than zero will be excluded from the results. By default this is set to false. 

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the currency holding
currency-id | The ID of the currency that the currency holding holds
currency-name | The name of the currency that the currency holding holds
currency-icon-url | The URL at which the icon picture of the currency that the currency holding holds can be found
currency-burn-rate | The annual rate at which the currency contained within the currency holding burns, by basis point (100 = 1%) 
currency-daily-burn-rate | The daily rate at which the currency contained within the public currency holding burns, by fraction of 1 (0.01 = 1%) 
store-count | The number of stores associated with the currency
amount-atomic | The amount of currency held in the currency holding, in atomic units (each whole unit is composed of 10^10 atomic units)
burn-amount-out | The total amount that has been debited from the public currency holding as a result of the daily burnrate of the currency 
is-issuer-active | Whether the issuer of the currency is active
issuer-user-id | The ID of the user that issues the currency
issuer-user-name | The username of the user that issues the currency
issuer-user-avatar-url | The URL of the avatar of the user that issues the currency
created-at | The time and date when the public currency holding was created
updated-at | The time and date when the public currency holding was last updated

## List User's Externally Issued Currency Holdings with Authorization

```shell
curl 'https://api.mycurrency.com/users/4/authorized_externally_issued_currency_holdings' \
  -H 'Accept: application/json' -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer j47lbjj8r9n5yy8mup6cxqc8h70yvhnilm0g84kg0raqckus0k1koj9f75ao'
```

> The above command returns JSON structured like this:

```json
{
  "data": [{
      "currency-holding-pair": {
        "data": [{
            "id": 14,
            "type": "PrivateCurrencyHolding",
            "attributes": {
              "currency-id": 1,
              "currency-name": "Micro Asteroid bucks",
              "currency-icon-url": "/icons/original/missing.png",
              "currency-burn-rate": 500,
              "currency-daily-burn-rate": "0.00014052",
              "store_count": 1,
              "amount-atomic": 800500000000000,
              "burn-amount-out": 0,
              "is-issuer-active": true,
              "issuer-user-id": 3,
              "issuer-user-name": "Hannibal",
              "issuer-user-avatar-url": "/avatars/original/missing.png",
              "created-at": "2018-11-30 23:04:50 -0800",
              "updated-at": "2019-06-12 03:56:21 -0700"
            }
          },
          {
            "id": 13,
            "type": "PublicCurrencyHolding",
            "attributes": {
              "currency-id": 1,
              "currency-name": "Micro Asteroid bucks",
              "currency-icon-url": "/icons/original/missing.png",
              "currency-burn-rate": 500,
              "currency-daily-burn-rate": "0.00014052",
              "store_count": 1,
              "amount-atomic": 500000000000,
              "burn-amount-out": 0,
              "is-issuer-active": true,
              "issuer-user-id": 3,
              "issuer-user-name": "Hannibal",
              "issuer-user-avatar-url": "/avatars/original/missing.png",
              "created-at": "2019-06-12 03:45:36 -0700",
              "updated-at": "2019-06-12 03:56:21 -0700"
            }
          }
        ]
      }
    },
    {
      "currency-holding-pair": {
        "data": [{
            "id": 8,
            "type": "PrivateCurrencyHolding",
            "attributes": {
              "currency-id": 4,
              "currency-name": "spiderman pizza dollars",
              "currency-icon-url": "/icons/original/missing.png",
              "currency-burn-rate": 420,
              "currency-daily-burn-rate": "0.000117548",
              "store_count": 0,
              "amount-atomic": 10496473974509,
              "burn-amount-out": 3526025491,
              "is-issuer-active": true,
              "issuer-user-id": 2,
              "issuer-user-name": "spiderman",
              "issuer-user-avatar-url": "/avatars/original/missing.png",
              "created-at": "2018-11-05 13:27:52 -0800",
              "updated-at": "2019-06-12 03:55:15 -0700"
            }
          },
          {
            "id": 16,
            "type": "PublicCurrencyHolding",
            "attributes": {
              "currency-id": 4,
              "currency-name": "spiderman pizza dollars",
              "currency-icon-url": "/icons/original/missing.png",
              "currency-burn-rate": 420,
              "currency-daily-burn-rate": "0.000117548",
              "store_count": 0,
              "amount-atomic": 500000000000,
              "burn-amount-out": 0,
              "is-issuer-active": true,
              "issuer-user-id": 2,
              "issuer-user-name": "spiderman",
              "issuer-user-avatar-url": "/avatars/original/missing.png",
              "created-at": "2019-06-12 03:55:15 -0700",
              "updated-at": "2019-06-12 03:55:15 -0700"
            }
          }
        ]
      }
    }
  ],
  "meta": {
    "user-data": {
      "number-of-reviews": 23,
      "currency-count": 6
    }
  }
}
```

This endpoint retrieves the full details of all of a user's public and private holdings of currencies that the user is not the issuer of, grouped in sets of up to two holdings containing the same currency 

### HTTP Request

`GET https://api.mycurrency.com/users/<USER-ID>/authorized_externally_issued_currency_holdings`

<aside class="notice">
Authentication: the request requires the OAuth access-token associated with the User referenced by the ID 
</aside>

### ARGUMENTS

Parameter | Type | Required | Description
--------- | ------- | ------- | -----------
user_id | integer | yes | The ID of the user which owns the currency holdings, provided in URL path
exclude_empty | boolean | no | If set to true, currency holding public private pairs where neither holding has an amount_atomic value greater than zero will be excluded from the results. By default this is set to false. 

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the currency holding
currency-id | The ID of the currency that the currency holding holds
currency-name | The name of the currency that the currency holding holds
currency-icon-url | The URL at which the icon picture of the currency that the currency holding holds can be found
currency-burn-rate | The annual rate at which the currency contained within the currency holding burns, by basis point (100 = 1%) 
currency-daily-burn-rate | The daily rate at which the currency contained within the public currency holding burns, by fraction of 1 (0.01 = 1%) 
store-count | The number of stores associated with the currency
amount-atomic | The amount of currency held in the currency holding, in atomic units (each whole unit is composed of 10^10 atomic units)
burn-amount-out | The total amount that has been debited from the public currency holding as a result of the daily burnrate of the currency 
is-issuer-active | Whether the issuer of the currency is active
issuer-user-id | The ID of the user that issues the currency
issuer-user-name | The username of the user that issues the currency
issuer-user-avatar-url | The URL of the avatar of the user that issues the currency
created-at | The time and date when the public currency holding was created
updated-at | The time and date when the public currency holding was last updated

## List User's Self-Issued Combined Currency Holdings with Authorization

```shell
curl 'https://api.mycurrency.com/users/3/authorized_self_issued_combined_currency_holdings' \
  -H 'Accept: application/json' -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer j47lbjj8r9n5yy8mup6cxqc8h70yvhnilm0g84kg0raqckus0k1koj9f75ao'
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": "1",
      "type": "combined-currency-holdings",
      "attributes": {
        "currency-id": 1,
        "currency-name": "Micro Asteroid bucks",
        "currency-icon-url": "/system/currencies/icons/missing.png",
        "currency-burn-rate": 450,
        "currency-daily-burn-rate": "0.00012614",
        "store-count": 2,
        "is-issuer-active": true,
        "issuer-user-id": 3,
        "issuer-user-name": "Hannibal",
        "issuer-user-avatar-url": "/system/users/avatars/000/000/003/original/avatar.jpg?1562578009",
        "issuer-public-currency-holding-id": 2,
        "public-currency-holding-id": 2,
        "public-currency-holding-amount-atomic": 3599957849922,
        "private-currency-holding-id": 1,
        "private-currency-holding-amount-atomic": 6645827142424,
        "total-burn-amount-atomic": 47666191538,
        "amount-atomic": 10245784992346
      }
    },
    {
      "id": "60",
      "type": "combined-currency-holdings",
      "attributes": {
        "currency-id": 60,
        "currency-name": "Hoola Hoop Cash",
        "currency-icon-url": "/system/currencies/icons/000/000/060/original/currency.jpg?1562578289",
        "currency-burn-rate": 500,
        "currency-daily-burn-rate": "0.00014052",
        "store-count": 0,
        "is-issuer-active": true,
        "issuer-user-id": 3,
        "issuer-user-name": "Hannibal",
        "issuer-user-avatar-url": "/system/users/avatars/000/000/003/original/avatar.jpg?1562578009",
        "issuer-public-currency-holding-id": 50,
        "public-currency-holding-id": 50,
        "public-currency-holding-amount-atomic": 2400000000000,
        "private-currency-holding-id": 107,
        "private-currency-holding-amount-atomic": 6600000000000,
        "total-burn-amount-atomic": 35091980457,
        "amount-atomic": 9000000000000
      }
    },
    {
      "id": "74",
      "type": "combined-currency-holdings",
      "attributes": {
        "currency-id": 74,
        "currency-name": "sam dollar",
        "currency-icon-url": "/system/currencies/icons/000/000/074/original/currency.jpg?1563139948",
        "currency-burn-rate": 0,
        "currency-daily-burn-rate": "0.0",
        "store-count": 0,
        "is-issuer-active": true,
        "issuer-user-id": 3,
        "issuer-user-name": "Hannibal",
        "issuer-user-avatar-url": "/system/users/avatars/000/000/003/original/avatar.jpg?1562578009",
        "issuer-public-currency-holding-id": 53,
        "public-currency-holding-id": 53,
        "public-currency-holding-amount-atomic": 3000000000000,
        "private-currency-holding-id": 134,
        "private-currency-holding-amount-atomic": 4000000000000,
        "total-burn-amount-atomic": 9977028307,
        "amount-atomic": 7000000000000
      }
    },
    {
      "id": "75",
      "type": "combined-currency-holdings",
      "attributes": {
        "currency-id": 75,
        "currency-name": "Saint Patricks Day Money",
        "currency-icon-url": "/system/currencies/icons/000/000/075/original/currency.jpg?1563341979",
        "currency-burn-rate": 1000,
        "currency-daily-burn-rate": "0.000288618",
        "store-count": 0,
        "is-issuer-active": true,
        "issuer-user-id": 3,
        "issuer-user-name": "Hannibal",
        "issuer-user-avatar-url": "/system/users/avatars/000/000/003/original/avatar.jpg?1562578009",
        "issuer-public-currency-holding-id": 122,
        "public-currency-holding-id": 122,
        "public-currency-holding-amount-atomic": 0,
        "private-currency-holding-id": 143,
        "private-currency-holding-amount-atomic": 10000000000000,
        "total-burn-amount-atomic": 4581322108,
        "amount-atomic": 10000000000000
      }
    },
    {
      "id": "86",
      "type": "combined-currency-holdings",
      "attributes": {
        "currency-id": 86,
        "currency-name": "Hastings-Sunrise dollars",
        "currency-icon-url": "/system/currencies/icons/000/000/086/original/currency.jpg?1565312742",
        "currency-burn-rate": 300,
        "currency-daily-burn-rate": "0.000083447",
        "store-count": 0,
        "is-issuer-active": true,
        "issuer-user-id": 3,
        "issuer-user-name": "Hannibal",
        "issuer-user-avatar-url": "/system/users/avatars/000/000/003/original/avatar.jpg?1562578009",
        "issuer-public-currency-holding-id": 128,
        "public-currency-holding-id": 128,
        "public-currency-holding-amount-atomic": 0,
        "private-currency-holding-id": 169,
        "private-currency-holding-amount-atomic": 10000000000000,
        "total-burn-amount-atomic": 1842388131,
        "amount-atomic": 10000000000000
      }
    }
  ],
  "links": {
    "self": "https://api.mycurrency.com/users/3/authorized_self_issued_combined_currency_holdings?",
    "first": "https://api.mycurrency.com/users/3/authorized_self_issued_combined_currency_holdings?page=1&per_page=25",
    "prev": null,
    "next": null,
    "last": "https://api.mycurrency.com/users/3/authorized_self_issued_combined_currency_holdings?page=1&per_page=25"
  },
  "meta": {
    "pagination": {
      "per-page": null,
      "total-pages": "1",
      "total-count": "5"
    },
    "user-data": {
      "number-of-reviews": 1,
      "currency-count": 5
    },
    "authorized-externally-issued-combined-currency-holdings-data": {
      "count": 10
    }
  }
}
```

This endpoint retrieves the details of all of a user's public and private holdings of currencies that the user is also the issuer of, with a combined amount-atomic value showing the sum of units in the holding pair.

### HTTP Request

`GET https://api.mycurrency.com/users/<USER-ID>/authorized_self_issued_combined_currency_holdings`

<aside class="notice">
Authentication: the request requires the OAuth access-token associated with the User referenced by the ID 
</aside>

### ARGUMENTS

Parameter | Type | Required | Description
--------- | ------- | ------- | -----------
user_id | integer | yes | The ID of the user which owns the currency holdings, provided in URL path
exclude_empty | boolean | no | If set to true, currency holding public private pairs where neither holding has an amount_atomic value greater than zero will be excluded from the results. By default this is set to false. 

### RESPONSE

### COMBINED CURRENCY HOLDING

Parameter | Description
--------- | ----------- 
id | The ID of the currency holding currency-id | The ID of the currency that the currency holding holds
currency-name | The name of the currency that the currency holding holds
currency-icon-url | The URL at which the icon picture of the currency that the currency holding holds can be found
currency-burn-rate | The annual rate at which the currency contained within the currency holding burns, by basis point (100 = 1%) 
currency-daily-burn-rate | The daily rate at which the currency contained within the currency holding burns, by fraction of 1 (0.01 = 1%) 
store-count | The number of stores associated with the currency
is-issuer-active | Whether the issuer of the currency is active
issuer-user-id | The ID of the user that issues the currency
issuer-user-name | The username of the user that issues the currency
issuer-user-avatar-url | The URL of the avatar of the user that issues the currency
issuer-public-currency-holding-id | The user ID of the public currency holding of the issuer of the currency in the holding pair
public-currency-holding-id | The ID of the user's public currency holding of the specified currency
public-currency-holding-amount-atomic | The amount of currency held in the public holding of the specified currency, in atomic units (each whole unit is composed of 10^10 atomic units)
private-currency-holding-id | The ID of the user's private currency holding of the specified currency
private-currency-holding-amount-atomic | The amount of currency held in the private holding of the specified currency, in atomic units (each whole unit is composed of 10^10 atomic units)
total-burn-amount-atomic | The total amount of currency burned to date in both the private and public holding of the specified currency, in atomic units (each whole unit is composed of 10^10 atomic units) 
amount-atomic | The amount of currency held in both the private and public holding of the specified currency, in atomic units (each whole unit is composed of 10^10 atomic units)

### USER INFO

Parameter | Description
--------- | -----------
number-of-reviews | The number of store reviews received by stores owned by the logged-in user
currency-count | The number of currencies owned by the logged-in user

### EXTERNALLY ISSUED CURRENCY HOLDINGS INFO

Parameter | Description
--------- | -----------
count | The number of externally issued currencies the logged-in user has

## List User's Externally Issued Combined Currency Holdings with Authorization

```shell
curl 'https://api.mycurrency.com/users/3/authorized_externally_issued_combined_currency_holdings?per_page=5' \
  -H 'Accept: application/json' -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer j47lbjj8r9n5yy8mup6cxqc8h70yvhnilm0g84kg0raqckus0k1koj9f75ao'
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": "2",
      "type": "combined-currency-holdings",
      "attributes": {
        "currency-id": 2,
        "currency-name": "solar electricity zaps",
        "currency-icon-url": "/system/currencies/icons/missing.png",
        "currency-burn-rate": 400,
        "currency-daily-burn-rate": "0.000111835",
        "store-count": 2,
        "is-issuer-active": false,
        "issuer-user-id": 4,
        "issuer-user-name": "ScipioAfricanus",
        "issuer-user-avatar-url": "/system/users/avatars/000/000/004/original/1.jpg?1559736060",
        "issuer-public-currency-holding-id": 42,
        "public-currency-holding-id": 15,
        "public-currency-holding-amount-atomic": 0,
        "private-currency-holding-id": 3,
        "private-currency-holding-amount-atomic": 10009994565314,
        "total-burn-amount-atomic": 14788763198,
        "amount-atomic": 10009994565314
      }
    },
    {
      "id": "3",
      "type": "combined-currency-holdings",
      "attributes": {
        "currency-id": 3,
        "currency-name": "Moon hotel coins",
        "currency-icon-url": "/system/currencies/icons/missing.png",
        "currency-burn-rate": 550,
        "currency-daily-burn-rate": "0.000154976",
        "store-count": 1,
        "is-issuer-active": false,
        "issuer-user-id": 4,
        "issuer-user-name": "ScipioAfricanus",
        "issuer-user-avatar-url": "/system/users/avatars/000/000/004/original/1.jpg?1559736060",
        "issuer-public-currency-holding-id": 68,
        "public-currency-holding-id": 4,
        "public-currency-holding-amount-atomic": 5997675720243,
        "private-currency-holding-id": 6,
        "private-currency-holding-amount-atomic": 4197675720243,
        "total-burn-amount-atomic": 57565603087,
        "amount-atomic": 10195351440486
      }
    },
    {
      "id": "4",
      "type": "combined-currency-holdings",
      "attributes": {
        "currency-id": 4,
        "currency-name": "spiderman pizza dollars",
        "currency-icon-url": "/system/currencies/icons/missing.png",
        "currency-burn-rate": 420,
        "currency-daily-burn-rate": "0.000117548",
        "store-count": 3,
        "is-issuer-active": true,
        "issuer-user-id": 2,
        "issuer-user-name": "spiderman",
        "issuer-user-avatar-url": "/system/users/avatars/original/missing.png",
        "issuer-public-currency-holding-id": 54,
        "public-currency-holding-id": 6,
        "public-currency-holding-amount-atomic": 1899118493626,
        "private-currency-holding-id": 9,
        "private-currency-holding-amount-atomic": 2119118493626,
        "total-burn-amount-atomic": 3303335834,
        "amount-atomic": 4018236987252
      }
    },
    {
      "id": "5",
      "type": "combined-currency-holdings",
      "attributes": {
        "currency-id": 5,
        "currency-name": "Home Repair dollars",
        "currency-icon-url": "/system/currencies/icons/missing.png",
        "currency-burn-rate": 450,
        "currency-daily-burn-rate": "0.00012614",
        "store-count": 0,
        "is-issuer-active": false,
        "issuer-user-id": 4,
        "issuer-user-name": "ScipioAfricanus",
        "issuer-user-avatar-url": "/system/users/avatars/000/000/004/original/1.jpg?1559736060",
        "issuer-public-currency-holding-id": 69,
        "public-currency-holding-id": null,
        "public-currency-holding-amount-atomic": null,
        "private-currency-holding-id": 13,
        "private-currency-holding-amount-atomic": 5098738679556,
        "total-burn-amount-atomic": 41983449141,
        "amount-atomic": 5098738679556
      }
    },
    {
      "id": "6",
      "type": "combined-currency-holdings",
      "attributes": {
        "currency-id": 6,
        "currency-name": "Wholesome foods tokens",
        "currency-icon-url": "/system/currencies/icons/missing.png",
        "currency-burn-rate": 710,
        "currency-daily-burn-rate": "0.000201751",
        "store-count": 0,
        "is-issuer-active": false,
        "issuer-user-id": 4,
        "issuer-user-name": "ScipioAfricanus",
        "issuer-user-avatar-url": "/system/users/avatars/000/000/004/original/1.jpg?1559736060",
        "issuer-public-currency-holding-id": 70,
        "public-currency-holding-id": null,
        "public-currency-holding-amount-atomic": null,
        "private-currency-holding-id": 12,
        "private-currency-holding-amount-atomic": 13995965387034,
        "total-burn-amount-atomic": 22460541440,
        "amount-atomic": 13995965387034
      }
    },
    {
      "id": "8",
      "type": "combined-currency-holdings",
      "attributes": {
        "currency-id": 8,
        "currency-name": "Alex Token",
        "currency-icon-url": "/system/currencies/icons/missing.png",
        "currency-burn-rate": 350,
        "currency-daily-burn-rate": "0.000097604",
        "store-count": 0,
        "is-issuer-active": true,
        "issuer-user-id": 9,
        "issuer-user-name": "alex",
        "issuer-user-avatar-url": "/system/users/avatars/original/missing.png",
        "issuer-public-currency-holding-id": 72,
        "public-currency-holding-id": 52,
        "public-currency-holding-amount-atomic": 400000000000,
        "private-currency-holding-id": 94,
        "private-currency-holding-amount-atomic": 2600000000000,
        "total-burn-amount-atomic": 40194182911,
        "amount-atomic": 3000000000000
      }
    },
    {
      "id": "9",
      "type": "combined-currency-holdings",
      "attributes": {
        "currency-id": 9,
        "currency-name": "Alabama steak coins",
        "currency-icon-url": "/system/currencies/icons/missing.png",
        "currency-burn-rate": 550,
        "currency-daily-burn-rate": "0.000154976",
        "store-count": 1,
        "is-issuer-active": false,
        "issuer-user-id": 4,
        "issuer-user-name": "ScipioAfricanus",
        "issuer-user-avatar-url": "/system/users/avatars/000/000/004/original/1.jpg?1559736060",
        "issuer-public-currency-holding-id": 11,
        "public-currency-holding-id": null,
        "public-currency-holding-amount-atomic": null,
        "private-currency-holding-id": 106,
        "private-currency-holding-amount-atomic": 1000000000000,
        "total-burn-amount-atomic": 8511474011,
        "amount-atomic": 1000000000000
      }
    },
    {
      "id": "10",
      "type": "combined-currency-holdings",
      "attributes": {
        "currency-id": 10,
        "currency-name": "Turbo points",
        "currency-icon-url": "/system/currencies/icons/missing.png",
        "currency-burn-rate": 600,
        "currency-daily-burn-rate": "0.000169508",
        "store-count": 1,
        "is-issuer-active": false,
        "issuer-user-id": 4,
        "issuer-user-name": "ScipioAfricanus",
        "issuer-user-avatar-url": "/system/users/avatars/000/000/004/original/1.jpg?1559736060",
        "issuer-public-currency-holding-id": 12,
        "public-currency-holding-id": 14,
        "public-currency-holding-amount-atomic": 0,
        "private-currency-holding-id": 23,
        "private-currency-holding-amount-atomic": 5600000000000,
        "total-burn-amount-atomic": 15195784813,
        "amount-atomic": 5600000000000
      }
    },
    {
      "id": "21",
      "type": "combined-currency-holdings",
      "attributes": {
        "currency-id": 21,
        "currency-name": "new",
        "currency-icon-url": "/system/currencies/icons/000/000/021/original/currency.jpg?1561624253",
        "currency-burn-rate": 500,
        "currency-daily-burn-rate": "0.00014052",
        "store-count": 1,
        "is-issuer-active": true,
        "issuer-user-id": 5,
        "issuer-user-name": "Kostya",
        "issuer-user-avatar-url": "/system/users/avatars/000/000/005/original/avatar.jpg?1561060914",
        "issuer-public-currency-holding-id": 19,
        "public-currency-holding-id": null,
        "public-currency-holding-amount-atomic": null,
        "private-currency-holding-id": 97,
        "private-currency-holding-amount-atomic": 0,
        "total-burn-amount-atomic": 0,
        "amount-atomic": 0
      }
    },
    {
      "id": "57",
      "type": "combined-currency-holdings",
      "attributes": {
        "currency-id": 57,
        "currency-name": "Rails Programming Dollars",
        "currency-icon-url": "/system/currencies/icons/000/000/057/original/currency.jpg?1562376330",
        "currency-burn-rate": 500,
        "currency-daily-burn-rate": "0.00014052",
        "store-count": 0,
        "is-issuer-active": false,
        "issuer-user-id": 4,
        "issuer-user-name": "ScipioAfricanus",
        "issuer-user-avatar-url": "/system/users/avatars/000/000/004/original/1.jpg?1559736060",
        "issuer-public-currency-holding-id": 107,
        "public-currency-holding-id": null,
        "public-currency-holding-amount-atomic": null,
        "private-currency-holding-id": 90,
        "private-currency-holding-amount-atomic": 3000000000000,
        "total-burn-amount-atomic": 0,
        "amount-atomic": 3000000000000
      }
    }
  ],
  "links": {
    "self": "https://api.mycurrency.com/users/3/authorized_externally_issued_combined_currency_holdings?",
    "first": "https://api.mycurrency.com/users/3/authorized_externally_issued_combined_currency_holdings?page=1&per_page=25",
    "prev": null,
    "next": null,
    "last": "https://api.mycurrency.com/users/3/authorized_externally_issued_combined_currency_holdings?page=1&per_page=25"
  },
  "meta": {
    "pagination": {
      "per-page": null,
      "total-pages": "1",
      "total-count": "10"
    },
    "user-data": {
      "number-of-reviews": 1,
      "currency-count": 5
    },
    "authorized-externally-issued-combined-currency-holdings-data": {
      "count": 10
    }
  }
}
```

This endpoint retrieves the details of all of a user's public and private holdings of currencies that the user is not the issuer of, with a combined amount-atomic value showing the sum of units in the holding pair.

### HTTP Request

`GET https://api.mycurrency.com/users/<USER-ID>/authorized_externally_issued_combined_currency_holdings`

<aside class="notice">
Authentication: the request requires the OAuth access-token associated with the User referenced by the ID 
</aside>

### ARGUMENTS

Parameter | Type | Required | Description
--------- | ------- | ------- | -----------
user_id | integer | yes | The ID of the user which owns the currency holdings, provided in URL path
exclude_empty | boolean | no | If set to true, currency holding public private pairs where neither holding has an amount_atomic value greater than zero will be excluded from the results. By default this is set to false. 

### RESPONSE

### COMBINED CURRENCY HOLDING

Parameter | Description
--------- | -----------
id | The ID of the currency holding
currency-id | The ID of the currency that the currency holding holds
currency-name | The name of the currency that the currency holding holds
currency-icon-url | The URL at which the icon picture of the currency that the currency holding holds can be found
currency-burn-rate | The annual rate at which the currency contained within the currency holding burns, by basis point (100 = 1%) 
currency-daily-burn-rate | The daily rate at which the currency contained within the currency holding burns, by fraction of 1 (0.01 = 1%) 
store-count | The number of stores associated with the currency
is-issuer-active | Whether the issuer of the currency is active
issuer-user-id | The ID of the user that issues the currency
issuer-user-name | The username of the user that issues the currency
issuer-user-avatar-url | The URL of the avatar of the user that issues the currency
issuer-public-currency-holding-id | The user ID of the public currency holding of the issuer of the currency in the holding pair
public-currency-holding-id | The ID of the user's public currency holding of the specified currency
public-currency-holding-amount-atomic | The amount of currency held in the public holding of the specified currency, in atomic units (each whole unit is composed of 10^10 atomic units)
private-currency-holding-id | The ID of the user's private currency holding of the specified currency
private-currency-holding-amount-atomic | The amount of currency held in the private holding of the specified currency, in atomic units (each whole unit is composed of 10^10 atomic units)
total-burn-amount-atomic | The total amount of currency burned to date in both the private and public holding of the specified currency, in atomic units (each whole unit is composed of 10^10 atomic units) 
amount-atomic | The amount of currency held in both the private and public holding of the specified currency, in atomic units (each whole unit is composed of 10^10 atomic units)

### USER INFO

Parameter | Description
--------- | -----------
number-of-reviews | The number of store reviews received by stores owned by the logged-in user
currency-count | The number of currencies owned by the logged-in user

### EXTERNALLY ISSUED CURRENCY HOLDINGS INFO

Parameter | Description
--------- | -----------
count | The number of externally issued currencies the logged-in user has

# Public Currency Holdings

Unlike private currency holdings, the basic information of public currency holdings, like account balance, is publicly accessible. Authorized endpoints are only accessible to the user that owns the public currency holding and provides the full details of the holding. The publicly accessible endpoints provide basic information about the public currency holding.

## Get a Public Currency Holding

```shell
curl 'https://api.mycurrency.com/users/3/public_currency_holdings/2' \
  -H 'Accept: application/json' -H 'Content-Type: application/json'
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "id": "2",
    "type": "public-currency-holdings",
    "attributes": {
      "owning-user-id": 3,
      "currency-id": 1,
      "currency-name": "Micro Asteroid bucks",
      "currency-icon-url": "/icons/original/missing.png",
      "amount-atomic": 2049957849922,
      "is-issuer-active": true,
      "currency-burn-rate": 500,
      "currency-daily-burn-rate": "0.00014052",
      "store-count": 1,
      "issuer-user-id": 3,
      "issuer-user-name": "Hannibal",
      "issuer-user-avatar-url": "/avatars/original/missing.png"
    }
  }
}
```

This endpoint retrieves a particular publicly viewable currency holding. 

### HTTP Request

`GET https://api.mycurrency.com/users/<USER-ID>/public_currency_holdings/<ID>`

<aside class="notice">
Authentication: not required
</aside>

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the public currency holding
owning-user-id | The ID of the user that the public currency holding belongs to
currency-id | The ID of the currency that the public currency holding holds
currency-name | The name of the currency that the public currency holding holds
currency-icon-url | The URL at which the icon picture of the public currency that the currency holding holds can be found
amount-atomic | The amount of currency held in the public currency holding, in atomic units (each whole unit is composed of 10^10 atomic units)
is-issuer-active | Whether the user that issues the currency holder is active
currency-burn-rate | The annual burn rate of the currency in the holding
currency-daily-burn-rate | The daily burn rate of the currency in the holding
store-count | The number of stores associated with the currency in the holding
issuer-user-id | The ID of the user that issues the currency in the holding
issuer-user-name | The username of the user that issues the currency in the holding 
issuer-user-avatar-url | The URL of the user that issues the currency in the holding 

## List User's Public Self-Issued Currency Holdings 

```shell
curl 'https://api.mycurrency.com/users/3/self_issued_public_currency_holdings' \
  -H 'Accept: application/json' -H 'Content-Type: application/json'
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": "11",
      "type": "public-currency-holdings",
      "attributes": {
        "owning-user-id": 4,
        "currency-id": 9,
        "currency-name": "Alabama steak coins",
        "currency-icon-url": "/icons/original/missing.png",
        "amount-atomic": 80000000000000,
        "currency-burn-rate": 550,
        "currency-daily-burn-rate": "0.000154976",
        "store-count": 1
      }
    },
    {
      "id": "12",
      "type": "public-currency-holdings",
      "attributes": {
        "owning-user-id": 4,
        "currency-id": 10,
        "currency-name": "Turbo points",
        "currency-icon-url": "/icons/original/missing.png",
        "amount-atomic": 62000000000000,
        "currency-burn-rate": 600,
        "currency-daily-burn-rate": "0.000169508",
        "store-count": 1
      }
    }
  ],
  "links": {
    "self": "https://api.mycurrency.com/users/4/self_issued_public_currency_holdings?",
    "first": "https://api.mycurrency.com/users/4/self_issued_public_currency_holdings?page=1&per_page=25",
    "prev": null,
    "next": null,
    "last": "https://api.mycurrency.com/users/4/self_issued_public_currency_holdings?page=1&per_page=25"
  },
  "meta": {
    "pagination": {
      "per-page": null,
      "total-pages": "1",
      "total-count": "2"
    }
  }
}
```

This endpoint retrieves all of a user's publicly viewable holdings of currencies that the user is also the issuer of.

### HTTP Request

`GET https://api.mycurrency.com/users/<USER-ID>/self_issued_public_currency_holdings`

<aside class="notice">
Authentication: not required
</aside>

### ARGUMENTS

Parameter | Type | Required | Description
--------- | ------- | ------- | -----------
user_id | integer | yes | The ID of the user which owns the currency holdings, provided in URL path
min_amount | integer | no | The set of currency holdings returned will only include those with balances exceeding min_amount. By default all currency holdings are returned, including those with a balance of zero

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the public currency holding
owning-user-id | The ID of the user that the public currency holding belongs to
currency-id | The ID of the currency that the public currency holding holds
currency-name | The name of the currency that the public currency holding holds
currency-icon-url | The URL at which the icon picture of the public currency that the currency holding holds can be found
amount-atomic | The amount of currency held in the public currency holding, in atomic units (each whole unit is composed of 10^10 atomic units)
is-issuer-active | Whether the user that issues the currency holder is active
currency-burn-rate | The annual burn rate of the currency in the holding
currency-daily-burn-rate | The daily burn rate of the currency in the holding
store-count | The number of stores associated with the currency in the holding

## List User's Public Externally Issued Currency Holdings 

```shell
curl 'https://api.mycurrency.com/users/4/externally_issued_public_currency_holdings' \
  -H 'Accept: application/json' -H 'Content-Type: application/json'
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": "13",
      "type": "public-currency-holdings",
      "attributes": {
        "owning-user-id": 4,
        "currency-id": 1,
        "currency-name": "Micro Asteroid bucks",
        "currency-icon-url": "/icons/original/missing.png",
        "amount-atomic": 500000000000,
        "is-issuer-active": true,
        "currency-burn-rate": 500,
        "currency-daily-burn-rate": "0.00014052",
        "store-count": 1,
        "issuer-user-id": 3,
        "issuer-user-name": "Hannibal",
        "issuer-user-avatar-url": "/avatars/original/missing.png"
      }
    },
    {
      "id": "16",
      "type": "public-currency-holdings",
      "attributes": {
        "owning-user-id": 4,
        "currency-id": 4,
        "currency-name": "spiderman pizza dollars",
        "currency-icon-url": "/icons/original/missing.png",
        "amount-atomic": 500000000000,
        "is-issuer-active": true,
        "currency-burn-rate": 420,
        "currency-daily-burn-rate": "0.000117548",
        "store-count": 0,
        "issuer-user-id": 2,
        "issuer-user-name": "spiderman",
        "issuer-user-avatar-url": "/avatars/original/missing.png"
      }
    }
  ],
  "meta": {
    "pagination": {
      "per-page": null,
      "total-pages": "1",
      "total-count": "2"
    }
  }
}
```

This endpoint retrieves all of a user's publicly viewable holdings of currencies that the user is not the issuer of.

### HTTP Request

`GET https://api.mycurrency.com/users/<USER-ID>/externally_issued_public_currency_holdings`

<aside class="notice">
Authentication: not required
</aside>

### ARGUMENTS

Parameter | Type | Required | Description
--------- | ------- | ------- | -----------
user_id | integer | yes | The ID of the user which owns the currency holdings, provided in URL path
min_amount | integer | no | The set of currency holdings returned will only include those with balances exceeding min_amount. The default min_amount is zero resulting in currency holdings with a zero balance not being returned.

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the public currency holding
owning-user-id | The ID of the user that the public currency holding belongs to
currency-id | The ID of the currency that the public currency holding holds
currency-name | The name of the currency that the public currency holding holds
currency-icon-url | The URL at which the icon picture of the public currency that the currency holding holds can be found
amount-atomic | The amount of currency held in the public currency holding, in atomic units (each whole unit is composed of 10^10 atomic units)
is-issuer-active | Whether the user that issues the currency holder is active
currency-burn-rate | The annual burn rate of the currency in the holding
currency-daily-burn-rate | The daily burn rate of the currency in the holding
store-count | The number of stores associated with the currency in the holding
issuer-user-id | The ID of the user that issues the currency in the holding
issuer-user-name | The username of the user that issues the currency in the holding 
issuer-user-avatar-url | The URL of the user that issues the currency in the holding 

## List Public Holdings of Currency

```shell
curl 'https://api.mycurrency.com/currencies/4/public_currency_holdings' \
  -H 'Accept: application/json' -H 'Content-Type: application/json'
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": "5",
      "type": "public-currency-holdings",
      "attributes": {
        "owning-user-id": 1,
        "currency-id": 4,
        "currency-name": "spiderman pizza dollars",
        "currency-icon-url": "/icons/original/missing.png",
        "amount-atomic": 999647397450,
        "is-holder-active": true,
        "currency-burn-rate": 420,
        "currency-daily-burn-rate": "0.000117548",
        "store-count": 0,
        "owning-user-name": "admin",
        "owning-user-avatar-url": "/avatars/original/missing.png"
      }
    },
    {
      "id": "6",
      "type": "public-currency-holdings",
      "attributes": {
        "owning-user-id": 3,
        "currency-id": 4,
        "currency-name": "spiderman pizza dollars",
        "currency-icon-url": "/icons/original/missing.png",
        "amount-atomic": 2499118493626,
        "is-holder-active": true,
        "currency-burn-rate": 420,
        "currency-daily-burn-rate": "0.000117548",
        "store-count": 0,
        "owning-user-name": "Hannibal",
        "owning-user-avatar-url": "/avatars/original/missing.png"
      }
    },
    {
      "id": "16",
      "type": "public-currency-holdings",
      "attributes": {
        "owning-user-id": 4,
        "currency-id": 4,
        "currency-name": "spiderman pizza dollars",
        "currency-icon-url": "/icons/original/missing.png",
        "amount-atomic": 500000000000,
        "is-holder-active": true,
        "currency-burn-rate": 420,
        "currency-daily-burn-rate": "0.000117548",
        "store-count": 0,
        "owning-user-name": "ScipioAfricanus",
        "owning-user-avatar-url": "/system/users/avatars/000/000/004/original/1.jpg?1559736060"
      }
    }
  ],
  "links": {
    "self": "https://api.mycurrency.com/currencies/4/public_currency_holdings?",
    "first": "https://api.mycurrency.com/currencies/4/public_currency_holdings?page=1&per_page=25",
    "prev": null,
    "next": null,
    "last": "https://api.mycurrency.com/currencies/4/public_currency_holdings?page=1&per_page=25"
  },
  "meta": {
    "pagination": {
      "per-page": null,
      "total-pages": "1",
      "total-count": "3"
    }
  }
}
```

### HTTP Request

`GET https://api.mycurrency.com/currencies/<CURRENCY-ID>/public_currency_holdings`

<aside class="notice">
Authentication: not required
</aside>

### ARGUMENTS

Parameter | Type | Required | Description
--------- | ------- | ------- | -----------
currency_id | integer | yes | The ID of the currency that the public holdings returned contain, provided in URL path
min_amount | integer | no | The set of currency holdings returned will only include those with balances exceeding min_amount. The default min_amount is zero resulting in currency holdings with a zero balance not being returned.

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the public currency holding
owning-user-id | The ID of the user that the public currency holding belongs to
currency-id | The ID of the currency that the public currency holding holds
currency-name | The name of the currency that the public currency holding holds
currency-icon-url | The URL at which the icon picture of the public currency that the currency holding holds can be found
amount-atomic | The amount of currency held in the public currency holding, in atomic units (each whole unit is composed of 10^10 atomic units)
is-holder-active | Whether the user that owns the currency holder is active
currency-burn-rate | The annual burn rate of the currency in the holding
currency-daily-burn-rate | The daily burn rate of the currency in the holding
store-count | The number of stores associated with the currency in the holding
owning-user-name | The username of the user that the public currency holding belongs to
owning-user-avatar-url | The URL of the user that the public currency holding belongs to

## Get a Public Currency Holding with Authorization

```shell
curl 'https://api.mycurrency.com/users/3/authorized_public_currency_holdings/3' \
  -H 'Accept: application/json' -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer j47lbjj8r9n5yy8mup6cxqc8h70yvhnilm0g84kg0raqckus0k1koj9f75ao'
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "id": "3",
    "type": "public-currency-holdings",
    "attributes": {
      "owning-user-id": 3,
      "owning-user-username": "Hannibal",
      "currency-id": 2,
      "currency-name": "ACME Toon Shop dollars",
      "currency-icon-url": "/system/currencies/icons/000/000/002/original/DaffyDuck.png?1534142996",
      "currency-burn-rate": 450,
      "currency-daily-burn-rate": "0.00012614",
      "amount-atomic": 49918217200,
      "transfer-out": 0,
      "transfer-in": 50000000000,
      "micro-currency-order-out": 0,
      "issuance-in": 0,
      "burn-amount-out": 81782800,
      "created-at": "2018-09-16T13:26:52.023-07:00",
      "updated-at": "2018-09-16T13:26:52.059-07:00"
    }
  }
}
```

This endpoint retrieves the full details of a particular publicly viewable currency holding. 

### HTTP Request

`GET https://api.mycurrency.com/users/<USER-ID>/authorized_public_currency_holdings/<ID>`

<aside class="notice">
Authentication: the request requires the OAuth access-token associated with the User referenced by the ID 
</aside>

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the public currency holding
owning-user-id | The ID of the user that the public currency holding belongs to
owning-user-username | The username of the user that the public currency holding belongs to
currency-id | The ID of the currency that the public currency holding holds
currency-name | The name of the currency that the public currency holding holds
currency-icon-url | The URL at which the icon picture of the public currency that the currency holding holds can be found
currency-burn-rate | The annual rate at which the currency contained within the public currency holding burns, by basis point (100 = 1%) 
currency-daily-burn-rate | The daily rate at which the currency contained within the public currency holding burns, by fraction of 1 (0.01 = 1%) 
amount-atomic | The amount of currency held in the public currency holding, in atomic units (each whole unit is composed of 10^10 atomic units)
transfer-out | The total amount that has been debited from the public currency holding as a result of outgoing transfers
transfer-in | The total amount that has been credited to the public currency holding as a result of incoming transfers
micro-currency-order-out | The total amount that has been debited from the public currency holding as a result of micro_currency_orders 
issuance-in | The total amount that has been credited to the public currency holding as a result of incoming issuances
burn-amount-out | The total amount that has been debited from the public currency holding as a result of the daily burnrate of the currency 
created-at | The time and date when the public currency holding was created
updated-at | The time and date when the public currency holding was last updated

## List User's Public Self-Issued Currency Holdings with Authorization

```shell
curl 'https://api.mycurrency.com/users/3/authorized_self_issued_public_currency_holdings' \
  -H 'Accept: application/json' -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer j47lbjj8r9n5yy8mup6cxqc8h70yvhnilm0g84kg0raqckus0k1koj9f75ao'
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": "3",
      "type": "public-currency-holdings",
      "attributes": {
        "owning-user-id": 3,
        "currency-id": 2,
        "currency-name": "ACME Toon Shop dollars",
        "currency-icon-url": "/system/currencies/icons/000/000/002/original/DaffyDuck.png?1534142996",
        "currency-burn-rate": 450,
        "currency-daily-burn-rate": "0.00012614",
        "amount-atomic": 49918217200,
        "transfer-out": 0,
        "transfer-in": 50000000000,
        "micro-currency-order-out": 0,
        "issuance-in": 0,
        "burn-amount-out": 81782800,
        "created-at": "2018-09-16T13:26:52.023-07:00",
        "updated-at": "2018-09-16T13:26:52.059-07:00"
      }
    },
    {
      "id": "8",
      "type": "public-currency-holdings",
      "attributes": {
        "owning-user-id": 3,
        "currency-id": 6,
        "currency-name": "Diamond dollars",
        "currency-icon-url": "/system/currencies/icons/000/000/006/original/Diamond-coins.png?1534142996",
        "currency-burn-rate": 300,
        "currency-daily-burn-rate": "0.00008345",
        "amount-atomic": 99975465160,
        "transfer-out": 50000000000,
        "transfer-in": 150000000000,
        "micro-currency-order-out": 0,
        "issuance-in": 0,
        "burn-amount-out": 24534840,
        "created-at": "2018-09-17T11:51:21.014-07:00",
        "updated-at": "2018-09-17T11:51:21.014-07:00",
      }
    }
  ],
  "links": {
    "self": "https://api.mycurrency.com/users/3/authorized_self_issued_public_currency_holdings?",
    "first": "https://api.mycurrency.com/users/3/authorized_self_issued_public_currency_holdings?page=1&per_page=25",
    "prev": null,
    "next": null,
    "last": "https://api.mycurrency.com/users/3/authorized_self_issued_public_currency_holdings?page=1&per_page=25"
  },
  "meta": {
    "pagination": {
      "per-page": null,
      "total-pages": "1",
      "total-count": "2"
    }
  }
}
```

This endpoint retrieves the full details of all of a user's publicly viewable holdings of currencies that the user is also the issuer of.

### HTTP Request

`GET https://api.mycurrency.com/users/<USER-ID>/authorized_self_issued_public_currency_holdings`

<aside class="notice">
Authentication: the request requires the OAuth access-token associated with the User referenced by the ID 
</aside>

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the public currency holding
owning-user-id | The ID of the user that the public currency holding belongs to
currency-id | The ID of the currency that the public currency holding holds
currency-name | The name of the currency that the public currency holding holds
currency-icon-url | The URL at which the icon picture of the public currency that the currency holding holds can be found
currency-burn-rate | The annual rate at which the currency contained within the public currency holding burns, by basis point (100 = 1%) 
currency-daily-burn-rate | The daily rate at which the currency contained within the public currency holding burns, by fraction of 1 (0.01 = 1%) 
amount-atomic | The amount of currency held in the public currency holding, in atomic units (each whole unit is composed of 10^10 atomic units)
transfer-out | The total amount that has been debited from the public currency holding as a result of outgoing transfers
transfer-in | The total amount that has been credited to the public currency holding as a result of incoming transfers
micro-currency-order-out | The total amount that has been debited from the public currency holding as a result of micro_currency_orders 
issuance-in | The total amount that has been credited to the public currency holding as a result of incoming issuances
burn-amount-out | The total amount that has been debited from the public currency holding as a result of the daily burnrate of the currency 
created-at | The time and date when the public currency holding was created
updated-at | The time and date when the public currency holding was last updated

## List User's Public Externally Issued Currency Holdings with Authorization

```shell
curl 'https://api.mycurrency.com/users/4/authorized_externally_issued_public_currency_holdings' \
  -H 'Accept: application/json' -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer j47lbjj8r9n5yy8mup6cxqc8h70yvhnilm0g84kg0raqckus0k1koj9f75ao'
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": "2",
      "type": "public-currency-holdings",
      "attributes": {
        "owning-user-id": 4,
        "currency-id": 2,
        "currency-name": "ACME Toon Shop dollars",
        "currency-icon-url": "/system/currencies/icons/000/000/002/original/DaffyDuck.png?1534142996",
        "currency-burn-rate": 450,
        "currency-daily-burn-rate": "0.00012614",
        "amount-atomic": 119942752040,
        "transfer-out": 80000000000,
        "transfer-in": 200000000000,
        "micro-currency-order-out": 0,
        "issuance-in": 0,
        "burn-amount-out": 57247960,
        "created-at": "2018-09-13T01:15:41.041-07:00",
        "updated-at": "2018-09-13T01:15:41.041-07:00",
      }
    },
    {
      "id": "4",
      "type": "public-currency-holdings",
      "attributes": {
        "owning-user-id": 4,
        "currency-id": 3,
        "currency-name": "Horizon Cloud Computing dollars",
        "currency-icon-url": "/system/currencies/icons/000/000/003/original/horizon_dollars.png?1534142996",
        "currency-burn-rate": 420,
        "currency-daily-burn-rate": "0.00011755",
        "amount-atomic": 79983643440,
        "transfer-out": 80000000000,
        "transfer-in": 160000000000,
        "micro-currency-order-out": 0,
        "issuance-in": 0,
        "burn-amount-out": 16356560,
        "created-at": "2018-09-13T01:15:41.041-07:00",
        "updated-at": "2018-09-13T01:15:41.041-07:00",
      }
    }
  ],
  "links": {
    "self": "https://api.mycurrency.com/users/4/authorized_externally_issued_public_currency_holdings?",
    "first": "https://api.mycurrency.com/users/4/authorized_externally_issued_public_currency_holdings?page=1&per_page=25",
    "prev": null,
    "next": null,
    "last": "https://api.mycurrency.com/users/4/authorized_externally_issued_public_currency_holdings?page=1&per_page=25"
  },
  "meta": {
    "pagination": {
    "per-page": null,
    "total-pages": "1",
    "total-count": "2"
    }
  }
}
```

This endpoint retrieves the full details of all of a user's publicly viewable holdings of currencies that the user is not the issuer of.

### HTTP Request

`GET https://api.mycurrency.com/users/<USER-ID>/authorized_externally_issued_public_currency_holdings`

<aside class="notice">
Authentication: the request requires the OAuth access-token associated with the User referenced by the ID 
</aside>

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the public currency holding
owning-user-id | The ID of the user that the public currency holding belongs to
currency-id | The ID of the currency that the public currency holding holds
currency-name | The name of the currency that the public currency holding holds
currency-icon-url | The URL at which the icon picture of the currency that the public currency holding holds can be found
currency-burn-rate | The annual rate at which the currency contained within the public currency holding burns, by basis point (100 = 1%) 
currency-daily-burn-rate | The daily rate at which the currency contained within the public currency holding burns, by fraction of 1 (0.01 = 1%) 
amount-atomic | The amount of currency held in the public currency holding, in atomic units (each whole unit is composed of 10^10 atomic units)
transfer-out | The total amount that has been debited from the public currency holding as a result of outgoing transfers
transfer-in | The total amount that has been credited to the public currency holding as a result of incoming transfers
micro-currency-order-out | The total amount that has been debited from the public currency holding as a result of micro_currency_orders 
issuance-in | The total amount that has been credited to the public currency holding as a result of incoming issuances
burn-amount-out | The total amount that has been debited from the public currency holding as a result of the daily burnrate of the currency 
created-at | The time and date when the public currency holding was created
updated-at | The time and date when the public currency holding was last updated

# Private Currency Holdings

Private currency holding endpoints can only be accessed by the user that owns the holding.

## Get a Private Currency Holding with Authorization

```shell
curl 'https://api.mycurrency.com/users/4/authorized_private_currency_holdings/5' \
  -H 'Accept: application/json' -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer j47lbjj8r9n5yy8mup6cxqc8h70yvhnilm0g84kg0raqckus0k1koj9f75ao'
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "id": "5",
    "type": "private-currency-holdings",
    "attributes": {
      "owning-user-id": 4,
      "currency-id": 3,
      "currency-name": "Moon hotel coins",
      "currency-icon-url": "/icons/original/missing.png",
      "currency-burn-rate": 550,
      "currency-daily-burn-rate": "0.000154976",
      "store-count": 1,
      "amount-atomic": 9795351440488,
      "transfer-out": 10200000000000,
      "transfer-in": 0,
      "micro-currency-order-out": 0,
      "issuance-in": 20000000000000,
      "issuance-fee-in": 0,
      "burn-amount-out": 4648559512,
      "created-at": "2018-11-05T13:27:52.000-08:00",
      "updated-at": "2018-12-20T06:18:37.200-08:00",
      "is-issuer-active": true,
      "issuer-user-id": 4,
      "issuer-user-name": "ScipioAfricanus",
      "issuer-user-avatar-url": "/system/users/avatars/000/000/004/original/1.jpg?1559736060"
    }
  }
}
```

This endpoint retrieves the full details of a particular private currency holding. 

### HTTP Request

`GET https://api.mycurrency.com/users/<USER-ID>/authorized_private_currency_holdings/<ID>`

<aside class="notice">
Authentication: the request requires the OAuth access-token associated with the User referenced by the ID 
</aside>

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the private currency holding
owning-user-id | The ID of the user that the private currency holding belongs to
currency-id | The ID of the currency that the private currency holding holds
currency-name | The name of the currency that the private currency holding holds
currency-icon-url | The URL at which the icon picture of the currency that the private currency holding holds can be found
currency-burn-rate | The annual rate at which the currency contained within the private currency holding burns, by basis point (100 = 1%) 
currency-daily-burn-rate | The daily rate at which the currency contained within the public currency holding burns, by fraction of 1 (0.01 = 1%) 
store-count | The number of stores associated with the currency
amount-atomic | The amount of currency held in the private currency holding, in atomic units (each whole unit is composed of 10^10 atomic units)
transfer-out | The total amount that has been debited from the private currency holding as a result of outgoing transfers
transfer-in | The total amount that has been credited to the private currency holding as a result of incoming transfers
micro-currency-order-out | The total amount that has been debited from the private currency holding as a result of micro_currency_orders 
issuance-in | The total amount that has been credited to the private currency holding as a result of incoming issuances
burn-amount-out | The total amount that has been debited from the private currency holding as a result of the daily burnrate of the currency 
created-at | The time and date when the private currency holding was created
updated-at | The time and date when the private currency holding was last updated
is-issuer-active | Whether the issuer of the currency is active
issuer-user-id | The ID of the user that issues the currency
issuer-user-name | The username of the user that issues the currency
issuer-user-avatar-url | The URL of the avatar of the user that issues the currency

## List User's Private Self-Issued Currency Holdings with Authorization

```shell
curl 'https://api.mycurrency.com/users/4/authorized_self_issued_private_currency_holdings' \
  -H 'Accept: application/json' -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer j47lbjj8r9n5yy8mup6cxqc8h70yvhnilm0g84kg0raqckus0k1koj9f75ao'
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": "2",
      "type": "private-currency-holdings",
      "attributes": {
        "owning-user-id": 4,
        "currency-id": 2,
        "currency-name": "solar electricity zaps",
        "currency-icon-url": "/icons/original/missing.png",
        "currency-burn-rate": 640,
        "currency-daily-burn-rate": "0.000181189",
        "store-count": 2,
        "amount-atomic": 4884625096360,
        "transfer-out": 5110000000000,
        "transfer-in": 0,
        "micro-currency-order-out": 0,
        "issuance-in": 10000000000000,
        "issuance-fee-in": 0,
        "burn-amount-out": 5374903640,
        "created-at": "2018-11-05T13:27:52.000-08:00",
        "updated-at": "2018-12-17T05:15:10.273-08:00"
      }
    },
    {
      "id": "5",
      "type": "private-currency-holdings",
      "attributes": {
        "owning-user-id": 4,
        "currency-id": 3,
        "currency-name": "Moon hotel coins",
        "currency-icon-url": "/icons/original/missing.png",
        "currency-burn-rate": 550,
        "currency-daily-burn-rate": "0.000154976",
        "store-count": 1,
        "amount-atomic": 9795351440488,
        "transfer-out": 10200000000000,
        "transfer-in": 0,
        "micro-currency-order-out": 0,
        "issuance-in": 20000000000000,
        "issuance-fee-in": 0,
        "burn-amount-out": 4648559512,
        "created-at": "2018-11-05T13:27:52.000-08:00",
        "updated-at": "2018-12-20T06:18:37.200-08:00"
      }
    },
    {
      "id": "10",
      "type": "private-currency-holdings",
      "attributes": {
        "owning-user-id": 4,
        "currency-id": 5,
        "currency-name": "Home Repair dollars",
        "currency-icon-url": "/icons/original/missing.png",
        "currency-burn-rate": 450,
        "currency-daily-burn-rate": "0.00012614",
        "store-count": 0,
        "amount-atomic": 4998738679556,
        "transfer-out": 5000000000000,
        "transfer-in": 0,
        "micro-currency-order-out": 0,
        "issuance-in": 10000000000000,
        "issuance-fee-in": 0,
        "burn-amount-out": 1261320444,
        "created-at": "2018-11-06T13:27:52.000-08:00",
        "updated-at": "2018-11-08T13:26:13.501-08:00"
      }
    },
    {
      "id": "11",
      "type": "private-currency-holdings",
      "attributes": {
        "owning-user-id": 4,
        "currency-id": 6,
        "currency-name": "Wholesome foods tokens",
        "currency-icon-url": "/icons/original/missing.png",
        "currency-burn-rate": 710,
        "currency-daily-burn-rate": "0.000201751",
        "store-count": 0,
        "amount-atomic": 9995965387034,
        "transfer-out": 0,
        "transfer-in": 0,
        "micro-currency-order-out": 0,
        "issuance-in": 10000000000000,
        "issuance-fee-in": 0,
        "burn-amount-out": 4034612966,
        "created-at": "2018-11-06T13:27:52.000-08:00",
        "updated-at": "2018-11-08T13:26:13.525-08:00"
      }
    },
    {
      "id": "17",
      "type": "private-currency-holdings",
      "attributes": {
        "owning-user-id": 4,
        "currency-id": 9,
        "currency-name": "Alabama steak coins",
        "currency-icon-url": "/icons/original/missing.png",
        "currency-burn-rate": 550,
        "currency-daily-burn-rate": "0.000154976",
        "store-count": 1,
        "amount-atomic": 130000000000000,
        "transfer-out": 80000000000000,
        "transfer-in": 0,
        "micro-currency-order-out": 0,
        "issuance-in": 210000000000000,
        "issuance-fee-in": 0,
        "burn-amount-out": 0,
        "created-at": "2019-06-12T03:23:26.867-07:00",
        "updated-at": "2019-06-12T03:39:39.335-07:00"
      }
    },
    {
      "id": "18",
      "type": "private-currency-holdings",
      "attributes": {
        "owning-user-id": 4,
        "currency-id": 10,
        "currency-name": "Turbo points",
        "currency-icon-url": "/icons/original/missing.png",
        "currency-burn-rate": 600,
        "currency-daily-burn-rate": "0.000169508",
        "store-count": 1,
        "amount-atomic": 40000000000000,
        "transfer-out": 70000000000000,
        "transfer-in": 0,
        "micro-currency-order-out": 0,
        "issuance-in": 110000000000000,
        "issuance-fee-in": 0,
        "burn-amount-out": 0,
        "created-at": "2019-06-12T03:24:27.664-07:00",
        "updated-at": "2019-06-12T03:41:24.054-07:00"
      }
    }
  ],
  "links": {
    "self": "https://api.mycurrency.com/users/4/authorized_self_issued_private_currency_holdings?",
    "first": "https://api.mycurrency.com/users/4/authorized_self_issued_private_currency_holdings?page=1&per_page=25",
    "prev": null,
    "next": null,
    "last": "https://api.mycurrency.com/users/4/authorized_self_issued_private_currency_holdings?page=1&per_page=25"
  },
  "meta": {
    "pagination": {
      "per-page": null,
      "total-pages": "1",
      "total-count": "6"
    }
  }
}
```

This endpoint retrieves the full details of all of a user's privately viewable holdings of currencies that the user is also the issuer of.

### HTTP Request

`GET https://api.mycurrency.com/users/<USER-ID>/authorized_self_issued_private_currency_holdings`

<aside class="notice">
Authentication: the request requires the OAuth access-token associated with the User referenced by the ID 
</aside>

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the private currency holding
owning-user-id | The ID of the user that the private currency holding belongs to
currency-id | The ID of the currency that the private currency holding holds
currency-name | The name of the currency that the private currency holding holds
currency-icon-url | The URL at which the icon picture of the currency that the private currency holding holds can be found
currency-burn-rate | The annual rate at which the currency contained within the private currency holding burns, by basis point (100 = 1%) 
currency-daily-burn-rate | The daily rate at which the currency contained within the public currency holding burns, by fraction of 1 (0.01 = 1%) 
store-count | The number of stores associated with the currency
amount-atomic | The amount of currency held in the private currency holding, in atomic units (each whole unit is composed of 10^10 atomic units)
transfer-out | The total amount that has been debited from the private currency holding as a result of outgoing transfers
transfer-in | The total amount that has been credited to the private currency holding as a result of incoming transfers
micro-currency-order-out | The total amount that has been debited from the private currency holding as a result of micro_currency_orders 
issuance-in | The total amount that has been credited to the private currency holding as a result of incoming issuances
burn-amount-out | The total amount that has been debited from the private currency holding as a result of the daily burnrate of the currency 
created-at | The time and date when the private currency holding was created
updated-at | The time and date when the private currency holding was last updated

## List User's Private Externally Issued Currency Holdings with Authorization

```shell
curl 'https://api.mycurrency.com/users/3/authorized_externally_issued_private_currency_holdings' \
  -H 'Accept: application/json' -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer j47lbjj8r9n5yy8mup6cxqc8h70yvhnilm0g84kg0raqckus0k1koj9f75ao'
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": "3",
      "type": "private-currency-holdings",
      "attributes": {
        "owning-user-id": 3,
        "currency-id": 2,
        "currency-name": "solar electricity zaps",
        "currency-icon-url": "/icons/original/missing.png",
        "currency-burn-rate": 640,
        "currency-daily-burn-rate": "0.000181189",
        "store-count": 2,
        "amount-atomic": 5009994565314,
        "transfer-out": 0,
        "transfer-in": 5010000000000,
        "micro-currency-order-out": 0,
        "issuance-in": 0,
        "issuance-fee-in": 0,
        "burn-amount-out": 5434686,
        "created-at": "2018-11-05T13:27:52.000-08:00",
        "updated-at": "2018-12-17T05:15:10.244-08:00",
        "is-issuer-active": true,
        "issuer-user-id": 4,
        "issuer-user-name": "ScipioAfricanus",
        "issuer-user-avatar-url": "/system/users/avatars/000/000/004/original/1.jpg?1559736060"
      }
    },
    {
      "id": "6",
      "type": "private-currency-holdings",
      "attributes": {
        "owning-user-id": 3,
        "currency-id": 3,
        "currency-name": "Moon hotel coins",
        "currency-icon-url": "/icons/original/missing.png",
        "currency-burn-rate": 550,
        "currency-daily-burn-rate": "0.000154976",
        "store-count": 1,
        "amount-atomic": 5197675720243,
        "transfer-out": 5000000000000,
        "transfer-in": 10200000000000,
        "micro-currency-order-out": 0,
        "issuance-in": 0,
        "issuance-fee-in": 0,
        "burn-amount-out": 2324279757,
        "created-at": "2018-11-05T13:27:52.000-08:00",
        "updated-at": "2018-12-20T06:18:37.182-08:00",
        "is-issuer-active": true,
        "issuer-user-id": 4,
        "issuer-user-name": "ScipioAfricanus",
        "issuer-user-avatar-url": "/system/users/avatars/000/000/004/original/1.jpg?1559736060"
      }
    },
    {
      "id": "9",
      "type": "private-currency-holdings",
      "attributes": {
        "owning-user-id": 3,
        "currency-id": 4,
        "currency-name": "spiderman pizza dollars",
        "currency-icon-url": "/icons/original/missing.png",
        "currency-burn-rate": 420,
        "currency-daily-burn-rate": "0.000117548",
        "store-count": 0,
        "amount-atomic": 1499118493626,
        "transfer-out": 3500000000000,
        "transfer-in": 5000000000000,
        "micro-currency-order-out": 0,
        "issuance-in": 0,
        "issuance-fee-in": 0,
        "burn-amount-out": 881506374,
        "created-at": "2018-11-05T13:27:52.000-08:00",
        "updated-at": "2019-06-12T03:53:10.051-07:00",
        "is-issuer-active": true,
        "issuer-user-id": 2,
        "issuer-user-name": "spiderman",
        "issuer-user-avatar-url": "/avatars/original/missing.png"
      }
    },
    {
      "id": "12",
      "type": "private-currency-holdings",
      "attributes": {
        "owning-user-id": 3,
        "currency-id": 6,
        "currency-name": "Wholesome foods tokens",
        "currency-icon-url": "/icons/original/missing.png",
        "currency-burn-rate": 710,
        "currency-daily-burn-rate": "0.000201751",
        "store-count": 0,
        "amount-atomic": 9995965387034,
        "transfer-out": 0,
        "transfer-in": 0,
        "micro-currency-order-out": 0,
        "issuance-in": 10000000000000,
        "issuance-fee-in": 0,
        "burn-amount-out": 4034612966,
        "created-at": "2018-11-06T13:27:52.000-08:00",
        "updated-at": "2018-11-08T13:26:13.538-08:00",
        "is-issuer-active": true,
        "issuer-user-id": 4,
        "issuer-user-name": "ScipioAfricanus",
        "issuer-user-avatar-url": "/system/users/avatars/000/000/004/original/1.jpg?1559736060"
      }
    },
    {
      "id": "13",
      "type": "private-currency-holdings",
      "attributes": {
        "owning-user-id": 3,
        "currency-id": 5,
        "currency-name": "Home Repair dollars",
        "currency-icon-url": "/icons/original/missing.png",
        "currency-burn-rate": 450,
        "currency-daily-burn-rate": "0.00012614",
        "store-count": 0,
        "amount-atomic": 4998738679556,
        "transfer-out": 0,
        "transfer-in": 5000000000000,
        "micro-currency-order-out": 0,
        "issuance-in": 0,
        "issuance-fee-in": 0,
        "burn-amount-out": 1261320444,
        "created-at": "2018-11-06T13:27:52.000-08:00",
        "updated-at": "2018-11-08T13:26:13.555-08:00",
        "is-issuer-active": true,
        "issuer-user-id": 4,
        "issuer-user-name": "ScipioAfricanus",
        "issuer-user-avatar-url": "/system/users/avatars/000/000/004/original/1.jpg?1559736060"
      }
    },
    {
      "id": "23",
      "type": "private-currency-holdings",
      "attributes": {
        "owning-user-id": 3,
        "currency-id": 10,
        "currency-name": "Turbo points",
        "currency-icon-url": "/icons/original/missing.png",
        "currency-burn-rate": 600,
        "currency-daily-burn-rate": "0.000169508",
        "store-count": 1,
        "amount-atomic": 2000000000000,
        "transfer-out": 0,
        "transfer-in": 2000000000000,
        "micro-currency-order-out": 0,
        "issuance-in": 0,
        "issuance-fee-in": 0,
        "burn-amount-out": 0,
        "created-at": "2019-06-17T10:06:45.113-07:00",
        "updated-at": "2019-06-17T10:06:45.144-07:00",
        "is-issuer-active": true,
        "issuer-user-id": 4,
        "issuer-user-name": "ScipioAfricanus",
        "issuer-user-avatar-url": "/system/users/avatars/000/000/004/original/1.jpg?1559736060"
      }
    }
  ],
  "links": {
    "self": "https://api.mycurrency.com/users/3/authorized_externally_issued_private_currency_holdings?",
    "first": "https://api.mycurrency.com/users/3/authorized_externally_issued_private_currency_holdings?page=1&per_page=25",
    "prev": null,
    "next": null,
    "last": "https://api.mycurrency.com/users/3/authorized_externally_issued_private_currency_holdings?page=1&per_page=25"
  },
  "meta": {
    "pagination": {
      "per-page": null,
      "total-pages": "1",
      "total-count": "6"
    }
  }
}
```

This endpoint retrieves the full details of all of a user's privately viewable holdings of currencies that the user is not the issuer of.

### HTTP Request

`GET https://api.mycurrency.com/users/<USER-ID>/authorized_externally_issued_private_currency_holdings`

<aside class="notice">
Authentication: the request requires the OAuth access-token associated with the User referenced by the ID 
</aside>

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the private currency holding
owning-user-id | The ID of the user that the private currency holding belongs to
currency-id | The ID of the currency that the private currency holding holds
currency-name | The name of the currency that the private currency holding holds
currency-icon-url | The URL at which the icon picture of the currency that the private currency holding holds can be found
currency-burn-rate | The annual rate at which the currency contained within the private currency holding burns, by basis point (100 = 1%) 
currency-daily-burn-rate | The daily rate at which the currency contained within the public currency holding burns, by fraction of 1 (0.01 = 1%) 
store-count | The number of stores associated with the currency
amount-atomic | The amount of currency held in the private currency holding, in atomic units (each whole unit is composed of 10^10 atomic units)
transfer-out | The total amount that has been debited from the private currency holding as a result of outgoing transfers
transfer-in | The total amount that has been credited to the private currency holding as a result of incoming transfers
micro-currency-order-out | The total amount that has been debited from the private currency holding as a result of micro_currency_orders 
issuance-in | The total amount that has been credited to the private currency holding as a result of incoming issuances
burn-amount-out | The total amount that has been debited from the private currency holding as a result of the daily burnrate of the currency 
created-at | The time and date when the private currency holding was created
updated-at | The time and date when the private currency holding was last updated
is-issuer-active | Whether the issuer of the currency is active
issuer-user-id | The ID of the user that issues the currency
issuer-user-name | The username of the user that issues the currency
issuer-user-avatar-url | The URL of the avatar of the user that issues the currency

# Transactions

Transactions are all user actions that change the balance of currency holdings: issuances, transfers, and micro currency orders. When listing the transactions associated with a particular public or private currency holding, the burnrate periods of that currency holding are also shown, to enable calculation of the amount of currency burned over time.

## List Public Currency Holding's Transactions

This endpoint retrieves all issuances, transfers, micro currency orders and burnrate periods associated with a public currency holding, sorted by created_at date, the most recent to the oldest

```shell
curl 'https://api.mycurrency.com/users/3/authorized_public_currency_holdings/4/pu_h_transactions' \
  -H 'Accept: application/json' -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer j47lbjj8r9n5yy8mup6cxqc8h70yvhnilm0g84kg0raqckus0k1koj9f75ao'
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": "107",
      "type": "transfers",
      "attributes": {
        "amount-atomic": 1000000000000,
        "transfer-type": "transfer-from-private",
        "receiver-day-counter": 0,
        "sending-user-id": 3,
        "sender-username": "Hannibal",
        "sending-user-avatar-url": "/system/users/avatars/000/000/003/original/avatar.jpg?1562578009",
        "receiver-before-amount-atomic": 4997675720243,
        "receiver-after-amount-atomic": 5997675720243,
        "transfer-sender-currency-holding-type": "PrivateCurrencyHolding",
        "created-at": "2019-07-08T02:22:55.070-07:00",
        "updated-at": "2019-07-08T02:22:55.070-07:00"
      }
    },
    {
      "id": "51",
      "type": "burnrate-periods",
      "attributes": {
        "day-counter": 0,
        "final-day-counter": null,
        "burn-rate": 550,
        "daily-burn-rate": "0.000154976",
        "start-amount-atomic": 4997675720243,
        "last-amount-atomic": 5997675720243,
        "created-at": "2019-06-20T00:15:20.343-07:00",
        "updated-at": "2019-07-08T02:22:55.073-07:00"
      }
    },
    {
      "id": "47",
      "type": "burnrate-periods",
      "attributes": {
        "day-counter": 0,
        "final-day-counter": 0,
        "burn-rate": 2000,
        "daily-burn-rate": "0.000611166",
        "start-amount-atomic": 4997675720243,
        "last-amount-atomic": 4997675720243,
        "created-at": "2019-06-20T00:08:34.886-07:00",
        "updated-at": "2019-06-20T00:15:20.340-07:00"
      }
    },
    {
      "id": "5",
      "type": "transfers",
      "attributes": {
        "amount-atomic": 5000000000000,
        "transfer-type": "transfer-from-private",
        "receiver-day-counter": 0,
        "sending-user-id": 3,
        "sender-username": "Hannibal",
        "sending-user-avatar-url": "/system/users/avatars/000/000/003/original/avatar.jpg?1562578009",
        "receiver-before-amount-atomic": 0,
        "receiver-after-amount-atomic": 5000000000000,
        "transfer-sender-currency-holding-type": "PrivateCurrencyHolding",
        "created-at": "2018-11-05T11:07:15.062-08:00",
        "updated-at": "2018-11-05T11:07:15.062-08:00"
      }
    },
    {
      "id": "10",
      "type": "burnrate-periods",
      "attributes": {
        "day-counter": 3,
        "final-day-counter": 3,
        "burn-rate": 550,
        "daily-burn-rate": "0.000154976",
        "start-amount-atomic": 0,
        "last-amount-atomic": 4997675720243,
        "created-at": "2018-11-05T11:07:15.043-08:00",
        "updated-at": "2019-06-20T00:08:34.882-07:00"
      }
    }
  ],
  "links": {
    "self": "https://api.mycurrency.com/users/3/authorized_public_currency_holdings/4/pu_h_transactions?",
    "first": "https://api.mycurrency.com/users/3/authorized_public_currency_holdings/4/pu_h_transactions?page=1&per_page=25",
    "prev": null,
    "next": null,
    "last": "https://api.mycurrency.com/users/3/authorized_public_currency_holdings/4/pu_h_transactions?page=1&per_page=25"
  },
  "meta": {
    "pagination": {
      "per-page": null,
      "total-pages": "1",
      "total-count": "5"
    }
  }
}
```

### HTTP Request

`GET https://api.mycurrency.com/users/<USER-ID>/authorized_public_currency_holdings/<PUBLIC-CURRENCY-HOLDING-ID>/pu_h_transactions`

<aside class="notice">
Authentication: the request requires the OAuth access-token associated with the User referenced by the ID 
</aside>

### RESPONSE

### Transfers:

Parameter | Description
--------- | -----------
id | The ID of the transfer
amount-atomic | The amount of currency transferred, in atomic units (each whole unit is composed of 10^10 atomic units)
transfer-type | Whether the transfer is a transfer-to-public, transfer-from-public, transfer-to-private, transfer-from-private, transfer-out or transfer-in
sender-day-counter | The day counter of the sending currency holding when it was debited by the transfer, only shown if the owner of the public currency holding is the sending user
receiver-day-counter | The day counter of the receiving currency holding when it was credited by the transfer, only shown if the owner of the public or private currency holding is the receiving user
sending-user-id | The ID of the transfer sender, only shown if the owner of the public currency holding is the transfer receiver 
sender-username | The username of the transfer sender, only shown if the owner of the public currency holding is the transfer receiver
sending-user-avatar-url | The URL of the avatar of the transfer sender, only shown if the owner of the public currency holding is the transfer receiver
receiving-user-id | The ID of the transfer receiver, only shown if owner of the public currency holding is the transfer sender
receiving-username | The username of the transfer receiver, only shown if the owner of the public currency holding is the transfer sender 
receiving-user-avatar-url | The URL of the avatar of the transfer receiver, only shown if the owner of the public currency holding is the transfer sender 
sender-before-amount-atomic | The balance, in atomic units, of the sending currency holding before it was debited by the transfer, only shown if the owner of the public currency holding is the transfer sender
sender-after-amount-atomic | The balance, in atomic units, of the sending currency holding after it was debited by the transfer, only shown if the owner of the public currency holding is the transfer sender
receiver-before-amount-atomic | The balance, in atomic units, of the receiving currency holding before it was credited by the transfer, only shown if the owner of the public currency holding is the transfer receiver
receiver-after-amount-atomic | The balance, in atomic units, of the receiving currency holding after it was credited by the transfer, only shown if the owner of the public currency holding is the transfer receiver
created-at | The time and date when the transfer was created
updated-at | The time and date when the transfer was last updated

### Issuances: 

Parameter | Description
--------- | -----------
id | The ID of the issuance
amount-atomic | The amount of currency issued, in atomic units (each whole unit is composed of 10^10 atomic units)
issueing-user-id | The ID of the issueing user
issuer-username | The username of the issueing user
issuer-user-avatar-url | The URL of the avatar of the issueing user
before-amount-atomic | The balance, in atomic units, of the public currency holding before it was credited by the issuance
after-amount-atomic | The balance, in atomic units, of the public currency holding after it was credited by the issuance
day-counter | The day counter of the public currency holding when it was credited by the issuance
created-at | The time and date when the transfer was created
updated-at | The time and date when the transfer was last updated

### Micro Currency Orders: 

Parameter | Description
--------- | -----------
id | The ID of the micro currency order
amount-atomic | The amount of currency spent, in atomic units (each whole unit is composed of 10^10 atomic units)
store-id | The ID of the store that the micro currency order was spent at
store-name | The name of the store that the micro currency order was spent at
before-amount-atomic | The balance, in atomic units, of the public currency holding before it was debited by the micro currency order
after-amount-atomic | The balance, in atomic units, of the public currency holding after it was debited by the micro currency order
day-counter | The day counter of the public currency holding when it was debited by the micro currency order
created-at | The time and date when the micro currency order was created
updated-at | The time and date when the micro currency order was last updated

### Burnrate Periods:

Parameter | Description
--------- | -----------
id | The ID of the burnrate period
day-counter | The number of daily burns that have been applied to the public currency holding since the burnrate period was started
final-day-counter | The number of daily burns that were applied to the public currency holding over the lifetime of a burnrate period. Only set once a burnrate period is succeeded by a new burnrate period.
burn-rate | The burn rate of public currency holding within the burnrate period
start-amount-atomic | The balance, in atomic units, of the public currency holding when the burnrate period began
last-amount-atomic | The last balance, in atomic units, of the public currency holding during the burnrate period. The value stops being updated when the burnrate period is succeeded by a new burnrate period.
created-at | The time and date when the burnrate period was created
updated-at | The time and date when the burnrate period was last updated

## List Private Currency Holding's Transactions

This endpoint retrieves all issuances, transfers, micro currency orders and burnrate periods associated with a private currency holding, sorted by created_at date, the most recent to the oldest

```shell
curl 'https://api.mycurrency.com/users/3/authorized_private_currency_holdings/9/pr_h_transactions' \
  -H 'Accept: application/json' -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer j47lbjj8r9n5yy8mup6cxqc8h70yvhnilm0g84kg0raqckus0k1koj9f75ao'
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": "171",
      "type": "transfers",
      "attributes": {
        "amount-atomic": 800000000000,
        "transfer-type": "transfer-in",
        "receiver-day-counter": 3,
        "sending-user-id": 2,
        "sender-username": "spiderman",
        "sending-user-avatar-url": "/avatars/original/missing.png",
        "receiver-before-amount-atomic": 1499118493626,
        "receiver-after-amount-atomic": 2299118493626,
        "transfer-sender-currency-holding-type": "PublicCurrencyHolding",
        "created-at": "2019-07-21T20:43:04.398-07:00",
        "updated-at": "2019-07-21T20:43:04.398-07:00"
      }
    },
    {
      "id": "20",
      "type": "transfers",
      "attributes": {
        "amount-atomic": 1000000000000,
        "transfer-type": "transfer-out",
        "sender-day-counter": 3,
        "receiving-user-id": 4,
        "receiver-username": "ScipioAfricanus",
        "receiving-user-avatar-url": "/system/users/avatars/000/000/004/original/1.jpg?1559736060",
        "sender-before-amount-atomic": 2499118493626,
        "sender-after-amount-atomic": 1499118493626,
        "transfer-receiver-currency-holding-type": "PrivateCurrencyHolding",
        "created-at": "2019-06-12T03:53:10.039-07:00",
        "updated-at": "2019-06-12T03:53:10.039-07:00"
      }
    },
    {
      "id": "7",
      "type": "transfers",
      "attributes": {
        "amount-atomic": 2500000000000,
        "transfer-type": "transfer-to-public",
        "sender-day-counter": 0,
        "receiving-user-id": 3,
        "receiver-username": "Hannibal",
        "receiving-user-avatar-url": "/system/users/avatars/000/000/003/original/avatar.jpg?1562578009",
        "sender-before-amount-atomic": 5000000000000,
        "sender-after-amount-atomic": 2500000000000,
        "transfer-receiver-currency-holding-type": "PublicCurrencyHolding",
        "created-at": "2018-11-05T11:15:33.226-08:00",
        "updated-at": "2018-11-05T11:15:33.226-08:00"
      }
    },
    {
      "id": "6",
      "type": "transfers",
      "attributes": {
        "amount-atomic": 5000000000000,
        "transfer-type": "transfer-in",
        "receiver-day-counter": 0,
        "sending-user-id": 2,
        "sender-username": "spiderman",
        "sending-user-avatar-url": "/avatars/original/missing.png",
        "receiver-before-amount-atomic": 0,
        "receiver-after-amount-atomic": 5000000000000,
        "transfer-sender-currency-holding-type": "PrivateCurrencyHolding",
        "created-at": "2018-11-05T11:12:30.723-08:00",
        "updated-at": "2018-11-05T11:12:30.723-08:00"
      }
    },
    {
      "id": "15",
      "type": "burnrate-periods",
      "attributes": {
        "day-counter": 3,
        "final-day-counter": null,
        "burn-rate": 420,
        "daily-burn-rate": "0.000117548",
        "start-amount-atomic": 0,
        "last-amount-atomic": 2299118493626,
        "created-at": "2018-11-05T11:12:30.704-08:00",
        "updated-at": "2019-07-21T20:43:04.413-07:00"
      }
    }
  ],
  "links": {
    "self": "https://api.mycurrency.com/users/3/authorized_private_currency_holdings/9/pr_h_transactions?",
    "first": "https://api.mycurrency.com/users/3/authorized_private_currency_holdings/9/pr_h_transactions?page=1&per_page=25",
    "prev": null,
    "next": null,
    "last": "https://api.mycurrency.com/users/3/authorized_private_currency_holdings/9/pr_h_transactions?page=1&per_page=25"
  },
  "meta": {
    "pagination": {
      "per-page": null,
      "total-pages": "1",
      "total-count": "5"
    }
  }
}
```

### HTTP Request

`GET https://api.mycurrency.com/users/<USER-ID>/authorized_private_currency_holdings/<PRIVATE-CURRENCY-HOLDING-ID>/pr_h_transactions`

<aside class="notice">
Authentication: the request requires the OAuth access-token associated with the User referenced by the ID 
</aside>

### RESPONSE

### Transfers:

Parameter | Description
--------- | -----------
id | The ID of the transfer
amount-atomic | The amount of currency transferred, in atomic units (each whole unit is composed of 10^10 atomic units)
transfer-type | Whether the transfer is a transfer-to-public, transfer-from-public, transfer-to-private, transfer-from-private, transfer-out or transfer-in
sender-day-counter | The day counter of the sending currency holding when it was debited by the transfer, only shown if the owner of the private currency holding is the sending user
receiver-day-counter | The day counter of the receiving currency holding when it was credited by the transfer, only shown if the owner of the public or private currency holding is the receiving user
sending-user-id | The ID of the transfer sender, only shown if the owner of the private currency holding is the transfer receiver 
sender-username | The username of the transfer sender, only shown if the owner of the private currency holding is the transfer receiver
sending-user-avatar-url | The URL of the avatar of the transfer sender, only shown if the owner of the private currency holding is the transfer receiver
receiving-user-id | The ID of the transfer receiver, only shown if owner of the private currency holding is the transfer sender
receiving-username | The username of the transfer sender, only shown if the owner of the private currency holding is the transfer sender 
receiving-user-avatar-url | The URL of the avatar of the transfer receiver, only shown if the owner of the private currency holding is the transfer sender 
sender-before-amount-atomic | The balance, in atomic units, of the sending currency holding before it was debited by the transfer, only shown if the logged-in user that owns the private currency holding is the transfer sender
sender-after-amount-atomic | The balance, in atomic units, of the sending currency holding after it was debited by the transfer, only shown if the logged-in user that owns the private currency holding is the transfer sender
receiver-before-amount-atomic | The balance, in atomic units, of the receiving currency holding before it was credited by the transfer, only shown if the logged-in user that owns the private currency holding is the transfer receiver
receiver-after-amount-atomic | The balance, in atomic units, of the receiving currency holding after it was credited by the transfer, only shown if the logged-in user that owns the private currency holding is the transfer receiver
created-at | The time and date when the transfer was created
updated-at | The time and date when the transfer was last updated

### Issuances: 

Parameter | Description
--------- | -----------
id | The ID of the issuance
amount-atomic | The amount of currency issued, in atomic units (each whole unit is composed of 10^10 atomic units)
issueing-user-id | The ID of the issueing user
issuer-username | The username of the issueing user
issuer-user-avatar-url | The URL of the avatar of the issueing user
before-amount-atomic | The balance, in atomic units, of the private currency holding before it was credited by the issuance
after-amount-atomic | The balance, in atomic units, of the private currency holding after it was credited by the issuance
day-counter | The day counter of the private currency holding when it was credited by the issuance
created-at | The time and date when the transfer was created
updated-at | The time and date when the transfer was last updated

### Micro Currency Orders: 

Parameter | Description
--------- | -----------
id | The ID of the micro currency order
amount-atomic | The amount of currency spent, in atomic units (each whole unit is composed of 10^10 atomic units)
store-id | The ID of the store that the micro currency order was spent at
store-name | The name of the store that the micro currency order was spent at
before-amount-atomic | The balance, in atomic units, of the private currency holding before it was debited by the micro currency order
after-amount-atomic | The balance, in atomic units, of the private currency holding after it was debited by the micro currency order
day-counter | The day counter of the private currency holding when it was debited by the micro currency order
created-at | The time and date when the micro currency order was created
updated-at | The time and date when the micro currency order was last updated

### Burnrate Periods:

Parameter | Description
--------- | -----------
id | The ID of the burnrate period
day-counter | The number of daily burns that have been applied to the private currency holding since the burnrate period was started
final-day-counter | The number of daily burns that were applied to the private currency holding over the lifetime of a burnrate period. Only set once a burnrate period is succeeded by a new burnrate period.
burn-rate | The burn rate of private currency holding within the burnrate period
start-amount-atomic | The balance, in atomic units, of the private currency holding when the burnrate period began
last-amount-atomic | The last balance, in atomic units, of the private currency holding during the burnrate period. The value stops being updated when the burnrate period is succeeded by a new burnrate period.
created-at | The time and date when the burnrate period was created
updated-at | The time and date when the burnrate period was last updated

## List User's Recent Transactions

This endpoint retrieves the 100 most recently created issuances, transfers, and outgoing micro currency orders associated with a user, sorted by created_at date, starting from the most recent

```shell
curl 'https://api.mycurrency.com/users/3/recent_transactions?per_page=10' \
  -H 'Accept: application/json' -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer j47lbjj8r9n5yy8mup6cxqc8h70yvhnilm0g84kg0raqckus0k1koj9f75ao'
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": "206",
      "type": "issuances",
      "attributes": {
        "day-counter": 0,
        "amount-atomic": 100000000000000,
        "proposed-issuance-id": 86,
        "is-genesis-issuance": false,
        "issuance-receiver-currency-holding-id": 185,
        "issuance-receiver-currency-holding-type": "PrivateCurrencyHolding",
        "issued-currency-id": 7,
        "issued-currency-name": "Kian Token",
        "issued-currency-icon-url": "/system/currencies/icons/000/000/007/original/currency.jpg?1566784334",
        "issueing-user-id": 7,
        "issuer-username": "Kian",
        "issueing-user-avatar-url": "/system/users/avatars/original/missing.png",
        "before-amount-atomic": 50000000000000,
        "after-amount-atomic": 150000000000000,
        "created-at": "2019-08-25T19:25:14.644-07:00",
        "updated-at": "2019-08-25T19:25:14.644-07:00"
      }
    },
    {
      "id": "228",
      "type": "transfers",
      "attributes": {
        "amount-atomic": 100000000000000,
        "receiving-user-id": 7,
        "receiver-username": "Kian",
        "receiving-user-avatar-url": "/system/users/avatars/original/missing.png",
        "transfer-type": "transfer-public-out",
        "sender-day-counter": 0,
        "transfer-sender-currency-holding-type": "PublicCurrencyHolding",
        "transfer-sender-currency-holding-id": 2,
        "sender-before-amount-atomic": 103419957849922,
        "sender-after-amount-atomic": 3419957849922,
        "transferred-currency-id": 1,
        "transferred-currency-name": "Micro Asteroid bucks",
        "transferred-currency-icon-url": "/system/currencies/icons/missing.png",
        "created-at": "2019-08-25T19:25:14.610-07:00",
        "updated-at": "2019-08-25T19:25:14.610-07:00"
      }
    },
    {
      "id": "227",
      "type": "transfers",
      "attributes": {
        "amount-atomic": 100000000000000,
        "receiving-user-id": 3,
        "receiver-username": "Hannibal",
        "receiving-user-avatar-url": "/system/users/avatars/000/000/003/original/avatar.jpg?1562578009",
        "transfer-type": "transfer-from-private-to-public",
        "sender-day-counter": 0,
        "receiver-day-counter": 0,
        "transfer-sender-currency-holding-type": "PrivateCurrencyHolding",
        "transfer-receiver-currency-holding-type": "PublicCurrencyHolding",
        "transfer-sender-currency-holding-id": 1,
        "transfer-receiver-currency-holding-id": 2,
        "sending-user-id": 3,
        "sender-username": "Hannibal",
        "sending-user-avatar-url": "/system/users/avatars/000/000/003/original/avatar.jpg?1562578009",
        "sender-before-amount-atomic": 106645827142424,
        "sender-after-amount-atomic": 6645827142424,
        "receiver-before-amount-atomic": 3419957849922,
        "receiver-after-amount-atomic": 103419957849922,
        "transferred-currency-id": 1,
        "transferred-currency-name": "Micro Asteroid bucks",
        "transferred-currency-icon-url": "/system/currencies/icons/missing.png",
        "created-at": "2019-08-25T19:21:52.846-07:00",
        "updated-at": "2019-08-25T19:21:52.846-07:00"
      }
    },
    {
      "id": "205",
      "type": "issuances",
      "attributes": {
        "day-counter": 0,
        "amount-atomic": 100000000000000,
        "receiving-user-id": 3,
        "receiver-username": "Hannibal",
        "receiving-user-avatar-url": "/system/users/avatars/000/000/003/original/avatar.jpg?1562578009",
        "proposed-issuance-id": null,
        "is-genesis-issuance": false,
        "issuance-receiver-currency-holding-id": 1,
        "issuance-receiver-currency-holding-type": "PrivateCurrencyHolding",
        "issued-currency-id": 1,
        "issued-currency-name": "Micro Asteroid bucks",
        "issued-currency-icon-url": "/system/currencies/icons/missing.png",
        "issueing-user-id": 3,
        "issuer-username": "Hannibal",
        "issueing-user-avatar-url": "/system/users/avatars/000/000/003/original/avatar.jpg?1562578009",
        "before-amount-atomic": 6645827142424,
        "after-amount-atomic": 106645827142424,
        "created-at": "2019-08-25T19:21:29.563-07:00",
        "updated-at": "2019-08-25T19:21:29.563-07:00"
      }
    },
    {
      "id": "226",
      "type": "transfers",
      "attributes": {
        "amount-atomic": 40000000000000,
        "transfer-type": "transfer-private-in",
        "receiver-day-counter": 0,
        "transfer-receiver-currency-holding-type": "PrivateCurrencyHolding",
        "transfer-receiver-currency-holding-id": 185,
        "sending-user-id": 7,
        "sender-username": "Kian",
        "sending-user-avatar-url": "/system/users/avatars/original/missing.png",
        "receiver-before-amount-atomic": 10000000000000,
        "receiver-after-amount-atomic": 50000000000000,
        "transferred-currency-id": 7,
        "transferred-currency-name": "Kian Token",
        "transferred-currency-icon-url": "/system/currencies/icons/000/000/007/original/currency.jpg?1566784334",
        "created-at": "2019-08-25T19:19:16.319-07:00",
        "updated-at": "2019-08-25T19:19:16.319-07:00"
      }
    },
    {
      "id": "203",
      "type": "issuances",
      "attributes": {
        "day-counter": 0,
        "amount-atomic": 10000000000000,
        "proposed-issuance-id": 85,
        "is-genesis-issuance": false,
        "issuance-receiver-currency-holding-id": 185,
        "issuance-receiver-currency-holding-type": "PrivateCurrencyHolding",
        "issued-currency-id": 7,
        "issued-currency-name": "Kian Token",
        "issued-currency-icon-url": "/system/currencies/icons/000/000/007/original/currency.jpg?1566784334",
        "issueing-user-id": 7,
        "issuer-username": "Kian",
        "issueing-user-avatar-url": "/system/users/avatars/original/missing.png",
        "before-amount-atomic": 0,
        "after-amount-atomic": 10000000000000,
        "created-at": "2019-08-25T19:12:55.565-07:00",
        "updated-at": "2019-08-25T19:12:55.565-07:00"
      }
    },
    {
      "id": "202",
      "type": "issuances",
      "attributes": {
        "amount-atomic": 100000000000000,
        "receiving-user-id": 7,
        "receiver-username": "Kian",
        "receiving-user-avatar-url": "/system/users/avatars/original/missing.png",
        "proposed-issuance-id": 84,
        "is-genesis-issuance": false,
        "issued-currency-id": 1,
        "issued-currency-name": "Micro Asteroid bucks",
        "issued-currency-icon-url": "/system/currencies/icons/missing.png",
        "created-at": "2019-08-25T19:12:55.463-07:00",
        "updated-at": "2019-08-25T19:12:55.463-07:00"
      }
    },
    {
      "id": "223",
      "type": "transfers",
      "attributes": {
        "amount-atomic": 1000000000000,
        "transfer-type": "transfer-private-in",
        "receiver-day-counter": 3,
        "transfer-receiver-currency-holding-type": "PrivateCurrencyHolding",
        "transfer-receiver-currency-holding-id": 9,
        "sending-user-id": 2,
        "sender-username": "spiderman",
        "sending-user-avatar-url": "/system/users/avatars/original/missing.png",
        "receiver-before-amount-atomic": 2169118493626,
        "receiver-after-amount-atomic": 3169118493626,
        "transferred-currency-id": 4,
        "transferred-currency-name": "spiderman pizza dollars",
        "transferred-currency-icon-url": "/system/currencies/icons/missing.png",
        "created-at": "2019-08-25T05:27:53.020-07:00",
        "updated-at": "2019-08-25T05:27:53.020-07:00"
      }
    },
    {
      "id": "222",
      "type": "transfers",
      "attributes": {
        "amount-atomic": 180000000000,
        "receiving-user-id": 2,
        "receiver-username": "spiderman",
        "receiving-user-avatar-url": "/system/users/avatars/original/missing.png",
        "transfer-type": "transfer-public-out",
        "sender-day-counter": 0,
        "transfer-sender-currency-holding-type": "PublicCurrencyHolding",
        "transfer-sender-currency-holding-id": 2,
        "sender-before-amount-atomic": 3599957849922,
        "sender-after-amount-atomic": 3419957849922,
        "transferred-currency-id": 1,
        "transferred-currency-name": "Micro Asteroid bucks",
        "transferred-currency-icon-url": "/system/currencies/icons/missing.png",
        "created-at": "2019-08-25T05:27:52.968-07:00",
        "updated-at": "2019-08-25T05:27:52.968-07:00"
      }
    }
  ],
  "links": {
    "self": "https://api.mycurrency.com/users/3/recent_transactions?per_page=10",
    "first": "https://api.mycurrency.com/users/3/recent_transactions?page=1&per_page=10",
    "prev": null,
    "next": "https://api.mycurrency.com/users/3/recent_transactions?page=2&per_page=10",
    "last": "https://api.mycurrency.com/users/3/recent_transactions?page=10&per_page=10"
  },
  "meta": {
    "pagination": {
      "per-page": "10",
      "total-pages": "10",
      "total-count": "100"
    }
  }
}
```

### HTTP Request

`GET https://api.mycurrency.com/users/<USER-ID>/recent_transactions`

<aside class="notice">
Authentication: the request requires the OAuth access-token associated with the User referenced by the ID 
</aside>

### RESPONSE

### Transfers:

Parameter | Description
--------- | -----------
id | The ID of the transfer
amount-atomic | The amount of currency transferred, in atomic units (each whole unit is composed of 10^10 atomic units)
receiving-user-id | The ID of the transfer receiver, only shown if the owner of the currency holding that the transfer debited from is the logged-in user
receiver-username | The username of the transfer receiver, only shown if the owner of the currency holding that the transfer debited from is the logged-in user 
receiving-user-avatar-url | The URL of the avatar of the transfer receiver, only shown if the owner of the currency holding that the transfer debited from is the logged-in user
transfer-type | Whether the transfer is a transfer-from-private-to-public, transfer-from-public-to-private, transfer-private-out, transfer-public-out, transfer-private-in, or transfer-public-in 
sender-day-counter | The day counter of the sending currency holding when it was debited by the transfer, only shown if the owner of the currency holding that the transfer debited from is the logged-in user
receiver-day-counter | The day counter of the receiving currency holding when it was credited by the transfer, only shown if the owner of the currency holding that the transfer credited to is the logged-in user
transfer-sender-currency-holding-type | Whether the currency holding that the transfer debited from is a "PublicCurrencyHolding" or a "PrivateCurrencyHolding", only shown if the owner of the currency holding that the transfer debited from is the logged-in user
transfer-sender-currency-holding-id | The ID of the public or private currency holding that the transfer debited from, only shown if the owner of the currency holding that the transfer debited from is the logged-in user
transfer-receiver-currency-holding-type | Whether the currency holding that the transfer credited to is a "PublicCurrencyHolding" or a "PrivateCurrencyHolding", only shown if the owner of the currency holding that the transfer credited to is the logged-in user
transfer-receiver-currency-holding-id | The ID of the public or private currency holding that the transfer credited to, only shown if the owner of the currency holding that the transfer credited to is the logged-in user
sending-user-id | The ID of the transfer sender, only shown if the owner of the currency holding that the transfer credited to is the logged-in user 
sender-username | The username of the transfer sender, only shown if the owner of the currency holding that the transfer credited to is the logged-in user
sending-user-avatar-url | The URL of the avatar of the transfer sender, only shown if the owner of the currency holding that the transfer credited to is the logged-in user
sender-before-amount-atomic | The balance, in atomic units, of the sending currency holding before it was debited from by the transfer, only shown if the owner of the currency holding that the transfer debited from is the logged-in user
sender-after-amount-atomic | The balance, in atomic units, of the sending currency holding after it was debited from by the transfer, only shown if the owner of the currency holding that the transfer debited from is the logged-in user
receiver-before-amount-atomic | The balance, in atomic units, of the receiving currency holding before it was credited to by the transfer, only shown if the owner of the currency holding that the transfer credited to is the logged-in user
receiver-after-amount-atomic | The balance, in atomic units, of the receiving currency holding after it was credited to by the transfer, only shown if the owner of the currency holding that the transfer credited to is the logged-in user
transferred-currency-id | The ID of the transferred currency
transferred-currency-name | The name of the transferred currency
transferred-currency-icon-url | The URL of the icon of the transferred currency
created-at | The time and date when the transfer was created
updated-at | The time and date when the transfer was last updated

### Issuances: 

Parameter | Description
--------- | -----------
id | The ID of the issuance
day-counter | The day counter of the currency holding when it was credited by the issuance
amount-atomic | The amount of currency issued, in atomic units (each whole unit is composed of 10^10 atomic units)
receiving-user-id | The ID of the issuance receiver, only shown if the issuer is the logged-in user
receiver-username | The username of the issuance sender, only shown if the issuer is the logged-in user 
receiving-user-avatar-url | The URL of the avatar of the issuance receiver, only shown if the issuer is the logged-in user
proposed-issuance-id | The ID of the proposed issuance that initiated the creation of the issuance, null if the issuance has no associated proposed_issuance
is-genesis-issuance | Whether the issuance was created as part of the creation of a new currency. When a new currency is created, 1000 units of the currency are issued to the currency issuer without the 5 percent issuance_fee being paid to the site administration
issuance-receiver-currency-holding-id | The ID of the public or private currency holding that the issuance credited to, only shown if the issuance receiver is the logged-in user
issuance-receiver-currency-holding-type | Whether the currency holding that the issuance credited to is a "PublicCurrencyHolding" or a "PrivateCurrencyHolding", only shown if the issuance receiver is the logged-in user
issued-currency-id | The ID of the issued currency
issued-currency-name | The name of the issued currency
issued-currency-icon-url | The URL of the icon of the issued currency
issueing-user-id | The ID of the issueing user, only shown if the issuance receiver is the logged-in user 
issuer-username | The username of the issueing user, only shown if the issuance receiver is the logged-in user
issueing-user-avatar-url | The URL of the avatar of the issueing user, only shown if the issuance receiver is the logged-in user
before-amount-atomic | The balance, in atomic units, of the currency holding before it was credited by the issuance, only shown if the issuance receiver is the logged-in user
after-amount-atomic | The balance, in atomic units, of the currency holding after it was credited by the issuance, only shown if the issuance receiver is the logged-in user
created-at | The time and date when the transfer was created
updated-at | The time and date when the transfer was last updated

### Micro Currency Orders: 

Parameter | Description
--------- | -----------
id | The ID of the micro currency order
day-counter | The day counter of the currency holding when it was debited by the micro currency order
amount-atomic | The amount of currency spent, in atomic units (each whole unit is composed of 10^10 atomic units)
store-id | The ID of the store that the micro currency order was spent at
store-name | The name of the store that the micro currency order was spent at
source-currency-holding-id | The ID of the public or private currency holding that the micro currency order spent from
source-currency-holding-type | Whether the currency holding that the micro currency order spent from is a "PublicCurrencyHolding" or a "PrivateCurrencyHolding"
spent-currency-id | The ID of the spent currency
spent-currency-name | The name of the spent currency
spent-currency-icon-url | The URL of the icon of the spent currency
before-amount-atomic | The balance, in atomic units, of the currency holding before it was debited by the micro currency order
after-amount-atomic | The balance, in atomic units, of the currency holding after it was debited by the micro currency order
created-at | The time and date when the micro currency order was created
updated-at | The time and date when the micro currency order was last updated

## Authenticate with Transaction to Private Currency Holding

This endpoint verifies whether an issuance or transfer, sent by the issuer of the currency, of the amount and after the time provided, respectively, credited the specified private currency holding.

```shell
curl 'https://api.mycurrency.com/users/2/authorized_private_currency_holdings/2/pr_h_authentication_transaction?amount=100&start_time=1555333832' \
  -H 'Accept: application/json' -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer j47lbjj8r9n5yy8mup6cxqc8h70yvhnilm0g84kg0raqckus0k1koj9f75ao'
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "type": "transaction-authentication-status",
    "attributes": {
      "transaction-authentication-status": true
    }
  }
}
```

### HTTP Request

`GET https://api.mycurrency.com/users/<USER-ID>/authorized_private_currency_holdings/<PRIVATE-CURRENCY-HOLDING-ID>/pr_h_authentication_transaction?amount={}&start_time={}`

<aside class="notice"> Authentication: the request requires the OAuth access-token associated with the User referenced by the ID
</aside>

### ARGUMENTS

Parameter | Type | Required | Description
--------- | ------- | ------- | -----------
user_id | integer | yes | The ID of the logged in user, provided in URL path
authorized_private_currency_holding_id | integer | yes | The ID of the logged in user's private currency holding, provided in URL path
amount | integer | yes | The amount that a transfer or issuance has to match in order for the endpoint to return true, in whole units
start_time | integer | no | A unix timestamp. The transfers and issuances received by the private currency holding after the provided timestamp are checked to see if they match the amount value. If no start_time argument is provided, the endpoint defaults to a unix timestamp of 0, which results in all issuances and transfers that the private currency holding has ever received being checked.

### RESPONSE

Parameter | Description
--------- | -----------
transaction-authentication-status | Whether a transaction of the amount and after the start_time provided was received by the specified private currency holding 

# Issuances

## Get an Issuance

```shell
curl 'https://api.mycurrency.com/issuances/1' -H 'Accept: application/json' -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer j47lbjj8r9n5yy8mup6cxqc8h70yvhnilm0g84kg0raqckus0k1koj9f75ao'
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "id": "1",
    "type": "issuances",
    "attributes": {
      "proposed-issuance-id": null,
      "amount-atomic": 10000000000000,
      "is-genesis-issuance": true,
      "issuance-receiver-currency-holding-type": "PrivateCurrencyHolding",
      "issuance-receiver-currency-holding-id": 1,
      "day-counter": 0,
      "burnrate-period-id": 1,
      "before-amount-atomic": 0,
      "after-amount-atomic": 10000000000000,
      "issueing-user-id": 3,
      "issuer-username": "Hannibal",
      "receiving-user-id": 3,
      "receiver-username": "Hannibal",
      "receiving-user-avatar-url": "/avatars/original/missing.png",
      "issued-currency-id": 1,
      "issued-currency-name": "Calm dollars",
      "issued-currency-icon-url": "/system/currencies/icons/000/000/001/original/currency.jpg?1561201201",
      "created-at": "2018-08-12T01:17:31.260-07:00",
      "updated-at": "2018-08-12T01:17:31.260-07:00"
    }
  }
}
```

This endpoint retrieves a particular issuance. The logged in user must be active and be either the issuer or the receiver of the issuance to view it.

### HTTP Request

`GET https://api.mycurrency.com/issuances/<ID>`

<aside class="notice">
Authentication: the request requires the OAuth access-token associated with the User referenced by the ID 
</aside>

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the issuance
proposed-issuance-id | The ID of the proposed issuance that initiated the creation of the issuance, null if the issuance has no associated proposed_issuance
amount-atomic | The amount of currency issued, in atomic units (each whole unit is composed of 10^10 atomic units)
is-genesis-issuance | Whether the issuance was created as part of the creation of a new currency. When a new currency is created, 1000 units of the currency are issued to the currency issuer without the 5 percent issuance_fee being paid to the site administration
issuance-receiver-currency-holding-type | Whether the currency holding that the issuance credited to is a "PublicCurrencyHolding" or a "PrivateCurrencyHolding". All issuances are made to the private currency holding of the receiver
issuance-receiver-currency-holding-id | The ID of the public or private currency holding that the issuance credited to, only shown if the issuance receiver is the logged-in user
day-counter | The day counter of the currency holding when it was credited by the issuance, only shown if the issuance receiver is the logged-in user
burnrate-period-id | The ID of the burnrate period of the receiving currency holding when it received the issuance, only shown if the issuance receiver is the logged-in user
before-amount-atomic | The balance, in atomic units, of the currency holding before it was credited by the issuance, only shown if the issuance receiver is the logged-in user
after-amount-atomic | The balance, in atomic units, of the currency holding after it was credited by the issuance, only shown if the issuance receiver is the logged-in user
issueing-user-id | The ID of the issueing user, only shown if the issuance receiver is the logged-in user 
issuer-username | The username of the issueing user, only shown if the issuance receiver is the logged-in user
receiving-user-id | The ID of the issuance receiver, only shown if the issuer is the logged-in user
receiver-username | The username of the issuance sender, only shown if the issuer is the logged-in user 
receiver-user-avatar-url | The URL of the avatar of the issuer, only shown if the issuer is the logged-in user 
issued-currency-id | The ID of the issued currency
issued-currency-name | The name of the issued currency
issued-currency-icon-url | The URL of the icon of the issued currency
created-at | The time and date when the transfer was created
updated-at | The time and date when the transfer was last updated

## List User's Issuances

```shell
curl 'https://api.mycurrency.com/issuances?receiving_user_id=3' \
  -H 'Accept: application/json' -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer j47lbjj8r9n5yy8mup6cxqc8h70yvhnilm0g84kg0raqckus0k1koj9f75ao'
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": "1",
      "type": "issuances",
      "attributes": {
        "proposed-issuance-id": null,
        "amount-atomic": 10000000000000,
        "is-genesis-issuance": true,
        "issuance-receiver-currency-holding-type": "PrivateCurrencyHolding",
        "issuance-receiver-currency-holding-id": 1,
        "day-counter": 0,
        "burnrate-period-id": 1,
        "before-amount-atomic": 0,
        "after-amount-atomic": 10000000000000,
        "issueing-user-id": 3,
        "issuer-username": "Hannibal",
        "receiving-user-id": 3,
        "receiver-username": "Hannibal",
        "receiving-user-avatar-url": "/avatars/original/missing.png",
        "issued-currency-id": 1,
        "issued-currency-name": "Calm dollars",
        "issued-currency-icon-url": "/system/currencies/icons/000/000/001/original/currency.jpg?1561201201",
        "created-at": "2018-08-12T01:17:31.260-07:00",
        "updated-at": "2018-08-12T01:17:31.260-07:00"
      }
    },
    {
      "id": "2",
      "type": "issuances",
      "attributes": {
        "proposed-issuance-id": null,
        "amount-atomic": 10000000000000,
        "is-genesis-issuance": true,
        "issuance-receiver-currency-holding-type": "PrivateCurrencyHolding",
        "issuance-receiver-currency-holding-id": 1,
        "day-counter": 0,
        "burnrate-period-id": 1,
        "before-amount-atomic": 0,
        "after-amount-atomic": 10000000000000,
        "issueing-user-id": 3,
        "issuer-username": "Hannibal",
        "receiving-user-id": 3,
        "receiver-username": "Hannibal",
        "receiving-user-avatar-url": "/avatars/original/missing.png",
        "issued-currency-id": 2,
        "issued-currency-name": "ACME Toon Shop dollars",
        "issued-currency-icon-url": "/system/currencies/icons/000/000/002/original/currency.jpg?1561020503",
        "created-at": "2018-08-12T01:17:31.260-07:00",
        "updated-at": "2018-08-12T01:17:31.260-07:00"
      }
    },
    {
      "id": "3",
      "type": "issuances",
      "attributes": {
        "proposed-issuance-id": null,
        "amount-atomic": 10000000000000,
        "is-genesis-issuance": true,
        "issuance-receiver-currency-holding-type": "PrivateCurrencyHolding",
        "issuance-receiver-currency-holding-id": 3,
        "day-counter": 0,
        "burnrate-period-id": 3,
        "before-amount-atomic": 0,
        "after-amount-atomic": 10000000000000,
        "issueing-user-id": 3,
        "issuer-username": "Hannibal",
        "receiving-user-id": 3,
        "receiver-username": "Hannibal",
        "receiving-user-avatar-url": "/avatars/original/missing.png",
        "issued-currency-id": 3,
        "issued-currency-name": "macaroon dollars",
        "issued-currency-icon-url": "/system/currencies/icons/000/000/003/original/currency.jpg?1561113125",
        "created-at": "2018-08-19T14:24:09.642-07:00",
        "updated-at": "2018-08-19T14:24:09.642-07:00"
      }
    }
  ],
  "links": {
    "self": "https://api.mycurrency.com/issuances?receiving_user_id=3",
    "first": "https://api.mycurrency.com/issuances?page=1&per_page=25&receiving_user_id=3",
    "prev": null,
    "next": null,
    "last": "https://api.mycurrency.com/issuances?page=1&per_page=25&receiving_user_id=3"
  },
  "meta": {
    "pagination": {
      "per-page": null,
      "total-pages": "1",
      "total-count": "3"
    }
  }
}
```

This endpoint retrieves all received or created issuances of a user. The logged in user must be active to view the issuances. 

### HTTP Request

`GET https://api.mycurrency.com/issuances?receiving_user_id=<USER-ID>`

<aside class="notice">
Authentication: the request requires the OAuth access-token associated with the User referenced by the USER-ID 
</aside>

### ARGUMENTS

Parameter | Type | Required | Description
--------- | ------- | ------- | -----------
receiving_user_id | integer | required if :issueing_user_id not provided | The ID of the issuance receiver. If provided, the incoming issuances of the specified user are returned.
issueing_user_id | integer |  required if :receiving_user_id not provided| The ID of the issuance creator. If provided, the outgoing issuances of the specified user are returned.

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the issuance
proposed-issuance-id | The ID of the proposed issuance that initiated the creation of the issuance, null if the issuance has no associated proposed_issuance
amount-atomic | The amount of currency issued, in atomic units (each whole unit is composed of 10^10 atomic units)
is-genesis-issuance | Whether the issuance was created as part of the creation of a new currency. When a new currency is created, 1000 units of the currency are issued to the currency issuer without the 5 percent issuance_fee being paid to the site administration
issuance-receiver-currency-holding-type | Whether the currency holding that the issuance credited to is a "PublicCurrencyHolding" or a "PrivateCurrencyHolding". All issuances are made to the private currency holding of the receiver
issuance-receiver-currency-holding-id | The ID of the public or private currency holding that the issuance credited to, only shown if the issuance receiver is the logged-in user
day-counter | The day counter of the currency holding when it was credited by the issuance, only shown if the issuance receiver is the logged-in user
burnrate-period-id | The ID of the burnrate period of the receiving currency holding when it received the issuance, only shown if the issuance receiver is the logged-in user
before-amount-atomic | The balance, in atomic units, of the currency holding before it was credited by the issuance, only shown if the issuance receiver is the logged-in user
after-amount-atomic | The balance, in atomic units, of the currency holding after it was credited by the issuance, only shown if the issuance receiver is the logged-in user
issueing-user-id | The ID of the issueing user, only shown if the issuance receiver is the logged-in user 
issuer-username | The username of the issueing user, only shown if the issuance receiver is the logged-in user
receiving-user-id | The ID of the issuance receiver, only shown if the issuer is the logged-in user
receiver-username | The username of the issuance sender, only shown if the issuer is the logged-in user 
receiver-user-avatar-url | The URL of the avatar of the issuer, only shown if the issuer is the logged-in user 
issued-currency-id | The ID of the issued currency
issued-currency-name | The name of the issued currency
issued-currency-icon-url | The URL of the icon of the issued currency
created-at | The time and date when the transfer was created
updated-at | The time and date when the transfer was last updated

## List User's Issuances of Particular Currency

```shell
curl 'https://api.mycurrency.com/currencies/3/issuances?issueing_user_id=4' \
  -H 'Accept: application/json' -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer j47lbjj8r9n5yy8mup6cxqc8h70yvhnilm0g84kg0raqckus0k1koj9f75ao'
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": "3",
      "type": "issuances",
      "attributes": {
        "proposed-issuance-id": null,
        "amount-atomic": 10000000000000,
        "is-genesis-issuance": true,
        "issuance-receiver-currency-holding-type": "PrivateCurrencyHolding",
        "issuance-receiver-currency-holding-id": 5,
        "day-counter": 0,
        "burnrate-period-id": 7,
        "before-amount-atomic": 0,
        "after-amount-atomic": 10000000000000,
        "issueing-user-id": 4,
        "issuer-username": "ScipioAfricanus",
        "receiving-user-id": 4,
        "receiver-username": "ScipioAfricanus",
        "receiving-user-avatar-url": "/system/users/avatars/000/000/004/original/1.jpg?1559736060",
        "issued-currency-id": 3,
        "issued-currency-name": "Moon hotel coins",
        "issued-currency-icon-url": "/icons/original/missing.png",
        "created-at": "2018-11-05T11:02:43.272-08:00",
        "updated-at": "2018-11-05T11:02:43.272-08:00"
      }
    },
    {
      "id": "4",
      "type": "issuances",
      "attributes": {
        "proposed-issuance-id": null,
        "amount-atomic": 10000000000000,
        "is-genesis-issuance": false,
        "issuance-receiver-currency-holding-type": "PrivateCurrencyHolding",
        "issuance-receiver-currency-holding-id": 5,
        "day-counter": 0,
        "burnrate-period-id": 7,
        "before-amount-atomic": 10000000000000,
        "after-amount-atomic": 20000000000000,
        "issueing-user-id": 4,
        "issuer-username": "ScipioAfricanus",
        "receiving-user-id": 4,
        "receiver-username": "ScipioAfricanus",
        "receiving-user-avatar-url": "/system/users/avatars/000/000/004/original/1.jpg?1559736060",
        "issued-currency-id": 3,
        "issued-currency-name": "Moon hotel coins",
        "issued-currency-icon-url": "/icons/original/missing.png",
        "created-at": "2018-11-05T11:03:46.101-08:00",
        "updated-at": "2018-11-05T11:03:46.101-08:00"
      }
    }
  ],
  "links": {
    "self": "https://api.mycurrency.com/currencies/3/issuances?issueing_user_id=4",
    "first": "https://api.mycurrency.com/currencies/3/issuances?issueing_user_id=4&page=1&per_page=25",
    "prev": null,
    "next": null,
    "last": "https://api.mycurrency.com/currencies/3/issuances?issueing_user_id=4&page=1&per_page=25"
  },
  "meta": {
    "pagination": {
      "per-page": null,
      "total-pages": "1",
      "total-count": "2"
    }
  }
}
```

This endpoint retrieves all received or created issuances of a user associated with the currency specified by CURRENCY-ID. The logged in user must be active to view the issuances. 

### HTTP Request

`GET https://api.mycurrency.com/currencies/<CURRENCY-ID>/issuances?issueing_user_id=<USER-ID>`

<aside class="notice">
Authentication: the request requires the OAuth access-token associated with the User referenced by the USER-ID 
</aside>

### ARGUMENTS

Parameter | Type | Required | Description
--------- | ------- | ------- | -----------
currency_id | integer | yes | Issuances of the specified currency are returned, provided in URL path
receiving_user_id | integer | required if :issueing_user_id not provided | The ID of the issuance receiver. If provided, the incoming issuances of the specified user are returned.
issueing_user_id | integer |  required if :receiving_user_id not provided| The ID of the issuance creator. If provided, the outgoing issuances of the specified user are returned.

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the issuance
proposed-issuance-id | The ID of the proposed issuance that initiated the creation of the issuance, null if the issuance has no associated proposed_issuance
amount-atomic | The amount of currency issued, in atomic units (each whole unit is composed of 10^10 atomic units)
is-genesis-issuance | Whether the issuance was created as part of the creation of a new currency. When a new currency is created, 1000 units of the currency are issued to the currency issuer without the 5 percent issuance_fee being paid to the site administration
issuance-receiver-currency-holding-type | Whether the currency holding that the issuance credited to is a "PublicCurrencyHolding" or a "PrivateCurrencyHolding". All issuances are made to the private currency holding of the receiver
issuance-receiver-currency-holding-id | The ID of the public or private currency holding that the issuance credited to, only shown if the issuance receiver is the logged-in user
day-counter | The day counter of the currency holding when it was credited by the issuance, only shown if the issuance receiver is the logged-in user
burnrate-period-id | The ID of the burnrate period of the receiving currency holding when it received the issuance, only shown if the issuance receiver is the logged-in user
before-amount-atomic | The balance, in atomic units, of the currency holding before it was credited by the issuance, only shown if the issuance receiver is the logged-in user
after-amount-atomic | The balance, in atomic units, of the currency holding after it was credited by the issuance, only shown if the issuance receiver is the logged-in user
issueing-user-id | The ID of the issueing user, only shown if the issuance receiver is the logged-in user 
issuer-username | The username of the issueing user, only shown if the issuance receiver is the logged-in user
receiving-user-id | The ID of the issuance receiver, only shown if the issuer is the logged-in user
receiver-username | The username of the issuance sender, only shown if the issuer is the logged-in user 
receiver-user-avatar-url | The URL of the avatar of the issuer, only shown if the issuer is the logged-in user 
issued-currency-id | The ID of the issued currency
issued-currency-name | The name of the issued currency
issued-currency-icon-url | The URL of the icon of the issued currency
created-at | The time and date when the transfer was created
updated-at | The time and date when the transfer was last updated

## Create Issuance

```shell
curl -X POST https://api.mycurrency.com/users/3/issuer/currencies/3/issuances \
  -d '{"issuance": { "amount_atomic": "100000000000", "receiving_user_id": "4"} }' \
  -H 'Authorization: Bearer j47lbjj8r9n5yy8mup6cxqc8h70yvhnilm0g84kg0raqckus0k1koj9f75ao' \
  -H 'Accept: application/json' -H 'Content-Type: application/json'
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "id": "13",
    "type": "issuances",
    "attributes": {
      "proposed-issuance-id": null,
      "amount-atomic": 10000000000000,
      "is-genesis-issuance": false,
      "issuance-receiver-currency-holding-type": "PrivateCurrencyHolding",
      "issuance-receiver-currency-holding-id": 5,
      "day-counter": 0,
      "burnrate-period-id": 7,
      "before-amount-atomic": 10000000000000,
      "after-amount-atomic": 20000000000000,
      "issueing-user-id": 4,
      "issuer-username": "ScipioAfricanus",
      "receiving-user-id": 4,
      "receiver-username": "ScipioAfricanus",
      "receiving-user-avatar-url": "/system/users/avatars/000/000/004/original/1.jpg?1559736060",
      "issued-currency-id": 3,
      "issued-currency-name": "Moon hotel coins",
      "issued-currency-icon-url": "/icons/original/missing.png",
      "created-at": "2018-11-05T11:03:46.101-08:00",
      "updated-at": "2018-11-05T11:03:46.101-08:00"
    }
  }
}
```

Creates an issuance.

### HTTP Request

`https://api.mycurrency.com/users/<USER-ID>/issuer/currencies/<CURRENCY-ID>/issuances`

<aside class="notice">
Authentication: the request requires the OAuth access-token associated with the User referenced by the ID 
</aside>

### ARGUMENTS

Parameter | Type | Required | Description
--------- | ------- | ------- | -----------
user_id | integer | yes | The ID of the user creating the issuance, provided in URL path
currency_id | integer | yes | The ID of the currency being issued, provided in URL path
amount_atomic | integer | yes | The amount of currency issued, in atomic units (each whole unit is composed of 10^10 atomic units)
receiving_user_id | integer | yes |  The ID of the user that is to receive the issuance

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the issuance
proposed-issuance-id | The ID of the proposed issuance that initiated the creation of the issuance, null if the issuance has no associated proposed_issuance
amount-atomic | The amount of currency issued, in atomic units (each whole unit is composed of 10^10 atomic units)
is-genesis-issuance | Whether the issuance was created as part of the creation of a new currency. When a new currency is created, 1000 units of the currency are issued to the currency issuer without the 5 percent issuance_fee being paid to the site administration
issuance-receiver-currency-holding-type | Whether the currency holding that the issuance credited to is a "PublicCurrencyHolding" or a "PrivateCurrencyHolding". All issuances are made to the private currency holding of the receiver
issuance-receiver-currency-holding-id | The ID of the public or private currency holding that the issuance credited to, only shown if the issuance receiver is the logged-in user
day-counter | The day counter of the currency holding when it was credited by the issuance, only shown if the issuance receiver is the logged-in user
burnrate-period-id | The ID of the burnrate period of the receiving currency holding when it received the issuance, only shown if the issuance receiver is the logged-in user
before-amount-atomic | The balance, in atomic units, of the currency holding before it was credited by the issuance, only shown if the issuance receiver is the logged-in user
after-amount-atomic | The balance, in atomic units, of the currency holding after it was credited by the issuance, only shown if the issuance receiver is the logged-in user
issueing-user-id | The ID of the issueing user, only shown if the issuance receiver is the logged-in user 
issuer-username | The username of the issueing user, only shown if the issuance receiver is the logged-in user
receiving-user-id | The ID of the issuance receiver, only shown if the issuer is the logged-in user
receiver-username | The username of the issuance sender, only shown if the issuer is the logged-in user 
receiver-user-avatar-url | The URL of the avatar of the issuer, only shown if the issuer is the logged-in user 
issued-currency-id | The ID of the issued currency
issued-currency-name | The name of the issued currency
issued-currency-icon-url | The URL of the icon of the issued currency
created-at | The time and date when the transfer was created
updated-at | The time and date when the transfer was last updated

# Transfers

## Get a Transfer

```shell
curl 'https://api.mycurrency.com/transfers/7' -H 'Accept: application/json' \
  -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer j47lbjj8r9n5yy8mup6cxqc8h70yvhnilm0g84kg0raqckus0k1koj9f75ao'
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "id": "7",
    "type": "transfers",
    "attributes": {
      "amount-atomic": 500000000000,
      "receiving-user-id": 3,
      "receiver-username": "Hannibal",
      "receiving-user-avatar-url": "/system/users/avatars/000/000/003/original/avatar.jpg?1561125132",
      "sender-day-counter": 36,
      "sender-burnrate-period-id": 10
      "transfer-sender-currency-holding-type": "PrivateCurrencyHolding",
      "transfer-receiver-currency-holding-type": "PrivateCurrencyHolding",
      "transfer-sender-currency-holding-id": 5,
      "sender-before-amount-atomic": 9918678637475,
      "sender-after-amount-atomic": 9418678637475,
      "transferred-currency-id": 5,
      "transferred-currency-name": "Freds Fishing Supplies dollars",
      "transferred-currency-icon-url": "/system/currencies/icons/000/000/005/original/currency.jpg?1550842432",
      "created-at": "2018-10-03T00:20:58.124-07:00",
      "updated-at": "2018-10-03T00:20:58.124-07:00"
    }
  }
}
```

This endpoint retrieves a particular transfer. The logged in user must be active and be either the transferrer or the receiver of the transfer to view it.

### HTTP Request

`GET https://api.mycurrency.com/transfers/<ID>`

<aside class="notice">
Authentication: the request requires the OAuth access-token associated with the User referenced by the ID 
</aside>

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the transfer
amount-atomic | The amount of currency transferred, in atomic units (each whole unit is composed of 10^10 atomic units)
receiving-user-id | The ID of the transfer receiver, only shown if the owner of the currency holding that the transfer debited from is the logged-in user
receiver-username | The username of the transfer receiver, only shown if the owner of the currency holding that the transfer debited from is the logged-in user 
receiver-user-avatar-url | The URL of the avatar of the transfer receiver, only shown if the owner of the currency holding that the transfer debited from is the logged-in user 
sender-day-counter | The day counter of the sending currency holding when it was debited by the transfer, only shown if the owner of the currency holding that the transfer debited from is the logged-in user
receiver-day-counter | The day counter of the receiving currency holding when it was credited by the transfer, only shown if the owner of the currency holding that the transfer credited to is the logged-in user
sender-burnrate-period-id | The ID of the burnrate period of the sending currency holding when it was debited by the transfer, only shown if the owner of the currency holding that the transfer debited from is the logged-in user
receiver-burnrate-period-id | The ID of the burnrate period of the receiving currency holding when it was credited by the transfer, only shown if the owner of the currency holding that the transfer credited to is the logged-in user
transfer-sender-currency-holding-type | Whether the currency holding that the transfer debited from is a "PublicCurrencyHolding" or a "PrivateCurrencyHolding", only shown if the owner of the currency holding that the transfer debited from is the logged-in user
transfer-sender-currency-holding-id | The ID of the public or private currency holding that the transfer debited from, only shown if the owner of the currency holding that the transfer debited from is the logged-in user
transfer-receiver-currency-holding-type | Whether the currency holding that the transfer credited to is a "PublicCurrencyHolding" or a "PrivateCurrencyHolding"
transfer-receiver-currency-holding-id | The ID of the public or private currency holding that the transfer credited to, only shown if the owner of the currency holding that the transfer credited to is the logged-in user
sending-user-id | The ID of the transfer sender, only shown if the owner of the currency holding that the transfer credited to is the logged-in user 
sender-username | The username of the transfer sender, only shown if the owner of the currency holding that the transfer credited to is the logged-in user
sender-user-avatar-url | The URL of the avatar of the transfer receiver, only shown if the owner of the currency holding that the transfer credited to is the logged-in user
sender-before-amount-atomic | The balance, in atomic units, of the sending currency holding before it was debited from by the transfer, only shown if the owner of the currency holding that the transfer debited from is the logged-in user
sender-after-amount-atomic | The balance, in atomic units, of the sending currency holding after it was debited from by the transfer, only shown if the owner of the currency holding that the transfer debited from is the logged-in user
receiver-before-amount-atomic | The balance, in atomic units, of the receiving currency holding before it was credited to by the transfer, only shown if the owner of the currency holding that the transfer credited to is the logged-in user
receiver-after-amount-atomic | The balance, in atomic units, of the receiving currency holding after it was credited to by the transfer, only shown if the owner of the currency holding that the transfer credited to is the logged-in user
transferred-currency-id | The ID of the transferred currency
transferred-currency-name | The name of the transferred currency
transferred-currency-icon-url | The URL of the icon of the transferred currency
created-at | The time and date when the transfer was created
updated-at | The time and date when the transfer was last updated

## Create Transfer

```shell
curl -X POST https://api.mycurrency.com/users/4/transfers \
  -d '{"transfer": { "amount_atomic": "10000000000", "receiving_user_id": "3", "transfer_sender_currency_holding_id": "5", "transfer_sender_currency_holding_type": "PrivateCurrencyHolding"} }' \
  -H 'Authorization: Bearer j47lbjj8r9n5yy8mup6cxqc8h70yvhnilm0g84kg0raqckus0k1koj9f75ao' \
  -H 'Accept: application/json' -H 'Content-Type: application/json'
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "id": "8",
    "type": "transfers",
    "attributes": {
      "amount-atomic": 10000000000,
      "receiving-user-id": 3,
      "receiver-username": "Hannibal",
      "receiving-user-avatar-url": "/system/users/avatars/000/000/003/original/avatar.jpg?1561125132",
      "sender-day-counter": 43,
      "sender-burnrate-period-id": 10
      "transfer-sender-currency-holding-type": "PrivateCurrencyHolding",
      "transfer-receiver-currency-holding-type": "PrivateCurrencyHolding",
      "transfer-sender-currency-holding-id": 5,   
      "sender-before-amount-atomic": 9395579089463,
      "sender-after-amount-atomic": 9385579089463,
      "transferred-currency-id": 5,
      "transferred-currency-name": "Freds Fishing Supplies dollars",
      "transferred-currency-icon-url": "/system/currencies/icons/000/000/005/original/currency.jpg?1550842432",
      "created-at": "2018-10-10T16:57:37.062-07:00",
      "updated-at": "2018-10-10T16:57:37.062-07:00"
    }
  }
}
```

Creates a transfer.

### HTTP Request

`https://api.mycurrency.com/users/<USER-ID>/transfers`

<aside class="notice">
Authentication: the request requires the OAuth access-token associated with the User referenced by the ID 
</aside>

### ARGUMENTS

Parameter | Type | Required | Description
--------- | ------- | ------- | -----------
user_id | integer | yes | The ID of the user creating the transfer, provided in URL path
amount_atomic | integer | yes | The amount of currency transferred, in atomic units (each whole unit is composed of 10^10 atomic units)
receiving_user_id | integer | yes |  The ID of the user that is to receive the transfer
transfer_sender_currency_holding_id | integer | yes | The ID of the currency holding from which the transfer is debiting from
transfer_sender_currency_holding_type | string | no | Whether the currency holding that the transfer is debiting from is a "PublicCurrencyHolding" or a "PrivateCurrencyHolding". If no value is provided, it will default to "PrivateCurrencyHolding"
transfer_sender_currency_holding_type | string | no | Whether the currency holding that the transfer is crediting to is a "PublicCurrencyHolding" or a "PrivateCurrencyHolding". If no value is provided, it will default to "PrivateCurrencyHolding". You cannot set this parameter to "PublicCurrencyHolding" unless the transfer is a self send of a currency from a user's private holding to public holding.

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the transfer
amount-atomic | The amount of currency transferred, in atomic units (each whole unit is composed of 10^10 atomic units)
receiving-user-id | The ID of the transfer receiver, only shown if the owner of the currency holding that the transfer debited from is the logged-in user
receiver-username | The username of the transfer receiver, only shown if the owner of the currency holding that the transfer debited from is the logged-in user 
receiver-user-avatar-url | The URL of the avatar of the transfer receiver, only shown if the owner of the currency holding that the transfer debited from is the logged-in user 
sender-day-counter | The day counter of the sending currency holding when it was debited by the transfer, only shown if the owner of the currency holding that the transfer debited from is the logged-in user
receiver-day-counter | The day counter of the receiving currency holding when it was credited by the transfer, only shown if the owner of the currency holding that the transfer credited to is the logged-in user
sender-burnrate-period-id | The ID of the burnrate period of the sending currency holding when it was debited by the transfer, only shown if the owner of the currency holding that the transfer debited from is the logged-in user
receiver-burnrate-period-id | The ID of the burnrate period of the receiving currency holding when it was credited by the transfer, only shown if the owner of the currency holding that the transfer credited to is the logged-in user
transfer-sender-currency-holding-type | Whether the currency holding that the transfer debited from is a "PublicCurrencyHolding" or a "PrivateCurrencyHolding", only shown if the owner of the currency holding that the transfer debited from is the logged-in user
transfer-sender-currency-holding-id | The ID of the public or private currency holding that the transfer debited from, only shown if the owner of the currency holding that the transfer debited from is the logged-in user
transfer-receiver-currency-holding-type | Whether the currency holding that the transfer credited to is a "PublicCurrencyHolding" or a "PrivateCurrencyHolding"
transfer-receiver-currency-holding-id | The ID of the public or private currency holding that the transfer credited to, only shown if the owner of the currency holding that the transfer credited to is the logged-in user
sending-user-id | The ID of the transfer sender, only shown if the owner of the currency holding that the transfer credited to is the logged-in user 
sender-username | The username of the transfer sender, only shown if the owner of the currency holding that the transfer credited to is the logged-in user
sender-user-avatar-url | The URL of the avatar of the transfer receiver, only shown if the owner of the currency holding that the transfer credited to is the logged-in user
sender-before-amount-atomic | The balance, in atomic units, of the sending currency holding before it was debited from by the transfer, only shown if the owner of the currency holding that the transfer debited from is the logged-in user
sender-after-amount-atomic | The balance, in atomic units, of the sending currency holding after it was debited from by the transfer, only shown if the owner of the currency holding that the transfer debited from is the logged-in user
receiver-before-amount-atomic | The balance, in atomic units, of the receiving currency holding before it was credited to by the transfer, only shown if the owner of the currency holding that the transfer credited to is the logged-in user
receiver-after-amount-atomic | The balance, in atomic units, of the receiving currency holding after it was credited to by the transfer, only shown if the owner of the currency holding that the transfer credited to is the logged-in user
transferred-currency-id | The ID of the transferred currency
transferred-currency-name | The name of the transferred currency
transferred-currency-icon-url | The URL of the icon of the transferred currency
created-at | The time and date when the transfer was created
updated-at | The time and date when the transfer was last updated

# Offers

## Get an Offer

```shell
curl 'https://api.mycurrency.com/users/2/offers/9' -H 'Accept: application/json' \
  -H 'Content-Type: application/json' -H 'Authorization: Bearer j47lbjj8r9n5yy8mup6cxqc8h70yvhnilm0g84kg0raqckus0k1koj9f75ao'
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "id": "9",
    "type": "offers",
    "attributes": {
      "offer-receiver-id": 2,
      "offer-receiver-username": "spiderman",
      "offer-receiver-avatar-url": "/system/users/avatars/original/missing.png",
      "offer-sender-id": 3,
      "offer-sender-username": "Hannibal",
      "offer-sender-avatar-url": "/system/users/avatars/000/000/003/original/avatar.jpg?1562578009",
      "previous-offer-id": 8,
      "requested-proposed-transactions": {
        "data": [
          {
            "id": "9",
            "type": "proposed-issuances",
            "attributes": {
              "offer-id": 9,
              "source-currency-id": 4,
              "source-currency-name": "spiderman pizza dollars",
              "source-currency-icon-url": "/system/currencies/icons/missing.png",
              "source-currency-burn-rate": 420,
              "source-currency-daily-burn-rate": "0.000117548",
              "source-currency-store-count": 3,
              "currency-issuer-id": 2,
              "currency-issuer-username": "spiderman",
              "currency-sender-public-holding-amount-atomic": 3200000000000,
              "amount-atomic": 50000000000,
              "products": {
                "data": [
                  {
                    "id": "52",
                    "type": "products",
                    "attributes": {
                      "sub-category-id": 20,
                      "sub-category-name": "kid's clothing",
                      "currency-id": 4,
                      "currency-name": "spiderman pizza dollars",
                      "currency-icon-url": "/system/currencies/icons/missing.png",
                      "issuer-public-currency-holding-id": 54,
                      "days-to-cancellation": null,
                      "minutes-to-cancellation": null,
                      "store-id": 29,
                      "store-name": "Spiderman store",
                      "product-name": "spidermask",
                      "product-description": "a spiderman mask",
                      "price-cents": 200,
                      "active": true,
                      "continued": true,
                      "last-activated-at": "2019-07-29T17:07:27.574-07:00",
                      "created-at": "2019-07-29T17:07:27.574-07:00",
                      "updated-at": "2019-07-29T17:07:27.574-07:00",
                      "get-image-url": "/system/products/images/original/missing.png"
                    }
                  }
                ]
              },
              "active": false,
              "created-at": "2019-07-21T18:32:30.728-07:00",
              "updated-at": "2019-07-21T18:32:49.020-07:00"
            }
          }
        ]
      },
      "offered-proposed-transactions": {
        "data": [
          {
            "id": "9",
            "type": "proposed-transfers",
            "attributes": {
              "offer-id": 9,
              "source-currency-holding-id": 2,
              "source-currency-id": 1,
              "source-currency-name": "Micro Asteroid bucks",
              "source-currency-icon-url": "/system/currencies/icons/missing.png",
              "source-currency-burn-rate": 450,
              "source-currency-daily-burn-rate": "0.00012614",
              "source-currency-store-count": 2,
              "currency-sender-id": 3,
              "currency-sender-username": "Hannibal",
              "currency-sender-public-holding-amount-atomic": 3599957849922,
              "amount-atomic": 50000000000,
              "products": {
                "data": [
                  {
                    "id": "51",
                    "type": "products",
                    "attributes": {
                      "sub-category-id": 12,
                      "sub-category-name": "computer accessories",
                      "currency-id": 1,
                      "currency-name": "Micro Asteroid bucks",
                      "currency-icon-url": "/system/currencies/icons/missing.png",
                      "issuer-public-currency-holding-id": 2,
                      "days-to-cancellation": null,
                      "minutes-to-cancellation": null,
                      "store-id": 28,
                      "store-name": "Moon Store",
                      "product-name": "Lunar solar panels",
                      "product-description": "solar panels designed to be installed on the moon",
                      "price-cents": 100000,
                      "active": true,
                      "continued": true,
                      "last-activated-at": "2019-07-29T16:56:30.169-07:00",
                      "created-at": "2019-07-29T16:56:30.169-07:00",
                      "updated-at": "2019-07-29T16:56:30.169-07:00",
                      "get-image-url": "/system/products/images/original/missing.png"
                    }
                  },
                  {
                    "id": "40",
                    "type": "products",
                    "attributes": {
                      "sub-category-id": 15,
                      "sub-category-name": "audio equipment",
                      "currency-id": 1,
                      "currency-name": "Micro Asteroid bucks",
                      "currency-icon-url": "/system/currencies/icons/missing.png",
                      "issuer-public-currency-holding-id": 2,
                      "days-to-cancellation": null,
                      "minutes-to-cancellation": null,
                      "store-id": 1,
                      "store-name": "Asteroid Industries",
                      "product-name": "goliath rocket 2",
                      "product-description": "second version of rocket for reaching the moon",
                      "price-cents": 1000000,
                      "active": true,
                      "continued": true,
                      "last-activated-at": "2019-07-26T04:57:32.173-07:00",
                      "created-at": "2019-07-26T04:57:32.173-07:00",
                      "updated-at": "2019-07-26T04:57:32.173-07:00",
                      "get-image-url": "/system/products/images/original/missing.png"
                    }
                  },
                  {
                    "id": "39",
                    "type": "products",
                    "attributes": {
                      "sub-category-id": 15,
                      "sub-category-name": "audio equipment",
                      "currency-id": 1,
                      "currency-name": "Micro Asteroid bucks",
                      "currency-icon-url": "/system/currencies/icons/missing.png",
                      "issuer-public-currency-holding-id": 2,
                      "days-to-cancellation": null,
                      "minutes-to-cancellation": null,
                      "store-id": 1,
                      "store-name": "Asteroid Industries",
                      "product-name": "goliath rocket",
                      "product-description": "rocket for reaching the moon",
                      "price-cents": 1000000,
                      "active": true,
                      "continued": true,
                      "last-activated-at": "2019-07-26T04:51:29.353-07:00",
                      "created-at": "2019-07-26T04:51:29.353-07:00",
                      "updated-at": "2019-07-26T04:51:29.353-07:00",
                      "get-image-url": "/system/products/images/original/missing.png"
                    }
                  }
                ]
              },
              "active": false,
              "created-at": "2019-07-21T18:32:30.727-07:00",
              "updated-at": "2019-07-21T18:32:49.019-07:00"
            }
          }
        ]
      },
      "offer-type": 1,
      "raw-offer-type": 1,
      "active": false,
      "self-cancellation": false,
      "created-at": "2019-07-21T18:32:30.701-07:00",
      "updated-at": "2019-07-21T18:32:49.017-07:00"
    }
  }
}
```

This endpoint retrieves a particular offer. The logged in user must be active and be either the sender or receiver of the offer to view it.

### HTTP Request

`GET https://api.mycurrency.com/users/<USER-ID>/offers/<ID>`

<aside class="notice">
Authentication: the request requires the OAuth access-token associated with the User referenced by the ID 
</aside>

### RESPONSE

### Offer

Parameter | Description
--------- | -----------
id | The ID of the offer
offer-receiver-id | The ID of the user that received the offer
offer-receiver-username | The username of the user that received the offer
offer-receiver-avatar-url | The URL of the avatar of the user that received the offer
offer-sender-id | The ID of the user that made the offer
offer-sender-username | The username of the user that made the offer
offer-sender-avatar-url | The URL of the avatar of the user that made the offer
previous-offer-id | The ID of the offer that is being counter-offered. If the first offer of an offer-chain, the value will be 0
requested-proposed-transactions | An array of proposed transfers and proposed issuances being requested from the offer receiver
offered-proposed-transactions | An array of proposed transfers and proposed issuances being offered by the offer sender
offer-type | 0 is the offer that starts an offer chain, 1 is a counter-offer, 2 is an offer rejection, 3 is an offer acceptance, and 4 is a new offer or counter-offer with a self-cancellation value of true
raw-offer-type | The offer type value in the database. 0 is the offer that starts an offer chain, 1 is a counter-offer, 2 is an offer rejection, and 3 is an offer acceptance
active | Whether the offer is still active and can be countered or accepted/rejected
proposed-transfers | The proposed_transfers included in the offer
proposed-issuances | The proposed_issuances included in the offer
self-cancellation | Whether the offer sender has cancelled the offer by disactivating their user account
created-at | The time and date when the offer was created
updated-at | The time and date when the offer was last updated

### Proposed Transfers

Parameter | Description
--------- | -----------
id | The ID of the proposed transfer
offer-id | The ID of the offer that the proposed transfer is associated with
source-currency-holding-id | The ID of the public currency holding from which the proposed transfer would be sent
source-currency-id | The ID of the currency that is proposed to be transferred
source-currency-name | The name of the currency that is proposed to be transferred
source-currency-icon-url | The URL of the icon of the currency that is proposed to be transferred
source-currency-burn-rate | The burn rate of the currency that is proposed to be transferred
source-currency-daily-burn-rate | The daily burn rate of the currency that is proposed to be transferred
source-currency-store-count | The number of stores associated with the currency that is proposed to be transferred
currency-sender-id | The ID of the user that would send the proposed transfer
currency-sender-username | The username of the user that would send the proposed transfer
currency-sender-public-holding-amount-atomic | The amount of currency in the public holding that the transfer would be sent from, in atomic units (each whole unit is composed of 10^10 atomic units)
amount-atomic | The amount of currency that is proposed to be transferred, in atomic units (each whole unit is composed of 10^10 atomic units)
active | Whether the proposed transfer is still valid or not
products | The three most recently updated products associated with the currency of the proposed_transfer
created-at | The time and date when the proposed transfer was created
updated-at | The time and date when the proposed transfer was last updated

### Proposed Issuances

Parameter | Description
--------- | -----------
id | The ID of the proposed issuance
offer-id | The ID of the offer that the proposed issuance is associated with
source-currency-id | The ID of the currency that is proposed to be issued
source-currency-name | The name of the currency that is proposed to be issued
source-currency-icon-url | The URL of the icon of the currency that is proposed to be transferred
source-currency-burn-rate | The burn rate of the currency that is proposed to be transferred
source-currency-daily-burn-rate | The daily burn rate of the currency that is proposed to be transferred
source-currency-store-count | The number of stores associated with the currency that is proposed to be transferred
currency-issuer-id | The ID of the user that would issue the proposed issuance
currency-issuer-username | The username of the user that would issue the proposed issuance
currency-sender-public-holding-id | The ID of currency in the proposed issuer's public holding of the currency that would be issued
currency-sender-public-holding-amount-atomic | The amount of currency in the proposed issuer's public holding of the currency that would be issued, in atomic units (each whole unit is composed of 10^10 atomic units)
amount-atomic | The amount of currency that is proposed to be issued, in atomic units (each whole unit is composed of 10^10 atomic units)
active | Whether the proposed issuance is still valid or not
products | The three most recently updated products associated with the currency of the proposed_issuance
created-at | The time and date when the proposed issuance was created
updated-at | The time and date when the proposed issuance was last updated

## List Offers

```shell
curl 'https://api.mycurrency.com/users/3/offers?index_type=offer_chain&offer_id=10' \
  -H 'Accept: application/json' -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer j47lbjj8r9n5yy8mup6cxqc8h70yvhnilm0g84kg0raqckus0k1koj9f75ao'
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": "10",
      "type": "offers",
      "attributes": {
        "offer-receiver-id": 3,
        "offer-receiver-username": "Hannibal",
        "offer-receiver-avatar-url": "/system/users/avatars/000/000/003/original/avatar.jpg?1562578009",
        "offer-sender-id": 2,
        "offer-sender-username": "spiderman",
        "offer-sender-avatar-url": "/system/users/avatars/original/missing.png",
        "previous-offer-id": 9,
        "requested-proposed-transactions": {
          "data": []
        },
        "offered-proposed-transactions": {
          "data": []
        },
        "offer-type": 2,
        "raw-offer-type": 2,
        "active": false,
        "self-cancellation": false,
        "created-at": "2019-07-21T18:32:48.989-07:00",
        "updated-at": "2019-07-21T18:32:48.989-07:00"
      }
    },
    {
      "id": "9",
      "type": "offers",
      "attributes": {
        "offer-receiver-id": 2,
        "offer-receiver-username": "spiderman",
        "offer-receiver-avatar-url": "/system/users/avatars/original/missing.png",
        "offer-sender-id": 3,
        "offer-sender-username": "Hannibal",
        "offer-sender-avatar-url": "/system/users/avatars/000/000/003/original/avatar.jpg?1562578009",
        "previous-offer-id": 8,
        "requested-proposed-transactions": {
          "data": [
            {
              "id": "9",
              "type": "proposed-issuances",
              "attributes": {
                "offer-id": 9,
                "source-currency-id": 4,
                "source-currency-name": "spiderman pizza dollars",
                "source-currency-icon-url": "/system/currencies/icons/missing.png",
                "source-currency-burn-rate": 420,
                "source-currency-daily-burn-rate": "0.000117548",
                "source-currency-store-count": 3,
                "currency-issuer-id": 2,
                "currency-issuer-username": "spiderman",
                "currency-sender-public-holding-id": 54,
                "currency-sender-public-holding-amount-atomic": 3200000000000,
                "amount-atomic": 50000000000,
                "products": {
                  "data": [
                    {
                      "id": "52",
                      "type": "products",
                      "attributes": {
                        "sub-category-id": 20,
                        "sub-category-name": "kid's clothing",
                        "currency-id": 4,
                        "currency-name": "spiderman pizza dollars",
                        "currency-icon-url": "/system/currencies/icons/missing.png",
                        "issuer-public-currency-holding-id": 54,
                        "days-to-cancellation": null,
                        "minutes-to-cancellation": null,
                        "store-id": 29,
                        "store-name": "Spiderman store",
                        "product-name": "spidermask",
                        "product-description": "a spiderman mask",
                        "price-cents": 200,
                        "active": true,
                        "continued": true,
                        "last-activated-at": "2019-07-29T17:07:27.574-07:00",
                        "created-at": "2019-07-29T17:07:27.574-07:00",
                        "updated-at": "2019-07-29T17:07:27.574-07:00",
                        "get-image-url": "/system/products/images/original/missing.png"
                      }
                    }
                  ]
                },
                "active": false,
                "created-at": "2019-07-21T18:32:30.728-07:00",
                "updated-at": "2019-07-21T18:32:49.020-07:00"
              }
            }
          ]
        },
        "offered-proposed-transactions": {
          "data": [
            {
              "id": "9",
              "type": "proposed-transfers",
              "attributes": {
                "offer-id": 9,
                "source-currency-holding-id": 2,
                "source-currency-id": 1,
                "source-currency-name": "Micro Asteroid bucks",
                "source-currency-icon-url": "/system/currencies/icons/missing.png",
                "source-currency-burn-rate": 450,
                "source-currency-daily-burn-rate": "0.00012614",
                "source-currency-store-count": 2,
                "currency-sender-id": 3,
                "currency-sender-username": "Hannibal",
                "currency-sender-public-holding-amount-atomic": 3599957849922,
                "amount-atomic": 50000000000,
                "products": {
                  "data": [
                    {
                      "id": "51",
                      "type": "products",
                      "attributes": {
                        "sub-category-id": 12,
                        "sub-category-name": "computer accessories",
                        "currency-id": 1,
                        "currency-name": "Micro Asteroid bucks",
                        "currency-icon-url": "/system/currencies/icons/missing.png",
                        "issuer-public-currency-holding-id": 2,
                        "days-to-cancellation": null,
                        "minutes-to-cancellation": null,
                        "store-id": 28,
                        "store-name": "Moon Store",
                        "product-name": "Lunar solar panels",
                        "product-description": "solar panels designed to be installed on the moon",
                        "price-cents": 100000,
                        "active": true,
                        "continued": true,
                        "last-activated-at": "2019-07-29T16:56:30.169-07:00",
                        "created-at": "2019-07-29T16:56:30.169-07:00",
                        "updated-at": "2019-07-29T16:56:30.169-07:00",
                        "get-image-url": "/system/products/images/original/missing.png"
                      }
                    },
                    {
                      "id": "40",
                      "type": "products",
                      "attributes": {
                        "sub-category-id": 15,
                        "sub-category-name": "audio equipment",
                        "currency-id": 1,
                        "currency-name": "Micro Asteroid bucks",
                        "currency-icon-url": "/system/currencies/icons/missing.png",
                        "issuer-public-currency-holding-id": 2,
                        "days-to-cancellation": null,
                        "minutes-to-cancellation": null,
                        "store-id": 1,
                        "store-name": "Asteroid Industries",
                        "product-name": "goliath rocket 2",
                        "product-description": "second version of rocket for reaching the moon",
                        "price-cents": 1000000,
                        "active": true,
                        "continued": true,
                        "last-activated-at": "2019-07-26T04:57:32.173-07:00",
                        "created-at": "2019-07-26T04:57:32.173-07:00",
                        "updated-at": "2019-07-26T04:57:32.173-07:00",
                        "get-image-url": "/system/products/images/original/missing.png"
                      }
                    },
                    {
                      "id": "39",
                      "type": "products",
                      "attributes": {
                        "sub-category-id": 15,
                        "sub-category-name": "audio equipment",
                        "currency-id": 1,
                        "currency-name": "Micro Asteroid bucks",
                        "currency-icon-url": "/system/currencies/icons/missing.png",
                        "issuer-public-currency-holding-id": 2,
                        "days-to-cancellation": null,
                        "minutes-to-cancellation": null,
                        "store-id": 1,
                        "store-name": "Asteroid Industries",
                        "product-name": "goliath rocket",
                        "product-description": "rocket for reaching the moon",
                        "price-cents": 1000000,
                        "active": true,
                        "continued": true,
                        "last-activated-at": "2019-07-26T04:51:29.353-07:00",
                        "created-at": "2019-07-26T04:51:29.353-07:00",
                        "updated-at": "2019-07-26T04:51:29.353-07:00",
                        "get-image-url": "/system/products/images/original/missing.png"
                      }
                    }
                  ]
                },
                "active": false,
                "created-at": "2019-07-21T18:32:30.727-07:00",
                "updated-at": "2019-07-21T18:32:49.019-07:00"
              }
            }
          ]
        },
        "offer-type": 1,
        "raw-offer-type": 1,
        "active": false,
        "self-cancellation": false,
        "created-at": "2019-07-21T18:32:30.701-07:00",
        "updated-at": "2019-07-21T18:32:49.017-07:00"
      }
    },
    {
      "id": "8",
      "type": "offers",
      "attributes": {
        "offer-receiver-id": 3,
        "offer-receiver-username": "Hannibal",
        "offer-receiver-avatar-url": "/system/users/avatars/000/000/003/original/avatar.jpg?1562578009",
        "offer-sender-id": 2,
        "offer-sender-username": "spiderman",
        "offer-sender-avatar-url": "/system/users/avatars/original/missing.png",
        "previous-offer-id": 7,
        "requested-proposed-transactions": {
          "data": [
            {
              "id": "8",
              "type": "proposed-transfers",
              "attributes": {
                "offer-id": 8,
                "source-currency-holding-id": 2,
                "source-currency-id": 1,
                "source-currency-name": "Micro Asteroid bucks",
                "source-currency-icon-url": "/system/currencies/icons/missing.png",
                "source-currency-burn-rate": 450,
                "source-currency-daily-burn-rate": "0.00012614",
                "source-currency-store-count": 2,
                "currency-sender-id": 3,
                "currency-sender-username": "Hannibal",
                "currency-sender-public-holding-amount-atomic": 3599957849922,
                "amount-atomic": 55000000000,
                "products": {
                  "data": [
                    {
                      "id": "51",
                      "type": "products",
                      "attributes": {
                        "sub-category-id": 12,
                        "sub-category-name": "computer accessories",
                        "currency-id": 1,
                        "currency-name": "Micro Asteroid bucks",
                        "currency-icon-url": "/system/currencies/icons/missing.png",
                        "issuer-public-currency-holding-id": 2,
                        "days-to-cancellation": null,
                        "minutes-to-cancellation": null,
                        "store-id": 28,
                        "store-name": "Moon Store",
                        "product-name": "Lunar solar panels",
                        "product-description": "solar panels designed to be installed on the moon",
                        "price-cents": 100000,
                        "active": true,
                        "continued": true,
                        "last-activated-at": "2019-07-29T16:56:30.169-07:00",
                        "created-at": "2019-07-29T16:56:30.169-07:00",
                        "updated-at": "2019-07-29T16:56:30.169-07:00",
                        "get-image-url": "/system/products/images/original/missing.png"
                      }
                    },
                    {
                      "id": "40",
                      "type": "products",
                      "attributes": {
                        "sub-category-id": 15,
                        "sub-category-name": "audio equipment",
                        "currency-id": 1,
                        "currency-name": "Micro Asteroid bucks",
                        "currency-icon-url": "/system/currencies/icons/missing.png",
                        "issuer-public-currency-holding-id": 2,
                        "days-to-cancellation": null,
                        "minutes-to-cancellation": null,
                        "store-id": 1,
                        "store-name": "Asteroid Industries",
                        "product-name": "goliath rocket 2",
                        "product-description": "second version of rocket for reaching the moon",
                        "price-cents": 1000000,
                        "active": true,
                        "continued": true,
                        "last-activated-at": "2019-07-26T04:57:32.173-07:00",
                        "created-at": "2019-07-26T04:57:32.173-07:00",
                        "updated-at": "2019-07-26T04:57:32.173-07:00",
                        "get-image-url": "/system/products/images/original/missing.png"
                      }
                    },
                    {
                      "id": "39",
                      "type": "products",
                      "attributes": {
                        "sub-category-id": 15,
                        "sub-category-name": "audio equipment",
                        "currency-id": 1,
                        "currency-name": "Micro Asteroid bucks",
                        "currency-icon-url": "/system/currencies/icons/missing.png",
                        "issuer-public-currency-holding-id": 2,
                        "days-to-cancellation": null,
                        "minutes-to-cancellation": null,
                        "store-id": 1,
                        "store-name": "Asteroid Industries",
                        "product-name": "goliath rocket",
                        "product-description": "rocket for reaching the moon",
                        "price-cents": 1000000,
                        "active": true,
                        "continued": true,
                        "last-activated-at": "2019-07-26T04:51:29.353-07:00",
                        "created-at": "2019-07-26T04:51:29.353-07:00",
                        "updated-at": "2019-07-26T04:51:29.353-07:00",
                        "get-image-url": "/system/products/images/original/missing.png"
                      }
                    }
                  ]
                },
                "active": false,
                "created-at": "2019-07-21T18:30:26.916-07:00",
                "updated-at": "2019-07-21T18:32:30.723-07:00"
              }
            }
          ]
        },
        "offered-proposed-transactions": {
          "data": [
            {
              "id": "8",
              "type": "proposed-issuances",
              "attributes": {
                "offer-id": 8,
                "source-currency-id": 4,
                "source-currency-name": "spiderman pizza dollars",
                "source-currency-icon-url": "/system/currencies/icons/missing.png",
                "source-currency-burn-rate": 420,
                "source-currency-daily-burn-rate": "0.000117548",
                "source-currency-store-count": 3,
                "currency-issuer-id": 2,
                "currency-issuer-username": "spiderman",
                "currency-sender-public-holding-id": 54,
                "currency-sender-public-holding-amount-atomic": 3200000000000,
                "amount-atomic": 50000000000,
                "products": {
                  "data": [
                    {
                      "id": "52",
                      "type": "products",
                      "attributes": {
                        "sub-category-id": 20,
                        "sub-category-name": "kid's clothing",
                        "currency-id": 4,
                        "currency-name": "spiderman pizza dollars",
                        "currency-icon-url": "/system/currencies/icons/missing.png",
                        "issuer-public-currency-holding-id": 54,
                        "days-to-cancellation": null,
                        "minutes-to-cancellation": null,
                        "store-id": 29,
                        "store-name": "Spiderman store",
                        "product-name": "spidermask",
                        "product-description": "a spiderman mask",
                        "price-cents": 200,
                        "active": true,
                        "continued": true,
                        "last-activated-at": "2019-07-29T17:07:27.574-07:00",
                        "created-at": "2019-07-29T17:07:27.574-07:00",
                        "updated-at": "2019-07-29T17:07:27.574-07:00",
                        "get-image-url": "/system/products/images/original/missing.png"
                      }
                    }
                  ]
                },
                "active": false,
                "created-at": "2019-07-21T18:30:26.917-07:00",
                "updated-at": "2019-07-21T18:32:30.726-07:00"
              }
            }
          ]
        },
        "offer-type": 1,
        "raw-offer-type": 1,
        "active": false,
        "self-cancellation": false,
        "created-at": "2019-07-21T18:30:26.893-07:00",
        "updated-at": "2019-07-21T18:32:30.719-07:00"
      }
    },
    {
      "id": "7",
      "type": "offers",
      "attributes": {
        "offer-receiver-id": 2,
        "offer-receiver-username": "spiderman",
        "offer-receiver-avatar-url": "/system/users/avatars/original/missing.png",
        "offer-sender-id": 3,
        "offer-sender-username": "Hannibal",
        "offer-sender-avatar-url": "/system/users/avatars/000/000/003/original/avatar.jpg?1562578009",
        "previous-offer-id": 0,
        "requested-proposed-transactions": {
          "data": [
            {
              "id": "7",
              "type": "proposed-issuances",
              "attributes": {
                "offer-id": 7,
                "source-currency-id": 4,
                "source-currency-name": "spiderman pizza dollars",
                "source-currency-icon-url": "/system/currencies/icons/missing.png",
                "source-currency-burn-rate": 420,
                "source-currency-daily-burn-rate": "0.000117548",
                "source-currency-store-count": 3,
                "currency-issuer-id": 2,
                "currency-issuer-username": "spiderman",
                "currency-sender-public-holding-id": 54,
                "currency-sender-public-holding-amount-atomic": 3200000000000,
                "amount-atomic": 50000000000,
                "products": {
                  "data": [
                    {
                      "id": "52",
                      "type": "products",
                      "attributes": {
                        "sub-category-id": 20,
                        "sub-category-name": "kid's clothing",
                        "currency-id": 4,
                        "currency-name": "spiderman pizza dollars",
                        "currency-icon-url": "/system/currencies/icons/missing.png",
                        "issuer-public-currency-holding-id": 54,
                        "days-to-cancellation": null,
                        "minutes-to-cancellation": null,
                        "store-id": 29,
                        "store-name": "Spiderman store",
                        "product-name": "spidermask",
                        "product-description": "a spiderman mask",
                        "price-cents": 200,
                        "active": true,
                        "continued": true,
                        "last-activated-at": "2019-07-29T17:07:27.574-07:00",
                        "created-at": "2019-07-29T17:07:27.574-07:00",
                        "updated-at": "2019-07-29T17:07:27.574-07:00",
                        "get-image-url": "/system/products/images/original/missing.png"
                      }
                    }
                  ]
                },
                "active": false,
                "created-at": "2019-07-21T18:29:36.825-07:00",
                "updated-at": "2019-07-21T18:30:26.915-07:00"
              }
            }
          ]
        },
        "offered-proposed-transactions": {
          "data": [
            {
              "id": "7",
              "type": "proposed-transfers",
              "attributes": {
                "offer-id": 7,
                "source-currency-holding-id": 2,
                "source-currency-id": 1,
                "source-currency-name": "Micro Asteroid bucks",
                "source-currency-icon-url": "/system/currencies/icons/missing.png",
                "source-currency-burn-rate": 450,
                "source-currency-daily-burn-rate": "0.00012614",
                "source-currency-store-count": 2,
                "currency-sender-id": 3,
                "currency-sender-username": "Hannibal",
                "currency-sender-public-holding-amount-atomic": 3599957849922,
                "amount-atomic": 50000000000,
                "products": {
                  "data": [
                    {
                      "id": "51",
                      "type": "products",
                      "attributes": {
                        "sub-category-id": 12,
                        "sub-category-name": "computer accessories",
                        "currency-id": 1,
                        "currency-name": "Micro Asteroid bucks",
                        "currency-icon-url": "/system/currencies/icons/missing.png",
                        "issuer-public-currency-holding-id": 2,
                        "days-to-cancellation": null,
                        "minutes-to-cancellation": null,
                        "store-id": 28,
                        "store-name": "Moon Store",
                        "product-name": "Lunar solar panels",
                        "product-description": "solar panels designed to be installed on the moon",
                        "price-cents": 100000,
                        "active": true,
                        "continued": true,
                        "last-activated-at": "2019-07-29T16:56:30.169-07:00",
                        "created-at": "2019-07-29T16:56:30.169-07:00",
                        "updated-at": "2019-07-29T16:56:30.169-07:00",
                        "get-image-url": "/system/products/images/original/missing.png"
                      }
                    },
                    {
                      "id": "40",
                      "type": "products",
                      "attributes": {
                        "sub-category-id": 15,
                        "sub-category-name": "audio equipment",
                        "currency-id": 1,
                        "currency-name": "Micro Asteroid bucks",
                        "currency-icon-url": "/system/currencies/icons/missing.png",
                        "issuer-public-currency-holding-id": 2,
                        "days-to-cancellation": null,
                        "minutes-to-cancellation": null,
                        "store-id": 1,
                        "store-name": "Asteroid Industries",
                        "product-name": "goliath rocket 2",
                        "product-description": "second version of rocket for reaching the moon",
                        "price-cents": 1000000,
                        "active": true,
                        "continued": true,
                        "last-activated-at": "2019-07-26T04:57:32.173-07:00",
                        "created-at": "2019-07-26T04:57:32.173-07:00",
                        "updated-at": "2019-07-26T04:57:32.173-07:00",
                        "get-image-url": "/system/products/images/original/missing.png"
                      }
                    },
                    {
                      "id": "39",
                      "type": "products",
                      "attributes": {
                        "sub-category-id": 15,
                        "sub-category-name": "audio equipment",
                        "currency-id": 1,
                        "currency-name": "Micro Asteroid bucks",
                        "currency-icon-url": "/system/currencies/icons/missing.png",
                        "issuer-public-currency-holding-id": 2,
                        "days-to-cancellation": null,
                        "minutes-to-cancellation": null,
                        "store-id": 1,
                        "store-name": "Asteroid Industries",
                        "product-name": "goliath rocket",
                        "product-description": "rocket for reaching the moon",
                        "price-cents": 1000000,
                        "active": true,
                        "continued": true,
                        "last-activated-at": "2019-07-26T04:51:29.353-07:00",
                        "created-at": "2019-07-26T04:51:29.353-07:00",
                        "updated-at": "2019-07-26T04:51:29.353-07:00",
                        "get-image-url": "/system/products/images/original/missing.png"
                      }
                    }
                  ]
                },
                "active": false,
                "created-at": "2019-07-21T18:29:36.824-07:00",
                "updated-at": "2019-07-21T18:30:26.912-07:00"
              }
            }
          ]
        },
        "offer-type": 0,
        "raw-offer-type": 0,
        "active": false,
        "self-cancellation": false,
        "created-at": "2019-07-21T18:29:36.808-07:00",
        "updated-at": "2019-07-21T18:30:26.909-07:00"
      }
    }
  ],
  "links": {
    "self": "https://api.mycurrency.com/users/3/offers?index_type=offer_chain&offer_id=10",
    "first": "https://api.mycurrency.com/users/3/offers?index_type=offer_chain&offer_id=10&page=1&per_page=25",
    "prev": null,
    "next": null,
    "last": "https://api.mycurrency.com/users/3/offers?index_type=offer_chain&offer_id=10&page=1&per_page=25"
  },
  "meta": {
    "pagination": {
      "per-page": null,
      "total-pages": "1",
      "total-count": "4"
    }
  }
}
```

This endpoint retrieves a user's offers. There are five different offer lists that can be returned, depending on what argument is passed to the endpoint.

### HTTP Request

`GET https://api.mycurrency.com/users/<USER-ID>/offers?index_type={}`

<aside class="notice">
Authentication: the request requires the OAuth access-token associated with the User referenced by the ID 
</aside>

### ARGUMENTS

Parameter | Type | Required | Description
--------- | ------- | ------- | -----------
user_id | integer | yes | The ID of the user creating the offer, provided in URL path
index_type | string | yes | one of five index_types determining which type of list of offers is returned
offer_id | integer | required if the :index_type value is "offer_chain" | the ID of the offer at the head of the chain of offers returned

### INDEX TYPES

Value | Description
--------- | -----------
all_active_offers | returns active received and sent offers/counter-offers associated with user
received_active_offers | returns only active received offers/counter-offers associated with user
offer_chain_ending | returns all offers that ended offer chains (offer rejections, acceptances or offers that were self_cancelled) associated with user
head_offers | returns all offers that are the last in their offer chain associated with user
offer_chain | returns the chain of offers associated with head offer (the last offer in an offer chain) referenced by :offer_id associated with user

### RESPONSE

### Offer

Parameter | Description
--------- | -----------
id | The ID of the offer
offer-receiver-id | The ID of the user that received the offer
offer-receiver-username | The username of the user that received the offer
offer-receiver-avatar-url | The URL of the avatar of the user that received the offer
offer-sender-id | The ID of the user that made the offer
offer-sender-username | The username of the user that made the offer
offer-sender-avatar-url | The URL of the avatar of the user that made the offer
previous-offer-id | The ID of the offer that is being counter-offered. If the first offer of an offer-chain, the value will be 0
requested-proposed-transactions | An array of proposed transfers and proposed issuances being requested from the offer receiver
offered-proposed-transactions | An array of proposed transfers and proposed issuances being offered by the offer sender
offer-type | 0 is the offer that starts an offer chain, 1 is a counter-offer, 2 is an offer rejection, 3 is an offer acceptance, and 4 is a new offer or counter-offer with a self-cancellation value of true
raw-offer-type | The offer type value in the database. 0 is the offer that starts an offer chain, 1 is a counter-offer, 2 is an offer rejection, and 3 is an offer acceptance
active | Whether the offer is still active and can be countered or accepted/rejected
proposed-transfers | The proposed_transfers included in the offer
proposed-issuances | The proposed_issuances included in the offer
self-cancellation | Whether the offer sender has cancelled the offer by disactivating their user account
created-at | The time and date when the offer was created
updated-at | The time and date when the offer was last updated

### Proposed Transfers

Parameter | Description
--------- | -----------
id | The ID of the proposed transfer
offer-id | The ID of the offer that the proposed transfer is associated with
source-currency-holding-id | The ID of the public currency holding from which the proposed transfer would be sent
source-currency-id | The ID of the currency that is proposed to be transferred
source-currency-name | The name of the currency that is proposed to be transferred
source-currency-icon-url | The URL of the icon of the currency that is proposed to be transferred
source-currency-burn-rate | The burn rate of the currency that is proposed to be transferred
source-currency-daily-burn-rate | The daily burn rate of the currency that is proposed to be transferred
source-currency-store-count | The number of stores associated with the currency that is proposed to be transferred
currency-sender-id | The ID of the user that would send the proposed transfer
currency-sender-username | The username of the user that would send the proposed transfer
currency-sender-public-holding-amount-atomic | The amount of currency in the public holding that the transfer would be sent from, in atomic units (each whole unit is composed of 10^10 atomic units)
amount-atomic | The amount of currency that is proposed to be transferred, in atomic units (each whole unit is composed of 10^10 atomic units)
active | Whether the proposed transfer is still valid or not
products | The three most recently updated products associated with the currency of the proposed_transfer
created-at | The time and date when the proposed transfer was created
updated-at | The time and date when the proposed transfer was last updated

### Proposed Issuances

Parameter | Description
--------- | -----------
id | The ID of the proposed issuance
offer-id | The ID of the offer that the proposed issuance is associated with
source-currency-id | The ID of the currency that is proposed to be issued
source-currency-name | The name of the currency that is proposed to be issued
source-currency-icon-url | The URL of the icon of the currency that is proposed to be transferred
source-currency-burn-rate | The burn rate of the currency that is proposed to be transferred
source-currency-daily-burn-rate | The daily burn rate of the currency that is proposed to be transferred
source-currency-store-count | The number of stores associated with the currency that is proposed to be transferred
currency-issuer-id | The ID of the user that would issue the proposed issuance
currency-issuer-username | The username of the user that would issue the proposed issuance
currency-sender-public-holding-id | The ID of currency in the proposed issuer's public holding of the currency that would be issued
currency-sender-public-holding-amount-atomic | The amount of currency in the proposed issuer's public holding of the currency that would be issued, in atomic units (each whole unit is composed of 10^10 atomic units)
amount-atomic | The amount of currency that is proposed to be issued, in atomic units (each whole unit is composed of 10^10 atomic units)
active | Whether the proposed issuance is still valid or not
products | The three most recently updated products associated with the currency of the proposed_issuance
created-at | The time and date when the proposed issuance was created
updated-at | The time and date when the proposed issuance was last updated

### Products

Parameter | Description
--------- | -----------
id | The ID of the product
sub-category-id | The sub category that the product belongs to
sub-category-name | The name of the sub category that the product belongs to
currency-id | The ID of the currency that the product can be redeemed by
currency-name | The name of the currency that the product can be redeemed by
currency-icon-url | The URL of the icon of the currency that the product can be redeemed by 
days-to-cancellation | How many days until the product's product-discontinual is activated and the product is cancelled. A NULL value if the product has no product discontinual
store-id | The ID of the store where the product is sold
store-name | The name of the store where the product is sold
product-name | The name of the product
product-description | The description of the product
price-cents | The price of the product by multiple of 100, and denominated in the currency of the store where the product is sold
active | Whether the product is active or not
continued | Whether the product is continued or not. Discontinued products cannot be recontinued
last-activated-at | The time and date when the product was last activated
created-at | The time and date when the product was created
updated-at | The time and date when the product was last updated
get-image-url | The URL at which the product image picture can be found

## Create Offer

```shell
curl https://api.mycurrency.com/users/2/offers -d '{ "offer": {"offer_sender_id": "2", "offer_receiver_id": "3", "offer_type": "0", "proposed_requesting_attributes": [{"currency_id": "75", "amount_atomic": "100000000000"}], "proposed_offering_attributes": [{"currency_id": "4", "amount_atomic": "50000000000"}] }}' \
  -H 'Authorization: Bearer j47lbjj8r9n5yy8mup6cxqc8h70yvhnilm0g84kg0raqckus0k1koj9f75ao' \
  -H 'Accept: application/json' -H 'Content-Type: application/json'
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "id": "42",
    "type": "offers",
    "attributes": {
      "offer-receiver-id": 3,
      "offer-receiver-username": "Hannibal",
      "offer-receiver-avatar-url": "/system/users/avatars/000/000/003/original/avatar.jpg?1562578009",
      "offer-sender-id": 2,
      "offer-sender-username": "spiderman",
      "offer-sender-avatar-url": "/system/users/avatars/original/missing.png",
      "previous-offer-id": 0,
      "requested-proposed-transactions": {
        "data": [
          {
            "id": "45",
            "type": "proposed-issuances",
            "attributes": {
              "offer-id": 42,
              "source-currency-id": 75,
              "source-currency-name": "Saint Patricks Day Money",
              "source-currency-icon-url": "/system/currencies/icons/000/000/075/original/currency.jpg?1563341979",
              "source-currency-burn-rate": 1000,
              "source-currency-daily-burn-rate": "0.000288618",
              "source-currency-store-count": 0,
              "currency-issuer-id": 3,
              "currency-issuer-username": "Hannibal",
              "amount-atomic": 100000000000,
              "products": {
                "data": []
              },
              "active": true,
              "created-at": "2019-08-03T16:17:13.346-07:00",
              "updated-at": "2019-08-03T16:17:13.346-07:00"
            }
          }
        ]
      },
      "offered-proposed-transactions": {
        "data": [
          {
            "id": "48",
            "type": "proposed-transfers",
            "attributes": {
              "offer-id": 42,
              "source-currency-holding-id": 54,
              "source-currency-id": 4,
              "source-currency-name": "spiderman pizza dollars",
              "source-currency-icon-url": "/system/currencies/icons/missing.png",
              "source-currency-burn-rate": 420,
              "source-currency-daily-burn-rate": "0.000117548",
              "source-currency-store-count": 3,
              "currency-sender-id": 2,
              "currency-sender-username": "spiderman",
              "currency-sender-public-holding-amount-atomic": 3200000000000,
              "amount-atomic": 50000000000,
              "products": {
                "data": [
                  {
                    "id": "52",
                    "type": "products",
                    "attributes": {
                      "sub-category-id": 20,
                      "sub-category-name": "kid's clothing",
                      "currency-id": 4,
                      "currency-name": "spiderman pizza dollars",
                      "currency-icon-url": "/system/currencies/icons/missing.png",
                      "issuer-public-currency-holding-id": 54,
                      "days-to-cancellation": null,
                      "minutes-to-cancellation": null,
                      "store-id": 29,
                      "store-name": "Spiderman store",
                      "product-name": "spidermask",
                      "product-description": "a spiderman mask",
                      "price-cents": 200,
                      "active": true,
                      "continued": true,
                      "last-activated-at": "2019-07-29T17:07:27.574-07:00",
                      "created-at": "2019-07-29T17:07:27.574-07:00",
                      "updated-at": "2019-07-29T17:07:27.574-07:00",
                      "get-image-url": "/system/products/images/original/missing.png"
                    }
                  }
                ]
              },
              "active": true,
              "created-at": "2019-08-03T16:17:13.345-07:00",
              "updated-at": "2019-08-03T16:17:13.345-07:00"
            }
          }
        ]
      },
      "offer-type": 0,
      "raw-offer-type": 0,
      "active": true,
      "self-cancellation": false,
      "created-at": "2019-08-03T16:17:13.293-07:00",
      "updated-at": "2019-08-03T16:17:13.293-07:00"
    }
  }
}
```

Creates an offer. For each proposed requesting attribute hash, the server will attempt to create a proposed transfer or proposed issuance from the offer receiver, while for each proposed offering attribute hash, the server will attempt to create a proposed transfer or proposed issuance from the offer sender. The server will check if the proposed sender has enough units of currency in the holding of the specified currency, and if so, create a proposed transfer. If not, the server will check if the proposed sender is also the issuer of the specified currency, and if so, then it will create a proposed issuance from the proposed sender. If the proposed sender neither has a public holding of the specified currency, not is the issuer of the specified currency, then no proposed transfer or proposed issuance is created from the proposed offering/requesting attribute hash.

### HTTP Request

`GET https://api.mycurrency.com/users/<USER-ID>/offers`

<aside class="notice">
Authentication: the request requires the OAuth access-token associated with the User referenced by the ID 
</aside>

### OFFER ARGUMENTS

Parameter | Type | Required | Description
--------- | ------- | ------- | -----------
user_id | integer | yes | The ID of the user creating the offer, provided in URL path
offer_sender_id | integer | required if offer starts an offer chain | The ID of the user sending the offer
offer_receiver_id | integer | required if offer starts an offer chain | The ID of the user receiving the offer
previous_offer_id | integer | required if offer is not starting an offer chain | The ID of the previous offer in the offer chain
offer_type | integer | yes | One of four offer types: first offer, counter-offer, offer rejection and offer acceptance 

### OFFER TYPES

Value | Description
--------- | -----------
0 | An offer that starts a new offer chain
1 | A counter offer
2 | An offer rejection
3 | An offer acceptance

### PROPOSED REQUESTING ATTRIBUTES

Parameter | Type | Required | Description
--------- | ------- | ------- | -----------
currency_id | integer | yes | The ID of the currency that is being requested 
amount_atomic | integer | yes | The amount of currency that is being requested, in atomic units (each whole unit is composed of 10^10 atomic units)

### PROPOSED OFFERING ATTRIBUTES

Parameter | Type | Required | Description
--------- | ------- | ------- | -----------
currency_id | integer | yes | The ID of the currency that is being offered 
amount_atomic | integer | yes | The amount of currency that is being offered, in atomic units (each whole unit is composed of 10^10 atomic units)

### RESPONSE

### Offer

Parameter | Description
--------- | -----------
id | The ID of the offer
offer-receiver-id | The ID of the user that received the offer
offer-receiver-username | The username of the user that received the offer
offer-receiver-avatar-url | The URL of the avatar of the user that received the offer
offer-sender-id | The ID of the user that made the offer
offer-sender-username | The username of the user that made the offer
offer-sender-avatar-url | The URL of the avatar of the user that made the offer
previous-offer-id | The ID of the offer that is being counter-offered. If the first offer of an offer-chain, the value will be 0
requested-proposed-transactions | An array of proposed transfers and proposed issuances being requested from the offer receiver
offered-proposed-transactions | An array of proposed transfers and proposed issuances being offered by the offer sender
offer-type | 0 is the offer that starts an offer chain, 1 is a counter-offer, 2 is an offer rejection, 3 is an offer acceptance, and 4 is a new offer or counter-offer with a self-cancellation value of true
raw-offer-type | The offer type value in the database. 0 is the offer that starts an offer chain, 1 is a counter-offer, 2 is an offer rejection, and 3 is an offer acceptance
active | Whether the offer is still active and can be countered or accepted/rejected
proposed-transfers | The proposed_transfers included in the offer
proposed-issuances | The proposed_issuances included in the offer
self-cancellation | Whether the offer sender has cancelled the offer by disactivating their user account
created-at | The time and date when the offer was created
updated-at | The time and date when the offer was last updated

### Proposed Transfers

Parameter | Description
--------- | -----------
id | The ID of the proposed transfer
offer-id | The ID of the offer that the proposed transfer is associated with
source-currency-holding-id | The ID of the public currency holding from which the proposed transfer would be sent
source-currency-id | The ID of the currency that is proposed to be transferred
source-currency-name | The name of the currency that is proposed to be transferred
source-currency-icon-url | The URL of the icon of the currency that is proposed to be transferred
source-currency-burn-rate | The burn rate of the currency that is proposed to be transferred
source-currency-daily-burn-rate | The daily burn rate of the currency that is proposed to be transferred
source-currency-store-count | The number of stores associated with the currency that is proposed to be transferred
currency-sender-id | The ID of the user that would send the proposed transfer
currency-sender-username | The username of the user that would send the proposed transfer
currency-sender-public-holding-amount-atomic | The amount of currency in the public holding that the transfer would be sent from, in atomic units (each whole unit is composed of 10^10 atomic units)
amount-atomic | The amount of currency that is proposed to be transferred, in atomic units (each whole unit is composed of 10^10 atomic units)
active | Whether the proposed transfer is still valid or not
products | The three most recently updated products associated with the currency of the proposed_transfer
created-at | The time and date when the proposed transfer was created
updated-at | The time and date when the proposed transfer was last updated

### Proposed Issuances

Parameter | Description
--------- | -----------
id | The ID of the proposed issuance
offer-id | The ID of the offer that the proposed issuance is associated with
source-currency-id | The ID of the currency that is proposed to be issued
source-currency-name | The name of the currency that is proposed to be issued
source-currency-icon-url | The URL of the icon of the currency that is proposed to be transferred
source-currency-burn-rate | The burn rate of the currency that is proposed to be transferred
source-currency-daily-burn-rate | The daily burn rate of the currency that is proposed to be transferred
source-currency-store-count | The number of stores associated with the currency that is proposed to be transferred
currency-issuer-id | The ID of the user that would issue the proposed issuance
currency-issuer-username | The username of the user that would issue the proposed issuance
currency-sender-public-holding-id | The ID of currency in the proposed issuer's public holding of the currency that would be issued
currency-sender-public-holding-amount-atomic | The amount of currency in the proposed issuer's public holding of the currency that would be issued, in atomic units (each whole unit is composed of 10^10 atomic units)
amount-atomic | The amount of currency that is proposed to be issued, in atomic units (each whole unit is composed of 10^10 atomic units)
active | Whether the proposed issuance is still valid or not
products | The three most recently updated products associated with the currency of the proposed_issuance
created-at | The time and date when the proposed issuance was created
updated-at | The time and date when the proposed issuance was last updated

### Products

Parameter | Description
--------- | -----------
id | The ID of the product
sub-category-id | The sub category that the product belongs to
sub-category-name | The name of the sub category that the product belongs to
currency-id | The ID of the currency that the product can be redeemed by
currency-name | The name of the currency that the product can be redeemed by
currency-icon-url | The URL of the icon of the currency that the product can be redeemed by 
days-to-cancellation | How many days until the product's product-discontinual is activated and the product is cancelled. A NULL value if the product has no product discontinual
store-id | The ID of the store where the product is sold
store-name | The name of the store where the product is sold
product-name | The name of the product
product-description | The description of the product
price-cents | The price of the product by multiple of 100, and denominated in the currency of the store where the product is sold
active | Whether the product is active or not
continued | Whether the product is continued or not. Discontinued products cannot be recontinued
last-activated-at | The time and date when the product was last activated
created-at | The time and date when the product was created
updated-at | The time and date when the product was last updated
get-image-url | The URL at which the product image picture can be found

# Listing

## Get a Listing

```shell
curl 'https://api.mycurrency.com/listings/2' \
  -H 'Accept: application/json' -H 'Content-Type: application/json'
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "id": "2",
    "type": "listings",
    "attributes": {
      "user-id": 4,
      "username": "ScipioAfricanus",
      "currency-id": 4,
      "currency-name": "Pool coins",
      "amount-atomic": 50000000000,
      "cl-link": "https://vancouver.craigslist.ca/van/clt/6722934016.html",
      "cl-title": "For sale - 5 Pool coins",
      "offer-currency": true,
      "currency-icon-url": "/system/currencies/icons/000/000/004/original/currency.jpg?1569902813",
      "user-avatar-url": "/system/users/avatars/000/000/005/original/portrait.jpg?1559144410",
      "currency-issuer-user-id": 4,
      "currency-issuer-user-username": "ScipioAfricanus",
      "currency-issuer-user-avatar-url": "/system/users/avatars/000/000/005/original/portrait.jpg?1559144410",
      "created-at": "2018-10-13T22:37:59.492-07:00",
      "updated-at": "2018-10-13T22:37:59.492-07:00"
    }
  }
}
```

This endpoint retrieves a particular listing and its basic public information by ID.

### HTTP Request

`GET https://api.mycurrency.com/listings/<ID>`

<aside class="notice">
Authentication: not required
</aside>

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the listing
user-id | The ID of the user account that created the listing
username | The username of the user account that created the listing
currency-id | The ID of the currency that the listing is offering
currency-name | The name of the currency that the listing is offering
amount-atomic | The amount of currency being offered, in atomic units (each whole unit is composed of 10^10 atomic units)
cl-link | The link to the Craigslist post containing the description of the listing
cl-title | The title of the Craiglist post containing the description of the listing. Must match the cl-title value
offer-currency | Whether the listing is offering currency. If true, the user must have an adequate amount of currency in the source currency holding they designate to cover the amount offered
currency-icon-url | The URL for the icon of the currency being offered
user-avatar-url | The URL of the avatar of the user that created the listing
currency-issuer-user-id | The ID of the user that issues the currency being offered
currency-issuer-user-username | The username of the user that issues the currency being offered
currency-issuer-user-avatar-url | The URL of the avatar of the user that issues the currency being offered
created-at | The time and date when the listing was created
updated-at | The time and date when the listing was last updated

## Get a Listing with Authorization

```shell
curl 'https://api.mycurrency.com/users/3/authorized_listings/5' \
  -H 'Accept: application/json' -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer j47lbjj8r9n5yy8mup6cxqc8h70yvhnilm0g84kg0raqckus0k1koj9f75ao'
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "id": "5",
    "type": "listings",
    "attributes": {
      "user-id": 3,
      "username": "Hannibal",
      "currency-id": 3,
      "currency-name": "macaroon dollars",
      "amount-atomic": 50000000000,
      "cl-link": "https://vancouver.craigslist.ca/van/clt/6722960191.html",
      "cl-title": "Looking for trade, offering - 5 macaroon dollars",
      "offer-currency": true,
      "currency-icon-url": "/system/currencies/icons/000/000/003/original/currency.jpg?1561113125,
      "user-avatar-url": "/system/users/avatars/000/000/004/original/1.jpg?1559736060",
      "currency-issuer-user-id": 3,
      "currency-issuer-user-username": "Hannibal",
      "currency-issuer-user-avatar-url": "/system/users/avatars/000/000/004/original/1.jpg?1559736060",
      "created-at": "2018-10-14T03:07:51.191-07:00",
      "updated-at": "2018-10-14T03:07:51.191-07:00",
      "currency-holding-id": 3,
      "currency-holding-type": "PrivateCurrencyHolding",
      "active": true,
      "canceled": false
    }
  }
}
```

This endpoint retrieves the full details of a particular listing. 

### HTTP Request

`GET https://api.mycurrency.com/users/<USER-ID>/authorized_listings/<ID>`

<aside class="notice">
Authentication: the request requires the OAuth access-token associated with the User referenced by the ID 
</aside>

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the listing
user-id | The ID of the user account that created the listing
username | The username of the user account that created the listing
currency-id | The ID of the currency that the listing is offering
currency-name | The name of the currency that the listing is offering
amount-atomic | The amount of currency being offered, in atomic units (each whole unit is composed of 10^10 atomic units)
cl-link | The link to the Craigslist post containing the description of the listing
cl-title | The title of the Craiglist post containing the description of the listing. Must match the cl-title value
offer-currency | Whether the listing is offering currency. If true, the user must have an adequate amount of currency in the source currency holding they designate to cover the amount offered
currency-icon-url | The URL for the icon of the currency being offered
user-avatar-url | The URL of the avatar of the user that created the listing
currency-issuer-user-id | The ID of the user that issues the currency being offered
currency-issuer-user-username | The username of the user that issues the currency being offered
currency-issuer-user-avatar-url | The URL of the avatar of the user that issues the currency being offered
created-at | The time and date when the listing was created
updated-at | The time and date when the listing was last updated
currency-holding-id | The ID of the public or private currency holding that the currency being offered is held in
currency-holding-type | Whether the currency holding that the offered currency is held in is a "PublicCurrencyHolding" or a "PrivateCurrencyHolding"
active | Whether the listing is active or not. Inactive listings can only be activated if the listing has not been cancelled.
canceled | Whether the listing has been canceled or not. Cancelled listings cannot be uncancelled or reactivated.

## List All Listings

```shell
curl "https://api.mycurrency.com/listings" -H 'Host: api.mycurrency.com' \
  -H 'Accept: application/json' -H 'Content-Type: application/json'
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": "2",
      "type": "listings",
      "attributes": {
        "user-id": 4,
        "username": "ScipioAfricanus",
        "currency-id": 4,
        "currency-name": "Pool coins",
        "amount-atomic": 50000000000,
        "cl-link": "https://vancouver.craigslist.ca/van/clt/6722934016.html",
        "cl-title": "For sale - 5 Pool coins",
        "offer-currency": true,
        "currency-icon-url": "/system/currencies/icons/000/000/004/original/currency.jpg?1569902813",
        "user-avatar-url": "/system/users/avatars/000/000/005/original/portrait.jpg?1559144410",
        "currency-issuer-user-id": 4,
        "currency-issuer-user-username": "ScipioAfricanus",
        "currency-issuer-user-avatar-url": "/system/users/avatars/000/000/005/original/portrait.jpg?1559144410",
        "created-at": "2018-10-13T22:37:59.492-07:00",
        "updated-at": "2018-10-13T22:37:59.492-07:00"
      }
    },
    {
      "id": "3",
      "type": "listings",
      "attributes": {
        "user-id": 4,
        "username": "ScipioAfricanus",
        "currency-id": 4,
        "currency-name": "Pool coins",
        "amount-atomic": 50000000000,
        "cl-link": "https://vancouver.craigslist.ca/van/clt/6722959469.html",
        "cl-title": "Selling - 5 Pool coins",
        "offer-currency": true,
        "currency-icon-url": "/system/currencies/icons/000/000/004/original/currency.jpg?1569902813",
        "user-avatar-url": "/system/users/avatars/000/000/005/original/portrait.jpg?1559144410",
        "currency-issuer-user-id": 4,
        "currency-issuer-user-username": "ScipioAfricanus",
        "currency-issuer-user-avatar-url": "/system/users/avatars/000/000/005/original/portrait.jpg?1559144410",
        "created-at": "2018-10-14T02:56:42.738-07:00",
        "updated-at": "2018-10-14T02:56:42.738-07:00"
      }
    },
    {
      "id": "4",
      "type": "listings",
      "attributes": {
        "user-id": 4,
        "username": "ScipioAfricanus",
        "currency-id": 5,
        "currency-name": "Freds Fishing Supplies dollars",
        "amount-atomic": 50000000000,
        "cl-link": "https://vancouver.craigslist.ca/van/clt/6722959714.html",
        "cl-title": "Offering - 5 Freds Fishing Supplies dollars",
        "offer-currency": true,
        "currency-icon-url": "/icons/original/missing.png",
        "user-avatar-url": "/system/users/avatars/000/000/005/original/portrait.jpg?1559144410",
        "currency-issuer-user-id": 4,
        "currency-issuer-user-username": "ScipioAfricanus",
        "currency-issuer-user-avatar-url": "/system/users/avatars/000/000/005/original/portrait.jpg?1559144410",
        "created-at": "2018-10-14T02:56:57.624-07:00",
        "updated-at": "2018-10-14T02:56:57.624-07:00"
      }
    },
    {
      "id": "5",
      "type": "listings",
      "attributes": {
        "user-id": 3,
        "username": "Hannibal",
        "currency-id": 3,
        "currency-name": "macaroon dollars",
        "amount-atomic": 50000000000,
        "cl-link": "https://vancouver.craigslist.ca/van/clt/6722960191.html",
        "cl-title": "Looking for trade, offering - 5 macaroon dollars",
        "offer-currency": true,
        "currency-icon-url": "/system/currencies/icons/000/000/003/original/currency.jpg?1561113125,
        "user-avatar-url": "/system/users/avatars/000/000/004/original/1.jpg?1559736060",
        "currency-issuer-user-id": 3,
        "currency-issuer-user-username": "Hannibal",
        "currency-issuer-user-avatar-url": "/system/users/avatars/000/000/004/original/1.jpg?1559736060",
        "created-at": "2018-10-14T03:07:51.191-07:00",
        "updated-at": "2018-10-14T03:07:51.191-07:00"
      }
    },
    {
      "id": "6",
      "type": "listings",
      "attributes": {
        "user-id": 3,
        "username": "Hannibal",
        "currency-id": 4,
        "currency-name": "Pool coins",
        "amount-atomic": 50000000000,
        "cl-link": "https://vancouver.craigslist.ca/van/clt/6722960432.html",
        "cl-title": "Trading - 5 Pool coins",
        "offer-currency": true,
        "currency-icon-url": "/system/currencies/icons/000/000/004/original/currency.jpg?1569902813",
        "user-avatar-url": "/system/users/avatars/000/000/004/original/1.jpg?1559736060",
        "currency-issuer-user-id": 4,
        "currency-issuer-user-username": "ScipioAfricanus",
        "currency-issuer-user-avatar-url": "/system/users/avatars/000/000/005/original/portrait.jpg?1559144410",
        "created-at": "2018-10-14T03:13:29.210-07:00",
        "updated-at": "2018-10-14T03:13:29.210-07:00"
      }
    }
  ],
  "links": {
    "self": "https://api.mycurrency.com/listings?",
    "first": "https://api.mycurrency.com/listings?page=1&per_page=25",
    "prev": null,
    "next": null,
    "last": "https://api.mycurrency.com/listings?page=1&per_page=25"
  },
  "meta": {
    "pagination": {
      "per-page": null,
      "total-pages": "1",
      "total-count": "5"
    }
  }
}
```

This endpoint retrieves all active listings and their basic public information.

### HTTP Request

`GET https://api.mycurrency.com/listings`

<aside class="notice">
Authentication: not required
</aside>

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the listing
user-id | The ID of the user account that created the listing
username | The username of the user account that created the listing
currency-id | The ID of the currency that the listing is offering
currency-name | The name of the currency that the listing is offering
amount-atomic | The amount of currency being offered, in atomic units (each whole unit is composed of 10^10 atomic units)
cl-link | The link to the Craigslist post containing the description of the listing
cl-title | The title of the Craiglist post containing the description of the listing. Must match the cl-title value
offer-currency | Whether the listing is offering currency. If true, the user must have an adequate amount of currency in the source currency holding they designate to cover the amount offered
currency-icon-url | The URL for the icon of the currency being offered
user-avatar-url | The URL of the avatar of the user that created the listing
currency-issuer-user-id | The ID of the user that issues the currency being offered
currency-issuer-user-username | The username of the user that issues the currency being offered
currency-issuer-user-avatar-url | The URL of the avatar of the user that issues the currency being offered
created-at | The time and date when the listing was created
updated-at | The time and date when the listing was last updated

## List User's Listings

```shell
curl "https://api.mycurrency.com/users/4/listings" -H 'Host: api.mycurrency.com' \
  -H 'Accept: application/json' -H 'Content-Type: application/json'
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": "2",
      "type": "listings",
      "attributes": {
        "user-id": 4,
        "username": "ScipioAfricanus",
        "currency-id": 4,
        "currency-name": "Pool coins",
        "amount-atomic": 50000000000,
        "cl-link": "https://vancouver.craigslist.ca/van/clt/6722934016.html",
        "cl-title": "For sale - 5 Pool coins",
        "offer-currency": true,
        "currency-icon-url": "/system/currencies/icons/000/000/004/original/currency.jpg?1569902813",
        "user-avatar-url": "/system/users/avatars/000/000/005/original/portrait.jpg?1559144410",
        "currency-issuer-user-id": 4,
        "currency-issuer-user-username": "ScipioAfricanus",
        "currency-issuer-user-avatar-url": "/system/users/avatars/000/000/005/original/portrait.jpg?1559144410",
        "created-at": "2018-10-13T22:37:59.492-07:00",
        "updated-at": "2018-10-13T22:37:59.492-07:00"
      }
    },
    {
      "id": "3",
      "type": "listings",
      "attributes": {
        "user-id": 4,
        "username": "ScipioAfricanus",
        "currency-id": 4,
        "currency-name": "Pool coins",
        "amount-atomic": 50000000000,
        "cl-link": "https://vancouver.craigslist.ca/van/clt/6722959469.html",
        "cl-title": "Selling - 5 Pool coins",
        "offer-currency": true,
        "currency-icon-url": "/system/currencies/icons/000/000/004/original/currency.jpg?1569902813",
        "user-avatar-url": "/system/users/avatars/000/000/005/original/portrait.jpg?1559144410",
        "currency-issuer-user-id": 4,
        "currency-issuer-user-username": "ScipioAfricanus",
        "currency-issuer-user-avatar-url": "/system/users/avatars/000/000/005/original/portrait.jpg?1559144410",
        "created-at": "2018-10-14T02:56:42.738-07:00",
        "updated-at": "2018-10-14T02:56:42.738-07:00"
      }
    },
    {
      "id": "4",
      "type": "listings",
      "attributes": {
        "user-id": 4,
        "username": "ScipioAfricanus",
        "currency-id": 5,
        "currency-name": "Freds Fishing Supplies dollars",
        "amount-atomic": 50000000000,
        "cl-link": "https://vancouver.craigslist.ca/van/clt/6722959714.html",
        "cl-title": "Offering - 5 Freds Fishing Supplies dollars",
        "offer-currency": true,
        "currency-icon-url": "/icons/original/missing.png",
        "user-avatar-url": "/system/users/avatars/000/000/005/original/portrait.jpg?1559144410",
        "currency-issuer-user-id": 4,
        "currency-issuer-user-username": "ScipioAfricanus",
        "currency-issuer-user-avatar-url": "/system/users/avatars/000/000/005/original/portrait.jpg?1559144410",
        "created-at": "2018-10-14T02:56:57.624-07:00",
        "updated-at": "2018-10-14T02:56:57.624-07:00"
      }
    }
  ],
  "links": {
    "self": "https://api.mycurrency.com/users/4/listings?",
    "first": "https://api.mycurrency.com/users/4/listings?page=1&per_page=25",
    "prev": null,
    "next": null,
    "last": "https://api.mycurrency.com/users/4/listings?page=1&per_page=25"
  },
  "meta": {
    "pagination": {
      "per-page": null,
      "total-pages": "1",
      "total-count": "3"
    }
  }
}
```

This endpoint retrieves all active listings created by the specified user and outputs their basic public information.

### HTTP Request

`GET https://api.mycurrency.com/users/<USER-ID>/listings`

<aside class="notice">
Authentication: not required
</aside>

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the listing
user-id | The ID of the user account that created the listing
username | The username of the user account that created the listing
currency-id | The ID of the currency that the listing is offering
currency-name | The name of the currency that the listing is offering
amount-atomic | The amount of currency being offered, in atomic units (each whole unit is composed of 10^10 atomic units)
cl-link | The link to the Craigslist post containing the description of the listing
cl-title | The title of the Craiglist post containing the description of the listing. Must match the cl-title value
offer-currency | Whether the listing is offering currency. If true, the user must have an adequate amount of currency in the source currency holding they designate to cover the amount offered
currency-icon-url | The URL for the icon of the currency being offered
user-avatar-url | The URL of the avatar of the user that created the listing
currency-issuer-user-id | The ID of the user that issues the currency being offered
currency-issuer-user-username | The username of the user that issues the currency being offered
currency-issuer-user-avatar-url | The URL of the avatar of the user that issues the currency being offered
created-at | The time and date when the listing was created
updated-at | The time and date when the listing was last updated

## List Currency's Listings

```shell
curl "https://api.mycurrency.com/currencies/4/listings" -H 'Host: api.mycurrency.com' \
  -H 'Accept: application/json' -H 'Content-Type: application/json'
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": "2",
      "type": "listings",
      "attributes": {
        "user-id": 4,
        "username": "ScipioAfricanus",
        "currency-id": 4,
        "currency-name": "Pool coins",
        "amount-atomic": 50000000000,
        "cl-link": "https://vancouver.craigslist.ca/van/clt/6722934016.html",
        "cl-title": "For sale - 5 Pool coins",
        "offer-currency": true,
        "currency-icon-url": "/system/currencies/icons/000/000/004/original/currency.jpg?1569902813",
        "user-avatar-url": "/system/users/avatars/000/000/005/original/portrait.jpg?1559144410",
        "currency-issuer-user-id": 4,
        "currency-issuer-user-username": "ScipioAfricanus",
        "currency-issuer-user-avatar-url": "/system/users/avatars/000/000/005/original/portrait.jpg?1559144410",
        "created-at": "2018-10-13T22:37:59.492-07:00",
        "updated-at": "2018-10-13T22:37:59.492-07:00"
      }
    },
    {
      "id": "3",
      "type": "listings",
      "attributes": {
        "user-id": 4,
        "username": "ScipioAfricanus",
        "currency-id": 4,
        "currency-name": "Pool coins",
        "amount-atomic": 50000000000,
        "cl-link": "https://vancouver.craigslist.ca/van/clt/6722959469.html",
        "cl-title": "Selling - 5 Pool coins",
        "offer-currency": true,
        "currency-icon-url": "/system/currencies/icons/000/000/004/original/currency.jpg?1569902813",
        "user-avatar-url": "/system/users/avatars/000/000/005/original/portrait.jpg?1559144410",
        "currency-issuer-user-id": 4,
        "currency-issuer-user-username": "ScipioAfricanus",
        "currency-issuer-user-avatar-url": "/system/users/avatars/000/000/005/original/portrait.jpg?1559144410",
        "created-at": "2018-10-14T02:56:42.738-07:00",
        "updated-at": "2018-10-14T02:56:42.738-07:00"
      }
    },
    {
      "id": "6",
      "type": "listings",
      "attributes": {
        "user-id": 3,
        "username": "Hannibal",
        "currency-id": 4,
        "currency-name": "Pool coins",
        "amount-atomic": 50000000000,
        "cl-link": "https://vancouver.craigslist.ca/van/clt/6722960432.html",
        "cl-title": "Trading - 5 Pool coins",
        "offer-currency": true,
        "currency-icon-url": "/system/currencies/icons/000/000/004/original/currency.jpg?1569902813",
        "user-avatar-url": "/system/users/avatars/000/000/004/original/1.jpg?1559736060",
        "currency-issuer-user-id": 4,
        "currency-issuer-user-username": "ScipioAfricanus",
        "currency-issuer-user-avatar-url": "/system/users/avatars/000/000/005/original/portrait.jpg?1559144410",
        "created-at": "2018-10-14T03:13:29.210-07:00",
        "updated-at": "2018-10-14T03:13:29.210-07:00"
      }
    }
  ],
  "links": {
    "self": "https://api.mycurrency.com/currencies/4/listings?",
    "first": "https://api.mycurrency.com/currencies/4/listings?page=1&per_page=25",
    "prev": null,
    "next": null,
    "last": "https://api.mycurrency.com/currencies/4/listings?page=1&per_page=25"
  },
  "meta": {
    "pagination": {
      "per-page": null,
      "total-pages": "1",
      "total-count": "3"
    }
  }
}
```

This endpoint retrieves all active listings where the specified currency is being offered and outputs their basic public information.

### HTTP Request

`GET https://api.mycurrency.com/currencies/<CURRENCY-ID>/listings`

<aside class="notice">
Authentication: not required
</aside>

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the listing
user-id | The ID of the user account that created the listing
username | The username of the user account that created the listing
currency-id | The ID of the currency that the listing is offering
currency-name | The name of the currency that the listing is offering
amount-atomic | The amount of currency being offered, in atomic units (each whole unit is composed of 10^10 atomic units)
cl-link | The link to the Craigslist post containing the description of the listing
cl-title | The title of the Craiglist post containing the description of the listing. Must match the cl-title value
offer-currency | Whether the listing is offering currency. If true, the user must have an adequate amount of currency in the source currency holding they designate to cover the amount offered
currency-icon-url | The URL for the icon of the currency being offered
user-avatar-url | The URL of the avatar of the user that created the listing
currency-issuer-user-id | The ID of the user that issues the currency being offered
currency-issuer-user-username | The username of the user that issues the currency being offered
currency-issuer-user-avatar-url | The URL of the avatar of the user that issues the currency being offered
created-at | The time and date when the listing was created
updated-at | The time and date when the listing was last updated

## List Sub Location's Listings

```shell
curl "https://api.mycurrency.com/sub_locations/1/listings" -H 'Host: api.mycurrency.com' \
  -H 'Accept: application/json' -H 'Content-Type: application/json'
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": "2",
      "type": "listings",
      "attributes": {
        "user-id": 4,
        "username": "ScipioAfricanus",
        "currency-id": 4,
        "currency-name": "Pool coins",
        "amount-atomic": 50000000000,
        "cl-link": "https://vancouver.craigslist.ca/van/clt/6722934016.html",
        "cl-title": "For sale - 5 Pool coins",
        "offer-currency": true,
        "currency-icon-url": "/system/currencies/icons/000/000/004/original/currency.jpg?1569902813",
        "user-avatar-url": "/system/users/avatars/000/000/005/original/portrait.jpg?1559144410",
        "currency-issuer-user-id": 4,
        "currency-issuer-user-username": "ScipioAfricanus",
        "currency-issuer-user-avatar-url": "/system/users/avatars/000/000/005/original/portrait.jpg?1559144410",
        "created-at": "2018-10-13T22:37:59.492-07:00",
        "updated-at": "2018-10-13T22:37:59.492-07:00"
      }
    },
    {
      "id": "3",
      "type": "listings",
      "attributes": {
        "user-id": 4,
        "username": "ScipioAfricanus",
        "currency-id": 4,
        "currency-name": "Pool coins",
        "amount-atomic": 50000000000,
        "cl-link": "https://vancouver.craigslist.ca/van/clt/6722959469.html",
        "cl-title": "Selling - 5 Pool coins",
        "offer-currency": true,
        "currency-icon-url": "/system/currencies/icons/000/000/004/original/currency.jpg?1569902813",
        "user-avatar-url": "/system/users/avatars/000/000/005/original/portrait.jpg?1559144410",
        "currency-issuer-user-id": 4,
        "currency-issuer-user-username": "ScipioAfricanus",
        "currency-issuer-user-avatar-url": "/system/users/avatars/000/000/005/original/portrait.jpg?1559144410",
        "created-at": "2018-10-14T02:56:42.738-07:00",
        "updated-at": "2018-10-14T02:56:42.738-07:00"
      }
    },
    {
      "id": "4",
      "type": "listings",
      "attributes": {
        "user-id": 4,
        "username": "ScipioAfricanus",
        "currency-id": 5,
        "currency-name": "Freds Fishing Supplies dollars",
        "amount-atomic": 50000000000,
        "cl-link": "https://vancouver.craigslist.ca/van/clt/6722959714.html",
        "cl-title": "Offering - 5 Freds Fishing Supplies dollars",
        "offer-currency": true,
        "currency-icon-url": "/icons/original/missing.png",
        "user-avatar-url": "/system/users/avatars/000/000/005/original/portrait.jpg?1559144410",
        "currency-issuer-user-id": 4,
        "currency-issuer-user-username": "ScipioAfricanus",
        "currency-issuer-user-avatar-url": "/system/users/avatars/000/000/005/original/portrait.jpg?1559144410",
        "created-at": "2018-10-14T02:56:57.624-07:00",
        "updated-at": "2018-10-14T02:56:57.624-07:00"
      }
    },
    {
      "id": "5",
      "type": "listings",
      "attributes": {
        "user-id": 3,
        "username": "Hannibal",
        "currency-id": 3,
        "currency-name": "macaroon dollars",
        "amount-atomic": 50000000000,
        "cl-link": "https://vancouver.craigslist.ca/van/clt/6722960191.html",
        "cl-title": "Looking for trade, offering - 5 macaroon dollars",
        "offer-currency": true,
        "currency-icon-url": "/system/currencies/icons/000/000/003/original/currency.jpg?1561113125,
        "user-avatar-url": "/system/users/avatars/000/000/004/original/1.jpg?1559736060",
        "currency-issuer-user-id": 3,
        "currency-issuer-user-username": "Hannibal",
        "currency-issuer-user-avatar-url": "/system/users/avatars/000/000/004/original/1.jpg?1559736060",
        "created-at": "2018-10-14T03:07:51.191-07:00",
        "updated-at": "2018-10-14T03:07:51.191-07:00"
      }
    },
    {
      "id": "6",
      "type": "listings",
      "attributes": {
        "user-id": 3,
        "username": "Hannibal",
        "currency-id": 4,
        "currency-name": "Pool coins",
        "amount-atomic": 50000000000,
        "cl-link": "https://vancouver.craigslist.ca/van/clt/6722960432.html",
        "cl-title": "Trading - 5 Pool coins",
        "offer-currency": true,
        "currency-icon-url": "/system/currencies/icons/000/000/004/original/currency.jpg?1569902813",
        "user-avatar-url": "/system/users/avatars/000/000/005/original/portrait.jpg?155914441",
        "currency-issuer-user-id": 4,
        "currency-issuer-user-username": "ScipioAfricanus",
        "currency-issuer-user-avatar-url": "/system/users/avatars/000/000/005/original/portrait.jpg?1559144410",
        "created-at": "2018-10-14T03:13:29.210-07:00",
        "updated-at": "2018-10-14T03:13:29.210-07:00"
      }
    }
  ],
  "links": {
    "self": "http://api.mycurrency.com/sub_locations/1/listings?",
    "first": "http://api.mycurrency.com/sub_locations/1/listings?page=1&per_page=25",
    "prev": null,
    "next": null,
    "last": "http://api.mycurrency.com/sub_locations/1/listings?page=1&per_page=25"
  },
  "meta": {
    "pagination": {
      "per-page": null,
      "total-pages": "1",
      "total-count": "5"
    }
  }
}
```

This endpoint retrieves all active listings being offered in the Craigslist region associated with the specified sub location and outputs their basic public information.

### HTTP Request

`GET https://api.mycurrency.com/sub_locations/<SUB-LOCATION-ID>/listings`

<aside class="notice">
Authentication: not required
</aside>

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the listing
user-id | The ID of the user account that created the listing
username | The username of the user account that created the listing
currency-id | The ID of the currency that the listing is offering
currency-name | The name of the currency that the listing is offering
amount-atomic | The amount of currency being offered, in atomic units (each whole unit is composed of 10^10 atomic units)
cl-link | The link to the Craigslist post containing the description of the listing
cl-title | The title of the Craiglist post containing the description of the listing. Must match the cl-title value
offer-currency | Whether the listing is offering currency. If true, the user must have an adequate amount of currency in the source currency holding they designate to cover the amount offered
currency-icon-url | The URL for the icon of the currency being offered
user-avatar-url | The URL of the avatar of the user that created the listing
currency-issuer-user-id | The ID of the user that issues the currency being offered
currency-issuer-user-username | The username of the user that issues the currency being offered
currency-issuer-user-avatar-url | The URL of the avatar of the user that issues the currency being offered
created-at | The time and date when the listing was created
updated-at | The time and date when the listing was last updated

## List User's Listings with Authorization

```shell
curl https://api.mycurrency.com/users/4/authorized_listings \
  -d '{ "listing": {"amount_atomic": "50000000000", "cl_link": "https://vancouver.craigslist.ca/van/clt/6722959469.html", "cl_title": "Selling", "offer_currency": "true", "currency_holding_type": "PrivateCurrencyHolding", "currency_holding_id": "4"} }' \
  -H 'Accept: application/json' -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer j47lbjj8r9n5yy8mup6cxqc8h70yvhnilm0g84kg0raqckus0k1koj9f75ao' 
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": "1",
      "type": "listings",
      "attributes": {
        "user-id": 4,
        "username": "ScipioAfricanus",
        "currency-id": 4,
        "currency-name": "Pool coins",
        "amount-atomic": 50000000000,
        "cl-link": "https://vancouver.craigslist.ca/van/clt/6722658767.html",
        "cl-title": "For sale - 5 Pool coins",
        "offer-currency": true,
        "currency-icon-url": "/system/currencies/icons/000/000/004/original/currency.jpg?1569902813",
        "user-avatar-url": "/system/users/avatars/000/000/005/original/portrait.jpg?155914441",
        "currency-issuer-user-id": 4,
        "currency-issuer-user-username": "ScipioAfricanus",
        "currency-issuer-user-avatar-url": "/system/users/avatars/000/000/005/original/portrait.jpg?1559144410",
        "created-at": "2018-10-12T22:35:43.000-07:00",
        "updated-at": "2018-10-12T22:35:43.000-07:00",
        "currency-holding-id": 5,
        "currency-holding-type": "PublicCurrencyHolding",
        "active": false,
        "canceled": true
      }
    },
    {
      "id": "2",
      "type": "listings",
      "attributes": {
        "user-id": 4,
        "username": "ScipioAfricanus",
        "currency-id": 4,
        "currency-name": "Pool coins",
        "amount-atomic": 50000000000,
        "cl-link": "https://vancouver.craigslist.ca/van/clt/6722934016.html",
        "cl-title": "For sale - 5 Pool coins",
        "offer-currency": true,
        "currency-icon-url": "/system/currencies/icons/000/000/004/original/currency.jpg?1569902813",
        "user-avatar-url": "/system/users/avatars/000/000/005/original/portrait.jpg?155914441",
        "currency-issuer-user-id": 4,
        "currency-issuer-user-username": "ScipioAfricanus",
        "currency-issuer-user-avatar-url": "/system/users/avatars/000/000/005/original/portrait.jpg?1559144410",
        "created-at": "2018-10-13T22:37:59.492-07:00",
        "updated-at": "2018-10-13T22:37:59.492-07:00",
        "currency-holding-id": 5,
        "currency-holding-type": "PublicCurrencyHolding",
        "active": true,
        "canceled": false
      }
    },
    {
      "id": "3",
      "type": "listings",
      "attributes": {
        "user-id": 4,
        "username": "ScipioAfricanus",
        "currency-id": 4,
        "currency-name": "Pool coins",
        "amount-atomic": 50000000000,
        "cl-link": "https://vancouver.craigslist.ca/van/clt/6722959469.html",
        "cl-title": "Selling - 5 Pool coins",
        "offer-currency": true,
        "currency-icon-url": "/system/currencies/icons/000/000/004/original/currency.jpg?1569902813",
        "user-avatar-url": "/system/users/avatars/000/000/005/original/portrait.jpg?155914441",
        "currency-issuer-user-id": 4,
        "currency-issuer-user-username": "ScipioAfricanus",
        "currency-issuer-user-avatar-url": "/system/users/avatars/000/000/005/original/portrait.jpg?1559144410",
        "created-at": "2018-10-14T02:56:42.738-07:00",
        "updated-at": "2018-10-14T02:56:42.738-07:00",
        "currency-holding-id": 4,
        "currency-holding-type": "PrivateCurrencyHolding",
        "active": true,
        "canceled": false
      }
    },
    {
      "id": "4",
      "type": "listings",
      "attributes": {
        "user-id": 4,
        "username": "ScipioAfricanus",
        "currency-id": 5,
        "currency-name": "Freds Fishing Supplies dollars",
        "amount-atomic": 50000000000,
        "cl-link": "https://vancouver.craigslist.ca/van/clt/6722959714.html",
        "cl-title": "Offering - 5 Freds Fishing Supplies dollars",
        "offer-currency": true,
        "currency-icon-url": "/icons/original/missing.png",
        "user-avatar-url": "/system/users/avatars/000/000/005/original/portrait.jpg?1559144410",
        "currency-issuer-user-id": 4,
        "currency-issuer-user-username": "ScipioAfricanus",
        "currency-issuer-user-avatar-url": "/system/users/avatars/000/000/005/original/portrait.jpg?1559144410",
        "created-at": "2018-10-14T02:56:57.624-07:00",
        "updated-at": "2018-10-14T02:56:57.624-07:00",
        "currency-holding-id": 5,
        "currency-holding-type": "PrivateCurrencyHolding",
        "active": true,
        "canceled": false
      }
    }
  ],
  "links": {
    "self": "https://api.mycurrency.com/users/4/authorized_listings?",
    "first": "https://api.mycurrency.com/users/4/authorized_listings?page=1&per_page=25",
    "prev": null,
    "next": null,
    "last": "https://api.mycurrency.com/users/4/authorized_listings?page=1&per_page=25"
  },
  "meta": {
    "pagination": {
      "per-page": null,
      "total-pages": "1",
      "total-count": "4"
    }
  }
}
```

This endpoint retrieves all listings created by the logged in user and outputs their full details.

### HTTP Request

`GET https://api.mycurrency.com/users/<USER-ID>/authorized_listings`

<aside class="notice">
Authentication: the request requires the OAuth access-token associated with the User referenced by the ID 
</aside>

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the listing
user-id | The ID of the user account that created the listing
username | The username of the user account that created the listing
currency-id | The ID of the currency that the listing is offering
currency-name | The name of the currency that the listing is offering
amount-atomic | The amount of currency being offered, in atomic units (each whole unit is composed of 10^10 atomic units)
cl-link | The link to the Craigslist post containing the description of the listing
cl-title | The title of the Craiglist post containing the description of the listing. Must match the cl-title value
offer-currency | Whether the listing is offering currency. If true, the user must have an adequate amount of currency in the source currency holding they designate to cover the amount offered
currency-icon-url | The URL for the icon of the currency being offered
user-avatar-url | The URL of the avatar of the user that created the listing
currency-issuer-user-id | The ID of the user that issues the currency being offered
currency-issuer-user-username | The username of the user that issues the currency being offered
currency-issuer-user-avatar-url | The URL of the avatar of the user that issues the currency being offered
created-at | The time and date when the listing was created
updated-at | The time and date when the listing was last updated
currency-holding-id | The ID of the public or private currency holding that the currency being offered is held in
currency-holding-type | Whether the currency holding that the offered currency is held in is a "PublicCurrencyHolding" or a "PrivateCurrencyHolding"
active | Whether the listing is active or not. Inactive listings can only be activated if the listing has not been cancelled.
canceled | Whether the listing has been canceled or not. Cancelled listings cannot be uncancelled or reactivated.

## Create Listing

```shell
curl https://api.mycurrency.com/users/4/authorized_listings \
  -d '{ "listing": {"amount_atomic": "50000000000", "cl_link": "https://vancouver.craigslist.ca/van/clt/6722959469.html", "cl_title": "Selling", "offer_currency": "true", "currency_holding_type": "PrivateCurrencyHolding", "currency_holding_id": "4"} }' \
  -H 'Authorization: Bearer j47lbjj8r9n5yy8mup6cxqc8h70yvhnilm0g84kg0raqckus0k1koj9f75ao' \
  -H 'Accept: application/json' -H 'Content-Type: application/json'
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "id": "3",
    "type": "authorized-listings",
    "attributes": {
      "user-id": 4,
      "currency-id": 4,
      "amount-atomic": 50000000000,
      "cl-link": "https://vancouver.craigslist.ca/van/clt/6722959469.html",
      "cl-title": "Selling - 5 Pool coins",
      "offer-currency": true,
      "currency-icon-url": "/system/currencies/icons/000/000/004/original/currency.jpg?1569902813",
      "user-avatar-url": "/system/users/avatars/000/000/005/original/portrait.jpg?155914441",
      "currency-issuer-user-id": 4,
      "currency-issuer-user-username": "ScipioAfricanus",
      "currency-issuer-user-avatar-url": "/system/users/avatars/000/000/005/original/portrait.jpg?1559144410",
      "created-at": "2018-10-14T02:56:42.738-07:00",
      "updated-at": "2018-10-14T02:56:42.738-07:00",
      "currency-holding-id": 4,
      "currency-holding-type": "PrivateCurrencyHolding",
      "active": true,
      "canceled": false
    }
  }
}
```

This endpoint creates a listing. The cl-link provided in the parameters must exist, and the cl-title value must match the title of the Craigslist post found at the URL specified by the cl-link for the listing to be created. Successful listing creation also requires that listings with an :offer_currency value of true have at least as much available currency in the source currency holding they specify as the amount of currency specified by the :amount_atomic parameter they set.

### HTTP Request

`GET https://api.mycurrency.com/users/<USER-ID>/authorized_listings`

<aside class="notice">
Authentication: the request requires the OAuth access-token associated with the User referenced by the ID 
</aside>

### ARGUMENTS

Parameter | Type | Required | Description
--------- | ------- | ------- | -----------
user_id | integer | yes | The ID of the user creating the listing, provided in URL path
amount_atomic | integer | required if :offer_currency is set to true | The amount of currency that is being offered, in atomic units (each whole unit is composed of 10^10 atomic units)
cl-link | string | yes | The link to the Craigslist post containing the description of the listing
cl-title | string | yes | The title of the Craiglist post containing the description of the listing. Must match the cl-title value
offer-currency | boolean | yes | Whether the listing is offering currency. If true, the user must have an adequate amount of currency in the source currency holding they designate to cover the amount offered
currency-holding-id | integer | required if :offer_currency is set to true | The ID of the public or private currency holding that the currency being offered is held in
currency-holding-type | string | required if :offer_currency is set to true | Whether the currency holding that the offered currency is held in is a "PublicCurrencyHolding" or a "PrivateCurrencyHolding"

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the listing
user-id | The ID of the user account that created the listing
username | The username of the user account that created the listing
currency-id | The ID of the currency that the listing is offering
currency-name | The name of the currency that the listing is offering
amount-atomic | The amount of currency being offered, in atomic units (each whole unit is composed of 10^10 atomic units)
cl-link | The link to the Craigslist post containing the description of the listing
cl-title | The title of the Craiglist post containing the description of the listing. Must match the cl-title value
offer-currency | Whether the listing is offering currency. If true, the user must have an adequate amount of currency in the source currency holding they designate to cover the amount offered
currency-icon-url | The URL for the icon of the currency being offered
user-avatar-url | The URL of the avatar of the user that created the listing
currency-issuer-user-id | The ID of the user that issues the currency being offered
currency-issuer-user-username | The username of the user that issues the currency being offered
currency-issuer-user-avatar-url | The URL of the avatar of the user that issues the currency being offered
created-at | The time and date when the listing was created
updated-at | The time and date when the listing was last updated
currency-holding-id | The ID of the public or private currency holding that the currency being offered is held in
currency-holding-type | Whether the currency holding that the offered currency is held in is a "PublicCurrencyHolding" or a "PrivateCurrencyHolding"
active | Whether the listing is active or not. Inactive listings can only be activated if the listing has not been cancelled.
canceled | Whether the listing has been canceled or not. Cancelled listings cannot be uncancelled or reactivated.

## Update Listing

```shell
curl -X PUT https://api.mycurrency.com/users/4/authorized_listings/4 \
  -d '{"listing": {"active": "false"}}' -H 'Authorization: Bearer j47lbjj8r9n5yy8mup6cxqc8h70yvhnilm0g84kg0raqckus0k1koj9f75ao' -H 'Accept: application/json' -H 'Content-Type: application/json'
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "id": "4",
    "type": "authorized-listings",
    "attributes": {
      "user-id": 4,
      "username": "ScipioAfricanus",
      "currency-id": 5,
      "currency-name": "Freds Fishing Supplies dollars",
      "amount-atomic": 50000000000,
      "cl-link": "https://vancouver.craigslist.ca/van/clt/6722959714.html",
      "cl-title": "Offering - 5 Freds Fishing Supplies dollars",
      "offer-currency": true,
      "currency-icon-url": "/icons/original/missing.png",
      "user-avatar-url": "/system/users/avatars/000/000/005/original/portrait.jpg?1559144410",
      "currency-issuer-user-id": 4,
      "currency-issuer-user-username": "ScipioAfricanus",
      "currency-issuer-user-avatar-url": "/system/users/avatars/000/000/005/original/portrait.jpg?1559144410",
      "created-at": "2018-10-14T02:56:57.624-07:00",
      "updated-at": "2018-10-14T17:48:29.981-07:00",
      "currency-holding-id": 5,
      "currency-holding-type": "PrivateCurrencyHolding",
      "active": false,
      "canceled": false
    }
  }
}
```

This endpoint updates a listing. The cl-link provided in the parameters must exist, and the cl-title value must match the title of the Craigslist post found at the URL specified by the cl-link, for the listing's :active value to be changed from false to true. Listing activation also requires that listings with an :offer_currency value of true have at least as much available currency in the source currency holding they specify as the amount of currency specified by the :amount_atomic field.

### HTTP Request

`GET https://api.mycurrency.com/users/<USER-ID>/authorized_listings/<ID>`

<aside class="notice">
Authentication: the request requires the OAuth access-token associated with the User referenced by the ID 
</aside>

### ARGUMENTS

Parameter | Type | Required | Description
--------- | ------- | ------- | -----------
user_id | integer | yes | The ID of the user updating the listing, provided in URL path
active | boolean | yes | Whether the listing is active or not. Inactive listings can only be activated if the listing has not been cancelled.

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the listing
user-id | The ID of the user account that created the listing
username | The username of the user account that created the listing
currency-id | The ID of the currency that the listing is offering
currency-name | The name of the currency that the listing is offering
amount-atomic | The amount of currency being offered, in atomic units (each whole unit is composed of 10^10 atomic units)
cl-link | The link to the Craigslist post containing the description of the listing
cl-title | The title of the Craiglist post containing the description of the listing. Must match the cl-title value
offer-currency | Whether the listing is offering currency. If true, the user must have an adequate amount of currency in the source currency holding they designate to cover the amount offered
currency-icon-url | The URL for the icon of the currency being offered
user-avatar-url | The URL of the avatar of the user that created the listing
currency-issuer-user-id | The ID of the user that issues the currency being offered
currency-issuer-user-username | The username of the user that issues the currency being offered
currency-issuer-user-avatar-url | The URL of the avatar of the user that issues the currency being offered
created-at | The time and date when the listing was created
updated-at | The time and date when the listing was last updated
currency-holding-id | The ID of the public or private currency holding that the currency being offered is held in
currency-holding-type | Whether the currency holding that the offered currency is held in is a "PublicCurrencyHolding" or a "PrivateCurrencyHolding"
active | Whether the listing is active or not. Inactive listings can only be activated if the listing has not been cancelled.
canceled | Whether the listing has been canceled or not. Cancelled listings cannot be uncancelled or reactivated.

# Categories

## Get a Super Category

```shell
curl 'https://api.mycurrency.com/super_categories/1' \
  -H 'Accept: application/json' -H 'Content-Type: application/json'
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "id": "1",
    "type": "super-categories",
    "attributes": {
      "name": "Arts/Craft",
      "description": "handicrafts, art and furniture"
    }
  }
}
```

This endpoint retrieves a particular super category.

### HTTP Request

`GET https://api.mycurrency.com/super_categories/<ID>`

<aside class="notice">
Authentication: not required
</aside>

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the super category
name | The name of the super category
description | The description of the super category

## List Super Categories

```shell
curl 'https://api.mycurrency.com/super_categories' \
  -H 'Accept: application/json' -H 'Content-Type: application/json'
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": "1",
      "type": "super-categories",
      "attributes": {
        "name": "Arts/Craft",
        "description": "handicrafts, art and furniture"
      }
    },
    {
      "id": "2",
      "type": "super-categories",
      "attributes": {
        "name": "Therapeutic Services",
        "description": "all types of therapeutic services including spa treatments and massage"
      }
    },
    {
      "id": "3",
      "type": "super-categories",
      "attributes": {
        "name": "sporting",
        "description": "outdoor and sporting goods"
      }
    }
  ],
  "links": {
    "self": "https://api.mycurrency.com/super_categories?",
    "first": "https://api.mycurrency.com/super_categories?page=1&per_page=25",
    "prev": null,
    "next": null,
    "last": "https://api.mycurrency.com/super_categories?page=1&per_page=25"
  },
  "meta": {
    "pagination": {
      "per-page": null,
      "total-pages": "1",
      "total-count": "3"
    }
  }
}
```

This endpoint retrieves all super categories.

### HTTP Request

`GET https://api.mycurrency.com/super_categories`

<aside class="notice">
Authentication: not required
</aside>

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the super category
name | The name of the super category
description | The description of the super category

## Get a Mid Category

```shell
curl 'https://api.mycurrency.com/mid_categories/1' \
  -H 'Accept: application/json' -H 'Content-Type: application/json'
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "id": "1",
    "type": "mid-categories",
    "attributes": {
      "name": "furniture",
      "description": "furniture of all kinds",
      "super-category-id": 1
    }
  }
}
```

This endpoint retrieves a particular mid category.

### HTTP Request

`GET https://api.mycurrency.com/mid_categories/<ID>`

<aside class="notice">
Authentication: not required
</aside>

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the mid category
name | The name of the mid category
description | The description of the mid category
super-category-id | The ID of the parent super category

## List Mid Categories

```shell
curl 'https://api.mycurrency.com/mid_categories' \
  -H 'Accept: application/json' -H 'Content-Type: application/json'
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": "1",
      "type": "mid-categories",
      "attributes": {
        "name": "furniture",
        "description": "furniture of all kinds",
        "super-category-id": 1
      }
    },
    {
      "id": "2",
      "type": "mid-categories",
      "attributes": {
        "name": "spa services",
        "description": "various types of spa services",
        "super-category-id": 2
      }
    },
    {
      "id": "3",
      "type": "mid-categories",
      "attributes": {
        "name": "outdoor supplies",
        "description": "camping, hunting and fishing goods",
        "super-category-id": 3
      }
    }
  ],
  "links": {
    "self": "https://api.mycurrency.com/mid_categories?",
    "first": "https://api.mycurrency.com/mid_categories?page=1&per_page=25",
    "prev": null,
    "next": null,
    "last": "https://api.mycurrency.com/mid_categories?page=1&per_page=25"
  },
  "meta": {
    "pagination": {
      "per-page": null,
      "total-pages": "1",
      "total-count": "3"
    }
  }
}
```

This endpoint retrieves all mid categories.

### HTTP Request

`GET https://api.mycurrency.com/mid_categories`

<aside class="notice">
Authentication: not required
</aside>

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the mid category
name | The name of the mid category
description | The description of the mid category
super-category-id | The ID of the parent super category

## List Super Category's Mid Categories

```shell
curl 'https://api.mycurrency.com/super_categories/1/mid_categories' \
  -H 'Accept: application/json' -H 'Content-Type: application/json'
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": "1",
      "type": "mid-categories",
      "attributes": {
        "name": "furniture",
        "description": "furniture of all kinds",
        "super-category-id": 1
      }
    }
  ],
  "links": {
    "self": "https://api.mycurrency.com/super_categories/1/mid_categories?",
    "first": "https://api.mycurrency.com/super_categories/1/mid_categories?page=1&per_page=25",
    "prev": null,
    "next": null,
    "last": "https://api.mycurrency.com/super_categories/1/mid_categories?page=1&per_page=25"
  },
  "meta": {
    "pagination": {
      "per-page": null,
      "total-pages": "1",
      "total-count": "1"
    }
  }
}
```

This endpoint retrieves all child mid categories of the specified super category.

### HTTP Request

`GET https://api.mycurrency.com/super_categories/<SUPER-CATEGORY-ID>/mid_categories`

<aside class="notice">
Authentication: not required
</aside>

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the mid category
name | The name of the mid category
description | The description of the mid category
super-category-id | The ID of the parent super category

## Get a Sub Category

```shell
curl 'https://api.mycurrency.com/sub_categories/1' \
  -H 'Accept: application/json' -H 'Content-Type: application/json'
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "id": "1",
    "type": "sub-categories",
    "attributes": {
      "name": "couch",
      "description": "couches of all kinds",
      "mid-category-id": 1
    }
  }
}
```

This endpoint retrieves a particular sub category.

### HTTP Request

`GET https://api.mycurrency.com/sub_categories/<ID>`

<aside class="notice">
Authentication: not required
</aside>

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the sub category
name | The name of the name category
description | The description of the sub category
mid-category-id | The ID of the parent mid category

## List Sub Categories

```shell
curl 'https://api.mycurrency.com/sub_categories' \
  -H 'Accept: application/json' -H 'Content-Type: application/json'
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": "1",
      "type": "sub-categories",
      "attributes": {
        "name": "couch",
        "description": "couches of all kinds",
        "mid-category-id": 1
      }
    },
    {
      "id": "2",
      "type": "sub-categories",
      "attributes": {
        "name": "massage",
        "description": "therapeutic massages",
        "mid-category-id": 2
      }
    },
    {
      "id": "3",
      "type": "sub-categories",
      "attributes": {
        "name": "skin treatment",
        "description": "all manner of spa skin treatments",
        "mid-category-id": 2
      }
    },
    {
      "id": "4",
      "type": "sub-categories",
      "attributes": {
        "name": "fishing supplies",
        "description": "fishing supplies including bait and tackle",
        "mid-category-id": 3
      }
    }
  ],
  "links": {
    "self": "https://api.mycurrency.com/sub_categories?",
    "first": "https://api.mycurrency.com/sub_categories?page=1&per_page=25",
    "prev": null,
    "next": null,
    "last": "https://api.mycurrency.com/sub_categories?page=1&per_page=25"
  },
  "meta": {
    "pagination": {
      "per-page": null,
      "total-pages": "1",
      "total-count": "4"
    }
  }
}
```

This endpoint retrieves all sub categories.

### HTTP Request

`GET https://api.mycurrency.com/sub_categories`

<aside class="notice">
Authentication: not required
</aside>

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the sub category
name | The name of the name category
description | The description of the sub category
mid-category-id | The ID of the parent mid category

## List Mid Category's Sub Categories

```shell
curl 'https://api.mycurrency.com/super_categories/2/mid_categories/2/sub_categories' \
  -H 'Accept: application/json' -H 'Content-Type: application/json'
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": "2",
      "type": "sub-categories",
      "attributes": {
        "name": "massage",
        "description": "therapeutic massages",
        "mid-category-id": 2
      }
    },
    {
      "id": "3",
      "type": "sub-categories",
      "attributes": {
        "name": "skin treatment",
        "description": "all manner of spa skin treatments",
        "mid-category-id": 2
      }
    }
  ],
  "links": {
    "self": "https://api.mycurrency.com/super_categories/2/mid_categories/2/sub_categories?",
    "first": "https://api.mycurrency.com/super_categories/2/mid_categories/2/sub_categories?page=1&per_page=25",
    "prev": null,
    "next": null,
    "last": "https://api.mycurrency.com/super_categories/2/mid_categories/2/sub_categories?page=1&per_page=25"
  },
  "meta": {
    "pagination": {
      "per-page": null,
      "total-pages": "1",
      "total-count": "2"
    }
  }
}
```

This endpoint retrieves all child sub categories of the specified mid category.

### HTTP Request

`GET https://api.mycurrency.com/super_categories/<SUPER-CATEGORY-ID>/mid_categories/<MID-CATEGORY-ID>/sub_categories`

<aside class="notice">
Authentication: not required
</aside>

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the sub category
name | The name of the name category
description | The description of the sub category
mid-category-id | The ID of the parent mid category

## List Super Category's Sub Categories

```shell
curl 'https://api.mycurrency.com/super_categories/2/sub_categories' \
  -H 'Accept: application/json' -H 'Content-Type: application/json'
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": "2",
      "type": "sub-categories",
      "attributes": {
        "name": "massage",
        "description": "therapeutic massages",
        "mid-category-id": 2
      }
    },
    {
      "id": "3",
      "type": "sub-categories",
      "attributes": {
        "name": "skin treatment",
        "description": "all manner of spa skin treatments",
        "mid-category-id": 2
      }
    }
  ],
  "links": {
    "self": "https://api.mycurrency.com/super_categories/2/sub_categories?",
    "first": "https://api.mycurrency.com/super_categories/2/sub_categories?page=1&per_page=25",
    "prev": null,
    "next": null,
    "last": "https://api.mycurrency.com/super_categories/2/sub_categories?page=1&per_page=25"
  },
  "meta": {
    "pagination": {
      "per-page": null,
      "total-pages": "1",
      "total-count": "2"
    }
  }
}
```

This endpoint retrieves all child sub categories of the specified super category.

### HTTP Request

`GET https://api.mycurrency.com/super_categories/<SUPER-CATEGORY-ID>/sub_categories`

<aside class="notice">
Authentication: not required
</aside>

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the sub category
name | The name of the name category
description | The description of the sub category
mid-category-id | The ID of the parent mid category

# Locations

## Get a Super Location

```shell
curl 'https://api.mycurrency.com/super_locations/1' \
  -H 'Accept: application/json' -H 'Content-Type: application/json'
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "id": "1",
    "type": "super-locations",
    "attributes": {
      "name": "US"
    }
  }
}
```

This endpoint retrieves a particular super location.

### HTTP Request

`GET https://api.mycurrency.com/super_locations/<ID>`

<aside class="notice">
Authentication: not required
</aside>

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the super location
name | The name of the super location

## List Super Locations

```shell
curl 'https://api.mycurrency.com/super_locations' \
  -H 'Accept: application/json' -H 'Content-Type: application/json'
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": "2",
      "type": "super-locations",
      "attributes": {
        "name": "US"
      }
    },
    {
      "id": "3",
      "type": "super-locations",
      "attributes": {
        "name": "Canada"
      }
    },
    {
      "id": "4",
      "type": "super-locations",
      "attributes": {
        "name": "Europe"
      }
    },
    {
      "id": "5",
      "type": "super-locations",
      "attributes": {
        "name": "Asia, Pacific and Middle East"
      }
    },
    {
      "id": "6",
      "type": "super-locations",
      "attributes": {
        "name": "Oceania"
      }
    },
    {
      "id": "7",
      "type": "super-locations",
      "attributes": {
        "name": "Latin America and Caribbean"
      }
    },
    {
      "id": "8",
      "type": "super-locations",
      "attributes": {
        "name": "Africa"
      }
    }
  ],
  "links": {
    "self": "https://api.mycurrency.com/super_locations?",
    "first": "https://api.mycurrency.com/super_locations?page=1&per_page=25",
    "prev": null,
    "next": null,
    "last": "https://api.mycurrency.com/super_locations?page=1&per_page=25"
  },
  "meta": {
    "pagination": {
      "per-page": null,
      "total-pages": "1",
      "total-count": "7"
    }
  }
}
```

This endpoint retrieves all super locations.

### HTTP Request

`GET https://api.mycurrency.com/super_locations`

<aside class="notice">
Authentication: not required
</aside>

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the super location
name | The name of the super location

## Get a Mid Location

```shell
curl 'https://api.mycurrency.com/mid_locations/2' \
  -H 'Accept: application/json' -H 'Content-Type: application/json'
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "id": "2",
    "type": "mid-locations",
    "attributes": {
      "name": "Alabama",
      "super-location-id": 2
    }
  }
}
```

This endpoint retrieves a particular mid location.

### HTTP Request

`GET https://api.mycurrency.com/mid_locations/<ID>`

<aside class="notice">
Authentication: not required
</aside>

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the mid location
name | The name of the mid location
super-location-id | The ID of the parent super location

## List Mid Locations

```shell
curl 'https://api.mycurrency.com/mid_locations' \
  -H 'Accept: application/json' -H 'Content-Type: application/json'
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": "2",
      "type": "mid-locations",
      "attributes": {
        "name": "Alabama",
        "super-location-id": 2
      }
    },
    {
      "id": "3",
      "type": "mid-locations",
      "attributes": {
        "name": "Alaska",
        "super-location-id": 2
      }
    },
    {
      "id": "4",
      "type": "mid-locations",
      "attributes": {
        "name": "Arizona",
        "super-location-id": 2
      }
    },
    {
      "id": "5",
      "type": "mid-locations",
      "attributes": {
        "name": "Arkansas",
        "super-location-id": 2
      }
    },
    {
      "id": "6",
      "type": "mid-locations",
      "attributes": {
        "name": "California",
        "super-location-id": 2
      }
    },
    {
      "id": "7",
      "type": "mid-locations",
      "attributes": {
        "name": "Colorado",
        "super-location-id": 2
      }
    },
    {
      "id": "8",
      "type": "mid-locations",
      "attributes": {
        "name": "Connecticut",
        "super-location-id": 2
      }
    },
    {
      "id": "9",
      "type": "mid-locations",
      "attributes": {
        "name": "Delaware",
        "super-location-id": 2
      }
    },
    {
      "id": "10",
      "type": "mid-locations",
      "attributes": {
        "name": "District of Columbia",
        "super-location-id": 2
      }
    },
    {
      "id": "11",
      "type": "mid-locations",
      "attributes": {
        "name": "Florida",
        "super-location-id": 2
      }
    },
    {
      "id": "12",
      "type": "mid-locations",
      "attributes": {
        "name": "Georgia",
        "super-location-id": 2
      }
    },
    {
      "id": "13",
      "type": "mid-locations",
      "attributes": {
        "name": "Hawaii",
        "super-location-id": 2
      }
    },
    {
      "id": "14",
      "type": "mid-locations",
      "attributes": {
        "name": "Idaho",
        "super-location-id": 2
      }
    },
    {
      "id": "15",
      "type": "mid-locations",
      "attributes": {
        "name": "Illinois",
        "super-location-id": 2
      }
    },
    {
      "id": "16",
      "type": "mid-locations",
      "attributes": {
        "name": "Indiana",
        "super-location-id": 2
      }
    },
    {
      "id": "17",
      "type": "mid-locations",
      "attributes": {
        "name": "Iowa",
        "super-location-id": 2
      }
    },
    {
      "id": "18",
      "type": "mid-locations",
      "attributes": {
        "name": "Kansas",
        "super-location-id": 2
      }
    },
    {
      "id": "19",
      "type": "mid-locations",
      "attributes": {
        "name": "Kentucky",
        "super-location-id": 2
      }
    },
    {
      "id": "20",
      "type": "mid-locations",
      "attributes": {
        "name": "Louisiana",
        "super-location-id": 2
      }
    },
    {
      "id": "21",
      "type": "mid-locations",
      "attributes": {
        "name": "Maine",
        "super-location-id": 2
      }
    },
    {
      "id": "22",
      "type": "mid-locations",
      "attributes": {
        "name": "Maryland",
        "super-location-id": 2
      }
    },
    {
      "id": "23",
      "type": "mid-locations",
      "attributes": {
        "name": "Massachusetts",
        "super-location-id": 2
      }
    },
    {
      "id": "24",
      "type": "mid-locations",
      "attributes": {
        "name": "Michigan",
        "super-location-id": 2
      }
    },
    {
      "id": "25",
      "type": "mid-locations",
      "attributes": {
        "name": "Minnesota",
        "super-location-id": 2
      }
    },
    {
      "id": "26",
      "type": "mid-locations",
      "attributes": {
        "name": "Mississippi",
        "super-location-id": 2
      }
    }
  ],
  "links": {
    "self": "https://api.mycurrency.com/mid_locations?",
    "first": "https://api.mycurrency.com/mid_locations?page=1&per_page=25",
    "prev": null,
    "next": "https://api.mycurrency.com/mid_locations?page=2&per_page=25",
    "last": "https://api.mycurrency.com/mid_locations?page=6&per_page=25"
  },
  "meta": {
    "pagination": {
      "per-page": null,
      "total-pages": "6",
      "total-count": "140"
    }
  }
}
```

This endpoint retrieves all mid locations.

### HTTP Request

`GET https://api.mycurrency.com/mid_locations`

<aside class="notice">
Authentication: not required
</aside>

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the mid location
name | The name of the mid location
super-location-id | The ID of the parent super location

## List Super Location's Mid Locations

```shell
curl 'https://api.mycurrency.com/super_locations/2/mid_locations' \
  -H 'Accept: application/json' -H 'Content-Type: application/json'
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": "2",
      "type": "mid-locations",
      "attributes": {
        "name": "Alabama",
        "super-location-id": 2
      }
    },
    {
      "id": "3",
      "type": "mid-locations",
      "attributes": {
        "name": "Alaska",
        "super-location-id": 2
      }
    },
    {
      "id": "4",
      "type": "mid-locations",
      "attributes": {
        "name": "Arizona",
        "super-location-id": 2
      }
    },
    {
      "id": "5",
      "type": "mid-locations",
      "attributes": {
        "name": "Arkansas",
        "super-location-id": 2
      }
    },
    {
      "id": "6",
      "type": "mid-locations",
      "attributes": {
        "name": "California",
        "super-location-id": 2
      }
    },
    {
      "id": "7",
      "type": "mid-locations",
      "attributes": {
        "name": "Colorado",
        "super-location-id": 2
      }
    },
    {
      "id": "8",
      "type": "mid-locations",
      "attributes": {
        "name": "Connecticut",
        "super-location-id": 2
      }
    },
    {
      "id": "9",
      "type": "mid-locations",
      "attributes": {
        "name": "Delaware",
        "super-location-id": 2
      }
    },
    {
      "id": "10",
      "type": "mid-locations",
      "attributes": {
        "name": "District of Columbia",
        "super-location-id": 2
      }
    },
    {
      "id": "11",
      "type": "mid-locations",
      "attributes": {
        "name": "Florida",
        "super-location-id": 2
      }
    },
    {
      "id": "12",
      "type": "mid-locations",
      "attributes": {
        "name": "Georgia",
        "super-location-id": 2
      }
    },
    {
      "id": "13",
      "type": "mid-locations",
      "attributes": {
        "name": "Hawaii",
        "super-location-id": 2
      }
    },
    {
      "id": "14",
      "type": "mid-locations",
      "attributes": {
        "name": "Idaho",
        "super-location-id": 2
      }
    },
    {
      "id": "15",
      "type": "mid-locations",
      "attributes": {
        "name": "Illinois",
        "super-location-id": 2
      }
    },
    {
      "id": "16",
      "type": "mid-locations",
      "attributes": {
        "name": "Indiana",
        "super-location-id": 2
      }
    },
    {
      "id": "17",
      "type": "mid-locations",
      "attributes": {
        "name": "Iowa",
        "super-location-id": 2
      }
    },
    {
      "id": "18",
      "type": "mid-locations",
      "attributes": {
        "name": "Kansas",
        "super-location-id": 2
      }
    },
    {
      "id": "19",
      "type": "mid-locations",
      "attributes": {
        "name": "Kentucky",
        "super-location-id": 2
      }
    },
    {
      "id": "20",
      "type": "mid-locations",
      "attributes": {
        "name": "Louisiana",
        "super-location-id": 2
      }
    },
    {
      "id": "21",
      "type": "mid-locations",
      "attributes": {
        "name": "Maine",
        "super-location-id": 2
      }
    },
    {
      "id": "22",
      "type": "mid-locations",
      "attributes": {
        "name": "Maryland",
        "super-location-id": 2
      }
    },
    {
      "id": "23",
      "type": "mid-locations",
      "attributes": {
        "name": "Massachusetts",
        "super-location-id": 2
      }
    },
    {
      "id": "24",
      "type": "mid-locations",
      "attributes": {
        "name": "Michigan",
        "super-location-id": 2
      }
    },
    {
      "id": "25",
      "type": "mid-locations",
      "attributes": {
        "name": "Minnesota",
        "super-location-id": 2
      }
    },
    {
      "id": "26",
      "type": "mid-locations",
      "attributes": {
        "name": "Mississippi",
        "super-location-id": 2
      }
    }
  ],
  "links": {
    "self": "https://api.mycurrency.com/super_locations/2/mid_locations?",
    "first": "https://api.mycurrency.com/super_locations/2/mid_locations?page=1&per_page=25",
    "prev": null,
    "next": "https://api.mycurrency.com/super_locations/2/mid_locations?page=2&per_page=25",
    "last": "https://api.mycurrency.com/super_locations/2/mid_locations?page=3&per_page=25"
  },
  "meta": {
    "pagination": {
      "per-page": null,
      "total-pages": "3",
      "total-count": "52"
    }
  }
}
```

This endpoint retrieves all child mid locations of the specified super location.

### HTTP Request

`GET https://api.mycurrency.com/super_locations/<SUPER-LOCATION-ID>/mid_locations`

<aside class="notice">
Authentication: not required
</aside>

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the mid location
name | The name of the mid location
super-location-id | The ID of the parent super location

## Get a Sub Location

```shell
curl 'https://api.mycurrency.com/sub_locations/1' \
  -H 'Accept: application/json' -H 'Content-Type: application/json'
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "id": "1",
    "type": "sub-locations",
    "attributes": {
      "name": "auburn",
      "mid-location-id": 1,
      "mid-location-name": "Alabama",
      "longitude": -85.48078249999999,
      "latitude": 32.6098566,
      "time-zone": "America/Chicago"
    }
  }
}
```

This endpoint retrieves a particular sub location.

### HTTP Request

`GET https://api.mycurrency.com/sub_locations/<ID>`

<aside class="notice">
Authentication: not required
</aside>

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the sub location
name | The name of the sub location
mid-location-id | The ID of the parent mid location
mid-location-name | The name of the parent mid location
longitude | The longitude of the sub location
latitude | The latitude of the sub location
time-zone | The time zone of the sub location

## List Sub Locations

```shell
curl 'https://api.mycurrency.com/sub_locations?per_page=10' \
  -H 'Accept: application/json' -H 'Content-Type: application/json'
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": "1",
      "type": "sub-locations",
      "attributes": {
        "name": "auburn",
        "mid-location-id": 1,
        "mid-location-name": "Alabama",
        "longitude": -85.48078249999999,
        "latitude": 32.6098566,
        "time-zone": "America/Chicago"
      }
    },
    {
      "id": "2",
      "type": "sub-locations",
      "attributes": {
        "name": "birmingham",
        "mid-location-id": 1,
        "mid-location-name": "Alabama",
        "longitude": -86.8103567,
        "latitude": 33.5185892,
        "time-zone": "America/Chicago"
      }
    },
    {
      "id": "3",
      "type": "sub-locations",
      "attributes": {
        "name": "dothan",
        "mid-location-id": 1,
        "mid-location-name": "Alabama",
        "longitude": -85.3904888,
        "latitude": 31.2232313,
        "time-zone": "America/Chicago"
      }
    },
    {
      "id": "4",
      "type": "sub-locations",
      "attributes": {
        "name": "florence / muscle shoals",
        "mid-location-id": 1,
        "mid-location-name": "Alabama",
        "longitude": -87.66752919999999,
        "latitude": 34.7448112,
        "time-zone": "America/Chicago"
      }
    },
    {
      "id": "5",
      "type": "sub-locations",
      "attributes": {
        "name": "gadsden-anniston",
        "mid-location-id": 1,
        "mid-location-name": "Alabama",
        "longitude": -85.7933312,
        "latitude": 33.7094448,
        "time-zone": "America/Chicago"
      }
    },
    {
      "id": "6",
      "type": "sub-locations",
      "attributes": {
        "name": "huntsville / decatur",
        "mid-location-id": 1,
        "mid-location-name": "Alabama",
        "longitude": -86.9833417,
        "latitude": 34.6059253,
        "time-zone": "America/Chicago"
      }
    },
    {
      "id": "7",
      "type": "sub-locations",
      "attributes": {
        "name": "mobile",
        "mid-location-id": 1,
        "mid-location-name": "Alabama",
        "longitude": -88.0398912,
        "latitude": 30.6953657,
        "time-zone": "America/Chicago"
      }
    },
    {
      "id": "8",
      "type": "sub-locations",
      "attributes": {
        "name": "montgomery",
        "mid-location-id": 1,
        "mid-location-name": "Alabama",
        "longitude": -86.3077368,
        "latitude": 32.3792233,
        "time-zone": "America/Chicago"
      }
    },
    {
      "id": "9",
      "type": "sub-locations",
      "attributes": {
        "name": "tuscaloosa",
        "mid-location-id": 1,
        "mid-location-name": "Alabama",
        "longitude": -87.56917349999999,
        "latitude": 33.2098407,
        "time-zone": "America/Chicago"
      }
    },
    {
      "id": "10",
      "type": "sub-locations",
      "attributes": {
        "name": "anchorage / mat-su",
        "mid-location-id": 2,
        "mid-location-name": "Alaska",
        "longitude": -149.8714752,
        "latitude": 61.1774892,
        "time-zone": "America/Anchorage"
      }
    }
  ],
  "links": {
    "self": "https://api.mycurrency.com/sub_locations?per_page=10",
    "first": "https://api.mycurrency.com/sub_locations?page=1&per_page=10",
    "prev": null,
    "next": "https://api.mycurrency.com/sub_locations?page=2&per_page=10",
    "last": "https://api.mycurrency.com/sub_locations?page=72&per_page=10"
  },
  "meta": {
    "pagination": {
      "per-page": "10",
      "total-pages": "72",
      "total-count": "712"
    }
  }
}
```

This endpoint retrieves all sub locations.

### HTTP Request

`GET https://api.mycurrency.com/sub_locations`

<aside class="notice">
Authentication: not required
</aside>

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the sub location
name | The name of the sub location
mid-location-id | The ID of the parent mid location
mid-location-name | The name of the parent mid location
longitude | The longitude of the sub location
latitude | The latitude of the sub location
time-zone | The time zone of the sub location

## List Mid Location's Sub Locations

```shell
curl 'https://api.mycurrency.com/super_locations/2/mid_locations/54/sub_locations?per_page=10' \
  -H 'Accept: application/json' -H 'Content-Type: application/json'
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": "426",
      "type": "sub-locations",
      "attributes": {
        "name": "cariboo",
        "mid-location-id": 54,
        "mid-location-name": "British Columbia",
        "longitude": -123.4553619,
        "latitude": 52.4031805,
        "time-zone": "America/Vancouver"
      }
    },
    {
      "id": "427",
      "type": "sub-locations",
      "attributes": {
        "name": "comox valley",
        "mid-location-id": 54,
        "mid-location-name": "British Columbia",
        "longitude": -125.0219451,
        "latitude": 49.70641879999999,
        "time-zone": "America/Vancouver"
      }
    },
    {
      "id": "428",
      "type": "sub-locations",
      "attributes": {
        "name": "fraser valley",
        "mid-location-id": 54,
        "mid-location-name": "British Columbia",
        "longitude": -121.8159307,
        "latitude": 49.3764104,
        "time-zone": "America/Vancouver"
      }
    },
    {
      "id": "429",
      "type": "sub-locations",
      "attributes": {
        "name": "kamloops",
        "mid-location-id": 54,
        "mid-location-name": "British Columbia",
        "longitude": -120.3272675,
        "latitude": 50.674522,
        "time-zone": "America/Vancouver"
      }
    },
    {
      "id": "430",
      "type": "sub-locations",
      "attributes": {
        "name": "kelowna / okanagan",
        "mid-location-id": 54,
        "mid-location-name": "British Columbia",
        "longitude": -119.4960106,
        "latitude": 49.8879519,
        "time-zone": "America/Vancouver"
      }
    },
    {
      "id": "431",
      "type": "sub-locations",
      "attributes": {
        "name": "kootenays",
        "mid-location-id": 54,
        "mid-location-name": "British Columbia",
        "longitude": -115.9592102,
        "latitude": 50.9769367,
        "time-zone": "America/Edmonton"
      }
    },
    {
      "id": "432",
      "type": "sub-locations",
      "attributes": {
        "name": "nanaimo",
        "mid-location-id": 54,
        "mid-location-name": "British Columbia",
        "longitude": -123.9400648,
        "latitude": 49.1658836,
        "time-zone": "America/Vancouver"
      }
    },
    {
      "id": "433",
      "type": "sub-locations",
      "attributes": {
        "name": "prince george",
        "mid-location-id": 54,
        "mid-location-name": "British Columbia",
        "longitude": -122.7496693,
        "latitude": 53.9170641,
        "time-zone": "America/Vancouver"
      }
    },
    {
      "id": "434",
      "type": "sub-locations",
      "attributes": {
        "name": "skeena-bulkley",
        "mid-location-id": 54,
        "mid-location-name": "British Columbia",
        "longitude": -126.907872,
        "latitude": 54.8281552,
        "time-zone": "America/Vancouver"
      }
    },
    {
      "id": "435",
      "type": "sub-locations",
      "attributes": {
        "name": "sunshine coast",
        "mid-location-id": 54,
        "mid-location-name": "British Columbia",
        "longitude": -123.7643986,
        "latitude": 49.7604377,
        "time-zone": "America/Vancouver"
      }
    }
  ],
  "links": {
    "self": "https://api.mycurrency.com/super_locations/2/mid_locations/54/sub_locations?per_page=10",
    "first": "https://api.mycurrency.com/super_locations/2/mid_locations/54/sub_locations?page=1&per_page=10",
    "prev": null,
    "next": "https://api.mycurrency.com/super_locations/2/mid_locations/54/sub_locations?page=2&per_page=10",
    "last": "https://api.mycurrency.com/super_locations/2/mid_locations/54/sub_locations?page=2&per_page=10"
  },
  "meta": {
    "pagination": {
      "per-page": "10",
      "total-pages": "2",
      "total-count": "13"
    }
  }
}
```

This endpoint retrieves all child sub locations of the specified mid location.

### HTTP Request

`GET https://api.mycurrency.com/super_locations/<SUPER-LOCATION-ID>/mid_locations/<MID-LOCATION-ID>/sub_locations`

<aside class="notice">
Authentication: not required
</aside>

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the sub location
name | The name of the sub location
mid-location-id | The ID of the parent mid location
mid-location-name | The name of the parent mid location
longitude | The longitude of the sub location
latitude | The latitude of the sub location
time-zone | The time zone of the sub location

## List Super Location's Sub Locations

```shell
curl 'https://api.mycurrency.com/super_locations/2/sub_locations?per_page=10' \
  -H 'Accept: application/json' -H 'Content-Type: application/json'
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": "419",
      "type": "sub-locations",
      "attributes": {
        "name": "calgary",
        "mid-location-id": 53,
        "mid-location-name": "Alberta",
        "longitude": -114.0708459,
        "latitude": 51.0486151,
        "time-zone": "America/Edmonton"
      }
    },
    {
      "id": "420",
      "type": "sub-locations",
      "attributes": {
        "name": "edmonton",
        "mid-location-id": 53,
        "mid-location-name": "Alberta",
        "longitude": -113.4909267,
        "latitude": 53.544389,
        "time-zone": "America/Edmonton"
      }
    },
    {
      "id": "421",
      "type": "sub-locations",
      "attributes": {
        "name": "ft mcmurray",
        "mid-location-id": 53,
        "mid-location-name": "Alberta",
        "longitude": -111.3803407,
        "latitude": 56.72637959999999,
        "time-zone": "America/Edmonton"
      }
    },
    {
      "id": "422",
      "type": "sub-locations",
      "attributes": {
        "name": "lethbridge",
        "mid-location-id": 53,
        "mid-location-name": "Alberta",
        "longitude": -112.84184,
        "latitude": 49.69349,
        "time-zone": "America/Edmonton"
      }
    },
    {
      "id": "423",
      "type": "sub-locations",
      "attributes": {
        "name": "medicine hat",
        "mid-location-id": 53,
        "mid-location-name": "Alberta",
        "longitude": -110.6764257,
        "latitude": 50.0405486,
        "time-zone": "America/Edmonton"
      }
    },
    {
      "id": "424",
      "type": "sub-locations",
      "attributes": {
        "name": "peace river country",
        "mid-location-id": 53,
        "mid-location-name": "Alberta",
        "longitude": -117.2893839,
        "latitude": 56.2341823,
        "time-zone": "America/Edmonton"
      }
    },
    {
      "id": "425",
      "type": "sub-locations",
      "attributes": {
        "name": "red deer",
        "mid-location-id": 53,
        "mid-location-name": "Alberta",
        "longitude": -113.8112386,
        "latitude": 52.2681118,
        "time-zone": "America/Edmonton"
      }
    },
    {
      "id": "426",
      "type": "sub-locations",
      "attributes": {
        "name": "cariboo",
        "mid-location-id": 54,
        "mid-location-name": "British Columbia",
        "longitude": -123.4553619,
        "latitude": 52.4031805,
        "time-zone": "America/Vancouver"
      }
    },
    {
      "id": "427",
      "type": "sub-locations",
      "attributes": {
        "name": "comox valley",
        "mid-location-id": 54,
        "mid-location-name": "British Columbia",
        "longitude": -125.0219451,
        "latitude": 49.70641879999999,
        "time-zone": "America/Vancouver"
      }
    },
    {
      "id": "428",
      "type": "sub-locations",
      "attributes": {
        "name": "fraser valley",
        "mid-location-id": 54,
        "mid-location-name": "British Columbia",
        "longitude": -121.8159307,
        "latitude": 49.3764104,
        "time-zone": "America/Vancouver"
      }
    }
  ],
  "links": {
    "self": "https://api.mycurrency.com/super_locations/2/sub_locations?per_page=10",
    "first": "https://api.mycurrency.com/super_locations/2/sub_locations?page=1&per_page=10",
    "prev": null,
    "next": "https://api.mycurrency.com/super_locations/2/sub_locations?page=2&per_page=10",
    "last": "https://api.mycurrency.com/super_locations/2/sub_locations?page=6&per_page=10"
  },
  "meta": {
    "pagination": {
      "per-page": "10",
      "total-pages": "6",
      "total-count": "55"
    }
  }
}
```

This endpoint retrieves all child sub locations of the specified super location.

### HTTP Request

`GET https://api.mycurrency.com/super_locations/<SUPER-LOCATION-ID>/sub_locations`

<aside class="notice">
Authentication: not required
</aside>

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the sub location
name | The name of the sub location
mid-location-id | The ID of the parent mid location
mid-location-name | The name of the parent mid location
longitude | The longitude of the sub location
latitude | The latitude of the sub location
time-zone | The time zone of the sub location

## List Nearby Sub Locations

```shell
curl 'https://api.mycurrency.com/nearby_locations/?ip_address=73.37.205.94' \
  -H 'Accept: application/json' -H 'Content-Type: application/json'
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": "196",
      "type": "sub-locations",
      "attributes": {
        "name": "minneapolis / st paul",
        "mid-location-id": 24,
        "mid-location-name": "Minnesota",
        "longitude": -93.20099979999999,
        "latitude": 44.9374831,
        "time-zone": "America/Chicago"
      }
    },
    {
      "id": "195",
      "type": "sub-locations",
      "attributes": {
        "name": "mankato",
        "mid-location-id": 24,
        "mid-location-name": "Minnesota",
        "longitude": -93.99939959999999,
        "latitude": 44.1635775,
        "time-zone": "America/Chicago"
      }
    },
    {
      "id": "199",
      "type": "sub-locations",
      "attributes": {
        "name": "st cloud",
        "mid-location-id": 24,
        "mid-location-name": "Minnesota",
        "longitude": -94.16324039999999,
        "latitude": 45.5579451,
        "time-zone": "America/Chicago"
      }
    },
    {
      "id": "197",
      "type": "sub-locations",
      "attributes": {
        "name": "rochester ",
        "mid-location-id": 24,
        "mid-location-name": "Minnesota",
        "longitude": -92.4801989,
        "latitude": 44.0121221,
        "time-zone": "America/Chicago"
      }
    },
    {
      "id": "405",
      "type": "sub-locations",
      "attributes": {
        "name": "eau claire",
        "mid-location-id": 50,
        "mid-location-name": "Wisconsin",
        "longitude": -91.4984941,
        "latitude": 44.811349,
        "time-zone": "America/Chicago"
      }
    }
  ]
}
```

This endpoint retrieves the five sub locations closest to the geolocation of the IP address provided.

### HTTP Request

`GET https://api.mycurrency.com/nearby_locations?ip_address={}`

<aside class="notice">
Authentication: not required
</aside>

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the sub location
name | The name of the sub location
mid-location-id | The ID of the parent mid location
mid-location-name | The name of the parent mid location
longitude | The longitude of the sub location
latitude | The latitude of the sub location
time-zone | The time zone of the sub location

# Orders

## Get an Order

```shell
curl 'https://api.mycurrency.com/order_sets/1' -H 'Accept: application/json' \
  -H 'Content-Type: application/json' -H 'Authorization: Bearer j47lbjj8r9n5yy8mup6cxqc8h70yvhnilm0g84kg0raqckus0k1koj9f75ao'
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "id": "1",
    "type": "micro-currency-orders",
    "attributes": {
      "store-id": 3,
      "store-name": "Freds Fishing Supplies",
      "order-set-id": 1,
      "source-currency-holding-id": 9,
      "source-currency-holding-type": "PrivateCurrencyHolding",
      "spent-currency-id": 5,
      "spent-currency-name": "Freds Fishing Supplies dollars",
      "before-amount-atomic": 510000000000,
      "after-amount-atomic": 410000000000,
      "burnrate-period-id": 20,
      "day-counter": 0,
      "amount-atomic": 100000000000,
      "product-id": 5,
      "product-name": "fishing bait",
      "product-image-url": "/system/products/images/000/000/005/original/fish_bait.jpg?1535342847",
      "product-quantity": 1,
      "product-sub-category-id": 28,
      "product-sub-category-id": "outdoor sporting goods",
      "created-at": "2018-10-03T00:39:37.860-07:00",
      "updated-at": "2018-10-03T00:39:37.860-07:00"
    }
  }
}
```

This endpoint retrieves a particular order. The logged in user must be active and be either the ordering user or the owner of the store that received the order to view it.

### HTTP Request

`GET https://api.mycurrency.com/order_sets/ID`

<aside class="notice">
Authentication: the request requires the OAuth access-token associated with the User referenced by the ID 
</aside>

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the micro currency order
store-id | The ID of the store that the micro currency order was spent at
store-name | The name of the store that the micro currency order was spent at
order-set-id | The ID of the order set that the micro currency order is associated with
ordering-user-id | The ID of the user that made the order, only shown if the logged in user is the owner of the store that received the order
ordering-user-name | The username of the user that made the order, only shown if the logged in user is the owner of the store that received the order
source-currency-holding-id | The ID of the public or private currency holding that the micro currency order spent from, only shown if the logged in user made the order
source-currency-holding-type | Whether the currency holding that the micro currency order spent from is a "PublicCurrencyHolding" or a "PrivateCurrencyHolding", only shown if the logged in user made the order
spent-currency-id | The ID of the currency spent
spent-currency-name | The name of the currency spent
before-amount-atomic | The balance, in atomic units, of the currency holding before it was debited by the micro currency order, only shown if the logged in user made the order
after-amount-atomic | The balance, in atomic units, of the currency holding after it was debited by the micro currency order, only shown if the logged in user made the order
burnrate-period-id | The ID of the burnrate period of the currency holding when it was debited by the micro currency order, only shown if the logged in user made the order 
day-counter | The day counter of the currency holding when it was debited by the micro currency order, only shown if the logged in user made the order
amount-atomic | The amount of currency spent, in atomic units (each whole unit is composed of 10^10 atomic units)
product-id | The ID of the product that was ordered
product-name | The name of the product that was ordered
product-image-url | The URL of the image of the product that was ordered 
product-quantity | The quantity of the product that was ordered
product-sub-category-id | The ID of the sub_category of the product that was ordered
product-sub-category-name | The name of the sub_category of the product that was ordered
created-at | The time and date when the micro currency order was created
updated-at | The time and date when the micro currency order was last updated

## List Orders

```shell
curl 'https://api.mycurrency.com/order_sets?ordering_user_id=3' \
  -H 'Accept: application/json' -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer j47lbjj8r9n5yy8mup6cxqc8h70yvhnilm0g84kg0raqckus0k1koj9f75ao'
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": "3",
      "type": "micro-currency-orders",
      "attributes": {
        "store-id": 3,
        "store-name": "Freds Fishing Supplies",
        "order-set-id": 3,
        "source-currency-holding-id": 9,
        "source-currency-holding-type": "PrivateCurrencyHolding",
        "spent-currency-id": 5,
        "spent-currency-name": "Freds Fishing Supplies dollars",
        "before-amount-atomic": 310000000000,
        "after-amount-atomic": 210000000000,
        "burnrate-period-id": 20,
        "day-counter": 0,
        "amount-atomic": 100000000000,
        "product-id": 7,
        "product-name": "fishing rod",
        "product-image-url": "/system/products/images/000/000/007/original/fish_rod.jpg?1535411381",
        "product-quantity": 1,
        "product-sub-category-id": 28,
        "product-sub-category-id": "outdoor sporting goods",
        "created-at": "2018-10-03T01:58:03.223-07:00",
        "updated-at": "2018-10-03T01:58:03.223-07:00"
      }
    },
    {
      "id": "2",
      "type": "micro-currency-orders",
      "attributes": {
        "store-id": 3,
        "store-name": "Freds Fishing Supplies",
        "order-set-id": 2,
        "source-currency-holding-id": 9,
        "source-currency-holding-type": "PrivateCurrencyHolding",
        "spent-currency-id": 5,
        "spent-currency-name": "Freds Fishing Supplies dollars",
        "before-amount-atomic": 410000000000,
        "after-amount-atomic": 310000000000,
        "burnrate-period-id": 20,
        "day-counter": 0,
        "amount-atomic": 100000000000,
        "product-id": 6,
        "product-name": "tackle",
        "product-image-url": "/system/products/images/000/000/006/original/tackle.jpg?1535101001",
        "product-quantity": 1,
        "product-sub-category-id": 28,
        "product-sub-category-id": "outdoor sporting goods",
        "created-at": "2018-10-03T00:43:31.756-07:00",
        "updated-at": "2018-10-03T00:43:31.756-07:00"
      }
    },
    {
      "id": "1",
      "type": "micro-currency-orders",
      "attributes": {
        "store-id": 3,
        "store-name": "Freds Fishing Supplies",
        "order-set-id": 1,
        "source-currency-holding-id": 9,
        "source-currency-holding-type": "PrivateCurrencyHolding",
        "spent-currency-id": 5,
        "spent-currency-name": "Freds Fishing Supplies dollars",
        "before-amount-atomic": 510000000000,
        "after-amount-atomic": 410000000000,
        "burnrate-period-id": 20,
        "day-counter": 0,
        "amount-atomic": 100000000000,
        "product-id": 5,
        "product-name": "fishing bait",
        "product-image-url": "/system/products/images/000/000/005/original/fish_bait.jpg?1535342847",
        "product-quantity": 1,
        "product-sub-category-id": 28,
        "product-sub-category-id": "outdoor sporting goods",
        "created-at": "2018-10-03T00:39:37.860-07:00",
        "updated-at": "2018-10-03T00:39:37.860-07:00"
      }
    }
  ],
  "links": {
    "self": "https://api.mycurrency.com/order_sets?ordering_user_id=3",
    "first": "https://api.mycurrency.com/order_sets?ordering_user_id=3&page=1&per_page=25",
    "prev": null,
    "next": null,
    "last": "https://api.mycurrency.com/order_sets?ordering_user_id=3&page=1&per_page=25"
  },
  "meta": {
    "pagination": {
      "per-page": null,
      "total-pages": "1",
      "total-count": "3"
    }
  }
}
```

This endpoint retrieves a user's orders sorted by created_at date, starting from the most recent

### HTTP Request

`GET https://api.mycurrency.com/order_sets?ordering_user_id={}`

OR

`GET https://api.mycurrency.com/order_sets?selling_user_id={}`

<aside class="notice">
Authentication: the request requires the OAuth access-token associated with the User referenced by the ID 
</aside>

### ARGUMENTS

Parameter | Type | Required | Description
--------- | ------- | ------- | -----------
user_id | integer | yes | The ID of the user creating the order, provided in URL path
ordering_user_id | integer | required if :selling_user_id not provided | The ID of the user that made the orders. If provided, the orders created by the specified user are returned.
selling_user_id | integer | required if :ordering_user_id not provided | The ID of the user that owns the stores that received the order. If provided, the orders received by the specified user are returned.
store_id | integer | no | The orders received by the specified store are returned if store_id is provided. This parameter needs to be provided along with a :selling_user_id with a value that matches the ID of the user that owns the store.

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the micro currency order
store-id | The ID of the store that the micro currency order was spent at
store-name | The name of the store that the micro currency order was spent at
order-set-id | The ID of the order set that the micro currency order is associated with
ordering-user-id | The ID of the user that made the order, only shown if the logged in user is the owner of the store that received the order
ordering-user-name | The username of the user that made the order, only shown if the logged in user is the owner of the store that received the order
source-currency-holding-id | The ID of the public or private currency holding that the micro currency order spent from, only shown if the logged in user made the order
source-currency-holding-type | Whether the currency holding that the micro currency order spent from is a "PublicCurrencyHolding" or a "PrivateCurrencyHolding", only shown if the logged in user made the order
spent-currency-id | The ID of the currency spent
spent-currency-name | The name of the currency spent
before-amount-atomic | The balance, in atomic units, of the currency holding before it was debited by the micro currency order, only shown if the logged in user made the order
after-amount-atomic | The balance, in atomic units, of the currency holding after it was debited by the micro currency order, only shown if the logged in user made the order
burnrate-period-id | The ID of the burnrate period of the currency holding when it was debited by the micro currency order, only shown if the logged in user made the order 
day-counter | The day counter of the currency holding when it was debited by the micro currency order, only shown if the logged in user made the order
amount-atomic | The amount of currency spent, in atomic units (each whole unit is composed of 10^10 atomic units)
product-id | The ID of the product that was ordered
product-name | The name of the product that was ordered
product-image-url | The URL of the image of the product that was ordered 
product-quantity | The quantity of the product that was ordered
product-sub-category-id | The ID of the sub_category of the product that was ordered
product-sub-category-name | The name of the sub_category of the product that was ordered
created-at | The time and date when the micro currency order was created
updated-at | The time and date when the micro currency order was last updated

## Create Order

```shell
curl -X POST https://api.mycurrency.com/users/3/order_sets \
  -d '{"order_set": { "micro_currency_orders_attributes": [{"product_id": "5", "micro_currency_seller_id": "3", "micro_order_source_currency_holding_id": "9", "micro_order_source_currency_holding_type": "PrivateCurrencyHolding", "amount_atomic": "100000000000", "product_quantity": "1"}]}}' \
  -H 'Authorization: Bearer j47lbjj8r9n5yy8mup6cxqc8h70yvhnilm0g84kg0raqckus0k1koj9f75ao' \
  -H 'Accept: application/json' -H 'Content-Type: application/json'
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "id": "1",
    "type": "micro-currency-orders",
    "attributes": {
      "store-id": 3,
      "store-name": "Freds Fishing Supplies",
      "order-set-id": 1,
      "source-currency-holding-id": 9,
      "source-currency-holding-type": "PrivateCurrencyHolding",
      "spent-currency-id": 5,
      "spent-currency-name": "Freds Fishing Supplies dollars",
      "before-amount-atomic": 510000000000,
      "after-amount-atomic": 410000000000,
      "burnrate-period-id": 20,
      "day-counter": 0,
      "amount-atomic": 100000000000,
      "product-id": 5,
      "product-name": "fishing bait",
      "product-image-url": "/system/products/images/000/000/005/original/fish_bait.jpg?1535342847",
      "product-quantity": 1,
      "product-sub-category-id": 28,
      "product-sub-category-id": "outdoor sporting goods",
      "created-at": "2018-10-03T00:39:37.860-07:00",
      "updated-at": "2018-10-03T00:39:37.860-07:00"
    }
  }
}
```

Creates an Order.

### HTTP Request

`https://api.mycurrency.com/users/<USER-ID>/order_sets`

<aside class="notice">
Authentication: the request requires the OAuth access-token associated with the User referenced by the ID 
</aside>

### ARGUMENTS

Parameter | Type | Required | Description
--------- | ------- | ------- | -----------
user_id | integer | yes | The ID of the user creating the order, provided in URL path
product_id | integer | yes | The ID of the product being ordered
micro_currency_seller_id | integer | yes | The ID of the store from which the product is being ordered
micro_order_currency_holding_id | integer | yes | The ID of the public or private currency holding that is being spent from
micro_order_currency_holding_type | string | yes | Whether the currency holding that is being spent from is a "PublicCurrencyHolding" or a "PrivateCurrencyHolding"
amount-atomic | integer | yes | The amount of currency spent, in atomic units (each whole unit is composed of 10^10 atomic units)
product-quantity | integer | yes | The quantity of the product that is being ordered

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the micro currency order
store-id | The ID of the store that the micro currency order was spent at
store-name | The name of the store that the micro currency order was spent at
order-set-id | The ID of the order set that the micro currency order is associated with
ordering-user-id | The ID of the user that made the order, only shown if the logged in user is the owner of the store that received the order
ordering-user-name | The username of the user that made the order, only shown if the logged in user is the owner of the store that received the order
source-currency-holding-id | The ID of the public or private currency holding that the micro currency order spent from, only shown if the logged in user made the order
source-currency-holding-type | Whether the currency holding that the micro currency order spent from is a "PublicCurrencyHolding" or a "PrivateCurrencyHolding", only shown if the logged in user made the order
spent-currency-id | The ID of the currency spent
spent-currency-name | The name of the currency spent
before-amount-atomic | The balance, in atomic units, of the currency holding before it was debited by the micro currency order, only shown if the logged in user made the order
after-amount-atomic | The balance, in atomic units, of the currency holding after it was debited by the micro currency order, only shown if the logged in user made the order
burnrate-period-id | The ID of the burnrate period of the currency holding when it was debited by the micro currency order, only shown if the logged in user made the order 
day-counter | The day counter of the currency holding when it was debited by the micro currency order, only shown if the logged in user made the order
amount-atomic | The amount of currency spent, in atomic units (each whole unit is composed of 10^10 atomic units)
product-id | The ID of the product that was ordered
product-name | The name of the product that was ordered
product-image-url | The URL of the image of the product that was ordered 
product-quantity | The quantity of the product that was ordered
product-sub-category-id | The ID of the sub_category of the product that was ordered
product-sub-category-name | The name of the sub_category of the product that was ordered
created-at | The time and date when the micro currency order was created
updated-at | The time and date when the micro currency order was last updated

# Notices

## Get a Notice

```shell
curl 'https://api.mycurrency.com/users/3/notices/35' \
  -H 'Accept: application/json' -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer j47lbjj8r9n5yy8mup6cxqc8h70yvhnilm0g84kg0raqckus0k1koj9f75ao'
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "id": "35",
    "type": "notices",
    "attributes": {
      "title": "You made an issuance to ScipioAfricanus",
      "message": "\nDetails of issuance:\n\nDate Issuance was made: Wednesday, October 10, 2018 at 04:33AM\n10.0000000000 macaroon dollars sent from Hannibal to the private holding of ScipioAfricanus",
      "seen": true,
      "read": false,
      "notice-type": 4,
      "user-id": 3
      "created-at": "2018-10-10T04:33:15.831-07:00",
      "updated-at": "2018-10-16T22:12:46.481-07:00",
    }
  }
}
```

This endpoint retrieves a particular notice. The logged in user must be active and must be the recipient of the notice to view it. Calling this endpoint also sets the :read attribute of the retrieved notice to TRUE

### HTTP Request

`GET https://api.mycurrency.com/users/<USER-ID>/notices/<ID>`

<aside class="notice">
Authentication: the request requires the OAuth access-token associated with the User referenced by the ID 
</aside>

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the notice
title | The title of the notice
message | The main body of the notice
seen | Whether the notice's title has been seen by the user or not
read | Whether the notice's message has been read by the user or not
notice-type | Whether the notice is of notice type 2 (offers), 3 (transfers), 4 (issuances), 5 (listings) or 6 (orders)
user-id | The ID of the user that the notice belongs to
created-at | The time and date when the notice was created
updated-at | The time and date when the notice was last updated

## Get Number of Unseen Notices

```shell
curl 'https://api.mycurrency.com/users/3/number_of_unseen_notices' \
  -H 'Accept: application/json' -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer j47lbjj8r9n5yy8mup6cxqc8h70yvhnilm0g84kg0raqckus0k1koj9f75ao'
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "type": "number-of-unseen-notices",
    "attributes": {
      "number-of-unseen-notices": 1
    }
  }
}
```

This endpoint retrieves the number of notices belonging to the specified user that have not been seen by the user.

### HTTP Request

`GET https://api.mycurrency.com/users/<USER-ID>/number_of_unseen_notices`

<aside class="notice">
Authentication: the request requires the OAuth access-token associated with the User referenced by the ID 
</aside>

### RESPONSE

Parameter | Description
--------- | -----------
number-of-unseen-notices | The number of unseen notices belonging to the user

## List Notices

```shell
curl 'https://api.mycurrency.com/users/3/notices?per_page=10' \
  -H 'Accept: application/json' -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer j47lbjj8r9n5yy8mup6cxqc8h70yvhnilm0g84kg0raqckus0k1koj9f75ao'
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": "29",
      "type": "notices",
      "attributes": {
        "title": "ScipioAfricanus ordered a product from your store, Asteroid Industries",
        "message": "\nDetails of order:\n\nDate Order was made: Friday, November 30, 2018 at 11:13PM\n1 mine 1 pound of X-group asteroid purchased by ScipioAfricanus from Asteroid Industries for 10000.0000000000 Micro Asteroid bucks",
        "seen": true,
        "read": false,
        "notice-type": 6,
        "user-id": 3,
        "created-at": "2018-11-30T23:13:41.215-08:00",
        "updated-at": "2018-12-05T04:59:41.744-08:00"
      }
    },
    {
      "id": "26",
      "type": "notices",
      "attributes": {
        "title": "You made an issuance to ScipioAfricanus",
        "message": "\nDetails of issuance:\n\nDate Issuance was made: Friday, November 30, 2018 at 11:04PM\n100000.0000000000 Micro Asteroid bucks sent from Hannibal to the private holding of ScipioAfricanus",
        "seen": true,
        "read": false,
        "notice-type": 4,
        "user-id": 3,
        "created-at": "2018-11-30T23:04:51.059-08:00",
        "updated-at": "2018-12-05T04:59:41.737-08:00"
      }
    },
    {
      "id": "25",
      "type": "notices",
      "attributes": {
        "title": "You received a transfer from ScipioAfricanus",
        "message": "\nDetails of transfer made:\n\nDate Transfer was made: Monday, November 05, 2018 at 06:29PM\n500.0000000000 Home Repair dollars sent from the private holding of ScipioAfricanus to the private holding of Hannibal",
        "seen": true,
        "read": false,
        "notice-type": 3,
        "user-id": 3,
        "created-at": "2018-11-05T18:29:51.630-08:00",
        "updated-at": "2018-12-05T04:59:41.730-08:00"
      }
    },
    {
      "id": "23",
      "type": "notices",
      "attributes": {
        "title": "You received an issuance from ScipioAfricanus",
        "message": "\nDetails of issuance:\n\nDate Issuance was made: Monday, November 05, 2018 at 06:28PM\n1000.0000000000 Wholesome foods tokens sent from ScipioAfricanus to the private holding of Hannibal",
        "seen": true,
        "read": false,
        "notice-type": 4,
        "user-id": 3,
        "created-at": "2018-11-05T18:28:14.593-08:00",
        "updated-at": "2018-12-05T04:59:41.723-08:00"
      }
    },
    {
      "id": "19",
      "type": "notices",
      "attributes": {
        "title": "You made a transfer to your account",
        "message": "\nDetails of transfer made:\n\nDate Transfer was made: Monday, November 05, 2018 at 11:15AM\n250.0000000000 spiderman pizza dollars sent from the private holding of Hannibal to the public holding of Hannibal",
        "seen": true,
        "read": false,
        "notice-type": 3,
        "user-id": 3,
        "created-at": "2018-11-05T11:15:33.244-08:00",
        "updated-at": "2018-12-05T04:59:41.716-08:00"
      }
    },
    {
      "id": "18",
      "type": "notices",
      "attributes": {
        "title": "You received a transfer from spiderman",
        "message": "\nDetails of transfer made:\n\nDate Transfer was made: Monday, November 05, 2018 at 11:12AM\n500.0000000000 spiderman pizza dollars sent from the private holding of spiderman to the private holding of Hannibal",
        "seen": true,
        "read": false,
        "notice-type": 3,
        "user-id": 3,
        "created-at": "2018-11-05T11:12:30.742-08:00",
        "updated-at": "2018-12-05T04:59:41.709-08:00"
      }
    },
    {
      "id": "12",
      "type": "notices",
      "attributes": {
        "title": "You made a transfer to your account",
        "message": "\nDetails of transfer made:\n\nDate Transfer was made: Monday, November 05, 2018 at 11:07AM\n500.0000000000 Moon hotel coins sent from the private holding of Hannibal to the public holding of Hannibal",
        "seen": true,
        "read": false,
        "notice-type": 3,
        "user-id": 3,
        "created-at": "2018-11-05T11:07:15.076-08:00",
        "updated-at": "2018-12-05T04:59:41.702-08:00"
      }
    },
    {
      "id": "11",
      "type": "notices",
      "attributes": {
        "title": "You received a transfer from ScipioAfricanus",
        "message": "\nDetails of transfer made:\n\nDate Transfer was made: Monday, November 05, 2018 at 11:05AM\n1000.0000000000 Moon hotel coins sent from the private holding of ScipioAfricanus to the private holding of Hannibal",
        "seen": true,
        "read": false,
        "notice-type": 3,
        "user-id": 3,
        "created-at": "2018-11-05T11:05:32.103-08:00",
        "updated-at": "2018-12-05T04:59:41.694-08:00"
      }
    },
    {
      "id": "7",
      "type": "notices",
      "attributes": {
        "title": "You made a transfer to your account",
        "message": "\nDetails of transfer made:\n\nDate Transfer was made: Monday, November 05, 2018 at 11:00AM\n10.0000000000 Micro Asteroid bucks sent from the private holding of Hannibal to the public holding of Hannibal",
        "seen": true,
        "read": false,
        "notice-type": 3,
        "user-id": 3,
        "created-at": "2018-11-05T11:00:13.494-08:00",
        "updated-at": "2018-12-05T04:59:41.687-08:00"
      }
    },
    {
      "id": "4",
      "type": "notices",
      "attributes": {
        "title": "You received a transfer from ScipioAfricanus",
        "message": "\nDetails of transfer made:\n\nDate Transfer was made: Monday, November 05, 2018 at 10:40AM\n1.0000000000 solar electricity zaps sent from the private holding of ScipioAfricanus to the private holding of Hannibal",
        "seen": true,
        "read": false,
        "notice-type": 3,
        "user-id": 3,
        "created-at": "2018-11-05T10:40:50.242-08:00",
        "updated-at": "2018-12-05T04:59:41.680-08:00"
      }
    }
  ],
  "links": {
    "self": "https://api.mycurrency.com/users/3/notices?per_page=10",
    "first": "https://api.mycurrency.com/users/3/notices?page=1&per_page=10",
    "prev": null,
    "next": "https://api.mycurrency.com/users/3/notices?page=2&per_page=10",
    "last": "https://api.mycurrency.com/users/3/notices?page=2&per_page=10"
  },
  "meta": {
    "pagination": {
      "per-page": "10",
      "total-pages": "2",
      "total-count": "11"
    }
  }
}
```

This endpoint retrieves all of a user's notices. Calling this endpoint also sets the :seen attribute of all retrieved notices to TRUE.

### HTTP Request

`GET https://api.mycurrency.com/users/<USER-ID>/notices`

<aside class="notice">
Authentication: the request requires the OAuth access-token associated with the User referenced by the ID 
</aside>

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the notice
title | The title of the notice
message | The main body of the notice
seen | Whether the notice's title has been seen by the user or not
read | Whether the notice's message has been read by the user or not
notice-type | Whether the notice is of notice type 2 (offers), 3 (transfers), 4 (issuances), 5 (listings) or 6 (orders)
user-id | The ID of the user that the notice belongs to
created-at | The time and date when the notice was created
updated-at | The time and date when the notice was last updated

## List Unread Notices

```shell
curl 'https://api.mycurrency.com/users/3/unread_notices?per_page=10' \
  -H 'Accept: application/json' -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer j47lbjj8r9n5yy8mup6cxqc8h70yvhnilm0g84kg0raqckus0k1koj9f75ao'
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": "29",
      "type": "notices",
      "attributes": {
        "title": "ScipioAfricanus ordered a product from your store, Asteroid Industries",
        "message": "\nDetails of order:\n\nDate Order was made: Friday, November 30, 2018 at 11:13PM\n1 mine 1 pound of X-group asteroid purchased by ScipioAfricanus from Asteroid Industries for 10000.0000000000 Micro Asteroid bucks",
        "seen": true,
        "read": false,
        "notice-type": 6,
        "user-id": 3,
        "created-at": "2018-11-30T23:13:41.215-08:00",
        "updated-at": "2018-12-05T04:59:41.744-08:00"
      }
    },
    {
      "id": "26",
      "type": "notices",
      "attributes": {
        "title": "You made an issuance to ScipioAfricanus",
        "message": "\nDetails of issuance:\n\nDate Issuance was made: Friday, November 30, 2018 at 11:04PM\n100000.0000000000 Micro Asteroid bucks sent from Hannibal to the private holding of ScipioAfricanus",
        "seen": true,
        "read": false,
        "notice-type": 4,
        "user-id": 3,
        "created-at": "2018-11-30T23:04:51.059-08:00",
        "updated-at": "2018-12-05T04:59:41.737-08:00"
      }
    },
    {
      "id": "25",
      "type": "notices",
      "attributes": {
        "title": "You received a transfer from ScipioAfricanus",
        "message": "\nDetails of transfer made:\n\nDate Transfer was made: Monday, November 05, 2018 at 06:29PM\n500.0000000000 Home Repair dollars sent from the private holding of ScipioAfricanus to the private holding of Hannibal",
        "seen": true,
        "read": false,
        "notice-type": 3,
        "user-id": 3,
        "created-at": "2018-11-05T18:29:51.630-08:00",
        "updated-at": "2018-12-05T04:59:41.730-08:00"
      }
    },
    {
      "id": "23",
      "type": "notices",
      "attributes": {
        "title": "You received an issuance from ScipioAfricanus",
        "message": "\nDetails of issuance:\n\nDate Issuance was made: Monday, November 05, 2018 at 06:28PM\n1000.0000000000 Wholesome foods tokens sent from ScipioAfricanus to the private holding of Hannibal",
        "seen": true,
        "read": false,
        "notice-type": 4,
        "user-id": 3,
        "created-at": "2018-11-05T18:28:14.593-08:00",
        "updated-at": "2018-12-05T04:59:41.723-08:00"
      }
    },
    {
      "id": "19",
      "type": "notices",
      "attributes": {
        "title": "You made a transfer to your account",
        "message": "\nDetails of transfer made:\n\nDate Transfer was made: Monday, November 05, 2018 at 11:15AM\n250.0000000000 spiderman pizza dollars sent from the private holding of Hannibal to the public holding of Hannibal",
        "seen": true,
        "read": false,
        "notice-type": 3,
        "user-id": 3,
        "created-at": "2018-11-05T11:15:33.244-08:00",
        "updated-at": "2018-12-05T04:59:41.716-08:00"
      }
    },
    {
      "id": "18",
      "type": "notices",
      "attributes": {
        "title": "You received a transfer from spiderman",
        "message": "\nDetails of transfer made:\n\nDate Transfer was made: Monday, November 05, 2018 at 11:12AM\n500.0000000000 spiderman pizza dollars sent from the private holding of spiderman to the private holding of Hannibal",
        "seen": true,
        "read": false,
        "notice-type": 3,
        "user-id": 3,
        "created-at": "2018-11-05T11:12:30.742-08:00",
        "updated-at": "2018-12-05T04:59:41.709-08:00"
      }
    },
    {
      "id": "12",
      "type": "notices",
      "attributes": {
        "title": "You made a transfer to your account",
        "message": "\nDetails of transfer made:\n\nDate Transfer was made: Monday, November 05, 2018 at 11:07AM\n500.0000000000 Moon hotel coins sent from the private holding of Hannibal to the public holding of Hannibal",
        "seen": true,
        "read": false,
        "notice-type": 3,
        "user-id": 3,
        "created-at": "2018-11-05T11:07:15.076-08:00",
        "updated-at": "2018-12-05T04:59:41.702-08:00"
      }
    },
    {
      "id": "11",
      "type": "notices",
      "attributes": {
        "title": "You received a transfer from ScipioAfricanus",
        "message": "\nDetails of transfer made:\n\nDate Transfer was made: Monday, November 05, 2018 at 11:05AM\n1000.0000000000 Moon hotel coins sent from the private holding of ScipioAfricanus to the private holding of Hannibal",
        "seen": true,
        "read": false,
        "notice-type": 3,
        "user-id": 3,
        "created-at": "2018-11-05T11:05:32.103-08:00",
        "updated-at": "2018-12-05T04:59:41.694-08:00"
      }
    },
    {
      "id": "7",
      "type": "notices",
      "attributes": {
        "title": "You made a transfer to your account",
        "message": "\nDetails of transfer made:\n\nDate Transfer was made: Monday, November 05, 2018 at 11:00AM\n10.0000000000 Micro Asteroid bucks sent from the private holding of Hannibal to the public holding of Hannibal",
        "seen": true,
        "read": false,
        "notice-type": 3,
        "user-id": 3,
        "created-at": "2018-11-05T11:00:13.494-08:00",
        "updated-at": "2018-12-05T04:59:41.687-08:00"
      }
    },
    {
      "id": "4",
      "type": "notices",
      "attributes": {
        "title": "You received a transfer from ScipioAfricanus",
        "message": "\nDetails of transfer made:\n\nDate Transfer was made: Monday, November 05, 2018 at 10:40AM\n1.0000000000 solar electricity zaps sent from the private holding of ScipioAfricanus to the private holding of Hannibal",
        "seen": true,
        "read": false,
        "notice-type": 3,
        "user-id": 3,
        "created-at": "2018-11-05T10:40:50.242-08:00",
        "updated-at": "2018-12-05T04:59:41.680-08:00"
      }
    }
  ],
  "links": {
    "self": "https://api.mycurrency.com/users/3/unread_notices?per_page=10",
    "first": "https://api.mycurrency.com/users/3/unread_notices?page=1&per_page=10",
    "prev": null,
    "next": "https://api.mycurrency.com/users/3/unread_notices?page=2&per_page=10",
    "last": "https://api.mycurrency.com/users/3/unread_notices?page=2&per_page=10"
  },
  "meta": {
    "pagination": {
      "per-page": "10",
      "total-pages": "2",
      "total-count": "11"
    }
  }
}
```

This endpoint retrieves all of a user's unread notices. Calling this endpoint also sets the :seen attribute of all retrieved notices to TRUE.

### HTTP Request

`GET https://api.mycurrency.com/users/<USER-ID>/unread_notices`

<aside class="notice">
Authentication: the request requires the OAuth access-token associated with the User referenced by the ID 
</aside>

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the notice
title | The title of the notice
message | The main body of the notice
seen | Whether the notice's title has been seen by the user or not
read | Whether the notice's message has been read by the user or not
notice-type | Whether the notice is of notice type 2 (offers), 3 (transfers), 4 (issuances), 5 (listings) or 6 (orders)
user-id | The ID of the user that the notice belongs to
created-at | The time and date when the notice was created
updated-at | The time and date when the notice was last updated

## List Recent Unread Notices

```shell
curl 'https://api.mycurrency.com/users/3/recent_unread_notices?per_page=10' \
  -H 'Accept: application/json' -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer j47lbjj8r9n5yy8mup6cxqc8h70yvhnilm0g84kg0raqckus0k1koj9f75ao'
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": "29",
      "type": "notices",
      "attributes": {
        "title": "ScipioAfricanus ordered a product from your store, Asteroid Industries",
        "message": "\nDetails of order:\n\nDate Order was made: Friday, November 30, 2018 at 11:13PM\n1 mine 1 pound of X-group asteroid purchased by ScipioAfricanus from Asteroid Industries for 10000.0000000000 Micro Asteroid bucks",
        "seen": true,
        "read": false,
        "notice-type": 6,
        "user-id": 3,
        "created-at": "2018-11-30T23:13:41.215-08:00",
        "updated-at": "2018-12-05T04:59:41.744-08:00"
      }
    },
    {
      "id": "26",
      "type": "notices",
      "attributes": {
        "title": "You made an issuance to ScipioAfricanus",
        "message": "\nDetails of issuance:\n\nDate Issuance was made: Friday, November 30, 2018 at 11:04PM\n100000.0000000000 Micro Asteroid bucks sent from Hannibal to the private holding of ScipioAfricanus",
        "seen": true,
        "read": false,
        "notice-type": 4,
        "user-id": 3,
        "created-at": "2018-11-30T23:04:51.059-08:00",
        "updated-at": "2018-12-05T04:59:41.737-08:00"
      }
    }
  ],
  "links": {
    "self": "https://api.mycurrency.com/users/3/recent_unread_notices?per_page=10",
    "first": "https://api.mycurrency.com/users/3/recent_unread_notices?page=1&per_page=10",
    "prev": null,
    "next": null,
    "last": "https://api.mycurrency.com/users/3/recent_unread_notices?page=1&per_page=10"
  },
  "meta": {
    "pagination": {
      "per-page": "10",
      "total-pages": "1",
      "total-count": "2"
    }
  }
}
```

This endpoint retrieves all of a user's unread notices that are less than 30 days old. Calling this endpoint also sets the :seen attribute of all retrieved notices to TRUE.

### HTTP Request

`GET https://api.mycurrency.com/users/<USER-ID>/recent_unread_notices`

<aside class="notice">
Authentication: the request requires the OAuth access-token associated with the User referenced by the ID 
</aside>

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the notice
title | The title of the notice
message | The main body of the notice
seen | Whether the notice's title has been seen by the user or not
read | Whether the notice's message has been read by the user or not
notice-type | Whether the notice is of notice type 2 (offers), 3 (transfers), 4 (issuances), 5 (listings) or 6 (orders)
user-id | The ID of the user that the notice belongs to
created-at | The time and date when the notice was created
updated-at | The time and date when the notice was last updated

## Update Notice

```shell
curl -X PUT 'https://api.mycurrency.com/users/3/notices/35' \
  -d '{"notice": { "read": false } }' -H 'Accept: application/json' \
  -H 'Content-Type: application/json' -H 'Authorization: Bearer j47lbjj8r9n5yy8mup6cxqc8h70yvhnilm0g84kg0raqckus0k1koj9f75ao'
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "id": "35",
    "type": "notices",
    "attributes": {
      "title": "You made an issuance to ScipioAfricanus",
      "message": "\nDetails of issuance:\n\nDate Issuance was made: Wednesday, October 10, 2018 at 04:33AM\n10.0000000000 macaroon dollars sent from Hannibal to the private holding of ScipioAfricanus",
      "seen": true,
      "read": false,
      "notice-type": 4,
      "user-id": 3,
      "created-at": "2018-10-10T04:33:15.831-07:00",
      "updated-at": "2018-10-19T02:21:30.073-07:00"
    }
  }
}
```

Updates a notice.

### HTTP Request

`POST https://api.mycurrency.com/users/<USER-ID>/notices/<ID>`

<aside class="notice">
Authentication: the request requires the OAuth access-token associated with the User referenced by the ID 
</aside>

### ARGUMENTS

Parameter | Type | Required | Description
--------- | ------- | ------- | -----------
read | boolean | yes | Whether the notice's message has been read by the user or not

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the notice
title | The title of the notice
message | The main body of the notice
seen | Whether the notice's title has been seen by the user or not
read | Whether the notice's message has been read by the user or not
notice-type | Whether the notice is of notice type 2 (offers), 3 (transfers), 4 (issuances), 5 (listings) or 6 (orders)
user-id | The ID of the user that the notice belongs to
created-at | The time and date when the notice was created
updated-at | The time and date when the notice was last updated

# Vouchers

## Get a Voucher

```shell
curl 'https://api.mycurrency.com/vouchers/3' \
  -H 'Accept: application/json' -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer j47lbjj8r9n5yy8mup6cxqc8h70yvhnilm0g84kg0raqckus0k1koj9f75ao'
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "id": "3",
    "type": "vouchers",
    "attributes": {
      "micro-currency-order-id": 3,
      "holding-user-id": 21,
      "holding-user-username": "deleted_user",
      "holding-user-avatar-url": "/avatars/original/missing.png",
      "product-id": 1,
      "product-name": "mine 1 pound of X-group asteroid",
      "product-image-url": "/system/products/images/original/missing.png",
      "product-sub-category-id": 57,
      "product-sub-category-name": "general labor",
      "product-quantity": 1,
      "store-id": 1,
      "store-name": "Asteroid Industries",
      "expiration": "2019-08-22T17:25:56.353-07:00",
      "redeemed": false,
      "created-at": "2019-07-23T17:25:56.398-07:00",
      "updated-at": "2019-07-23T17:25:56.398-07:00"
    }
  }
}
```

This endpoint retrieves a particular voucher. The logged in user must be either the holder of the voucher or the owner of the store at which the voucher is redeemable in order to view the voucher's details.

### HTTP Request

`GET https://api.mycurrency.com/vouchers/<ID>`

<aside class="notice">
Authentication: the request requires the OAuth access-token associated with the User that issued the voucher or the user that holds it
</aside>

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the voucher
micro-currency-order-id | The ID of the micro currency order that purchased the voucher
holding-user-id | The ID of the user that purchased the voucher
holding-user-username | The username of the user that purchased the voucher
holding-user-avatar-url | The URL of the avatar of the user that purchased the voucher
product-id | The ID of the product for which the voucher is redeemable for
product-name | The name of the product for which the voucher is redeemable for
product-image-url | The URL of the image of the product for which the voucher is redeemable for
product-sub-category-id | The ID of the sub_category that the product for which the voucher is redeemable for belongs to
product-sub-category-name | The name of the sub_category that the product for which the voucher is redeemable for belongs to
product-quantity | The quantity of the product for which the voucher is redeemable for
store-id | The ID of the store at which the product that the voucher can be redeemed for is sold at
store-name | The name of the store at which the product that the voucher can be redeemed for is sold at
code | The secret code that the voucher holder must reveal to the store owner in order to redeem their voucher, only shown if the logged-in user is the voucher holder
expiration | The date at which the voucher expires, which is one month after it is issued to the buyer
redeemed | Whether the voucher has been redeemed or not
created-at | The time and date when the voucher was created
updated-at | The time and date when the voucher was last updated

## Get an Order's Voucher

```shell
curl 'https://api.mycurrency.com/order_sets/3/associated_voucher' \
  -H 'Accept: application/json' -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer j47lbjj8r9n5yy8mup6cxqc8h70yvhnilm0g84kg0raqckus0k1koj9f75ao'
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "id": "3",
    "type": "vouchers",
    "attributes": {
      "micro-currency-order-id": 3,
      "holding-user-id": 21,
      "holding-user-username": "deleted_user",
      "holding-user-avatar-url": "/avatars/original/missing.png",
      "product-id": 1,
      "product-name": "mine 1 pound of X-group asteroid",
      "product-image-url": "/system/products/images/original/missing.png",
      "product-sub-category-id": 57,
      "product-sub-category-name": "general labor",
      "product-quantity": 1,
      "store-id": 1,
      "store-name": "Asteroid Industries",
      "expiration": "2019-08-22T17:25:56.353-07:00",
      "redeemed": false,
      "created-at": "2019-07-23T17:25:56.398-07:00",
      "updated-at": "2019-07-23T17:25:56.398-07:00"
    }
  }
}
```

This endpoint retrieves the voucher associated with a particular order. The logged in user must be either the holder of the voucher or the owner of the store at which the voucher is redeemable in order to view the voucher's details.

### HTTP Request

`GET https://api.mycurrency.com/order_sets/<ORDER-SET-ID>/associated_voucher`

<aside class="notice">
Authentication: the request requires the OAuth access-token associated with the User that issued the voucher or the user that holds it
</aside>

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the voucher
micro-currency-order-id | The ID of the micro currency order that purchased the voucher
holding-user-id | The ID of the user that purchased the voucher
holding-user-username | The username of the user that purchased the voucher
holding-user-avatar-url | The URL of the avatar of the user that purchased the voucher
product-id | The ID of the product for which the voucher is redeemable for
product-name | The name of the product for which the voucher is redeemable for
product-image-url | The URL of the image of the product for which the voucher is redeemable for
product-sub-category-id | The ID of the sub_category that the product for which the voucher is redeemable for belongs to
product-sub-category-name | The name of the sub_category that the product for which the voucher is redeemable for belongs to
product-quantity | The quantity of the product for which the voucher is redeemable for
store-id | The ID of the store at which the product that the voucher can be redeemed for is sold at
store-name | The name of the store at which the product that the voucher can be redeemed for is sold at
code | The secret code that the voucher holder must reveal to the store owner in order to redeem their voucher, only shown if the logged-in user is the voucher holder
expiration | The date at which the voucher expires, which is one month after it is issued to the buyer
redeemed | Whether the voucher has been redeemed or not
created-at | The time and date when the voucher was created
updated-at | The time and date when the voucher was last updated

## List Vouchers

```shell
curl 'https://api.mycurrency.com/vouchers?holding_user_id=3' \
  -H 'Accept: application/json' -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer j47lbjj8r9n5yy8mup6cxqc8h70yvhnilm0g84kg0raqckus0k1koj9f75ao'
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": "12",
      "type": "vouchers",
      "attributes": {
        "micro-currency-order-id": 12,
        "holding-user-id": 3,
        "holding-user-username": "Hannibal",
        "holding-user-avatar-url": "/system/users/avatars/000/000/004/original/1.jpg?1559736060",
        "product-id": 52,
        "product-name": "spidermask",
        "product-image-url": "/system/products/images/original/missing.png",
        "product-sub-category-id": 20,
        "product-sub-category-name": "kid's clothing",
        "product-quantity": 1,
        "store-id": 29,
        "store-name": "Spiderman store",
        "code": "J575ECXNWAPDN8X8U0WBI",
        "expiration": "2019-09-12T04:43:46.827-07:00",
        "redeemed": false,
        "created-at": "2019-08-13T04:43:46.847-07:00",
        "updated-at": "2019-08-13T04:43:46.847-07:00"
      }
    },
    {
      "id": "11",
      "type": "vouchers",
      "attributes": {
        "micro-currency-order-id": 11,
        "holding-user-id": 3,
        "holding-user-username": "Hannibal",
        "holding-user-avatar-url": "/system/users/avatars/000/000/004/original/1.jpg?1559736060",
        "product-id": 52,
        "product-name": "spidermask",
        "product-image-url": "/system/products/images/original/missing.png",
        "product-sub-category-id": 20,
        "product-sub-category-name": "kid's clothing",
        "product-quantity": 1,
        "store-id": 29,
        "store-name": "Spiderman store",
        "code": "0X4ULLIO08A28MXMLJLSX",
        "expiration": "2019-09-12T04:43:16.819-07:00",
        "redeemed": false,
        "created-at": "2019-08-13T04:43:16.873-07:00",
        "updated-at": "2019-08-13T04:43:16.873-07:00"
      }
    },
    {
      "id": "10",
      "type": "vouchers",
      "attributes": {
        "micro-currency-order-id": 10,
        "holding-user-id": 3,
        "holding-user-username": "Hannibal",
        "holding-user-avatar-url": "/system/users/avatars/000/000/004/original/1.jpg?1559736060",
        "product-id": 52,
        "product-name": "spidermask",
        "product-image-url": "/system/products/images/original/missing.png",
        "product-sub-category-id": 20,
        "product-sub-category-name": "kid's clothing",
        "product-quantity": 1,
        "store-id": 29,
        "store-name": "Spiderman store",
        "code": "OYY48JWD47XSS1AVCS7WJ",
        "expiration": "2019-09-12T03:53:08.267-07:00",
        "redeemed": false,
        "created-at": "2019-08-13T03:53:08.727-07:00",
        "updated-at": "2019-08-13T03:53:08.727-07:00"
      }
    },
    {
      "id": "9",
      "type": "vouchers",
      "attributes": {
        "micro-currency-order-id": 9,
        "holding-user-id": 3,
        "holding-user-username": "Hannibal",
        "holding-user-avatar-url": "/system/users/avatars/000/000/004/original/1.jpg?1559736060",
        "product-id": 52,
        "product-name": "spidermask",
        "product-image-url": "/system/products/images/original/missing.png",
        "product-sub-category-id": 20,
        "product-sub-category-name": "kid's clothing",
        "product-quantity": 1,
        "store-id": 29,
        "store-name": "Spiderman store",
        "code": "COX1CTO6Q4R3EOJICBRPU",
        "expiration": "2019-09-12T03:51:28.943-07:00",
        "redeemed": false,
        "created-at": "2019-08-13T03:51:28.962-07:00",
        "updated-at": "2019-08-13T03:51:28.962-07:00"
      }
    },
    {
      "id": "8",
      "type": "vouchers",
      "attributes": {
        "micro-currency-order-id": 8,
        "holding-user-id": 3,
        "holding-user-username": "Hannibal",
        "holding-user-avatar-url": "/system/users/avatars/000/000/004/original/1.jpg?1559736060",
        "product-id": 52,
        "product-name": "spidermask",
        "product-image-url": "/system/products/images/original/missing.png",
        "product-sub-category-id": 20,
        "product-sub-category-name": "kid's clothing",
        "product-quantity": 1,
        "store-id": 29,
        "store-name": "Spiderman store",
        "code": "83LMETZC9EH4JW5H2X84B",
        "expiration": "2019-09-12T03:51:19.317-07:00",
        "redeemed": false,
        "created-at": "2019-08-13T03:51:19.403-07:00",
        "updated-at": "2019-08-13T03:51:19.403-07:00"
      }
    },
    {
      "id": "7",
      "type": "vouchers",
      "attributes": {
        "micro-currency-order-id": 7,
        "holding-user-id": 3,
        "holding-user-username": "Hannibal",
        "holding-user-avatar-url": "/system/users/avatars/000/000/004/original/1.jpg?1559736060",
        "product-id": 52,
        "product-name": "spidermask",
        "product-image-url": "/system/products/images/original/missing.png",
        "product-sub-category-id": 20,
        "product-sub-category-name": "kid's clothing",
        "product-quantity": 1,
        "store-id": 29,
        "store-name": "Spiderman store",
        "code": "D1BTR6J6U2BYCIOXTDLI0",
        "expiration": "2019-09-12T03:48:39.248-07:00",
        "redeemed": false,
        "created-at": "2019-08-13T03:48:39.296-07:00",
        "updated-at": "2019-08-13T03:48:39.296-07:00"
      }
    },
    {
      "id": "6",
      "type": "vouchers",
      "attributes": {
        "micro-currency-order-id": 6,
        "holding-user-id": 3,
        "holding-user-username": "Hannibal",
        "holding-user-avatar-url": "/system/users/avatars/000/000/004/original/1.jpg?1559736060",
        "product-id": 52,
        "product-name": "spidermask",
        "product-image-url": "/system/products/images/original/missing.png",
        "product-sub-category-id": 20,
        "product-sub-category-name": "kid's clothing",
        "product-quantity": 1,
        "store-id": 29,
        "store-name": "Spiderman store",
        "code": "W7DAAYDDUZXEH8I6C3R97",
        "expiration": "2019-09-12T03:45:16.287-07:00",
        "redeemed": false,
        "created-at": "2019-08-13T03:45:16.390-07:00",
        "updated-at": "2019-08-13T03:45:16.390-07:00"
      }
    },
    {
      "id": "5",
      "type": "vouchers",
      "attributes": {
        "micro-currency-order-id": 5,
        "holding-user-id": 3,
        "holding-user-username": "Hannibal",
        "holding-user-avatar-url": "/system/users/avatars/000/000/004/original/1.jpg?1559736060",
        "product-id": 52,
        "product-name": "spidermask",
        "product-image-url": "/system/products/images/original/missing.png",
        "product-sub-category-id": 20,
        "product-sub-category-name": "kid's clothing",
        "product-quantity": 1,
        "store-id": 29,
        "store-name": "Spiderman store",
        "code": "6LO8OA821UWY8RX1XPN10",
        "expiration": "2019-09-12T03:27:55.950-07:00",
        "redeemed": false,
        "created-at": "2019-08-13T03:27:56.075-07:00",
        "updated-at": "2019-08-13T03:27:56.075-07:00"
      }
    },
    {
      "id": "4",
      "type": "vouchers",
      "attributes": {
        "micro-currency-order-id": 4,
        "holding-user-id": 3,
        "holding-user-username": "Hannibal",
        "holding-user-avatar-url": "/system/users/avatars/000/000/004/original/1.jpg?1559736060",
        "product-id": 52,
        "product-name": "spidermask",
        "product-image-url": "/system/products/images/original/missing.png",
        "product-sub-category-id": 20,
        "product-sub-category-name": "kid's clothing",
        "product-quantity": 1,
        "store-id": 29,
        "store-name": "Spiderman store",
        "code": "EQ2O4NVCOJ91KDKW0EZQW",
        "expiration": "2019-09-12T02:21:58.436-07:00",
        "redeemed": false,
        "created-at": "2019-08-13T02:21:58.501-07:00",
        "updated-at": "2019-08-13T02:21:58.501-07:00"
      }
    }
  ],
  "links": {
    "self": "https://api.mycurrency.com/vouchers?holding_user_id=3",
    "first": "https://api.mycurrency.com/vouchers?holding_user_id=3&page=1&per_page=25",
    "prev": null,
    "next": null,
    "last": "https://api.mycurrency.com/vouchers?holding_user_id=3&page=1&per_page=25"
  },
  "meta": {
    "pagination": {
      "per-page": null,
      "total-pages": "1",
      "total-count": "9"
    }
  }
}
```

This endpoint retrieves a user's vouchers. 

### HTTP Request

`GET https://api.mycurrency.com/vouchers?issueing_user_id={}&store_id={}`

<aside class="notice">
Authentication: the request requires the OAuth access-token associated with the User referenced by the ID 
</aside>

### ARGUMENTS

Parameter | Type | Required | Description
--------- | ------- | ------- | -----------
holding_user_id | integer | required if :issueing_user_id not provided | The ID of the user that purchased the vouchers. If provided, the vouchers purchased by the logged-in are returned.
issueing_user_id | integer | required if :holding_user_id not provided | The ID of the user that owns the stores that issued the vouchers. If provided, the vouchers issued by the stored owned by the specified user are returned.
store_id | integer | no | The vouchers issued by the specified store are returned if store_id is provided. This parameter needs to be provided along with a :issueing_user_id with a value that matches the ID of the user that owns the store.

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the voucher
micro-currency-order-id | The ID of the micro currency order that purchased the voucher
holding-user-id | The ID of the user that purchased the voucher
holding-user-username | The username of the user that purchased the voucher
holding-user-avatar-url | The URL of the avatar of the user that purchased the voucher
product-id | The ID of the product for which the voucher is redeemable for
product-name | The name of the product for which the voucher is redeemable for
product-image-url | The URL of the image of the product for which the voucher is redeemable for
product-sub-category-id | The ID of the sub_category that the product for which the voucher is redeemable for belongs to
product-sub-category-name | The name of the sub_category that the product for which the voucher is redeemable for belongs to
product-quantity | The quantity of the product for which the voucher is redeemable for
store-id | The ID of the store at which the product that the voucher can be redeemed for is sold at
store-name | The name of the store at which the product that the voucher can be redeemed for is sold at
code | The secret code that the voucher holder must reveal to the store owner in order to redeem their voucher, only shown if the logged-in user is the voucher holder
expiration | The date at which the voucher expires, which is one month after it is issued to the buyer
redeemed | Whether the voucher has been redeemed or not
created-at | The time and date when the voucher was created
updated-at | The time and date when the voucher was last updated

## List Product's Vouchers

```shell
curl 'https://api.mycurrency.com/products/55/product_vouchers' \
  -H 'Accept: application/json' -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer j47lbjj8r9n5yy8mup6cxqc8h70yvhnilm0g84kg0raqckus0k1koj9f75ao'
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": "27",
      "type": "vouchers",
      "attributes": {
        "micro-currency-order-id": 27,
        "holding-user-id": 2,
        "holding-user-username": "Spiderman",
        "holding-user-avatar-url": "/system/users/avatars/000/000/002/original/avatar.jpg?1568543223",
        "product-id": 55,
        "product-name": "coke",
        "product-image-url": "/system/products/images/original/missing.png",
        "product-sub-category-id": 16,
        "product-sub-category-name": "prepared food",
        "product-quantity": 1,
        "store-id": 59,
        "store-name": "ACME Toon Cafe",
        "code": "CDYZAAUGJII5PTS2SE1UN",
        "expiration": "2020-03-26T02:29:22.854-07:00",
        "redeemed": true,
        "created-at": "2020-02-25T01:29:23.027-08:00",
        "updated-at": "2020-02-25T01:30:29.335-08:00"
      }
    },
    {
      "id": "20",
      "type": "vouchers",
      "attributes": {
        "micro-currency-order-id": 20,
        "holding-user-id": 2,
        "holding-user-username": "Spiderman",
        "holding-user-avatar-url": "/system/users/avatars/000/000/002/original/avatar.jpg?1568543223",
        "product-id": 55,
        "product-name": "coke",
        "product-image-url": "/system/products/images/original/missing.png",
        "product-sub-category-id": 16,
        "product-sub-category-name": "prepared food",
        "product-quantity": 1,
        "store-id": 59,
        "store-name": "ACME Toon Cafe",
        "code": "XXFXLWD5GCP2YSW1FEXQU",
        "expiration": "2020-03-19T01:57:05.274-07:00",
        "redeemed": true,
        "created-at": "2020-02-18T00:57:05.481-08:00",
        "updated-at": "2020-02-18T00:57:36.499-08:00"
      }
    }
  ],
  "links": {
    "self": "https://api.mycurrency.com/products/55/product_vouchers?",
    "first": "https://api.mycurrency.com/products/55/product_vouchers?page=1&per_page=25",
    "prev": null,
    "next": null,
    "last": "https://api.mycurrency.com/products/55/product_vouchers?page=1&per_page=25"
  }
}
```

This endpoint retrieves vouchers for the specified product. If the logged in user owns the store that the product belongs to, they will see all vouchers issued for that product. If the logged in user does not own the store that the product belongs to, they will only see the vouchers for that product that were issued to them. 

### HTTP Request

`GET https://api.mycurrency.com/products/<PRODUCT-ID>/product_vouchers`

<aside class="notice">
Authentication: required
</aside>

### ARGUMENTS

Parameter | Type | Required | Description
--------- | ------- | ------- | -----------
product_id | integer | yes | The ID of the product that the vouchers are returned for, provided in URL path.

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the voucher
micro-currency-order-id | The ID of the micro currency order that purchased the voucher
holding-user-id | The ID of the user that purchased the voucher
holding-user-username | The username of the user that purchased the voucher
holding-user-avatar-url | The URL of the avatar of the user that purchased the voucher
product-id | The ID of the product for which the voucher is redeemable for
product-name | The name of the product for which the voucher is redeemable for
product-image-url | The URL of the image of the product for which the voucher is redeemable for
product-sub-category-id | The ID of the sub_category that the product for which the voucher is redeemable for belongs to
product-sub-category-name | The name of the sub_category that the product for which the voucher is redeemable for belongs to
product-quantity | The quantity of the product for which the voucher is redeemable for
store-id | The ID of the store at which the product that the voucher can be redeemed for is sold at
store-name | The name of the store at which the product that the voucher can be redeemed for is sold at
code | The secret code that the voucher holder must reveal to the store owner in order to redeem their voucher, only shown if the logged-in user is the voucher holder
expiration | The date at which the voucher expires, which is one month after it is issued to the buyer
redeemed | Whether the voucher has been redeemed or not
created-at | The time and date when the voucher was created
updated-at | The time and date when the voucher was last updated

## Update Voucher

```shell
curl -X PUT 'https://api.mycurrency.com/users/3/vouchers/1' \
  -d '{"voucher": { "redeemed": true, "code": "NQG05A1DGHC1ATZ0PLM5B" } }' \
  -H 'Accept: application/json' -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer j47lbjj8r9n5yy8mup6cxqc8h70yvhnilm0g84kg0raqckus0k1koj9f75ao'
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "id": "3",
    "type": "vouchers",
    "attributes": {
      "micro-currency-order-id": 3,
      "holding-user-id": 21,
      "holding-user-username": "deleted_user",
      "holding-user-avatar-url": "/avatars/original/missing.png",
      "product-id": 1,
      "product-name": "mine 1 pound of X-group asteroid",
      "product-image-url": "/system/products/images/original/missing.png",
      "product-sub-category-id": 57,
      "product-sub-category-name": "general labor",
      "product-quantity": 1,
      "store-id": 1,
      "store-name": "Asteroid Industries",
      "expiration": "2019-08-22T17:25:56.353-07:00",
      "redeemed": true,
      "created-at": "2019-07-23T17:25:56.398-07:00",
      "updated-at": "2019-07-23T17:25:56.398-07:00"
    }
  }
}
```

Updates a voucher.

### HTTP Request

`POST https://api.mycurrency.com/users/<USER-ID>/vouchers/<ID>`

Optional path, only viable if code provided:

`POST https://api.mycurrency.com/users/<USER-ID>/voucher`

<aside class="notice">
Authentication: the request requires the OAuth access-token associated with the User referenced by the ID 
</aside>

### ARGUMENTS

Parameter | Type | Required | Description
--------- | ------- | ------- | -----------
redeemed | boolean | yes | Whether the voucher has been redeemed or not
code | string | required if :redeemed has a value of true | The voucher's secret code, must be provided to redeem voucher

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the voucher
micro-currency-order-id | The ID of the micro currency order that purchased the voucher
holding-user-id | The ID of the user that purchased the voucher
holding-user-username | The username of the user that purchased the voucher
holding-user-avatar-url | The URL of the avatar of the user that purchased the voucher
product-id | The ID of the product for which the voucher is redeemable for
product-name | The name of the product for which the voucher is redeemable for
product-image-url | The URL of the image of the product for which the voucher is redeemable for
product-sub-category-id | The ID of the sub_category that the product for which the voucher is redeemable for belongs to
product-sub-category-name | The name of the sub_category that the product for which the voucher is redeemable for belongs to
product-quantity | The quantity of the product for which the voucher is redeemable for
store-id | The ID of the store at which the product that the voucher can be redeemed for is sold at
store-name | The name of the store at which the product that the voucher can be redeemed for is sold at
code | The secret code that the voucher holder must reveal to the store owner in order to redeem their voucher, only shown if the logged-in user is the voucher holder
expiration | The date at which the voucher expires, which is one month after it is issued to the buyer
redeemed | Whether the voucher has been redeemed or not
created-at | The time and date when the voucher was created
updated-at | The time and date when the voucher was last updated
