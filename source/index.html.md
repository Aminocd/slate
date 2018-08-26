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

This endpoint retrieves all stores belonging to the sub location associated with the ID provided.

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
currency_id | integer | yes | The ID of the currency that the store's products are purchasable with
sub_location_id | integer | yes | The sub location where the store is located
physical | boolean | yes | Whether the store is a physical location that customers can visit
store-name | string | yes | The name of the store
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
currency_id | integer | yes | The ID of the currency that the store's products are purchasable with
sub_location_id | integer | yes | The sub location where the store is located
physical | boolean | yes | Whether the store is a physical location that customers can visit
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
