# Scores

## Create Score Admin

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

    r = requests.post('/v1/scores', headers = headers)

    print(r.json())

    ```

=== "JavaScript"

    ```javascript
    const inputBody = '{
      "board_id": "string",
      "player_name": "string",
      "value": 0,
      "value_display": "string",
      "metadata": {},
      "account_id": "string",
      "game_id": "string",
      "device_id": "string",
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

    fetch('/v1/scores',
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
`POST /v1/scores`

Create a new score (Admin API).

Creates a new score submission for a board. Performs three-level validation:
board exists, board belongs to the specified account, and game matches
the board's game.

For regular admins: account_id is derived from auth, must provide game_id and device_id.
For superadmins: can provide account_id to create scores for any account.

Args:
    score_request: Score creation details including board_id, player_name, value,
                  and optionally account_id (superadmin only), game_id, device_id.
    request: FastAPI request object for accessing geo data.
    service: Injected score service dependency.
    background_tasks: FastAPI background tasks for async metadata updates.
    auth: Admin authentication context.

Returns:
    ScoreResponse with the created score including auto-generated ID and timestamps.

Raises:
    403: Non-superadmin tries to specify account_id, or access denied.
    400: Missing required fields (game_id or device_id).
    404: Account, game, board, or device not found.
    400: Validation failed (board doesn't belong to account, or game doesn't
        match board's game).

> Body parameter

```json
{
  "board_id": "string",
  "player_name": "string",
  "value": 0,
  "value_display": "string",
  "metadata": {},
  "account_id": "string",
  "game_id": "string",
  "device_id": "string",
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
|body|body|[ScoreCreateRequest](./schemas.md#scorecreaterequest)|true|none|

> Example responses

> 201 Response

```json
{
  "id": "string",
  "account_id": "string",
  "game_id": "string",
  "board_id": "string",
  "device_id": "string",
  "player_name": "string",
  "value": 0,
  "value_display": "string",
  "timezone": "string",
  "country": "string",
  "city": "string",
  "metadata": {},
  "rank": 0,
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z"
}
```

### Responses

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Successful Response|[ScoreResponse](./schemas.md#scoreresponse)|
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
filtering by board, game, or device. Supports cursor-based pagination
with bidirectional navigation and custom sorting.

For regular admin users, account_id is automatically derived from their API key.
For superadmins, account_id must be explicitly provided as a query parameter.

Pagination:
- Default: 20 items per page, sorted by created_at:desc,id:asc
- Custom sort: Use ?sort=value:desc,created_at:asc
- Valid sort fields: id, value, player_name, filter_timezone, filter_country,
  filter_city, created_at, updated_at
- Navigation: Use next_cursor/prev_cursor from response

Around Score:
- Use around_score_id to get scores centered around a specific score
- Requires board_id to be specified
- Mutually exclusive with cursor pagination
- Returns a window of scores with the target in the middle
- Respects limit (e.g., limit=5 returns 2 above + target + 2 below)

Example:
    GET /v1/scores?board_id=brd_123&limit=50&sort=value:desc,created_at:asc
    GET /v1/scores?board_id=brd_123&around_score_id=scr_456&limit=11

Args:
    auth: Authentication context with user info.
    service: Injected score service dependency.
    pagination: Pagination parameters (cursor, limit, sort).
    account_id: Optional account_id query parameter (required for superadmins).
    board_id: Optional board ID to filter by.
    game_id: Optional game ID to filter by.
    device_id: Optional device ID to filter by.
    around_score_id: Optional score ID to center results around.

Returns:
    PaginatedResponse with scores and pagination metadata.

Raises:
    400: Invalid cursor, sort field, cursor state mismatch, or around_score_id validation.
    400: Superadmin did not provide account_id.
    403: User does not have access to the specified account.
    404: around_score_id score not found.

### Parameters

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|account_id|query|any|false|none|
|board_id|query|any|false|none|
|game_id|query|any|false|none|
|device_id|query|any|false|none|
|around_score_id|query|any|false|Center results around this score ID|
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
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful Response|[PaginatedResponse_ScoreResponse_](./schemas.md#paginatedresponse_scoreresponse_)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|[HTTPValidationError](./schemas.md#httpvalidationerror)|

!!! success
    This operation does not require authentication

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
  "device_id": "string",
  "player_name": "string",
  "value": 0,
  "value_display": "string",
  "timezone": "string",
  "country": "string",
  "city": "string",
  "metadata": {},
  "rank": 0,
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

## Update Score

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

    r = requests.patch('/v1/scores/{score_id}', headers = headers)

    print(r.json())

    ```

=== "JavaScript"

    ```javascript
    const inputBody = '{
      "player_name": "string",
      "value": 0,
      "value_display": "string",
      "timezone": "string",
      "country": "string",
      "city": "string",
      "metadata": {},
      "deleted": true
    }';
    const headers = {
      'Content-Type':'application/json',
      'Accept':'application/json',
      'leadr-api-key':'string',
      'authorization':'string',
      'leadr-client-nonce':'string'
    };

    fetch('/v1/scores/{score_id}',
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
`PATCH /v1/scores/{score_id}`

Update a score.

Supports partial updates of score fields. Any field not provided will
remain unchanged. Set deleted: true to soft delete the score.

Args:
    score_id: Score identifier to update.
    request: Score update details with optional fields to modify.
    service: Injected score service dependency.
    auth: Authentication context with user info.

Returns:
    ScoreResponse with the updated score details.

Raises:
    403: User does not have access to this score's account.
    404: Score not found or already soft-deleted.

> Body parameter

```json
{
  "player_name": "string",
  "value": 0,
  "value_display": "string",
  "timezone": "string",
  "country": "string",
  "city": "string",
  "metadata": {},
  "deleted": true
}
```

### Parameters

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|score_id|path|string|true|none|
|account_id|query|any|false|none|
|leadr-api-key|header|any|false|none|
|authorization|header|any|false|none|
|leadr-client-nonce|header|any|false|none|
|body|body|[ScoreUpdateRequest](./schemas.md#scoreupdaterequest)|true|none|

> Example responses

> 200 Response

```json
{
  "id": "string",
  "account_id": "string",
  "game_id": "string",
  "board_id": "string",
  "device_id": "string",
  "player_name": "string",
  "value": 0,
  "value_display": "string",
  "timezone": "string",
  "country": "string",
  "city": "string",
  "metadata": {},
  "rank": 0,
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

Account ID is automatically derived from the authenticated device's account.
Clients can optionally filter by various criteria to find specific boards.

Filtering:
- Use ?game_id={id} or ?game_slug={slug} to filter boards by game
- Use ?game_slug={game_slug}&slug={slug} to find a specific board within a game
- Use ?code={code} to filter boards by short code
- Use ?is_published=true/false to filter by published status
- Use ?starts_before=<datetime>&starts_after=<datetime> for start date range
- Use ?ends_before=<datetime>&ends_after=<datetime> for end date range
- Note: board slug filter requires game_slug parameter

Pagination:
- Default: 20 items per page, sorted by created_at:desc,id:asc
- Custom sort: Use ?sort=name:asc,created_at:desc
- Valid sort fields: id, name, slug, short_code, created_at, updated_at
- Navigation: Use next_cursor/prev_cursor from response

Example:
    GET /v1/client/boards?code=WEEKLY-CHALLENGE&limit=50
    GET /v1/client/boards?game_slug=my-game&is_published=true
    GET /v1/client/boards?game_slug=my-game&slug=weekly-challenge
    GET /v1/client/boards?starts_after=2025-01-01T00:00:00Z

Args:
    auth: Client authentication context with device info.
    service: Injected board service dependency.
    game_service: Injected game service dependency.
    pagination: Pagination parameters (cursor, limit, sort).
    game_id: Optional game ID to filter boards by.
    code: Optional short code to filter boards by.
    game_slug: Optional game slug to filter boards by game (resolves to game_id).
    slug: Optional board slug to filter by specific board (requires game_slug).
    is_published: Optional filter for published status.
    starts_before: Optional filter for boards starting before this time.
    starts_after: Optional filter for boards starting after this time.
    ends_before: Optional filter for boards ending before this time.
    ends_after: Optional filter for boards ending after this time.

Returns:
    PaginatedResponse with boards and pagination metadata.

Raises:
    400: Invalid cursor, sort field, cursor state mismatch, or slug without game_slug.
    404: Game or board not found when using slug filters.

### Parameters

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|game_id|query|any|false|Filter by game ID|
|code|query|any|false|Filter by short code|
|game_slug|query|any|false|Filter by game slug|
|slug|query|any|false|Filter by board slug (requires game_slug)|
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

Creates a new score submission for a board. All IDs (account_id, game_id, device_id)
are automatically derived from the authenticated device session.

Args:
    score_request: Score creation details including board_id, player_name, and value.
    request: FastAPI request object for accessing geo data.
    service: Injected score service dependency.
    background_tasks: FastAPI background tasks for async metadata updates.
    auth: Client authentication context with device info.
    pre_create_hook: Hook called before score creation (for quota checks).
    post_create_hook: Hook called after successful score creation.

Returns:
    ScoreClientResponse with the created score (excludes device_id).

Raises:
    404: Board not found.
    400: Validation failed (board doesn't belong to account, or game doesn't
        match board's game).

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
  "player_name": "string",
  "value": 0,
  "value_display": "string",
  "metadata": {},
  "rank": 0,
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
filtering by board and/or device. Supports cursor-based pagination
with bidirectional navigation and custom sorting.

Pagination:
- Default: 20 items per page, sorted by created_at:desc,id:asc
- Custom sort: Use ?sort=value:desc,created_at:asc
- Valid sort fields: id, value, player_name, filter_timezone, filter_country,
  filter_city, created_at, updated_at
- Navigation: Use next_cursor/prev_cursor from response

Around Score:
- Use around_score_id to get scores centered around a specific score
- Requires board_id to be specified
- Mutually exclusive with cursor pagination
- Returns a window of scores with the target in the middle
- Respects limit (e.g., limit=5 returns 2 above + target + 2 below)

Example:
    GET /client/scores?board_id=brd_123&limit=50&sort=value:desc,created_at:asc
    GET /client/scores?board_id=brd_123&around_score_id=scr_456&limit=11

Args:
    auth: Authentication context with user info.
    service: Injected score service dependency.
    pagination: Pagination parameters (cursor, limit, sort).
    board_id: Optional board ID to filter by.
    device_id: Optional device ID to filter by (e.g., to get "my scores").
    around_score_id: Optional score ID to center results around.

Returns:
    PaginatedResponse with scores and pagination metadata.

Raises:
    400: Invalid cursor, sort field, cursor state mismatch, or around_score_id validation.
    403: User does not have access to the specified account.
    404: around_score_id score not found.

### Parameters

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|board_id|query|any|false|none|
|device_id|query|any|false|none|
|around_score_id|query|any|false|Center results around this score ID|
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
