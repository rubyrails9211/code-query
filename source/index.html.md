---
title: CodeQuery Cover API docs

language_tabs: # must be one of https://git.io/vQNgJ
  - Ruby

toc_footers:
  - <a href='http://nugeninfo.com'>CodeQuery Cover API Docs</a>

search: true
---

# Introduction

CodeQuery Cover Api Docs

# Login-Signup

## Signup - Create User


> Success-Response:

```json

HTTP 200 OK
{
  "msg": 1,
  "token": "7dhf8hfjhdjf8rrhjdjfhdf844"
}

```

> Error-Response

```json
HTTP 422 Unprocessable entity
{
     "msg": 0,
     "error": "Email already taken"
}

```

This endpoint will save a new user.

### HTTP Request

`POST https://code-query.herokuapp.com/v1/users`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
email | String | Email of user
name | String | User name
dob | String | Date of birth
s_class | String | Class of user
password | String | Password of user
college | String | college of user
specifications | Array | Specifications must be in array


## Login - Authentication

> Success-Response:

```json

HTTP 200 OK
{
  "token": "7dhf8hfjhdjf8rrhjdjfhdf844",
  "msg": 1,
  "verified": true
}

```

> Error-Response

```json
HTTP 401 Unprocessable entity
{
     "msg": 0,
     "error": "Email/Password doesnot match"
}

```

Login/Authenticate User.

### HTTP Request

`POST https://code-query.herokuapp.com/v1/login`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
email | String | Email of user
password | String | Password of user


## Verify Account

> Success-Response:

```json

HTTP 200 OK
{
  "msg": 1
}

```

> Error-Response

```json
HTTP 422 Unprocessable entity
{
     "msg": 0,
     "error": "Please enter correct OTP."
}

```

Verify User Account

### HTTP Request

`POST https://code-query.herokuapp.com/v1/verification`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
code | String | Code sent to user

<aside class="success">
 User must be authorized to verify account.Send user token in the header.
</aside>


## Resend Verification Code

> Success-Response:

```json

HTTP 200 OK
{
  "msg": 1
}

```

> Error-Response

```json
HTTP 422 Unprocessable entity
{
     "msg": 0,
     "error": "Error while resending Code"
}

```
Resend Verification Code to User

### HTTP Request

`GET https://code-query.herokuapp.com/v1/resendCode`

### Query Parameters

No Parameters

<aside class="success">
 User must be authorized to resend code.Send user token in the header.
</aside>

## Fetch Single User

> Success-Response:

```json

HTTP 200 OK
{
  "name": "shilpa",
  "email": "data",
  "dob": "12/12/2019",
  "class": "10",
  "college": "ct",
  "specifications": ["js","c++"],
  "verified": "data"
}

```

> Error-Response

```json
HTTP 422 Unprocessable entity
{
     "msg": 0,
     "error": "Unable to find detail"
}

```

Fetch single user detail

### HTTP Request

`GET https://code-query.herokuapp.com/v1/getUser`

### Query Parameters

No Parameter

<aside class="success">
 User must be authorized to fetch data.Send user token in the header.
</aside>

## Update Password

> Success-Response:

```json

HTTP 200 OK
{
  "msg": 1
}

```

> Error-Response

```json
HTTP 422 Unprocessable entity
{
     "msg": 0,
     "error": "Your password was incorrect"
}

```

Update user Password when user is logged in

### HTTP Request

`POST https://code-query.herokuapp.com/v1/changePassword`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
old_password | String | Old Password of the user
new_password | String | New Password of the user

<aside class="success">
 User must be authorized to change password.Send user token in the header.
</aside>

## Send Code for Forgot Password

> Success-Response:

```json

HTTP 200 OK
{
  "msg": 1
}

```

> Error-Response

```json
HTTP 422 Unprocessable entity
{
     "msg": 0,
     "error": "Email not present in our database"
}

```

To reset password, Api will send code for resetting the password.

### HTTP Request

`POST https://code-query.herokuapp.com/v1/forgotPassword`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
email | String | Registered email of user


## Change Password (Forgot Password)

> Success-Response:

```json

HTTP 200 OK
{
  "msg": 1
}

```

> Error-Response

```json
HTTP 422 Unprocessable entity
{
     "msg": 0,
     "error": "Please enter correct OTP"
}

```

Change Password

### HTTP Request

`POST https://code-query.herokuapp.com/v1/updatePassword`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
code | String | Code sent to the registered mobile number
password | String | New Password


## Update User Info

> Success-Response:

```json

HTTP 200 OK
{
  "msg": 1
}

```

> Error-Response

```json
HTTP 422 Unprocessable entity
{
     "msg": 0
}

```

Update user credentials

### HTTP Request

`POST https://code-query.herokuapp.com/v1/updateUser`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
email | String | Email of user
name | String | User name
dob | String | Date of birth
s_class | String | Class of user
password | String | Password of user
college | String | college of user
specifications | Array | Specifications must be in array

<aside class="success">
 User must be authorized. Send user token in the header.
</aside>

