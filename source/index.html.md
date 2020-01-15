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

# Posts

## Add Posts

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
     "error": "Unable to add post"
}

```

Add Post

### HTTP Request

`POST https://code-query.herokuapp.com/v1/posts`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
name | String | name of post
detail | String | description of post
photo | String | Photo of post
tags | Array of string | tags of current post in array

<aside class="success">
 User must be authorized. Send user token in the header.
</aside>

## Fetch Single Post

> Success-Response:

```json

HTTP 200 OK
{
  "msg": 1,
  "post":  {
        "id": 1,
        "user_id": 1,
        "tags": [
            "js",
            "c++"
        ],
        "detail": "djfhjdhfjhdjhfdjhfjdhfjd dfhdfjhdjfh jdhhfjfhsksjd jdchfksfh kdhfkdhfkjdh jkhfdg jkf",
        "name": "js baics",
        "photo": "/uploads/8737hjdfh73.jpg",
        "is_active": true,
        "created_at": "2019-09-23T05:59:20.127Z",
        "updated_at": "2019-09-23T06:14:24.359Z"
    }
}

```

> Error-Response

```json
HTTP 422 Unprocessable entity
{
     "msg": 0,
     "error": "Post not found"
}

```

fetch single post detail

### HTTP Request

`GET https://code-query.herokuapp.com/v1/posts/:id`
`GET https://code-query.herokuapp.com/v1/posts/1`

### Query Parameters

Send post id in url as shown

<aside class="success">
 User must be authorized. Send user token in the header.
</aside>


## Change Post Active Status

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
     "error": "Unable to change post status"
}

```

Change Post active status from true to false

### HTTP Request

`POST https://code-query.herokuapp.com/v1/changePostStatus`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
is_active | Boolean | true or false


<aside class="success">
 User must be authorized. Send user token in the header.
</aside>


## Fetch user specific posts

> Success-Response:

```json

HTTP 200 OK
{
  "msg": 1,
  "posts":  [
    {
        "id": 1,
        "user_id": 1,
        "tags": [
            "js",
            "c++"
        ],
        "detail": "djfhjdhfjhdjhfdjhfjdhfjd dfhdfjhdjfh jdhhfjfhsksjd jdchfksfh kdhfkdhfkjdh jkhfdg jkf",
        "name": "js baics",
        "photo": "/uploads/8737hjdfh73.jpg",
        "is_active": true,
        "created_at": "2019-09-23T05:59:20.127Z",
        "updated_at": "2019-09-23T06:14:24.359Z"
    }
  ]
}

```


Fetch user specific posts

### HTTP Request

`GET https://code-query.herokuapp.com/v1/fetchUserSpecificPosts`

### Query Parameters

No parameters

<aside class="success">
 User must be authorized. Send user token in the header.
</aside>

## Update Single Posts

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
     "error": "Unable to update post"
}

```
Update Post

### HTTP Request

`POST https://code-query.herokuapp.com/v1/updatePost`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
name | String | name of post
detail | String | description of post
photo | String | Photo of post
tags | Array of string | tags of current post in array

<aside class="success">
 User must be authorized. Send user token in the header.
</aside>


## Like or unlike Single Post

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
     "error": "Unable to update"
}

```

Like or Unlike Single post

### HTTP Request

`POST https://code-query.herokuapp.com/v1/likes`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
post_id | String | id of current post

<aside class="success">
 User must be authorized. Send user token in the header.
</aside>


# Queries

## Add Query

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
     "error": "title can't be blank"
}

```

Add Query

### HTTP Request

`POST https://code-query.herokuapp.com/v1/queries`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
title | String | title of query
description | String | description of query
category | String | Category of query

<aside class="success">
 User must be authorized. Send user token in the header.
</aside>


## Fetch Queries

> Success-Response:

