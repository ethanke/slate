---
title: Live API Reference

language_tabs:
  - shell
  - json

toc_footers:
  - <!--<a href='#'>Sign Up for a Developer Key</a>-->
  - <!--<a href='https://github.com/tripit/slate'>Documentation Powered by Slate</a>-->

includes:
  - errors

search: true
---

# Introduction

Welcome to the LIVE API! You can use this API to access Live API endpoints, which can get information on various Artist, Users, Places and Events in the database.

We have language bindings in Shell, Ruby, and Python! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.


# Authentication

> To log in the user on the api, use this code:

```shell
curl --request POST \
     --url '93.113.206.223:8080/login' \
     --header 'content-type: application/x-www-form-urlencoded' \
     --data 'token={unique_device_id}&platform={web || ios || android}&version={your_app_version}}&device_name={device_name}'
```

```json
{
   "response": "Connected",
   "success": true,
   "token": "42",
   "config": {
      "min_radius": "1000",
      "max_radius": "10000",
      "secret_question": [
         "Quel est le nom de jeune fille de votre mère?",
         "Quel est le premier groupe que vous êtes allés voir en concert?",
         "Quel est le nom de votre premier animal de compagnie?"
      ]
   }
}
```

> Make sure to replace everything inside '{..}' with your data.

Live uses a token to allow access to the API. You must include your token in every request.
You should call this request every time your app is used to make sure your token is marked as connected in the database.
It will register a new token if the token you gave is not known in the database.
It will also give you some basic app requierement you must follow.

### HTTP Request

`POST http://93.113.206.223:8080/login`

### Query Parameters

Parameter | Description
--------- | -----------
token | A UNIQUE device identifier, could be a devide ID on mobile or mac address on website.
platform | A device description such as iOS, Android, Windows, or Mac.
device_name | A device name, example: Vico-iPhone.
version | The version code of the app your are building, example 1.12.

<aside class="success">
  Remember — Save the token where you can have easy access to it.
  <br>You must reuse the same token for every other request.
</aside>


# Artist

## Get Artists

```shell

curl --request POST \
     --url '93.113.206.223:8080/get/artist' \
     --header 'content-type: application/x-www-form-urlencoded' \
     --data 'token={unique_device_id}&artist_id={optional_artist_id}
```

```json
{
   "response": "Artist",
   "success": true,
   "token": "42",
   "artist": [
      {
         "__v": 0,
         "_id": "58a625dc35b08a03442a58d1",
         "access_limit": null,
         "access_token": null,
         "average_feedback": "5",
         "background_image": "photo-1487513743885",
         "description": "Développer account, testing purpose",
         "email": "vicostudio@gmail.com",
         "facebook_id": "1445402898817253",
         "instagram_id": "387513160",
         "instagram_token": "387513160.840568e.ff3661ddcc324ce6b5c21b0cb2f6fbb2",
         "name": "Victor Sousa",
         "nb_feedback": "12",
         "password": "da3ff4793bfb175b597e93e421fd1bdbe874065212f14b6b9761945ab7c80935b586090114267b29aa70e2181116841e5e9b79b95ec5595debb63b35a8bb7621",
         "profil_image": "photo-1487283720945",
         "soundcloud_id": "284658194",
         "style": "Personnal account",
         "event": [
            {
               "place": {
                  "name": "Les 3 Diables",
                  "address": "2, Cours Saleya",
                  "city": "Nice",
                  "code_postal": "06300",
                  "latitude": "43.69533790000001",
                  "longitude": "7.2764073",
                  "picture": "photo-1489293534318",
                  "_id": "58c4d0dedda72238fe377ee6",
                  "__v": 0,
                  "feedback": [
                     "58c4d0dedda72238fe377ee1",
                     "58c4d0dedda72238fe377ee2",
                     "58c4d0dedda72238fe377ee3",
                     "58c4d0dedda72238fe377ee4",
                     "58c4d0dedda72238fe377ee5"
                  ]
               },
               "artist": "58a625dc35b08a03442a58d1",
               "date": "3/12/2017 ",
               "_id": "58c4d0dedda72238fe377ee7",
               "__v": 0,
               "date_full": "2017-03-12T18:00:00.000Z"
            },
            {
               "place": {
                  "name": "KFC Nice Jean Médecin",
                  "address": "64, Avenue Jean Médecin",
                  "city": "Nice",
                  "code_postal": "06000",
                  "latitude": "43.7052351",
                  "longitude": "7.2653097",
                  "picture": "photo-1489349559080",
                  "_id": "58c5abb72c7ea70610d2ae79",
                  "__v": 0,
                  "feedback": [
                     "58c5abb72c7ea70610d2ae74",
                     "58c5abb72c7ea70610d2ae75",
                     "58c5abb72c7ea70610d2ae76",
                     "58c5abb72c7ea70610d2ae77",
                     "58c5abb72c7ea70610d2ae78"
                  ]
               },
               "artist": "58a625dc35b08a03442a58d1",
               "date": "3/12/2017 ",
               "_id": "58c5abb72c7ea70610d2ae7a",
               "__v": 0,
               "date_full": "2017-03-12T21:12:00.000Z"
            }
         ],
         "feedback": [
            {
               "title": "super concert",
               "content": "Top bonne bière! ",
               "note": 4,
               "pseudo": "jml",
               "imageUrl": "photo-1487701112604",
               "_id": "58ac8479b1fb3c09d7456029",
               "__v": 0,
               "date": "2017-02-21T18:18:33.229Z",
               "reported": false
            },
            {
               "title": "ça a l'air de marcher !",
               "content": "Et ouais !",
               "note": 4,
               "pseudo": "coucou",
               "imageUrl": "photo-1487708929510",
               "_id": "58aca30bb1fb3c09d745603d",
               "__v": 0,
               "date": "2017-02-21T20:28:59.210Z",
               "reported": false
            }
         ]
      }
   ]
}
```

