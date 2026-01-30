# Scores

## Get Score

=== "Python"

    ```python
    import requests
    headers = {
      'Accept': 'application/json',
      'leadr-api-key': 'string',
      'authorization': 'string',
      'leadr-client-nonce': 'string'
    }

    r = requests.get('/v1/scores/{score_id}', headers = headers)

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

    fetch('/v1/scores/{score_id}',
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
`GET /v1/scores/{score_id}`

Get a score by ID.

Returns the score with its computed rank based on the board's sort direction.
The rank represents the score's position in the leaderboard (1 = first place).

Args:
    score_id: Score identifier to retrieve.
    service: Injected score service dependency.
    auth: Authentication context with user info.

Returns:
    ScoreResponse with the score details including rank.

Raises:
    403: User does not have access to this score's account.
    404: Score not found or soft-deleted.

### Parameters

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|score_id|path|string|true|none|
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
  "player_name": "string",
  "value": 0,
  "value_display": "string",
  "timezone": "string",
  "country": "string",
  "city": "string",
  "metadata": {},
  "rank": 0,
  "is_placeholder": false,
  "is_test": false,
  "status": "provisional",
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z"
}
```

### Responses

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful Response|[ScoreResponse](./schemas.md#scoreresponse)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|[HTTPValidationError](./schemas.md#httpvalidationerror)|

!!! success
    This operation does not require authentication

## List Scores Admin

=== "Python"

    ```python
    import requests
    headers = {
      'Accept': 'application/json',
      'leadr-api-key': 'string',
      'authorization': 'string',
      'leadr-client-nonce': 'string'
    }

    r = requests.get('/v1/scores', headers = headers)

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

    fetch('/v1/scores',
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
`GET /v1/scores`

List scores for an account with optional filters and pagination.

Returns paginated scores for the specified account, with optional
filtering by board, game, or identity. Supports cursor-based pagination
with bidirectional navigation and custom sorting.

For regular admin users, account_id is automatically derived from their API key.
For superadmins, account_id must be explicitly provided as a query parameter.

Pagination:
- Default: 20 items per page, sorted by created_at:desc,id:asc
- Custom sort: Use ?sort=value:desc,created_at:asc
- Valid sort fields: id, value, player_name, created_at, updated_at
- Navigation: Use next_cursor/prev_cursor from response

Around Score:
- Use around_score_id to get scores centered around a specific score
- Use around_score_value to get scores centered around a hypothetical value
  (returns a placeholder score with is_placeholder=True)
- Both require board_id to be specified
- Mutually exclusive with cursor pagination and each other
- Returns a window of scores with the target in the middle
- Respects limit (e.g., limit=5 returns 2 above + target + 2 below)

Example:
    GET /v1/scores?board_id=brd_123&limit=50&sort=value:desc,created_at:asc
    GET /v1/scores?board_id=brd_123&around_score_id=scr_456&limit=11
    GET /v1/scores?board_id=brd_123&around_score_value=1500&limit=11

Args:
    auth: Authentication context with user info.
    service: Injected score service dependency.
    pagination: Pagination parameters (cursor, limit, sort).
    account_id: Optional account_id query parameter (required for superadmins).
    board_id: Optional board ID to filter by.
    game_id: Optional game ID to filter by.
    identity_id: Optional identity ID to filter by.
    around_score_id: Optional score ID to center results around.
    around_score_value: Optional value to center results around (with placeholder).

Returns:
    PaginatedResponse with scores and pagination metadata.

Raises:
    400: Invalid cursor, sort field, cursor state mismatch, or around validation.
    400: Superadmin did not provide account_id.
    403: User does not have access to the specified account.
    404: around_score_id score not found.

### Parameters

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|account_id|query|any|false|none|
|board_id|query|any|false|none|
|game_id|query|any|false|none|
|identity_id|query|any|false|none|
|is_test|query|[IsTestFilter](./schemas.md#istestfilter)|false|Filter for test scores. 'false' (default) returns production only, 'true' returns test only, 'all' returns both test and production|
|around_score_id|query|any|false|Center results around this score ID|
|around_score_value|query|any|false|Center results around this score value (returns placeholder)|
|cursor|query|any|false|Pagination cursor for navigating results|
|limit|query|integer|false|Number of items per page (1-100)|
|sort|query|any|false|Sort specification (e.g., 'value:desc,created_at:asc')|
|leadr-api-key|header|any|false|none|
|authorization|header|any|false|none|
|leadr-client-nonce|header|any|false|none|

#### Enumerated Values

|Parameter|Value|
|---|---|
|is_test|true|
|is_test|false|
|is_test|all|

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
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful Response|[PaginatedResponse_ScoreResponse_](./schemas.md#paginatedresponse_scoreresponse_)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|[HTTPValidationError](./schemas.md#httpvalidationerror)|

!!! success
    This operation does not require authentication

## List Boards Client

=== "Python"

    ```python
    import requests
    headers = {
      'Accept': 'application/json',
      'leadr-api-key': 'string',
      'authorization': 'string',
      'leadr-client-nonce': 'string'
    }

    r = requests.get('/v1/client/boards', headers = headers)

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

    fetch('/v1/client/boards',
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
`GET /v1/client/boards`

List boards (Client API).

Account ID and game ID are automatically derived from the authenticated client session.
Clients can optionally filter by various criteria to find specific boards.

Filtering:
- Use ?slug={slug} to find a specific board within the authenticated game
- Use ?code={code} to filter boards by short code
- Use ?is_published=true/false to filter by published status
- Use ?starts_before=<datetime>&starts_after=<datetime> for start date range
- Use ?ends_before=<datetime>&ends_after=<datetime> for end date range

Pagination:
- Default: 20 items per page, sorted by created_at:desc,id:asc
- Custom sort: Use ?sort=name:asc,created_at:desc
- Valid sort fields: id, name, slug, short_code, created_at, updated_at
- Navigation: Use next_cursor/prev_cursor from response

Example:
    GET /v1/client/boards?code=WEEKLY-CHALLENGE&limit=50
    GET /v1/client/boards?slug=weekly-challenge
    GET /v1/client/boards?is_published=true
    GET /v1/client/boards?starts_after=2025-01-01T00:00:00Z

Args:
    auth: Client authentication context with device info.
    service: Injected board service dependency.
    game_service: Injected game service dependency.
    pagination: Pagination parameters (cursor, limit, sort).
    code: Optional short code to filter boards by.
    slug: Optional board slug to filter by specific board.
    is_published: Optional filter for published status.
    starts_before: Optional filter for boards starting before this time.
    starts_after: Optional filter for boards starting after this time.
    ends_before: Optional filter for boards ending before this time.
    ends_after: Optional filter for boards ending after this time.

Returns:
    PaginatedResponse with boards and pagination metadata.

Raises:
    400: Invalid cursor, sort field, or cursor state mismatch.

### Parameters

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|code|query|any|false|Filter by short code|
|slug|query|any|false|Filter by board slug|
|is_published|query|any|false|Filter by published status|
|starts_before|query|any|false|Filter boards starting before this time (ISO 8601)|
|starts_after|query|any|false|Filter boards starting after this time (ISO 8601)|
|ends_before|query|any|false|Filter boards ending before this time (ISO 8601)|
|ends_after|query|any|false|Filter boards ending after this time (ISO 8601)|
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
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful Response|[PaginatedResponse_BoardResponse_](./schemas.md#paginatedresponse_boardresponse_)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|[HTTPValidationError](./schemas.md#httpvalidationerror)|

!!! success
    This operation does not require authentication

## Create Score Client

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

    r = requests.post('/v1/client/scores', headers = headers)

    print(r.json())

    ```

=== "JavaScript"

    ```javascript
    const inputBody = '{
      "board_id": "string",
      "player_name": "string",
      "value": 0,
      "value_display": "string",
      "metadata": {}
    }';
    const headers = {
      'Content-Type':'application/json',
      'Accept':'application/json',
      'leadr-api-key':'string',
      'authorization':'string',
      'leadr-client-nonce':'string'
    };

    fetch('/v1/client/scores',
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
`POST /v1/client/scores`

Create a new score (Client API).

Creates a new score submission for a board. All IDs (account_id, game_id, identity_id)
are automatically derived from the authenticated session.

Args:
    score_request: Score creation details including board_id, player_name, and value.
    request: FastAPI request object for accessing geo data.
    service: Injected score service dependency.
    board_service: Injected board service for board lookup.
    background_tasks: FastAPI background tasks for async metadata updates.
    auth: Client authentication context with device and identity info.
    pre_create_hook: Hook called before score creation (for quota checks).
    post_create_hook: Hook called after successful score creation.

Returns:
    ScoreClientResponse with the created score (excludes device_id).

Raises:
    404: Board not found.
    400: Validation failed (board doesn't belong to account, or game doesn't
        match board's game).
    403: Score rejected by anti-cheat (rate limit exceeded).

> Body parameter

```json
{
  "board_id": "string",
  "player_name": "string",
  "value": 0,
  "value_display": "string",
  "metadata": {}
}
```

### Parameters

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|account_id|query|any|false|none|
|leadr-api-key|header|any|false|none|
|authorization|header|any|false|none|
|leadr-client-nonce|header|any|false|none|
|body|body|[ScoreClientCreateRequest](./schemas.md#scoreclientcreaterequest)|true|none|

> Example responses

> 201 Response

```json
{
  "id": "string",
  "account_id": "string",
  "game_id": "string",
  "board_id": "string",
  "identity_id": "string",
  "player_name": "string",
  "value": 0,
  "value_display": "string",
  "metadata": {},
  "rank": 0,
  "is_placeholder": false,
  "is_test": false,
  "status": "provisional",
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z"
}
```

### Responses

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Successful Response|[ScoreClientResponse](./schemas.md#scoreclientresponse)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|[HTTPValidationError](./schemas.md#httpvalidationerror)|

!!! success
    This operation does not require authentication

## List Scores Client

=== "Python"

    ```python
    import requests
    headers = {
      'Accept': 'application/json',
      'leadr-api-key': 'string',
      'authorization': 'string',
      'leadr-client-nonce': 'string'
    }

    r = requests.get('/v1/client/scores', headers = headers)

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

    fetch('/v1/client/scores',
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
`GET /v1/client/scores`

List scores for an account with optional filters and pagination.

Returns paginated scores for the specified account, with optional
filtering by board and/or identity. Supports cursor-based pagination
with bidirectional navigation and custom sorting.

Pagination:
- Default: 20 items per page, sorted by created_at:desc,id:asc
- Custom sort: Use ?sort=value:desc,created_at:asc
- Valid sort fields: id, value, player_name, created_at, updated_at
- Navigation: Use next_cursor/prev_cursor from response

Around Score:
- Use around_score_id to get scores centered around a specific score
- Use around_score_value to get scores centered around a hypothetical value
  (returns a placeholder score with is_placeholder=True)
- Both require board_id to be specified
- Mutually exclusive with cursor pagination and each other
- Returns a window of scores with the target in the middle
- Respects limit (e.g., limit=5 returns 2 above + target + 2 below)

Example:
    GET /client/scores?board_id=brd_123&limit=50&sort=value:desc,created_at:asc
    GET /client/scores?board_id=brd_123&around_score_id=scr_456&limit=11
    GET /client/scores?board_id=brd_123&around_score_value=1500&limit=11

Args:
    auth: Authentication context with user info.
    service: Injected score service dependency.
    pagination: Pagination parameters (cursor, limit, sort).
    board_id: Optional board ID to filter by.
    identity_id: Optional identity ID to filter by (e.g., to get "my scores").
    around_score_id: Optional score ID to center results around.
    around_score_value: Optional value to center results around (with placeholder).

Returns:
    PaginatedResponse with scores and pagination metadata.

Raises:
    400: Invalid cursor, sort field, cursor state mismatch, or around validation.
    403: User does not have access to the specified account.
    404: around_score_id score not found.

### Parameters

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|board_id|query|any|false|none|
|identity_id|query|any|false|none|
|around_score_id|query|any|false|Center results around this score ID|
|around_score_value|query|any|false|Center results around this score value (returns placeholder)|
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
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful Response|[PaginatedResponse_ScoreClientResponse_](./schemas.md#paginatedresponse_scoreclientresponse_)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|[HTTPValidationError](./schemas.md#httpvalidationerror)|

!!! success
    This operation does not require authentication

## Get Score Client

=== "Python"

    ```python
    import requests
    headers = {
      'Accept': 'application/json',
      'leadr-api-key': 'string',
      'authorization': 'string',
      'leadr-client-nonce': 'string'
    }

    r = requests.get('/v1/client/scores/{score_id}', headers = headers)

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

    fetch('/v1/client/scores/{score_id}',
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
`GET /v1/client/scores/{score_id}`

Get a score by ID (Client API).

Returns the score with its computed rank based on the board's sort direction.
The rank represents the score's position in the leaderboard (1 = first place).

Clients can only access scores from boards belonging to the same game
as their authenticated device.

Args:
    score_id: Score identifier to retrieve.
    service: Injected score service dependency.
    auth: Client authentication context with device info.

Returns:
    ScoreClientResponse with the score details including rank.

Raises:
    403: Client does not have access to this score's game.
    404: Score not found or soft-deleted.

### Parameters

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|score_id|path|string|true|none|
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
  "player_name": "string",
  "value": 0,
  "value_display": "string",
  "metadata": {},
  "rank": 0,
  "is_placeholder": false,
  "is_test": false,
  "status": "provisional",
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z"
}
```

### Responses

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful Response|[ScoreClientResponse](./schemas.md#scoreclientresponse)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|[HTTPValidationError](./schemas.md#httpvalidationerror)|

!!! success
    This operation does not require authentication
