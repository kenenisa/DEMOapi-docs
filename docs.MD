# API Docs

> :warning: **THIS IS A DEMO**: Ony includes docs for auth and some types are not proved

*all requests must be prefixed `/api/`*

---
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

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| error | String | Returns a human readable error message |

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

*`On error`* Code ==500==  is thrown

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
| mobile | String | mobile number unique to user |
| password | String | password min 6 char |
| emergency_contact1 | String | emergency contact |

**Response**

*response type `json`*

*`On success`*

Responds with type `User`

*`On error`* Code ==500==  is thrown

---
### Send OTP

`POST` */send/otp*

Generates and responds with an OTP code over sms

**Request**

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| username | String | Mobile number to generate the OTP for with full format |

**Response**

*response type `json`*

*`On success`*

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| otp | String | Returns the OTP code generated |

*`On error`* Code ==500==  is thrown

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

*`On error`* Code ==500==  is thrown

---

### Verify OTP

`POST` */verify/otp*

Verified otp sent over sms or voice

**Request**

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| otp | Integer | OTP code send over either sms or voice |
| username | String | Mobile number to generate the OTP for with full format |
| device_token | String | Used to remember the device |

**Response**

*response type `json`*

*`On success`*

Responds with type `Response`

*`On error`* Code ==500==  is thrown

---

### Logout

`POST` */logout*

Used to logout user

**Request**

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| device_type | String | type of the device. values are `android` or `ios`|
| device_token | String | Used to remember the device |
| device_id | String | device_id |
| accessToken | String | Token from the other api|
| login_by | String | login by `facebook` or `google` |

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



