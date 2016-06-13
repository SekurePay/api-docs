---
title: API Reference

language_tabs:
  - shell

toc_footers:
  - <a href='https://sekurepay.com/users/sign_up'>Sign Up for SekurePay</a>
  - <a href='https://sekurepay.com/merchants/docs'>SekurePay Documentation</a>

includes:
  - errors

search: true
---

# Introduction

The SekurePay API is based around keeping it as simple as possible while keeping the highest level of security at the forefront of all that we do. The API is organized around [REST](https://en.wikipedia.org/wiki/Representational_state_transfer) and is designed to have resource oriented URLs and uses HTTP response codes to indicate errors. [JSON](http://json.org) is returned by all API responses, with all connections to SekurePay's API is done through HTTPS over HSTS. 


# Authentication

Authenticate your account when using the API by including your secret API key in the request. Authentication is made over [HTTPS](http://en.wikipedia.org/wiki/HTTPS) and we do not support any requests over plain HTTP. Calls made over plain HTTP will fail.

Each endpoint is protected and authenticated using [HTTP Basic Auth](https://en.wikipedia.org/wiki/Basic_access_authentication). Provide your API key as the basic auth username. You do not need to provide a password.

Your api key must be kept secure, which you may change at any time, by refreshing it within your merchant account settings. You can see your account’s API keys, and roll them if necessary, in your [account API settings](https://sekurepay.com/account/api_settings).


# Orders

The orders API allows you to create, and view a single order.

## Create an Order

This API allows you to create a new order.

```shell
curl -X "POST" "https://sekurepay.com/api/v1/orders" \
	-H "Authorization: Basic MDA2YmVhMWUtYjZhOS00OTNjLWE2NGEtMGEyMmViMzA2MGE4OioqKioqIEhpZGRlbiBjcmVkZW50aWFscyAqKioqKg==" \
	-H "Content-Type: application/json" \
	-d "{
		"id":"MERCHANT_GENERATED_ORDER_ID",
		"sub_total_cents": 10000,
		"shipping_amount_cents": 200,
		"total_cents": 12200,
		"currency": "USD",
		"items":
		[{
			"description": "51 inch TV",
			"amount_cents": "10000"
		}],
		"taxes":
		[{
			"description": "GST",
			"amount_cents": "500"
		}]}"
```


> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "name": "Fluffums",
    "breed": "calico",
    "fluffiness": 6,
    "cuteness": 7
  },
  {
    "id": 2,
    "name": "Max",
    "breed": "unknown",
    "fluffiness": 5,
    "cuteness": 10
  }
]
```

This endpoint retrieves all kittens.

### HTTP Request

`POST https://sekurepay.com/api/v1/orders`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

## Retrieve an Order

This API allows you retrieve and view a specific order.

```shell
curl -X "GET" "http://sekurepay.com/api/v1/orders/merchant_generated_order_id" \
	-H "Authorization: Basic MDA2YmVhMWUtYjZhOS00OTNjLWE2NGEtMGEyMmViMzA2MGE4OioqKioqIEhpZGRlbiBjcmVkZW50aWFscyAqKioqKg==" \```

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