```json

HTTP 200 OK
[
    {
        "id": 2,
        "user_id": 3,
        "title": "js",
        "description": "js testing",
        "category": "others",
        "created_at": "2020-01-14T05:14:44.596Z",
        "updated_at": "2020-01-14T05:14:44.596Z",
        "user_name": "shilpa",
        "comments_count": 4
    }
]

```
Fetch all Queries

### HTTP Request

`GET https://code-query.herokuapp.com/v1/queries`

<aside class="success">
 User must be authorized. Send user token in the header.
</aside>


## Delete Query

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
     "error": "Unable to delete query"
}

```

Delete Query

### HTTP Request

`POST https://code-query.herokuapp.com/v1/deleteQuery`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
id | Integer | ID of query

<aside class="success">
 User must be authorized. Send user token in the header.
</aside>

# Blogs

## Add Blog

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
     "error": "title can't be blank"
}

```

Add Query

### HTTP Request

`POST https://code-query.herokuapp.com/v1/blogs`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
title | String | title of blogs
description | String | description of blogs
tags | Array | tags of blogs

<aside class="success">
 User must be authorized. Send user token in the header.
</aside>


## Fetch Current User Blogs

> Success-Response:

```json

HTTP 200 OK
[
    {
        "id": 2,
        "user_id": 3,
        "title": "Javascript Functions",
        "description": "Testing testing",
        "tags": [
            "js"
        ],
        "created_at": "2020-01-12T10:32:55.289Z",
        "updated_at": "2020-01-12T10:32:55.289Z"
    }
]

```
Fetch all current user blogs

### HTTP Request

`GET https://code-query.herokuapp.com/v1/fetchUserBlogs`

<aside class="success">
 User must be authorized. Send user token in the header.
</aside>


## Fetch All Blogs

> Success-Response:

```json

HTTP 200 OK
[
    {
        "id": 2,
        "user_id": 3,
        "title": "Javascript Functions",
        "description": "Testing testing",
        "tags": [
            "js"
        ],
        "created_at": "2020-01-12T10:32:55.289Z",
        "updated_at": "2020-01-12T10:32:55.289Z"
    }
]

```
Fetch all blogs(for other users acc to specifications)

### HTTP Request

`GET https://code-query.herokuapp.com/v1/blogs`

<aside class="success">
 User must be authorized. Send user token in the header.
</aside>

## Delete Blog

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
     "error": "Unable to delete blog"
}

```

Delete Query

### HTTP Request

`POST https://code-query.herokuapp.com/v1/deleteBlog`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
id | Integer | ID of blog

<aside class="success">
 User must be authorized. Send user token in the header.
</aside>


#Comments

## Create Comment

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
     "error": "Not Allowed to answer the query"
}

```

Create Comment

### HTTP Request

`POST https://code-query.herokuapp.com/v1/comments`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
id | Integer | ID of query
body | text | body of comment

<aside class="success">
 User must be authorized. Send user token in the header.
</aside>

## Get all query Comments

> Success-Response:

```json

HTTP 200 OK
{
    "msg": 1,
    "comments": [
        {
            "id": 1,
            "user_id": 3,
            "query_id": 2,
            "body": "testing comment",
            "created_at": "2020-01-14T05:15:26.580Z",
            "updated_at": "2020-01-14T05:15:26.580Z",
            "parent_id": null,
            "user_name": "shilpa"
        },
        {
            "id": 2,
            "user_id": 3,
            "query_id": 2,
            "body": "testing comment 1",
            "created_at": "2020-01-14T10:07:12.245Z",
            "updated_at": "2020-01-14T10:07:12.245Z",
            "parent_id": null,
            "user_name": "shilpa"
        }
    ]
}

```

> Error-Response

```json
HTTP 422 Unprocessable entity
{
     "msg": 0,
     "error": "Body can't be blank"
}

```

Get all comments of queries

### HTTP Request

`POST https://code-query.herokuapp.com/v1/getQueryComments`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
id | Integer | ID of query

<aside class="success">
 User must be authorized. Send user token in the header.
</aside>
