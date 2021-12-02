---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell

toc_footers:
  - <a href='#'>Contact for API User and Password</a>
  - <a href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>

includes:
  - data-references
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
> Make sure to replace `username` and `password` with your account credential. </br>

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

# Balance

## Prefund Your Balance

Your balance refers to stored value in your Aricos account which can be sent out in remittances or withdrawn. Before you do any remittances, you will first have to add to your account balance ("prefund"). You can do this by transferring funds to Aricos's bank accounts. You can will get information about our bank account from our team so you can do prefund. After you have transferred the funds, please save the proof of transfer.

If you have prefunding to your account, the balance should be detected and updated in your account in 15-30 minutes. If prefunding failed or have technical issues, please contact our support team with the proof of transfer to complete the prefund.

## Get Balance

```shell
POST https://dev.aricos.co.id/api/v1/mitra/balance?account_type={account_type}
```

Retrieves your account balance. There are two balances: <b>CASH</b> refers to funds available for you to remit or withdraw. <b>HOLDING</b> refers to funds which are in transit.

## Get Balance Request

> Get Balance Example Request: </br>

```shell
curl https://dev.aricos.co.id/api/v1/mitra/balance -X POST \
-H 'authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOlwvXC8xMjcuMC4wLjE6ODAwMFwvYXBpXC92MVwvbG9naW4iLCJpYXQiOjE1NzI4NTA0ODMsImV4cCI6MTU3Mjg1NDA4MywibmJmIjoxNTcyODUwNDgzLCJqdGkiOiJNOEVqcmFTQlJsbWt3RGxzIiwic3ViIjoiNWRiZmNiMzE5MzgxODU3NTFmIiwicHJ2IjoiODdlMGFmMWVmOWZkMTU4MTJmZGVjOTcxNTNhMTRlMGIwNDc1NDZhYSJ9.mkZN7ipwisjUZcNJWthcIJvyUJGYvcy9BctEv8V6WMU'
--data '{"account_type":"CASH"}'
```

Parameter | Description
--------- | -----------
account_type </br><small><span style="color:grey">*optional* </span></small> </br> <small><span style="color:grey">*default* </span> `CASH`</small> | `string` The selected account type (`CASH` or `HOLDING`).

## Get Balance Response

> Get Balance Example Response:

```shell
{
  "balance": 1241231
}
```

Parameter | Description
--------- | -----------
balance | The balance remaining in your cash account

# Customers

## Customer Data

Customers are your end-customers, which include the sender and recipient of a remittance. You can perform recurring remittances with the same customers.

Use the following Customers API to manage your customers with Aricos. Your customers’ personal data is retained to comply with regulatory requirements for fund transfer services in Indonesia, and also allows Aricos to fulfill Know-Your-Client obligations.

## Create Customer Request

```shell
POST https://dev.aricos.co.id/api/v1/customer/register
```

Create customer for your end-customers for the sender and recipient.

> Create Customer Example Request:

```shell
curl https://dev.aricos.co.id/api/v1/customer/register \
   -H 'Content-Type: application/json' \
   -H 'authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOlwvXC8xMjcuMC4wLjE6ODAwMFwvYXBpXC92MVwvbG9naW4iLCJpYXQiOjE1NzI4NTA0ODMsImV4cCI6MTU3Mjg1NDA4MywibmJmIjoxNTcyODUwNDgzLCJqdGkiOiJNOEVqcmFTQlJsbWt3RGxzIiwic3ViIjoiNWRiZmNiMzE5MzgxODU3NTFmIiwicHJ2IjoiODdlMGFmMWVmOWZkMTU4MTJmZGVjOTcxNTNhMTRlMGIwNDc1NDZhYSJ9.mkZN7ipwisjUZcNJWthcIJvyUJGYvcy9BctEv8V6WMU' \
   --data '
     {
      "reference_id": "r-1234",
      "customer_type": "INDIVIDUAL",
      "given_name": "Ichwano",
      "surname": "Sembo",
      "address": {
          "country_code": "ID",
          "province": "DKI Jakarta",
          "city": "Jakarta Selatan",
          "line_1": "Jl. Senayan 1 No.15"
      },
      "date_of_birth": "11-01-1990",
      "identification": {
          "ktp_number": "0987654321320987",
          "npwp_number": "098765432132098"
      },
      "account_details": {
          "account_code": "BNI",
          "account_number": "123456780",
          "account_holder_name": "Ichwano"
      },
      "email": "ichwano@email.com",
      "mobile_number": "+628111555777",
      "phone_number": "+622199990000"
    }
   '
```

