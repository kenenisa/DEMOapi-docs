<h1 style="font-size:90px;text-align:center;">📃 API Docs </h1>

This doc is classified into 2 parts, **route methods** and **data types**. The route methods define an **HTTP** request with **request** and **response** part  and the types define how a certain data is structured.

Certain routes are **unprotected** or require no **access token** to be accessed but others require an access token that can be acquired from **login**. These route are marked with a star symbol(**\***) whenever you see that symbol next to a route name that means you have to provide a token in the request url as a **parameter**. eg. https://somedomain.com/api/route?api_token=[your_token] 

Routes are classified into 3 parts each require their own prefix to be accessed.

1. User `/api/user`
2. Fleet `/api/fleet`
3. Provider `/api/provider`

Some routes have bugs in them. They do not work at all or they do not work as intended. Info about these routes is written in thier own section.

<h1 style="font-size:30px;">✨ Contents</h1>

I. [Routes](#routes)
 1. [User routes](#user-routes)
    - [Access](#access)
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
      - [Logout*](#logout)
    - [Auth](#auth)
      - [Facebook](#facebook)
      - [Google](#google)
    - [User profile](#user-profile)
      - [Change password*](#change-password)
      - [Update location*](#update-location)
      - [Details*](#details)
      - [Update profile*](#update-profile)
    - [Services](#services)
      - [Services*](#services-1)
      - [Service geo fencing*](#service-geo-fencing)
      - [Rate provider*](#rate-provider)
    - [Request](#request)
      - [Send request*](#send-request)
      - [Cancel request*](#cancel-request)
      - [Check request*](#check-request)
      - [Show providers*](#show-providers)
      - [Update request*](#update-request)
    - [History](#history)
      - [Trips*](#trips)
      - [Upcoming trips*](#upcoming-trips)
      - [Trip details*](#trip-details)
      - [Upcoming trip details*](#upcoming-trip-details)
    - [Payment](#payment)
      - [Payment*](#payment-1)
      - [Add money*](#add-money)
      - [Estimated fee*](#estimated-fee)
      - [Help*](#help)
    - [Promo code](#promo-code)
      - [Promo codes*](#promo-codes)
      - [Add promo code*](#add-promo-code)
    - [Card](#card)
      - [Index Card*](#index-card)
      - [Store Card*](#store-card)
      - [Destroy Card*](#destroy-card)
    - [Location](#location)
      - [Index location*](#index-location)
      - [Store location*](#store-location)
      - [Show location*](#show-location)
      - [Edit location*](#edit-location)
      - [Destroy location*](#destroy-location)
    - [Passbook](#passbook)
      - [Wallet passbook*](#wallet-passbook)
      - [Promo passbook*](#promo-passbook)
    - [Others](#others)
      - [Chat push*](#chat-push)
      - [Package*](#package)
2. [Fleet routes](#fleet-routes)
    - [Access](#access-1)
      - [Forgot password](#forgot-password-1)
      - [Login](#login-1)
      - [Logout](#logout-1)
      - [Oauth token](#oauth-token)
    - [Profile](#profile)
      - [Profile detail*](#profile-detail)
      - [Profile password*](#profile-password)
      - [Profile update*](#profile-update)
    - [Provider](#provider)
      - [Index provider*](#index-provider)
      - [Store provider*](#store-provider)
      - [Provider requests*](#provider-requests)
      - [Show provider*](#show-provider)
      - [Update provider*](#update-provider)
      - [Delete provider*](#delete-provider)
    - [Documents*](#documents)
    - [Other](#other)
      - [Refresh token](#refresh-token)
      - [Reset password*](#reset-password-1)
      - [Provider review](#provider-review)
 3. [Provider routes](#provider-routes)
    - [Auth](#auth-1)
      - [Facebook](#facebook-1)
      - [Google](#google-1)
      - [Verify](#verify-1)
      - [Send OTP](#send-otp-1)
      - [Register](#register)
      - [Login](#login-2)
      - [Oauth token](#oauth-token-1)
      - [Verify OTP](#verify-otp-1)
      - [Forgot password](#forgot-password-2)
      - [Reset password](#reset-password-2)
      - [Settings](#settings-1)
      - [Logout](#logout-2)
    - [Trip](#trip)
      - [Index trip*](#index-trip)
      - [Store trip](#store-trip)
      - [Create trip](#create-trip)
      - [Accept trip*](#accept-trip)
      - [Calculate trip distance*](#calculate-trip-distance)
      - [Message trip](#message-trip)
      - [Rate trip*](#rate-trip)
      - [Show trip](#show-trip)
      - [Delete trip*](#delete-trip)
      - [Update trip*](#update-trip)
      - [Edit trip](#edit-trip)
      - [Cancel*](#cancel)
      - [Geo fencing*](#geo-fencing)
      - [Chat push*](#chat-push-1)
      - [Help details*](#help-details)
      - [Trip history*](#trip-history)
      - [Trip history details*](#trip-history-details)
      - [Trip rides*](#trip-rides)
      - [Upcoming trips*](#upcoming-trips-1)
      - [Upcoming trip details*](#upcoming-trip-details-1)
      - [Trip summery*](#trip-summery)
      - [test](#test)
    - [Instant ride](#instant-ride)
      - [Instant ride*](#instant-ride-1)
      - [Estimate*](#estimate)
      - [Now*](#now)
    - [Profile](#profile-1)
      - [Profile update*](#profile-update-1)
      - [Index profile*](#index-profile)
      - [Available profile*](#available-profile)
      - [Profile documents*](#profile-documents)
      - [Post document*](#post-document)
      - [Profile location](#profile-location)
      - [Profile password](#profile-password-1)
      - [Refresh token](#refresh-token-1)
      - [Target*](#target)

II. [Types](#types)
    - [User](#user)
    - [UserRequests](#userrequests)
    - [ServiceType](#servicetype)
    - [ServiceList](#servicelist)
    - [ServiceRentalHourPackage](#servicerentalhourpackage)
    - [Providers](#providers)
    - [Card](#card-1)
    - [Promocode](#promocode)
    - [PromocodePassbook](#promocodepassbook)
    - [WalletPassbook](#walletpassbook)
    - [Fleet](#fleet)
    - [Document](#document)
    - [Message](#message)
    - [Error](#error)

---

# Routes

## User routes

> **All requests to user api must be prefixed `/api/user`**

### Access

#### Settings

`GET` */settings*

gets setting values

**Request**

`Nothing`

**Response**

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

#### Verify

`POST` */verify*

verifies if email address is unique and valid

**Request**

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| email | String | Email address to be verified |

**Response**

*`On success`*

Returns type [Message](#message)

*`On error`*

Returns type [Error](#error)

---

#### Voice sms

`POST` */voice/sms*

Generates and responds with an OTP code

**Request**

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| username | Integer | Mobile number to generate the OTP for starting with `9` |

**Response**

*`On success`*

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| otp | String | Returns the OTP code generated |

*`On error`* Code `500`  is thrown

---

#### Sign up

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

*`On success`*

Responds with type [User](#user)

*`On error`* Code `500`  is thrown

---

#### Send OTP

`POST` */send/otp*

Generates and responds with an OTP code over sms

**Request**

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| username | Integer | Mobile number to generate the OTP for with full format |

**Response**

*`On success`*

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| otp | String | Returns the OTP code generated |

*`On error`* Code `500`  is thrown

---

#### Login

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

*`On success`*

Responds with type `Response`

*`On error`* Code `500`  is thrown

---

#### Verify OTP

`POST` */verify/otp*

Verified otp sent over sms or voice

**Request**

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| otp | Integer | OTP code send over either sms or voice |
| username | Integer | Mobile number to generate the OTP for with full format |
| device_token | String | Used to remember the device |

**Response**

*`On success`*

Responds with type `Response`

*`On error`* Code `500`  is thrown

---

#### Forgot password

`POST` */forgot/password*

generates and send an OTP Code for a mobile number of an existing user

**Request**

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| mobile | String | Mobile number to generate and send OTP for with full format |

**Response**

*`On success`*

Returns type [Message](#message)

*`On error`*

Returns type [Error](#error)

---

#### Reset password

`POST` */reset/password*

resets password for a user

**Request**

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| id | Integer | user id the reset password for |
| password | String | the new confirmed password (min 6 char) |

**Response**

*`On success`*

Returns type [Message](#message)

*`On error`*

Returns type [Error](#error)

---

#### Polygon

`GET` */polygon*

`undefined` in the code

---

#### Logout*

`POST` */logout*

Used to logout user

**Request**

`Nothing`

**Response**

*`On success`*

Returns type [Message](#message)

*`On error`*

Returns type [Error](#error) with code `500`

---

### Auth

#### Facebook

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

#### Google

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

### User profile

#### Change password*

`POST` */change/password*

Change password for a logged in user

**Request**

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| password | String | The new confirmed password to change to |
| old_password | String | The existing password |

**Response**

*`On success`*

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| message | String | Returns a human readable error message |

*`On error`*

Returns type [Error](#error)

---

#### Update location*

`POST` */update/location*

updates location value for a user

**Request**

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| latitude | Float | latitude of the new location |
| longitude | Float | longitude of the new location |

**Response**

*`On success`*

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| message | String | Returns a human readable error message |

*`On error`*

Returns type [Error](#error)

---

#### Details*

`GET` */details*

returns user data for the device

**Request**

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| device_type | Float | type of the device. values are `android` or `ios` |

**Response**

*`On success`*

Returns type [User](#user)

*`On error`*

Returns type [Error](#error)

---

#### Update profile*

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

*`On success`*

Returns type [User](#user)

*`On error`*

Returns type [Error](#error)

### Services

#### Services*

`GET` */services*

returns service types with rental hor package

**Request**

`Nothing`

**Response**
*`On success`*

Returns type [ServiceList](#serviceList) array

*`On error`*

Returns type [Error](#error)

---

#### Service geo fencing*

`GET` */services/geo_fencing*

Checks to see if service is available at provided location

**Request**

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| s_latitude | String | latitude to check availability on |
| s_longitude | String | longitude to check availability on |
| service_type | Integer | Id for the service type |


**Response**

*`On success`*

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| km | Integer | Distance to the service |
| fare | Integer | Price for the service  |
| service | Integer | Contains type [ServiceType](#servicetype) |

*`On error`*

Returns type [Error](#error)

---

#### Rate provider*

`POST` */rate/provider*

Adds a user rating

**Request**

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| request_id | Integer | ID for a user request |
| rating | Integer | rating with possible values `1`, `2` ,`3` ,`4` or `5` |
| comment | String | max 255 char comment |


**Response**

*`On success`*

Returns type [Message](#message)

*`On error`*

Returns type [Error](#error)

---

### Request

#### Send request*

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

*`On success`*

| Field | Type | Description |
| request_id | Integer | Unique identifier for the request |
| current_provider | Integer | Unique identifier for the current provider |

*`On error`*

Returns type [Error](#error)

---

#### Cancel request*

`POST` */cancel/request*

cancels user request

**Request**

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| request_id | Integer | unique identifier for request retrieved from [Send request](#send-request)  |

**Response**

*`On success`*

Returns type [Message](#message)

*`On error`*

Returns type [Error](#error)

---

#### Check request*

`GET` */request/check*

check user request

**Request**

`Nothing`

**Response**

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

#### Show providers*

`GET` */show/providers*

Returns providers for a certain area and service

**Request**

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| latitude | Integer | latitude to get providers for |
| longitude | Integer | longitude to get providers for |
| service | Integer | service to get providers for |

**Response**

*`On success`*

Returns type [Providers](#providers)

*`On error`*

Returns type [Error](#error) with status code `500`

---

#### Update request*

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

*`On success`*

Returns type [Message](#message)


*`On error`*

Returns type [Error](#error) with status code `500`

---

### History

#### Trips*

`GET` */trips*

Returns trip history using user requests

**Request**

`Nothing`

**Response**

*`On success`*

Returns type [UserRequests](#userrequests)

*`On error`*

Returns type [Error](#error) with status code `500`

---

#### Upcoming trips*

`GET` */upcoming/trips*

Returns upcoming trip histories using user requests

**Request**

`Nothing`

**Response**

*`On success`*

Returns type [UserRequests](#userrequests)

*`On error`*

Returns type [Error](#error) with status code `500`

---

#### Trip details*

`GET` */trips/details*

Returns trip details using user requests

**Request**

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| request_id | Integer | used to find a specific request |

**Response**

*`On success`*

Returns type [UserRequests](#userrequests)

*`On error`*

Returns type [Error](#error) with status code `500`

---

#### Upcoming trip details*

`GET` */upcoming/trips/details*

Returns upcoming trip histories using user requests

**Request**

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| request_id | Integer | used to find a specific request |

**Response**

*`On success`*

Returns type [UserRequests](#userrequests)

*`On error`*

Returns type [Error](#error) with status code `500`

---

### Payment

#### Payment*

`POST` */payment*

Returns payment method for user request

**Request**

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| request_id | Integer | used to find a specific request |

**Response**

*`On success`*

Returns type [Message](#message)

*`On error`*

Returns type [Error](#error) with status code `500`

---

#### Add money*

`POST` */add/money*

Returns payment method for user request

**Request**

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| amount | Integer | amount of money fo add |
| card_id | Integer | card identifier for the user |

**Response**

*`On success`*

Returns type [Message](#message)

*`On error`*

Returns type [Error](#error) with status code `500`

---

#### Estimated fee*

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

#### Help*

`GET` */help*

Returns help details

**Request**

`Nothing`

**Response**

*`On success`*

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| contact_number | String | contact number for help |
| contact_email | String | contact email for help |

*`On error`*

Returns type [Error](#error) with status code `500`

---

### Promo code

#### Promo codes*

`GET` */promocodes*

Returns active promo codes for current user

**Request**

`Nothing`

**Response**

*`On success`*

Returns type [Promocode](#promocode)

*`On error`*

Returns type [Error](#error) with status code `500`

---

#### Add promo code*

`POST` */promocode/add*

Adds promo code to the current user

**Request**

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| promocode | String | the promo code to be added  |

**Response**

*`On success`*

Returns type [Message](#message)

*`On error`*

Returns type [Error](#error) with status code `500`

---

### Card

#### Index Card*

`GET` */card*

Returns a list of cards for a user

**Request**

`Nothing`

**Response**

*`On success`*

Returns type [Card](#card)

*`On error`*

Returns type [Error](#error) with status code `500`

---

#### Store Card*

`POST` */card*

Stores a card

**Request**

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| stripe_token | String | required stripe token  |

**Response**

*`On success`*

Returns type [Message](#message)

*`On error`*

Returns type [Error](#error) with status code `500`

---

#### Destroy Card*

`DELETE` */card/{card}*

{card} is id if the card to be deleted
Deletes a card

**Request**

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| card_id | String | unique identifier for the card to be destroyed  |

**Response**

*`On success`*

Returns type [Message](#message)

*`On error`*

Returns type [Error](#error) with status code `500`

---

### Location

#### Index location*

`GET` */location/index*

Returns a list of location for a user

**Request**

`Nothing`

**Response**

*`On success`*

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| home | Location | - |
| work | Location | - |
| others | Location | - |
| recent | Location | - |

*`On error`*

Returns with status code `500`

---

#### Store location*

`POST` */location/store*

Stores a location

**Request**

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| address | String | address for the location  |
| latitude | Integer | latitude for the location  |
| longitude | Integer | longitude for the location  |
| type | Enum | possible values are `home`, `work`, `recent` and `others`  |

**Response**

*`On success`*

Returns type [Message](#message)

*`On error`*

Returns type [Error](#error) with status code `500`

---

#### Show location*

`GET` */location/{id}*

show specific location with id

**Request**

replace `{id}` in the route with the preferred id

**Response**

*`On success`*

Returns type [Message](#message)

*`On error`*

Returns type [Error](#error) with status code `500`

---

#### Edit location*

`POST` */location/{id}/edit*

replace `{id}` in the route with the preferred id

**Request**

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| address | String | address for the location  |
| latitude | Integer | latitude for the location  |
| longitude | Integer | longitude for the location  |
| type | Enum | possible values are `home`, `work`, `recent` and `others`  |

**Response**

*`On success`*

Returns type [Message](#message)

*`On error`*

Returns type [Error](#error) with status code `500`

---

---

#### Destroy location*

`DELETE` */location/{id}*

replace `{id}` in the route with the preferred id

**Request**

`Nothing`

**Response**

*`On success`*

Returns type [Message](#message)

*`On error`*

Returns type [Error](#error) with status code `500`

---

### Passbook

#### Wallet passbook*

`GET` */wallet/passbook*

Gets the wallet passbook for the current user

**Request**

`Nothing`

**Response**

*`On success`*

Returns type [WalletPassbook](#walletpassbook)

*`On error`*

Returns type [Error](#error) with status code `500`

---

#### Promo passbook*

`GET` */promo/passbook*

Gets the promo passbook for the current user

**Request**

`Nothing`

**Response**

*`On success`*

Returns type [PromocodePassbook](#PromocodePassbook)

*`On error`*

Returns type [Error](#error) with status code `500`

---

### Others

#### Chat push*

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

#### Package*

`GET` */package*

gets a list of packages

**Request**

`Nothing`

**Response**
Returns type `PackageType`

---

## Fleet routes

> **All requests to fleet api must be prefixed `/api/fleet`**

### Access

#### Forgot password

`POST` */forgot/password*

generates and send an OTP Code for a email of an existing fleet

**Request**

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| email | String | email of the account to reset password for |

**Response**

*`On success`*

Returns type [Message](#message)

*`On error`*

Returns type [Error](#error)

---

#### Login

> **This route is undefined in the code. It's functionality is routed to `/oauth/token` so you can use that as a login route**

---

#### Logout

`POST` */logout*

logout an account

**Request**

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| id | Integer | unique identifier for an account  |


**Response**

*`On success`*

Returns type [Message](#message)

*`On error`*

Returns type [Error](#error)

---

#### Oauth token

`POST` */oauth/token*

login as a fleet

**Request**

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| email | String | valid email for account |
| password | String | min 6 char |
| device_token | String | device identifier |
| device_id | String | unique identifier for a device |
| device_type | Enum | passible values are `android` or `ios` |

**Response**

*`On success`*

Returns type [Fleet](#fleet)

*`On error`*

Returns type [Error](#error)

---
### Profile

> **The following routes are middleware protected and need an access token to be accessed which can be acquired from login (eg. api_token=[token])**

#### Profile detail*

`GET` */profile/detail*

returns a logged in fleet's profile info

**Request**

`Nothing`

**Response**

*`On success`*

Returns type [Fleet](#fleet)

*`On error`*

Returns type [Error](#error)

---

#### Profile password*

`POST` */profile/password*

can be used to change a password for an account

**Request**

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| old_password | String | requires the existing password in use |
| password | String | the new password, min 6 char, confirmed(means it needs another field 'confirm_password') |

**Response**

*`On success`*

Returns type [Message](#message)

*`On error`*

Returns type [Error](#error)

---

#### Profile update*

`POST` */profile/update*

updates account profile

**Request**

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| name | String | new account name, max 255 char |
| company | String | new account company, max 255 char |
| mobile | Integer | new account mobile number, max 255 char |
| logo | Mimes | new account logo with `jpeg`,`jpg`,`bmp`or `png` file type, max 5242880 size |

**Response**

*`On success`*

Returns type [Message](#message)

*`On error`*

Returns type [Error](#error)

---

### Provider


#### Index provider*

`GET` */provider*

returns with info about the logged in fleet providers

**Request**

`Nothing`

**Response**

*`On success`*

Returns type [Providers](#providers)

*`On error`*

Returns type [Error](#error)

---

#### Store provider*

`POST` */provider*

creates a provider

**Request**

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| first_name | String | first name of the provider |
| last_name | String | last name of the provider |
| mobile | Integer | mobile number for the provider |
| avatar | Mimes | profile picture with file types `jpeg`, `jpg`, `bmp`,`png` with max size 5242880 |

**Response**

*`On success`*

Returns type [Message](#message)

*`On error`*

Returns type [Error](#error)

---

#### Provider requests*

`GET` */provider/{id}/request*

replace {id} with the id of a provider to get user requests for

**Request**

`Nothing`

**Response**

*`On success`*

Returns type [UserRequests](#userrequests)

*`On error`*

Returns type [Error](#error)

---

#### Show provider*

`GET` */provider/{provider}*

> :warning: **This route is buggy. It will return a view(html) not a json data**: replace {provider} with a providers id

**Request**

`Nothing`

**Response**

> :warning: **returns html**

---

#### Update provider*

`PUT|PATCH` */provider/{provider}*

updates a providers profile, replace {provider} with a providers id

**Request**

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| first_name | String | first name of the provider |
| last_name | String | last name of the provider |
| mobile | Integer | mobile number for the provider |
| avatar | Mimes | profile picture with file types `jpeg`, `jpg`, `bmp`,`png` with max size 5242880 |

**Response**

*`On success`*

Returns type [Message](#message)

*`On error`*

Returns type [Error](#error)

---

#### Delete provider*

`DELETE` */provider/{provider}*

deletes a providers account, replace {provider} with a providers id

**Request**

`Nothing`

**Response**

*`On success`*

Returns type [Message](#message)

*`On error`*

Returns type [Error](#error)

---

### Documents*

> :warning: **These routes are buggy. They will return a view(html) not a json data**

| Method | route |
| ------- |----- |
| POST    |   /provider/{provider}/document|
| GET\| HEAD  | /provider/{provider}/document|
| GET\| HEAD  | /provider/{provider}/document/create|
| GET\| HEAD  | /provider/{provider}/document/{document}|
| PUT\| PATCH | /provider/{provider}/document/{document}|
| DELETE    | /provider/{provider}/document/{document}|
| GET\| HEAD  | /provider/{provider}/document/{document}/edit|
| GET\| HEAD  | /provider/{provider}/edit|
| DELETE    | /provider/{provider}/service/{document}|

### Other

---

#### Refresh token

> :warning: **This does not work. It's not defined in the code**

---

#### Reset password*

`POST` */reset/password*

resets password with a new one

**Request**

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| id | String | unique identifier for the fleet |
| password | String | confirmed and min 6 char |

**Response**

*`On success`*

Returns type [Message](#message)

*`On error`*

Returns type [Error](#error)

---

#### Provider review

> :warning: **This route is buggy. It will return a view(html) not a json data**

---

## Provider routes

> **All requests to user api must be prefixed `/api/user`**

### Auth

#### Facebook

`POST` */auth/facebook*

Used to login provider using facebook login

**Request**

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| device_type | String | type of the device. values are `android` or `ios`|
| device_token | String | Used to remember the device |
| device_id | String | device_id |
| accessToken | String | Token from the other api|
| login_by | String | login by `facebook`, `google` or `manual` |

**Response**

*`On success`*

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| status | Boolean | Indicates the success status of the request |
| token_type | String | Default value `Bearer` |
| access_token | String | Api access token |
| currency | String | Setting value for currency |
| sos | String | Defaults to `911` |

*`On error`*

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| status | Boolean | Indicates the success status of the request |
| message | String | Returns a human readable error message |

---

#### Google

`POST` */auth/google*

Used to login provider using google login

**Request**

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| device_type | String | type of the device. values are `android` or `ios`|
| device_token | String | Used to remember the device |
| device_id | String | device_id |
| accessToken | String | Token from the other api|
| login_by | String | login by `facebook`, `google` or `manual` |

**Response**

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

#### Verify

`POST` */verify*

verifies if email address is unique and valid

**Request**

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| email | String | Email address to be verified |

**Response**

*`On success`*

Returns type [Message](#message)

*`On error`*

Returns type [Error](#error)

---

#### Send OTP

`POST` */send/otp*

Generates and responds with an OTP code over sms

**Request**

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| username | Integer | Mobile number to generate the OTP for with full format |

**Response**

*`On success`*

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| otp | String | Returns the OTP code generated |

*`On error`* Code `500`  is thrown

---

---

#### Register

`POST` */register*

Used to sign up providers

**Request** `ALL values are required`

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| device_type | String | type of the device. values are `android` or `ios`|
| device_token | String | Used to remember the device |
| device_id | String | Used to remember the device |
| first_name | String | first name max 255 char|
| last_name | String | last name max 255 char|
| mobile | Integer | mobile number unique to user |
| password | String | password min 6 char |
| emergency_contact1 | String | emergency contact |

**Response**

*`On success`*

Responds with type [Providers](#providers)

*`On error`*

Returns type [Error](#error)

---

#### Login

`POST` */login*

Used to login providers

**Request** `ALL values are required`

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| device_type | String | type of the device. values are `android` or `ios`|
| device_token | String | Used to remember the device |
| device_id | String | Used to remember the device |
| mobile | String | fully formated mobile number |
| country_code | Integer | country code |
| password | String | password min 6 char |

**Response**

*`On success`*

Responds with type [Providers](#providers)

*`On error`* 

Returns type [Error](#error)

---

#### Oauth token

`POST` */oauth/token*

> :warnning: *Points to the same method as `/login`* 

---

#### Verify OTP

`POST` */verify/otp*

Verified otp sent over sms or voice

**Request**

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| otp | Integer | OTP code send over either sms or voice |
| username | Integer | Mobile number to generate the OTP for with full format |
| device_token | String | Used to remember the device |

**Response**

*`On success`*

Responds with type `Response`

*`On error`* Code `500`  is thrown

---

#### Forgot password

`POST` */forgot/password*

generates and send an OTP Code for a mobile number of an existing user

**Request**

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| mobile | String | Mobile number to generate and send OTP for with full format |

**Response**

*`On success`*

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| message | String | Human readable message |
| provider | [Providers](#providers) | provider info |

*`On error`*

Returns type [Error](#error)

---

#### Reset password

`POST` */reset/password*

resets password for a user

**Request**

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| id | Integer | user id the reset password for |
| password | String | the new confirmed password (min 6 char) |

**Response**

*`On success`*

Returns type [Message](#message)

*`On error`*

Returns type [Error](#error)

---

#### Settings

`GET` */settings*

gets setting values

**Request**

`Nothing`

**Response**

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

#### Logout

`POST` */logout*

Used to logout provider

**Request**

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| id | Integer | Unique identifier for the provider to be logged out |

**Response**

*`On success`*

Returns type [Message](#message)

*`On error`*

Returns type [Error](#error) with code `500`

---

### Trip

---

#### Index trip*

`GET` */trip*

get all trips

**Request**

`Nothing`

**Response**

*`On success`*

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| account_status | Enum | possible values are `onboarding`, `approved` and `banned` |
| service_status | Enum | possible values are `active` and `offline` |
| requests | [UserRequests](#userrequests) | list of user requests |

Returns type [Message](#message)

*`On error`*

Returns type [Error](#error)

---

#### Store trip

`POST` */trip*

> :warning: this route is not defined in the code

---

#### Create trip

`POST` */trip/create*

> :warning: this route is not defined in the code

---

#### Accept trip*

`POST` */trip/{id}*

accept trips incoming from a user
replace {id} with id of a user request to be accepted

**Request**

`Nothing`

**Response**

*`On success`*

Returns type [UserRequests](#userrequests)

*`On error`*

Returns type [Error](#error)

---

#### Calculate trip distance*

`POST` */trip/{id}/calculate*

calculates trip distance
replace {id} with id of a user request

**Request**

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| latitude | Integer | current location |
| longitude | Integer | current location |

**Response**

*`On success`*

Returns type [UserRequests](#userrequests)

*`On error`*

Returns type [Error](#error)

---

#### Message trip

`POST` */trip/{id}/message*

> :warning: this route is not defined in the code

---

#### Rate trip*

`POST` */trip/{id}/rate*

rate a certain trip
replace {id} with id of a user request

**Request**

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| rating | Integer | rating with possible values `1`, `2` ,`3` ,`4` or `5` |
| comment | String | max 255 char comment |

**Response**

*`On success`*

Returns type [Message](#message)

*`On error`*

Returns type [Error](#error)

---

#### Show trip

`POST` */trip/{trip}*

> :warning: this route is not defined in the code

---

#### Delete trip*

`DELETE` */trip/{trip}*

deletes a certain trip
replace {trip} with id of a user request

**Request**

`Nothing`

**Response**

*`On success`*

Returns type [Message](#message) `or` Returns type [UserRequests](#userrequests) with a property .user:[User](#user) inside it

```
UserRequests{
    ...
    user: User
    ...
}
```

*`On error`*

Returns type [Error](#error)

---

#### Update trip*

`POST` */trip/trip*



**Request**

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| status | Enum | possible values are `SEARCHING`,`CANCELLED`,`ACCEPTED`,`STARTED`,`ARRIVED`,`PICKEDUP`,`DROPPED`,`COMPLETED` and `SCHEDULED` |
| address | String | current address |
| latitude | Integer | current location |
| longitude | Integer | current location |

**Response**

*`On success`*

Returns type [UserRequests](#userrequests)

*`On error`*

Returns type [Error](#error)

---

#### Edit trip

`POST` */trip/{trip}/edit*

> :warning: this route is not defined in the code

---

#### Cancel*

`POST` */cancel*

cancel a trip

**Request**

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| cancel_reason | String | max 255 char |

**Response**

*`On success`*

Returns type [UserRequests](#userrequests)

*`On error`*

Returns type [Error](#error)

---

#### Geo fencing*

`POST` */geo-fencing/live-track*

live track a request

**Request**

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| request_id | Integer | unique identifier to track data for |
| latitude | Integer | current location |
| longitude | Integer | current location |

**Response**

*`On success`*

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| Request | [UserRequests](#userrequests) | live info about the request |

*`On error`*

Returns type [Error](#error)

---

#### Chat push*

`POST` */chat/push*

push a chat to a user

**Request**

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| id | Integer | unique identifier for a request |
| message | String | message to be sent |

**Response**

`Nothing`

---

#### Help details*

`GET` */help*

get help info

**Request**

`Nothing`

**Response**

*`On success`*

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| contact_number | String | setting value for contact_number |
| contact_email | String | setting value for contact_email |

*`On error`*

Returns type [Error](#error)

---

---

#### Trip history*

`GET` */requests/history*

Get the trip history of the provider

**Request**

`Nothing`

**Response**

*`On success`*

Returns type [UserRequests](#userrequests)

*`On error`*

Returns type [Error](#error)

---

#### Trip history details*

`GET` */request/history/details*

Get the trip history details of the provider

**Request**

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| request_id | String | unique identifier for the request we want to get the details for |

**Response**

*`On success`*

Returns type [UserRequests](#userrequests)

*`On error`*

Returns type [Error](#error)

---

#### Trip rides*

`POST` */request/rides*

Get the ride history of the provider

**Request**

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| request_id | String | unique identifier for the request we want to get the details for |

**Response**

*`On success`*

Returns type [UserRequests](#userrequests)

*`On error`*

Returns type [Error](#error)

---

#### Upcoming trips*

`GET` */request/upcoming*

scheduled trips of the provider

**Request**

`Nothing`

**Response**

*`On success`*

Returns type [UserRequests](#userrequests)

*`On error`*

Returns type [Error](#error)

---

#### Upcoming trip details*

`GET` */requests/upcoming/details*

detail for scheduled trip

**Request**

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| request_id | String | unique identifier for the request we want to get the details for |

**Response**

*`On success`*

Returns type [UserRequests](#userrequests)

*`On error`*

Returns type [Error](#error)

---

#### Trip summery*

`POST` */summery*

summery for all trips of the provider

**Request**

`Nothing`

**Response**

*`On success`*

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| rides | [UserRequests](#userrequests) | list of info for rides by the provider |
| revenue | Integer | revenue summery  |
| cancel_rides | Integer | amount of canceled rides  |
| scheduled_rides | Integer | amount of scheduled rides  |

*`On error`*

Returns type [Error](#error)

---

#### test

`POST` */test/push*

> this is useless

### Instant ride

---

#### Instant ride*

`POST` */instant-ride*

-

**Request**

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| mobile | String | - |
| name | String | - |
| s_latitude | Integer | - |
| s_longitude | Integer | - |
| d_latitude | Integer | - |
| d_longitude | Integer | - |
| service_required | String | - |
| leave | String | - |
| return | String | - |
| day | String | - |

**Response**

*`On success`*

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| user | [User](#user) | - |
| estimated_fare | Integer | - |

*`On error`*

Returns type [Error](#error)

---

#### Estimate*

`GET` */instant-ride/estimate*

estimate instant ride

**Request**

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| s_latitude | Integer | - |
| s_longitude | Integer | - |
| d_latitude | Integer | - |
| d_longitude | Integer | - |

**Response**

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

*`On error`*

Returns type [Error](#error)

---

#### Now*

`POST` */instant-ride/now*

-

**Request**

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| s_latitude | Integer | - |
| s_longitude | Integer | - |
| s_address | String | - |
| d_latitude | Integer | - |
| d_longitude | Integer | - |
| d_address | String | - |
| user_id | Integer | - |

**Response**

*`On success`*

Returns type [UserRequests](#userrequests)

*`On error`*

Returns type [Error](#error)

---

### Profile

#### Profile update*

`POST` */profile*

update a provider profile

**Request**

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| first_name | String | first name max 255 char|
| last_name | String | last name max 255 char|
| mobile | Integer | mobile number unique to user |
| avatar | Mimes | profile picture with file types `jpeg`, `jpg`, `bmp`,`png` with max size 5242880 |
| language | String | max 255 char|
| address | String | max 255 char|
| address_secondary | String | max 255 char|
| city | String | max 255 char|
| country | String | max 255 char|
| postal_code | String | max 255 char|

**Response**

*`On success`*

Returns type [Providers](#providers)

*`On error`*

Returns type [Error](#error)

---

#### Index profile*

`GET` */profile*

index providers profile

**Request**

`Nothing`

**Response**

*`On success`*

Returns type [Providers](#providers)

*`On error`*

Returns type [Error](#error)

---

#### Available profile*

`POST` */profile/available*

check if provider is available

**Request**

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| service_status | Enum | possible values are `active` or `offline`  |

**Response**

*`On success`*

Returns type [Providers](#providers)

*`On error`*

Returns type [Error](#error)

---

#### Profile documents*

`GET` */profile/documents*

get documents for a profile

**Request**

`Nothing`

**Response**

*`On success`*

Returns type [Document](#document)

*`On error`*

Returns type [Error](#error)

---

#### Post document*

`POST` */profile/document*

upload document

**Request**

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| document | String | a list of document files |

**Response**

*`On success`*

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| success | String | Human readable success message |

*`On error`*

Returns type [Error](#error)

---

#### Profile location

`POST` */profile/location*

Update latitude and longitude of the provider

**Request**

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| latitude | Integer | current location |
| longitude | Integer | current location |

**Response**

*`On success`*

Returns type [Message](#message)

*`On error`*

Returns type [Error](#error)

---

#### Profile password

`POST` */profile/password*

Update password of the provider.

**Request**

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| password_old | String | old password |
| password | String | new confirmed password |

**Response**

*`On success`*

Returns type [Message](#message)

*`On error`*

Returns type [Error](#error)

---

#### Refresh token

`POST` */refresh/token*

refresh provider access token

**Request**

`Nothing`

**Response**

*`On success`*

Returns type [Providers](#providers) with access_token inside it

*`On error`*

Returns type [Error](#error)

---

#### Target*

`GET` */target*

Show providers daily target.

**Request**

`Nothing`

**Response**

*`On success`*

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| rides | [UserRequests](#userrequests) | contains a list of user requests |
| rides_count | Integer | count of rides |
| target | Integer | Default value is `0` |

*`On error`*

Returns type [Error](#error)


---
---
---
---
---
---

# Types

### User

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| id | Integer | Unique identifier for a user |
| social_unique_id | String | `Required` if login by facebook or google|
| device_type | String | type of the device. values are `android` or `ios`|
| device_token | String | Used to remember the device |
| device_id | String | Used to remember the device |
| login_by | String | Method used for login. values are `facebook` or `google` |
| first_name | String | first name max 255 char|
| last_name | String | last name max 255 char|
| email | String | email max 255 char and unique to user |
| mobile | String | mobile number unique to user |
| password | String | password min 6 char |
| emergency_contact1 | String | emergency contact |

---

### UserRequests

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| id | Integer | Unique identifier for a request |
| user_id | Integer | Unique identifier for a user issuing the request |
| provider_id | Integer | Unique identifier for a provider. Default value is `0` |
| current_provider_id | Integer | Unique identifier for a provider |
| service_type_id | Integer | Unique identifier for the type of a service |
| rental_hours | Integer \| null | value for rental hours |
| out_leave | String \| null | value date time |
| out_return | String \| null | value date time |
| day | String \| null | value date time |
| status | Enum | possible values are `SEARCHING`,`CANCELLED`,`ACCEPTED`,`STARTED`,`ARRIVED`,`PICKEDUP`,`DROPPED`,`COMPLETED` and `SCHEDULED` |
| cancelled_by | Enum | possible values are `NONE`,`USER` and `PROVIDER` |
| payment_mode | Enum | possible values are `CASH`,`CARD`,`PAYPAL` and `CC_AVENUE` |
| service_required | Enum | possible values are `none`,`rental` and `outstation` |
| paid | Boolean | Default value is `0` |
| distance | Double | DOUBLE equivalent with precision, 15 digits in total and 8 after the decimal point |
| s_address | String \| null | starting address |
| s_latitude | String \| null | starting latitude |
| s_longitude | String \| null | starting longitude |
| d_address | String \| null | destination address |
| otp | String | - |
| d_latitude | String \| null | destination latitude |
| d_longitude | String \| null | destination longitude |
| assigned_at | TIMESTAMP  \| null | provider assigned time |
| schedule_at | TIMESTAMP  \| null | service scheduled time |
| started_at | TIMESTAMP  \| null | service starting time |
| finished_at | TIMESTAMP  \| null | service finished time |
| is_scheduled | Enum | possible values are `YES` and `YES` |
| user_rated | Boolean | default value is `0` |
| provider_rated | Boolean | default value is `0` |
| use_wallet | Boolean | default value is `0` |
| surge | Boolean | default value is `0` |
| route_key | LongText | - |

---

### ServiceType

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| id | Integer | Unique identifier for a provider |
| name | String | name max 255 char|
| provider_name | String \| null | provider name max 255 char|
| image | String \| null | - |
| capacity | Integer | default value is `0` |
| fixed | Integer | - |
| price | Integer | price for the service |
| minute | Integer | - |
| outstation_km | Integer \| null | - |
| rental_fare | Integer \| null | - |
| outstation_driver | Integer \| null | - |
| hour | String \| null | - |
| distance | Integer | - |
| calculator | Enum | possible values are `MIN`, `HOUR`, `DISTANCE`, `DISTANCEMIN` and `DISTANCEHOUR` |
| description | String \| null | - |
| status | Integer | default value is `0` |

---

### ServiceList

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| id | Integer | Unique identifier for a provider |
| name | String | name max 255 char|
| provider_name | String \| null | provider name max 255 char|
| image | String \| null | - |
| capacity | Integer | default value is `0` |
| fixed | Integer | - |
| price | Integer | price for the service |
| minute | Integer | - |
| outstation_km | Integer \| null | - |
| rental_fare | Integer \| null | - |
| outstation_driver | Integer \| null | - |
| hour | String \| null | - |
| distance | Integer | - |
| calculator | Enum | possible values are `MIN`, `HOUR`, `DISTANCE`, `DISTANCEMIN` and `DISTANCEHOUR` |
| description | String \| null | - |
| status | Integer | default value is `0` |
| rental_hour_package | - | has the type [ServiceRentalHourPackage](#servicerentalhourpackage) |

---

### ServiceRentalHourPackage

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| id | Integer | Unique identifier for a provider |
| service_type_id | Integer | Unique identifier for the type of a service |
| hour | String \| null | - |
| km | String \| null | - |
| price | Double | default value is `0` |

---

### Providers

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| id | Integer | Unique identifier for a provider |
| first_name | String | first name max 255 char|
| last_name | String | last name max 255 char|
| email | String \| null | email max 255 char and unique to user |
| mobile | String \| null | mobile number unique to user |
| password | String | password min 6 char |
| avatar | String \| null | - |
| rating | Decimal | default value is `5` |
| status | Enum | possible values are `onboarding`, `approved` and `banned` |
| latitude | Double \| null | used for the location of the provider |
| longitude | Double \| null | used for the location of the provider |
| otp | Integer | used for confirmation. default value is `0` |

---

### Card

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| id | Integer | Unique identifier for a provider |
| user_id | Integer | id of user this card belongs to |
| last_four | String | - |
| card_id | String | - |
| brand | String \| null | - |
| is_default | Integer | Default value is `0` |

---

### Promocode

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| id | Integer | Unique identifier for a provider |
| promo_code | String | the promo code |
| discount | Float | amount of discount. default value is `0` |
| discount_type | Enum | possible values are `percent` and `amount` |
| status | Enum | possible values are `ADDED` and `EXPIRED` |
| expiration | Datetime | time the promo code expires |

---

### PromocodePassbook

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| id | Integer | Unique identifier for a provider |
| user_id | Integer | Unique identifier for a user |
| promocode_id | Integer | Unique identifier for the promo code |
| status | Enum | possible values are `ADDED`, `USED` and `EXPIRED` |

---

### WalletPassbook

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| id | Integer | Unique identifier for a provider |
| user_id | Integer | Unique identifier for a user |
| amount | Integer | amount in the passbook |
| status | Enum | possible values are `CREDITED` and `DEBITED` |
| via | String \| null | method for the passbook |

---

### Fleet

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| id | Integer | Unique identifier for a provider |
| name | String | name max 255 char|
| email | String | email max 255 char and unique to user |
| password | String | password min 6 char |
| mobile | String \| null | mobile number unique to user |
| logo | String \| null | logo of the fleet |
| company | String | name of the company |

---

### Document

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| id | Integer | Unique identifier for a provider |
| name | String | name max 255 char|
| type | Enum | possible values are `DRIVER` and `VEHICLE` |

---

### Message

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| message | String | Returns a human readable success message |

---

### Error

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| error | String | Returns a human readable error message |

