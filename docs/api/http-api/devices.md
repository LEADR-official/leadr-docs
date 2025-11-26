# Devices

## List Devices

=== "Python"

    ```python
    import requests
    headers = {
      'Accept': 'application/json',
      'leadr-api-key': 'string',
      'authorization': 'string',
      'leadr-client-nonce': 'string'
    }

    r = requests.get('/v1/devices', headers = headers)

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

    fetch('/v1/devices',
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
`GET /v1/devices`

List devices for an account with optional filters and pagination.

Returns all non-deleted devices for the specified account, with optional
filtering by game or status.

For regular users, account_id is automatically derived from their API key.
For superadmins, account_id must be explicitly provided as a query parameter.

Pagination:
- Default: 20 items per page, sorted by created_at:desc,id:asc
- Custom sort: Use ?sort=name:asc,created_at:desc
- Valid sort fields: id, platform, created_at, updated_at
- Navigation: Use next_cursor/prev_cursor from response

Example:
    GET /v1/devices?account_id=acc_123&game_id=game_456&status=active&limit=50

Args:
    auth: Authentication context with user info.
    service: Injected device service dependency.
    pagination: Pagination parameters (cursor, limit, sort).
    account_id: Optional account_id query parameter (required for superadmins).
    game_id: Optional game ID to filter by.
    device_status: Optional status to filter by (active, banned, suspended).

Returns:
    PaginatedResponse with devices and pagination metadata.

Raises:
    400: Invalid cursor, sort field, or cursor state mismatch.
    400: Superadmin did not provide account_id.
    403: User does not have access to the specified account.

### Parameters

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|account_id|query|any|false|none|
|game_id|query|any|false|Filter by game ID|
|status|query|any|false|Filter by status|
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
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful Response|[PaginatedResponse_DeviceResponse_](./schemas.md#paginatedresponse_deviceresponse_)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|[HTTPValidationError](./schemas.md#httpvalidationerror)|

!!! success
    This operation does not require authentication

## Get Device

=== "Python"

    ```python
    import requests
    headers = {
      'Accept': 'application/json',
      'leadr-api-key': 'string',
      'authorization': 'string',
      'leadr-client-nonce': 'string'
    }

    r = requests.get('/v1/devices/{device_id}', headers = headers)

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

    fetch('/v1/devices/{device_id}',
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
`GET /v1/devices/{device_id}`

Get a device by ID.

Args:
    device_id: Device identifier to retrieve.
    service: Injected device service dependency.
    auth: Authentication context with user info.

Returns:
    DeviceResponse with the device details.

Raises:
    403: User does not have access to this device's account.
    404: Device not found or soft-deleted.

### Parameters

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|device_id|path|string|true|none|
|account_id|query|any|false|none|
|leadr-api-key|header|any|false|none|
|authorization|header|any|false|none|
|leadr-client-nonce|header|any|false|none|

> Example responses

> 200 Response

```json
{
  "id": "string",
  "game_id": "string",
  "client_fingerprint": "string",
  "account_id": "string",
  "platform": "string",
  "status": "string",
  "first_seen_at": "2019-08-24T14:15:22Z",
  "last_seen_at": "2019-08-24T14:15:22Z",
  "metadata": {},
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z"
}
```

### Responses

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful Response|[DeviceResponse](./schemas.md#deviceresponse)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|[HTTPValidationError](./schemas.md#httpvalidationerror)|

!!! success
    This operation does not require authentication

## Update Device

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

    r = requests.patch('/v1/devices/{device_id}', headers = headers)

    print(r.json())

    ```

=== "JavaScript"

    ```javascript
    const inputBody = '{
      "status": "string"
    }';
    const headers = {
      'Content-Type':'application/json',
      'Accept':'application/json',
      'leadr-api-key':'string',
      'authorization':'string',
      'leadr-client-nonce':'string'
    };

    fetch('/v1/devices/{device_id}',
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
`PATCH /v1/devices/{device_id}`

Update a device (change status).

Allows changing device status to ban, suspend, or activate devices.

Args:
    device_id: Device identifier to update.
    request: Update details (status).
    service: Injected device service dependency.
    auth: Authentication context with user info.

Returns:
    DeviceResponse with the updated device details.

Raises:
    403: User does not have access to this device's account.
    404: Device not found.
    400: Invalid status value.

> Body parameter

```json
{
  "status": "string"
}
```

### Parameters

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|device_id|path|string|true|none|
|account_id|query|any|false|none|
|leadr-api-key|header|any|false|none|
|authorization|header|any|false|none|
|leadr-client-nonce|header|any|false|none|
|body|body|[DeviceUpdateRequest](./schemas.md#deviceupdaterequest)|true|none|

> Example responses

> 200 Response

```json
{
  "id": "string",
  "game_id": "string",
  "client_fingerprint": "string",
  "account_id": "string",
  "platform": "string",
  "status": "string",
  "first_seen_at": "2019-08-24T14:15:22Z",
  "last_seen_at": "2019-08-24T14:15:22Z",
  "metadata": {},
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z"
}
```

### Responses

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful Response|[DeviceResponse](./schemas.md#deviceresponse)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|[HTTPValidationError](./schemas.md#httpvalidationerror)|

!!! success
    This operation does not require authentication