> Make sure to replace everything inside '{..}' with your data.

This endpoint retrieves artists.

### HTTP Request

`POST http://93.113.206.223:8080/get/artist`

### Query Parameters

Parameter | Optional | Description
--------- | -------- | -----------
token | NO | Your UNIQUE device identifier.
artist_id | YES | If set, endpoint will only fill the array with the id corresponding artist.


## Create Artist

```shell
curl --request POST \
     --url 'http://93.113.206.223:8080/create/artist_account' \
     --header 'content-type: application/x-www-form-urlencoded' \
     --data 'token={unique_device_id}&name={artist_name}&style={artist_style}&password={artist_password}&description={artist_description}&email={artist_email}&secret_question={secret_question_string}&secret_response={secret_response_string}'
```

```json
{
   "response": "Artist created",
   "success": true,
   "token": "token",
   "artist_id": "artist_ID"
}
```

> Make sure to replace everything inside '{..}' with your data.

This endpoint creates an artists in the database.
It also connect your token to the artist if the creation is successfull.

### HTTP Request

`POST http://93.113.206.223:8080/create/artist_account`

### Query Parameters

Parameter | Description
--------- | -----------
token | Your UNIQUE device identifier.
name | The name of the artist to create.
email | His email.
password | His password.
style | His style.
description | His description.
secret_question | The string value of the questions he picked (must be one of those given in <a href='#authentication'>login</a>).
secret_response | His secret response.


## Connect Artist

```shell
curl --request POST \
     --url '93.113.206.223:8080/connect/artist_account' \
     --header 'content-type: application/x-www-form-urlencoded' \
     --data 'token={unique_device_id}&email={artist_email}&password={artist_password}'
```

```json
{
   "response": "Connection successfull",
   "success": true,
   "token": "42"
}
```

> Make sure to replace everything inside '{..}' with your data.

This endpoint connect your token to an artist.

### HTTP Request

`POST http://93.113.206.223:8080/connect/artist_account`

### Query Parameters

Parameter | Description
--------- | -----------
token | Your UNIQUE device identifier.
email | The artist email.
password | His password.


## Disconnect Artist

```shell
curl --request POST \
  --url '93.113.206.223:8080/logout/artist_account' \
  --header 'content-type: application/x-www-form-urlencoded' \
  --data 'token={unique_device_id}'
```

```json
{
   "response": "Disconnection successfull",
   "success": true,
   "token": "42"
}
```

> Make sure to replace everything inside '{..}' with your data.

This endpoint disconnect your token from the artist it is connected to.

### HTTP Request

`POST http://93.113.206.223:8080/logout/artist_account`

### Query Parameters

Parameter | Description
--------- | -----------
token | Your UNIQUE device identifier.
