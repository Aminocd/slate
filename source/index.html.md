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
created-at | The time and date when the user was created
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
        "created-at": "2018-08-13T05:45:12.342-07:00",
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
        "created-at": "2018-08-13T05:45:12.342-07:00",
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
cancellation_message | string | no | The message explaining why the product is being cancelled

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
curl 'https://api.mycurrency.com/users/3/authorized_self_issued_currency_holdings' \
  -H 'Accept: application/json' -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer j47lbjj8r9n5yy8mup6cxqc8h70yvhnilm0g84kg0raqckus0k1koj9f75ao'
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "currency-holding-pair": {
        "data": [
          {
            "id": 1,
            "type": "PrivateCurrencyHolding",
            "attributes": {
              "currency-id": 1,
              "currency-name": "Micro Asteroid bucks",
              "currency-icon-url": "/icons/original/missing.png",
              "currency-burn-rate": 500,
              "amount-atomic": 9895827142424,
              "burn-amount-out": 4172857576,
              "created-at": "2018-11-05 13:27:52 -0800",
              "updated-at": "2018-11-08 13:26:13 -0800"
            }
          },
          {
            "id": 2,
            "type": "PublicCurrencyHolding",
            "attributes": {
              "currency-id": 1,
              "currency-name": "Micro Asteroid bucks",
              "currency-icon-url": "/icons/original/missing.png",
              "currency-burn-rate": 500,
              "amount-atomic": 99957849922,
              "burn-amount-out": 42150078,
              "created-at": "2018-11-05 13:27:47 -0800",
              "updated-at": "2018-11-08 13:26:13 -0800"
            }
          }
        ]
      }
    }
  ]
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
amount-atomic | The amount of currency held in the currency holding, in atomic units (each whole unit is composed of 10^10 atomic units)
burn-amount-out | The total amount that has been debited from the public currency holding as a result of the daily burnrate of the currency 
created-at | The time and date when the public currency holding was created
updated-at | The time and date when the public currency holding was last updated

## List User's Externally Issued Currency Holdings with Authorization

