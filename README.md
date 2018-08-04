# Welcome to Red Queen's Hackathhon 2018!

## What is this?

This repository contains game data and art assets for the games participating in today's Hackathon.

## FAQ

### Q. Can I create something for a game that is not represented here?

### A. Absolutely.


## Slate API

For today's even, we have provided early access to an API actively under development. Slate API is designed to help Runecrafters handle things like storing user sessions in the cloud, and creating shareable pieces of content for creating rich experiences.

### Red Queen's Slate API v1.0beta

#### Supported Endpoints

##### Add a new Slate object to persistent storage

```http
POST https://api.redqueen.us/v1/slate
{
    "runeId": "0790609d-45b0-40b5-982c-521ca5526548",
    "ownerId": "eacbb5f2-f7ea-11e6-a0b7-1218132fb5f0",
    "data": "{\"someKey\": \"Some value.\"}",
    "isPublic": true
}
```

##### Add a new Counter object to persistent storage

```http
POST https://api.redqueen.us/v1/counter
{
    "runeId": "0790609d-45b0-40b5-982c-521ca5526548",
    "eventName": "MY_EVENT",
    "config": "{\"onlyMostRecent\": true}"
}
```

##### Add a new Event object to persistent storage

```http
POST https://api.redqueen.us/v1/event
{
    "runeId": "0790609d-45b0-40b5-982c-521ca5526548",
    "eventName": "MY_EVENT",
    "slateId": "deccdde8-2728-4479-9784-a93b8713ce24",
    "ownerId": "eacbb5f2-f7ea-11e6-a0b7-1218132fb5f0",
    "value": "{\"content\": \"This could be a sample comment.\"}",
    "isMostRecent": true
}
```

##### Add or update a User's Session Slate object to persistent storage

```http
PUT https://api.redqueen.us/v1/session/{runeId}/{userId}
{
    "runeId": "0790609d-45b0-40b5-982c-521ca5526548",
    "ownerId": "eacbb5f2-f7ea-11e6-a0b7-1218132fb5f0",
    "data": "{\"someKey\": \"Some value.\"}",
    "isPublic": true
}
```

##### Get a User's Session Slate object from persistent storage

```http
GET https://api.redqueen.us/v1/session/{runeId}/{userId}
```

##### Get one Slate from storage

```http
GET https://api.redqueen.us/v1/slate/{slateId}
```

##### Get all public slates for the specified Rune

```http
GET https://api.redqueen.us/v1/slates/{runeId}/{limit}?skip=n
```

##### Get all Events with `eventName` attached to `slateId`

```http
GET https://api.redqueen.us/v1/events/{slateId}/{eventName}
```

##### Get the count of how many Events with `eventName` attached to `slateId`

```http
GET https://api.redqueen.us/v1/events/{slateId}/{eventName}/count
```
