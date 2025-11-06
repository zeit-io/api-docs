# API Docs

This repository contains some general information about the [ZEIT.IO](https://zeit.io) API. 
The API itself is available as Open API Specification. The Swagger UI is available [here](https://zeit.io/api-docs/index.html). 

## Users & Organisations

Entities at [ZEIT.IO](https://zeit.io) belong either to a user or to an organisation. 
An entity is for example a `project`, a `customer` or a `time_record`. 
In general, the entities are similar but not always the same. 
Entitities for an organisation are usually more complex and contain more information.

The API Endpoints are devided into two namespaces: 

 - **Usr/*** - Endpoints which deal with user entities. 
 - **Org/*** - Endpoints which deal with organisation entities. 

The endpoints with a `Usr/` prefix create/update/delete entities which belong directly to a user. 
The endpoints with a `Org/` prefix create/update/delete entities which belong directly to an organisation. 

## Authentication

Most of the [ZEIT.IO API Endpoints](https://zeit.io/api-docs/index.html) require authentication. 
Every user and every organisation has an API key. As a user you can find your API key [here](https://zeit.io/de/settings/api) if you are logged in. 
The API key of an organisation is located under the organisation settings. 

To interact with the `Usr/*` endpoints you will need a users API key. 
And to interact with the `Org/*` endpoints you will need an API key from an organisation.

The ZEIT.IO API expects the API key always in the HTTP header under `apiKey`. 
Here an example how to submit the API key with a curl request: 

```
curl -X GET "https://zeit.io/api/v1/usr/projects" -H  "accept: application/json" -H  "apiKey: 1Y9WMdOfU7WdF06a4sKQ2xbzKOhD0MaNrb2ikGQ5"
```

## JSON 

The ZEIT.IO API consumes and produces JSON! XML and other formats are not supported! 

## Currency values

ZEIT.IO supports multiple currencies and calculates various currency values. 
Currency values are always stored as Integer in the database and represent the cent values. 
For example, the currency value `123,95` EUR would be stored as `12395`. 
Properties like `amount` and `hourly_wage` contain always the cent values. 
The UI is responsible for formating the values in a human readible way. 
All inputs for the API expect currency values as Integer, representing the cents! 

## Time duration values 

Time values are always stored as Integer in the database and represent the seconds. 
If a user records a `time_record` of one hour, ZEIT.IO will store the value of 3600 as `time_record.duration` in the database. 
Because 3600 seconds is equal to one hour. 
The UI is responsible for formating the values in a human readible way.

## Date formats 

When sending dates to the API, the format is obviously very important.
The ZEIT.IO API supports various formats.
However, it is recommended to send all dates in the following format: `<%Y-%m-%d>`. 
Here an example. The 1st of April 2026 would be formated like this: `2026-04-01`.


## Time zones 

ZEIT.IO converts all time values from the users time zone to UTC and stores all times in UTC format in the database. 
When fetching the data, ZEIT.IO converts the times back from UTC to the users time zone. 
For this process it is very important that the user correctly configures his/her time zone. 
The time zone can be configured in the users settings under [Localization](https://zeit.io/en/settings/localization).