```shell
curl 'https://api.mycurrency.com/users/3/authorized_externally_issued_currency_holdings' \
  -H 'Accept: application/json' -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer j47lbjj8r9n5yy8mup6cxqc8h70yvhnilm0g84kg0raqckus0k1koj9f75ao'
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "currency-holding-pair": {
        "data": [
          {
            "id": 3,
            "type": "PrivateCurrencyHolding",
            "attributes": {
              "currency-id": 2,
              "currency-name": "solar electricity zaps",
              "currency-icon-url": "/icons/original/missing.png",
              "currency-burn-rate": 640,
              "amount-atomic": 9994565314,
              "burn-amount-out": 5434686,
              "created-at": "2018-11-05 13:27:52 -0800",
              "updated-at": "2018-11-08 13:26:13 -0800"
            }
          }
        ]
      }
    },
    {
      "currency-holding-pair": {
        "data": [
          {
            "id": 6,
            "type": "PrivateCurrencyHolding",
            "attributes": {
              "currency-id": 3,
              "currency-name": "Moon hotel coins",
              "currency-icon-url": "/icons/original/missing.png",
              "currency-burn-rate": 550,
              "amount-atomic": 4997675720243,
              "burn-amount-out": 2324279757,
              "created-at": "2018-11-05 13:27:52 -0800",
              "updated-at": "2018-11-08 13:26:13 -0800"
            }
          },
          {
            "id": 4,
            "type": "PublicCurrencyHolding",
            "attributes": {
              "currency-id": 3,
              "currency-name": "Moon hotel coins",
              "currency-icon-url": "/icons/original/missing.png",
              "currency-burn-rate": 550,
              "amount-atomic": 4997675720243,
              "burn-amount-out": 2324279757,
              "created-at": "2018-11-05 13:27:47 -0800",
              "updated-at": "2018-11-08 13:26:13 -0800"
            }
          }
        ]
      }
    },
    {
      "currency-holding-pair": {
        "data": [
          {
            "id": 9,
            "type": "PrivateCurrencyHolding",
            "attributes": {
              "currency-id": 4,
              "currency-name": "spiderman pizza dollars",
              "currency-icon-url": "/icons/original/missing.png",
              "currency-burn-rate": 420,
              "amount-atomic": 2499118493626,
              "burn-amount-out": 881506374,
              "created-at": "2018-11-05 13:27:52 -0800",
              "updated-at": "2018-11-08 13:26:13 -0800"
            }
          },
          {
            "id": 6,
            "type": "PublicCurrencyHolding",
            "attributes": {
              "currency-id": 4,
              "currency-name": "spiderman pizza dollars",
              "currency-icon-url": "/icons/original/missing.png",
              "currency-burn-rate": 420,
              "amount-atomic": 2499118493626,
              "burn-amount-out": 881506374,
              "created-at": "2018-11-05 13:27:47 -0800",
              "updated-at": "2018-11-08 13:26:13 -0800"
            }
          }
        ]
      }
    },
    {
      "currency-holding-pair": {
        "data": [
          {
            "id": 13,
            "type": "PrivateCurrencyHolding",
            "attributes": {
              "currency-id": 5,
              "currency-name": "Home Repair dollars",
              "currency-icon-url": "/icons/original/missing.png",
              "currency-burn-rate": 450,
              "amount-atomic": 4998738679556,
              "burn-amount-out": 1261320444,
              "created-at": "2018-11-06 13:27:52 -0800",
              "updated-at": "2018-11-08 13:26:13 -0800"
            }
          }
        ]
      }
    },
    {
      "currency-holding-pair": {
        "data": [
          {
            "id": 12,
            "type": "PrivateCurrencyHolding",
            "attributes": {
              "currency-id": 6,
              "currency-name": "Wholesome foods tokens",
              "currency-icon-url": "/icons/original/missing.png",
              "currency-burn-rate": 710,
              "amount-atomic": 9995965387034,
              "burn-amount-out": 4034612966,
              "created-at": "2018-11-06 13:27:52 -0800",
              "updated-at": "2018-11-08 13:26:13 -0800"
            }
          }
        ]
      }
    }
  ]
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
amount-atomic | The amount of currency held in the currency holding, in atomic units (each whole unit is composed of 10^10 atomic units)
burn-amount-out | The total amount that has been debited from the public currency holding as a result of the daily burnrate of the currency 
created-at | The time and date when the public currency holding was created
updated-at | The time and date when the public currency holding was last updated

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
      "currency-name": "ACME Toon Shop dollars",
      "currency-icon-url": "/system/currencies/icons/000/000/002/original/DaffyDuck.png?1534142996",
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
currency-name | The name of the currency that the public currency holding holds
currency-icon-url | The URL at which the icon picture of the currency that the public currency holding holds can be found
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
        "currency-name": "ACME Toon Shop dollars",
        "currency-icon-url": "/system/currencies/icons/000/000/002/original/DaffyDuck.png?1534142996",
        "amount-atomic": 49918217200
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
user_id | integer | yes | The ID of the user which owns the currency holdings, provided in URL path
min_amount | integer | no | The set of currency holdings returned will only include those with balances exceeding min_amount. The default min_amount is zero resulting in currency holdings with a zero balance not being returned.

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the public currency holding
owning-user-id | The ID of the user that the public currency holding belongs to
currency-id | The ID of the currency that the public currency holding holds
currency-name | The name of the currency that the public currency holding holds
currency-icon-url | The URL at which the icon picture of the currency that the public currency holding holds can be found
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
        "currency-name": "ACME Toon Shop dollars",
        "currency-icon-url": "/system/currencies/icons/000/000/002/original/DaffyDuck.png?1534142996",
        "amount-atomic": 119942752040
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
        "amount-atomic": 999647397450
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
        "amount-atomic": 2499118493626
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
      "total-count": "2"
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
      "currency-name": "ACME Toon Shop dollars",
      "currency-icon-url": "/system/currencies/icons/000/000/002/original/DaffyDuck.png?1534142996",
      "currency-burn-rate": 450,
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
currency-name | The name of the currency that the public currency holding holds
currency-icon-url | The URL at which the icon picture of the public currency that the currency holding holds can be found
currency-burn-rate | The annual rate at which the currency contained within the public currency holding burns, by basis point (100 = 1%) 
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
      "currency-name": "Horizon Cloud Computing dollars",
      "currency-icon-url": "/system/currencies/icons/000/000/003/original/horizon_dollars.png?1534142996",
      "currency-burn-rate": 420,
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
id | The ID of the private currency holding
owning-user-id | The ID of the user that the private currency holding belongs to
currency-id | The ID of the currency that the private currency holding holds
currency-name | The name of the currency that the private currency holding holds
currency-icon-url | The URL at which the icon picture of the currency that the private currency holding holds can be found
currency-burn-rate | The annual rate at which the currency contained within the private currency holding burns, by basis point (100 = 1%) 
amount-atomic | The amount of currency held in the private currency holding, in atomic units (each whole unit is composed of 10^10 atomic units)
transfer-out | The total amount that has been debited from the private currency holding as a result of outgoing transfers
transfer-in | The total amount that has been credited to the private currency holding as a result of incoming transfers
micro-currency-order-out | The total amount that has been debited from the private currency holding as a result of micro_currency_orders 
issuance-in | The total amount that has been credited to the private currency holding as a result of incoming issuances
burn-amount-out | The total amount that has been debited from the private currency holding as a result of the daily burnrate of the currency 
created-at | The time and date when the private currency holding was created
updated-at | The time and date when the private currency holding was last updated

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
        "currency-name": "Tom's Fruitstand bucks",
        "currency-icon-url": "/system/currencies/icons/000/000/004/original/Toms_bucks.png?1534144151",
        "currency-burn-rate": 500,
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
        "currency-name": "Chilli pesos",
        "currency-icon-url": "/system/currencies/icons/000/000/005/original/chilli_pesos.png?1534151581",
        "currency-burn-rate": 500,
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
        "currency-name": "Diamond dollars",
        "currency-icon-url": "/system/currencies/icons/000/000/006/original/Diamond-coins.png?1534142996",
        "currency-burn-rate": 300,
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
id | The ID of the private currency holding
owning-user-id | The ID of the user that the private currency holding belongs to
currency-id | The ID of the currency that the private currency holding holds
currency-name | The name of the currency that the private currency holding holds
currency-icon-url | The URL at which the icon picture of the currency that the private currency holding holds can be found
currency-burn-rate | The annual rate at which the currency contained within the private currency holding burns, by basis point (100 = 1%) 
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
    "currency-name": "Horizon Cloud Computing dollars",
    "currency-icon-url": "/system/currencies/icons/000/000/003/original/horizon_dollars.png?1534142996",
    "currency-burn-rate": 420,
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
id | The ID of the private currency holding
owning-user-id | The ID of the user that the private currency holding belongs to
currency-id | The ID of the currency that the private currency holding holds
currency-name | The name of the currency that the private currency holding holds
currency-icon-url | The URL at which the icon picture of the currency that the private currency holding holds can be found
currency-burn-rate | The annual rate at which the currency contained within the private currency holding burns, by basis point (100 = 1%) 
amount-atomic | The amount of currency held in the private currency holding, in atomic units (each whole unit is composed of 10^10 atomic units)
transfer-out | The total amount that has been debited from the private currency holding as a result of outgoing transfers
transfer-in | The total amount that has been credited to the private currency holding as a result of incoming transfers
micro-currency-order-out | The total amount that has been debited from the private currency holding as a result of micro_currency_orders 
issuance-in | The total amount that has been credited to the private currency holding as a result of incoming issuances
burn-amount-out | The total amount that has been debited from the private currency holding as a result of the daily burnrate of the currency 
created-at | The time and date when the private currency holding was created
updated-at | The time and date when the private currency holding was last updated

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
    "id": "13",
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
      "created-at": "2018-10-10T04:33:15.801-07:00",
      "updated-at": "2018-10-10T04:33:15.801-07:00"
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
issued-currency-id | The ID of the issued currency
issued-currency-name | The name of the issued currency
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
      "sender-day-counter": 36,
      "transfer-sender-currency-holding-type": "PrivateCurrencyHolding",
      "transfer-receiver-currency-holding-type": "PrivateCurrencyHolding",
      "transfer-sender-currency-holding-id": 5,
      "sender-before-amount-atomic": 9918678637475,
      "sender-after-amount-atomic": 9418678637475,
      "transferred-currency-id": 5,
      "transferred-currency-name": "Freds Fishing Supplies dollars",
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
      "sender-day-counter": 43,
      "transfer-sender-currency-holding-type": "PrivateCurrencyHolding",
      "transfer-receiver-currency-holding-type": "PrivateCurrencyHolding",
      "transfer-sender-currency-holding-id": 5,   
      "sender-before-amount-atomic": 9395579089463,
      "sender-after-amount-atomic": 9385579089463,
      "transferred-currency-id": 5,
      "transferred-currency-name": "Freds Fishing Supplies dollars",
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

# Offers

## Get an Offer

```shell
curl 'https://api.mycurrency.com/users/3/offers/4' -H 'Accept: application/json' \
  -H 'Content-Type: application/json' -H 'Authorization: Bearer j47lbjj8r9n5yy8mup6cxqc8h70yvhnilm0g84kg0raqckus0k1koj9f75ao'
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "id": "4",
    "type": "offers",
    "attributes": {
      "offer-receiver-id": 3,
      "offer-receiver-username": "Hannibal",
      "offer-sender-id": 4,
      "offer-sender-username": "ScipioAfricanus",
      "previous-offer-id": 4,
      "offer-type": 1,
      "active": false,
      "self-cancellation": false,
      "created-at": "2018-10-11T20:18:34.813-07:00",
      "updated-at": "2018-10-11T20:18:47.253-07:00"
    },
    "relationships": {
      "proposed-transfers": {
        "data": [
          {
            "id": "3",
            "type": "proposed-transfers"
          }
        ]
      },
      "proposed-issuances": {
        "data": [
          {
            "id": "3",
            "type": "proposed-issuances"
          }
        ]
      }
    }
  },
  "included": [
    {
      "id": "3",
      "type": "proposed-transfers",
      "attributes": {
        "offer-id": 5,
        "source-currency-holding-id": 5,
        "source-currency-id": 4,
        "source-currency-name": "Pool coins",
        "currency-sender-id": 4,
        "currency-sender-username": "ScipioAfricanus",
        "amount-atomic": 50000000000,
        "active": false,
        "created-at": "2018-10-11T20:18:34.829-07:00",
        "updated-at": "2018-10-11T20:18:47.255-07:00"
      }
    },
    {
      "id": "3",
      "type": "proposed-issuances",
      "attributes": {
        "offer-id": 5,
        "source-currency-id": 3,
        "source-currency-name": "macaroon dollars",
        "currency-issuer-id": 3,
        "currency-issuer-username": "Hannibal",
        "amount-atomic": 60000000000,
        "active": false,
        "created-at": "2018-10-11T20:18:34.829-07:00",
        "updated-at": "2018-10-11T20:18:47.256-07:00"
      }
    }
  ]
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
offer-receiver-id | The ID of the user that made the offer
offer-receiver-username | The username of the user that made the offer
offer-sender-id | The ID of the user that received the offer
offer-sender-username | The username of the user that received the offer
previous-offer-id | The ID of the offer that is being counter-offered. If the first offer of an offer-chain, the value will be 0
offer-type | 0 is the offer that starts an offer chain, 1 is a counter-offer, 2 is an offer rejection, and 3 is an offer acceptance
active | Whether the offer is still active and can be countered or accepted/rejected
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
currency-sender-id | The ID of the user that would send the proposed transfer
currency-sender-username | The username of the user that would send the proposed transfer
amount-atomic | The amount of currency that is proposed to be transferred, in atomic units (each whole unit is composed of 10^10 atomic units)
active | Whether the proposed transfer is still valid or not
created-at | The time and date when the proposed transfer was created
updated-at | The time and date when the proposed transfer was last updated

### Proposed Issuances