Parameter | Description
--------- | -----------
reference_id </br><small><span style="color:grey">*required* </span></small>| `string` Your unique id for this customer. </br></br><span>`Characters` <span style="color:grey"><small>Special and alphanumeric</small></span></br><span style="color:grey">Maximum length <small>100 maximum characters</small></span>
customer_type </br><small><span style="color:grey">*required* </span></small>| `string` Legal entity. Valid values: `INDIVIDUAL` or `BUSINESS`
given_name </br><small><span style="color:grey">*conditionally required* </span></small>| `string` Given name(s). Required if `customer_type` is `INDIVIDUAL`. Only allowed if `customer_type` is `INDIVIDUAL`
surname </br><small><span style="color:grey">*optional* </span></small>| `string` Surname or family name, if applicable. Only allowed if `customer_type` is `INDIVIDUAL`
business_name </br><small><span style="color:grey">*conditionally required* </span></small>| `string` Required if `customer_type` is `BUSINESS`. Only allowed if `customer_type` is `BUSINESS`
address </br><small><span style="color:grey">*optional* </span></small>| `object` Customer's address
address.country_code </br><small><span style="color:grey">*required* </span></small>| `string` Customer’s country. 2-letter ISO 3166-2 country code. Refer to code standard [here](https://www.nationsonline.org/oneworld/country_code_list.htm). If `customer_type` is `BUSINESS`, the country in which the corporate entity is registered. If `customer_type` is `INDIVIDUAL`, a country in which the customer holds nationality
address.state </br><small><span style="color:grey">*optional* </span></small>| `string` Customer’s state
address.province </br><small><span style="color:grey">*optional* </span></small>| `string` Customer’s province
address.city </br><small><span style="color:grey">*optional* </span></small>| `string` Customer’s city
address.suburb </br><small><span style="color:grey">*optional* </span></small>| `string` Customer’s suburb
address.post_code </br><small><span style="color:grey">*optional* </span></small>| `string` Customer’s postal code
address.line_1 </br><small><span style="color:grey">*optional* </span></small>| `string` First line of customer’s address. Typically used for building name and / or apartment number
address.line_2 </br><small><span style="color:grey">*optional* </span></small>| `string` Second line of customer’s address. Typically used for building name and / or apartment number
date_of_birth </br><small><span style="color:grey">*optional* </span></small>| `string` Date of Birth. Only allowed if `customer_type` is `INDIVIDUAL`. ISO 8601 format YYYY-MM-DD
date_of_registration </br><small><span style="color:grey">*optional* </span></small>| `string` Date of Registration. Only allowed if `customer_type` is `BUSINESS`. ISO 8601 format YYYY-MM-DD
identification </br><small><span style="color:grey">*optional* </span></small>| `object` A legal document that verifies the identity of the customer
identification.ktp_number </br><small><span style="color:grey">*optional* </span></small>| `string` Kartu Tanda Penduduk (national identity card number) of the customer.</br></br> Only allowed if `customer_type` is `INDIVIDUAL`</br> `Characters` <span style="color:grey"><small>16 characters</small></span>
identification.npwp_number </br><small><span style="color:grey">*optional* </span></small>| `string` Nomor Pokok Wajib Pajak (tax number) of the customer.</br></br> Only allowed if `customer_type` is `INDIVIDUAL`</br> `Characters` <span style="color:grey"><small>15 characters</small></span>
identification.drivers_license </br><small><span style="color:grey">*optional* </span></small>| `string` Surat Izin Mengemudi (driver’s licence) number of the customer.</br></br> Only allowed if `customer_type` is `INDIVIDUAL`</br> `Characters` <span style="color:grey"><small>14 characters</small></span>
identification.passport_number </br><small><span style="color:grey">*optional* </span></small>| `string` Passport number of the customer.</br></br> Only allowed if `customer_type` is `INDIVIDUAL`</br></br> If provided, should provide `passport_country`. In the case of multiple passports, please choose the passport of the country closest to Indonesia
identification.passport_country </br><small><span style="color:grey">*conditionally required* </span></small>| `string` Passport country of the customer.</br></br> Only allowed if `customer_type` is `INDIVIDUAL`. 2-letter ISO 3166-2 country code. Refer to code standard [here](https://www.nationsonline.org/oneworld/country_code_list.htm).</br></br> Required if `passport_numberis` provided.
identification.business_tax_id </br><small><span style="color:grey">*optional* </span></small>| `string` Tax identification number of the business in its country of registration.</br></br> Examples:</br> - Nomor Pokok Wajib Pajak for indonesian businesses</br> - Business Registration number for Hong Kong businesses</br> - Unique Entity Number for Singaporean businesses</br></br> Only allowed if `customer_type` is `BUSINESS`. If provided, should provide `business_tax_id_country`.
identification.business_tax_id_country </br><small><span style="color:grey">*conditionally required* </span></small>| `string` Country for tax identification number of the business.</br></br> Only allowed if `customer_type` is `BUSINESS`. 2-letter ISO 3166-2 country code. Refer to code standard [here](https://www.nationsonline.org/oneworld/country_code_list.htm). </br></br> Required if `business_tax_id` is provided.
account_details </br><small><span style="color:grey">*optional* </span></small>| `object` Customer’s bank account details
account_details.account_code </br><small><span style="color:grey">*optional* </span></small>| `string` The code of the account, can be bank codes (BCA, MANDIRI, etc.) or ewallet codes (GOPAY, OVO, etc.). Only Indonesian banks and ewallets supported currently. See [Account Codes]()
account_details.account_number </br><small><span style="color:grey">*optional* </span></small>| `string` Destination bank account number. If disbursing to an e-wallet, phone number registered with the e-wallet account.</br></br> <span style="color:grey">`Characters` <small>Numeric and hyphens</small></br> `BCA required length` <small>10 characters</small></br>` Other banks maximum length` <small>No maximum characters</small></br> `Other banks minimum length` <small>1 character</small></br> `E-wallets` <small>Phone number registered with the e-wallet(Example: 0812XXXXXX)</small></span></br></br> <small>*** We support remittances to virtual accounts of major banks (BRI, BNI, Mandiri, CIMB Niaga, Permata, BTN, and NOBU Bank).<br> *** We support remittances to major e-wallets (GoPay, OVO, and Mandiri e-cash).</small>
account_details.account_holder_name </br><small><span style="color:grey">*optional* </span></small>| `string` Name of account holder per the bank's or e-wallet's records</br> <span style="color:grey">`Characters` <small>Special and alphanumeric</small></br> `Maximum length` <small>No maximum characters</small></br> `Minimum length` <small>1 character</small></span>
email </br><small><span style="color:grey">*optional* </span></small>| `string` Customer’s email address. Recommended if you want to notify the customer of the transaction statusShould include the top-level domain name</br> Example: abc@email.com
mobile_number </br><small><span style="color:grey">*optional* </span></small>| `string` Customer’s mobile number with international prefix. Recommended if you want to notify the customer of the transaction status</br> Example: +62812XXXXXX
phone_number </br><small><span style="color:grey">*optional* </span></small>| `string` Customer’s land line or alternate phone number with international prefix</br> Example: +62812XXXXXX

## Create Customer Response

We return a customer object if the call succeeded.

### Create Customer Errors

> Create Customer Example Response:

```shell
{
  "id": "5c1774e76966b43a5b8198fb",
  "external_id": "r-1234",
  "customer_type": "INDIVIDUAL",
  "given_name": "Ichwano",
  "surname": "Sembo",
  "address": {
      "country_code": "ID",
      "province": "DKI Jakarta",
      "city": "Jakarta Selatan",
      "line_1": "Jl. Senayan 1 No.15"
  },
  "date_of_birth": "11-01-1990",
  "identification": {
      "ktp_number": "0987654321320987",
      "npwp_number": "098765432132098"
  },
  "account_details": {
      "account_code": "BNI",
      "account_number": "123456780",
      "account_holder_name": "Ichwano"
  },
  "email": "ichwano@email.com",
  "mobile_number": "+628111555777",
  "phone_number": "+622199990000",
  "created": "2018-12-12T13:50:12.000Z",
  "updated": "2018-12-12T13:50:12.000Z"
}
```

Error Code | Description
--------- | -----------
API_VALIDATION_ERROR</br> <span class="badge">400</span>| Inputs are failing validation. The errors field contains details about which fields are violating validation</br> <span class="badge error">No retry</span>
INVALID_JSON_FORMAT</br> <span class="badge">400</span>| The request body is not a valid JSON format</br> <span class="badge error">No retry</span>
ACCOUNT_CODE_NOT_SUPPORTED_ERROR</br> <span class="badge">400</span>| The code of the account is currently not supported</br> <span class="badge error">No retry</span>
ACCOUNT_NUMBER_ERROR</br> <span class="badge">400</span>| Where account_code is “BCA”, account_number input needs to be 10 digits. Please check the account number length before retrying.</br> <span class="badge error">No retry</span>
DUPLICATE_CUSTOMER_ERROR</br> <span class="badge">400</span>| The external_id entered has been used before. Please enter a unique external_id and try again.</br> <span class="badge error">No retry</span>

## Update Customer Request

Updates an existing customer

```shell
PUT https://dev.aricos.co.id/api/v1/customer/update/{reference_id}
```

> Update Customer Example Request:

```shell
curl https://dev.aricos.co.id/api/v1/customer/update/r-1234 -X PUT \
   -H 'authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOlwvXC8xMjcuMC4wLjE6ODAwMFwvYXBpXC92MVwvbG9naW4iLCJpYXQiOjE1NzI4NTA0ODMsImV4cCI6MTU3Mjg1NDA4MywibmJmIjoxNTcyODUwNDgzLCJqdGkiOiJNOEVqcmFTQlJsbWt3RGxzIiwic3ViIjoiNWRiZmNiMzE5MzgxODU3NTFmIiwicHJ2IjoiODdlMGFmMWVmOWZkMTU4MTJmZGVjOTcxNTNhMTRlMGIwNDc1NDZhYSJ9.mkZN7ipwisjUZcNJWthcIJvyUJGYvcy9BctEv8V6WMU' \
   -H 'Content-Type: application/json' \
   -H 'cache-control: no-cache' \
   --data '{
     {
      "given_name": "Ahmad",
      "surname": "Shahab",
      "phone_number": "+622199990000"
    }
   }'
```

Parameter | Description
--------- | -----------
reference_id </br><small><span style="color:grey">*required* </span></small>| `string` Your unique id for this customer. </br></br><span>`Characters` <span style="color:grey"><small>Special and alphanumeric</small></span></br><span style="color:grey">Maximum length <small>100 maximum characters</small></span>
customer_type </br><small><span style="color:grey">*required* </span></small>| `string` Legal entity. Valid values: `INDIVIDUAL` or `BUSINESS`
given_name </br><small><span style="color:grey">*conditionally required* </span></small>| `string` Given name(s). Required if `customer_type` is `INDIVIDUAL`. Only allowed if `customer_type` is `INDIVIDUAL`
surname </br><small><span style="color:grey">*optional* </span></small>| `string` Surname or family name, if applicable. Only allowed if `customer_type` is `INDIVIDUAL`
business_name </br><small><span style="color:grey">*conditionally required* </span></small>| `string` Required if `customer_type` is `BUSINESS`. Only allowed if `customer_type` is `BUSINESS`
address </br><small><span style="color:grey">*optional* </span></small>| `object` Customer's address
address.country_code </br><small><span style="color:grey">*required* </span></small>| `string` Customer’s country. 2-letter ISO 3166-2 country code. Refer to code standard [here](https://www.nationsonline.org/oneworld/country_code_list.htm). If `customer_type` is `BUSINESS`, the country in which the corporate entity is registered. If `customer_type` is `INDIVIDUAL`, a country in which the customer holds nationality
address.state </br><small><span style="color:grey">*optional* </span></small>| `string` Customer’s state
address.province </br><small><span style="color:grey">*optional* </span></small>| `string` Customer’s province
address.city </br><small><span style="color:grey">*optional* </span></small>| `string` Customer’s city
address.suburb </br><small><span style="color:grey">*optional* </span></small>| `string` Customer’s suburb
address.post_code </br><small><span style="color:grey">*optional* </span></small>| `string` Customer’s postal code
address.line_1 </br><small><span style="color:grey">*optional* </span></small>| `string` First line of customer’s address. Typically used for building name and / or apartment number
address.line_2 </br><small><span style="color:grey">*optional* </span></small>| `string` Second line of customer’s address. Typically used for building name and / or apartment number
date_of_birth </br><small><span style="color:grey">*optional* </span></small>| `string` Date of Birth. Only allowed if `customer_type` is `INDIVIDUAL`. ISO 8601 format YYYY-MM-DD
date_of_registration </br><small><span style="color:grey">*optional* </span></small>| `string` Date of Registration. Only allowed if `customer_type` is `BUSINESS`. ISO 8601 format YYYY-MM-DD
identification </br><small><span style="color:grey">*optional* </span></small>| `object` A legal document that verifies the identity of the customer
identification.ktp_number </br><small><span style="color:grey">*optional* </span></small>| `string` Kartu Tanda Penduduk (national identity card number) of the customer.</br></br> Only allowed if `customer_type` is `INDIVIDUAL`</br> `Characters` <span style="color:grey"><small>16 characters</small></span>
identification.npwp_number </br><small><span style="color:grey">*optional* </span></small>| `string` Nomor Pokok Wajib Pajak (tax number) of the customer.</br></br> Only allowed if `customer_type` is `INDIVIDUAL`</br> `Characters` <span style="color:grey"><small>15 characters</small></span>
identification.drivers_license </br><small><span style="color:grey">*optional* </span></small>| `string` Surat Izin Mengemudi (driver’s licence) number of the customer.</br></br> Only allowed if `customer_type` is `INDIVIDUAL`</br> `Characters` <span style="color:grey"><small>14 characters</small></span>
identification.passport_number </br><small><span style="color:grey">*optional* </span></small>| `string` Passport number of the customer.</br></br> Only allowed if `customer_type` is `INDIVIDUAL`</br></br> If provided, should provide `passport_country`. In the case of multiple passports, please choose the passport of the country closest to Indonesia
identification.passport_country </br><small><span style="color:grey">*conditionally required* </span></small>| `string` Passport country of the customer.</br></br> Only allowed if `customer_type` is `INDIVIDUAL`. 2-letter ISO 3166-2 country code. Refer to code standard [here](https://www.nationsonline.org/oneworld/country_code_list.htm).</br></br> Required if `passport_numberis` provided.
identification.business_tax_id </br><small><span style="color:grey">*optional* </span></small>| `string` Tax identification number of the business in its country of registration.</br></br> Examples:</br> - Nomor Pokok Wajib Pajak for indonesian businesses</br> - Business Registration number for Hong Kong businesses</br> - Unique Entity Number for Singaporean businesses</br></br> Only allowed if `customer_type` is `BUSINESS`. If provided, should provide `business_tax_id_country`.
identification.business_tax_id_country </br><small><span style="color:grey">*conditionally required* </span></small>| `string` Country for tax identification number of the business.</br></br> Only allowed if `customer_type` is `BUSINESS`. 2-letter ISO 3166-2 country code. Refer to code standard [here](https://www.nationsonline.org/oneworld/country_code_list.htm). </br></br> Required if `business_tax_id` is provided.
account_details </br><small><span style="color:grey">*optional* </span></small>| `object` Customer’s bank account details
account_details.account_code </br><small><span style="color:grey">*optional* </span></small>| `string` The code of the account, can be bank codes (BCA, MANDIRI, etc.) or ewallet codes (GOPAY, OVO, etc.). Only Indonesian banks and ewallets supported currently. See [Account Codes]()
account_details.account_number </br><small><span style="color:grey">*optional* </span></small>| `string` Destination bank account number. If disbursing to an e-wallet, phone number registered with the e-wallet account.</br></br> <span style="color:grey">`Characters` <small>Numeric and hyphens</small></br> `BCA required length` <small>10 characters</small></br>` Other banks maximum length` <small>No maximum characters</small></br> `Other banks minimum length` <small>1 character</small></br> `E-wallets` <small>Phone number registered with the e-wallet(Example: 0812XXXXXX)</small></span></br></br> <small>*** We support remittances to virtual accounts of major banks (BRI, BNI, Mandiri, CIMB Niaga, Permata, BTN, and NOBU Bank).<br> *** We support remittances to major e-wallets (GoPay, OVO, and Mandiri e-cash).</small>
account_details.account_holder_name </br><small><span style="color:grey">*optional* </span></small>| `string` Name of account holder per the bank's or e-wallet's records</br> <span style="color:grey">`Characters` <small>Special and alphanumeric</small></br> `Maximum length` <small>No maximum characters</small></br> `Minimum length` <small>1 character</small></span>
email </br><small><span style="color:grey">*optional* </span></small>| `string` Customer’s email address. Recommended if you want to notify the customer of the transaction statusShould include the top-level domain name</br> Example: abc@email.com
mobile_number </br><small><span style="color:grey">*optional* </span></small>| `string` Customer’s mobile number with international prefix. Recommended if you want to notify the customer of the transaction status</br> Example: +62812XXXXXX
phone_number </br><small><span style="color:grey">*optional* </span></small>| `string` Customer’s land line or alternate phone number with international prefix</br> Example: +62812XXXXXX

## Update Customer Response

We return the updated customer object if the call succeeded.

### Update Customer Errors

> Update Customer Example Response:

```shell
{
  "id": "5c1774e76966b43a5b8198fb",
  "external_id": "r-1234",
  "customer_type": "INDIVIDUAL",
  "given_name": "Ichwano",
  "surname": "Sembo",
  "address": {
      "country_code": "ID",
      "province": "DKI Jakarta",
      "city": "Jakarta Selatan",
      "line_1": "Jl. Senayan 1 No.15"
  },
  "date_of_birth": "11-01-1990",
  "identification": {
      "ktp_number": "0987654321320987",
      "npwp_number": "098765432132098"
  },
  "account_details": {
      "account_code": "BNI",
      "account_number": "123456780",
      "account_holder_name": "Ichwano"
  },
  "email": "ichwano@email.com",
  "mobile_number": "+628111555777",
  "phone_number": "+622199990000",
  "created": "2018-12-12T13:50:12.000Z",
  "updated": "2018-12-12T13:50:12.000Z"
}
```

Error Code | Description
--------- | -----------
API_VALIDATION_ERROR</br> <span class="badge">400</span>| Inputs are failing validation. The errors field contains details about which fields are violating validation</br> <span class="badge error">No retry</span>
INVALID_JSON_FORMAT</br> <span class="badge">400</span>| The request body is not a valid JSON format</br> <span class="badge error">No retry</span>
ACCOUNT_CODE_NOT_SUPPORTED_ERROR</br> <span class="badge">400</span>| The code of the account is currently not supported</br> <span class="badge error">No retry</span>
ACCOUNT_NUMBER_ERROR</br> <span class="badge">400</span>| Where account_code is “BCA”, account_number input needs to be 10 digits. Please check the account number length before retrying.</br> <span class="badge error">No retry</span>
DUPLICATE_CUSTOMER_ERROR</br> <span class="badge">400</span>| The external_id entered has been used before. Please enter a unique external_id and try again.</br> <span class="badge error">No retry</span>
CUSTOMER_NOT_FOUND_ERROR</br> <span class="badge">400</span>| Could not find customer.</br> <span class="badge error">No retry</span>

## Get Customer With external_id Request

```shell
GET https://dev.aricos.co.id/api/v1/customer/search/{reference_id}
```

Returns an array with a single object which contains the customer corresponding to the unique external_id. Returns an empty array if there is no customer corresponding to the external_id.

> Get Customer With external_id Example Request:

```shell
curl https://dev.aricos.co.id/api/v1/customer/search/r-1234 -X GET \
  -H 'authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOlwvXC8xMjcuMC4wLjE6ODAwMFwvYXBpXC92MVwvbG9naW4iLCJpYXQiOjE1NzI4NTA0ODMsImV4cCI6MTU3Mjg1NDA4MywibmJmIjoxNTcyODUwNDgzLCJqdGkiOiJNOEVqcmFTQlJsbWt3RGxzIiwic3ViIjoiNWRiZmNiMzE5MzgxODU3NTFmIiwicHJ2IjoiODdlMGFmMWVmOWZkMTU4MTJmZGVjOTcxNTNhMTRlMGIwNDc1NDZhYSJ9.mkZN7ipwisjUZcNJWthcIJvyUJGYvcy9BctEv8V6WMU'
```

Query Parameter | Description
--------- | -----------
external_id </br><small><span style="color:grey">*optional* </span></small>| `string` Unique ID you provided in the Create Customer request</br> <span style="color:grey"><small>The external_id must match the external_id used at customer creation precisely</small></span>

> Get Customer With external_id Example Response:

```shell
[{
  "id": "5c1774e76966b43a5b8198fb",
  "external_id": "r-1234",
  "customer_type": "INDIVIDUAL",
  "given_name": "Ichwano",
  "surname": "Sembo",
  "address": {
      "country_code": "ID",
      "province": "DKI Jakarta",
      "city": "Jakarta Selatan",
      "line_1": "Jl. Senayan 1 No.15"
  },
  "date_of_birth": "11-01-1990",
  "identification": {
      "ktp_number": "0987654321320987",
      "npwp_number": "098765432132098"
  },
  "account_details": {
      "account_code": "BNI",
      "account_number": "123456780",
      "account_holder_name": "Ichwano"
  },
  "email": "ichwano@email.com",
  "mobile_number": "+628111555777",
  "phone_number": "+622199990000",
  "created": "2018-12-12T13:50:12.000Z",
  "updated": "2018-12-12T13:50:12.000Z"
}]
```

# Bank Account Remittance

Our Bank Account Remittance APIs allow you to send remittances from your Aricos Account on behalf of a sender to your designated recipient. Only IDR-IDR transfers supported currently.

<aside class="notice">
   Please note that you are unable to cancel a remittance request once it has been made.
</aside>

