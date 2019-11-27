---
title: Suggestic Partners API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - python

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the Suggestic Partners API You can use our Partners API to access Suggestic API endpoints, which can get or create information from or databases.

<aside class="success">
The Suggestic Partner API is only available under our Partnership Programs.
To get a production access to the API <a href='mailto:hello@suggestic.com'>Please contact us.</a>
</aside>

<aside class="notice">
All examples documented here can be tested on or staging enviroment <code>https://stg.api.suggestic.com</code>.
You shoul replace the url to <code>https://api.suggestic.com</code> when ready for production.
</aside>

# Authentication

Suggestic uses API keys to allow access to the API.

Suggestic expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: Token 2444bb179390b9dcfadb7f2555682074f885c805`

<aside class="notice">
You must replace <code>Token {API-KEY}</code> with your personal API key.
</aside>

# Users
## Create new User
```python
import requests

user = {
  "name": "Pedro",
  "email": "pedro@corp.com"
}
response = requests.post(
    "https://stg.api.suggestic.com/users",
    headers={"Authorization": "Token 2444bb179390b9dcfadb7f2555682074f885c805"},
    data=user
)
print(response.json())
```

```shell
curl "https://stg.api.suggestic.com/users" \
    -H "Authorization: Token 2444bb179390b9dcfadb7f2555682074f885c805" \
    -d 'email=pedro@corp.com' \
    -d 'name=Pedrro'
```

> The above command returns JSON structured like this:

```json
{
  "name": [
    "Pedro"
  ],
  "email": [
    "pedro@corp.com"
  ],
  "extra_data": "{}"
}
```
This endpoint creates a new user in to Suggestic

### HTTP Request

`POST https://stg.api.suggestic.com/users`

### Arguments

Parameter | Type | Required | Description
--------- | ----------- | ----------- | -----------
`name` | string | required | The user Name.
`email` | string | required | The user Email.
`program` | string | required | rogram ID, this will be the user initial program.
`restrictions` | list | optional | Restriction ID's, user restrictions.
`extra_data` | json string | optional | Extra user related meta data.

## Get All Users

```python
import requests

response = requests.get(
    "https://stg.api.suggestic.com/users",
    headers={"Authorization": "Token 2444bb179390b9dcfadb7f2555682074f885c805 "}
)
```

```shell
curl "https://stg.api.suggestic.com/users" \
    -H "Authorization: Token 2444bb179390b9dcfadb7f2555682074f885c805"
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
  }
]
```

This endpoint retrieves all users from my organization.

### HTTP Request

`GET https://stg.api.suggestic.com/users`

## Get a Specific User


```python
import requests
```

```shell
curl "http://example.com/api/kittens/2"
  -H "Authorization: meowmeowmeow"
```


> The above command returns JSON structured like this:

```json
{
  "id": 2,
}
```

This endpoint retrieves a specific user.

### HTTP Request

`GET https://stg.api.suggestic.com/users/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the user to retrive


# Programs
## Get all Programs

```python
import requests

response = requests.get(
    "https://stg.api.suggestic.com/programs",
    headers={"Authorization": "Token 2444bb179390b9dcfadb7f2555682074f885c805"}
)
```

```shell
curl "https://stg.api.suggestic.com/programs" \
    -H "Authorization: Token 2444bb179390b9dcfadb7f2555682074f885c805"
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
  }
]
```

This endpoint retrieves all programs.

### HTTP Request

`GET https://stg.api.suggestic.com/programs`


## Get a Specific Program

```python
import requests

response = requests.get(
    "https://stg.api.suggestic.com/programs/1",
    headers={"Authorization": "Token 2444bb179390b9dcfadb7f2555682074f885c805"}
)
```

```shell
curl "https://stg.api.suggestic.com/programs/1" \
    -H "Authorization: Token 2444bb179390b9dcfadb7f2555682074f885c805"
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
  }
]
```

This endpoint retrives a especific program

### HTTP Request

`GET https://stg.api.suggestic.com/programs/{ID}`

# Restriction
## Get all Restrictions

```python
import requests

response = requests.get(
    "https://stg.api.suggestic.com/restrictions",
    headers={"Authorization": "Token 2444bb179390b9dcfadb7f2555682074f885c805"}
)
```

```shell
curl "https://stg.api.suggestic.com/restrictions" \
    -H "Authorization: Token 2444bb179390b9dcfadb7f2555682074f885c805"
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
  }
]
```

This endpoint retrieves all available restrictions.

### HTTP Request

`GET https://stg.api.suggestic.com/restrictions`