Parameter | Description
--------- | -----------
id | The ID of the proposed issuance
offer-id | The ID of the offer that the proposed issuance is associated with
source-currency-id | The ID of the currency that is proposed to be issued
source-currency-name | The name of the currency that is proposed to be issued
currency-issuer-id | The ID of the user that would issue the proposed issuance
currency-issuer-username | The username of the user that would issue the proposed issuance
amount-atomic | The amount of currency that is proposed to be issued, in atomic units (each whole unit is composed of 10^10 atomic units)
active | Whether the proposed issuance is still valid or not
created-at | The time and date when the proposed issuance was created
updated-at | The time and date when the proposed issuance was last updated

## List Offers

```shell
curl 'https://api.mycurrency.com/users/3/offers?index_type=offer_chain&offer_id=3' \
  -H 'Accept: application/json' -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer j47lbjj8r9n5yy8mup6cxqc8h70yvhnilm0g84kg0raqckus0k1koj9f75ao'
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": "3",
      "type": "offers",
      "attributes": {
        "offer-receiver-id": 4,
        "offer-receiver-username": "ScipioAfricanus",
        "offer-sender-id": 3,
        "offer-sender-username": "Hannibal",
        "previous-offer-id": 2,
        "offer-type": 3,
        "active": false,
        "self-cancellation": false,
        "created-at": "2018-10-11T20:13:12.601-07:00",
        "updated-at": "2018-10-11T20:13:12.601-07:00"
      },
      "relationships": {
        "proposed-transfers": {
          "data": []
        },
        "proposed-issuances": {
          "data": []
        }
      }
    },
    {
      "id": "2",
      "type": "offers",
      "attributes": {
        "offer-receiver-id": 3,
        "offer-receiver-username": "Hannibal",
        "offer-sender-id": 4,
        "offer-sender-username": "ScipioAfricanus",
        "previous-offer-id": 1,
        "offer-type": 1,
        "active": false,
        "self-cancellation": false,
        "created-at": "2018-10-11T20:05:35.628-07:00",
        "updated-at": "2018-10-11T20:13:12.869-07:00"
      },
      "relationships": {
        "proposed-transfers": {
          "data": [
            {
              "id": "2",
              "type": "proposed-transfers"
            }
          ]
        },
        "proposed-issuances": {
          "data": [
            {
              "id": "2",
              "type": "proposed-issuances"
            }
          ]
        }
      }
    },
    {
      "id": "1",
      "type": "offers",
      "attributes": {
        "offer-receiver-id": 4,
        "offer-receiver-username": "ScipioAfricanus",
        "offer-sender-id": 3,
        "offer-sender-username": "Hannibal",
        "previous-offer-id": 0,
        "offer-type": 0,
        "active": false,
        "self-cancellation": false,
        "created-at": "2018-10-11T19:58:07.003-07:00",
        "updated-at": "2018-10-11T20:05:35.636-07:00"
      },
      "relationships": {
        "proposed-transfers": {
          "data": [
            {
              "id": "1",
              "type": "proposed-transfers"
            }
          ]
        },
        "proposed-issuances": {
          "data": [
            {
              "id": "1",
              "type": "proposed-issuances"
            }
          ]
        }
      }
    }
  ],
  "included": [
    {
      "id": "2",
      "type": "proposed-transfers",
      "attributes": {
        "offer-id": 2,
        "source-currency-holding-id": 5,
        "source-currency-id": 4,
        "source-currency-name": "Pool coins",
        "currency-sender-id": 4,
        "currency-sender-username": "ScipioAfricanus",
        "amount-atomic": 50000000000,
        "active": false,
        "created-at": "2018-10-11T20:05:35.645-07:00",
        "updated-at": "2018-10-11T20:13:12.757-07:00"
      }
    },
    {
      "id": "2",
      "type": "proposed-issuances",
      "attributes": {
        "offer-id": 2,
        "source-currency-id": 3,
        "source-currency-name": "macaroon dollars",
        "currency-issuer-id": 3,
        "currency-issuer-username": "Hannibal",
        "amount-atomic": 60000000000,
        "active": false,
        "created-at": "2018-10-11T20:05:35.646-07:00",
        "updated-at": "2018-10-11T20:13:12.837-07:00"
      }
    },
    {
      "id": "1",
      "type": "proposed-transfers",
      "attributes": {
        "offer-id": 1,
        "source-currency-holding-id": 5,
        "source-currency-id": 4,
        "source-currency-name": "Pool coins",
        "currency-sender-id": 4,
        "currency-sender-username": "ScipioAfricanus",
        "amount-atomic": 50000000000,
        "active": false,
        "created-at": "2018-10-11T19:58:07.038-07:00",
        "updated-at": "2018-10-11T20:05:35.641-07:00"
      }
    },
    {
      "id": "1",
      "type": "proposed-issuances",
      "attributes": {
        "offer-id": 1,
        "source-currency-id": 3,
        "source-currency-name": "macaroon dollars",
        "currency-issuer-id": 3,
        "currency-issuer-username": "Hannibal",
        "amount-atomic": 50000000000,
        "active": false,
        "created-at": "2018-10-11T19:58:07.040-07:00",
        "updated-at": "2018-10-11T20:05:35.644-07:00"
      }
    }
  ],
  "links": {
    "self": "https://api.mycurrency.com/users/3/offers?index_type=offer_chain&offer_id=3",
    "first": "https://api.mycurrency.com/users/3/offers?index_type=offer_chain&offer_id=3&page=1&per_page=25",
    "prev": null,
    "next": null,
    "last": "https://api.mycurrency.com/users/3/offers?index_type=offer_chain&offer_id=3&page=1&per_page=25"
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
offer-receiver-id | The ID of the user that made the offer
offer-receiver-username | The username of the user that made the offer
offer-sender-id | The ID of the user that received the offer
offer-sender-username | The username of the user that received the offer
previous-offer-id | The ID of the offer that is being counter-offered. If the first offer of an offer-chain, the value will be 0
offer-type | 0 is the offer that starts an offer chain, 1 is a counter-offer, 2 is an offer rejection, and 3 is an offer acceptance
active | Whether the offer is still active and can be countered or accepted/rejected
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
currency-sender-id | The ID of the user that would send the proposed transfer
currency-sender-username | The username of the user that would send the proposed transfer
amount-atomic | The amount of currency that is proposed to be transferred, in atomic units (each whole unit is composed of 10^10 atomic units)
active | Whether the proposed transfer is still valid or not
created-at | The time and date when the proposed transfer was created
updated-at | The time and date when the proposed transfer was last updated

### Proposed Issuances

Parameter | Description
--------- | -----------
id | The ID of the proposed issuance
offer-id | The ID of the offer that the proposed issuance is associated with
source-currency-id | The ID of the currency that is proposed to be issued
source-currency-name | The name of the currency that is proposed to be issued
currency-issuer-id | The ID of the user that would issue the proposed issuance
currency-issuer-username | The username of the user that would issue the proposed issuance
amount-atomic | The amount of currency that is proposed to be issued, in atomic units (each whole unit is composed of 10^10 atomic units)
active | Whether the proposed issuance is still valid or not
created-at | The time and date when the proposed issuance was created
updated-at | The time and date when the proposed issuance was last updated

## Create Offer

```shell
curl https://api.mycurrency.com/users/3/offers -d '{ "offer": {"offer_sender_id": "3", "offer_receiver_id": "4", "offer_type": "0", "proposed_transfers_attributes": [{"source_currency_holding_id": "5", "amount_atomic": "50000000000"}], "proposed_issuances_attributes": [{"source_currency_id": "3", "amount_atomic": "50000000000"}] }}' \
  -H 'Authorization: Bearer j47lbjj8r9n5yy8mup6cxqc8h70yvhnilm0g84kg0raqckus0k1koj9f75ao' \
  -H 'Accept: application/json' -H 'Content-Type: application/json'
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "id": "10",
    "type": "offers",
    "attributes": {
      "offer-receiver-id": 4,
      "offer-receiver-username": "ScipioAfricanus",
      "offer-sender-id": 3,
      "offer-sender-username": "Hannibal",
      "previous-offer-id": 0,
      "offer-type": 0,
      "active": true,
      "self-cancellation": false,
      "created-at": "2018-10-13T03:29:56.858-07:00",
      "updated-at": "2018-10-13T03:29:56.858-07:00"
    },
    "relationships": {
      "proposed-transfers": {
        "data": [
          {
            "id": "7",
            "type":"proposed-transfers"
          }
        ]
      },
      "proposed-issuances": {
        "data": [
          {
            "id": "7",
            "type": "proposed-issuances"
          }
        ]
      }
    }
  },
  "included": [
    {
      "id": "7",
      "type": "proposed-transfers",
      "attributes": {
        "offer-id": 10,
        "source-currency-holding-id": 5,
        "source-currency-id": 4,
        "source-currency-name": "Pool coins",
        "currency-sender-id": 4,
        "currency-sender-username": "ScipioAfricanus",
        "amount-atomic": 50000000000, 
        "active": true,
        "created-at": "2018-10-13T03:29:56.886-07:00",
        "updated-at": "2018-10-13T03:29:56.886-07:00"
      }
    },
    {
      "id": "7",
      "type":
      "proposed-issuances",
      "attributes": {
        "offer-id": 10,
        "source-currency-id": 3,
        "source-currency-name": "macaroon dollars",
        "currency-issuer-id": 3,
        "currency-issuer-username": "Hannibal",
        "amount-atomic": 50000000000,
        "active": true, 
        "created-at": "2018-10-13T03:29:56.887-07:00",
        "updated-at": "2018-10-13T03:29:56.887-07:00"
      }
    }
  ]
}
```

Creates an offer. 

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

### PROPOSED TRANSFER ARGUMENTS

Parameter | Type | Required | Description
--------- | ------- | ------- | -----------
source_currency_holding_id | integer | yes | The ID of the public currency holding from which the proposed transfer would be sent 
amount_atomic | integer | yes | The amount of currency that is proposed to be transferred, in atomic units (each whole unit is composed of 10^10 atomic units)

### PROPOSED ISSUANCE ARGUMENTS

Parameter | Type | Required | Description
--------- | ------- | ------- | -----------
source_currency_id | integer| yes | The ID of the currency that is proposed to be issued
amount-atomic | integer | yes | The amount of currency that is proposed to be issued, in atomic units (each whole unit is composed of 10^10 atomic units)

### RESPONSE

### Offer

Parameter | Description
--------- | -----------
id | The ID of the offer
offer-receiver-id | The ID of the user that made the offer
offer-receiver-username | The username of the user that made the offer
offer-sender-id | The ID of the user that received the offer
offer-sender-username | The username of the user that received the offer
previous-offer-id | The ID of the offer that is being counter-offered. If the first offer of an offer-chain, the value will be 0
offer-type | 0 is the offer that starts an offer chain, 1 is a counter-offer, 2 is an offer rejection, and 3 is an offer acceptance
active | Whether the offer is still active and can be countered or accepted/rejected
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
currency-sender-id | The ID of the user that would send the proposed transfer
currency-sender-username | The username of the user that would send the proposed transfer
amount-atomic | The amount of currency that is proposed to be transferred, in atomic units (each whole unit is composed of 10^10 atomic units)
active | Whether the proposed transfer is still valid or not
created-at | The time and date when the proposed transfer was created
updated-at | The time and date when the proposed transfer was last updated

### Proposed Issuances

Parameter | Description
--------- | -----------
id | The ID of the proposed issuance
offer-id | The ID of the offer that the proposed issuance is associated with
source-currency-id | The ID of the currency that is proposed to be issued
source-currency-name | The name of the currency that is proposed to be issued
currency-issuer-id | The ID of the user that would issue the proposed issuance
currency-issuer-username | The username of the user that would issue the proposed issuance
amount-atomic | The amount of currency that is proposed to be issued, in atomic units (each whole unit is composed of 10^10 atomic units)
active | Whether the proposed issuance is still valid or not
created-at | The time and date when the proposed issuance was created
updated-at | The time and date when the proposed issuance was last updated

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

This endpoint retrieves all active listings created by the logged in user and outputs their full details.

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
curl 'https://api.mycurrency.com/sub_locations/3' \
  -H 'Accept: application/json' -H 'Content-Type: application/json'
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "id": "3",
    "type": "sub-locations",
    "attributes": {
      "name": "auburn",
      "longitude": -85.48078249999999,
      "latitude": 32.6098566,
      "time-zone": "America/Chicago",
      "mid-location-id": 2
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
longitude | The longitude of the sub location
latitude | The latitude of the sub location
time-zone | The time zone of the sub location
mid-location-id | The ID of the parent mid location

## List Sub Locations

```shell
curl 'https://api.mycurrency.com/sub_locations' \
  -H 'Accept: application/json' -H 'Content-Type: application/json'
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": "3",
      "type": "sub-locations",
      "attributes": {
        "name": "auburn",
        "longitude": -85.48078249999999,
        "latitude": 32.6098566,
        "time-zone": "America/Chicago",
        "mid-location-id": 2
      }
    },
    {
      "id": "4",
      "type": "sub-locations",
      "attributes": {
        "name": "birmingham",
        "longitude": -86.8103567,
        "latitude": 33.5185892,
        "time-zone": "America/Chicago",
        "mid-location-id": 2
      }
    },
    {
      "id": "5",
      "type": "sub-locations",
      "attributes": {
        "name": "dothan",
        "longitude": -85.3904888,
        "latitude": 31.2232313,
        "time-zone": "America/Chicago",
        "mid-location-id": 2
      }
    },
    {
      "id": "6",
      "type": "sub-locations",
      "attributes": {
        "name": "florence / muscle shoals",
        "longitude": -87.66752919999999,
        "latitude": 34.7448112,
        "time-zone": "America/Chicago",
        "mid-location-id": 2
      }
    },
    {
      "id": "7",
      "type": "sub-locations",
      "attributes": {
        "name": "gadsden-anniston",
        "longitude": -85.7933312,
        "latitude": 33.7094448,
        "time-zone": "America/Chicago",
        "mid-location-id": 2
      }
    },
    {
      "id": "8",
      "type": "sub-locations",
      "attributes": {
        "name": "huntsville / decatur",
        "longitude": -86.9833417,
        "latitude": 34.6059253,
        "time-zone": "America/Chicago",
        "mid-location-id": 2
      }
    },
    {
      "id": "9",
      "type": "sub-locations",
      "attributes": {
        "name": "mobile",
        "longitude": -88.0398912,
        "latitude": 30.6953657,
        "time-zone": "America/Chicago",
        "mid-location-id": 2
      }
    },
    {
      "id": "10",
      "type": "sub-locations",
      "attributes": {
        "name": "montgomery",
        "longitude": -86.3077368,
        "latitude": 32.3792233,
        "time-zone": "America/Chicago",
        "mid-location-id": 2
      }
    },
    {
      "id": "11",
      "type": "sub-locations",
      "attributes": {
        "name": "tuscaloosa",
        "longitude": -87.56917349999999,
        "latitude": 33.2098407,
        "time-zone": "America/Chicago",
        "mid-location-id": 2
      }
    },
    {
      "id": "12",
      "type": "sub-locations",
      "attributes": {
        "name": "anchorage / mat-su",
        "longitude": -149.8714752,
        "latitude": 61.1774892,
        "time-zone": "America/Anchorage",
        "mid-location-id": 3
      }
    },
    {
      "id": "13",
      "type": "sub-locations",
      "attributes": {
        "name": "fairbanks",
        "longitude": -147.7163888,
        "latitude": 64.8377778,
        "time-zone": "America/Anchorage",
        "mid-location-id": 3
      }
    },
    {
      "id": "14",
      "type": "sub-locations",
      "attributes": {
        "name": "kenai peninsula",
        "longitude": -151.382264,
        "latitude": 60.0858486,
        "time-zone": "America/Anchorage",
        "mid-location-id": 3
      }
    },
    {
      "id": "15",
      "type": "sub-locations",
      "attributes": {
        "name": "southeast alaska",
        "longitude": -149.4936733,
        "latitude": 64.2008413,
        "time-zone": "America/Anchorage",
        "mid-location-id": 3
      }
    },
    {
      "id": "16",
      "type": "sub-locations",
      "attributes": {
        "name": "flagstaff / sedona",
        "longitude": -111.8108845,
        "latitude": 34.8704779,
        "time-zone": "America/Phoenix",
        "mid-location-id": 4
      }
    },
    {
      "id": "17",
      "type": "sub-locations",
      "attributes": {
        "name": "mohave county",
        "longitude": -113.7632828,
        "latitude": 35.2143346,
        "time-zone": "America/Phoenix",
        "mid-location-id": 4
      }
    },
    {
      "id": "18",
      "type": "sub-locations",
      "attributes": {
        "name": "phoenix",
        "longitude": -112.0740373,
        "latitude": 33.4483771,
        "time-zone": "America/Phoenix",
        "mid-location-id": 4
      }
    },
    {
      "id": "19",
      "type": "sub-locations",
      "attributes": {
        "name": "prescott",
        "longitude": -112.4685025,
        "latitude": 34.5400242,
        "time-zone": "America/Phoenix",
        "mid-location-id": 4
      }
    },
    {
      "id": "20",
      "type": "sub-locations",
      "attributes": {
        "name": "show low",
        "longitude": -110.0298327,
        "latitude": 34.2542084,
        "time-zone": "America/Phoenix",
        "mid-location-id": 4
      }
    },
    {
      "id": "21",
      "type": "sub-locations",
      "attributes": {
        "name": "sierra vista",
        "longitude": -110.2772856,
        "latitude": 31.5455001,
        "time-zone": "America/Phoenix",
        "mid-location-id": 4
      }
    },
    {
      "id": "22",
      "type": "sub-locations",
      "attributes": {
        "name": "tucson",
        "longitude": -110.9747108,
        "latitude": 32.2226066,
        "time-zone": "America/Phoenix",
        "mid-location-id": 4
      }
    },
    {
      "id": "23",
      "type": "sub-locations",
      "attributes": {
        "name": "yuma",
        "longitude": -114.6276916,
        "latitude": 32.6926512,
        "time-zone": "America/Phoenix",
        "mid-location-id": 4
      }
    },
    {
      "id": "24",
      "type": "sub-locations",
      "attributes": {
        "name": "fayetteville ",
        "longitude": -94.17185420000001,
        "latitude": 36.082156,
        "time-zone": "America/Chicago",
        "mid-location-id": 5
      }
    },
    {
      "id": "25",
      "type": "sub-locations",
      "attributes": {
        "name": "fort smith",
        "longitude": -94.39854749999999,
        "latitude": 35.3859242,
        "time-zone": "America/Chicago",
        "mid-location-id": 5
      }
    },
    {
      "id": "26",
      "type": "sub-locations",
      "attributes": {
        "name": "jonesboro",
        "longitude": -90.704279,
        "latitude": 35.84229670000001,
        "time-zone": "America/Chicago",
        "mid-location-id": 5
      }
    },
    {
      "id": "27",
      "type": "sub-locations",
      "attributes": {
        "name": "little rock",
        "longitude": -92.28959479999999,
        "latitude": 34.7464809,
        "time-zone": "America/Chicago",
        "mid-location-id": 5
      }
    }
  ],
  "links": {
    "self": "https://api.mycurrency.com/sub_locations?",
    "first": "https://api.mycurrency.com/sub_locations?page=1&per_page=25",
    "prev": null,
    "next": "https://api.mycurrency.com/sub_locations?page=2&per_page=25",
    "last": "https://api.mycurrency.com/sub_locations?page=29&per_page=25"
  },
  "meta": {
    "pagination": {
      "per-page": null,
      "total-pages": "29",
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
longitude | The longitude of the sub location
latitude | The latitude of the sub location
time-zone | The time zone of the sub location
mid-location-id | The ID of the parent mid location

## List Mid Location's Sub Locations

```shell
curl 'https://api.mycurrency.com/super_locations/2/mid_locations/2/sub_locations' \
  -H 'Accept: application/json' -H 'Content-Type: application/json'
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": "3",
      "type": "sub-locations",
      "attributes": {
        "name": "auburn",
        "longitude": -85.48078249999999,
        "latitude": 32.6098566,
        "time-zone": "America/Chicago",
        "mid-location-id": 2
      }
    },
    {
      "id": "4",
      "type": "sub-locations",
      "attributes": {
        "name": "birmingham",
        "longitude": -86.8103567,
        "latitude": 33.5185892,
        "time-zone": "America/Chicago",
        "mid-location-id": 2
      }
    },
    {
      "id": "5",
      "type": "sub-locations",
      "attributes": {
        "name": "dothan",
        "longitude": -85.3904888,
        "latitude": 31.2232313,
        "time-zone": "America/Chicago",
        "mid-location-id": 2
      }
    },
    {
      "id": "6",
      "type": "sub-locations",
      "attributes": {
        "name": "florence / muscle shoals",
        "longitude": -87.66752919999999,
        "latitude": 34.7448112,
        "time-zone": "America/Chicago",
        "mid-location-id": 2
      }
    },
    {
      "id": "7",
      "type": "sub-locations",
      "attributes": {
        "name": "gadsden-anniston",
        "longitude": -85.7933312,
        "latitude": 33.7094448,
        "time-zone": "America/Chicago",
        "mid-location-id": 2
      }
    },
    {
      "id": "8",
      "type": "sub-locations",
      "attributes": {
        "name": "huntsville / decatur",
        "longitude": -86.9833417,
        "latitude": 34.6059253,
        "time-zone": "America/Chicago",
        "mid-location-id": 2
      }
    },
    {
      "id": "9",
      "type": "sub-locations",
      "attributes": {
        "name": "mobile",
        "longitude": -88.0398912,
        "latitude": 30.6953657,
        "time-zone": "America/Chicago",
        "mid-location-id": 2
      }
    },
    {
      "id": "10",
      "type": "sub-locations",
      "attributes": {
        "name": "montgomery",
        "longitude": -86.3077368,
        "latitude": 32.3792233,
        "time-zone": "America/Chicago",
        "mid-location-id": 2
      }
    },
    {
      "id": "11",
      "type": "sub-locations",
      "attributes": {
        "name": "tuscaloosa",
        "longitude": -87.56917349999999,
        "latitude": 33.2098407,
        "time-zone": "America/Chicago",
        "mid-location-id": 2
      }
    }
  ],
  "links": {
    "self": "https://api.mycurrency.com/super_locations/2/mid_locations/2/sub_locations?",
    "first": "https://api.mycurrency.com/super_locations/2/mid_locations/2/sub_locations?page=1&per_page=25",
    "prev": null,
    "next": null,
    "last": "https://api.mycurrency.com/super_locations/2/mid_locations/2/sub_locations?page=1&per_page=25"
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
longitude | The longitude of the sub location
latitude | The latitude of the sub location
time-zone | The time zone of the sub location
mid-location-id | The ID of the parent mid location

## List Super Location's Sub Locations

```shell
curl 'https://api.mycurrency.com/super_locations/2/sub_locations' \
  -H 'Accept: application/json' -H 'Content-Type: application/json'
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": "3",
      "type": "sub-locations",
      "attributes": {
        "name": "auburn",
        "longitude": -85.48078249999999,
        "latitude": 32.6098566,
        "time-zone": "America/Chicago",
        "mid-location-id": 2
      }
    },
    {
      "id": "4",
      "type": "sub-locations",
      "attributes": {
        "name": "birmingham",
        "longitude": -86.8103567,
        "latitude": 33.5185892,
        "time-zone": "America/Chicago",
        "mid-location-id": 2
      }
    },
    {
      "id": "5",
      "type": "sub-locations",
      "attributes": {
        "name": "dothan",
        "longitude": -85.3904888,
        "latitude": 31.2232313,
        "time-zone": "America/Chicago",
        "mid-location-id": 2
      }
    },
    {
      "id": "6",
      "type": "sub-locations",
      "attributes": {
        "name": "florence / muscle shoals",
        "longitude": -87.66752919999999,
        "latitude": 34.7448112,
        "time-zone": "America/Chicago",
        "mid-location-id": 2
      }
    },
    {
      "id": "7",
      "type": "sub-locations",
      "attributes": {
        "name": "gadsden-anniston",
        "longitude": -85.7933312,
        "latitude": 33.7094448,
        "time-zone": "America/Chicago",
        "mid-location-id": 2
      }
    },
    {
      "id": "8",
      "type": "sub-locations",
      "attributes": {
        "name": "huntsville / decatur",
        "longitude": -86.9833417,
        "latitude": 34.6059253,
        "time-zone": "America/Chicago",
        "mid-location-id": 2
      }
    },
    {
      "id": "9",
      "type": "sub-locations",
      "attributes": {
        "name": "mobile",
        "longitude": -88.0398912,
        "latitude": 30.6953657,
        "time-zone": "America/Chicago",
        "mid-location-id": 2
      }
    },
    {
      "id": "10",
      "type": "sub-locations",
      "attributes": {
        "name": "montgomery",
        "longitude": -86.3077368,
        "latitude": 32.3792233,
        "time-zone": "America/Chicago",
        "mid-location-id": 2
      }
    },
    {
      "id": "11",
      "type": "sub-locations",
      "attributes": {
        "name": "tuscaloosa",
        "longitude": -87.56917349999999,
        "latitude": 33.2098407,
        "time-zone": "America/Chicago",
        "mid-location-id": 2
      }
    },
    {
      "id": "12",
      "type": "sub-locations",
      "attributes": {
        "name": "anchorage / mat-su",
        "longitude": -149.8714752,
        "latitude": 61.1774892,
        "time-zone": "America/Anchorage",
        "mid-location-id": 3
      }
    },
    {
      "id": "13",
      "type": "sub-locations",
      "attributes": {
        "name": "fairbanks",
        "longitude": -147.7163888,
        "latitude": 64.8377778,
        "time-zone": "America/Anchorage",
        "mid-location-id": 3
      }
    },
    {
      "id": "14",
      "type": "sub-locations",
      "attributes": {
        "name": "kenai peninsula",
        "longitude": -151.382264,
        "latitude": 60.0858486,
        "time-zone": "America/Anchorage",
        "mid-location-id": 3
      }
    },
    {
      "id": "15",
      "type": "sub-locations",
      "attributes": {
        "name": "southeast alaska",
        "longitude": -149.4936733,
        "latitude": 64.2008413,
        "time-zone": "America/Anchorage",
        "mid-location-id": 3
      }
    },
    {
      "id": "16",
      "type": "sub-locations",
      "attributes": {
        "name": "flagstaff / sedona",
        "longitude": -111.8108845,
        "latitude": 34.8704779,
        "time-zone": "America/Phoenix",
        "mid-location-id": 4
      }
    },
    {
      "id": "17",
      "type": "sub-locations",
      "attributes": {
        "name": "mohave county",
        "longitude": -113.7632828,
        "latitude": 35.2143346,
        "time-zone": "America/Phoenix",
        "mid-location-id": 4
      }
    },
    {
      "id": "18",
      "type": "sub-locations",
      "attributes": {
        "name": "phoenix",
        "longitude": -112.0740373,
        "latitude": 33.4483771,
        "time-zone": "America/Phoenix",
        "mid-location-id": 4
      }
    },
    {
      "id": "19",
      "type": "sub-locations",
      "attributes": {
        "name": "prescott",
        "longitude": -112.4685025,
        "latitude": 34.5400242,
        "time-zone": "America/Phoenix",
        "mid-location-id": 4
      }
    },
    {
      "id": "20",
      "type": "sub-locations",
      "attributes": {
        "name": "show low",
        "longitude": -110.0298327,
        "latitude": 34.2542084,
        "time-zone": "America/Phoenix",
        "mid-location-id": 4
      }
    },
    {
      "id": "21",
      "type": "sub-locations",
      "attributes": {
        "name": "sierra vista",
        "longitude": -110.2772856,
        "latitude": 31.5455001,
        "time-zone": "America/Phoenix",
        "mid-location-id": 4
      }
    },
    {
      "id": "22",
      "type": "sub-locations",
      "attributes": {
        "name": "tucson",
        "longitude": -110.9747108,
        "latitude": 32.2226066,
        "time-zone": "America/Phoenix",
        "mid-location-id": 4
      }
    },
    {
      "id": "23",
      "type": "sub-locations",
      "attributes": {
        "name": "yuma",
        "longitude": -114.6276916,
        "latitude": 32.6926512,
        "time-zone": "America/Phoenix",
        "mid-location-id": 4
      }
    },
    {
      "id": "24",
      "type": "sub-locations",
      "attributes": {
        "name": "fayetteville ",
        "longitude": -94.17185420000001,
        "latitude": 36.082156,
        "time-zone": "America/Chicago",
        "mid-location-id": 5
      }
    },
    {
      "id": "25",
      "type": "sub-locations",
      "attributes": {
        "name": "fort smith",
        "longitude": -94.39854749999999,
        "latitude": 35.3859242,
        "time-zone": "America/Chicago",
        "mid-location-id": 5
      }
    },
    {
      "id": "26",
      "type": "sub-locations",
      "attributes": {
        "name": "jonesboro",
        "longitude": -90.704279,
        "latitude": 35.84229670000001,
        "time-zone": "America/Chicago",
        "mid-location-id": 5
      }
    },
    {
      "id": "27",
      "type": "sub-locations",
      "attributes": {
        "name": "little rock",
        "longitude": -92.28959479999999,
        "latitude": 34.7464809,
        "time-zone": "America/Chicago",
        "mid-location-id": 5
      }
    }
  ],
  "links": {
    "self": "https://api.mycurrency.com/super_locations/2/sub_locations?",
    "first": "https://api.mycurrency.com/super_locations/2/sub_locations?page=1&per_page=25",
    "prev": null,
    "next": "https://api.mycurrency.com/super_locations/2/sub_locations?page=2&per_page=25",
    "last": "https://api.mycurrency.com/super_locations/2/sub_locations?page=17&per_page=25"
  },
  "meta": {
    "pagination": {
      "per-page": null,
      "total-pages": "17",
      "total-count": "418"
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
longitude | The longitude of the sub location
latitude | The latitude of the sub location
time-zone | The time zone of the sub location
mid-location-id | The ID of the parent mid location

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
      "id": "198",
      "type": "sub-locations",
      "attributes": {
        "name": "minneapolis / st paul",
        "longitude": -93.20099979999999,
        "latitude": 44.9374831,
        "time-zone": "America/Chicago",
        "mid-location-id": 25
      }
    },
    {
      "id": "197",
      "type": "sub-locations",
      "attributes": {
        "name": "mankato",
        "longitude": -93.99939959999999,
        "latitude": 44.1635775,
        "time-zone": "America/Chicago",
        "mid-location-id": 25
      }
    },
    {
      "id": "201",
      "type": "sub-locations",
      "attributes": {
        "name": "st cloud",
        "longitude": -94.16324039999999,
        "latitude": 45.5579451,
        "time-zone": "America/Chicago",
        "mid-location-id": 25
      }
    },
    {
      "id": "199",
      "type": "sub-locations",
      "attributes": {
        "name": "rochester ",
        "longitude": -92.4801989,
        "latitude": 44.0121221,
        "time-zone": "America/Chicago",
        "mid-location-id": 25
      }
    },
    {
      "id": "407",
      "type": "sub-locations",
      "attributes": {
        "name": "eau claire",
        "longitude": -91.4984941,
        "latitude": 44.811349,
        "time-zone": "America/Chicago",
        "mid-location-id": 51
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
longitude | The longitude of the sub location
latitude | The latitude of the sub location
time-zone | The time zone of the sub location
mid-location-id | The ID of the parent mid location

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
      "product-quantity": 1,
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
ordering-user-id | The username of the user that made the order, only shown if the logged in user is the owner of the store that received the order
source-currency-holding-id | The ID of the public or private currency holding that the micro currency order spent from, only shown if the logged in user made the order
source-currency-holding-type | Whether the currency holding that the micro currency order spent from is a "PublicCurrencyHolding" or a "PrivateCurrencyHolding", only shown if the logged in user made the order
before-amount-atomic | The balance, in atomic units, of the currency holding before it was debited by the micro currency order, only shown if the logged in user made the order
after-amount-atomic | The balance, in atomic units, of the currency holding after it was debited by the micro currency order, only shown if the logged in user made the order
day-counter | The day counter of the currency holding when it was debited by the micro currency order, only shown if the logged in user made the order
amount-atomic | The amount of currency spent, in atomic units (each whole unit is composed of 10^10 atomic units)
product-id | The ID of the product that was ordered
product-name | The name of the product that was ordered
product-quantity | The quantity of the product that was ordered
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
        "product-quantity": 1,
        "created-at": "2018-10-03T00:39:37.860-07:00",
        "updated-at": "2018-10-03T00:39:37.860-07:00"
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
        "product-quantity": 1,
        "created-at": "2018-10-03T00:43:31.756-07:00",
        "updated-at": "2018-10-03T00:43:31.756-07:00"
      }
    },
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
        "product-quantity": 1,
        "created-at": "2018-10-03T01:58:03.223-07:00",
        "updated-at": "2018-10-03T01:58:03.223-07:00"
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

This endpoint retrieves a user's orders. 

### HTTP Request

`GET https://api.mycurrency.com/users/<USER-ID>/offers?index_type={}`

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
ordering-user-id | The username of the user that made the order, only shown if the logged in user is the owner of the store that received the order
source-currency-holding-id | The ID of the public or private currency holding that the micro currency order spent from, only shown if the logged in user made the order
source-currency-holding-type | Whether the currency holding that the micro currency order spent from is a "PublicCurrencyHolding" or a "PrivateCurrencyHolding", only shown if the logged in user made the order
before-amount-atomic | The balance, in atomic units, of the currency holding before it was debited by the micro currency order, only shown if the logged in user made the order
after-amount-atomic | The balance, in atomic units, of the currency holding after it was debited by the micro currency order, only shown if the logged in user made the order
day-counter | The day counter of the currency holding when it was debited by the micro currency order, only shown if the logged in user made the order
amount-atomic | The amount of currency spent, in atomic units (each whole unit is composed of 10^10 atomic units)
product-id | The ID of the product that was ordered
product-name | The name of the product that was ordered
product-quantity | The quantity of the product that was ordered
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
      "product-quantity": 1,
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
ordering-user-id | The username of the user that made the order, only shown if the logged in user is the owner of the store that received the order
source-currency-holding-id | The ID of the public or private currency holding that the micro currency order spent from, only shown if the logged in user made the order
source-currency-holding-type | Whether the currency holding that the micro currency order spent from is a "PublicCurrencyHolding" or a "PrivateCurrencyHolding", only shown if the logged in user made the order
before-amount-atomic | The balance, in atomic units, of the currency holding before it was debited by the micro currency order, only shown if the logged in user made the order
after-amount-atomic | The balance, in atomic units, of the currency holding after it was debited by the micro currency order, only shown if the logged in user made the order
day-counter | The day counter of the currency holding when it was debited by the micro currency order, only shown if the logged in user made the order
amount-atomic | The amount of currency spent, in atomic units (each whole unit is composed of 10^10 atomic units)
product-id | The ID of the product that was ordered
product-name | The name of the product that was ordered
product-quantity | The quantity of the product that was ordered
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
      "id": "1",
      "type": "notices",
      "attributes": {
        "title": "You made an issuance to your account",
        "message": "\nDetails of issuance:\n\nDate Issuance was made: Sunday, August 12, 2018 at 01:17AM\n1000.0000000000 Calm dollars sent from Hannibal to the private holding of Hannibal",
        "seen": true,
        "read": false,
        "notice-type": 4,
        "user-id": 3,
        "created-at": "2018-08-12T01:17:31.289-07:00",
        "updated-at": "2018-10-16T22:12:46.399-07:00"
      }
    },
    {
      "id": "2",
      "type": "notices",
      "attributes": {
        "title": "You made an issuance to your account",
        "message": "\nDetails of issuance:\n\nDate Issuance was made: Sunday, August 19, 2018 at 02:11PM\n1000.0000000000 ACME Toon Shop dollars sent from Hannibal to the private holding of Hannibal",
        "seen": true,
        "read": false,
        "notice-type": 4,
        "user-id": 3,
        "created-at": "2018-08-19T14:11:16.976-07:00",
        "updated-at": "2018-10-16T22:12:46.404-07:00"
      }
    },
    {
      "id": "3",
      "type": "notices",
      "attributes": {
        "title": "You made an issuance to your account",
        "message": "\nDetails of issuance:\n\nDate Issuance was made: Sunday, August 19, 2018 at 02:24PM\n1000.0000000000 macaroon dollars sent from Hannibal to the private holding of Hannibal",
        "seen": true,
        "read": false,
        "notice-type": 4,
        "user-id": 3,
        "created-at": "2018-08-19T14:24:09.649-07:00",
        "updated-at": "2018-10-16T22:12:46.408-07:00"
      }
    },
    {
      "id": "7",
      "type": "notices",
      "attributes": {
        "title": "You made an issuance to ScipioAfricanus",
        "message": "\nDetails of issuance:\n\nDate Issuance was made: Saturday, September 15, 2018 at 08:37PM\n10.0000000000 macaroon dollars sent from Hannibal to the private holding of ScipioAfricanus",
        "seen": true,
        "read": false,
        "notice-type": 4,
        "user-id": 3,
        "created-at": "2018-09-15T20:37:38.352-07:00",
        "updated-at": "2018-10-16T22:12:46.413-07:00"
      }
    },
    {
      "id": "10",
      "type": "notices",
      "attributes": {
        "title": "You received a transfer from ScipioAfricanus",
        "message": "\nDetails of transfer made:\n\nDate Transfer was made: Sunday, September 16, 2018 at 01:06PM\n1.0000000000 macaroon dollars sent from the private holding of ScipioAfricanus to the private holding of Hannibal",
        "seen": true,
        "read": false,
        "notice-type": 3,
        "user-id": 3,
        "created-at": "2018-09-16T13:06:56.467-07:00",
        "updated-at": "2018-10-16T22:12:46.417-07:00"
      }
    },
    {
      "id": "12",
      "type": "notices",
      "attributes": {
        "title": "You received a transfer from ScipioAfricanus",
        "message": "\nDetails of transfer made:\n\nDate Transfer was made: Sunday, September 16, 2018 at 01:08PM\n1.0000000000 macaroon dollars sent from the private holding of ScipioAfricanus to the private holding of Hannibal",
        "seen": true,
        "read": false,
        "notice-type": 3,
        "user-id": 3,
        "created-at": "2018-09-16T13:08:27.258-07:00",
        "updated-at": "2018-10-16T22:12:46.422-07:00"
      }
    },
    {
      "id": "13",
      "type": "notices",
      "attributes": {
        "title": "You made a transfer to your account",
        "message": "\nDetails of transfer made:\n\nDate Transfer was made: Sunday, September 16, 2018 at 01:26PM\n5.0000000000 ACME Toon Shop dollars sent from the private holding of Hannibal to the public holding of Hannibal",
        "seen": true,
        "read": false,
        "notice-type": 3,
        "user-id": 3,
        "created-at": "2018-09-16T13:26:52.086-07:00",
        "updated-at": "2018-10-16T22:12:46.426-07:00"
      }
    },
    {
      "id": "16",
      "type": "notices",
      "attributes": {
        "title": "You received a transfer from ScipioAfricanus",
        "message": "\nDetails of transfer made:\n\nDate Transfer was made: Tuesday, October 02, 2018 at 04:33AM\n1.0000000000 Pool coins sent from the private holding of ScipioAfricanus to the private holding of Hannibal",
        "seen": true,
        "read": false,
        "notice-type": 3,
        "user-id": 3,
        "created-at": "2018-10-02T04:33:05.434-07:00",
        "updated-at": "2018-10-16T22:12:46.430-07:00"
      }
    },
    {
      "id": "17",
      "type": "notices",
      "attributes": {
        "title": "You made an issuance to ScipioAfricanus",
        "message": "\nDetails of issuance:\n\nDate Issuance was made: Tuesday, October 02, 2018 at 03:58PM\n10.0000000000 macaroon dollars sent from Hannibal to the private holding of ScipioAfricanus",
        "seen": true,
        "read": false,
        "notice-type": 4,
        "user-id": 3,
        "created-at": "2018-10-02T15:58:40.164-07:00",
        "updated-at": "2018-10-16T22:12:46.435-07:00"
      }
    },
    {
      "id": "20",
      "type": "notices",
      "attributes": {
        "title": "You received a transfer from ScipioAfricanus",
        "message": "\nDetails of transfer made:\n\nDate Transfer was made: Wednesday, October 03, 2018 at 12:19AM\n1.0000000000 Freds Fishing Supplies dollars sent from the private holding of ScipioAfricanus to the private holding of Hannibal",
        "seen": true,
        "read": false,
        "notice-type": 3,
        "user-id": 3,
        "created-at": "2018-10-03T00:19:35.227-07:00",
        "updated-at": "2018-10-16T22:12:46.439-07:00"
      }
    }
  ],
  "links": {
    "self": "https://api.mycurrency.com/users/3/notices?per_page=10",
    "first": "https://api.mycurrency.com/users/3/notices?page=1&per_page=10",
    "prev": null,
    "next": "https://api.mycurrency.com/users/3/notices?page=2&per_page=10",
    "last": "https://api.mycurrency.com/users/3/notices?page=4&per_page=10"
  },
  "meta": {
    "pagination": {
      "per-page": "10",
      "total-pages": "4",
      "total-count": "35"
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
      "holding-user-id": 3
      "holding-user-username": "Hannibal" 
      "product-id": 7,
      "product-name": "fishing rod",
      "product-quantity": 1,
      "store-id": 3,
      "code": "ARCW97G8QJBZXZ5F7TC0K",
      "expiration": "2018-11-02T01:58:03.223-07:00",
      "redeemed": false,
      "created-at": "2018-10-03T01:58:03.467-07:00",
      "updated-at": "2018-10-03T01:58:03.467-07:00"
    }
  }
}
```

This endpoint retrieves a particular voucher. The logged in user must be either the holder of the voucher or the owner of the store at which the voucher is redeemable in order to view the voucher's details.

### HTTP Request

`GET https://api.mycurrency.com/vouchers/<ID>`

