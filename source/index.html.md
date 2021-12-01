---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell

toc_footers:
  - <a href='#'>Contact for API User and Password</a>
  - <a href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true

code_clipboard: true

meta:
  - name: description
    content: Documentation for the Aricos Bank Accout Remittance API
---

# Introduction

Aricos is middleware that is make transfer transaction easy, fast, secure, reliable and accessible from all around the World. We provide simple APIs which you can use to send money to all banks in Indonesia quickly and securely.

Aricos is organized around REST. We use built-in HTTP features and HTTP verbs and we return all responses in JSON.

## Bank Account Remittance Overview

Use the Remittance API to transfer funds instantly to any bank in Indonesia at any time, including holidays and weekends. Due to restrictions from the banks, we’re unable to disburse when the bank channel are offline or when they fail.

The remittance flow is as follows:

1. [Prefund](#prefund) your Instamoney account balance

2. [Create a customer](#create-customer) which represents the sender, and a customer which represents the recipient of the remittance. You’ll get an id for each

3. [Create a remittance](#create-remittance), attaching ids of the sender and recipient

4. We run this remittance through our risk-scoring system. If necessary, our compliance team will contact you for additional verification of information

5. We process the remittance and return a callback with the status of the remittance. You may also query the status of a remittance anytime via the [Get Remittance](get-remittance) API

# Getting Started

## Set Up Your Account

To use our Bank Account Remittance APIs, register for an Aricos account by contacting your account manager or our support team.

You can start testing our APIs immediately in development environment. When you are ready to process live transactions, contact your account manager to go live.

## Retrieve Your API Account

Before you access all our features, you have to register your account to access all our API Feature. Our support team will give you the information of your account to login into our API.

To successfully authenticate with Aricos's API, you must append a colon and Base 64 encode the API key. All API requests should be made over HTTPS instead of HTTP (all calls made over plain HTTP will fail).

You can access our development end-point url to https://dev.aricos.co.id and production end-point url to https://aricos.co.id.

## Start Testing!

You may test our APIs by sending requests in the development environment--You will automatically get IDR balances in your development account balance for testing. Requests made in the development environment will not hit the banking networks and will not cost you anything.

## Postman Collection

The easiest way to get started using our API is to use our Postman Collection. Postman is a free client application that enables you to make calls to APIs easily. To make integrating with our APIs easier, we've created a Postman Collection of our endpoints so that you can test our APIs more easily.

The following is an outline of actions to get started with Postman.

1. Install [Postman](https://www.getpostman.com/).

2. Download our <a href="https://github.com/juniusvariant/aricos-bankaccount-remittance/raw/main/source/images/logo.png" download> Postman collection</a>.

3. Open Postman and Import the Aricos API Postman Collection.

4. Set up the collection’s Authorization header.

	a. Under the Authorization tab of each folder, the default authorization type is set to “Inherit auth from parent”. The “Inherit auth from parent” setting indicates that every request in the folder by default uses the authorization type from the parent.

	b. Edit the Instamoney API collection.

	c. Under “Authorization”, paste your secret API key into the Username. Use your Development Key to test in the development environment, and your Live Key to send live transactions.

	d. Click Update.

	e. This authorization key will be automatically used for each request in the collection.

5. Try getting [your balance](#balance).

	a. Click on the Balances folder and click Get Balances.

	b. Hit the blue Send button.

	c. In the response area, you should get your latest cash balance.

6. If you can query your balance successfully, you’re all set up! Feel free to explore our other APIs by selecting it in the collection and launching it.

# Account

## Account Register

All information about your account and password will be provide by our support team by email. So if you're not getting any information about your account for development testing or for go live, please let us know.

## Account Login

```shell
# With shell, you can just pass the correct header with each request

POST https://dev.aricos.co.id/api/v1/login
```

You have to login to get token access before you do a request to our APIs. You have to keep every token from our request response every time you want to access another request.

### Login Request

> Login Example Request:

```shell

curl https://dev.aricos.co.id/api/v1/login -X POST \
-H 'Content-Type: application/json' \
--data '
{
"username": "Junius",
"password": "123456"}'

```
> Make sure to replace `username` and `password` with your account credential.

Parameter | Description
--------- | -----------
username | The User Account That Provided By Our Team
password | The User Password That Provided By Our Team

<aside class="notice">
   Make sure to replace <code>username</code> and <code>password</code> with your account credential.
</aside>

### Login Response

> Login Example Response:

```shell
{
    "success": {
        "code": 200,
        "message": "Login Success"
    },
    "data": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOlwvXC9hcmljb3NhcmcuY28uaWRcL2FwaVwvdjFcL2xvZ2luIiwiaWF0IjoxNTczNzQzNTA3LCJleHAiOjE1NzM3NDcxMDcsIm5iZiI6MTU3Mzc0MzUwNywianRpIjoiVjBGS2JmSnlLOXBYUU00RyIsInN1YiI6IjVkYzRkYjZiYWVlNjEzNjllOSIsInBydiI6Ijg3ZTBhZjFlZjlmZDE1ODEyZmRlYzk3MTUzYTE0ZTBiMDQ3NTQ2YWEifQ.fei1OIN0nDU9-hzT_yAMp_cqs53YmBPIOvjf2sUtf0E"
}
```

Parameter | Description
--------- | -----------
success | Response That Given When You're Success To Access Our API
failed | Response That Given When You're Failed To Access Our API
data | Bearer Token That You Have To Use Everytime When You Want To Access Our APIs

# Authentication

> To authorize, use this code:

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
```

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here" \
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
```

> Make sure to replace `meowmeowmeow` with your API key.

Kittn uses API keys to allow access to the API. You can register a new Kittn API key at our [developer portal](http://example.com/developers).

Kittn expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: meowmeowmeow`

<aside class="notice">
You must replace <code>meowmeowmeow</code> with your personal API key.
</aside>

# Kittens

## Get All Kittens

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get()
```

```shell
curl "http://example.com/api/kittens" \
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let kittens = api.kittens.get();
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

`GET http://example.com/api/kittens`

### Query Parameters

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
curl "http://example.com/api/kittens/2" \
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
curl "http://example.com/api/kittens/2" \
  -X DELETE \
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

