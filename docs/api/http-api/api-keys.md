# API Keys

## Create Api Key

=== "Python"

    ```python
    import requests
    headers = {
      'Content-Type': 'application/json',
      'Accept': 'application/json',
      'leadr-api-key': 'string'
    }

    r = requests.post('/v1/api-keys', headers = headers)

    print(r.json())

    ```

=== "JavaScript"

    ```javascript
    const inputBody = '{
      "account_id": "449e7a5c-69d3-4b8a-aaaf-5c9b713ebc65",
      "name": "string",
      "expires_at": "2019-08-24T14:15:22Z"
    }';
    const headers = {
      'Content-Type':'application/json',
      'Accept':'application/json',
      'leadr-api-key':'string'
    };

    fetch('/v1/api-keys',
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
`POST /v1/api-keys`

Create a new API key for an account.

The plain API key is returned only once in this response.
Store it securely as it cannot be retrieved later.

Returns:
    CreateAPIKeyResponse with the plain key included.

Raises:
    404: Account not found.

> Body parameter

```json
{
  "account_id": "449e7a5c-69d3-4b8a-aaaf-5c9b713ebc65",
  "name": "string",
  "expires_at": "2019-08-24T14:15:22Z"
}
```

### Parameters

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|leadr-api-key|header|any|false|none|
|body|body|[CreateAPIKeyRequest](./schemas.md#createapikeyrequest)|true|none|

> Example responses

> 201 Response

```json
{
  "id": "497f6eca-6276-4993-bfeb-53cbbbba6f08",
  "name": "string",
  "key": "string",
  "prefix": "string",
  "status": "active",
  "expires_at": "2019-08-24T14:15:22Z",
  "created_at": "2019-08-24T14:15:22Z"
}
```

### Responses

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Successful Response|[CreateAPIKeyResponse](./schemas.md#createapikeyresponse)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|[HTTPValidationError](./schemas.md#httpvalidationerror)|

!!! success
    This operation does not require authentication

## List Api Keys

=== "Python"

    ```python
    import requests
    headers = {
      'Accept': 'application/json',
      'leadr-api-key': 'string'
    }

    r = requests.get('/v1/api-keys', params={
      'account_id': 'string'
    }, headers = headers)

    print(r.json())

    ```

=== "JavaScript"

    ```javascript

    const headers = {
      'Accept':'application/json',
      'leadr-api-key':'string'
    };

    fetch('/v1/api-keys?account_id=string',
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
`GET /v1/api-keys`

List API keys for an account with optional filters.

TODO: Replace account_id query param with account_id from auth token.

Args:
    account_id: Account ID to filter results (REQUIRED for multi-tenant safety).
    status: Optional status to filter results (active or revoked).

Returns:
    List of API keys matching the filters.

### Parameters

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|account_id|query|string(uuid4)|true|Account ID to filter by|
|status|query|any|false|Filter by status|
|leadr-api-key|header|any|false|none|

> Example responses

> 200 Response

```json
[
  {
    "id": "497f6eca-6276-4993-bfeb-53cbbbba6f08",
    "account_id": "449e7a5c-69d3-4b8a-aaaf-5c9b713ebc65",
    "name": "string",
    "prefix": "string",
    "status": "active",
    "last_used_at": "2019-08-24T14:15:22Z",
    "expires_at": "2019-08-24T14:15:22Z",
    "created_at": "2019-08-24T14:15:22Z",
    "updated_at": "2019-08-24T14:15:22Z"
  }
]
```

### Responses

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful Response|Inline|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|[HTTPValidationError](./schemas.md#httpvalidationerror)|

### Response Schema

Status Code **200**

*Response List Api Keys V1 Api Keys Get*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|Response List Api Keys V1 Api Keys Get|[[APIKeyResponse](./schemas.md#apikeyresponse)]|false|none|[Response schema for API key details.<br><br>Excludes sensitive information like key_hash.<br>The full key is never returned after creation.]|
|» APIKeyResponse|[APIKeyResponse](./schemas.md#apikeyresponse)|false|none|Response schema for API key details.<br><br>Excludes sensitive information like key_hash.<br>The full key is never returned after creation.|
|»» id|string(uuid)|true|none|Unique identifier for the API key|
|»» account_id|string(uuid)|true|none|ID of the account this key belongs to|
|»» name|string|true|none|Human-readable name for the API key|
|»» prefix|string|true|none|Key prefix for identification (first 8 characters)|
|»» status|[APIKeyStatus](./schemas.md#apikeystatus)|true|none|API Key status enumeration.|
|»» last_used_at|any|false|none|Timestamp of last successful authentication (UTC)|

*anyOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» *anonymous*|string(date-time)|false|none|none|

*or*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» *anonymous*|null|false|none|none|

*continued*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» expires_at|any|false|none|Expiration timestamp (UTC), or null if never expires|

*anyOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» *anonymous*|string(date-time)|false|none|none|

*or*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» *anonymous*|null|false|none|none|

*continued*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» created_at|string(date-time)|true|none|Timestamp when the key was created (UTC)|
|»» updated_at|string(date-time)|true|none|Timestamp of last update (UTC)|

#### Enumerated Values

|Property|Value|
|---|---|
|status|active|
|status|revoked|

!!! success
    This operation does not require authentication

## Get Api Key

=== "Python"

    ```python
    import requests
    headers = {
      'Accept': 'application/json',
      'leadr-api-key': 'string'
    }

    r = requests.get('/v1/api-keys/{key_id}', headers = headers)

    print(r.json())

    ```

=== "JavaScript"

    ```javascript

    const headers = {
      'Accept':'application/json',
      'leadr-api-key':'string'
    };

    fetch('/v1/api-keys/{key_id}',
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
`GET /v1/api-keys/{key_id}`

Get a single API key by ID.

Args:
    key_id: The UUID of the API key to retrieve.

Returns:
    APIKeyResponse with key details (excludes the plain key).

Raises:
    404: API key not found.

### Parameters

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|key_id|path|string(uuid4)|true|none|
|leadr-api-key|header|any|false|none|

> Example responses

> 200 Response

```json
{
  "id": "497f6eca-6276-4993-bfeb-53cbbbba6f08",
  "account_id": "449e7a5c-69d3-4b8a-aaaf-5c9b713ebc65",
  "name": "string",
  "prefix": "string",
  "status": "active",
  "last_used_at": "2019-08-24T14:15:22Z",
  "expires_at": "2019-08-24T14:15:22Z",
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z"
}
```

### Responses

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful Response|[APIKeyResponse](./schemas.md#apikeyresponse)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|[HTTPValidationError](./schemas.md#httpvalidationerror)|

!!! success
    This operation does not require authentication

## Update Api Key

=== "Python"

    ```python
    import requests
    headers = {
      'Content-Type': 'application/json',
      'Accept': 'application/json',
      'leadr-api-key': 'string'
    }

    r = requests.patch('/v1/api-keys/{key_id}', headers = headers)

    print(r.json())

    ```

=== "JavaScript"

    ```javascript
    const inputBody = '{
      "status": "active",
      "deleted": true
    }';
    const headers = {
      'Content-Type':'application/json',
      'Accept':'application/json',
      'leadr-api-key':'string'
    };

    fetch('/v1/api-keys/{key_id}',
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
`PATCH /v1/api-keys/{key_id}`

Update an API key.

Currently supports:
- Updating status (e.g., to revoke a key)
- Soft delete via deleted flag

Args:
    key_id: The UUID of the API key to update.
    request: Update request with optional status and deleted fields.

Returns:
    APIKeyResponse with updated key details.

Raises:
    404: API key not found.

> Body parameter

```json
{
  "status": "active",
  "deleted": true
}
```

### Parameters

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|key_id|path|string(uuid4)|true|none|
|leadr-api-key|header|any|false|none|
|body|body|[UpdateAPIKeyRequest](./schemas.md#updateapikeyrequest)|true|none|

> Example responses

> 200 Response

```json
{
  "id": "497f6eca-6276-4993-bfeb-53cbbbba6f08",
  "account_id": "449e7a5c-69d3-4b8a-aaaf-5c9b713ebc65",
  "name": "string",
  "prefix": "string",
  "status": "active",
  "last_used_at": "2019-08-24T14:15:22Z",
  "expires_at": "2019-08-24T14:15:22Z",
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z"
}
```

### Responses

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful Response|[APIKeyResponse](./schemas.md#apikeyresponse)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|[HTTPValidationError](./schemas.md#httpvalidationerror)|

!!! success
    This operation does not require authentication
