---
title: API Reference

language_tabs:
  - shell

search: true
---

# Introduction

The user watch list API allows registered end consumers to save catalog assets to be watched at a later time. Watch list items are saved per associated consumer, each of which have just one watch list known as the <em>default</em> watch list.

There are two versions of this service, v1 and v2.  The version to use is specified in the URL as you can see on the examples that follow.

You can view examples of calls to the API in the area to the right.

# Authentication

```shell
curl 'http://player.ooyala.com/watchlist/<api_version>/list?account_token=<acount_token>'
```

> Make sure to replace `<account_token>` with the one provided by the Gigya authentication service and <code>api_version</code> with either v1 or v2.

Our user authentication and identity management is integrated with Gigya.  Gigya is a third party vendor that handles identity management of our clients from all types of social networks such as facebook, linkedin, google plus, etc.

<aside class="warning">
The watch list API expects the <code>account_token</code> URL parameter to be included in all API requests to the server.
</aside>

# Watch Lists

## Get The Default Watch List

```shell
curl 'http://player.ooyala.com/watchlist/<api_version>/list?account_token=<acount_token>'
```

> The above command returns JSON structured like this:

```json
{
  "_shards": {
    "failed": 0,
    "successful": 4,
    "total": 4
  },
  "hits": {
    "hits": [],
    "max_score": 0.053994928,
    "total": 3
  },
  "timed_out": false,
  "took": 3
}
```

This endpoint retrieves the metadata asociated with the ids saven in the default watch list.

### HTTP Request

`GET http://player.ooyala.com/watchlist/:api_version/list`

### Query Parameters

Parameter | Description | Type    | Required
--------- | ----------- | ------- | --------
account_token | Authentication token provided by Gigya | String | True
api_version | The version of the api the query is directed to. Must be either v1 OR v2 | String | True

<aside class="success">
Remember — all request to the Watch List API must be authenticated!
</aside>

<aside class="notice">
The internal <code>hits</code> field in the response has a complicated structure that is supressed in the examples.
</aside>

## Add an item

```shell
curl -XPOST -H 'Content-Type: application/json' 'http://player.ooyala.com/watchlist/<api_version>/list?embed_code=9pMGJ4cDowP-bX8-aITZyNyuHH7dyeOk&account_token=<acount_token>' -d '{}'
```

> The above command returns JSON structured like this:

```json
{
  "item_id": "9pMGJ4cDowP-bX8-aITZyNyuHH7dyeOk",
  "position": 1,
  "created_at": "2015-06-03T11:59:31.91646667-05:00",
  "updated_at": "2015-06-03T11:59:31.91646667-05:00"
}
```

This endpoint adds a item to the default watch list.


### HTTP Request

`POST http://player.ooyala.com/watchlist/:api_version/list`

### URL Parameters

Parameter | Description | Type    | Required
--------- | ----------- | ------- | --------
account_token | Authentication token provided by Gigya | String | True
api_version | The version of the api the query is directed to. Must be either v1 OR v2 | String | True
embed_code | The id of the item to be added to the default watch list | String | True

## Delete and item

```shell
curl -XDELETE 'http://player.ooyala.com/watchlist/<api_version>/list?embed_code=9pMGJ4cDowP-bX8-aITZyNyuHH7dyeOk&account_token=<acount_token>'
```

> The above command returns JSON structured like this:

```json
{
  "success": true
}
```

This endpoint deletes a item from the default watch list.

### HTTP Request

`DELETE http://player.ooyala.com/watchlist/:api_version/list`

### URL Parameters

Parameter | Description | Type    | Required
--------- | ----------- | ------- | --------
account_token | Authentication token provided by Gigya | String | True
api_version | The version of the api the query is directed to. Must be either v1 OR v2 | String | True
embed_code | The id of the item to be added to the default watch list | String | True

## Check for an item existance in the default watch list

```shell
curl 'http://player.ooyala.com/watchlist/<api_version>/list/has?embed_code=9pMGJ4cDowP-bX8-aITZyNyuHH7dyeOk&account_token=<acount_token>'
```

> The above command returns JSON structured like this:

```json
{
  "response": false
}
```

This endpoint checks for the existance a item in the default watch list.

### HTTP Request

`GET http://player.ooyala.com/watchlist/:api_version/list/has`

### URL Parameters

Parameter | Description | Type    | Required
--------- | ----------- | ------- | --------
account_token | Authentication token provided by Gigya | String | True
api_version | The version of the api the query is directed to. Must be either v1 OR v2 | String | True
embed_code | The id of the item to be added to the default watch list | String | True
