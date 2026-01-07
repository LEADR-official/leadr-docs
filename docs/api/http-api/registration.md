# Registration

## Create Jam Code

=== "Python"

    ```python
    import requests
    headers = {
      'Content-Type': 'application/json',
      'Accept': 'application/json',
      'leadr-api-key': 'string',
      'authorization': 'string',
      'leadr-client-nonce': 'string'
    }

    r = requests.post('/v1/jam-codes', headers = headers)

    print(r.json())

    ```

=== "JavaScript"

    ```javascript
    const inputBody = '{
      "code": "string",
      "description": "string",
      "features": {},
      "max_uses": 0,
      "expires_at": "2019-08-24T14:15:22Z"
    }';
    const headers = {
      'Content-Type':'application/json',
      'Accept':'application/json',
      'leadr-api-key':'string',
      'authorization':'string',
      'leadr-client-nonce':'string'
    };

    fetch('/v1/jam-codes',
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
`POST /v1/jam-codes`

Create a new jam code (superadmin only).

Jam codes can be used for promotional campaigns, game jams, or referral tracking.
They can optionally have usage limits, expiration dates, and custom features.

> Body parameter

```json
{
  "code": "string",
  "description": "string",
  "features": {},
  "max_uses": 0,
  "expires_at": "2019-08-24T14:15:22Z"
}
```

### Parameters

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|account_id|query|any|false|none|
|leadr-api-key|header|any|false|none|
|authorization|header|any|false|none|
|leadr-client-nonce|header|any|false|none|
|body|body|[CreateJamCodeRequest](./schemas.md#createjamcoderequest)|true|none|

> Example responses

> 201 Response

```json
{
  "id": "string",
  "code": "string",
  "description": "string",
  "features": {},
  "max_uses": 0,
  "current_uses": 0,
  "active": true,
  "expires_at": "2019-08-24T14:15:22Z",
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z"
}
```

### Responses

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Successful Response|[JamCodeResponse](./schemas.md#jamcoderesponse)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|[HTTPValidationError](./schemas.md#httpvalidationerror)|

!!! success
    This operation does not require authentication

## List Jam Codes

=== "Python"

    ```python
    import requests
    headers = {
      'Accept': 'application/json',
      'leadr-api-key': 'string',
      'authorization': 'string',
      'leadr-client-nonce': 'string'
    }

    r = requests.get('/v1/jam-codes', headers = headers)

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

    fetch('/v1/jam-codes',
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
`GET /v1/jam-codes`

List all jam codes (superadmin only).

Returns a paginated list of all jam codes, including their usage statistics.

### Parameters

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|account_id|query|any|false|none|
|cursor|query|any|false|Pagination cursor for navigating results|
|limit|query|integer|false|Number of items per page (1-100)|
|sort|query|any|false|Sort specification (e.g., 'value:desc,created_at:asc')|
|leadr-api-key|header|any|false|none|
|authorization|header|any|false|none|
|leadr-client-nonce|header|any|false|none|

> Example responses

> 200 Response

```json
{
  "data": [
    {
      "id": "scr_123",
      "value": 1000
    }
  ],
  "pagination": {
    "count": 20,
    "has_next": true,
    "has_prev": false,
    "next_cursor": "eyJwdiI6WzEwMDAsMTIzXX0="
  }
}
```

### Responses

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful Response|[PaginatedResponse_JamCodeResponse_](./schemas.md#paginatedresponse_jamcoderesponse_)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|[HTTPValidationError](./schemas.md#httpvalidationerror)|

!!! success
    This operation does not require authentication

## Get Jam Code

=== "Python"

    ```python
    import requests
    headers = {
      'Accept': 'application/json',
      'leadr-api-key': 'string',
      'authorization': 'string',
      'leadr-client-nonce': 'string'
    }

    r = requests.get('/v1/jam-codes/{jam_code_id}', headers = headers)

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

    fetch('/v1/jam-codes/{jam_code_id}',
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
`GET /v1/jam-codes/{jam_code_id}`

Get a specific jam code by ID (superadmin only).

### Parameters

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|jam_code_id|path|string(uuid)|true|none|
|account_id|query|any|false|none|
|leadr-api-key|header|any|false|none|
|authorization|header|any|false|none|
|leadr-client-nonce|header|any|false|none|

> Example responses

> 200 Response

```json
{
  "id": "string",
  "code": "string",
  "description": "string",
  "features": {},
  "max_uses": 0,
  "current_uses": 0,
  "active": true,
  "expires_at": "2019-08-24T14:15:22Z",
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z"
}
```

### Responses

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful Response|[JamCodeResponse](./schemas.md#jamcoderesponse)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|[HTTPValidationError](./schemas.md#httpvalidationerror)|

!!! success
    This operation does not require authentication

## Update Jam Code

=== "Python"

    ```python
    import requests
    headers = {
      'Content-Type': 'application/json',
      'Accept': 'application/json',
      'leadr-api-key': 'string',
      'authorization': 'string',
      'leadr-client-nonce': 'string'
    }

    r = requests.patch('/v1/jam-codes/{jam_code_id}', headers = headers)

    print(r.json())

    ```

=== "JavaScript"

    ```javascript
    const inputBody = '{
      "description": "string",
      "features": {},
      "max_uses": 0,
      "active": true,
      "expires_at": "2019-08-24T14:15:22Z"
    }';
    const headers = {
      'Content-Type':'application/json',
      'Accept':'application/json',
      'leadr-api-key':'string',
      'authorization':'string',
      'leadr-client-nonce':'string'
    };

    fetch('/v1/jam-codes/{jam_code_id}',
    {
      method: 'PATCH',
      body: inputBody,
      headers: headers
    })
    .then(function(res) {
        return res.json();
    }).then(function(body) {
        console.log(body);
    });

    ```
`PATCH /v1/jam-codes/{jam_code_id}`

Update a jam code (superadmin only).

Can update description, features, max uses, active status, and expiration.

> Body parameter

```json
{
  "description": "string",
  "features": {},
  "max_uses": 0,
  "active": true,
  "expires_at": "2019-08-24T14:15:22Z"
}
```

### Parameters

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|jam_code_id|path|string(uuid)|true|none|
|account_id|query|any|false|none|
|leadr-api-key|header|any|false|none|
|authorization|header|any|false|none|
|leadr-client-nonce|header|any|false|none|
|body|body|[UpdateJamCodeRequest](./schemas.md#updatejamcoderequest)|true|none|

> Example responses

> 200 Response

```json
{
  "id": "string",
  "code": "string",
  "description": "string",
  "features": {},
  "max_uses": 0,
  "current_uses": 0,
  "active": true,
  "expires_at": "2019-08-24T14:15:22Z",
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z"
}
```

### Responses

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful Response|[JamCodeResponse](./schemas.md#jamcoderesponse)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|[HTTPValidationError](./schemas.md#httpvalidationerror)|

!!! success
    This operation does not require authentication

## Initiate Registration

=== "Python"

    ```python
    import requests
    headers = {
      'Content-Type': 'application/json',
      'Accept': 'application/json'
    }

    r = requests.post('/v1/register/initiate', headers = headers)

    print(r.json())

    ```

=== "JavaScript"

    ```javascript
    const inputBody = '{
      "email": "user@example.com"
    }';
    const headers = {
      'Content-Type':'application/json',
      'Accept':'application/json'
    };

    fetch('/v1/register/initiate',
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
`POST /v1/register/initiate`

Initiate registration by sending a verification code to the provided email.

This endpoint is publicly accessible and requires no authentication.
A 6-character verification code will be sent to the email address.

> Body parameter

```json
{
  "email": "user@example.com"
}
```

### Parameters

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|[InitiateRegistrationRequest](./schemas.md#initiateregistrationrequest)|true|none|

> Example responses

> 201 Response

```json
{
  "message": "string",
  "code_expires_in": 0
}
```

### Responses

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Successful Response|[InitiateRegistrationResponse](./schemas.md#initiateregistrationresponse)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|[HTTPValidationError](./schemas.md#httpvalidationerror)|

!!! success
    This operation does not require authentication

## Verify Code

=== "Python"

    ```python
    import requests
    headers = {
      'Content-Type': 'application/json',
      'Accept': 'application/json'
    }

    r = requests.post('/v1/register/verify', headers = headers)

    print(r.json())

    ```

=== "JavaScript"

    ```javascript
    const inputBody = '{
      "email": "user@example.com",
      "code": "string"
    }';
    const headers = {
      'Content-Type':'application/json',
      'Accept':'application/json'
    };

    fetch('/v1/register/verify',
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
`POST /v1/register/verify`

Verify an email verification code and return a temporary token.

This endpoint validates the verification code and returns a short-lived
token that can be used to complete the registration process.

> Body parameter

```json
{
  "email": "user@example.com",
  "code": "string"
}
```

### Parameters

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|[VerifyCodeRequest](./schemas.md#verifycoderequest)|true|none|

> Example responses

> 200 Response

```json
{
  "verification_token": "string",
  "expires_in": 0
}
```

### Responses

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful Response|[VerifyCodeResponse](./schemas.md#verifycoderesponse)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|[HTTPValidationError](./schemas.md#httpvalidationerror)|

!!! success
    This operation does not require authentication

## Complete Registration

=== "Python"

    ```python
    import requests
    headers = {
      'Content-Type': 'application/json',
      'Accept': 'application/json'
    }

    r = requests.post('/v1/register/complete', headers = headers)

    print(r.json())

    ```

=== "JavaScript"

    ```javascript
    const inputBody = '{
      "verification_token": "string",
      "account_name": "string",
      "account_slug": "string",
      "jam_code": "string",
      "display_name": "string"
    }';
    const headers = {
      'Content-Type':'application/json',
      'Accept':'application/json'
    };

    fetch('/v1/register/complete',
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
`POST /v1/register/complete`

Complete registration by creating the account, user, and API key.

This endpoint creates the full account structure:
- Account with the specified name and slug
- User associated with the verified email
- API key for CLI authentication
- Optional jam code redemption

The API key is returned in plaintext and should be stored securely by the client.

> Body parameter

```json
{
  "verification_token": "string",
  "account_name": "string",
  "account_slug": "string",
  "jam_code": "string",
  "display_name": "string"
}
```

### Parameters

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|[CompleteRegistrationRequest](./schemas.md#completeregistrationrequest)|true|none|

> Example responses

> 201 Response

```json
{
  "account_id": "string",
  "account_slug": "string",
  "api_key": "string",
  "display_name": "string"
}
```

### Responses

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Successful Response|[CompleteRegistrationResponse](./schemas.md#completeregistrationresponse)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|[HTTPValidationError](./schemas.md#httpvalidationerror)|

!!! success
    This operation does not require authentication

## Resend Verification Code

=== "Python"

    ```python
    import requests
    headers = {
      'Content-Type': 'application/json',
      'Accept': 'application/json'
    }

    r = requests.post('/v1/register/resend-code', headers = headers)

    print(r.json())

    ```

=== "JavaScript"

    ```javascript
    const inputBody = '{
      "email": "user@example.com"
    }';
    const headers = {
      'Content-Type':'application/json',
      'Accept':'application/json'
    };

    fetch('/v1/register/resend-code',
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
`POST /v1/register/resend-code`

Resend a verification code to the provided email.

This endpoint invalidates any existing codes for the email and sends a new one.

> Body parameter

```json
{
  "email": "user@example.com"
}
```

### Parameters

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|[InitiateRegistrationRequest](./schemas.md#initiateregistrationrequest)|true|none|

> Example responses

> 200 Response

```json
{
  "message": "string",
  "code_expires_in": 0
}
```

### Responses

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful Response|[InitiateRegistrationResponse](./schemas.md#initiateregistrationresponse)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|[HTTPValidationError](./schemas.md#httpvalidationerror)|

!!! success
    This operation does not require authentication
