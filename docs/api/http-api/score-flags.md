# Score Flags

## List Score Flags

=== "Python"

    ```python
    import requests
    headers = {
      'Accept': 'application/json',
      'leadr-api-key': 'string',
      'authorization': 'string',
      'leadr-client-nonce': 'string'
    }

    r = requests.get('/v1/score-flags', headers = headers)

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

    fetch('/v1/score-flags',
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
`GET /v1/score-flags`

List score flags for an account with optional filters and pagination.

Returns paginated flags for the specified account, with optional
filtering by board, game, status, or flag type. Supports cursor-based
pagination with bidirectional navigation and custom sorting.

For regular users, account_id is automatically derived from their API key.
For superadmins, account_id is optional - if omitted, returns flags from all accounts.

Args:
    auth: Authentication context with user info.
    service: Injected score flag service dependency.
    pagination: Pagination parameters (cursor, limit, sort).
    account_id: Optional account_id query parameter (superadmins can omit to see all).
    board_id: Optional board ID to filter by.
    game_id: Optional game ID to filter by.
    status: Optional status to filter by (PENDING, CONFIRMED_CHEAT, etc.).
    flag_type: Optional flag type to filter by (VELOCITY, DUPLICATE, etc.).

Returns:
    PaginatedResponse containing ScoreFlagResponse objects matching the filter criteria.

Raises:
    400: Invalid cursor or sort field.
    403: User does not have access to the specified account.

### Parameters

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|account_id|query|any|false|none|
|board_id|query|any|false|none|
|game_id|query|any|false|none|
|status|query|any|false|none|
|flag_type|query|any|false|none|
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
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful Response|[PaginatedResponse_ScoreFlagResponse_](./schemas.md#paginatedresponse_scoreflagresponse_)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|[HTTPValidationError](./schemas.md#httpvalidationerror)|

!!! success
    This operation does not require authentication

## Get Score Flag

=== "Python"

    ```python
    import requests
    headers = {
      'Accept': 'application/json',
      'leadr-api-key': 'string',
      'authorization': 'string',
      'leadr-client-nonce': 'string'
    }

    r = requests.get('/v1/score-flags/{flag_id}', headers = headers)

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

    fetch('/v1/score-flags/{flag_id}',
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
`GET /v1/score-flags/{flag_id}`

Get a score flag by ID.

Args:
    flag_id: Flag identifier to retrieve.
    service: Injected score flag service dependency.
    auth: Authentication context with user info.

Returns:
    ScoreFlagResponse with the flag details.

Raises:
    403: User does not have access to this flag's account.
    404: Flag not found or soft-deleted.

### Parameters

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|flag_id|path|string|true|none|
|account_id|query|any|false|none|
|leadr-api-key|header|any|false|none|
|authorization|header|any|false|none|
|leadr-client-nonce|header|any|false|none|

> Example responses

> 200 Response

```json
{
  "id": "string",
  "score_id": "string",
  "flag_type": "string",
  "confidence": "string",
  "metadata": {},
  "status": "string",
  "reviewed_at": "2019-08-24T14:15:22Z",
  "reviewer_id": "string",
  "reviewer_decision": "string",
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z"
}
```

### Responses

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful Response|[ScoreFlagResponse](./schemas.md#scoreflagresponse)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|[HTTPValidationError](./schemas.md#httpvalidationerror)|

!!! success
    This operation does not require authentication

## Update Score Flag

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

    r = requests.patch('/v1/score-flags/{flag_id}', headers = headers)

    print(r.json())

    ```

=== "JavaScript"

    ```javascript
    const inputBody = '{
      "status": "string",
      "reviewer_decision": "string",
      "deleted": true
    }';
    const headers = {
      'Content-Type':'application/json',
      'Accept':'application/json',
      'leadr-api-key':'string',
      'authorization':'string',
      'leadr-client-nonce':'string'
    };

    fetch('/v1/score-flags/{flag_id}',
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
`PATCH /v1/score-flags/{flag_id}`

Update a score flag (review or soft-delete).

Allows reviewing a flag (updating status and reviewer decision) or
soft-deleting the flag.

Args:
    flag_id: Flag identifier to update.
    request: Update details (status, reviewer_decision, or deleted flag).
    service: Injected score flag service dependency.
    auth: Authentication context with user info.

Returns:
    ScoreFlagResponse with the updated flag details.

Raises:
    403: User does not have access to this flag's account.
    404: Flag not found.
    400: Invalid update request.

> Body parameter

```json
{
  "status": "string",
  "reviewer_decision": "string",
  "deleted": true
}
```

### Parameters

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|flag_id|path|string|true|none|
|account_id|query|any|false|none|
|leadr-api-key|header|any|false|none|
|authorization|header|any|false|none|
|leadr-client-nonce|header|any|false|none|
|body|body|[ScoreFlagUpdateRequest](./schemas.md#scoreflagupdaterequest)|true|none|

> Example responses

> 200 Response

```json
{
  "id": "string",
  "score_id": "string",
  "flag_type": "string",
  "confidence": "string",
  "metadata": {},
  "status": "string",
  "reviewed_at": "2019-08-24T14:15:22Z",
  "reviewer_id": "string",
  "reviewer_decision": "string",
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z"
}
```

### Responses

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful Response|[ScoreFlagResponse](./schemas.md#scoreflagresponse)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|[HTTPValidationError](./schemas.md#httpvalidationerror)|

!!! success
    This operation does not require authentication
