---
title: Suggestic Partners API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - python

toc_footers:
  - <a href='mailto:partners@suggestic.com'>Contact us for a Developer Key</a>
  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to Suggestic's Personalized Nutrition Platform. You can use our APIs and services to access out different modules and data.

<aside class="success">
The Suggestic Partner API is only available as part of our Partnership Program.
To get production access to the API <a href='mailto:partners@suggestic.com'>Please contact us.</a>
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
  "email": "pedro@corp.com",
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
`restrictions` | list | optional | Restriction slugs, user restrictions.
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
{
    "count": 1,
    "next": null,
    "previous": null,
    "results": [
        {
            "user_id": "d6044ee8-b372-45e0-b9dc-d21aad4fface",
            "email": "pedro@corp.com",
            "name": "Pedro",
            "restrictions": [],
            "extra_data": "{}"
        }
    ]
}
```

This endpoint retrieves all users from my organization.

### HTTP Request

`GET https://stg.api.suggestic.com/users`

## Get a Specific User


```python
import requests
```

```shell
curl "https://stg.api.suggestic.com/users/d6044ee8-b372-45e0-b9dc-d21aad4fface" \
  -H "Authorization: Token 2444bb179390b9dcfadb7f2555682074f885c805"
```


> The above command returns JSON structured like this:

```json
{
  "user_id": "d6044ee8-b372-45e0-b9dc-d21aad4fface",
  "email": "pedro@corp.com",
  "name": "Pedro",
  "restrictions": [],
  "extra_data": "{}"
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

> This example has shortened for sample reason.
> The above command returns JSON structured like this: 

```json
{
  "count": 2,
  "next": null,
  "previous": null,
  "results": [
    {
      "id": "01bbd541-939b-4b85-8d90-48ff0b02d0ee",
      "is_premium": true,
      "slug": "wheat-belly-10-day-grain-detox",
      "order": 2200,
      "name": "Wheat Belly 10-Day Grain Detox",
      "author": "Dr. William Davis",
      "description_long": "The Wheat Belly 10-Day Grain Detox is unlike all other “detox” programs before it. It does not involve “cleansing” your body with various juices or a magical concoction of supplements purported to remove body “toxins,” nor a schedule of daily enemas that complicate your meeting schedule. It is a detoxification process from wheat and grains, a detoxification in the truest sense of the term. \r\n\r\nThis 10-Day Grain Detox distills all the wisdom of the original Wheat Belly books,  incorporating the most insightful, cutting-edge and effective strategies, and sharing them with you so that you can begin your path to weight and health success...in a short 10 days. \r\n\r\nThe Three Steps of Grain Detox are:\r\n1: Eliminate all grains\r\n-Start with a grain-free kitchen\r\n-Eliminate hidden sources by reading labels\r\n-Go grain-free shopping \r\n\r\n2: Choose real, single-ingredient foods\r\n\r\n3: Manage carbohydrates",
      "description_short": "With the Wheat Belly 10-Day Grain Detox you will get great health benefits such as: weight loss, drops in blood sugar, reduction in blood pressure, improvement in skin conditions, better gastrointestinal health, among others.",
      "books": [
        {
          "url": "https://www.amazon.com/Wheat-Belly-10-Day-Reprogram-Amazing",
          "name": "10-Day Grain Detox"
        }
      ],
      "image": "https://sg-data.storage.googleapis.com/images_bucket/Cover.png",
      "cover": "https://sg-data.storage.googleapis.com/images_bucket/WheatBelly.png",
      "background_image": "https://sg-data.storage.googleapis.com:443/program/wheat-belly-10-day-grain-detox.png"
    },
    {
      "id": "074c7b86-057c-4d47-8f4b-7f4339c8d1f4",
      "is_premium": true,
      "slug": "healing-foods-28-day-reset",
      "order": 2100,
      "name": "Healing Foods 28-Day Reset",
      "author": "Dr. Michael Murray",
      "description_long": "The Healing Foods 28-Day Reset brings together healing forces that certain foods and their components exert on our health and well-being to provide a healthy eating and weight-loss program. This program incorporates the best of the most healthful diets in the world. \r\n\r\nOne of the goals of this program, is to instill the importance of eating a wider spectrum of health-promoting foods. Healing foods 28-Day reset is meant to help you appreciate how eating a wide variety of foods can improve your health and well-being. People who include a variety of different foods in their diets have a lower rate of obesity than those who consume the same foods day in and day out.  \r\nOpen your eyes and mouth, and take advantage of the incredible bounty of foods that is available to you!",
      "description_short": "Live Longer and Healthier—and Lose Weight— with the Healing Foods 28-Day reset",
      "books": [],
      "image": "https://sg-data.storage.googleapis.com/images_bucket/Small_Murray.png",
      "cover": "https://sg-data.storage.googleapis.com/images_bucket/Back_Murray.png",
      "background_image": "https://sg-data.storage.googleapis.com:443/program/healing-foods-28-day-reset.png"
    }
  ]
}
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
{
  "id": "01bbd541-939b-4b85-8d90-48ff0b02d0ee",
  "is_premium": true,
  "slug": "wheat-belly-10-day-grain-detox",
  "order": 2200,
  "name": "Wheat Belly 10-Day Grain Detox",
  "author": "Dr. William Davis",
  "description_long": "The Wheat Belly 10-Day Grain Detox is unlike all other “detox” programs before it. It does not involve “cleansing” your body with various juices or a magical concoction of supplements purported to remove body “toxins,” nor a schedule of daily enemas that complicate your meeting schedule. It is a detoxification process from wheat and grains, a detoxification in the truest sense of the term. \r\n\r\nThis 10-Day Grain Detox distills all the wisdom of the original Wheat Belly books,  incorporating the most insightful, cutting-edge and effective strategies, and sharing them with you so that you can begin your path to weight and health success...in a short 10 days. \r\n\r\nThe Three Steps of Grain Detox are:\r\n1: Eliminate all grains\r\n-Start with a grain-free kitchen\r\n-Eliminate hidden sources by reading labels\r\n-Go grain-free shopping \r\n\r\n2: Choose real, single-ingredient foods\r\n\r\n3: Manage carbohydrates",
  "description_short": "With the Wheat Belly 10-Day Grain Detox you will get great health benefits such as: weight loss, drops in blood sugar, reduction in blood pressure, improvement in skin conditions, better gastrointestinal health, among others.",
  "books": [
    {
      "url": "https://www.amazon.com/Wheat-Belly-10-Day-Reprogram-Amazing",
      "name": "10-Day Grain Detox"
    }
  ],
  "image": "https://sg-data.storage.googleapis.com/images_bucket/Cover.png",
  "cover": "https://sg-data.storage.googleapis.com/images_bucket/WheatBelly.png",
  "background_image": "https://sg-data.storage.googleapis.com:443/program/wheat-belly-10-day-grain-detox.png"
}
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
{
  "count": 6,
  "next": null,
  "previous": null,
  "results": [
    {
      "name": "Avoid almonds",
      "slugname": "avoid-almonds"
    },
    {
      "name": "Avoid anchovies",
      "slugname": "avoid-anchovies"
    },
    {
      "name": "Avoid apple",
      "slugname": "avoid-apple"
    },
    {
      "name": "Avoid artichoke",
      "slugname": "avoid-artichoke"
    },
    {
      "name": "Avoid asparagus",
      "slugname": "avoid-asparagus"
    },
    {
      "name": "Avoid avocado",
      "slugname": "avoid-avocado"
    }
  ]
}
```

This endpoint retrieves all available restrictions.

### HTTP Request

`GET https://stg.api.suggestic.com/restrictions`
