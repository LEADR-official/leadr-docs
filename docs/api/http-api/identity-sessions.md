# Identity Sessions

## List Identity Sessions

=== "Python"

    ```python
    import requests
    headers = {
      'Accept': 'application/json',
      'leadr-api-key': 'string',
      'authorization': 'string',
      'leadr-client-nonce': 'string'
    }

    r = requests.get('/v1/identity-sessions', headers = headers)

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

    fetch('/v1/identity-sessions',
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
`GET /v1/identity-sessions`

List identity sessions with optional filters and pagination.

Returns all non-deleted sessions, with optional filtering by account or identity.

For regular users, account_id is automatically derived from their API key.
For superadmins, account_id is optional - if omitted, returns sessions from all accounts.

Pagination:
- Default: 20 items per page, sorted by created_at:desc,id:asc
- Custom sort: Use ?sort=created_at:desc
- Valid sort fields: id, created_at, updated_at
- Navigation: Use next_cursor/prev_cursor from response

Example:
    GET /v1/identity-sessions?account_id=acc_123&identity_id=ide_456&limit=50

Args:
    auth: Authentication context with user info.
    service: Injected identity service dependency.
    pagination: Pagination parameters (cursor, limit, sort).
    account_id: Optional account_id query parameter (superadmins can omit to see all).
    identity_id: Optional identity ID to filter by.

Returns:
    PaginatedResponse with sessions and pagination metadata.

Raises:
    400: Invalid cursor, sort field, or cursor state mismatch.
    403: User does not have access to the specified account.

### Parameters

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|account_id|query|any|false|none|
|identity_id|query|any|false|Filter by identity ID|
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
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful Response|[PaginatedResponse_IdentitySessionResponse_](./schemas.md#paginatedresponse_identitysessionresponse_)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|[HTTPValidationError](./schemas.md#httpvalidationerror)|

!!! success
    This operation does not require authentication

## Get Identity Session

=== "Python"

    ```python
    import requests
    headers = {
      'Accept': 'application/json',
      'leadr-api-key': 'string',
      'authorization': 'string',
      'leadr-client-nonce': 'string'
    }

    r = requests.get('/v1/identity-sessions/{session_id}', headers = headers)

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

    fetch('/v1/identity-sessions/{session_id}',
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
`GET /v1/identity-sessions/{session_id}`

Get an identity session by ID.

Args:
    session_id: Session identifier to retrieve.
    service: Injected identity service dependency.
    auth: Authentication context with user info.

Returns:
    IdentitySessionResponse with the session details.

Raises:
    403: User does not have access to this session's account.
    404: Session not found or soft-deleted.

### Parameters

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|session_id|path|string|true|none|
|account_id|query|any|false|none|
|leadr-api-key|header|any|false|none|
|authorization|header|any|false|none|
|leadr-client-nonce|header|any|false|none|

> Example responses

> 200 Response

```json
{
  "id": "string",
  "identity_id": "string",
  "expires_at": "2019-08-24T14:15:22Z",
  "refresh_expires_at": "2019-08-24T14:15:22Z",
  "revoked_at": "2019-08-24T14:15:22Z",
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z"
}
```

### Responses

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful Response|[IdentitySessionResponse](./schemas.md#identitysessionresponse)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|[HTTPValidationError](./schemas.md#httpvalidationerror)|

!!! success
    This operation does not require authentication

## Revoke Identity Session

=== "Python"

    ```python
    import requests
    headers = {
      'Accept': 'application/json',
      'leadr-api-key': 'string',
      'authorization': 'string',
      'leadr-client-nonce': 'string'
    }

    r = requests.patch('/v1/identity-sessions/{session_id}', headers = headers)

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

    fetch('/v1/identity-sessions/{session_id}',
    {
      method: 'PATCH',

      headers: headers
    })
    .then(function(res) {
        return res.json();
    }).then(function(body) {
        console.log(body);
    });

    ```
`PATCH /v1/identity-sessions/{session_id}`

Revoke an identity session.

Marks the session as revoked, preventing further use.

Args:
    session_id: Session identifier to revoke.
    service: Injected identity service dependency.
    auth: Authentication context with user info.

Returns:
    IdentitySessionResponse with the revoked session details.

Raises:
    403: User does not have access to this session's account.
    404: Session not found.

### Parameters

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|session_id|path|string|true|none|
|account_id|query|any|false|none|
|leadr-api-key|header|any|false|none|
|authorization|header|any|false|none|
|leadr-client-nonce|header|any|false|none|

> Example responses

> 200 Response

```json
{
  "id": "string",
  "identity_id": "string",
  "expires_at": "2019-08-24T14:15:22Z",
  "refresh_expires_at": "2019-08-24T14:15:22Z",
  "revoked_at": "2019-08-24T14:15:22Z",
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z"
}
```

### Responses

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful Response|[IdentitySessionResponse](./schemas.md#identitysessionresponse)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|[HTTPValidationError](./schemas.md#httpvalidationerror)|

!!! success
    This operation does not require authentication
