# Score Events

## Create Score Event

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

    r = requests.post('/v1/score-events', headers = headers)

    print(r.json())

    ```

=== "JavaScript"

    ```javascript
    const inputBody = '{
      "board_id": "string",
      "identity_id": "string",
      "value": 0,
      "player_name": "string",
      "is_test": false,
      "timezone": "string",
      "country": "string",
      "city": "string"
    }';
    const headers = {
      'Content-Type':'application/json',
      'Accept':'application/json',
      'leadr-api-key':'string',
      'authorization':'string',
      'leadr-client-nonce':'string'
    };

    fetch('/v1/score-events',
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
`POST /v1/score-events`

Create a score event (Admin API).

Creates a score event using the same processing as client submissions:
- Runs anti-cheat checks
- Updates rankings (BoardState/RunEntry)
- Validates board type and payload

This endpoint is for admin testing, data seeding, and demo purposes.

Args:
    request: Score event creation request
    auth: Admin authentication context
    score_service: Score service for submission
    board_service: Board service for validation

Returns:
    Created score event

Raises:
    404: Board not found
    403: Non-superadmin accessing another account's board
    400: Validation error (wrong board type, etc.)

> Body parameter

```json
{
  "board_id": "string",
  "identity_id": "string",
  "value": 0,
  "player_name": "string",
  "is_test": false,
  "timezone": "string",
  "country": "string",
  "city": "string"
}
```

### Parameters

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|account_id|query|any|false|none|
|leadr-api-key|header|any|false|none|
|authorization|header|any|false|none|
|leadr-client-nonce|header|any|false|none|
|body|body|[ScoreEventCreateRequest](./schemas.md#scoreeventcreaterequest)|true|none|

> Example responses

> 201 Response

```json
{
  "id": "string",
  "account_id": "string",
  "game_id": "string",
  "board_id": "string",
  "identity_id": "string",
  "event_payload": {},
  "is_test": true,
  "timezone": "string",
  "country": "string",
  "city": "string",
  "created_at": "2019-08-24T14:15:22Z"
}
```

### Responses

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Successful Response|[ScoreEventResponse](./schemas.md#scoreeventresponse)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|[HTTPValidationError](./schemas.md#httpvalidationerror)|

!!! success
    This operation does not require authentication

## List Score Events

=== "Python"

    ```python
    import requests
    headers = {
      'Accept': 'application/json',
      'leadr-api-key': 'string',
      'authorization': 'string',
      'leadr-client-nonce': 'string'
    }

    r = requests.get('/v1/score-events', headers = headers)

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

    fetch('/v1/score-events',
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
`GET /v1/score-events`

List score events (Admin API).

Returns a paginated list of score events. Score events are immutable
facts about score submissions and cannot be updated or deleted.

For regular admins: account_id defaults to their account.
For superadmins: can view events across all accounts.

Args:
    auth: Admin authentication context.
    service: Injected score event service dependency.
    pagination: Pagination parameters (cursor, limit, sort).
    account_id: Optional filter by account ID.
    board_id: Optional filter by board ID.
    identity_id: Optional filter by identity ID.
    is_test: Optional filter for test events.

Returns:
    Paginated list of score events.

Raises:
    400: Invalid pagination cursor.

### Parameters

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|account_id|query|any|false|none|
|board_id|query|any|false|Filter by board ID|
|identity_id|query|any|false|Filter by identity ID|
|is_test|query|any|false|Filter by test mode|
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
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful Response|[PaginatedResponse_ScoreEventResponse_](./schemas.md#paginatedresponse_scoreeventresponse_)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|[HTTPValidationError](./schemas.md#httpvalidationerror)|

!!! success
    This operation does not require authentication

## Get Score Event

=== "Python"

    ```python
    import requests
    headers = {
      'Accept': 'application/json',
      'leadr-api-key': 'string',
      'authorization': 'string',
      'leadr-client-nonce': 'string'
    }

    r = requests.get('/v1/score-events/{event_id}', headers = headers)

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

    fetch('/v1/score-events/{event_id}',
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
`GET /v1/score-events/{event_id}`

Get a single score event by ID (Admin API).

Args:
    event_id: Score event ID.
    auth: Admin authentication context.
    service: Injected score event service dependency.

Returns:
    Score event details.

Raises:
    404: Score event not found.
    403: Non-superadmin trying to access another account's event.

### Parameters

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|event_id|path|string|true|none|
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
  "board_id": "string",
  "identity_id": "string",
  "event_payload": {},
  "is_test": true,
  "timezone": "string",
  "country": "string",
  "city": "string",
  "created_at": "2019-08-24T14:15:22Z"
}
```

### Responses

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful Response|[ScoreEventResponse](./schemas.md#scoreeventresponse)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|[HTTPValidationError](./schemas.md#httpvalidationerror)|

!!! success
    This operation does not require authentication
