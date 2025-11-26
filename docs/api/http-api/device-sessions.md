# Device Sessions

## List Sessions

=== "Python"

    ```python
    import requests
    headers = {
      'Accept': 'application/json',
      'leadr-api-key': 'string',
      'authorization': 'string',
      'leadr-client-nonce': 'string'
    }

    r = requests.get('/v1/device-sessions', headers = headers)

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

    fetch('/v1/device-sessions',
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
`GET /v1/device-sessions`

List device sessions for an account with optional filters and pagination.

Returns all non-deleted device sessions for the specified account, with optional
filtering by device.

For regular users, account_id is automatically derived from their API key.
For superadmins, account_id must be explicitly provided as a query parameter.

Pagination:
- Default: 20 items per page, sorted by created_at:desc,id:asc
- Custom sort: Use ?sort=created_at:asc,id:desc
- Valid sort fields: id, created_at, updated_at
- Navigation: Use next_cursor/prev_cursor from response

Example:
    GET /v1/device-sessions?account_id=acc_123&device_id=dev_456&limit=50

Args:
    auth: Authentication context with user info.
    service: Injected device service dependency.
    pagination: Pagination parameters (cursor, limit, sort).
    account_id: Optional account_id query parameter (required for superadmins).
    device_id: Optional device ID to filter by.

Returns:
    PaginatedResponse with device sessions and pagination metadata.

Raises:
    400: Invalid cursor, sort field, or cursor state mismatch.
    400: Superadmin did not provide account_id.
    403: User does not have access to the specified account.

### Parameters

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|account_id|query|any|false|none|
|device_id|query|any|false|Filter by device ID|
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
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful Response|[PaginatedResponse_DeviceSessionResponse_](./schemas.md#paginatedresponse_devicesessionresponse_)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|[HTTPValidationError](./schemas.md#httpvalidationerror)|

!!! success
    This operation does not require authentication

## Get Session

=== "Python"

    ```python
    import requests
    headers = {
      'Accept': 'application/json',
      'leadr-api-key': 'string',
      'authorization': 'string',
      'leadr-client-nonce': 'string'
    }

    r = requests.get('/v1/device-sessions/{session_id}', headers = headers)

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

    fetch('/v1/device-sessions/{session_id}',
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
`GET /v1/device-sessions/{session_id}`

Get a device session by ID.

Args:
    session_id: Session identifier to retrieve.
    service: Injected device service dependency.
    auth: Authentication context with user info.

Returns:
    DeviceSessionResponse with the session details.

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
  "device_id": "string",
  "expires_at": "2019-08-24T14:15:22Z",
  "refresh_expires_at": "2019-08-24T14:15:22Z",
  "ip_address": "string",
  "user_agent": "string",
  "revoked_at": "2019-08-24T14:15:22Z",
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z"
}
```

### Responses

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful Response|[DeviceSessionResponse](./schemas.md#devicesessionresponse)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|[HTTPValidationError](./schemas.md#httpvalidationerror)|

!!! success
    This operation does not require authentication

## Update Session

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

    r = requests.patch('/v1/device-sessions/{session_id}', headers = headers)

    print(r.json())

    ```

=== "JavaScript"

    ```javascript
    const inputBody = '{
      "revoked": true
    }';
    const headers = {
      'Content-Type':'application/json',
      'Accept':'application/json',
      'leadr-api-key':'string',
      'authorization':'string',
      'leadr-client-nonce':'string'
    };

    fetch('/v1/device-sessions/{session_id}',
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
`PATCH /v1/device-sessions/{session_id}`

Update a device session (revoke).

Allows revoking a device session to invalidate authentication.

Args:
    session_id: Session identifier to update.
    request: Update details (revoked status).
    service: Injected device service dependency.
    auth: Authentication context with user info.

Returns:
    DeviceSessionResponse with the updated session details.

Raises:
    403: User does not have access to this session's account.
    404: Session not found.
    400: Invalid request or no revoked field provided.

> Body parameter

```json
{
  "revoked": true
}
```

### Parameters

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|session_id|path|string|true|none|
|account_id|query|any|false|none|
|leadr-api-key|header|any|false|none|
|authorization|header|any|false|none|
|leadr-client-nonce|header|any|false|none|
|body|body|[DeviceSessionUpdateRequest](./schemas.md#devicesessionupdaterequest)|true|none|

> Example responses

> 200 Response

```json
{
  "id": "string",
  "device_id": "string",
  "expires_at": "2019-08-24T14:15:22Z",
  "refresh_expires_at": "2019-08-24T14:15:22Z",
  "ip_address": "string",
  "user_agent": "string",
  "revoked_at": "2019-08-24T14:15:22Z",
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z"
}
```

### Responses

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful Response|[DeviceSessionResponse](./schemas.md#devicesessionresponse)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|[HTTPValidationError](./schemas.md#httpvalidationerror)|

!!! success
    This operation does not require authentication
