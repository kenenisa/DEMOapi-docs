# API Docs

> :warning: **THIS IS A DEMO**: Ony includes docs for auth and some types are not proved
*all requests must be prefixed `/api`*

## Contents

- [API Docs](#api-docs)
  - [Contents](#contents)
  - [Routes](#routes)
    - [Settings](#settings)
    - [Verify](#verify)
    - [Voice sms](#voice-sms)
    - [Sign up](#sign-up)
    - [Send OTP](#send-otp)
    - [Login](#login)
    - [Verify OTP](#verify-otp)
    - [Forgot password](#forgot-password)
    - [Reset password](#reset-password)
    - [Polygon](#polygon)
    - [Logout](#logout)
  - [Auth](#auth)
    - [Facebook](#facebook)
    - [Google](#google)
  - [User profile](#user-profile)
    - [Change password](#change-password)
    - [Update location](#update-location)
    - [Details](#details)
    - [Update profile](#update-profile)
  - [Services](#services)
    - [Services](#services-1)
    - [Service geo fencing](#service-geo-fencing)
    - [Rate provider](#rate-provider)
  - [Request](#request)
    - [Send request](#send-request)
    - [Cancel request](#cancel-request)
    - [Check request](#check-request)
    - [Show providers](#show-providers)
    - [Update request](#update-request)
  - [History](#history)
    - [Trips](#trips)
    - [Upcoming trips](#upcoming-trips)
    - [Trip details](#trip-details)
    - [Upcoming trip details](#upcoming-trip-details)
  - [Payment](#payment)
    - [Payment](#payment-1)
    - [Add money](#add-money)
    - [Estimated fee](#estimated-fee)
    - [Help](#help)
  - [Promo code](#promo-code)
    - [Promo codes](#promo-codes)
    - [Add promo code](#add-promo-code)
  - [Card](#card)
    - [Insert Card](#insert-card)
  - [Location](#location)
    - [Insert Location](#insert-location)
  - [Passbook](#passbook)
    - [Wallet passbook](#wallet-passbook)
    - [Promo passbook](#promo-passbook)
  - [Others](#others)
    - [Chat push](#chat-push)
    - [Package](#package)
  - [Types](#types)
    - [User](#user)
    - [Error](#error)





---
## Routes

### Settings

`GET` */settings*

gets setting values

**Request**

`Nothing`

**Response**

*response type `json`*

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| serviceTypes | String | value for service types |
| api_key | String | api key |
| android_api_key | String | device specific api key |
| ios_api_key | String | device specific api key |
| stripe_secret_key | String | payment method secret api key |
| stripe_publishable_key | String | payment method publishable api key |
| stripe_currency | String | currency for payment |

---
### Verify

`POST` */verify*

verifies if email address is unique and valid

**Request**

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| email | String | Email address to be verified |

**Response**

*response type `json`*

*`On success`*

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| message | String | Returns a human readable success message |

*`On error`*

Returns type [Error](#error)

---
### Voice sms

`POST` */voice/sms*

Generates and responds with an OTP code

**Request**

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| username | Integer | Mobile number to generate the OTP for starting with `9` |

**Response**

*response type `json`*

*`On success`*

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| otp | String | Returns the OTP code generated |

*`On error`* Code `500`  is thrown

---
### Sign up

`POST` */signup*

Used to sign up users

**Request** `ALL values are required`

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| social_unique_id | String | `Required` if login by facebook or google|
| device_type | String | type of the device. values are `android` or `ios`|
| device_token | String | Used to remember the device |
| device_id | String | Used to remember the device |
| login_by | String | Method used for login. values are `facebook` or `google` |
| first_name | String | first name max 255 char|
| last_name | String | last name max 255 char|
| email | String | email max 255 char and unique to user |
| mobile | Integer | mobile number unique to user |
| password | String | password min 6 char |
| emergency_contact1 | String | emergency contact |

**Response**

*response type `json`*

*`On success`*

Responds with type [User](#user)

*`On error`* Code `500`  is thrown

---
### Send OTP

`POST` */send/otp*

Generates and responds with an OTP code over sms

**Request**

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| username | Integer | Mobile number to generate the OTP for with full format |

**Response**

*response type `json`*

*`On success`*

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| otp | String | Returns the OTP code generated |

*`On error`* Code `500`  is thrown

---
### Login

`POST` */login*

Used to login users

**Request** `ALL values are required`

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| device_type | String | type of the device. values are `android` or `ios`|
| device_token | String | Used to remember the device |
| username | String | user name for login|
| country_code | Integer | country code |
| password | String | password min 6 char |

**Response**

*response type `json`*

*`On success`*

Responds with type `Response`

*`On error`* Code `500`  is thrown

---
### Verify OTP

`POST` */verify/otp*

Verified otp sent over sms or voice

**Request**

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| otp | Integer | OTP code send over either sms or voice |
| username | Integer | Mobile number to generate the OTP for with full format |
| device_token | String | Used to remember the device |

**Response**

*response type `json`*

*`On success`*

Responds with type `Response`

*`On error`* Code `500`  is thrown

---

### Forgot password

`POST` */forgot/password*

generates and send an OTP Code for a mobile number of an existing user

**Request**

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| mobile | String | Mobile number to generate and send OTP for with full format |

**Response**

*response type `json`*

*`On success`*

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| message | String | Returns a human readable success message |

*`On error`*

Returns type [Error](#error)

---

### Reset password

`POST` */reset/password*

resets password for a user

**Request**

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| id | Integer | user id the reset password for |
| password | String | the new confirmed password (min 6 char) |

**Response**

*response type `json`*

*`On success`*

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| message | String | Returns a human readable success message |

*`On error`*

Returns type [Error](#error)

---

### Polygon

`GET` */polygon*

`undefined` in the code

---

### Logout

`POST` */logout*

Used to logout user

**Request**

`Nothing`

**Response**

*response type `json`*

*`On success`*

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| message | String | Returns a human readable success message |

*`On error`*

Returns type [Error](#error) with code `500`

---

## Auth

### Facebook

`POST` */auth/facebook*

Used to login user using facebook login

**Request**

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| device_type | String | type of the device. values are `android` or `ios`|
| device_token | String | Used to remember the device |
| device_id | String | device_id |
| accessToken | String | Token from the other api|
| login_by | String | login by `facebook`, `google` or `manual` |

**Response**

*response type `json`*

*`On success`*

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| status | Boolean | Indicates the success status of the request |
| token_type | String | Default value `Bearer` |
| access_token | String | Api access token |

*`On error`*

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| status | Boolean | Indicates the success status of the request |
| message | String | Returns a human readable error message |

### Google

`POST` */auth/google*

Used to login user using google login

**Request**

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| device_type | String | type of the device. values are `android` or `ios`|
| device_token | String | Used to remember the device |
| device_id | String | device_id |
| accessToken | String | Token from the other api|
| login_by | String | login by `facebook`, `google` or `manual` |

**Response**

*response type `json`*

*`On success`*

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| status | Boolean | Indicates the success status of the request |
| token_type | String | Default value `Bearer` |
| access_token | String | Api access token |

*`On error`*

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| status | Boolean | Indicates the success status of the request |
| message | String | Returns a human readable error message |

---

> :warning: **The following routes are middleware protected and require *`api_token`* to be specified (eg. `/?api_token=[token]`)**

## User profile

### Change password

`POST` */change/password*

Change password for a logged in user

**Request**

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| password | String | The new confirmed password to change to |
| old_password | String | The existing password |

**Response**

*response type `json`*

*`On success`*

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| message | String | Returns a human readable error message |

*`On error`*

Returns type [Error](#error)

---

### Update location

`POST` */update/location*

updates location value for a user

**Request**

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| latitude | Float | latitude of the new location |
| longitude | Float | longitude of the new location |

**Response**

*response type `json`*

*`On success`*

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| message | String | Returns a human readable error message |

*`On error`*

Returns type [Error](#error)

---

### Details

`GET` */details*

returns user data for the device

**Request**

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| device_type | Float | type of the device. values are `android` or `ios` |

**Response**

*response type `json`*

*`On success`*

Returns type [User](#user)

*`On error`*

Returns type [Error](#error)

---

### Update profile

`POST` */update/profile*

updates user profile

**Request**

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| first_name | String | first name max 255 char|
| last_name | String | last name max 255 char|
| email | String | email max 255 char and unique to user |
| mobile | String | mobile number unique to user |
| picture | Mimes | profile picture for the user. accepted types are `jpeg` ,`bmp` and `png` |

**Response**

*response type `json`*

*`On success`*

Returns type [User](#user)

*`On error`*

Returns type [Error](#error)

## Services

### Services

`GET` */services*

returns service types with rental hor package

**Request**

`Nothing`

**Response**

*response type `json`*

*`On success`*

Returns type [ServiceList](#serviceList)

*`On error`*

Returns type [Error](#error)

---

### Service geo fencing

`GET` */services/geo_fencing*

Checks to see if service is available at provided location

**Request**

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| s_latitude | String | latitude to check availability on |
| s_longitude | String | longitude to check availability on |
| service_type | Integer | Id for the service type |


**Response**

*response type `json`*

*`On success`*

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| km | Integer | Distance to the service |
| fare | Integer | Price for the service  |
| service | Integer | Contains type [service](#service) |

*`On error`*

Returns type [Error](#error)

---

### Rate provider

`POST` */rate/provider*

Adds a user rating

**Request**

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| request_id | Integer | ID for a user [request](#request) |
| rating | Integer | rating with possible values `1`, `2` ,`3` ,`4` or `5` |
| comment | String | max 255 char comment |


**Response**

*response type `json`*

*`On success`*

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| message | String | Returns a human readable success message |

*`On error`*

Returns type [Error](#error)

---

## Request

### Send request

`POST` */send/request*

generate a new user request

**Request**

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| s_latitude | Integer | latitude for the request |
| s_longitude | Integer | longitude for the request |
| service_type | Integer | unique identifier for the service type |
| promo_code *(optional)* | String | Promotion code |
| distance | Integer | distance of the request |
| use_wallet *(optional)* | Integer | - |
| payment_mode | String | Spec for payment method. Possible values are `CASH`, `CARD`, `PAYPAL` and `CC_AVENUE` |
| card_id | Integer | `Requied` if payment mode is `CARD` and the card exists |

**Response**

*response type `json`*

*`On success`*

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| message | String | Returns a human readable success message |
| request_id | Integer | Unique identifier for the request |
| current_provider | Integer | Unique identifier for the current provider |

*`On error`*

Returns type [Error](#error)

---

### Cancel request

`POST` */cancel/request*

cancels user request

**Request**

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| request_id | Integer | unique identifier for request retrieved from [Send request](#send-request)  |

**Response**

*response type `json`*

*`On success`*

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| message | String | Returns a human readable success message |

*`On error`*

Returns type [Error](#error)

---

### Check request

`GET` */request/check*

check user request

**Request**

`Nothing`

**Response**

*response type `json`*

*`On success`*

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| sos | Integer | sos number with default value `911` |
| cash | String | setting value for `CASH` |
| card | String | setting value for `CARD` |
| stripe_secret_key | String | setting value for stripe secret key |
| stripe_publishable_key | String | setting value for stripe publishable key |

*`On error`*

Returns type [Error](#error) with status code `500`

---

### Show providers

`GET` */show/providers*

Returns providers for a certain area and service

**Request**

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| latitude | Integer | latitude to get providers for |
| longitude | Integer | longitude to get providers for |
| service | Integer | service to get providers for |

**Response**

*response type `json`*

*`On success`*

Returns type [Providers](#providers)

*`On error`*

Returns type [Error](#error) with status code `500`

---

### Update request

`POST` */update/request*

Returns providers for a certain area and service

**Request**

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| latitude | Integer | latitude to get providers for |
| longitude | Integer | longitude to get providers for |
| request_id | Integer | unique identifier or the request to be modified |
| address | String | address information |

**Response**

*response type `json`*

*`On success`*

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| message | String | Returns a human readable success message |


*`On error`*

Returns type [Error](#error) with status code `500`

---

## History

### Trips

`GET` */trips*

Returns trip history using user requests

**Request**

`Nothing`

**Response**

*response type `json`*

*`On success`*

Returns type [UserRequests](#UserRequests)

*`On error`*

Returns type [Error](#error) with status code `500`

---

### Upcoming trips

`GET` */upcoming/trips*

Returns upcoming trip histories using user requests

**Request**

`Nothing`

**Response**

*response type `json`*

*`On success`*

Returns type [UserRequests](#UserRequests)

*`On error`*

Returns type [Error](#error) with status code `500`

---

### Trip details

`GET` */trips/details*

Returns trip details using user requests

**Request**

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| request_id | Integer | used to find a specific request |

**Response**

*response type `json`*

*`On success`*

Returns type [UserRequests](#UserRequests)

*`On error`*

Returns type [Error](#error) with status code `500`

---

### Upcoming trip details

`GET` */upcoming/trips/details*

Returns upcoming trip histories using user requests

**Request**

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| request_id | Integer | used to find a specific request |

**Response**

*response type `json`*

*`On success`*

Returns type [UserRequests](#UserRequests)

*`On error`*

Returns type [Error](#error) with status code `500`

---

## Payment

### Payment

`POST` */payment*

Returns payment method for user request

**Request**

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| request_id | Integer | used to find a specific request |

**Response**

*response type `json`*

*`On success`*

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| message | String | Returns a human readable success message |

*`On error`*

Returns type [Error](#error) with status code `500`

---

### Add money

`POST` */add/money*

Returns payment method for user request

**Request**

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| amount | Integer | amount of money fo add |
| card_id | Integer | card identifier for the user |

**Response**

*response type `json`*

*`On success`*

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| message | String | Returns a human readable success message |

*`On error`*

Returns type [Error](#error) with status code `500`

---

### Estimated fee

`GET` */estimated/fee*

Returns payment method for user request

**Request**

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| s_latitude | Integer | numeric starting latitude |
| s_longitude | Integer | numeric starting longitude |
| d_latitude | Integer | numeric destination latitude |
| d_longitude | Integer | numeric destination longitude |
| service_type | Integer | unique identifier for service type |
| service_required | String | possible values include `rental` and `outstation` |
| leave | Datetime | datatime to leave |
| return | Datetime | datatime to return |
| day | Datetime | datatime  |


**Response**

*response type `json`*

*`On success`*

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| estimated_fare | Integer | estimated fee for the service |
| distance | Integer | distance in kilometer |
| minute | Integer | estimated minutes |
| minute | Integer | estimated minutes |
| time | Integer | estimated time |
| surge | Integer | - |
| surge_value | Integer | - |
| tax_price | Integer | tax price on the fee |
| base_price | Integer | base price of the fee |
| service_type | Integer | unique identifier for the service type |
| wallet_balance | Integer | remaining ballance in the user wallet  |
| city_limits | Integer | - |
| service_required | String | - |
| rental_hours | Integer | rental hours |
| leave | Integer | time to leave |
| return  | Integer | time to return |
| day | Integer | day time |
| limit_message | String | setting value for `limit_message` |
| non_geo_price | Integer | - |
| rental_hour_package | Integer | - |
| time_package | Integer | - |
| rental_package | Integer | - |

*`On error`*

Returns type [Error](#error) with status code `500`

---

### Help

`GET` */help*

Returns help details

**Request**

`Nothing`

**Response**

*response type `json`*

*`On success`*

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| contact_number | String | contact number for help |
| contact_email | String | contact email for help |

*`On error`*

Returns type [Error](#error) with status code `500`

---

## Promo code

### Promo codes

`GET` */promocodes*

Returns active promo codes for current user

**Request**

`Nothing`

**Response**

*response type `json`*

*`On success`*

Returns type [Promocode](#Promocode)

*`On error`*

Returns type [Error](#error) with status code `500`

---

### Add promo code

`POST` */promocode/add*

Adds promo code to the current user

**Request**

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| promocode | String | the promo code to be added  |

**Response**

*response type `json`*

*`On success`*

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| message | String | Returns a human readable success message |

*`On error`*

Returns type [Error](#error) with status code `500`

---

## Card

### Insert Card

---

## Location

### Insert Location

---

## Passbook

### Wallet passbook

`GET` */wallet/passbook*

Gets the wallet passbook for the current user

**Request**

`Nothing`

**Response**

*response type `json`*

*`On success`*

Returns type [WalletPassbook](#WalletPassbook)

*`On error`*

Returns type [Error](#error) with status code `500`

---

### Promo passbook

`GET` */promo/passbook*

Gets the promo passbook for the current user

**Request**

`Nothing`

**Response**

*response type `json`*

*`On success`*

Returns type [PromocodePassbook](#PromocodePassbook)

*`On error`*

Returns type [Error](#error) with status code `500`

---

## Others

### Chat push

`POST` */chat/push*

push notification or chat

**Request**

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| id | Integer | - |
| message | String | message for the chat to push |

**Response**

`Nothing`

---

### Package

`POST` */package*

returns packages

**Request**

`Nothing`

**Response**

Returns type `PackageType`


















---
---
---
## Types

### User

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| social_unique_id | String | `Required` if login by facebook or google|
| device_type | String | type of the device. values are `android` or `ios`|
| device_token | String | Used to remember the device |
| device_id | String | Used to remember the device |
| login_by | String | Method used for login. values are `facebook` or `google` |
| first_name | String | first name max 255 char|
| last_name | String | last name max 255 char|
| email | String | email max 255 char and unique to user |
| mobile | Integer | mobile number unique to user |
| password | String | password min 6 char |
| emergency_contact1 | String | emergency contact |

---

### Error

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| error | String | Returns a human readable error message |

