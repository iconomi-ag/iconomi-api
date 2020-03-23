# Introduction
Welcome to the ICONOMI Platform API. There are two ways to integrate with the ICONOMI platform, the REST API and a stream-oriented API using Websockets.

## Versioning

This API maintains backward compatibility. Breaking changes to the API are managed by providing new endpoints. Old versions will remain available for two months after a new version is released and can then be removed at any time. All information about releases is published on this website.
Non-breaking changes are released in the same major-version API.

## Types

All request bodies should have content type application/json and be valid JSON.

<br/>

### Timestamps

Unless otherwise specified, all timestamps are returned in ISO 8601 with microseconds.

<br/> Example:

```
2019-08-01T01:02:03.000004Z
```

<br/>

### Numbers

Integers are unquoted.

<br/> Example:

```
"x": 194767
```

Decimals are returned as strings with a period as a decimal separator and no thousands separator.

<br/> Example:

```
"price": "3.3847"
```

<br/>

### IDs

All IDs are UUIDs.

<br/> Example:

``` 
6EFB3D83-830A-42F8-84CD-2C307FE62AD8
```

<br/>

### Enumerations

There are several enumerations on the platform that are used across the platform.

<br/>

#### DAA types
There are different types of DAAs supported on the platform which use different strategies for 
investment:

* **PASSIVE** DAAs that have structures based set on percentages and are rebalances less often

* **ACTIVE** DAAs that follow a more active strategy not using an index

<br/>

#### Granulations

Depending on the time period selected different granulation of data is possible as a result. 
For each of the granulations there will be one data point available:

* **TWO_MINUTE** - only available for institutional strategies. 
* **FIVE_MINUTE**
* **HOURLY**
* **THREE_HOURLY**
* **EIGHT_HOURLY**
* **DAILY**

## Rate limiting

The public API (both the REST API and the Websocket API) allows for 60 requests per minute. This rate is subject to change.

## Authentication

To access authenticated endpoints you need an account on the ICONOMI platform. After you have an account you need to setup your api
keys (you can find the option under Settings).

### Creating a request

All REST requests must contain the following headers:

* **ICN-API-KEY** The api key as a string.
* **ICN-SIGN** The base64-encoded signature (see Signing a Message).
* **ICN-TIMESTAMP** A timestamp for your request in epoch miliseconds.

<br/>
 
### Signing a Message

You generate the **ICN-SIGN** header by creating a **sha512 HMAC** using the base64-decoded secret key on the prehash string timestamp + method + requestPath + body (where + represents string concatenation) and base64-encode the output, where:
* the timestamp value is the same as the **ICN-TIMESTAMP** header.
* the body is the request body string or omitted if there is no request body (typically for GET requests). 
* method must always be in upper case

Example:
``` 
base64_encode(HMAC_SHA512(base64_decode(secret_key), timestamp + upper_case(method) + requestPath + body))
```

<br/>

### Websocket Authentication

It is possible to authenticate yourself when subscribing to the websocket feed.

When opening connection to websocket, add additional headers, as if you were signing a request. To get the necessary parameters, you would go through the same process as you do to make authenticated calls to the API.

## Sample libraries
You can find sample libraries for communicating with our API at our <a href="https://github.com/iconomi-ag" target="_blank" rel="nofollow">github page.</a>

## Bug reports
For any bug reports in the documentation or the API, feel free to report them to our <a href="https://github.com/iconomi-ag/iconomi-api" target="_blank" rel="nofollow">github page.</a>