<aside class="notice">
Authentication: the request requires the OAuth access-token associated with the User referenced by the ID 
</aside>

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the voucher
micro-currency-order-id | The ID of the micro currency order that purchased the voucher
holding-user-id | The ID of the user that purchased the voucher
holding-user-username | The username of the user that purchased the voucher
product-id | The ID of the product for which the voucher is redeemable for
product-name | The name of the product for which the voucher is redeemable for
product-quantity | The quantity of the product for which the voucher is redeemable for
store-id | The ID of the store at which the product that the voucher can be redeemed for is sold at
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
      "id": "1",
      "type": "vouchers",
      "attributes": {
        "micro-currency-order-id": 1,
        "holding-user-id": 3
        "holding-user-username": "Hannibal" 
        "product-id": 5,
        "product-name": "fishing bait",
        "product-quantity": 1,
        "store-id": 3,
        "code": "NQG05A1DGHC1ATZ0PLM5B",
        "expiration": "2018-11-02T00:39:37.861-07:00",
        "redeemed": false,
        "created-at": "2018-10-03T00:39:37.942-07:00",
        "updated-at": "2018-10-03T00:39:37.942-07:00"
      }
    },
    {
      "id": "2",
      "type": "vouchers",
      "attributes": {
        "micro-currency-order-id": 2,
        "holding-user-id": 3
        "holding-user-username": "Hannibal" 
        "product-id": 6,
        "product-name": "tackle",
        "product-quantity": 1,
        "store-id": 3,
        "code": "QT3W19RS0RMX07CCG5XWG",
        "expiration": "2018-11-02T00:43:31.756-07:00",
        "redeemed": false,
        "created-at": "2018-10-03T00:43:31.834-07:00",
        "updated-at": "2018-10-03T00:43:31.834-07:00"
      }
    },
    {
      "id": "3",
      "type": "vouchers",
      "attributes": {
        "micro-currency-order-id": 3,
        "holding-user-id": 3
        "holding-user-username": "Hannibal" 
        "product-id": 7,
        "product-name": "fishing rod",
        "product-quantity": 1,
        "store-id": 3,
        "code": "ARCW97G8QJBZXZ5F7TC0K",
        "expiration": "2018-11-02T01:58:03.223-07:00",
        "redeemed": false,
        "created-at": "2018-10-03T01:58:03.467-07:00",
        "updated-at": "2018-10-03T01:58:03.467-07:00"
      }
    }
  ],
  "links": {
    "self": "https://api.mycurrency.com/vouchers?holding_user_id=3",
    "first": "https://api.mycurrency.com/vouchers?holding_user_id=3&page=1&per_page=25",
    "prev": null,
    "next": "https://api.mycurrency.com/vouchers?holding_user_id=3&page=2&per_page=25",
    "last": "https://api.mycurrency.com/vouchers?holding_user_id=3&page=0&per_page=25"
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
product-id | The ID of the product for which the voucher is redeemable for
product-name | The name of the product for which the voucher is redeemable for
product-quantity | The quantity of the product for which the voucher is redeemable for
store-id | The ID of the store at which the product that the voucher can be redeemed for is sold at
code | The secret code that the voucher holder must reveal to the store owner in order to redeem their voucher, only shown if the logged-in user is the voucher holder
expiration | The date at which the voucher expires, which is one month after it is issued to the buyer
redeemed | Whether the voucher has been redeemed or not
created-at | The time and date when the voucher was created
updated-at | The time and date when the voucher was last updated

## Update Voucher

```shell
curl -X PUT 'https://api.mycurrency.com/users/4/vouchers/1' \
  -d '{"voucher": { "redeemed": true, "code": "NQG05A1DGHC1ATZ0PLM5B" } }' \
  -H 'Accept: application/json' -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer j47lbjj8r9n5yy8mup6cxqc8h70yvhnilm0g84kg0raqckus0k1koj9f75ao'
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "id": "1",
    "type": "vouchers",
    "attributes": {
      "micro-currency-order-id": 1,
      "holding-user-id": 3,
      "holding-user-username": "Hannibal",
      "product-id": 5,
      "product-name": "fishing bait",
      "product-quantity": 1,
      "store-id": 3,
      "expiration": "2018-11-02T00:39:37.861-07:00",
      "redeemed": true,
      "created-at": "2018-10-03T00:39:37.942-07:00",
      "updated-at": "2018-10-20T01:45:15.259-07:00"
    }
  }
}
```

Updates a voucher.

### HTTP Request

`POST https://api.mycurrency.com/users/<USER-ID>/vouchers/<ID>`

<aside class="notice">
Authentication: the request requires the OAuth access-token associated with the User referenced by the ID 
</aside>

### ARGUMENTS

Parameter | Type | Required | Description
--------- | ------- | ------- | -----------
redeemed | boolean | yes | Whether the voucher is has been redeemed or not
code | string | required if :redeemed has a value of true | The voucher's secret code, must be provided to redeem voucher

### RESPONSE

Parameter | Description
--------- | -----------
id | The ID of the voucher
micro-currency-order-id | The ID of the micro currency order that purchased the voucher
holding-user-id | The ID of the user that purchased the voucher
holding-user-username | The username of the user that purchased the voucher
product-id | The ID of the product for which the voucher is redeemable for
product-name | The name of the product for which the voucher is redeemable for
product-quantity | The quantity of the product for which the voucher is redeemable for
store-id | The ID of the store at which the product that the voucher can be redeemed for is sold at
code | The secret code that the voucher holder must reveal to the store owner in order to redeem their voucher, only shown if the logged-in user is the voucher holder
expiration | The date at which the voucher expires, which is one month after it is issued to the buyer
redeemed | Whether the voucher has been redeemed or not
created-at | The time and date when the voucher was created
updated-at | The time and date when the voucher was last updated
