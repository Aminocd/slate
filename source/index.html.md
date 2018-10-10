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
      "get-avatar-url": "/system/users/avatars/000/000/002/original/afternoon_portrait.jpg?1534139495"
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
created_at | The time and date when the user was created
active | Whether the user is active or not
get-avatar-url | The URL at which the user profile picture can be found

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

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the user
username | The username that the user is identified by
created-at | The time and date when the user was created
active | Whether the user is active or not
get-avatar-url | The URL at which the user profile picture can be found
email | The email address associated with the user account
sub-location-id | The ID of the sub location associated with the user account
updated-at | The time and date when the user was last updated

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
      "get-avatar-url": "/system/users/avatars/000/000/002/original/afternoon_portrait.jpg?1534139495"
      "email": "RonaldMcDonald@mcdonalds.com",
      "sub-location-id": 2,
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
get-avatar-url | The URL at which the user profile picture can be found
email | The email address associated with the user account
sub-location-id | The ID of the sub location associated with the user account
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
      "burn-rate": 450,
      "name": "ACME Toon Shop dollars",
      "description": "Spendable at any ACME Toon Shop",
      "created-at": "2018-08-12T01:17:31.176-07:00",
      "updated-at": "2018-08-12T23:49:56.793-07:00",
      "get-icon-url": "/system/currencies/icons/000/000/002/original/DaffyDuck.png?1534142996"
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
burn-rate | The annual rate at which holdings of the currency burn, by basis point (100 = 1%) 
name | The name of the currency
description | The description of the currency
created-at | The time and date when the currency was created
updated-at | The time and date when the currency was last updated
get-icon-url | The URL at which the currency icon picture can be found

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
      "id": "1",
      "type": "currencies",
      "attributes": {
        "issuer-id": 2,
        "burn-rate": 740,
        "name": "Calm dollars",
        "description": "Redeemable for services at Calm Massage Therapy",
        "created-at": "2017-08-10T17:03:08.287-07:00",
        "updated-at": "2017-08-10T17:58:08.738-07:00",
        "get-icon-url": "/system/currencies/icons/000/000/001/original/calm_dollars.jpg?1534619841"
      }
    },
    {
      "id": "2",
      "type": "currencies",
      "attributes": {
        "issuer-id": 3,
        "burn-rate": 450,
        "name": "ACME Toon Shop dollars",
        "description": "Spendable at any ACME Toon Shop",
        "created-at": "2018-08-12T01:17:31.176-07:00",
        "updated-at": "2018-08-12T23:49:56.793-07:00",
        "get-icon-url": "/system/currencies/icons/000/000/002/original/DaffyDuck.png?1534142996"
      }
    },
    {
      "id": "3",
      "type": "currencies",
      "attributes": {
        "issuer-id": 3,
        "burn-rate": 420,
        "name": "Horizon Cloud Computing dollars",
        "description": "Redeemable for Horizon Cloud Computing services",
        "created-at": "2018-09-22T17:10:21.588-07:00",
        "updated-at": "2018-09-22T17:10:21.588-07:00",
        "get-icon-url": "/system/currencies/icons/000/000/003/original/horizon-cloud.png?1534243939"
      }
    },
    {
      "id": "4",
      "type": "currencies",
      "attributes": {
        "issuer-id": 4,
        "burn-rate": 550,
        "name": "Tom's Fruitstand bucks",
        "description": "Redeem Tom's Fruitstand bucks for delicious fruit",
        "created-at": "2018-09-22T17:10:21.588-07:00",
        "updated-at": "2018-09-22T17:10:21.588-07:00",
        "get-icon-url": "/system/currencies/icons/000/000/004/original/Tom-bucks.png?1534148467"
      }
    },
    {
      "id": "5",
      "type": "currencies",
      "attributes": {
        "issuer-id": 5,
        "burn-rate": 500,
        "name": "Chilli pesos",
        "description": "Chilli pesos are backed by chillis",
        "created-at": "2018-09-22T18:57:27.193-07:00",
        "updated-at": "2018-09-22T18:57:27.193-07:00",
        "get-icon-url": "/system/currencies/icons/000/000/005/original/chilli-pesos.png?153414511"
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

This endpoint retrieves all currencies.

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
burn-rate | The annual rate at which holdings of the currency burn, by basis point (100 = 1%) 
name | The name of the currency
description | The description of the currency
created-at | The time and date when the currency was created
updated-at | The time and date when the currency was last updated
get-icon-url | The URL at which the currency icon picture can be found

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
      "id": "2",
      "type": "currencies",
      "attributes": {
        "issuer-id": 3,
        "burn-rate": 450,
        "name": "ACME Toon Shop dollars",
        "description": "Spendable at any ACME Toon Shop",
        "created-at": "2018-08-12T01:17:31.176-07:00",
        "updated-at": "2018-08-12T23:49:56.793-07:00",
        "get-icon-url": "/system/currencies/icons/000/000/002/original/DaffyDuck.png?1534142996"
      }
    },
    {
      "id": "3",
      "type": "currencies",
      "attributes": {
        "issuer-id": 3,
        "burn-rate": 420,
        "name": "Horizon Cloud Computing dollars",
        "description": "Redeemable for Horizon Cloud Computing services",
        "created-at": "2018-09-22T17:10:21.588-07:00",
        "updated-at": "2018-09-22T17:10:21.588-07:00",
        "get-icon-url": "/system/currencies/icons/000/000/003/original/horizon-cloud.png?1534243939"
      }
    }  
  ],
  "links": {
    "self": "http://api.mycurrency.com/currencies?user_id=3",
    "first": "http://api.mycurrency.com/currencies?page=1&per_page=25&user_id=3",
    "prev": null,
    "next": null,
    "last": "http://api.mycurrency.com/currencies?page=1&per_page=25&user_id=3"
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

This endpoint retrieves all currencies belonging to the user associated with the ID provided.

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
burn-rate | The annual rate at which holdings of the currency burn, by basis point (100 = 1%) 
name | The name of the currency
description | The description of the currency
created-at | The time and date when the currency was created
updated-at | The time and date when the currency was last updated
get-icon-url | The URL at which the currency icon picture can be found

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
    "id":"1",
    "type":"currencies",
    "attributes": {
      "issuer-id": 2,
      "burn-rate": 740,
      "name": "Calm dollars",
      "description": "Redeemable for services at Calm Massage Therapy",
      "created-at": "2017-08-10T17:03:08.287-07:00",
      "updated-at": "2017-08-10T17:58:08.738-07:00",
      "get-icon-url":"/icons/original/missing.png"
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
id | The ID of the new currency
issuer-id | The ID of the issuer account that issued the currency
burn-rate | The annual rate at which holdings of the currency burn, by basis point (100 = 1%) 
name | The name of the currency
description | The description of the currency
created-at | The time and date when the currency was created
updated-at | The time and date when the currency was last updated
get-icon-url | The URL at which the currency icon picture can be found

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
      "issuer-id": 2,
      "burn-rate": 740,
      "name": "Calm dollars",
      "description": "Redeemable for services at Calm Massage Therapy",
      "created-at": "2017-08-10T17:03:08.287-07:00",
      "updated-at": "2017-08-10T17:58:08.738-07:00",
      "get-icon-url": "/system/currencies/icons/000/000/001/original/calm_dollars.jpg?1534619841"
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
id | The ID of the updated currency
issuer-id | The ID of the issuer account that issued the currency
burn-rate | The annual rate at which holdings of the currency burn, by basis point (100 = 1%) 
name | The name of the currency
description | The description of the currency
created-at | The time and date when the currency was created
updated-at | The time and date when the currency was last updated
get-icon-url | The URL at which the currency icon picture can be found

#Burnrate Change

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
      "id":"1",
      "type":"burnrate-changes",
      "attributes": {
        "old-burn-rate": 740,
        "new-burn-rate": 500,
        "currency-id": 1,
        "comment": "lowering the burn rate",
        "created-at":"2018-08-19T17:00:50.093-07:00",
        "updated-at":"2018-08-19T17:00:50.093-07:00"
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

This endpoint retrieves all of the specified currency's burnrate changes.

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
new_burn_rate | integer | yes | The value that you want to update the currency's burn rate to
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
      "currency-id": 2,
      "sub-location-id": 2,
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
currency-id | The ID of the currency that the store's products are purchasable with
sub-location-id | The sub location where the store is located
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
      "id": "1",
      "type": "stores",
      "attributes": {
        "currency-id": 1,
        "sub-location-id": 1,
        "physical": true,
        "store-name": "Calm Spa",
        "store-description": "A full service spa for full relaxation",
        "index": "Calm Spa A full service spa for full relaxation\nFacial - standard facial, spa services, includes facials, manicures and pedicures - 5000\n",
        "created-at": "2018-08-11T12:11:16.475-07:00",
        "updated-at": "2018-08-12T02:21:49.458-07:00"
      }
    },
    {
      "id": "2",
      "type": "stores",
      "attributes": {
        "currency-id": 2,
        "sub-location-id": 2,
        "physical": true,
        "store-name": "Vancouver ACME Toon Shop",
        "store-description": "All manner of ACME Toon items available",
        "index": "Vancouver ACME Toon Shop All manner of ACME Toon items available\nBugs Bunny Q-Tips - q-tips that work on the biggest ears, Toon products, products usable by toons - 1550\n",
        "updated-at": "2018-08-13T05:45:12.342-07:00",
        "updated-at": "2018-08-13T05:45:12.342-07:00",
      }
    },
    {
      "id": "3",
      "type": "stores",
      "attributes": {
        "currency-id": 2,
        "sub-location-id": 1,
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

This endpoint retrieves all stores.

### HTTP Request

`GET https://api.mycurrency.com/stores`

<aside class="notice">
Authentication: not required
</aside>

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the store
currency-id | The ID of the currency that the store's products are purchasable with
sub-location-id | The sub location where the store is located
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
      "id": "2",
      "type": "stores",
      "attributes": {
        "currency-id": 2,
        "sub-location-id": 2,
        "physical": true,
        "store-name": "Vancouver ACME Toon Shop",
        "store-description": "All manner of ACME Toon items available",
        "index": "Vancouver ACME Toon Shop All manner of ACME Toon items available\nBugs Bunny Q-Tips - q-tips that work on the biggest ears, Toon products, products usable by toons - 1550\n",
        "updated-at": "2018-08-13T05:45:12.342-07:00",
        "updated-at": "2018-08-13T05:45:12.342-07:00",
      }
    },
    {
      "id": "3",
      "type": "stores",
      "attributes": {
        "currency-id": 2,
        "sub-location-id": 1,
        "physical": true,
        "store-name": "San Francisco ACME Toon Shop",
        "store-description": "San Francisco's premier shop for toons",
        "index": "San Francisco ACME Toon Shop San Francisco's premier shop for toons\nBugs Bunny Q-Tips - q-tips that work on the biggest ears, Fictional items, Toon products - 1550\nTeleport hole - can turn any rock face into a tunnel, fictional items, Toon products - 4000\n",
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

This endpoint retrieves all stores belonging to the currency associated with the ID provided.

### HTTP Request

`GET https://api.mycurrency.com/currencies/<CURRENCY-ID>/stores`

<aside class="notice">
Authentication: not required
</aside>

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the store
currency-id | The ID of the currency that the store's products are purchasable with
sub-location-id | The sub location where the store is located
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
        "currency-id": 1,
        "sub-location-id": 1,
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

This endpoint retrieves all stores that have an index that contains text that matches the search keyword provided.

### HTTP Request

`GET https://api.mycurrency.com/stores?keyword={}`

<aside class="notice">
Authentication: not required
</aside>

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the store
currency-id | The ID of the currency that the store's products are purchasable with
sub-location-id | The sub location where the store is located
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
      "id": "1",
      "type": "stores",
      "attributes": {
        "currency-id": 1,
        "sub-location-id": 1,
        "physical": true,
        "store-name": "Calm Spa",
        "store-description": "A full service spa for full relaxation",
        "index": "Calm Spa A full service spa for full relaxation\nFacial - standard facial, spa services, includes facials, manicures and pedicures - 5000\n",
        "created-at": "2018-08-11T12:11:16.475-07:00",
        "updated-at": "2018-08-12T02:21:49.458-07:00"
      }
    },
    {
      "id": "3",
      "type": "stores",
      "attributes": {
        "currency-id": 2,
        "sub-location-id": 1,
        "physical": true,
        "store-name": "San Francisco ACME Toon Shop",
        "store-description": "San Francisco's premier shop for toons",
        "index": "San Francisco ACME Toon Shop San Francisco's premier shop for toons\nBugs Bunny Q-Tips - q-tips that work on the biggest ears, Fictional items, Toon products - 1550\nTeleport hole - can turn any rock face into a tunnel, fictional items, Toon products - 4000\n",
        "created-at": "2018-08-12T02:11:46.512-07:00",
        "updated-at": "2018-08-12T02:11:46.512-07:00"
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

This endpoint retrieves all stores belonging to the sub location associated with the ID provided.

### HTTP Request

`GET https://api.mycurrency.com/sub_locations/<SUB-LOCATION-ID>/stores`

<aside class="notice">
Authentication: not required
</aside>

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the store
currency-id | The ID of the currency that the store's products are purchasable with
sub-location-id | The sub location where the store is located
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
        "currency-id": 2,
        "sub-location-id": 1,
        "physical": true,
        "store-name": "San Francisco ACME Toon Shop",
        "store-description": "San Francisco's premier shop for toons",
        "index": "San Francisco ACME Toon Shop San Francisco's premier shop for toons\nBugs Bunny Q-Tips - q-tips that work on the biggest ears, Fictional items, Toon products - 1550\nTeleport hole - can turn any rock face into a tunnel, fictional items, Toon products - 4000\n",
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

This endpoint retrieves all stores that belong to the sub location associated with the ID provided and contain text that matches the search keyword provided.

### HTTP Request

`GET https://api.mycurrency.com/sub_locations/<SUB-LOCATION-ID>/stores?keyword={}`

<aside class="notice">
Authentication: not required
</aside>

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the store
currency-id | The ID of the currency that the store's products are purchasable with
sub-location-id | The sub location where the store is located
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
      "currency-id": 5,
      "sub-location-id": 2,
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
currency-id | The ID of the currency that the store's products are purchasable with
sub-location-id | The sub location where the store is located
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
      "currency-id": 5,
      "sub-location-id": 2,
      "physical": true,
      "store-name": "Freds Fishing Supplies",
      "store-description": "The finest fishing shop in San Francisco",
      "index": "Freds Fishing Supplies The finest fishing shop in San Francisco",
      "created-at": "2018-08-26T16:09:40.080-07:00",
      "updated-at": "2018-08-26T16:09:40.080-07:00"
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
sub_category_id | integer | yes | The sub category that the product belongs to 
product_name | string | yes | The name of the product
product_description | string | no | The description of the product
active
store-description | string | no | The description of the store

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the store
currency-id | The ID of the currency that the store's products are purchasable with, provided in URL path
sub-location-id | The sub location where the store is located
physical | Whether the store is a physical location that customers can visit
store-name | The name of the store
store-description | The description of the store
index | Keywords derived from the description of the store and its products that are checked against in searches
created-at | The time and date when the currency was created
updated-at | The time and date when the currency was last updated

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
      "score": 9,
      "created-at": "2018-08-29T00:51:11.631-07:00",
      "updated-at": "2018-08-29T00:51:11.631-07:00"
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
score | A score between 0 and 10 (inclusive) by the store reviewer 
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
        "score": 10,
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
        "score": 9,
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
        "score": 9,
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

<aside class="notice">
Authentication: not required
</aside>

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the store review
store-id | The ID of the store that the store review relates to
comment | The written content of the review
score | A score between 0 and 10 (inclusive) by the store reviewer 
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
        "score": 10,
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
        "score": 9,
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
score | A score between 0 and 10 (inclusive) by the store reviewer 
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
        "score": 9,
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
score | A score between 0 and 10 (inclusive) by the store reviewer 
created-at | The time and date when the store review was created

## Create Store Review

```shell
curl -X POST https://api.mycurrency.com/users/4/store_reviews \
  -d '{"store_review": { "store_id": "1", "score": "9", "comment": "Lucy'\''s Tom Yum Soup is as good as anything I had in Thailand"} }' \
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
      "score": 9,
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
score | integer | yes | A score between 0 and 10 (inclusive)

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the store review
store-id | The ID of the store that the store review relates to
comment | The written content of the review
score | A score between 0 and 10 (inclusive) by the store reviewer 
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
      "sub-category-id": 2,
      "store-id":1,
      "product-name": "Facial",
      "product-description": "standard facial",
      "price-cents": 5000,
      "active": true,
      "continued": true,
      "last-activated-at": "2018-08-24T05:01:25.879-07:00",
      "created-at": "2018-08-24T05:01:25.879-07:00",
      "updated-at": "2018-08-24T05:01:25.879-07:00",
      "get-image-url": "/system/products/images/000/000/001/original/facial.jpg"
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
store-id | The ID of the store where the product is sold
product-name | The name of the product
product-description | The description of the product
price-cents | The price of the product by multiple of 100, and denominated in the currency of the store where the product is sold
active | Whether the product is active or not
continued | Whether the product is continued or not. Discontinued products cannot be recontinued
last-activated-at | The time and date when the product was last activated
created-at | The time and date when the product was created
updated-at | The time and date when the product was last updated
get-image-url | The URL at which the product image picture can be found

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
        "sub-category-id": 2,
        "store-id":1,
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
        "store-id":2,
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
        "store-id":3,
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
        "store-id":3,
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
store-id | The ID of the store where the product is sold
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
        "store-id":3,
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
        "store-id":3,
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

This endpoint retrieves all products belonging to a particular currency. Only products that are active and not discontinued are shown to non-authorized users while authorized users see all of the store's products.

### HTTP Request

`GET https://api.mycurrency.com/stores/<STORE-ID>/products`

<aside class="notice">
Authentication: not required to see the products of a store that are active and that have not been discontinued. To view details of a store's products that are inactive and/or discontinued, the request requires the OAuth access-token associated with the User that the specified store belongs to
</aside>

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the product
sub-category-id | The sub category that the product belongs to
store-id | The ID of the store where the product is sold
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
curl -X POST https://api.mycurrency.com/users/4/issuer/currencies/5/stores/3/products \
  -d '{"product": { "sub_category_id": "4", "product_name": "fishing bait", "product_description": "natural fishing bait made of worms", "active": "true", "price_cents": "1000"} }' 
  -H 'Authorization: Bearer j47lbjj8r9n5yy8mup6cxqc8h70yvhnilm0g84kg0raqckus0k1koj9f75ao' 
  -H 'Accept: application/json' 
  -H 'Content-Type: application/json'
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "id":"5",
    "type":"products",
    "attributes": {
      "sub-category-id": 4,
      "store-id": 3,
      "product-name": "fishing bait",
      "product-description": "natural fishing bait made of worms",
      "price-cents": 1000,
      "active": true,
      "continued": true,
      "last-activated-at": "2018-08-26T17:15:53.011-07:00",
      "created-at": "2018-08-26T17:15:53.011-07:00",
      "updated-at": "2018-08-26T17:15:53.011-07:00",
      "get-image-url": "/images/original/missing.png"
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
store-id | The ID of the store where the product is sold
product-name | The name of the product
product-description | The description of the product
price-cents | The price of the product by multiple of 100, and denominated in the currency of the store where the product is sold
active | Whether the product is active or not
continued | Whether the product is continued or not. Discontinued products cannot be recontinued
last-activated-at | The time and date when the product was last activated
created-at | The time and date when the product was created
updated-at | The time and date when the product was last updated
get-image-url | The URL at which the product image picture can be found

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
      "store-id": 3,
      "product-name": "fishing bait",
      "product-description": "natural fishing bait made of worms",
      "price-cents": 1000,
      "active": true,
      "continued": true,
      "last-activated-at": "2018-08-26T17:15:53.011-07:00",
      "created-at": "2018-08-26T17:15:53.011-07:00",
      "updated-at": "2018-08-26T21:07:27.184-07:00",
      "get-image-url": "/system/products/images/000/000/005/original/fish_bait.jpg?1535342847"
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
price_cents | integer | yes | The price of the product by multiple of 100, and denominated in the currency of the store where the product is sold
active | boolean | yes | Whether the product is active or not
image | filename | no | The image file to be uploaded as product's image picture

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the product
sub-category-id | The sub category that the product belongs to
store-id | The ID of the store where the product is sold
product-name | The name of the product
product-description | The description of the product
price-cents | The price of the product by multiple of 100, and denominated in the currency of the store where the product is sold
active | Whether the product is active or not
continued | Whether the product is continued or not. Discontinued products cannot be recontinued
last-activated-at | The time and date when the product was last activated
created-at | The time and date when the product was created
updated-at | The time and date when the product was last updated
get-image-url | The URL at which the product image picture can be found

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
      "product-id": 5,
      "product-discontinual-id": null,
      "product-name": "fishing bait",
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
        "product-id": 5,
        "product-discontinual-id": null,
        "product-name": "fishing bait",
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
        "product-id": 9,
        "product-discontinual-id": null,
        "product-name": "chameleon tent",
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
        "product-id": 12,
        "product-discontinual-id": null,
        "product-name": "Hawaiian pizza",
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
product-id | The ID of the product that was cancelled
product-discontinual-id | The ID of the product_discontinual that created the product_cancellation
product-name | The name of the cancelled product
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
        "product-id": 5,
        "product-discontinual-id": null,
        "product-name": "fishing bait",
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
        "product-id": 9,
        "product-discontinual-id": null,
        "product-name": "chameleon tent",
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
product-id | The ID of the product that was cancelled
product-discontinual-id | The ID of the product_discontinual that created the product_cancellation
product-name | The name of the cancelled product
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
        "product-id": 5,
        "product-discontinual-id": null,
        "product-name": "fishing bait",
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
product-id | The ID of the product that was cancelled
product-discontinual-id | The ID of the product_discontinual that created the product_cancellation
product-name | The name of the cancelled product
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
      "product-id": 5,
      "product-discontinual-id": null,
      "product-name": "fishing bait",
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
cancellation-message | string | no | The message explaining why the product is being cancelled

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the product cancellation
store-id | The ID of the store where the cancelled product was sold
product-id | The ID of the product that was cancelled
product-discontinual-id | The ID of the product_discontinual that created the product_cancellation
product-name | The name of the cancelled product
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
discontinual-message | string | no | The message explaining why the product will be cancelled

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

# Public Currency Holdings

Unlike private currency holdings, the basic information of public currency holdings, like account balance, is publicly accessible. Authorized endpoints are only accessible to the user that owns the public currency holding and provides the full details of the holding. The publicly accessible endpoints provide basic information about the public currency holding.

## Get a Public Currency Holding

```shell
curl 'https://api.mycurrency.com/users/3/public_currency_holdings/3' \
  -H 'Accept: application/json' -H 'Content-Type: application/json'
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "id": "3",
    "type": "public-currency-holdings",
    "attributes": {
      "owning-user-id": 3,
      "currency-id": 2,
      "amount-atomic": 49918217200
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
amount-atomic | The amount of currency held in the public currency holding, in atomic units (each whole unit is composed of 10^10 atomic units)

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
      "id": "3",
      "type": "public-currency-holdings",
      "attributes": {
        "owning-user-id": 3,
        "currency-id": 2,
        "amount-atomic": 49918217200
      }
    },
    {
      "id": "8",
      "type": "public-currency-holdings",
      "attributes": {
        "owning-user-id": 3,
        "currency-id": 6,
        "amount-atomic": 99975465160 
      }
    }
  ],
  "links": {
    "self": "https://api.mycurrency.com/users/3/self_issued_public_currency_holdings?",
    "first": "https://api.mycurrency.com/users/3/self_issued_public_currency_holdings?page=1&per_page=25",
    "prev": null,
    "next": null,
    "last": "https://api.mycurrency.com/users/3/self_issued_public_currency_holdings?page=1&per_page=25"
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
user_id | integer | yes | The ID of the user which offered the product that is being cancelled, provided in URL path
min_amount | integer | no | The set of currency holdings returned will only include those with balances exceeding min_amount. The default min_amount is zero resulting in currency holdings with a zero balance not being returned.

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the public currency holding
owning-user-id | The ID of the user that the public currency holding belongs to
currency-id | The ID of the currency that the public currency holding holds
amount-atomic | The amount of currency held in the public currency holding, in atomic units (each whole unit is composed of 10^10 atomic units)

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
      "id": "2",
      "type": "public-currency-holdings",
      "attributes": {
        "owning-user-id": 4,
        "currency-id": 2,
        "amount-atomic": 119942752040
      }
    },
    {
      "id": "4",
      "type": "public-currency-holdings",
      "attributes": {
        "owning-user-id": 4,
        "currency-id": 3,
        "amount-atomic": 79983643440 
      }
    }
  ],
  "links": {
    "self": "https://api.mycurrency.com/users/4/externally_issued_public_currency_holdings?",
    "first": "https://api.mycurrency.com/users/4/externally_issued_public_currency_holdings?page=1&per_page=25",
    "prev": null,
    "next": null,
    "last": "https://api.mycurrency.com/users/4/externally_issued_public_currency_holdings?page=1&per_page=25"
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

This endpoint retrieves all of a user's publicly viewable holdings of currencies that the user is not the issuer of.

### HTTP Request

`GET https://api.mycurrency.com/users/<USER-ID>/self_issued_public_currency_holdings`

<aside class="notice">
Authentication: not required
</aside>

### ARGUMENTS

Parameter | Type | Required | Description
--------- | ------- | ------- | -----------
user_id | integer | yes | The ID of the user which offered the product that is being cancelled, provided in URL path
min_amount | integer | no | The set of currency holdings returned will only include those with balances exceeding min_amount. The default min_amount is zero resulting in currency holdings with a zero balance not being returned.

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the public currency holding
owning-user-id | The ID of the user that the public currency holding belongs to
currency-id | The ID of the currency that the public currency holding holds
amount-atomic | The amount of currency held in the public currency holding, in atomic units (each whole unit is composed of 10^10 atomic units)

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
      "currency-id": 2,
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
currency-id | The ID of the currency that the public currency holding holds
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
curl 'https://api.mycurrency.com/users/4/authorized_private_currency_holdings/7' \
  -H 'Accept: application/json' -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer j47lbjj8r9n5yy8mup6cxqc8h70yvhnilm0g84kg0raqckus0k1koj9f75ao'
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "id": "7",
    "type": "private-currency-holdings",
    "attributes": {
      "owning-user-id": 4,
      "currency-id": 3,
      "amount-atomic": 0,
      "transfer-out": 100000000000,
      "transfer-in": 0,
      "micro-currency-order-out": 0,
      "issuance-in": 100000000000,
      "issuance-fee-in": 0,
      "burn-amount-out": 0,
      "created-at": "2018-09-15T20:37:38.277-07:00",
      "updated-at": "2018-09-26T20:35:07.532-07:00"
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
id | The ID of the public currency holding
owning-user-id | The ID of the user that the public currency holding belongs to
currency-id | The ID of the currency that the public currency holding holds
amount-atomic | The amount of currency held in the public currency holding, in atomic units (each whole unit is composed of 10^10 atomic units)
transfer-out | The total amount that has been debited from the public currency holding as a result of outgoing transfers
transfer-in | The total amount that has been credited to the public currency holding as a result of incoming transfers
micro-currency-order-out | The total amount that has been debited from the public currency holding as a result of micro_currency_orders 
issuance-in | The total amount that has been credited to the public currency holding as a result of incoming issuances
burn-amount-out | The total amount that has been debited from the public currency holding as a result of the daily burnrate of the currency 
created-at | The time and date when the public currency holding was created
updated-at | The time and date when the public currency holding was last updated

## List User's Private Self-Issued Currency Holdings with Authorization

```shell
curl 'https://api.mycurrency.com/users/3/authorized_self_issued_private_currency_holdings' \
  -H 'Accept: application/json' -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer j47lbjj8r9n5yy8mup6cxqc8h70yvhnilm0g84kg0raqckus0k1koj9f75ao'
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": "4",
      "type": "private-currency-holdings",
      "attributes": {
        "owning-user-id": 4,
        "currency-id": 4,
        "amount-atomic": 9964274765720,
        "transfer-out": 0,
        "transfer-in": 0,
        "micro-currency-order-out": 0,
        "issuance-in": 10000000000000,
        "issuance-fee-in": 0,
        "burn-amount-out": 35725234280,
        "created-at": "2018-08-25T01:22:20.152-07:00",
        "updated-at": "2018-09-26T19:20:07.007-07:00"
      }
    },
    {
      "id": "5",
      "type": "private-currency-holdings",
      "attributes": {
        "owning-user-id": 4,
        "currency-id": 5,
        "amount-atomic": 9938553881223,
        "transfer-out": 0,
        "transfer-in": 0,
        "micro-currency-order-out": 0,
        "issuance-in": 10000000000000,
        "issuance-fee-in": 0,
        "burn-amount-out": 61446118777,
        "created-at": "2018-08-26T16:07:08.081-07:00",
        "updated-at": "2018-09-27T16:06:07.148-07:00"
      }
    },
    {
      "id": "6",
      "type": "private-currency-holdings",
      "attributes": {
        "owning-user-id": 4,
        "currency-id": 6,
        "amount-atomic": 9989990954562,
        "transfer-out": 0,
        "transfer-in": 0,
        "micro-currency-order-out": 0,
        "issuance-in": 10000000000000,
        "issuance-fee-in": 0,
        "burn-amount-out": 10009045438,
        "created-at": "2018-09-14T13:23:12.338-07:00",
        "updated-at": "2018-09-26T19:20:07.032-07:00"
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
        "total-count": "3"
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
id | The ID of the public currency holding
owning-user-id | The ID of the user that the public currency holding belongs to
currency-id | The ID of the currency that the public currency holding holds
amount-atomic | The amount of currency held in the public currency holding, in atomic units (each whole unit is composed of 10^10 atomic units)
transfer-out | The total amount that has been debited from the public currency holding as a result of outgoing transfers
transfer-in | The total amount that has been credited to the public currency holding as a result of incoming transfers
micro-currency-order-out | The total amount that has been debited from the public currency holding as a result of micro_currency_orders 
issuance-in | The total amount that has been credited to the public currency holding as a result of incoming issuances
burn-amount-out | The total amount that has been debited from the public currency holding as a result of the daily burnrate of the currency 
created-at | The time and date when the public currency holding was created
updated-at | The time and date when the public currency holding was last updated

## List User's Private Externally Issued Currency Holdings with Authorization

```shell
curl 'https://api.mycurrency.com/users/4/authorized_externally_issued_private_currency_holdings' \
  -H 'Accept: application/json' -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer j47lbjj8r9n5yy8mup6cxqc8h70yvhnilm0g84kg0raqckus0k1koj9f75ao'
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
    "id": "7",
    "type": "private-currency-holdings",
    "attributes": {
    "owning-user-id": 4,
    "currency-id": 3,
    "amount-atomic": 0,
    "transfer-out": 100000000000,
    "transfer-in": 0,
    "micro-currency-order-out": 0,
    "issuance-in": 100000000000,
    "issuance-fee-in": 0,
    "burn-amount-out": 0,
    "created-at": "2018-09-15T20:37:38.277-07:00",
    "updated-at": "2018-09-26T20:35:07.532-07:00"
    }
    }
  ],
  "links": {
    "self": "https://api.mycurrency.com/users/4/authorized_externally_issued_private_currency_holdings?",
    "first": "https://api.mycurrency.com/users/4/authorized_externally_issued_private_currency_holdings?page=1&per_page=25",
    "prev": null,
    "next": null,
    "last": "https://api.mycurrency.com/users/4/authorized_externally_issued_private_currency_holdings?page=1&per_page=25"
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

This endpoint retrieves the full details of all of a user's privately viewable holdings of currencies that the user is not the issuer of.

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
amount-atomic | The amount of currency held in the public currency holding, in atomic units (each whole unit is composed of 10^10 atomic units)
transfer-out | The total amount that has been debited from the public currency holding as a result of outgoing transfers
transfer-in | The total amount that has been credited to the public currency holding as a result of incoming transfers
micro-currency-order-out | The total amount that has been debited from the public currency holding as a result of micro_currency_orders 
issuance-in | The total amount that has been credited to the public currency holding as a result of incoming issuances
burn-amount-out | The total amount that has been debited from the public currency holding as a result of the daily burnrate of the currency 
created-at | The time and date when the public currency holding was created
updated-at | The time and date when the public currency holding was last updated

# Transactions

Transactions are all user actions that change the balance of currency holdings: issuances, transfers, and micro currency orders. When listing the transactions associated with a particular public or private currency holding, the burnrate periods of that currency holding are also shown, to enable calculation of the amount of currency burned over time.

## List Public Currency Holding's Transactions

This endpoint retrieves all issuances, transfers, micro currency orders and burnrate periods associated with a public currency holding, sorted by created_at date, from the oldest to the most recent

```shell
curl 'https://api.mycurrency.com/users/4/authorized_public_currency_holdings/4/pu_h_transactions' \
  -H 'Accept: application/json' -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer j47lbjj8r9n5yy8mup6cxqc8h70yvhnilm0g84kg0raqckus0k1koj9f75ao'
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": "18",
      "type": "burnrate-periods",
      "attributes": {
        "day-counter": 16,
        "final-day-counter": null,
        "burn-rate": 580,
        "daily-burn-rate": "0.000163686",
        "start-amount-atomic": 0,
        "last-amount-atomic": 79790738929
        "created-at": "2018-09-16T13:40:22.420-07:00",
        "updated-at": "2018-10-02T19:44:06.603-07:00",
      }
    },
    {
      "id": "4",
      "type": "transfers",
      "attributes": {
        "amount-atomic": 80000000000,
        "receiver-day-counter": 0,
        "sending-user-id": 4,
        "sender-username": "ScipioAfricanus",
        "receiver-before-amount-atomic": 0,
        "receiver-after-amount-atomic": 80000000000,
        "created-at": "2018-09-16T13:40:22.461-07:00",
        "updated-at": "2018-09-16T13:40:22.461-07:00",
      }
    }
  ],
  "links": {
    "self": "https://api.mycurrency.com/users/4/authorized_public_currency_holdings/4/pu_h_transactions?",
    "first": "https://api.mycurrency.com/users/4/authorized_public_currency_holdings/4/pu_h_transactions?page=1&per_page=25",
    "prev": null,
    "next": null,
    "last": "https://api.mycurrency.com/users/4/authorized_public_currency_holdings/4/pu_h_transactions?page=1&per_page=25"
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

### HTTP Request

`https://api.mycurrency.com/users/<USER-ID>/authorized_public_currency_holdings/<PUBLIC-CURRENCY-HOLDING-ID>/pu_h_transactions`

<aside class="notice">
Authentication: the request requires the OAuth access-token associated with the User referenced by the ID 
</aside>

### RESPONSE

### Transfers:

Parameter | Description
--------- | -----------
id | The ID of the transfer
amount-atomic | The amount of currency transferred, in atomic units (each whole unit is composed of 10^10 atomic units)
sender-day-counter | The day counter of the sending currency holding when it was debited by the transfer, only shown if the owner of the public currency holding is the sending user
receiver-day-counter | The day counter of the receiving currency holding when it was credited by the transfer, only shown if the owner of the public or private currency holding is the receiving user
sending-user-id | The ID of the transfer sender, only shown if the owner of the public currency holding is the transfer receiver 
sender-username | The username of the transfer sender, only shown if the owner of the public currency holding is the transfer receiver
receiving-user-id | The ID of the transfer receiver, only shown if owner of the public currency holding is the transfer sender
receiving-username | The username of the transfer sender, only shown if the owner of the public currency holding is the transfer sender 
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

This endpoint retrieves all issuances, transfers, micro currency orders and burnrate periods associated with a private currency holding, sorted by created_at date, from the oldest to the most recent

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
      "id": "20",
      "type": "burnrate-periods",
      "attributes": {
        "day-counter": 0,
        "final-day-counter": null,
        "burn-rate": 700,
        "daily-burn-rate": "0.000198805",
        "start-amount-atomic": 0,
        "last-amount-atomic": 210000000000,
        "created-at": "2018-10-03T00:19:35.155-07:00",
        "updated-at": "2018-10-03T01:58:03.334-07:00"
      }
    },
    {
      "id": "6",
      "type": "transfers",
      "attributes": {
        "amount-atomic": 10000000000,
        "receiver-day-counter": 0,
        "sending-user-id": 4,
        "sender-username": "ScipioAfricanus",
        "receiver-before-amount-atomic": 0,
        "receiver-after-amount-atomic": 10000000000,
        "created-at": "2018-10-03T00:19:35.177-07:00",
        "updated-at": "2018-10-03T00:19:35.177-07:00"
      }
    },
    {
      "id": "7",
      "type": "transfers",
      "attributes": {
        "amount-atomic": 500000000000,
        "receiver-day-counter": 0,
        "sending-user-id": 4,
        "sender-username": "ScipioAfricanus",
        "receiver-before-amount-atomic": 10000000000,
        "receiver-after-amount-atomic": 510000000000,
        "created-at": "2018-10-03T00:20:58.124-07:00",
        "updated-at": "2018-10-03T00:20:58.124-07:00"
      }
    },
    {
      "id": "1",
      "type": "micro-currency-orders",
      "attributes": {
        "amount-atomic": 100000000000,
        "store-id": 3,
        "store-name": "Freds Fishing Supplies",
        "before-amount-atomic": 510000000000,
        "after-amount-atomic": 410000000000,
        "day-counter": 0,
        "created-at": "2018-10-03T00:39:37.860-07:00",
        "updated-at": "2018-10-03T00:39:37.860-07:00"
      }
    },
    {
      "id": "2",
      "type": "micro-currency-orders",
      "attributes": {
        "amount-atomic": 100000000000,
        "store-id": 3,
        "store-name": "Freds Fishing Supplies",
        "before-amount-atomic": 410000000000,
        "after-amount-atomic": 310000000000,
        "day-counter": 0,
        "created-at": "2018-10-03T00:43:31.756-07:00",
        "updated-at": "2018-10-03T00:43:31.756-07:00"
      }
    },
    {
      "id": "3",
      "type": "micro-currency-orders",
      "attributes": {
        "amount-atomic": 100000000000,
        "store-id": 3,
        "store-name": "Freds Fishing Supplies",
        "before-amount-atomic": 310000000000,
        "after-amount-atomic": 210000000000,
        "day-counter": 0,
        "created-at": "2018-10-03T01:58:03.223-07:00",
        "updated-at": "2018-10-03T01:58:03.223-07:00"
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
      "total-count": "6"
    }
  }
}
```

### HTTP Request

`https://api.mycurrency.com/users/<USER-ID>/authorized_public_currency_holdings/<PRIVATE-CURRENCY-HOLDING-ID>/pr_h_transactions`

<aside class="notice">
Authentication: the request requires the OAuth access-token associated with the User referenced by the ID 
</aside>

### RESPONSE

### Transfers:

Parameter | Description
--------- | -----------
id | The ID of the transfer
amount-atomic | The amount of currency transferred, in atomic units (each whole unit is composed of 10^10 atomic units)
sender-day-counter | The day counter of the sending currency holding when it was debited by the transfer, only shown if the owner of the private currency holding is the sending user
receiver-day-counter | The day counter of the receiving currency holding when it was credited by the transfer, only shown if the owner of the public or private currency holding is the receiving user
sending-user-id | The ID of the transfer sender, only shown if the owner of the private currency holding is the transfer receiver 
sender-username | The username of the transfer sender, only shown if the owner of the private currency holding is the transfer receiver
receiving-user-id | The ID of the transfer receiver, only shown if owner of the private currency holding is the transfer sender
receiving-username | The username of the transfer sender, only shown if the owner of the private currency holding is the transfer sender 
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
      "id": "3",
      "type": "micro-currency-orders",
      "attributes": {
        "day-counter": 0,
        "amount-atomic": 100000000000,
        "store-id": 3,
        "store-name": "Freds Fishing Supplies",
        "source-currency-holding-id": 9,
        "source-currency-holding-type": "PrivateCurrencyHolding",
        "spent-currency-id": 5,
        "spent-currency-name": "Freds Fishing Supplies dollars",
        "before-amount-atomic": 310000000000,
        "after-amount-atomic": 210000000000,
        "created-at": "2018-10-03T01:58:03.223-07:00",
        "updated-at": "2018-10-03T01:58:03.223-07:00"
      }
    },
    {
      "id": "2",
      "type": "micro-currency-orders",
      "attributes": {
        "day-counter": 0,
        "amount-atomic": 100000000000,
        "store-id": 3,
        "store-name": "Freds Fishing Supplies",
        "source-currency-holding-id": 9,
        "source-currency-holding-type": "PrivateCurrencyHolding",
        "spent-currency-id": 5,
        "spent-currency-name": "Freds Fishing Supplies dollars",
        "before-amount-atomic": 410000000000,
        "after-amount-atomic": 310000000000,
        "created-at": "2018-10-03T00:43:31.756-07:00",
        "updated-at": "2018-10-03T00:43:31.756-07:00"
      }
    },
    {
      "id": "1",
      "type": "micro-currency-orders",
      "attributes": {
        "day-counter": 0,
        "amount-atomic": 100000000000,
        "store-id": 3,
        "store-name": "Freds Fishing Supplies",
        "source-currency-holding-id": 9,
        "source-currency-holding-type": "PrivateCurrencyHolding",
        "spent-currency-id": 5,
        "spent-currency-name": "Freds Fishing Supplies dollars",
        "before-amount-atomic": 510000000000,
        "after-amount-atomic": 410000000000,
        "created-at": "2018-10-03T00:39:37.860-07:00",
        "updated-at": "2018-10-03T00:39:37.860-07:00"
      }
    },
    {
      "id": "7",
      "type": "transfers",
      "attributes": {
        "amount-atomic": 500000000000,
        "receiver-day-counter": 0,
        "transfer-receiver-currency-holding-type": "PrivateCurrencyHolding",
        "transfer-receiver-currency-holding-id": 9,
        "sending-user-id": 4,
        "sender-username": "ScipioAfricanus",
        "receiver-before-amount-atomic": 10000000000,
        "receiver-after-amount-atomic": 510000000000,
        "transferred-currency-id": 5,
        "transferred-currency-name": "Freds Fishing Supplies dollars",
        "created-at": "2018-10-03T00:20:58.124-07:00",
        "updated-at": "2018-10-03T00:20:58.124-07:00"
      }
    },
    {
      "id": "6",
      "type": "transfers",
      "attributes": {
        "amount-atomic": 10000000000,
        "receiver-day-counter": 0,
        "transfer-receiver-currency-holding-type": "PrivateCurrencyHolding",
        "transfer-receiver-currency-holding-id": 9,
        "sending-user-id": 4,
        "sender-username": "ScipioAfricanus",
        "receiver-before-amount-atomic": 0,
        "receiver-after-amount-atomic": 10000000000,
        "transferred-currency-id": 5,
        "transferred-currency-name": "Freds Fishing Supplies dollars",
        "created-at": "2018-10-03T00:19:35.177-07:00",
        "updated-at": "2018-10-03T00:19:35.177-07:00"
      }
    },
    {
      "id": "8",
      "type": "issuances",
      "attributes": {
        "amount-atomic": 100000000000,
        "receiving-user-id": 4,
        "receiver-username": "ScipioAfricanus",
        "issued-currency-id": 3,
        "issued-currency-name": "macaroon dollars",
        "created-at": "2018-10-02T15:58:40.136-07:00",
        "updated-at": "2018-10-02T15:58:40.136-07:00"
      }
    },
    {
      "id": "5",
      "type": "transfers",
      "attributes": {
        "amount-atomic": 10000000000,
        "receiver-day-counter": 0,
        "transfer-receiver-currency-holding-type": "PrivateCurrencyHolding",
        "transfer-receiver-currency-holding-id": 8,
        "sending-user-id": 4,
        "sender-username": "ScipioAfricanus",
        "receiver-before-amount-atomic": 0,
        "receiver-after-amount-atomic": 10000000000,
        "transferred-currency-id": 4,
        "transferred-currency-name": "Pool coins",
        "created-at": "2018-10-02T04:33:05.301-07:00",
        "updated-at": "2018-10-02T04:33:05.301-07:00"
      }
    },
    {
      "id": "3",
      "type": "transfers",
      "attributes": {
        "amount-atomic": 50000000000,
        "receiving-user-id": 3,
        "receiver-username": "Hannibal",
        "sender-day-counter": 0,
        "receiver-day-counter": 0,
        "transfer-sender-currency-holding-type": "PrivateCurrencyHolding",
        "transfer-receiver-currency-holding-type": "PublicCurrencyHolding",
        "transfer-sender-currency-holding-id": 2,
        "transfer-receiver-currency-holding-id": 3,
        "sending-user-id": 3,
        "sender-username": "Hannibal",
        "sender-before-amount-atomic": 10000000000000,
        "sender-after-amount-atomic": 9950000000000,
        "receiver-before-amount-atomic": 0,
        "receiver-after-amount-atomic": 50000000000,
        "transferred-currency-id": 2,
        "transferred-currency-name": "ACME bucks",
        "created-at": "2018-09-16T13:26:52.053-07:00",
        "updated-at": "2018-09-16T13:26:52.053-07:00"
      }
    },
    {
      "id": "2",
      "type": "transfers",
      "attributes": {
        "amount-atomic": 10000000000,
        "receiver-day-counter": 0,
        "transfer-receiver-currency-holding-type": "PrivateCurrencyHolding",
        "transfer-receiver-currency-holding-id": 3,
        "sending-user-id": 4,
        "sender-username": "ScipioAfricanus",
        "receiver-before-amount-atomic": 10010000000000,
        "receiver-after-amount-atomic": 10020000000000,
        "transferred-currency-id": 3,
        "transferred-currency-name": "macaroon dollars",
        "created-at": "2018-09-16T13:08:27.204-07:00",
        "updated-at": "2018-09-16T13:08:27.204-07:00"
      }
    }
  ],
  "links": {
    "self": "https://api.mycurrency.com/users/3/recent_transactions?per_page=10",
    "first": "https://api.mycurrency.com/users/3/recent_transactions?page=1&per_page=10",
    "prev": null,
    "next": "https://api.mycurrency.com/users/3/recent_transactions?page=2&per_page=10",
    "last": "https://api.mycurrency.com/users/3/recent_transactions?page=2&per_page=10"
  },
  "meta": {
    "pagination": {
      "per-page": "10",
      "total-pages": "2",
      "total-count": "15"
    }
  }
}
```

### HTTP Request

`https://api.mycurrency.com/users/<USER-ID>/recent_transactions`

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
sender-day-counter | The day counter of the sending currency holding when it was debited by the transfer, only shown if the owner of the currency holding that the transfer debited from is the logged-in user
receiver-day-counter | The day counter of the receiving currency holding when it was credited by the transfer, only shown if the owner of the currency holding that the transfer credited to is the logged-in user
transfer-sender-currency-holding-type | Whether the currency holding that the transfer debited from is a "PublicCurrencyHolding" or a "PrivateCurrencyHolding", only shown if the owner of the currency holding that the transfer debited from is the logged-in user
transfer-sender-currency-holding-id | The ID of the public or private currency holding that the transfer debited from, only shown if the owner of the currency holding that the transfer debited from is the logged-in user
transfer-receiver-currency-holding-type | Whether the currency holding that the transfer credited to is a "PublicCurrencyHolding" or a "PrivateCurrencyHolding", only shown if the owner of the currency holding that the transfer credited to is the logged-in user
transfer-receiver-currency-holding-id | The ID of the public or private currency holding that the transfer credited to, only shown if the owner of the currency holding that the transfer credited to is the logged-in user
sending-user-id | The ID of the transfer sender, only shown if the owner of the currency holding that the transfer credited to is the logged-in user 
sender-username | The username of the transfer sender, only shown if the owner of the currency holding that the transfer credited to is the logged-in user
sender-before-amount-atomic | The balance, in atomic units, of the sending currency holding before it was debited from by the transfer, only shown if the owner of the currency holding that the transfer debited from is the logged-in user
sender-after-amount-atomic | The balance, in atomic units, of the sending currency holding after it was debited from by the transfer, only shown if the owner of the currency holding that the transfer debited from is the logged-in user
receiver-before-amount-atomic | The balance, in atomic units, of the receiving currency holding before it was credited to by the transfer, only shown if the owner of the currency holding that the transfer credited to is the logged-in user
receiver-after-amount-atomic | The balance, in atomic units, of the receiving currency holding after it was credited to by the transfer, only shown if the owner of the currency holding that the transfer credited to is the logged-in user
transferred-currency-id | The ID of the transferred currency
transferred-currency-name | The name of the transferred currency
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
issuance-receiver-currency-holding-id | The ID of the public or private currency holding that the issuance credited to, only shown if the issuance receiver is the logged-in user
issuance-receiver-currency-holding-type | Whether the currency holding that the issuance credited to is a "PublicCurrencyHolding" or a "PrivateCurrencyHolding", only shown if the issuance receiver is the logged-in user
issued-currency-id | The ID of the issued currency
issued-currency-name | The name of the issued currency
issueing-user-id | The ID of the issueing user, only shown if the issuance receiver is the logged-in user 
issuer-username | The username of the issueing user, only shown if the issuance receiver is the logged-in user
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
spent-currency-id | The ID of the issued currency
spent-currency-name | The name of the issued currency
before-amount-atomic | The balance, in atomic units, of the currency holding before it was debited by the micro currency order
after-amount-atomic | The balance, in atomic units, of the currency holding after it was debited by the micro currency order
created-at | The time and date when the micro currency order was created
updated-at | The time and date when the micro currency order was last updated

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
      "issued-currency-id": 1,
      "issued-currency-name": "Calm dollars",
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
issued-currency-id | The ID of the issued currency
issued-currency-name | The name of the issued currency
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
        "issued-currency-id": 1,
        "issued-currency-name": "Calm dollars",
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
        "issuance-receiver-currency-holding-id": 2,
        "day-counter": 0,
        "burnrate-period-id": 2,
        "before-amount-atomic": 0,
        "after-amount-atomic": 10000000000000,
        "issueing-user-id": 3,
        "issuer-username": "Hannibal",
        "receiving-user-id": 3,
        "receiver-username": "Hannibal",
        "issued-currency-id": 2,
        "issued-currency-name": "ACME bucks",
        "created-at": "2018-08-19T14:11:16.951-07:00",
        "updated-at": "2018-08-19T14:11:16.951-07:00"
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
        "issued-currency-id": 3,
        "issued-currency-name": "macaroon dollars",
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
issued-currency-id | The ID of the issued currency
issued-currency-name | The name of the issued currency
created-at | The time and date when the transfer was created
updated-at | The time and date when the transfer was last updated

## List User's Issuances of Particular Currency

```shell
curl 'https://api.mycurrency.com/currencies/3/issuances?issueing_user_id=3' \
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
      "issuance-receiver-currency-holding-id": 3,
      "day-counter": 0,
      "burnrate-period-id": 3,
      "before-amount-atomic": 0,
      "after-amount-atomic": 10000000000000,
      "issueing-user-id": 3,
      "issuer-username": "Hannibal",
      "receiving-user-id": 3,
      "receiver-username": "Hannibal",
      "issued-currency-id": 3,
      "issued-currency-name": "macaroon dollars",
      "created-at": "2018-08-19T14:24:09.642-07:00",
      "updated-at": "2018-08-19T14:24:09.642-07:00"
    }
  },
  {
    "id": "7",
    "type": "issuances",
    "attributes": {
      "proposed-issuance-id": null,
      "amount-atomic": 100000000000,
      "is-genesis-issuance": false,
      "issuance-receiver-currency-holding-type": "PrivateCurrencyHolding",
      "receiving-user-id": 4,
      "receiver-username": "ScipioAfricanus",
      "issued-currency-id": 3,
      "issued-currency-name": "macaroon dollars",
      "created-at": "2018-09-15T20:37:38.324-07:00",
      "updated-at": "2018-09-15T20:37:38.324-07:00"
    }
  },
  {
    "id": "8",
    "type": "issuances",
    "attributes": {
      "proposed-issuance-id": null,
      "amount-atomic": 100000000000,
      "is-genesis-issuance": false,
      "issuance-receiver-currency-holding-type": "PrivateCurrencyHolding",
      "receiving-user-id": 4,
      "receiver-username": "ScipioAfricanus",
      "issued-currency-id": 3,
      "issued-currency-name": "macaroon dollars",
      "created-at": "2018-10-02T15:58:40.136-07:00",
      "updated-at": "2018-10-02T15:58:40.136-07:00"
    }
  }
  ],
  "links": {
    "self": "http://api.mycurrency.com/currencies/3/issuances?issueing_user_id=3",
    "first": "http://api.mycurrency.com/currencies/3/issuances?issueing_user_id=3&page=1&per_page=25",
    "prev": null,
    "next": null,
    "last": "http://api.mycurrency.com/currencies/3/issuances?issueing_user_id=3&page=1&per_page=25"
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

This endpoint retrieves all received or created issuances of a user associated with the currency specified by CURRENCY-ID. The logged in user must be active to view the issuances. 

### HTTP Request

`GET https://api.mycurrency.com/currencies/<CURRENCY-ID>/issuances?receiving_user_id=<USER-ID>`

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
issued-currency-id | The ID of the issued currency
issued-currency-name | The name of the issued currency
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
    "id": "9",
    "type": "issuances",
    "attributes": {
      "proposed-issuance-id": null,
      "amount-atomic": 100000000000,
      "is-genesis-issuance": false,
      "issuance-receiver-currency-holding-type": "PrivateCurrencyHolding",
      "issued-currency-id": 3,
      "issued-currency-name": "macaroon dollars",
      "created-at": "2018-10-09T19:59:38.499-07:00",
      "updated-at": "2018-10-09T19:59:38.499-07:00"
    }
  }
}
```

Creates a currency.

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
receiving_user_id | integer | yes |  The ID of the user that to receive the issuance

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
issued-currency-id | The ID of the issued currency
issued-currency-name | The name of the issued currency
created-at | The time and date when the transfer was created
updated-at | The time and date when the transfer was last updated
