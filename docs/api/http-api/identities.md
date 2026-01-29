# Identities

## List Identities

=== "Python"

    ```python
    import requests
    headers = {
      'Accept': 'application/json',
      'leadr-api-key': 'string',
      'authorization': 'string',
      'leadr-client-nonce': 'string'
    }

    r = requests.get('/v1/identities', headers = headers)

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

    fetch('/v1/identities',
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
`GET /v1/identities`

List identities for an account with optional filters and pagination.

Returns all non-deleted identities for the specified account, with optional
filtering by game or kind.

For regular users, account_id is automatically derived from their API key.
For superadmins, account_id is optional - if omitted, returns identities from all accounts.

Pagination:
- Default: 20 items per page, sorted by created_at:desc,id:asc
- Custom sort: Use ?sort=display_name:asc,created_at:desc
- Valid sort fields: id, display_name, kind, created_at, updated_at
- Navigation: Use next_cursor/prev_cursor from response

Example:
    GET /v1/identities?account_id=acc_123&game_id=game_456&kind=DEVICE&limit=50

Args:
    auth: Authentication context with user info.
    service: Injected identity service dependency.
    pagination: Pagination parameters (cursor, limit, sort).
    account_id: Optional account_id query parameter (superadmins can omit to see all).
    game_id: Optional game ID to filter by.
    kind: Optional kind to filter by (DEVICE, STEAM, CUSTOM).

Returns:
    PaginatedResponse with identities and pagination metadata.

Raises:
    400: Invalid cursor, sort field, kind, or cursor state mismatch.
    403: User does not have access to the specified account.

### Parameters

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|account_id|query|any|false|none|
|game_id|query|any|false|Filter by game ID|
|kind|query|any|false|Filter by identity kind|
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
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful Response|[PaginatedResponse_IdentityResponse_](./schemas.md#paginatedresponse_identityresponse_)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|[HTTPValidationError](./schemas.md#httpvalidationerror)|

!!! success
    This operation does not require authentication

## Get Identity

=== "Python"

    ```python
    import requests
    headers = {
      'Accept': 'application/json',
      'leadr-api-key': 'string',
      'authorization': 'string',
      'leadr-client-nonce': 'string'
    }

    r = requests.get('/v1/identities/{identity_id}', headers = headers)

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

    fetch('/v1/identities/{identity_id}',
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
`GET /v1/identities/{identity_id}`

Get an identity by ID.

Args:
    identity_id: Identity identifier to retrieve.
    service: Injected identity service dependency.
    auth: Authentication context with user info.

Returns:
    IdentityResponse with the identity details.

Raises:
    403: User does not have access to this identity's account.
    404: Identity not found or soft-deleted.

### Parameters

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|identity_id|path|string|true|none|
|account_id|query|any|false|none|
|leadr-api-key|header|any|false|none|
|authorization|header|any|false|none|
|leadr-client-nonce|header|any|false|none|

> Example responses

> 200 Response

```json
{
  "id": "string",
  "account_id": "string",
  "game_id": "string",
  "kind": "string",
  "external_key": "string",
  "display_name": "string",
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z"
}
```

### Responses

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful Response|[IdentityResponse](./schemas.md#identityresponse)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|[HTTPValidationError](./schemas.md#httpvalidationerror)|

!!! success
    This operation does not require authentication

## Update Identity

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

    r = requests.patch('/v1/identities/{identity_id}', headers = headers)

    print(r.json())

    ```

=== "JavaScript"

    ```javascript
    const inputBody = '{
      "display_name": "string",
      "deleted": true
    }';
    const headers = {
      'Content-Type':'application/json',
      'Accept':'application/json',
      'leadr-api-key':'string',
      'authorization':'string',
      'leadr-client-nonce':'string'
    };

    fetch('/v1/identities/{identity_id}',
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
`PATCH /v1/identities/{identity_id}`

Update an identity.

Allows updating display name or soft-deleting the identity.

Args:
    identity_id: Identity identifier to update.
    request: Update details (display_name, deleted).
    service: Injected identity service dependency.
    auth: Authentication context with user info.

Returns:
    IdentityResponse with the updated identity details.

Raises:
    403: User does not have access to this identity's account.
    404: Identity not found.

> Body parameter

```json
{
  "display_name": "string",
  "deleted": true
}
```

### Parameters

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|identity_id|path|string|true|none|
|account_id|query|any|false|none|
|leadr-api-key|header|any|false|none|
|authorization|header|any|false|none|
|leadr-client-nonce|header|any|false|none|
|body|body|[IdentityUpdateRequest](./schemas.md#identityupdaterequest)|true|none|

> Example responses

> 200 Response

```json
{
  "id": "string",
  "account_id": "string",
  "game_id": "string",
  "kind": "string",
  "external_key": "string",
  "display_name": "string",
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z"
}
```

### Responses

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful Response|[IdentityResponse](./schemas.md#identityresponse)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|[HTTPValidationError](./schemas.md#httpvalidationerror)|

!!! success
    This operation does not require authentication
