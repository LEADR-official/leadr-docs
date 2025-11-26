# Authentication

## Refresh Session

=== "Python"

    ```python
    import requests
    headers = {
      'Content-Type': 'application/json',
      'Accept': 'application/json'
    }

    r = requests.post('/v1/client/sessions/refresh', headers = headers)

    print(r.json())

    ```

=== "JavaScript"

    ```javascript
    const inputBody = '{
      "refresh_token": "string"
    }';
    const headers = {
      'Content-Type':'application/json',
      'Accept':'application/json'
    };

    fetch('/v1/client/sessions/refresh',
    {
      method: 'POST',
      body: inputBody,
      headers: headers
    })
    .then(function(res) {
        return res.json();
    }).then(function(body) {
        console.log(body);
    });

    ```
`POST /v1/client/sessions/refresh`

Refresh an expired access token using a valid refresh token.

This endpoint implements token rotation for security:
- Returns new access and refresh tokens
- Increments the token version
- Invalidates the old refresh token (prevents replay attacks)

No authentication is required (the refresh token itself is the credential).

Args:
    request: Refresh token request
    service: DeviceService dependency

Returns:
    RefreshTokenResponse with new tokens

Raises:
    401: Invalid or expired refresh token
    422: Invalid request (missing refresh_token)

> Body parameter

```json
{
  "refresh_token": "string"
}
```

### Parameters

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|[RefreshTokenRequest](./schemas.md#refreshtokenrequest)|true|none|

> Example responses

> 200 Response

```json
{
  "access_token": "string",
  "refresh_token": "string",
  "expires_in": 0
}
```

### Responses

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful Response|[RefreshTokenResponse](./schemas.md#refreshtokenresponse)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|[HTTPValidationError](./schemas.md#httpvalidationerror)|

!!! success
    This operation does not require authentication

## Generate Nonce

=== "Python"

    ```python
    import requests
    headers = {
      'Accept': 'application/json',
      'leadr-api-key': 'string',
      'authorization': 'string',
      'leadr-client-nonce': 'string'
    }

    r = requests.get('/v1/client/nonce', headers = headers)

    print(r.json())

    ```

=== "JavaScript"

    ```javascript

    const headers = {
      'Accept':'application/json',
      'leadr-api-key':'string',
      'authorization':'string',
      'leadr-client-nonce':'string'
    };

    fetch('/v1/client/nonce',
    {
      method: 'GET',

      headers: headers
    })
    .then(function(res) {
        return res.json();
    }).then(function(body) {
        console.log(body);
    });

    ```
`GET /v1/client/nonce`

Generate a fresh nonce for replay protection.

Nonces are single-use tokens with short TTL (60 seconds) that clients must
obtain before making mutating requests (POST, PATCH, DELETE). This prevents
replay attacks by ensuring each request is fresh and authorized.

Requires device authentication via access token.

Args:
    auth: Authenticated client auth context (device guaranteed non-None)
    service: NonceService dependency

Returns:
    NonceResponse with nonce_value and expires_at

Raises:
    401: Invalid or missing device token

Example:
    1. Client calls GET /client/nonce with Authorization header
    2. Server returns nonce_value and expires_at
    3. Client includes nonce in leadr-client-nonce header for mutations
    4. Server validates and consumes nonce (single-use)

### Parameters

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|account_id|query|any|false|none|
|leadr-api-key|header|any|false|none|
|authorization|header|any|false|none|
|leadr-client-nonce|header|any|false|none|

> Example responses

> 200 Response

```json
{
  "nonce_value": "string",
  "expires_at": "2019-08-24T14:15:22Z"
}
```

### Responses

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful Response|[NonceResponse](./schemas.md#nonceresponse)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|[HTTPValidationError](./schemas.md#httpvalidationerror)|

!!! success
    This operation does not require authentication

## Start Session

=== "Python"

    ```python
    import requests
    headers = {
      'Content-Type': 'application/json',
      'Accept': 'application/json'
    }

    r = requests.post('/v1/client/sessions', headers = headers)

    print(r.json())

    ```

=== "JavaScript"

    ```javascript
    const inputBody = '{
      "game_id": "string",
      "client_fingerprint": "string",
      "platform": "string",
      "metadata": {}
    }';
    const headers = {
      'Content-Type':'application/json',
      'Accept':'application/json'
    };

    fetch('/v1/client/sessions',
    {
      method: 'POST',
      body: inputBody,
      headers: headers
    })
    .then(function(res) {
        return res.json();
    }).then(function(body) {
        console.log(body);
    });

    ```
`POST /v1/client/sessions`

Start a new device session for a game client.

This endpoint authenticates game clients and provides JWT access tokens.
It is idempotent - calling multiple times for the same device updates last_seen_at
and generates a new access token.

No authentication is required to call this endpoint (it IS the authentication).

Args:
    request: Session start request with game_id and device_id
    service: DeviceService dependency

Returns:
    StartSessionResponse with device info and access token

Raises:
    404: Game not found
    422: Invalid request (missing required fields, invalid UUID format)

> Body parameter

```json
{
  "game_id": "string",
  "client_fingerprint": "string",
  "platform": "string",
  "metadata": {}
}
```

### Parameters

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|[StartSessionRequest](./schemas.md#startsessionrequest)|true|none|

> Example responses

> 201 Response

```json
{
  "id": "string",
  "game_id": "string",
  "client_fingerprint": "string",
  "account_id": "string",
  "platform": "string",
  "status": "active",
  "metadata": {},
  "access_token": "string",
  "refresh_token": "string",
  "expires_in": 0,
  "first_seen_at": "2019-08-24T14:15:22Z",
  "last_seen_at": "2019-08-24T14:15:22Z"
}
```

### Responses

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Successful Response|[StartSessionResponse](./schemas.md#startsessionresponse)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|[HTTPValidationError](./schemas.md#httpvalidationerror)|

!!! success
    This operation does not require authentication
